# CUTLASS Convolution[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#cutlass-convolution "Link to this heading")

Implicit GEMM is the formulation of a convolution operation as a GEMM (generalized matrix-matrix product). Convolution takes an activation tensor and applies a sliding filter on it to produce an output tensor.

## Introduction[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#introduction "Link to this heading")

This release of CUTLASS contains several artifacts related to convolution.

-   [**Implicit GEMM Algorithm**](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#implicit-gemm-algorithm)
-   [**CUTLASS Convolution Implementation**](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#cutlass-convolution-implementation)
-   [**Convolution Examples**](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#convolution-example)

# Implicit GEMM Algorithm[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#implicit-gemm-algorithm "Link to this heading")

2-D convolution may be mapped to matrix multiply by first forming a _convolution matrix_ containing elements of the activations tensor, then multiplying this by a matrix formed from the filters tensor. The earliest form of this algorithm constructs the convolution matrix explicitly via an operation conventionally referred to as `im2col`. The resulting matrix replicates each activation element by a factor equal to the filter size, consuming additional storage capacity and memory bandwidth.

The _implicit GEMM_ algorithm is a variation on the blocked, hierarchical GEMM computation in CUDA. Instead of constructing the convolution matrix explicitly, it forms tiles of the convolution matrix on the fly as data are loaded from global memory into Shared Memory by carefully updating pointers and predicates. Once the convolution matrix is formed in Shared Memory, the existing warp-level GEMM components accumulate the result of convolution and update the output tensor.

This section describes the structure of an efficient Implicit GEMM Convolution CUDA kernel for Turing Tensor Cores.

## Mapping Convolution to GEMM[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#mapping-convolution-to-gemm "Link to this heading")

The forward convolutional layer computes an output tensor _y = conv(x, w)_ where x(NHWC), w(KRSC), and y(NPQK) are 4-D tensors.

This computation may be described by the following analytic function.

y\[n, p, q, k\] = sum\_c(sum\_r(sum\_s( x\[n, f(p, r), g(q, s), c\] \* w\[k, r, s, c\] )))

Copy to clipboard

where functions _f_ and _g_ are defined as follows.

f(p, r) = p \* stride\_h + R - r - 1 + pad\_h
g(q, s) = q \* stride\_w + S - s - 1 + pad\_w

Copy to clipboard

A [host](https://github.com/NVIDIA/cutlass/tree/main/tools/util/include/cutlass/util/reference/host/convolution.h) and [device](https://github.com/NVIDIA/cutlass/tree/main/tools/util/include/cutlass/util/reference/device/convolution.h) reference implementation are provided in the CUTLASS Utilities.

This computation may be mapped to the elements of a matrix product as follows.

C = gemm(A, B)

Copy to clipboard

where

-   A is a row-major matrix of extent _NHW_\-by-_RSC_ containing activations
-   B is a column-major matrix of extent _RSC_\-by-_K_ containing filters
-   C is a row-major matrix of extent _NPQ_\-by-_K_ containing the output

Each element of the output matrix _Cij_ corresponds to an element in the output tensor y\[n, p, q, k\] according to the following relation.

y\[n, p, q, k\] = Cij

Copy to clipboard

where

i = q + Q \* (p + P \* n)
j = k

Copy to clipboard

These relations may be inverted as follows.

k = j

n = i / (PQ)
residual = i % (PQ)

p = residual / Q
q = residual % Q

Copy to clipboard

The triple loop nest iterating over CRS to accumulate the result may also be linearized and mapped to the inner GEMM _K_ dimension (not to be confused with the filter tensor dimension _K_) by the following relations.

gemm\_k = s + S \* (r + R \* c)

Copy to clipboard

and inverse

c = gemm\_k / (RS)
residual = gemm\_k % (RS)

r = residual / S
s = residual % S

Copy to clipboard

Given these equations, a GEMM triple loop nest could be augmented with tensor indexing as follows.

int GEMM\_M \= N \* P \* Q;
int GEMM\_N \= K;
int GEMM\_K \= C \* R \* S;

for (int gemm\_i \= 0; gemm\_i < GEMM\_M; ++gemm\_i) {
  for (int gemm\_j \= 0; gemm\_j < GEMM\_N; ++gemm\_j) {

    int n \= gemm\_i / (PQ);
    int npq\_residual \= gemm\_i % (PQ);

    int p \= npq\_residual / Q;
    int q \= npq\_residual % Q;

    Accumulator accum \= 0;

    for (int gemm\_k \= 0; gemm\_k < GEMM\_K; ++gemm\_k) {

      int k \= gemm\_j;

      int c \= gemm\_k / (RS);
      int crs\_residual \= gemm\_k % (RS);

      int r \= crs\_residual / S;
      int s \= crs\_residual % S;

      int h \= f(p, r);
      int w \= g(q, s);

      ElementA a \= tensor\_A.at({n, h, w, c});
      ElementB b \= tensor\_B.at({k, r, s, c});

      accum += a \* b;
    }

    C\[gemm\_i \* K + gemm\_j\] \= accum;
  }
}

Copy to clipboard

The [CUTLASS GEMM implementation](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html) explicitly iterates over tiles. Consequently, a tile iterator could be implemented to compute these functions analytically and load the appropriate elements. However, the resulting modulo arithmetic would be computationally intensive, and overhead would limit performance of a GEMM kernel targeting Turing Tensor Cores.

The following section describes how an efficient implementation may be implemented within the structure of a hierarchical GEMM kernel targeting Tensor Cores.

# CUTLASS Convolution Implementation[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#cutlass-convolution-implementation "Link to this heading")

To get the best performance, the following parameters are recommended.

-   All tensors are 128-bit aligned NHWC tensors
-   Channel count (C) is a multiple of 32 elements
-   Filter count (K) is a multiple of 32 elements

This enables 128-bit vector memory acceses which lead to efficient CUDA kernels. Smaller alignment is supported even on tensor cores by setting AlignmentA and AlignmentB in `conv::kernel::DefaultConv2dFprop`, but the performance is lower than 128-bit aligned tensors.

# CUTLASS Device-level Convolution Operator[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#cutlass-device-level-convolution-operator "Link to this heading")

CUTLASS defines CUDA C++ templates accepting numerous template arguments to specialize the resulting kernel by operation, data type, tile configuration, math instruction, and fused output operation.

In [turing\_tensorop\_conv2dfprop.cu](https://github.com/NVIDIA/cutlass/tree/main/examples/09_turing_tensorop_conv2dfprop/turing_tensorop_conv2dfprop.cu), a convolution operation is defined as follows.

/// Define an Implicit GEMM convolution forward propagation (fprop) kernel
using Conv2dFpropKernel \= typename cutlass::conv::kernel::DefaultConv2dFprop<
  ElementInputA,                                          // data type of element a (mapped to activation for fprop)                         
  LayoutInputA,                                           // layout of element a (mapped to activation for fprop)
  ElementInputB,                                          // data type of element b (mapped to filters for fprop)  
  LayoutInputB,                                           // layout of element b (mapped to filters for fprop)
  ElementC,                                               // data type of element c (mapped to output for fprop)
  LayoutC,                                                // layout of element c (mapped to output for fprop)
  ElementAccumulator,                                     // data type of internal accumulation
  MMAOp,                                                  // opcode class tag
  SmArch,                                                 // target SM architecture
  ThreadblockShape,                                       // shape of threadblock tile
  WarpShape,                                              // shape of warp-level GEMM tile
  InstructionShape,                                       // shape of target math instruction
  EpilogueOp,                                             // epilogue operator 
  SwizzleThreadBlock,                                     // optional function to reorder threadblocks for locality
  NumStages,                                              // number of pipeline stages in threadblock-scoped GEMM
  cutlass::arch::OpMultiplyAddSaturate,                   // math operation on data of element a and b
  cutlass::conv::IteratorAlgorithm::kOptimized            // global memory iterator algorithm  
\>::Kernel

Copy to clipboard

This template is intended to be generic and cover all feasible configurations. The example specifies the following concrete data types, layouts, and tile shapes.

/// Define an Implicit GEMM convolution forward propagation (fprop) kernel
using Conv2dFpropKernel \= typename cutlass::conv::kernel::DefaultConv2dFprop<
  cutlass::int4b\_t,                                    // data type of element a (mapped to activation for fprop)                         
  cutlass::layout::TensorNHWC,                         // layout of element a (mapped to activation for fprop)
  cutlass::int4b\_t,                                    // data type of element b (mapped to filters for fprop)  
  cutlass::layout::TensorNHWC,                         // layout of element b (mapped to filters for fprop)
  int32\_t,                                             // data type of element c (mapped to output for fprop)
  cutlass::layout::TensorNHWC,                         // layout of element c (mapped to output for fprop)
  int32\_t,                                             // data type of internal accumulation
  cutlass::arch::OpClassTensorOp,                      // opcode class tag
  cutlass::arch::Sm75,                                 // target SM architecture
  cutlass::gemm::GemmShape<128, 128, 128\>,             // shape of threadblock tile
  cutlass::gemm::GemmShape<64, 64, 128\>,               // shape of warp-level GEMM tile
  cutlass::gemm::GemmShape<8, 8, 32\>,                  // shape of target math instruction
  cutlass::epilogue::thread::LinearCombinationClamp<
    int32\_t,                                           // data type of output matrix
    8,                                                 // The number of elements per vectorized
                                                       // memory access. This becomes the vector width of
                                                       // math instructions in the epilogue too.
    int32\_t,                                           // Data type of accumulator
    float\>;    ,                                       // epilogue operator 
  SwizzleThreadBlock,                                  // optional function to reorder threadblocks for locality
  2,                                                   // number of pipeline stages in threadblock-scoped GEMM
  cutlass::arch::OpMultiplyAddSaturate,                // math operation on data of element a and b
  cutlass::conv::IteratorAlgorithm::kOptimized         // global memory iterator algorithm  
\>::Kernel

Copy to clipboard

That is, this computes 2D convolutional forward propagation with 4-bit integer inputs and outputs (`cutlass::int4b_t`). Internal accumulation is performed using 32-bit integers (`int32_t`), and an elementwise linear combination operation is performed on the output in single-precision floating point (`float`).

The threadblock and warp-level tile shapes refer to the hierarchically blocked GEMM computation [described here](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/gemm_api.html). Larger tiles achieve greater reuse of data loaded through shared memory but launch fewer CTAs and may not fully occupy the GPU for small problem sizes. Smaller tile configurations achieve lower peak utilizations but may better match the number of SMs within the GPU for real-world workloads.

## Launching the convolution[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#launching-the-convolution "Link to this heading")

The following code collects the arguments for an implicit GEMM operation into a structure.

//
// Define arguments for CUTLASS Convolution
//

// mode (kCrossCorrelation or kConvolution)
cutlass::conv::Mode mode \= cutlass::conv::Mode::kCrossCorrelation;

// Split K dimension into 1 partitions
int split\_k\_slices \= 1;

cutlass::conv::Conv2dProblemSize problem\_size(      
    options.input\_size,
    options.filter\_size,
    options.padding,
    options.conv\_stride,
    options.dilation,
    options.output\_size(),
    mode,
    split\_k\_slices);

typename ImplicitGemm::Arguments arguments{
  problem\_size,
  tensor\_a.device\_ref(),
  tensor\_b.device\_ref(),
  tensor\_c.device\_ref(),
  tensor\_c.device\_ref(),
  {options.alpha, options.beta},
};

Copy to clipboard

The `mode` flag indicates whether to compute cross correlation or convolution. The arguments `input_size`, `filter_size`, `padding`, `conv_stride`, and `dilation` specify the dimensions of the input and output tensors and characterize the problem size.

The arguments `tensor_a.device_ref()`, `tensor_b.device_ref()`, and `tensor_c.device_ref()` are CUTLASS `TensorRef<>` objects containing a pointer to the tensor data in GPU device memory and stride values.

The following code initializes and launches the Implicit GEMM operation on the device. After initializing the arguments structure, it is used to query device-side workspace requirements and allocate them in device memory if needed.

Then, the Implicit GEMM object is initialized with the `arguments` structure and the workspace in device memory. This initialization step precomputes internal lookup tables used by the convolution kernel and may also clear the device-side workspace if needed.

Finally, the initialized Implicit GEMM object is called, launching a kernel on the device. `tensor_c` now contains the result of the implicit GEMM.

ImplicitGemm implicit\_gemm\_op;

// Query workspace size
size\_t workspace\_size \= implicit\_gemm\_op.get\_workspace\_size(arguments);

// Allocate workspace memory
cutlass::device\_memory::allocation<uint8\_t\> workspace(workspace\_size);

// Initialize the Implicit GEMM object
cutlass::Status status \= implicit\_gemm\_op.initialize(arguments, workspace.get());

if (status != cutlass::Status::kSuccess) {
  /\* error \*/
}

//
// Launch initialized CUTLASS kernel
//

status \= implicit\_gemm\_op();

if (status != cutlass::Status::kSuccess) {
  /\* error \*/
}

Copy to clipboard

The example demonstrates how the input and output tensors may be written to a file as CSV using `cutlass::HostTensor<>` defined in the [CUTLASS Utilities](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/utilities.html).

  std::ofstream output\_workspace(ss.str());

  output\_workspace 
    << "Input = \\n" << tensor\_a.host\_view() << "\\n\\n"
    << "Filters = \\n" << tensor\_b.host\_view() << "\\n\\n";

  // Copy device memory to host backing store
  tensor\_c.sync\_host();

  output\_workspace << "Computed = \\n" << tensor\_c.host\_view() << std::endl;

Copy to clipboard

## CUTLASS Components[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#cutlass-components "Link to this heading")

CUTLASS defines the following CUDA C++ templates to implement Implicit GEMM Convolution which are described in greater detail in subsequent sections.

**Activations tile iterators** load the activations tile into registers. Two implementations are provided:

-   [conv2d\_fprop\_activation\_tile\_access\_iterator\_analytic.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_activation_tile_access_iterator_analytic.h) computes pointer deltas and masks analytically
-   [conv2d\_fprop\_activation\_tile\_access\_iterator\_optimized.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_activation_tile_access_iterator_optimized.h) optimizes iterating over global memory and creating GEMM-A tile in shared memory.

**Filter tile iterators** load filters into registers. Similarly, two implementations are provided:

-   [conv2d\_fprop\_filter\_tile\_access\_iterator\_analytic.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_filter_tile_access_iterator_analytic.h) computes pointer deltas and masks analytically
-   [conv2d\_fprop\_filter\_tile\_access\_iterator\_optimized.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_filter_tile_access_iterator_optimized.h) optimizes iterating over global memory and creating GEMM-B tile in shared memory.

The improvements covered by optimized iterators are:

a. Precomputing kernel-invariant pointer deltas on the host b. Computing cta-invariant mask predicates on device-side iterator ctors c. Use of [fast divmod](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/fast_math.h) to map GEMM dimensions to convolution tensors.

For example, an _optimized_ activation iterator uses fast divmod to map GEMM _M_ to NPQ.

**Pipelined mainloop** loads threadblock-scoped tiles from global memory into shared memory and then applies CUTLASS warp-level GEMM operations to load from Shared Memory and issue instructions to Turing Tensor Cores.

-   [mma\_pipelined.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/implicit_gemm_pipelined.h)

Operations for storing to shared memory and performing warp-wide matrix multiply operations using Turing Tensor Cores are applied directly from the CUTLASS GEMM components. These include the following components.

**Regular Tile Iterator** implemented in [transform::threadblock::RegularTileIterator](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/transform/threadblock/regular_tile_iterator.h) stores register-backed fragments to Shared Memory in permuted layouts.

**Warp-level GEMM** defined in [cutlass::gemm::warp::MmaTensorOp](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/warp/mma_tensor_op.h) defines tile iterators to load from Shared Memory and issue math instructions to Turing Tensor Cores. Further details are [described in here](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/gemm_api.html#warp-level-matrix-multiply-api).

**Epilogue** reorders accumulator elements among threads within a threadblock to efficiently update the output tensor. It is implemented in [epilogue::threadblock::Epilogue](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/epilogue/threadblock/epilogue.h).

### Loading Activations and Filters[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#loading-activations-and-filters "Link to this heading")

The Implicit GEMM Convolution algorithm partitions the GEMM _K_ dimension (of extent _CRS_) into threadblock tiles and assigning each threadblock tile to one filter position and an interval of channels. After iterating over all filter positions, the convolution algorithm advances to the next interval of channels and proceeds from filter `r=0, s=0`.

The matrix product of one threadblock tile is computed per iteration of the mainloop as described in the [CUTLASS GEMM implementation](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html). To summarize, the threadblock tile of activations and filters are loaded from tensors in global memory and stored to shared memory. Each thread within the threadblock loads one or more vectors and collectively span the entire tile.

The following figure illustrates one particular iteration of the Implicit GEMM mainloop. Each thread within the threadblock is mapped to several vectors of elements in the Activations and Filters tensors. Each index in the GEMM _M_ dimension corresponds to a unique _(N,P,Q)_ index of the output tensor, and pointers may be computed based on this as well as filter position _(r,s)_.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/conv2d-fprop-int4.png)

The CUTLASS component that embodies this functionality is [Conv2dFpropFilterTileAccessIteratorAnalytic](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_activation_tile_access_iterator_analytic.h). Its constructor computes the mapping of GEMM _M_ to _(N, P, Q)_, the `at()` method maps the linear offset into the Activations tensor for each memory access the thread is to perform. Additionally, the method `valid()` computes the valided of the access for each filter position and for each memory access to indicate whether the memory access will be within the bounds of the tensor or out of bounds.

`operator++()` iterates over memory accesses performed by a thread in both contiguous and strided dimension.

// cutlass/conv/threadblock/conv2d\_fprop\_activation\_tile\_access\_iterator\_analytic.h

// Update iterator to thread's next contiguous, strided memory access
Conv2dFpropActivationTileAccessIteratorAnalytic &operator++() {
  ++iteration\_contiguous\_;
  if (iteration\_contiguous\_ < ThreadMap::Iterations::kContiguous) {
    return \*this;
  }
  iteration\_contiguous\_ \= 0;
  
  ++iteration\_strided\_;
  if (iteration\_strided\_ < ThreadMap::Iterations::kStrided) {
    return \*this;
  }
  iteration\_strided\_ \= 0;
 
  return \*this;
}

Copy to clipboard

After all accesses have been visited for the current threadblock tile, `advance()` updates the pointers to next tile. Offsets added to each pointer follows the traversal of filter positions, performing one of the following:

-   advance from filter position _(r, s, c)_ to filter position _(r, s+1, c)_
-   advance from filter position _(r, S-1, c)_ to filter position _(r+1, 0, c)_
-   advance from filter position _(R-1, S-1, c)_ to filter position _(0, 0, c+32)_

This logic within method `advance()`’s body computes the above three updates for the activation GEMM-A tile.

// cutlass/conv/threadblock/conv2d\_fprop\_activation\_tile\_access\_iterator\_analytic.h

// Advance to the next access
void advance() {
  // moves to the next tile
  ++filter\_s\_;
  if (filter\_s\_ < problem\_size\_.S) {
    return;
  }
  filter\_s\_ \= 0;
  
  ++filter\_r\_;
  if (filter\_r\_ < problem\_size\_.R) {
    return;
  }
  filter\_r\_ \= 0;
  
  filter\_c\_ += Shape::kRow \* problem\_size\_.split\_k\_slices;
}

Copy to clipboard

Similar logic holds for [Conv2dFpropFilterTileAccessIteratorAnalytic](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_filter_tile_access_iterator_analytic.h).

To reduce computational overhead in the mainloop body, the pointer offsets may be precomputed in host code and provided to the CUDA kernel as a lookup table in its `Params` structure. As shown in [Conv2dFpropFilterTileAccessIteratorOptimized](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/conv/threadblock/conv2d_fprop_activation_tile_access_iterator_optimized.h), the logic to compute offsets from filter position has been extracted to the `Params` constructor.

// cutlass/conv/threadblock/conv2d\_params.h
struct Conv2dFpropActivationIteratorOptimizedParams<layout::TensorNHWC\> {
 ...
// next S
inc\_next\[0\] \= conv\_sign \* (int64\_t(layout.stride()\[0\]) \* problem\_size.dilation\_w) \* element\_size\_bits / 8;

// next R
inc\_next\[1\] \= conv\_sign \* (
    int64\_t(layout.stride()\[1\]) \* problem\_size.dilation\_h
    \- (problem\_size.S \- 1) \* layout.stride()\[0\] \* problem\_size.dilation\_w
  ) \* element\_size\_bits / 8;

// next C
inc\_next\[2\] \= (
    threadblock\_shape.column() \* problem\_size.split\_k\_slices
    \- conv\_sign \* int64\_t(problem\_size.R \- 1) \* layout.stride()\[1\] \* problem\_size.dilation\_h
    \- conv\_sign \* int64\_t(problem\_size.S \- 1) \* layout.stride()\[0\] \* problem\_size.dilation\_w
  ) \* element\_size\_bits / 8;

 ...
}

Copy to clipboard

This allows only a simple lookup from the _delta table_ performed in device code in `Conv2dFpropActivationTileAccessIteratorOptimized::advance()`.

// cutlass/conv/threadblock/conv2d\_fprop\_activation\_tile\_access\_iterator\_optimized.h
CUTLASS\_HOST\_DEVICE
void advance() { 

  int next\_idx \= 0;
 
  // moves to the next tile
  ++filter\_s\_;
  if (filter\_s\_ \== problem\_size\_.S) {
    filter\_s\_ \= 0;
    ++filter\_r\_;
 
    if (filter\_r\_ < problem\_size\_.R) {
      next\_idx \= 1;
    }
    else {
      filter\_r\_ \= 0;
      next\_idx \= 2;
    }
  }
  
  add\_byte\_offset\_(params\_.inc\_next\[next\_idx\]); // in addition to Conv2dFpropActivationTileAccessIteratorAnalytic::advance()

  if (next\_idx \== 2) {  
    filter\_c\_ += params\_.filter\_c\_delta;
  }
}

Copy to clipboard

### Making use of Tensor Cores[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#making-use-of-tensor-cores "Link to this heading")

Turing Tensor Cores compute matrix multiply-accumulate operations efficiently by sharing data among all threads within a warp. The following operations are supported.

| **Shape** | **A** | **B** | **C** |
| --- | --- | --- | --- |
| 8x8x32 | int4b\\_t | int4b\\_t | int32\\_t |
| 8x8x16 | int8b\\_t | int8b\\_t | int32\\_t |
| 16x8x8 | half | half | half |
| 16x8x8 | half | half | float |

Functionally, the Turing 8x8x32 matrix multiply operation distributes the _A_, _B_, and _C_ matrix across 32 threads within a warp according to the following illustration.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/mma-8x8x32.png)

This Tensor Core operation is accessible to the CUDA programmer via the PTX instruction [`mma.sync`](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#warp-level-matrix-fragment-mma-8832). CUTLASS wraps inline PTX with device-side intrinsics defined in [`cutlass/arch/mma_sm75.h`](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/arch/mma_sm75.h) as in the following example.

unsigned A;   // eight packed 4-bit integer elements
unsigned B;   // eight packed 4-bit integer elements

int C\[2\];     // two 32-bit integer elements
int D\[2\];     // two 32-bit integer elements

asm volatile(
  "mma.sync.aligned.m8n8k32.row.col.s32.s4.s4.s32 {%0,%1}, {%2}, {%3}, {%4,%5};\\n"
  : "=r"(D\[0\]), "=r"(D\[1\])
  : "r"(A), "r"(B), "r"(C\[0\]), "r"(C\[1\]));

Copy to clipboard

To load data efficiently from Shared Memory into registers with the distribution among warps matching the above, the Turing GPU architecture introduces [`ldmatrix`](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#warp-level-matrix-instructions-ldmatrix). `ldmatrix` is the ultimate warp-cooperative instruction, as all threads contribute addresses to up to 32 row vectors of size 128-bits in length. These rows are fetched from Shared Memory and then distributed among groups of four threads per row.

The arrangement of SMEM pointers and destination registers within threads is illustrated as follows. Thread 0 is highlighted in the illustration to emphasize the mapping.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/ldmatrix-8x128bx4.png)

The size of the Turing Tensor Core operation computing matrix multiply-accumulate on INT4 data is 8-by-8-by-32 elements. `ldmatrix` fetches up to 32 rows (or columns) per operation. Sixteen Tensor Core operations may be issued to implement a 32-by-32-by-32 matrix product and perfectly consume all data loaded by two `ldmatrix` instructions as shown in the following figure. Larger tiles are possible by increasing the number of memory instructions and issuing more Tensor Core operations, up to warp-level matrix operations of size 64-by-64-by-32. The limit is the number of registers to hold the accumulator elements.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/ldmatrix-tensorop-32x32x32.png)

### Shared Memory Layouts[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#shared-memory-layouts "Link to this heading")

In the previous two sections, we have described how data may be loaded from activations and filters tensors in global memory to compute convolution, and we have described a composition of `ldmatrix` and `mma.sync` to fetch data from Shared Memory and issue Tensor Core operations.

To ensure this data movement is efficient, care must be taken to ensure bank conflicts are avoided. CUTLASS uses a permuted Shared Memory layout to avoid bank conflicts when storing to Shared Memory and to efficiently load from Shared Memory using `ldmatrix`. The following figure illustrates the thread mapping used for the loading the activations and filters threadblock tiles from global memory and the permuted layout in Shared Memory.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/tensor-op-permuted-smem-layout-TN.png)

In the illustration, one warp-wide memory access is highlighted in blue, with individual threads loading one 128-bit vector. The tile in global memory could correspond either to the activations or filters and is assumed to be ‘strip-mined’ with four threads loading consecutive channels.

Shared Memory is visualized as a ‘row-major’ matrix with eight columns representing the eight 128-bit banks.  
As described in the CUTLASS GTC 2019 presentation [slides](https://developer.download.nvidia.com/video/gputechconf/gtc/2019/presentation/s9593-cutensor-high-performance-tensor-operations-in-cuda-v2.pdf), [recording](https://developer.nvidia.com/gtc/2019/video/S9593), an access to Shared Memory will be conflict-free if the following conditions are satisfied across each warp:

-   {T0, T1, .., T7} do not access the same 128-bit bank
-   {T8, T9, .., T15} do not access the same 128-bit bank
-   {T16, T17, .., T23} do not access the same 128-bit bank
-   {T24, T25, .., T31} do not access the same 128-bit bank

To achieve conflict-free stores, the Shared Memory layout remaps the strip-mined arrangement to transpose the vectors and applies an XOR operation on the column index of each thread’s pointer. Specifically,

  int store\_column \= (lane\_id % 8) ^ (lane\_id / 8);

Copy to clipboard

This transformation on the layout will be instrumental in reading slices of data from Shared Memory to compute the warp-level matrix multiply using Tensor Cores.

The following figure shows how the first sixteen threads participating in an `ldmatrix` instruction logically map to the c=0..31 slice of a matrix in Shared Memory. This slice is known as a “k-group” within the code because it corresponds to the same K-index of a warp-level matrix multiply.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/tensor-op-permuted-smem-layout-TN-k0.png)

The lower half of the figure shows the physical arrangement in Shared Memory, with threads offset by row and column according to the XOR function. By inspection, we can observe there are no bank conflicts, as _T0 … T7_ each access unique banks, as do _T8 … T15_. and beyond.

To advance to the next “k-group” within Shared Memory, pointers are updated using an XOR operation according to the following sequence:

-   **^1** advances from _k=0_ to _k=1_
-   **^3** advances from _k=1_ to _k=2_
-   **^1** advances from _k=2_ to _k=3_
-   **^3** advances from _k=3_ to _k=0_

The first of these transitions is shown below. ![ALT](https://docs.nvidia.com/cutlass/latest/_images/tensor-op-permuted-smem-layout-TN-k1.png)

The [CUTLASS warp-level GEMM API](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/gemm_api.html#warp-level-matrix-multiply-api) defines templates for loading slices of data from permuted Shared Memory and issuing operations to Tensor Cores.

### Updating the Output Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#updating-the-output-tensor "Link to this heading")

After the mainloop terminates, the accumulator tile of the warp-level GEMM stores a warp’s contribution to the output tensor. However, the distribution of data among threads within the threadblock is specialized for efficient matrix multiply-accumulate operations using Tensor Cores and is not conducive to efficient, coalesced operations to Global Memory. A data rearrangement is needed.

The **Epilogue** is the component for exchanging accumulator elements through Shared Memory, loading slices of the output matrix or tensor, applying an elementwise operation such as linear scaling or bias, and storing the result to the output tensor. CUTLASS structures this as several components:

-   [cutlass::epilogue::threadblock::Epilogue](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/epilogue/threadblock/epilogue.h) - the top-level component for looping over the entire threadblock tile
-   [cutlass::epilogue::warp::TileIteratorTensorOp](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/epilogue/warp/tile_iterator_tensor_op.h) - a specialized component for storing accumulators for Tensor Core to Shared Memory
-   [cutlass::epilogue::threadblock::SharedLoadIterator](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/epilogue/threadblock/shared_load_iterator.h) - a component for loading elements from a row-major arrangement in Shared Memory
-   [cutlass::epilogue::threadblock::PredicatedTileIterator](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/epilogue/threadblock/predicated_tile_iterator.h) - a component for loading or storing matrix fragments to Global Memory (with bounds checks)
-   [cutlass::epilogue::thread::LinearCombination](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/epilogue/thread/linear_combination.h) - an element-wise function computing `alpha * AB + beta * C` to compute the final output

## Unit Tests[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#unit-tests "Link to this heading")

Unit tests verify the functional behavior of each of the above components in a standalone CUDA kernel. This provides a convenient environment to

a. inspect the template definition, b. showcase instantiation of use of these templates in device code, and c. assert functional correctness.

**Convolution unit tests**

-   Device-wide convolution operator: [conv2d\_fprop\_implicit\_gemm\_s4nhwc\_s4nhwc\_s32nhwc\_tensor\_op\_s32\_sm75.cu](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s4nhwc_s4nhwc_s32nhwc_tensor_op_s32_sm75.cu)

**GEMM unit tests**

-   Warp-scoped matrix multiply for Turing Tensor Cores: [gemm\_sm75.cu](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/warp/gemm_sm75.cu)

**Epilogue unit tests**

-   Epilogue for Turing Tensor Cores: [epilogue\_tensor\_op.cu](https://github.com/NVIDIA/cutlass/tree/main/test/unit/epilogue/threadblock/epilogue_tensor_op.cu)

# Convolution Example[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#convolution-example "Link to this heading")

This section describes the provided convolution example and is intended to orient the reader to the CUTLASS implementation of Implicit GEMM Convolution.

## Building and Running the Example[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/implicit_gemm_convolution.html#building-and-running-the-example "Link to this heading")

Example `09_turing_tensorop_conv2dfprop` computes a forward convolutional layer in which inputs and outputs are 4-b integers. The example source is visible in [examples/09\_turing\_tensorop\_conv2dfprop/turing\_tensorop\_conv2dfprop.cu](https://github.com/NVIDIA/cutlass/tree/main/examples/09_turing_tensorop_conv2dfprop/turing_tensorop_conv2dfprop.cu).

Before building the example, first perform the prerequisite steps for building any CUTLASS component [described here](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/quickstart.html). Compute capability 7.5 refers to the Turing architecture, and this work requires CUDA 10.2 Toolkit or later to target Turing Tensor Cores using the native `mma` [PTX instruction](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#warp-level-matrix-fragment-mma-8832).

$ mkdir build && cd build

$ cmake .. \-DCUTLASS\_NVCC\_ARCHS\=75

Copy to clipboard

To build the example, execute `make 09_turing_tensorop_conv2dfprop` from the build directory.

$ make 09\_turing\_tensorop\_conv2dfprop

$ ls examples/09\_turing\_tensorop\_conv2dfprop 
examples/09\_turing\_tensorop\_conv2dfprop

Copy to clipboard

This example provides a simple command line interface to specify the extents of 4D tensors of 4-bit integer elements (`cutlass::int4b_t`), initialize them to random values, and compute the result of a convolutional layer. Optionally, the input and output tensors may be saved to .csv files, and the CUTLASS host-side reference check may be executed to verify correctness.

The complete usage statement is visible by running with `--help`:

$ ./examples/09\_turing\_tensorop\_conv2dfprop/09\_turing\_tensorop\_conv2dfprop \--help
09\_turing\_tensorop\_conv2dfprop example

  This example uses Turing's Tensor Core operators on int4 data types to compute
  forward convolution on tensors of layout NHWC.

Options:

  --help               If specified, displays this usage statement.

  --n <int>            Input tensor extent N
  --h <int>            Input tensor extent H
  --w <int>            Input tensor extent W
  --c <int>            Input tensor extent C
  --k <int>            Filter extent K
  --r <int>            Filter extent R
  --s <int>            Filter extent S

  --alpha <float>      Epilogue scalar alpha
  --beta <float>       Epilogue scalar beta

  --ref-check          If set (true), reference check on the host is computed
  --perf-check         If set (true), performance is measured.
  --benchmark          If set (true), performance benchmarking on several layers and batch-size.
  --iterations <int>   Number of profiling iterations to perform.
  --save-workspace     If set, workspace is written to a text file.
  --tag <string>       String to replicate across the first column in the results table

Examples:

$ ./examples/09\_turing\_tensorop\_conv2dfprop/09\_turing\_tensorop\_conv2dfprop  \--n\=32 \--h\=224 \--w\=224 \--c\=128 \--k\=256 \--r\=1 \--s\=1

$ ./examples/09\_turing\_tensorop\_conv2dfprop/09\_turing\_tensorop\_conv2dfprop  \--n\=1 \--h\=224 \--w\=224 \--c\=32 \--k\=32 \--r\=3 \--s\=3 \--ref-check

Copy to clipboard

_Note_, this example assumes all tensors are 128b aligned and in format _NHWC_. Consequently, dimension _C_ must be divisible by 32 for activations, filters, and output.

If the option `--benchmark` is passed, several layers from ResNet50 are profiled for various batch sizes. This sample output was computed on an NVIDIA RTX 2080 compiled with CUDA 10.2.

build$ ./examples/09\_turing\_tensorop\_conv2dfprop/09\_turing\_tensorop\_conv2dfprop \--benchmark

Copy to clipboard

Convolution can also be run by the CUTLASS Profiler.