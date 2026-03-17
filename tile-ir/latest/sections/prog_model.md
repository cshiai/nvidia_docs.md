# 2\. Programming Model[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#programming-model "Link to this heading")

**Tile IR** extends CUDA’s low-level programming model with new abstractions that differ from what has previously existed in CUDA C++ or PTX.

This section introduces the programming model of **Tile IR** and familiarizes the reader with its core concepts and abstractions. We do this by working through a series of real programs, building up to a dynamic, high-performance implementation of GEMM that makes use of the all major features of **Tile IR**.

**Tile IR** has an expressive tile-based programming model. We introduce users to the various ways to represent tensor computation by progressively adapting the example programs to take better advantage of **Tile IR** features which help simplify programs and enable the compiler to provide performance portability. We start by first introducing concepts that readers may be familiar with from prior art.

## 2.1. Tile Kernels[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#tile-kernels "Link to this heading")

**Tile IR** programs are referred to as _tile kernels_, which like CUDA C++ or PTX, are functions which run as N copies in parallel when invoked. The primary difference is the basic unit of execution: a _tile-block_, which expresses the computation performed by a single logical tile thread operating over a multi-dimensional tile of data.

During execution, each tile kernel is referred to as a tile kernel instance.

Below is a simple **Tile IR** kernel which prints “Hello World!”.

cuda\_tile.module @hello\_world\_module {
    entry @hello\_world\_kernel() {
        print "Hello World!\\n"
    }
}

Copy to clipboard

For those familiar with CUDA threads, it is important to note that **Tile IR**’s threads are different. Before we go any further into formalisms, it is essential we highlight those differences.

Tile kernels are the entry point of the program, executing as parallel instances of tile blocks.

### 2.1.1. What’s different about tile programming?[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#what-s-different-about-tile-programming "Link to this heading")

**Tile IR** is an extension to the CUDA programming model that enables first class support for tile programming. Tiled kernels express programs as a grid of logical tile threads that operate over tiles. The mapping of both the grid and individual tile threads to the underlying hardware’s threads is abstracted away from the programming model and is handled by the compiler.

The SIMT programming model of NVIDIA’s streaming multiprocessor (SM) is one in which threads operate over (relatively) small pieces of data and the user is responsible for dividing and scheduling the threads into the appropriate blocks to compute over the input data in an efficient manner. This model gives flexibility to programmers on how to map threads to data, or vice-versa. SIMT is the programming model exposed by CUDA and PTX and has served NVIDIA GPUs well since its introduction in 2006.

The rise in importance of deep learning has both introduced a greater regularity to user workloads and an ever increasing need to deliver performance for these workloads. As discussed in the [Introduction](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/introduction.html#section-introduction), this has led to new specialized hardware in the form of tensor cores.

Tensor cores introduce a new dimension to the SIMT programming model. Now, SM threads must cooperate with the tensor cores in order to reach peak performance. With each new generation of hardware the interplay between these two pieces of silicon has unlocked amazing new performance but with increasing programming complexity.

**Tile IR** has been built to aid in the implementation of high-performance algorithms that take full advantage of the underlying hardware’s capabilities while mitigating the increase in programming complexity.

By abstracting thread-to-data mapping, **Tile IR** simplifies the use of specialized hardware like Tensor Cores compared to traditional SIMT models.

### 2.1.2. Kernel I/O[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#kernel-i-o "Link to this heading")

To illustrate the design of **Tile IR** we will move from our simple hello world kernel to one which implements 1-d tensor (i.e., vector) addition with a fixed block size `128`. All examples presented in this section can be found in the [Programming Model Example Programs](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#section-appendix-sub-prog).

Tile kernels accept inputs and outputs as parameters; this is the only mechanism for consuming and producing data, so we start by defining the kernel parameters.

entry @vector\_block\_add\_128x1\_kernel(
    %a\_ptr\_base\_scalar : !cuda\_tile.tile<ptr<f32\>>,
    %b\_ptr\_base\_scalar : !cuda\_tile.tile<ptr<f32\>>,
    %c\_ptr\_base\_scalar : !cuda\_tile.tile<ptr<f32\>>)

Copy to clipboard

The above code fragment defines a kernel named `vector_block_add_128x1_kernel` which takes three arguments, representing the two input buffers `a` and `b`, and the output buffer `c`. The types of all the arguments are scalar pointers, which are represented as zero dimensional tensors containing a single pointer.

All values in **Tile IR** are either tensors, or tensor views (see [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-views)). A tensor is an n-dimensional rectangular array, described by its rank (number of dimensions), the shape (extent along each dimension), and its primitive element type. Tensors may have a rank of 0 or higher. Rank-0 tensors are scalars. The rank, dimensions, and element type are all part of the tensor type and are statically known. Tensor types are assigned to values which represent a logical view of a multidimensional array contained in global memory. Global memory is always accessed via tensors, and thus pointer arguments always point to CUDA device allocations in global device memory. Tile kernels do not have return values and thus omit a return type annotation (note that tile functions may have a return type, and will be discussed later).

An astute reader might now be wondering why we gave the inputs and outputs scalar pointer types instead of tensors types with statically known rank, shape, and stride. A common pattern in the **Tile IR** programming model is for kernels to take unstructured base pointers as parameters which can then be used to construct the required tensor. This flexibility gives rise to multiple ways to use pointers depending on the desired program behavior, but we will first focus on the most flexible representation by converting our base pointer into a tensor of arbitrary pointers. A tensor of arbitrary pointers is a flexible abstraction which allows you to perform scatter/gather style loads from a set of addresses all at once, and treat a set of addresses as a logical tile.

We must take a few steps to convert a base pointer `%a_ptr_base_scalar` into a tensor of pointers representing the `128x1` tile we want to compute on which contains addresses from `(base + 0, ..., base + 127)`

We start by creating an offset tensor which represents the inclusive `(0, 127)` interval. We use [cuda\_tile.iota](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-iota) which constructs a range tensor that counts from `0` to `n - 1` forming an `n` sized vector.

    %offset \= iota : tile<128xi32\>

Copy to clipboard

We then reshape from a scalar `ptr<f32>` to a 1-d tensor `1xptr<f32>` so we have the correct rank.

%a\_ptr\_base\_tensor \= reshape %a\_ptr\_base\_scalar :
    tile<ptr<f32\>> \-> tile<1xptr<f32\>>

Copy to clipboard

We then broadcast the pointer so we have a 1-d tensor of `(base, ..., base)` containing 128 elements.

%a\_ptr \= broadcast %a\_ptr\_base\_tensor : tile<1xptr<f32\>> \-> tile<128xptr<f32\>>

Copy to clipboard

Add the offset tensor to the tensor of pointers to obtain a `tile<128xptr<f32>>` that contains pointers of `(base + 0, ..., base + 127)` as its values. Now we have a tensor of pointers which represents the tile that we would like to compute on. We perform the same set of steps for `a`, `b`, and `c`.

%a\_tensor \= offset %a\_ptr, %offset :
    tile<128xptr<f32\>>, tile<128xi32\> \-> tile<128xptr<f32\>>

Copy to clipboard

Finally, we load both operands, perform the addition, and store to the output.

%a\_val, %token\_a \= load\_ptr\_tko weak %a\_tensor : tile<128xptr<f32\>> \-> tile<128xf32\>, token
%b\_val, %token\_b \= load\_ptr\_tko weak %b\_tensor : tile<128xptr<f32\>> \-> tile<128xf32\>, token
%c\_val \= addf %a\_val, %b\_val rounding<nearest\_even\> : tile<128xf32\>
store\_ptr\_tko weak %c\_tensor, %c\_val : tile<128xptr<f32\>>, tile<128xf32\> \-> token

Copy to clipboard

We now have a complete kernel for a single tile-block that performs addition over 128 element vectors. As you can see this code is written from a single thread of control, but its level of parallelism will be determined by the compiler.

Kernels communicate with global memory via pointer arguments, which can be transformed into tensors using shape and stride manipulation for flexible data access.

## 2.2. Tile Grid[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#tile-grid "Link to this heading")

So far we have only examined kernels which are written for a single tile block. **Tile IR** allows tile blocks to be grouped into a **tile grid**, similar to CUDA C++, enabling users to launch sets of tile blocks that execute in parallel. Tile kernels, as with PTX, are implicitly parameterized over the tile block coordinates (which can be queried via [cuda\_tile.get\_tile\_block\_id](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-tile-block-id)) and can be 1-d, 2-d, or 3-d.

When a tile kernel is launched the user specifies the grid size, which determines the number of tile blocks launched. The number of tile blocks launched is equal to the size of the grid. For example if we launch our previous example with a `(1, 1, 2)` grid, we will run an identical computation twice.

We can now look at an **improved** hello world program which shows off querying the grid size and coordinates.

cuda\_tile.module @hello\_world\_module {
    // TileIR kernel function
    entry @hello\_world\_kernel() {
        // Step 1. Get the tile block ID
        %block\_x\_index, %block\_y\_index, %block\_z\_index \= cuda\_tile.get\_tile\_block\_id : tile<i32\>

        // Step 2. Get the tile block dimensions
        %block\_dim\_x, %block\_dim\_y, %block\_dim\_z \= cuda\_tile.get\_num\_tile\_blocks : tile<i32\>

        // Step 3. Print the tile block ID and dimensions. Each tile executes the 
        // following print statement and prints a single line.
        cuda\_tile.print "Hello, I am tile <%i, %i, %i> in a kernel with <%i, %i, %i> tiles.\\n",
            %block\_x\_index, %block\_y\_index, %block\_z\_index, %block\_dim\_x, %block\_dim\_y, %block\_dim\_z
            : tile<i32\>, tile<i32\>, tile<i32\>,
              tile<i32\>, tile<i32\>, tile<i32\>
        }
}

Copy to clipboard

Each tile kernel can be launched with a 1-d, 2-d, or 3-d grid. Each tile block can query its position in the grid using [cuda\_tile.get\_tile\_block\_id](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-tile-block-id) and query the first, second, or third dimension index by varying the argument. Tile kernels can also observe the grid dimensions in a similar way using [cuda\_tile.get\_num\_tile\_blocks](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-num-tile-blocks).

If we use a grid that is `(1, 1, 2)` we will see two prints:

1      "Hello, I am tile <0, 0, 0> in a kernel with <1, 1, 2> tiles."
2      "Hello, I am tile <0, 0, 1> in a kernel with <1, 1, 2> tiles."

Copy to clipboard

The tile grid organizes parallel execution of tile blocks, allowing kernels to scale across the problem size by querying their coordinates within the grid.

### 2.2.1. Implementing GEMM[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#implementing-gemm "Link to this heading")

Now that we understand the basics concepts of the **Tile IR** programming model, we will introduce how to compute a 2-d GEMM for a single block, and then generalize it step by step to a full GEMM by utilizing the tile grid and introducing control flow and manual tiling.

This progression demonstrates how to compose basic tile operations into a complex, high-performance parallel algorithm.

### 2.2.2. GEMM with a Single Block[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#gemm-with-a-single-block "Link to this heading")

Let’s first start by naturally moving from a single static block vector addition to a single static square block matrix multiplication.

This example proceeds much as before:

    entry @gemm\_block\_64x64\_kernel(
        %a\_ptr\_base\_scalar: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>,
        %b\_ptr\_base\_scalar: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>,
        %c\_ptr\_base\_scalar: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>

Copy to clipboard

We start with a set of scalar pointers. To simplify this example, we assume that each of these pointers point to allocations which are at least 64 elements in length with stride equal to 1.

Then much like before we declare a square offset tensor.

    %offset\_flat \= iota : tile<4096xi32\>
    %offset \= reshape %offset\_flat :
        tile<4096xi32\> \-> tile<64x64xi32\>

Copy to clipboard

We declare pointers to the underlying tiles the same way as before for A, B, C.

    %a\_ptr\_base\_tensor \= reshape %a\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
    %a\_ptr \= broadcast %a\_ptr\_base\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
    %a\_tensor \= offset %a\_ptr, %offset :
        tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

Copy to clipboard

The only difference here is that we are building square tiles in 2D instead of 1D.

We then load the input arguments, compute the MMA operation (see [cuda\_tile.mmaf](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-mmaf) for floating-point and [cuda\_tile.mmai](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-mmai) for integers) to compute the output tile, and then store it.

    // Load a single 64x64 matrix from the tile.
    %A\_block, %token\_a \= load\_ptr\_tko weak %a\_tensor :
        tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token
    // Load a single 64x64 matrix from the tile.
    %B\_block, %token\_b \= load\_ptr\_tko weak %b\_tensor :
        tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token
    %C\_block \= mmaf %A\_block, %B\_block, %init\_accum: tile<64x64xf32\>, tile<64x64xf32\>, tile<64x64xf32\>
    store\_ptr\_tko weak %c\_tensor, %C\_block :
        tile<64x64xptr<f32\>>, tile<64x64xf32\> \-> token

Copy to clipboard

If you are experienced in implementing matrix multiplication, you can see that this works well for a single `64x64` square multiplication, but what happens if we want to run the tile kernel over a large input problem size in parallel?

Basic matrix multiplication is achieved by constructing 2D tiles from pointers and performing matrix-multiply-accumulate (MMA) operations within a single block.

### 2.2.3. GEMM Block by Block[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#gemm-block-by-block "Link to this heading")

Let us look at how to generalize this to work for a large matrix size – say `4096x4096`, where each tile block will compute a single output tile of the final matrix. Note that we are still working with the assumption that our problem shape is static and we will return to handling dynamically shaped inputs later on this section.

The kernel declaration looks identical to what we have been thus far taking scalar pointers to our inputs and outputs as arguments.

    entry @gemm\_square\_4096\_tile\_64x64\_kernel(
        %a\_ptr\_base\_scalar: tile<ptr<f32\>>,
        %b\_ptr\_base\_scalar: tile<ptr<f32\>>,
        %c\_ptr\_base\_scalar: tile<ptr<f32\>>

Copy to clipboard

In order to do full matrix multiplication over a large matrix we need to split the problem across multiple tile blocks using the tile grid. We will use a 2-d grid and as such each thread will need to first read its 2-d block coordinates.

    // Read Tile block id's.
    %block\_x\_index, %block\_y\_index, %block\_z\_index \= get\_tile\_block\_id : tile<i32\>

Copy to clipboard

The block coordinates determine which tile of the output matrix we will be computing on this tile block. The kernel is structured as a reduction over the K dimension of the matrix, producing individual but complete output tiles. It loop over the reduction dimension computing a matrix-multiply-accumulate (MMA) operation over each input tile that contributes to the output tile.

As we have been doing before the kernel begins by setting up the initial state. As this kernel is structured as a loop we will first start by setting up the loop state.

    %m\_tile\_size \= constant <i32: 64\> : tile<i32\>
    %m\_stride\_factor \= cuda\_tile.constant <i32: 64\> : tile<64x64xi32\> // todo fix the line # and restore this %n\_tile\_size = cuda\_tile.constant <i32: 64> : tile<i32>
    %k\_tile\_size \= cuda\_tile.constant <i32: 64\> : tile<i32\>

Copy to clipboard

First we specify the tile sizes as constants. In this case because we are using square tiles of square matrices everything is equivalent to 64. Constants in **Tile IR** can be tensor valued, and in this case we create 0-d tensors containing a single scalar value.

    %range\_start \= cuda\_tile.constant <i32: 0\> : tile<i32\>
    %range\_step \= cuda\_tile.constant <i32: 1\> : tile<i32\>
    %init\_accum \= cuda\_tile.constant <f32: 0.000000e+00\> : tile<64x64xf32\>

Copy to clipboard

Next we initialize constants for the loop which we will talk about more in a moment, and zero initialize an accumulator value for the MMA. It is worth noting that the tensor here is a value, the **Tile IR** compiler will deal with allocation and execution.

    %tile\_size\_range \= cuda\_tile.iota : tile<64xi32\>

Copy to clipboard

We also create a shared range from `(0, 63)` using [cuda\_tile.iota](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-iota) again for the reduction dimension.

    %a\_tile\_base \= cuda\_tile.muli %block\_x\_index, %k\_tile\_size : tile<i32\>
    %a\_tile\_base\_reshape \= cuda\_tile.reshape %a\_tile\_base : tile<i32\> \-> tile<1xi32\>
    %a\_tile\_base\_tensor \= cuda\_tile.broadcast %a\_tile\_base\_reshape :
        tile<1xi32\> \-> tile<64xi32\>
    %m\_offsets\_vec \= cuda\_tile.addi %a\_tile\_base\_tensor, %tile\_size\_range : tile<64xi32\>

Copy to clipboard

We must first compute the tensor of offsets for A and B so that we can obtain a tensor of pointers for each in order to load them from memory.

Conceptually we start by computing the offsets of the M dimension using the below Python pseudo code:

m\_offsets \= block\_x\_index \* k\_tile\_size + arange(0, k\_tile\_size)

Copy to clipboard

This produces a vector starting from the “top-corner” of the tile at `(block_x_index * k_tile_size, block_x_index * k_tile_size + k_tile_size)`.

The striding of the A matrix is `(64, 1)`, meaning we can omit the extra multiplication by 1 for the K dimension as each value in the row of the offset matrix is sequential.

For this the offsets in the K dimension would be `k_offs = arange(0, k_tile_size)`, so we can reuse %tile\_size\_range below.

Again we can use the following Python pseudo code to compute the offset matrix:

a\_tile \= reshape(m\_offsets, (64, 1)) \* m\_stride + reshape(k\_offsets, (1, 64)) \* k\_stride

Copy to clipboard

In a libraries like Python’s NumPy this computation hides implicit broadcasting that must be expanded in **Tile IR**.

We will do this in two pieces by first computing the offsets along the `M` dimension, the relative offsets along the `K` dimension, and then adding them together to produce the correct tensor of offsets.

We broadcast the `m_offsets` into a matrix where each column is identical and scaled by stride.

%m\_offsets\_matrix \= cuda\_tile.reshape %m\_offsets\_vec :
    tile<64xi32\> \-> tile<64x1xi32\>
%m\_offsets\_broadcast \= cuda\_tile.broadcast %m\_offsets\_matrix :
    tile<64x1xi32\> \-> tile<64x64xi32\>
%m\_offsets \= cuda\_tile.muli %m\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

Copy to clipboard

The matrix, which is now scaled by 64, would then contain these values:

   \[\[   0,    0,    0,  ...,   0,    0,    0\],
\[  64,   64,   64,  ...,   64,   64,   64\],
\[ 128,  128,  128,  ...,  128,  128,  128\],
   ...,
\[3904, 3904, 3904,  ..., 3904,  3904,  3904\],
\[3968, 3968, 3968,  ..., 3968,  3968,  3968\],
\[4032, 4032, 4032,  ..., 4032,  4032,  4032\]\]

Copy to clipboard

We then broadcast the k\_offsets into a matrix where row is identical and scaled by stride.

%ak\_offsets\_matrix \= cuda\_tile.reshape %tile\_size\_range :
     tile<64xi32\> \-> tile<1x64xi32\>
%ak\_offsets\_broadcast \= cuda\_tile.broadcast %ak\_offsets\_matrix :
    tile<1x64xi32\> \-> tile<64x64xi32\>
%ak\_offsets \= cuda\_tile.muli %ak\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

Copy to clipboard

A is a row-major matrix (i.e the K dimension’s stride is 1) so the K offsets contains sequential values.

   \[\[   0,    1,    2,  ...,   61,    62,    63\],
\[   0,    1,    2,  ...,   61,    62,    63\],
\[   0,    1,    2,  ...,   61,    62,    63\],
   ...,
\[   0,    1,    2,  ...,   61,    62,    63\],
\[   0,    1,    2,  ...,   61,    62,    63\],
\[   0,    1,    2,  ...,   61,    62,    63\]\]

Copy to clipboard

We add the two of them together resulting in rows where the i-th row begins at the i-th\`value of :code:\`m\_offsets and each column contains the next 63 integers.

%a\_tile\_offsets \= cuda\_tile.addi %m\_offsets, %ak\_offsets : tile<64x64xi32\>

Copy to clipboard

   \[\[   0,    1,    2,  ...,   61,   62,   63\],
\[  64,   65,   66,  ...,  125,  126,  127\],
\[ 128,  129,  130,  ...,  189,  190,  191\],
   ...,
\[3904, 3905, 3906,  ..., 3965, 3966, 3967\],
\[3968, 3969, 3970,  ..., 4029, 4030, 4031\],
\[4032, 4033, 4034,  ..., 4093, 4094, 4095\]\]

Copy to clipboard

Note that because this is the 0-th tile of the output matrix it is centered around (0, 0), the next tile will be centered around (64, 0), then (128, 0) and so on. The above computation will result in the 64 x 64 grid at that point based on the grid coordinates.

Now we must do the same for B.

n\_offs \= j \* n\_tile\_size + torch.arange(0, n\_tile\_size)
b\_tile \= k\_offs\[:, None\] \* k\_stride + n\_offs\[None, :\] \* n\_stride

Copy to clipboard

%b\_tile\_base \= cuda\_tile.muli %block\_y\_index, %k\_tile\_size : tile<i32\>
%b\_tile\_base\_reshape \= cuda\_tile.reshape %b\_tile\_base :
    tile<i32\> \-> tile<1xi32\>
%b\_tile\_base\_tensor \= cuda\_tile.broadcast %b\_tile\_base\_reshape :
    tile<1xi32\> \-> tile<64xi32\>
%n\_offsets\_vec \= cuda\_tile.addi %b\_tile\_base\_tensor, %tile\_size\_range : tile<64xi32\>

Copy to clipboard

%bk\_offsets\_matrix \= cuda\_tile.reshape %tile\_size\_range : tile<64xi32\> \-> tile<64x1xi32\>
%bk\_offsets \= cuda\_tile.broadcast %bk\_offsets\_matrix : tile<64x1xi32\> \-> tile<64x64xi32\>

Copy to clipboard

%n\_offsets\_matrix \= cuda\_tile.reshape %n\_offsets\_vec : tile<64xi32\> \-> tile<1x64xi32\>
%n\_offsets\_broadcast \= cuda\_tile.broadcast %n\_offsets\_matrix :  tile<1x64xi32\> \-> tile<64x64xi32\>
%n\_offsets \= cuda\_tile.muli %n\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>
%b\_tile\_offsets \= cuda\_tile.muli %bk\_offsets, %n\_offsets : tile<64x64xi32\>

Copy to clipboard

Now that we have computed the initial offsets for the pointers we simply convert the base pointers and add the offsets like before.

%a\_ptr\_base\_tensor \= cuda\_tile.reshape %a\_ptr\_base\_scalar :
    tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
%a\_ptr \= cuda\_tile.broadcast %a\_ptr\_base\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
%a\_tile\_ptr \= offset %a\_ptr, %a\_tile\_offsets :
    tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

Copy to clipboard

Large matrix operations are decomposed into smaller tiles processed by a grid of blocks, requiring careful calculation of global memory offsets for each block.

### 2.2.4. Looping Over Tiles[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#looping-over-tiles "Link to this heading")

Now after all that preparation we can perform the core computation of the kernel.

%C\_tile, %a\_ptr\_final, %b\_ptr\_final \= for %k in (%range\_start to %k\_tile\_size, step %range\_start) : tile<i32\>
    iter\_values(
        %acc\_prev \= %init\_accum,
        %a\_tile\_ptr\_prev \= %a\_tile\_ptr,
        %b\_tile\_ptr\_prev \= %b\_tile\_ptr
    ) \-> (tile<64x64xf32\>, tile<64x64xptr<f32\>>, tile<64x64xptr<f32\>>)
{
    // Load a single 64x64 matrix from the tile.
    %A\_tile, %token\_a \= load\_ptr\_tko weak %a\_tile\_ptr :
        tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token

    // Load a single 64x64 matrix from the tile.
    %B\_tile, %token\_b \= load\_ptr\_tko weak %b\_tile\_ptr :
        tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token

    %C\_tile\_acc \= mmaf %A\_tile, %B\_tile, %acc\_prev: tile<64x64xf32\>, tile<64x64xf32\>, tile<64x64xf32\>

    // Advance by K block size.
    %block\_size \= constant <i32: 64\> : tile<64x64xi32\>
    %a\_tile\_ptr\_next \= offset %a\_tile\_ptr\_prev, %block\_size
        : tile<64x64xptr<f32\>>, tile<64x64xi32\>
            \-> tile<64x64xptr<f32\>>
    %b\_tile\_ptr\_next \= offset %b\_tile\_ptr\_prev, %block\_size
        : tile<64x64xptr<f32\>>, tile<64x64xi32\>
            \-> tile<64x64xptr<f32\>>

    // Store the partial sum to the 64x64 accumulator.
    continue %C\_tile\_acc, %a\_tile\_ptr\_next, %b\_tile\_ptr\_next : tile<64x64xf32\>, tile<64x64xptr<f32\>>, tile<64x64xptr<f32\>>
}

Copy to clipboard

After completing the reduction over the K dimension we need to store the output tile to the C matrix.

We do the same as we did with A and B, but this time the computation is a little different as we can compute both the X and Y dimensions using only the block coordinates. To think about this intuitively the tiled “column” “rows” produce a single output tile.

cm\_offsets \= block\_x\_index \* BLOCK\_SIZE\_M + arange(0, BLOCK\_SIZE\_M)
cn\_offsets \= pid\_n \* BLOCK\_SIZE\_N + arange(0, BLOCK\_SIZE\_N)
c\_tile \= c\_ptr + stride\_cm \* reshape(cm\_offsets, (64, 1)) + stride\_cn \* reshape(cn\_offsets, (64, 1))

Copy to clipboard

We omit the index computation for %c\_tile\_offset then add it to the base pointer like before.

%c\_tile\_offsets \= muli %c\_tile\_x\_offsets, %c\_tile\_y\_offsets : tile<64x64xi32\>
%c\_ptr\_base\_tensor \= reshape %c\_ptr\_base\_scalar :
    tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
%c\_ptr \= broadcast %c\_ptr\_base\_tensor :
    tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
%c\_tile\_ptr \= offset %c\_ptr, %c\_tile\_offsets :
    tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

Copy to clipboard

We can then store the value just as we have done in all prior kernels.

store\_ptr\_tko weak %c\_tile\_ptr, %C\_tile :
    tile<64x64xptr<f32\>>, tile<64x64xf32\> \-> token

Copy to clipboard

Structured control flow allows efficient iteration over reduction dimensions, accumulating results in registers before writing the final output tile to memory.

## 2.3. Structured Pointers[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#structured-pointers "Link to this heading")

The previous examples have looked at how to define matrix multiplication using tensors of pointers and scatter/gather style loads and stores, which take arbitrary tensors of pointers to operate on. These operations give maximal expressivity to programmers but at the cost of potential performance.

These are valuable to understand; as we saw in the last section, you can build arbitrary tensors of pointers then load and store to them flexibly.

For example, if a user created a complete disjoint tensor of pointers, it is challenging for a human or a compiler to obtain meaningful performance from this program. In the worst case, each element will become a completely disjoint memory operation, preventing vectorized or tensorized operations, or code which makes use of cache or thread locality

This flexibility comes at a cost in both requiring more setup and manual computation to implement even relatively simple algorithms like a tiled GEMM, and the potential of being inefficient. Due to the fact that load/store take arbitrary tensors in the degenerate case it is quite possible that they get decomposed into a sequence of arbitrary loads and stores, which do not make good use of memory locality or the underlying hardware.

**Tile IR** will do its best to obtain good performance with these stores, but optimal performance can more easily be achieved by using a structured pointer, called a `tensor view` in **Tile IR**. tensor views allow us to simplify the programming model of **Tile IR** and to improve the efficiency of user programs.

As we have seen in our previous examples, when a kernel is given a tensor it is a scalar base pointer into global memory.

![A view of global memory](https://docs.nvidia.com/cuda/tile-ir/13.2/_images/global_memory.svg)

The base pointer to A points to an allocation that lives in global memory.[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#id1 "Link to this image")

By formulating our previous problem with the correct sizes, we completely side stepped the complex offset computation, and avoided dealing with imperfect tiling, or store/load masking. See XX for more details about masking.

When constructing a `tensor view` we convert the raw pointer into a tensor using static or dynamic shape and stride information.

In order to both simplify the programming model of **Tile IR** and to improve the efficiency of user programs **Tile IR** also has a structured pointer type known as a tensor view. A tensor view can be constructed from raw pointers via [cuda\_tile.make\_tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-make-tensor-view) and attaches shape and stride information to the pointer and effectively represents a typed pointer to a tensor.

When constructing a tensor view, we convert the raw pointer into a tensor using static or dynamic shape and stride information, which is done via [cuda\_tile.make\_tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-make-tensor-view). This op attaches shape and stride information to the pointer and effectively converts a typed pointer to a tensor.

![A view of global memory](https://docs.nvidia.com/cuda/tile-ir/13.2/_images/tensor_view.svg)

The base pointer to A points to an allocation that lives in global memory.[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#id2 "Link to this image")

Structured pointers, or tensor views, encapsulate shape and stride information, enabling the compiler to optimize memory access and simplifying the user’s code.

## 2.4. Tiling & Views[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#tiling-views "Link to this heading")

Once you have constructed a tensor view, we can make use of [cuda\_tile.make\_partition\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-make-partition-view) to perform tiling of the underlying tensor.

![A view of global memory](https://docs.nvidia.com/cuda/tile-ir/13.2/_images/tiled.svg)

The base pointer to A points to an allocation that lives in global memory.[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#id3 "Link to this image")

In the last section we simplified the problem by choosing tile dimensions that made the problem perfectly square, in the same layout, using simple tiling and static input dimensions, etc. We will relax those constraints to show more complex tile mappings as we explore views and partitions.

### 2.4.1. Vector Addition with Views[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#vector-addition-with-views "Link to this heading")

We can now implement a more complex vector operation with SAXPY or “Single-Precision A·X Plus Y” (a common BLAS operation). We can use `tensor view` and [cuda\_tile.make\_partition\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-make-partition-view) to implement this operation for arbitrary sized vectors.

The kernel first defines its arguments. We now take the inputs `%X`, `%Y`, `%alpha`, as well as the dimensions of the **full** vectors, as arguments.

entry @saxpy\_memref(%X: tile<ptr<f32\>>,
                    %Y: tile<ptr<f32\>>,
                    %alpha: tile<f32\>,
                    %M : tile<i32\>,
                    %N : tile<i32\>) {

Copy to clipboard

For those familiar with other tile programming models, you might wonder why we need to take the input tensor sizes as arguments instead of using them to control the number of blocks and remain implicit in the program.

The tensor view model differs from some existing tile programming models, wherein each kernel is unaware of the overall dimensions of the problem size beyond the need to mask loads and stores. In contrast, `tensor view`’s require the overall tensor dimensions in order to enable efficient and correct lowering of tiling and its related operations automatically.

%x\_memref \= make\_tensor\_view %X, shape \= \[%M, %N\], strides \= \[%M, 1\] : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,1\]\>
%y\_memref \= make\_tensor\_view %Y, shape \= \[%M, %N\], strides \= \[%M, 1\] : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,1\]\>

Copy to clipboard

The tensor view’s constructor takes the shapes and strides dynamically resulting in a dynamically shaped tensor view specified by ? in the type like so: `!cuda_tile.tile view<?x?xf32, strides=[?,1]>`.

We use [cuda\_tile.make\_partition\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-make-partition-view) to create views for `%x` and `%y` which represent a `(M/128 x N/256)` tensor of tiles. Each tile will have the size specified by tile parameter of the partition type.

%x\_view \= make\_partition\_view %x\_memref : partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>
%y\_view \= make\_partition\_view %y\_memref : partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>

Copy to clipboard

[cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) allows us to load the tile specified by `%view[%x, %y]` for both %X and %Y.

%x\_tile, %token\_x \= load\_view\_tko weak %x\_view\[%tileIdX, %tileIdY\] :
    partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>, tile<i32\> \-> tile<128x256xf32\>, token

Copy to clipboard

We can then simply compute using the tiles directly to obtain our result tile.

// Step 6. Compute sAXPY: y = alpha \* A + y

Copy to clipboard

Finally we accumulate the result into `%Y` directly. Here we treat it as both an input and output parameter in this kernel.

Copy to clipboard

Combining tensor views with partitioning simplifies kernel implementation, allowing direct loading and operating on logical tiles without manual offset arithmetic.

### 2.4.2. Dynamic GEMM with Views[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#dynamic-gemm-with-views "Link to this heading")

We have now introduced the core concepts of **Tile IR**. We can put together many of these ideas to support a dynamic GEMM kernel using structured pointers. To start, we make two changes to this GEMM: the inputs are actually transposed into column-major layout, and the inputs are in `fp16` while the output is in `fp32`.

We take the input and output tensors (as pointers), all dimension, and all strides as arguments.

    entry @gemm\_kloop\_kernel(
        %A\_ptr: !cuda\_tile.tile<!cuda\_tile.ptr<f16\>>,
        %B\_ptr: !cuda\_tile.tile<!cuda\_tile.ptr<f16\>>,
        %C\_ptr: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>,
        %M: !cuda\_tile.tile<i32\>, %N: !cuda\_tile.tile<i32\>, %K: !cuda\_tile.tile<i32\>,
        %stride\_ak: !cuda\_tile.tile<i32\>, %stride\_bn: !cuda\_tile.tile<i32\>, %stride\_cm: !cuda\_tile.tile<i32\>

Copy to clipboard

The **Tile IR** compiler can optimize the memory loads and stores of [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) if the alignment of the underlying pointers and strides are known. If these are statically known then we can infer the alignment directly but if they are dynamic, as they are in this case, we can use the [cuda\_tile.assume](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-assume) operation to inform the compiler that the pointer is properly aligned.

Here we use the `div_by` predicate to inform the compiler about the divisibility of these values which can be used to infer alignment constraints directly.

%A\_ptr\_assume \= assume #cuda\_tile.div\_by<16\>, %A\_ptr : tile<ptr<f16\>>
%B\_ptr\_assume \= assume #cuda\_tile.div\_by<16\>, %B\_ptr : tile<ptr<f16\>>
%C\_ptr\_assume \= assume #cuda\_tile.div\_by<16\>, %C\_ptr : tile<ptr<f32\>>
%stride\_ak\_assume \= assume #cuda\_tile.div\_by<8\>, %stride\_ak : tile<i32\>
%stride\_bn\_assume \= assume #cuda\_tile.div\_by<8\>, %stride\_bn : tile<i32\>
%stride\_cm\_assume \= assume #cuda\_tile.div\_by<8\>, %stride\_cm : tile<i32\>

Copy to clipboard

We create a tensor view for `%A`, `%B`, and `%C`.

// A reference to the A tensor pointed to by A\_ptr, (K x M)
%A \= make\_tensor\_view %A\_ptr\_assume, shape \= \[%K, %M\], strides \= \[%stride\_ak, 1\] : tile<i32\> \-> tensor\_view<?x?xf16, strides\=\[?,1\]\>
// A reference to the B tensor pointed to by B\_ptr, (N x K)
%B \= make\_tensor\_view %B\_ptr\_assume, shape \= \[%N, %K\], strides \= \[%stride\_bn, 1\] : tile<i32\> \-> tensor\_view<?x?xf16, strides\=\[?,1\]\>
// A reference to the C tensor pointed to by C\_ptr, (M x N)
%C \= make\_tensor\_view %C\_ptr\_assume, shape \= \[%M, %N\], strides \= \[%stride\_cm, 1\] : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,1\]\>

Copy to clipboard

We create a [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) for each tensor. First A:

%A\_block  \= make\_partition\_view %A : partition\_view<tile\=(128x64), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>

Copy to clipboard

Then B:

%B\_block  \= make\_partition\_view %B : partition\_view<tile\=(64x128), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>

Copy to clipboard

And last C:

%C\_block  \= make\_partition\_view %C : partition\_view<tile\=(128x128), tensor\_view<?x?xf32, strides\=\[?,1\]\>, dim\_map\=\[0, 1\]\>

Copy to clipboard

    // Load a single 64x128 matrix from the tile.
    %B\_frag, %t2 \= load\_view\_tko weak %B\_block \[%k, %bidy\] : partition\_view<tile\=(64x128), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>, tile<i32\> \-> tile<64x128xf16\>, token

Copy to clipboard

We then read the the tile block grid coordinates using [cuda\_tile.get\_tile\_block\_id](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-tile-block-id).

%bidx, %bidy, %bidz \= get\_tile\_block\_id : tile<i32\>

Copy to clipboard

Due to the `K` dimension being dynamic we could do calculations ourselves to compute the size of the index space of the reduction but **Tile IR** provides an operation to do this for us. [cuda\_tile.get\_index\_space\_shape](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-index-space-shape) to get the size of the index space, and thus the size of the reduction loop.

%mk\_len\_i32:2 \= get\_index\_space\_shape %A\_block : partition\_view<tile\=(128x64), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\> \-> tile<i32\>

Copy to clipboard

No we can use a [cuda\_tile.for](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-for) loop to iterate over the tile blocks.

A `for` loop is one of the structured control flow operations in **Tile IR** it steps a loop variable over a range from `(start, end, step)` executing the body for each value in the range. The iter\_values are loop carried variables of the body which are initialized in the loop header and are updated each iteration by yielding them with the [cuda\_tile.continue](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-continue) operation.

In order to implement the reduction we start from `0` to the size of the tiled `K` dimension, stepping uniformly by `1` on each step and a single loop carried variable representing the accumulator tile.

%result \= for %k in (%i0 to %mk\_len\_i32#1, step %i1) : tile<i32\>
    iter\_values(%acc\_prev \= %cst) \-> (tile<128x128xf32\>)

Copy to clipboard

We load tiles from A and B.

// Load a single 128x64 matrix from the tile.
%A\_frag, %t1 \= load\_view\_tko weak %A\_block\[%bidx, %k\] : partition\_view<tile\=(128x64), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>, tile<i32\> \-> tile<128x64xf16\>, token
// Load a single 64x128 matrix from the tile.
%B\_frag, %t2 \= load\_view\_tko weak %B\_block \[%k, %bidy\] : partition\_view<tile\=(64x128), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>, tile<i32\> \-> tile<64x128xf16\>, token

Copy to clipboard

We compute the MMA, and then continue to the next loop iteration with the value.

    %acc \= mmaf %A\_frag, %B\_frag, %acc\_prev: tile<128x64xf16\>, tile<64x128xf16\>, tile<128x128xf32\>
    continue %acc : tile<128x128xf32\>

Copy to clipboard

Finally, like our previous implementation, outside the loop we store to the tile back to `%C` this time via the view avoiding the need to compute the offsets again.

%t3 \= store\_view\_tko weak %result, %C\_block\[%bidx, %bidy\] : tile<128x128xf32\>, partition\_view<tile\=(128x128), tensor\_view<?x?xf32, strides\=\[?,1\]\>, dim\_map\=\[0, 1\]\>, tile<i32\> \-> token

Copy to clipboard

Tensor views support dynamic shapes and strides, enabling robust, flexible kernels that handle varying input sizes while maintaining high performance.

## 2.5. Cross TileBlock Communication[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/prog_model.html#cross-tileblock-communication "Link to this heading")

  cuda\_tile.module @hello\_cross\_block {
    global @\_global\_printf\_mutex <i32: 1\> : tile<1xi32\>

    entry @hello\_cross\_block\_kernel() {
      %idx, %idy, %idz \= get\_tile\_block\_id : tile<i32\>
      %tilex, %tiley, %tilez \= get\_num\_tile\_blocks : tile<i32\>
      %2 \= get\_global @\_global\_printf\_mutex : tile<ptr<i32\>>
      %3 \= cuda\_tile.constant <i32: 0\> : tile<i32\>
      %4 \= cuda\_tile.constant <i32: 1\> : tile<i32\>
      loop {
        %t1 \= make\_token : token
        %6, %t2 \= atomic\_cas\_tko relaxed device %2, %4, %3 token\=%t1: tile<!cuda\_tile.ptr<i32\>>, tile<i32\> \-> tile<i32\>, !cuda\_tile.token
        %7 \= trunci %6 : tile<i32\> \-> tile<i1\>
        if %7 {
          break
        }
      }
      print "current tile: %i / %i\\0A", %idx, %tilex : tile<i32\>, tile<i32\>
      %5, %t4 \= atomic\_rmw\_tko relaxed device %2, xchg, %4: tile<ptr<i32\>>, tile<i32\> \-> tile<i32\>, !cuda\_tile.token
      return
    }
  }
