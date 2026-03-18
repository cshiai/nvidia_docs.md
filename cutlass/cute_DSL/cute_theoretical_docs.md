# Getting Started With CuTe[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#getting-started-with-cute "Link to this heading")

CuTe is a collection of C++ CUDA template abstractions for defining and operating on hierarchically multidimensional layouts of threads and data. CuTe provides `Layout` and `Tensor` objects that compactly packages the type, shape, memory space, and layout of data, while performing the complicated indexing for the user. This lets programmers focus on the logical descriptions of their algorithms while CuTe does the mechanical bookkeeping for them. With these tools, we can quickly design, implement, and modify all dense linear algebra operations.

The core abstraction of CuTe are the hierarchically multidimensional layouts which can be composed with data arrays to represent tensors. The representation of layouts is powerful enough to represent nearly everything we need to implement efficient dense linear algebra. Layouts can also be combined and manipulated via functional composition, on which we build a large set of common operations such as tiling and partitioning.

## System Requirements[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#system-requirements "Link to this heading")

CuTe shares CUTLASS 3.x’s software requirements, including NVCC with a C++17 host compiler.

## Knowledge prerequisites[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#knowledge-prerequisites "Link to this heading")

CuTe is a CUDA C++ header-only library. It requires C++17 (the revision of the C++ Standard that was released in 2017).

Throughout this tutorial, we assume intermediate C++ experience. For example, we assume that readers know how to read and write templated functions and classes, and how to use the `auto` keyword to deduce a function’s return type. We will be gentle with C++ and explain some things that you might already know.

We also assume intermediate CUDA experience. For example, readers must know the difference between device and host code, and how to launch kernels.

## Building Tests and Examples[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#building-tests-and-examples "Link to this heading")

CuTe’s tests and examples build and run as part of CUTLASS’s normal build process.

CuTe’s unit tests live in the [`test/unit/cute`](https://github.com/NVIDIA/cutlass/tree/main/test/unit/cute) subdirectory.

CuTe’s examples live in the [`examples/cute`](https://github.com/NVIDIA/cutlass/tree/main/examples/cute) subdirectory.

## Library Organization[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#library-organization "Link to this heading")

CuTe is a header-only C++ library, so there is no source code that needs building. Library headers are contained within the top level [`include/cute`](https://github.com/NVIDIA/cutlass/tree/main/include/cute) directory, with components of the library grouped by directories that represent their semantics.

| Directory | Contents |
| --- | --- |
| [`include/cute`](https://github.com/NVIDIA/cutlass/tree/main/include/cute) | Each header in the top level corresponds to one of the fundamental building blocks of CuTe, such as [`Layout`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/layout.hpp) and [`Tensor`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/tensor.hpp). |
| [`include/cute/container`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/container) | Implementations of STL-like objects, such as tuple, array, and aligned array. |
| [`include/cute/numeric`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/numeric) | Fundamental numeric data types that include nonstandard floating-point types, nonstandard integer types, complex numbers, and integer sequence. |
| [`include/cute/algorithm`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm) | Implementations of utility algorithms such as copy, fill, and clear that automatically leverage architecture-specific features if available. |
| [`include/cute/arch`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/arch) | Wrappers for architecture-specific matrix-matrix multiply and copy instructions. |
| [`include/cute/atom`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/atom) | Meta-information for instructions in `arch` and utilities like partitioning and tiling. |

## Tutorial[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#tutorial "Link to this heading")

This directory contains a CuTe tutorial in Markdown format. The file [`0x_gemm_tutorial.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html) explains how to implement dense matrix-matrix multiply using CuTe components. It gives a broad overview of CuTe and thus would be a good place to start.

Other files in this directory discuss specific parts of CuTe.

-   [`01_layout.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html) describes `Layout`, CuTe’s core abstraction.
-   [`02_layout_algebra.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/02_layout_algebra.html) describes more advanced `Layout` operations and the CuTe layout algebra.
-   [`03_tensor.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html) describes `Tensor`, a multidimensional array abstraction which composes `Layout` with an array of data.
-   [`04_algorithms.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html) summarizes CuTe’s generic algorithms that operate on `Tensor`s.
-   [`0t_mma_atom.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html) demonstrates CuTe’s meta-information and interface to our GPUs’ architecture-specific Matrix Multiply-Accumulate (MMA) instructions.
-   [`0x_gemm_tutorial.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html) walks through building a GEMM from scratch using CuTe.
-   [`0y_predication.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0y_predication.html) explains what to do if a tiling doesn’t fit evenly into a matrix.
-   [`0z_tma_tensors.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html) explains an advanced `Tensor` type that CuTe uses to support TMA loads and stores.

## Quick Tips[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#quick-tips "Link to this heading")

### How do I print CuTe objects on host or device?[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#how-do-i-print-cute-objects-on-host-or-device "Link to this heading")

The `cute::print` function has overloads for almost all CuTe types, including Pointers, Integers, Strides, Shapes, Layouts, and Tensors. When in doubt, try calling `print` on it.

CuTe’s print functions work on either host or device. Note that on device, printing is expensive. Even just leaving print code in place on device, even if it is never called (e.g., printing in an `if` branch that is not taken at run time), may generate slower code. Thus, be sure to remove code that prints on device after debugging.

You might also only want to print on thread 0 of each threadblock, or threadblock 0 of the grid. The `thread0()` function returns true only for global thread 0 of the kernel, that is, for thread 0 of threadblock 0. A common idiom for printing CuTe objects to print only on global thread 0.

if (thread0()) {
  print(some\_cute\_object);
}

Copy to clipboard

Some algorithms depend on some thread or threadblock, so you may need to print on threads or threadblocks other than zero. The header file [`cute/util/debug.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/util/debug.hpp), among other utilities, includes the function `bool thread(int tid, int bid)` that returns `true` if running on thread `tid` and threadblock `bid`.

#### Other output formats[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html#other-output-formats "Link to this heading")

Some CuTe types have special printing functions that use a different output format.

The `cute::print_layout` function will display any rank-2 layout in a plain text table. This is excellent for visualizing the map from coordinates to indices.

The `cute::print_tensor` function will display any rank-1, rank-2, rank-3, or rank-4 tensor in a plain text multidimensional table. The values of the tensor are printed so you can verify the tile of data is what you expect after a copy, for example.

The `cute::print_latex` function will print LaTeX commands that you can use to build a nicely formatted and colored tables via `pdflatex`. This work for `Layout`, `TiledCopy`, and `TiledMMA`, which can be very useful to get a sense of layout patterns and partitioning patterns within CuTe.

# CuTe Layouts[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#cute-layouts "Link to this heading")

This document describes `Layout`, CuTe’s core abstraction. Fundamentally, a `Layout` maps from coordinate space(s) to an index space.

`Layout`s present a common interface to multidimensional array access that abstracts away the details of how the array’s elements are organized in memory. This lets users write algorithms that access multidimensional arrays generically, so that layouts can change, without users’ code needing to change. For example, a row-major MxN layout and a column-major MxN layout can be treated identically in software.

CuTe also provides an “algebra of `Layout`s.” `Layout`s can be combined and manipulated to construct more complicated layouts and to tile layouts across other layouts. This can help users do things like partition layouts of data over layouts of threads.

## Fundamental Types and Concepts[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#fundamental-types-and-concepts "Link to this heading")

### Integers[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#integers "Link to this heading")

CuTe makes great use of dynamic (known only at run-time) and static (known at compile-time) integers.

-   Dynamic integers (or “run-time integers”) are just ordinary integral types like `int` or `size_t` or `uint16_t`. Anything that is accepted by `std::is_integral<T>` is considered a dynamic integer in CuTe.
-   Static integers (or “compile-time integers”) are instantiations of types like `std::integral_constant<Value>`. These types encode the value as a `static constexpr` member. They also support casting to their underlying dynamic types, so they can be used in expressions with dynamic integers. CuTe defines its own CUDA-compatibe static integer types `cute::C<Value>` along with overloaded math operators so that math on static integers results in static integers. CuTe defines shortcut aliases `Int<1>`, `Int<2>`, `Int<3>` and `_1`, `_2`, `_3` as conveniences, which you should see often within examples.

CuTe attempts to handle static and dynamic integers identically. In the examples that follow, all dynamic integers could be replaced with static integers and vice versa. When we say “integer” in CuTe, we almost always mean a static OR dynamic integer.

CuTe provides a number of traits to work with integers.

-   `cute::is_integral<T>`: Checks whether `T` is a static or dynamic integer type.
-   `cute::is_std_integral<T>`: Checks whether `T` is a dynamic integer type. Equivalent to `std::is_integral<T>`.
-   `cute::is_static<T>`: Checks whether `T` is an empty type (so instantiations cannot depend on any dynamic information). Equivalent to `std::is_empty`.
-   `cute::is_constant<N,T>`: Checks that `T` is a static integer AND its value is equivalent to `N`.

See the [`integral_constant` implementations](https://github.com/NVIDIA/cutlass/tree/main/include/cute/numeric/integral_constant.hpp) for more information.

### Tuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#tuple "Link to this heading")

A tuple is a finite ordered list of zero or more elements. The [`cute::tuple` class](https://github.com/NVIDIA/cutlass/tree/main/include/cute/container/tuple.hpp) behaves like `std::tuple`, but works on device and host. It imposes restrictions on its template arguments and strips down the implementation for performance and simplicity.

### IntTuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#inttuple "Link to this heading")

CuTe defines the IntTuple concept as either an integer, or a tuple of IntTuples. Note the recursive definition. In C++, we define [operations on `IntTuple`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/int_tuple.hpp).

Examples of `IntTuple`s include:

-   `int{2}`, the dynamic integer 2.
-   `Int<3>{}`, the static integer 3.
-   `make_tuple(int{2}, Int<3>{})`, the tuple of dynamic-2, and static-3.
-   `make_tuple(uint16_t{42}, make_tuple(Int<1>{}, int32_t{3}), Int<17>{})`, the tuple of dynamic-42, tuple of static-1 and dynamic-3, and static-17.

CuTe reuses the `IntTuple` concept for many different things, including Shape, Stride, Step, and Coord (see [`include/cute/layout.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/layout.hpp)).

Operations defined on `IntTuple`s include the following.

-   `rank(IntTuple)`: The number of elements in an `IntTuple`. A single integer has rank 1, and a tuple has rank `tuple_size`.
-   `get<I>(IntTuple)`: The `I`th element of the `IntTuple`, with `I < rank`. For single integers, `get<0>` is just that integer.
-   `depth(IntTuple)`: The number of hierarchical `IntTuple`s. A single integer has depth 0, a tuple of integers has depth 1, a tuple that contains a tuple of integers has depth 2, etc.
-   `size(IntTuple)`: The product of all elements of the `IntTuple`.

We write `IntTuple`s with parentheses to denote the hierarchy. For example, `6`, `(2)`, `(4,3)`, and `(3,(6,2),8)` are all `IntTuple`s.

### Shapes and Strides[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#shapes-and-strides "Link to this heading")

Both `Shape` and `Stride` are `IntTuple` concepts.

### Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#layout "Link to this heading")

A `Layout` is a tuple of (`Shape`, `Stride`). Semantically, it implements a mapping from any coordinate within the Shape to an index via the Stride.

### Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#tensor "Link to this heading")

A `Layout` can be composed with data – e.g., a pointer or an array – to create a `Tensor`. The index generated by the `Layout` is used to subscript an iterator to retrieve the appropriate data. For details on `Tensor`, please refer to the [`Tensor` section of the tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html).

## Layout Creation and Use[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#layout-creation-and-use "Link to this heading")

A `Layout` is a pair of `IntTuple`s: the `Shape` and the `Stride`. The first element defines the abstract _shape_ of the `Layout`, and the second element defines the _strides_, which map from coordinates within the shape to the index space.

We define many operations on `Layout`s analogous to those defined on `IntTuple`.

-   `rank(Layout)`: The number of modes in a `Layout`. Equivalent to the tuple size of the `Layout`’s shape.
-   `get<I>(Layout)`: The `I`th sub-layout of the `Layout`, with `I < rank`.
-   `depth(Layout)`: The depth of the `Layout`’s shape. A single integer has depth 0, a tuple of integers has depth 1, a tuple of tuples of integers has depth 2, etc.
-   `shape(Layout)`: The shape of the `Layout`.
-   `stride(Layout)`: The stride of the `Layout`.
-   `size(Layout)`: The size of the `Layout` function’s domain. Equivalent to `size(shape(Layout))`.
-   `cosize(Layout)`: The size of the `Layout` function’s codomain (not necessarily the range). Equivalent to `A(size(A) - 1) + 1`.

### Hierarchical access functions[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#hierarchical-access-functions "Link to this heading")

`IntTuple`s and `Layout`s can be arbitrarily nested. For convenience, we define versions of some of the above functions that take a sequence of integers, instead of just one integer. This makes it possible to access elements inside of nested `IntTuple` or `Layout` more easily. For example, we permit `get<I...>(x)`, where `I...` is a “C++ parameter pack” that denotes zero or more (integer) template arguments. These hierarchical access functions include the following.

-   `get<I0,I1,...,IN>(x) := get<IN>(...(get<I1>(get<I0>(x)))...)`. Extract the `IN`th of the … of the `I1`st of the `I0`th element of `x`.
-   `rank<I...>(x)  := rank(get<I...>(x))`. The rank of the `I...`th element of `x`.
-   `depth<I...>(x) := depth(get<I...>(x))`. The depth of the `I...`th element of `x`.
-   `shape<I...>(x)  := shape(get<I...>(x))`. The shape of the `I...`th element of `x`.
-   `size<I...>(x)  := size(get<I...>(x))`. The size of the `I...`th element of `x`.

In the following examples, you’ll see use of `size<0>` and `size<1>` to determine loops bounds for the 0th and 1st mode of a layout or tensor.

### Constructing a Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#constructing-a-layout "Link to this heading")

A `Layout` can be constructed in many different ways. It can include any combination of compile-time (static) integers or run-time (dynamic) integers.

Layout s8 \= make\_layout(Int<8\>{});
Layout d8 \= make\_layout(8);

Layout s2xs4 \= make\_layout(make\_shape(Int<2\>{},Int<4\>{}));
Layout s2xd4 \= make\_layout(make\_shape(Int<2\>{},4));

Layout s2xd4\_a \= make\_layout(make\_shape (Int< 2\>{},4),
                             make\_stride(Int<12\>{},Int<1\>{}));
Layout s2xd4\_col \= make\_layout(make\_shape(Int<2\>{},4),
                               LayoutLeft{});
Layout s2xd4\_row \= make\_layout(make\_shape(Int<2\>{},4),
                               LayoutRight{});

Layout s2xh4 \= make\_layout(make\_shape (2,make\_shape (2,2)),
                           make\_stride(4,make\_stride(2,1)));
Layout s2xh4\_col \= make\_layout(shape(s2xh4),
                               LayoutLeft{});

Copy to clipboard

The `make_layout` function returns a `Layout`. It deduces the types of the function’s arguments and returns a `Layout` with the appropriate template arguments. Similarly, the `make_shape` and `make_stride` functions return a `Shape` resp. `Stride`. CuTe often uses these `make_*` functions due to restrictions around constructor template argument deduction (CTAD) and to avoid having to repeat static or dynamic integer types.

When the `Stride` argument is omitted, it is generated from the provided `Shape` with `LayoutLeft` as default. The `LayoutLeft` tag constructs strides as an exclusive prefix product of the `Shape` from left to right, without regard to the `Shape`’s hierarchy. This can be considered a “generalized column-major stride generation”. The `LayoutRight` tag constructs strides as an exclusive prefix product of the `Shape` from right to left, without regard to the `Shape`’s hierarchy. For shapes of depth one, this can be considered a “row-major stride generation”, but for hierarchical shapes the resulting strides may be surprising. For example, the strides of `s2xh4` above could be generated with `LayoutRight`.

Calling `print` on each layout above results in the following

s8        :  \_8:\_1
d8        :  8:\_1
s2xs4     :  (\_2,\_4):(\_1,\_2)
s2xd4     :  (\_2,4):(\_1,\_2)
s2xd4\_a   :  (\_2,4):(\_12,\_1)
s2xd4\_col :  (\_2,4):(\_1,\_2)
s2xd4\_row :  (\_2,4):(4,\_1)
s2xh4     :  (2,(2,2)):(4,(2,1))
s2xh4\_col :  (2,(2,2)):(\_1,(2,4))

Copy to clipboard

The `Shape:Stride` notation is used quite often for `Layout`. The `_N` notation is shorthand for a static integer while other integers are dynamic integers. Observe that both `Shape` and `Stride` may be composed of both static and dynamic integers.

Also note that the `Shape` and `Stride` are assumed to be _congruent_. That is, `Shape` and `Stride` have the same tuple profiles. For every integer in `Shape`, there is a corresponding integer in `Stride`. This can be asserted with

static\_assert(congruent(my\_shape, my\_stride));

Copy to clipboard

### Using a Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#using-a-layout "Link to this heading")

The fundamental use of a `Layout` is to map between coordinate space(s) defined by the `Shape` and an index space defined by the `Stride`. For example, to print an arbitrary rank-2 layout in a 2-D table, we can write the function

template <class Shape, class Stride\>
void print2D(Layout<Shape,Stride\> const& layout)
{
  for (int m \= 0; m < size<0\>(layout); ++m) {
    for (int n \= 0; n < size<1\>(layout); ++n) {
      printf("%3d  ", layout(m,n));
    }
    printf("\\n");
  }
}

Copy to clipboard

which produces the following output for the above examples.

\> print2D(s2xs4)
  0    2    4    6
  1    3    5    7
\> print2D(s2xd4\_a)
  0    1    2    3
 12   13   14   15
\> print2D(s2xh4\_col)
  0    2    4    6
  1    3    5    7
\> print2D(s2xh4)
  0    2    1    3
  4    6    5    7

Copy to clipboard

We can see static, dynamic, row-major, column-major, and hierarchical layouts printed here. The statement `layout(m,n)` provides the mapping of the logical 2-D coordinate (m,n) to the 1-D index.

Interestingly, the `s2xh4` example isn’t row-major or column-major. Furthermore, it has three modes but is still interpreted as rank-2 and we’re using a 2-D coordinate. Specifically, `s2xh4` has a 2-D multi-mode in the second mode, but we’re still able to use a 1-D coordinate for that mode. More on this in the next section, but first we can generalize this another step. Let’s use a 1-D coordinate and treat all of the modes of each layout as a single multi-mode. For instance, the following `print1D` function

template <class Shape, class Stride\>
void print1D(Layout<Shape,Stride\> const& layout)
{
  for (int i \= 0; i < size(layout); ++i) {
    printf("%3d  ", layout(i));
  }
}

Copy to clipboard

produces the following output for the above examples.

\> print1D(s2xs4)
  0    1    2    3    4    5    6    7
\> print1D(s2xd4\_a)
  0   12    1   13    2   14    3   15
\> print1D(s2xh4\_col)
  0    1    2    3    4    5    6    7
\> print1D(s2xh4)
  0    4    2    6    1    5    3    7

Copy to clipboard

Any multi-mode of a layout, including the entire layout itself, can accept a 1-D coordinate. More on this in the following sections.

CuTe provides more printing utilities for visualizing Layouts. The `print_layout` function produces a formatted 2-D table of the Layout’s mapping.

\> print\_layout(s2xh4)
(2,(2,2)):(4,(2,1))
      0   1   2   3
    +---+---+---+---+
 0  | 0 | 2 | 1 | 3 |
    +---+---+---+---+
 1  | 4 | 6 | 5 | 7 |
    +---+---+---+---+

Copy to clipboard

The `print_latex` function generates LaTeX that can be compiled with `pdflatex` into a color-coded vector graphics image of the same 2-D table.

### Vector Layouts[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#vector-layouts "Link to this heading")

We define a vector as any `Layout` with `rank == 1`. For example, the layout `8:1` can be interpreted as an 8-element vector whose indices are contiguous.

Layout:  8:1
Coord :  0  1  2  3  4  5  6  7
Index :  0  1  2  3  4  5  6  7

Copy to clipboard

Similarly, the layout `8:2` can be interpreted as an 8-element vector where the indices of the elements are strided by `2`.

Layout:  8:2
Coord :  0  1  2  3  4  5  6  7
Index :  0  2  4  6  8 10 12 14

Copy to clipboard

By the above rank-1 definition, we _also_ interpret layout `((4,2)):((2,1))` as a vector, since its shape is rank-1. The inner shape looks like a 4x2 row-major matrix, but the extra pair of parenthesis suggest we can interpret those two modes as a 1-D 8-element vector. The strides tell us that the first `4` elements are strided by `2` and then there are `2` of those first elements strided by `1`.

Layout:  ((4,2)):((2,1))
Coord :  0  1  2  3  4  5  6  7
Index :  0  2  4  6  1  3  5  7

Copy to clipboard

We can see the second set of `4` elements are duplicates of the first `4` with an extra stride of `1`.

Consider the layout `((4,2)):((1,4))`. Again, it’s `4` elements strided by `1` and then `2` of those first elements strided by `4`.

Layout:  ((4,2)):((1,4))
Coord :  0  1  2  3  4  5  6  7
Index :  0  1  2  3  4  5  6  7

Copy to clipboard

As a function from integers to integers, it’s identical to `8:1`. It’s the identity function.

### Matrix examples[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#matrix-examples "Link to this heading")

Generalizing, we define a matrix as any `Layout` that is rank-2. For example,

Shape :  (4,2)
Stride:  (1,4)
  0   4
  1   5
  2   6
  3   7

Copy to clipboard

is a 4x2 column-major layout with stride-1 down the columns and stride-4 across the rows, and

Shape :  (4,2)
Stride:  (2,1)
  0   1
  2   3
  4   5
  6   7

Copy to clipboard

is a 4x2 row-major layout with stride-2 down the columns and stride-1 across the rows. Majorness is simply which mode has stride-1.

Just like the vector layouts, each of the modes of the matrix can also be split into _multi-modes_. This lets us express more layouts beyond just row-major and column-major. For example,

Shape:  ((2,2),2)
Stride: ((4,1),2)
  0   2
  4   6
  1   3
  5   7

Copy to clipboard

is also logically 4x2, with stride-2 across the rows but a multi-stride down the columns. The first `2` elements down the column have a stride of `4` and then there is a copy of those with stride-1. Since this layout is logically 4x2, like the column-major and row-major examples above, we can _still_ use 2-D coordinates to index into it.

## Layout Concepts[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#layout-concepts "Link to this heading")

In this section, we’ll introduce the coordinate sets that `Layout`s accept and how the coordinate mappings and index mappings are computed.

### Layout compatibility[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#layout-compatibility "Link to this heading")

We say that layout A is _compatible_ with layout B if the shape of A is compatible with the shape of B. Shape A is compatible with shape B if

-   the size of A is equal to the size of B and
-   all coordinates within A are valid coordinates within B.

For example:

-   Shape 24 is NOT compatible with Shape 32.
-   Shape 24 is compatible with Shape (4,6).
-   Shape (4,6) is compatible with Shape ((2,2),6).
-   Shape ((2,2),6) is compatible with Shape ((2,2),(3,2)).
-   Shape 24 is compatible with Shape ((2,2),(3,2)).
-   Shape 24 is compatible with Shape ((2,3),4).
-   Shape ((2,3),4) is NOT compatible with Shape ((2,2),(3,2)).
-   Shape ((2,2),(3,2)) is NOT compatible with Shape ((2,3),4).
-   Shape 24 is compatible with Shape (24).
-   Shape (24) is NOT compatible with Shape 24.
-   Shape (24) is NOT compatible with Shape (4,6).

That is, _compatible_ is a weak partial order on Shapes as it is reflexive, antisymmetric, and transitive.

### Layouts Coordinates[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#layouts-coordinates "Link to this heading")

With the notion of compatibility above, we emphasize that every `Layout` accepts multiple kinds of coordinates. Every `Layout` accepts coordinates for any `Shape` that is compatible with it. CuTe provides mappings between these sets of coordinates via a colexicographical order.

Thus, all Layouts provide two fundamental mappings:

-   the map from an input coordinate to the corresponding natural coordinate via the `Shape`, and
-   the map from a natural coordinate to the index via the `Stride`.

#### Coordinate Mapping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#coordinate-mapping "Link to this heading")

The map from an input coordinate to a natural coordinate is the application of a colexicographical order (reading right to left, instead of “lexicographical,” which reads left to right) within the `Shape`.

Take the shape `(3,(2,3))`, for example. This shape has three coordinate sets: the 1-D coordinates, the 2-D coordinates, and the natural (h-D) coordinates.

| 1-D | 2-D | Natural |     | 1-D | 2-D | Natural |
| --- | --- | --- | --- | --- | --- | --- |
| `0` | `(0,0)` | `(0,(0,0))` |     | `9` | `(0,3)` | `(0,(1,1))` |
| `1` | `(1,0)` | `(1,(0,0))` |     | `10` | `(1,3)` | `(1,(1,1))` |
| `2` | `(2,0)` | `(2,(0,0))` |     | `11` | `(2,3)` | `(2,(1,1))` |
| `3` | `(0,1)` | `(0,(1,0))` |     | `12` | `(0,4)` | `(0,(0,2))` |
| `4` | `(1,1)` | `(1,(1,0))` |     | `13` | `(1,4)` | `(1,(0,2))` |
| `5` | `(2,1)` | `(2,(1,0))` |     | `14` | `(2,4)` | `(2,(0,2))` |
| `6` | `(0,2)` | `(0,(0,1))` |     | `15` | `(0,5)` | `(0,(1,2))` |
| `7` | `(1,2)` | `(1,(0,1))` |     | `16` | `(1,5)` | `(1,(1,2))` |
| `8` | `(2,2)` | `(2,(0,1))` |     | `17` | `(2,5)` | `(2,(1,2))` |

Each coordinate into the shape `(3,(2,3))` has two _equivalent_ coordinates and all equivalent coordinates map to the same natural coordinate. To emphasize again, because all of the above coordinates are valid inputs, a Layout with Shape `(3,(2,3))` can be used as if it is a 1-D array of 18 elements by using the 1-D coordinates, a 2-D matrix of 3x6 elements by using the 2-D coordinates, or a h-D tensor of 3x(2x3) elements by using the h-D (natural) coordinates.

The previous 1-D print demonstrates how CuTe identifies 1-D coordinates with a colexicographical ordering of 2-D coordinates. Iterating from `i = 0` to `size(layout)` and indexing into our layout with the single integer coordinate `i`, traverses the 2-D coordinates in this “generalized-column-major” order, even if the layout maps coordinates to indices in a row-major or more complex fashion.

The function `cute::idx2crd(idx, shape)` is responsible for the coordinate mapping. It will take any coordinate within the shape and compute the equivalent natural coordinate for that shape.

auto shape \= Shape<\_3,Shape<\_2,\_3\>>{};
print(idx2crd(   16, shape));                                // (1,(1,2))
print(idx2crd(\_16{}, shape));                                // (\_1,(\_1,\_2))
print(idx2crd(make\_coord(   1,5), shape));                   // (1,(1,2))
print(idx2crd(make\_coord(\_1{},5), shape));                   // (\_1,(1,2))
print(idx2crd(make\_coord(   1,make\_coord(1,   2)), shape));  // (1,(1,2))
print(idx2crd(make\_coord(\_1{},make\_coord(1,\_2{})), shape));  // (\_1,(1,\_2))

Copy to clipboard

#### Index Mapping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#index-mapping "Link to this heading")

The map from a natural coordinate to an index is performed by taking the inner product of the natural coordinate with the `Layout`’s `Stride`.

Take the layout `(3,(2,3)):(3,(12,1))`, for example. Then a natural coordinate `(i,(j,k))` will result in the index `i*3 + j*12 + k*1`. The indices this layout computes are shown in the 2-D table below where `i` is used as the row coordinate and `(j,k)` is used as the column coordinate.

       0     1     2     3     4     5     <== 1-D col coord
     (0,0) (1,0) (0,1) (1,1) (0,2) (1,2)   <== 2-D col coord (j,k)
    +-----+-----+-----+-----+-----+-----+
 0  |  0  |  12 |  1  |  13 |  2  |  14 |
    +-----+-----+-----+-----+-----+-----+
 1  |  3  |  15 |  4  |  16 |  5  |  17 |
    +-----+-----+-----+-----+-----+-----+
 2  |  6  |  18 |  7  |  19 |  8  |  20 |
    +-----+-----+-----+-----+-----+-----+

Copy to clipboard

The function `cute::crd2idx(c, shape, stride)` is responsible for the index mapping. It will take any coordinate within the shape, compute the equivalent natural coordinate for that shape (if it is not already), and compute the inner product with the strides.

auto shape  \= Shape <\_3,Shape<  \_2,\_3\>>{};
auto stride \= Stride<\_3,Stride<\_12,\_1\>>{};
print(crd2idx(   16, shape, stride));       // 17
print(crd2idx(\_16{}, shape, stride));       // \_17
print(crd2idx(make\_coord(   1,   5), shape, stride));  // 17
print(crd2idx(make\_coord(\_1{},   5), shape, stride));  // 17
print(crd2idx(make\_coord(\_1{},\_5{}), shape, stride));  // \_17
print(crd2idx(make\_coord(   1,make\_coord(   1,   2)), shape, stride));  // 17
print(crd2idx(make\_coord(\_1{},make\_coord(\_1{},\_2{})), shape, stride));  // \_17

Copy to clipboard

## Layout Manipulation[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#layout-manipulation "Link to this heading")

### Sublayouts[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#sublayouts "Link to this heading")

Sublayouts can be retrieved with `layout<I...>`

Layout a   \= Layout<Shape<\_4,Shape<\_3,\_6\>>>{}; // (4,(3,6)):(1,(4,12))
Layout a0  \= layout<0\>(a);                     // 4:1
Layout a1  \= layout<1\>(a);                     // (3,6):(4,12)
Layout a10 \= layout<1,0\>(a);                   // 3:4
Layout a11 \= layout<1,1\>(a);                   // 6:12

Copy to clipboard

or `select<I...>`

Layout a   \= Layout<Shape<\_2,\_3,\_5,\_7\>>{};     // (2,3,5,7):(1,2,6,30)
Layout a13 \= select<1,3\>(a);                   // (3,7):(2,30)
Layout a01 \= select<0,1,3\>(a);                 // (2,3,7):(1,2,30)
Layout a2  \= select<2\>(a);                     // (5):(6)

Copy to clipboard

or `take<ModeBegin, ModeEnd>`

Layout a   \= Layout<Shape<\_2,\_3,\_5,\_7\>>{};     // (2,3,5,7):(1,2,6,30)
Layout a13 \= take<1,3\>(a);                     // (3,5):(2,6)
Layout a14 \= take<1,4\>(a);                     // (3,5,7):(2,6,30)
// take<1,1> not allowed. Empty layouts not allowed.

Copy to clipboard

### Concatenation[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#concatenation "Link to this heading")

A `Layout` can be provided to `make_layout` to wrap and concatenate

Layout a \= Layout<\_3,\_1\>{};                     // 3:1
Layout b \= Layout<\_4,\_3\>{};                     // 4:3
Layout row \= make\_layout(a, b);                 // (3,4):(1,3)
Layout col \= make\_layout(b, a);                 // (4,3):(3,1)
Layout q   \= make\_layout(row, col);             // ((3,4),(4,3)):((1,3),(3,1))
Layout aa  \= make\_layout(a);                    // (3):(1)
Layout aaa \= make\_layout(aa);                   // ((3)):((1))
Layout d   \= make\_layout(a, make\_layout(a), a); // (3,(3),3):(1,(1),1)

Copy to clipboard

or can be combined with `append`, `prepend`, or `replace`.

Layout a \= Layout<\_3,\_1\>{};                     // 3:1
Layout b \= Layout<\_4,\_3\>{};                     // 4:3
Layout ab \= append(a, b);                       // (3,4):(1,3)
Layout ba \= prepend(a, b);                      // (4,3):(3,1)
Layout c  \= append(ab, ab);                     // (3,4,(3,4)):(1,3,(1,3))
Layout d  \= replace<2\>(c, b);                   // (3,4,4):(1,3,3)

Copy to clipboard

### Grouping and flattening[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#grouping-and-flattening "Link to this heading")

Layout modes can be grouped with `group<ModeBegin, ModeEnd>` and flattened with `flatten`.

Layout a \= Layout<Shape<\_2,\_3,\_5,\_7\>>{};  // (\_2,\_3,\_5,\_7):(\_1,\_2,\_6,\_30)
Layout b \= group<0,2\>(a);                 // ((\_2,\_3),\_5,\_7):((\_1,\_2),\_6,\_30)
Layout c \= group<1,3\>(b);                 // ((\_2,\_3),(\_5,\_7)):((\_1,\_2),(\_6,\_30))
Layout f \= flatten(b);                    // (\_2,\_3,\_5,\_7):(\_1,\_2,\_6,\_30)
Layout e \= flatten(c);                    // (\_2,\_3,\_5,\_7):(\_1,\_2,\_6,\_30)

Copy to clipboard

Grouping, flattening, and reordering modes allows the reinterpretation of tensors in place as matrices, matrices as vectors, vectors as matrices, etc.

### Slicing[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#slicing "Link to this heading")

`Layout`s can be sliced, but slicing is more appropriate to perform on `Tensor`s. See the [`Tensor` section](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html) for slicing details.

## Summary[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html#summary "Link to this heading")

-   The `Shape` of a `Layout` defines its coordinate space(s).
    
    -   Every `Layout` has a 1-D coordinate space. This can be used to iterate over the coordinate spaces in a colexicographical order.
    -   Every `Layout` has a R-D coordinate space, where R is the rank of the layout. The colexicographical enumeration of the R-D coordinates correspond to the 1-D coordinates above.
    -   Every `Layout` has an h-D (natural) coordinate space where h is “hierarchical.” These are ordered colexicographically and the enumeration of that order corresponds to the 1-D coordinates above. A natural coordinate is _congruent_ to the `Shape` so that each element of the coordinate has a corresponding element of the `Shape`.
-   The `Stride` of a `Layout` maps coordinates to indices.
    
    -   The inner product of the elements of the natural coordinate with the elements of the `Stride` produces the resulting index.

For each `Layout` there exists an integral `Shape` that is that compatible with that `Layout`. Namely, that integral shape is `size(layout)`. We can then observe that

> Layouts are functions from integers to integers.

If you’re familiar with the C++23 feature `mdspan`, this is an important difference between `mdspan` layout mappings and CuTe `Layout`s. In CuTe, `Layout` is a first class citizen, is natively hierarchical to naturally represent functions beyond row-major and column-major, and can similarly be indexed with a hierarchy of coordinates. (`mdspan` layout mappings can represent hierarchical functions as well, but this requires defining a custom layout.) Input coordinates for an `mdspan` must have the same shape as the `mdspan`; a multidimensional `mdspan` does not accept 1-D coordinates.

# Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/overview.html#overview "Link to this heading")

CUTLASS 4.x bridges the gap between productivity and performance for CUDA kernel development. By providing Python-based DSLs to the powerful CUTLASS C++ template library, it enables faster iteration, easier prototyping, and a gentler learning curve for high-performance linear algebra on NVIDIA GPUs.

Overall we envision CUTLASS DSLs as a family of domain-specific languages (DSLs). With the release of 4.0, we are releasing the first of these in CuTe DSL. This is a low level programming model that is fully consistent with CuTe C++ abstractions — exposing core concepts such as layouts, tensors, hardware atoms, and full control over the hardware thread and data hierarchy.

# Why CUTLASS DSLs?[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/overview.html#why-cutlass-dsls "Link to this heading")

While CUTLASS offers exceptional performance through its C++ template abstractions, the complexity can present challenges for many developers. CUTLASS 4.x addresses this by:

-   **Simplifying metaprogramming**: Metaprogramming in Python is a lot more intuitive than with C++
-   **Accelerating Iteration**: Rapid prototyping with familiar Python syntax and blazing fast compile times
-   **Lowering Barriers**: Reduced learning curve for GPU programming concepts and consistency between CuTe C++ and DSL
-   **Maintaining Performance**: Generated code leverages optimized CUTLASS primitives

Students can learn GPU programming concepts without the complexity of C++ templates. Researchers and performance engineers can rapidly explore algorithms, prototype, and tune kernels before moving to production implementations.

# Key Concepts and Approach[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/overview.html#key-concepts-and-approach "Link to this heading")

CUTLASS DSLs translate Python code into a custom intermediate representation (IR), which is then Just-In-Time (JIT) compiled into optimized CUDA kernels using MLIR and ptxas.

## Core CuTe DSL Abstractions[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/overview.html#core-cute-dsl-abstractions "Link to this heading")

-   **Layouts** – Describe how data is organized in memory and across threads.
-   **Tensors** – Combine data pointers or iterators with layout metadata.
-   **Atoms** – Represent fundamental hardware operations like matrix multiply-accumulate (MMA) or memory copy.
-   **Tiled Operations** – Define how atoms are applied across thread blocks and warps (e.g., `TiledMma`, `TiledCopy`).

For more on CuTe abstractions, refer to the [CuTe C++ library documentation](https://github.com/NVIDIA/cutlass/blob/main/media/docs/cpp/cute/00_quickstart.md).

**Pythonic Kernel Expression**

Developers express kernel logic, data movement, and computation using familiar Python syntax and control flow.

The DSLs simplify expressing loop tiling, threading strategies, and data transformations using concise Python code.

**JIT Compilation**

Python kernels are compiled at runtime into CUDA device code using MLIR infrastructure and NVIDIA’s `ptxas` toolchain, enabling rapid iteration and interactive debugging.

# Relationship to CUTLASS C++[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/overview.html#relationship-to-cutlass-c "Link to this heading")

CUTLASS DSLs are not a replacement for the CUTLASS C++ library or its 2.x and 3.x APIs. Instead, it aims to be a high-productivity kernel authoring framework that shares all concepts with CUTLASS 3.x C++ API such as CuTe, pipelines, schedulers etc.

-   **Performance**: Generated kernels aim to match CUTLASS C++ kernels in performance; however, some performance gaps may exist due to missing optimizations that have been added over the years to CUTLASS C++ and may be missing in the DSLs examples.
-   **Library**: The CUTLASS DSLs do not currently ship with a full GEMM/Conv autotuning profiler or library interface akin to CUTLASS C++. Instead, it focuses on generating and autotuning individual kernel instances (for example: via tile size exploration) and via native integration DL frameworks that support auto-tuning.

# Getting Started[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/overview.html#getting-started "Link to this heading")

-   [Quick Start Guide](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/quick_start.html) – Initial setup and installation.
-   [CuTe DSL](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl.html) – Overview of the typical development and workflow using CuTe DSL.
-   [CuTe DSL API](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api.html) – Refer to the full API documentation.
-   [Limitations](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/limitations.html) – Understand current CuTe DSL constraints and differences from C++.
-   [FAQs](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/faqs.html) – Common questions and known issues.

# CuTe Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#cute-tensors "Link to this heading")

This document describes `Tensor`, CuTe’s core container that deploys the `Layout` concepts previously described.

Fundamentally, a `Tensor` represents a multidimensional array. `Tensor`s abstracts away the details of how the array’s elements are organized and how the array’s elements are stored. This lets users write algorithms that access multidimensional arrays generically and potentially specialize algorithms on a `Tensor`s traits. For example, the rank of the `Tensor` can be dispatched against, the `Layout` of data can be inspected, and the type of data can be verified.

A `Tensor` is represented by two template parameters: `Engine` and `Layout`. For a description of `Layout`, please refer to [the `Layout` section](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/01_layout.html). The `Tensor` presents the same shape and access operators as the `Layout` and uses the result of the `Layout` computation to offset and dereference a random-access iterator held by the `Engine`. That is, the layout of the data is provided by `Layout` and the actual data is provided by the iterator. Such data can live in any kind of memory – global memory, shared memory, register memory – or can even be transformed or generated on the fly.

## Fundamental operations[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#fundamental-operations "Link to this heading")

CuTe `Tensor` provides container-like operations for accessing elements.

-   `.data()`. The iterator this `Tensor` holds.
-   `.size()`. The total logical size of this `Tensor`.
-   `.operator[](Coord)`. Access the element corresponding to the logical coordinate `Coord`.
-   `.operator()(Coord)`. Access the element corresponding to the logical coordinate `Coord`.
-   `.operator()(Coords...)`. Access the element corresponding to the logical coordinate `make_coord(Coords...)`.

CuTe `Tensor` provides a similar core of hierarchical operations as `Layout`.

-   `rank<I...>(Tensor)`. The rank of the `I...`th mode of the `Tensor`.
-   `depth<I...>(Tensor)`. The depth of the `I...`th mode of the `Tensor`.
-   `shape<I...>(Tensor)`. The shape of the `I...`th mode of the `Tensor`.
-   `size<I...>(Tensor)`. The size of the `I...`th mode of the `Tensor`.
-   `layout<I...>(Tensor)`. The layout of the `I...`th mode of the `Tensor`.
-   `tensor<I...>(Tensor)`. The subtensor corresponding to the the `I...`th mode of the `Tensor`.

## Tensor Engines[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#tensor-engines "Link to this heading")

The `Engine` concept is a wrapper for an iterator or array of data. It uses a stripped-down interface of `std::array` to present the iterator.

using iterator     \=  // The iterator type
using value\_type   \=  // The iterator value-type
using reference    \=  // The iterator reference-type
iterator begin()      // The iterator

Copy to clipboard

In general, users do not need to construct `Engine`s on their own. When a `Tensor` is constructed, the appropriate engine – often `ArrayEngine<T,N>`, `ViewEngine<Iter>`, or `ConstViewEngine<Iter>` – will be constructed.

### Tagged Iterators[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#tagged-iterators "Link to this heading")

Any random-access iterator can be used to construct a `Tensor`, but users can also “tag” any iterator with a memory space – e.g., to indicate this iterator is accessing global memory or shared memory. This is done by calling `make_gmem_ptr(g)` or `make_gmem_ptr<T>(g)` to tag `g` as a global memory iterator, and `make_smem_ptr(s)` or `make_smem_ptr<T>(s)` to tag `s` as a shared memory iterator.

Tagging memory makes it possible for CuTe’s `Tensor` algorithms to use the fastest implementation for the specific kind(s) of memory. When calling very specific operations with `Tensor`s, it also allows those operators to verify the tags against what is expected. For example, some kinds of optimized copy operations require the source of the copy to be global memory and the destination of the copy to be shared memory. Tagging makes it possible for CuTe to dispatch to those copy operations and/or verify against those copy operations.

## Tensor Creation[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#tensor-creation "Link to this heading")

`Tensor`s can be constructed as owning or nonowning.

“Owning” `Tensor`s behave like `std::array`. When you copy the `Tensor`, you (deep-)copy its elements, and the `Tensor`’s destructor deallocates the array of elements.

“Nonowning” `Tensor`’s behave like a (raw) pointer. Copying the `Tensor` doesn’t copy the elements, and destroying the `Tensor` doesn’t deallocate the array of elements.

This has implications for developers of generic `Tensor` algorithms. For example, input `Tensor` parameters of a function should be passed by reference or const reference, because passing a `Tensor` by value may or may not make a deep copy of the `Tensor`’s elements.

### Nonowning Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#nonowning-tensors "Link to this heading")

A `Tensor` is usually a nonowning view of existing memory. Nonowning `Tensor`s are created by calling `make_tensor` with two arguments: a random-access iterator, and the `Layout` or arguments to construct a `Layout`.

Here are some examples of creating `Tensor`s that are nonowning views of existing memory.

float\* A \= ...;

// Untagged pointers
Tensor tensor\_8   \= make\_tensor(A, make\_layout(Int<8\>{}));  // Construct with Layout
Tensor tensor\_8s  \= make\_tensor(A, Int<8\>{});               // Construct with Shape
Tensor tensor\_8d2 \= make\_tensor(A, 8, 2);                   // Construct with Shape and Stride

// Global memory (static or dynamic layouts)
Tensor gmem\_8s     \= make\_tensor(make\_gmem\_ptr(A), Int<8\>{});
Tensor gmem\_8d     \= make\_tensor(make\_gmem\_ptr(A), 8);
Tensor gmem\_8sx16d \= make\_tensor(make\_gmem\_ptr(A), make\_shape(Int<8\>{},16));
Tensor gmem\_8dx16s \= make\_tensor(make\_gmem\_ptr(A), make\_shape (      8  ,Int<16\>{}),
                                                   make\_stride(Int<16\>{},Int< 1\>{}));

// Shared memory (static or dynamic layouts)
Layout smem\_layout \= make\_layout(make\_shape(Int<4\>{},Int<8\>{}));
\_\_shared\_\_ float smem\[decltype(cosize(smem\_layout))::value\];   // (static-only allocation)
Tensor smem\_4x8\_col \= make\_tensor(make\_smem\_ptr(smem), smem\_layout);
Tensor smem\_4x8\_row \= make\_tensor(make\_smem\_ptr(smem), shape(smem\_layout), LayoutRight{});

Copy to clipboard

As shown, users wrap the pointer by identifying its memory space: e.g., global memory (via `make_gmem_ptr` or `make_gmem_ptr<T>`) or shared memory (via `make_smem_ptr` or `make_smem_ptr<T>`). `Tensor`s that view existing memory can have either static or dynamic `Layout`s.

Calling `print` on all of the above tensors displays

tensor\_8     : ptr\[32b\](0x7f42efc00000) o \_8:\_1
tensor\_8s    : ptr\[32b\](0x7f42efc00000) o \_8:\_1
tensor\_8d2   : ptr\[32b\](0x7f42efc00000) o 8:2
gmem\_8s      : gmem\_ptr\[32b\](0x7f42efc00000) o \_8:\_1
gmem\_8d      : gmem\_ptr\[32b\](0x7f42efc00000) o 8:\_1
gmem\_8sx16d  : gmem\_ptr\[32b\](0x7f42efc00000) o (\_8,16):(\_1,\_8)
gmem\_8dx16s  : gmem\_ptr\[32b\](0x7f42efc00000) o (8,\_16):(\_16,\_1)
smem\_4x8\_col : smem\_ptr\[32b\](0x7f4316000000) o (\_4,\_8):(\_1,\_4)
smem\_4x8\_row : smem\_ptr\[32b\](0x7f4316000000) o (\_4,\_8):(\_8,\_1)

Copy to clipboard

which displays the pointer type along with any memory space tags, the pointer’s `value_type` width, the raw pointer address, and the associated `Layout`.

### Owning Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#owning-tensors "Link to this heading")

A `Tensor` can also be an owning array of memory. Owning `Tensor`s are created by calling `make_tensor<T>`, where `T` is the type of each element of the array, and a `Layout` or arguments to construct a `Layout`. The array is allocated analogously to `std::array<T,N>` and, therefore, owning `Tensor`s must be constructed with a `Layout` that has static shapes and static strides. CuTe does not perform dynamic memory allocation in `Tensor`s as it is not a common or performant operation within CUDA kernels.

Here are some examples of creating owning `Tensor`s.

// Register memory (static layouts only)
Tensor rmem\_4x8\_col \= make\_tensor<float\>(Shape<\_4,\_8\>{});
Tensor rmem\_4x8\_row \= make\_tensor<float\>(Shape<\_4,\_8\>{},
                                         LayoutRight{});
Tensor rmem\_4x8\_pad \= make\_tensor<float\>(Shape <\_4, \_8\>{},
                                         Stride<\_32,\_2\>{});
Tensor rmem\_4x8\_like \= make\_tensor\_like(rmem\_4x8\_pad);

Copy to clipboard

The `make_tensor_like` function makes an owning Tensor of register memory with the same value type and shape as its input `Tensor` argument and attempts to use the same order of strides as well.

Calling `print` on each of the above tensors produces similar output

rmem\_4x8\_col  : ptr\[32b\](0x7fff48929460) o (\_4,\_8):(\_1,\_4)
rmem\_4x8\_row  : ptr\[32b\](0x7fff489294e0) o (\_4,\_8):(\_8,\_1)
rmem\_4x8\_pad  : ptr\[32b\](0x7fff489295e0) o (\_4,\_8):(\_32,\_2)
rmem\_4x8\_like : ptr\[32b\](0x7fff48929560) o (\_4,\_8):(\_8,\_1)

Copy to clipboard

and we can see that each pointer address is unique indicating that each `Tensor` is a unique array-like allocation.

## Accessing a Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#accessing-a-tensor "Link to this heading")

Users can access the elements of a `Tensor` via `operator()` and `operator[]`, which take `IntTuple`s of logical coordinates.

When users access a `Tensor`, the `Tensor` uses its `Layout` to map the logical coordinate to an offset that can be accessed by the iterator. You can see this in `Tensor`’s implementation of `operator[]`.

template <class Coord\>
decltype(auto) operator\[\](Coord const& coord) {
  return data()\[layout()(coord)\];
}

Copy to clipboard

For example, we can read and write to `Tensor`s using natural coordinates, using the variadic `operator()`, or the container-like `operator[]`.

Tensor A \= make\_tensor<float\>(Shape <Shape < \_4,\_5\>,Int<13\>>{},
                              Stride<Stride<\_12,\_1\>,    \_64\>{});
float\* b\_ptr \= ...;
Tensor B \= make\_tensor(b\_ptr, make\_shape(13, 20));

// Fill A via natural coordinates op\[\]
for (int m0 \= 0; m0 < size<0,0\>(A); ++m0)
  for (int m1 \= 0; m1 < size<0,1\>(A); ++m1)
    for (int n \= 0; n < size<1\>(A); ++n)
      A\[make\_coord(make\_coord(m0,m1),n)\] \= n + 2 \* m0;

// Transpose A into B using variadic op()
for (int m \= 0; m < size<0\>(A); ++m)
  for (int n \= 0; n < size<1\>(A); ++n)
    B(n,m) \= A(m,n);

// Copy B to A as if they are arrays
for (int i \= 0; i < A.size(); ++i)
  A\[i\] \= B\[i\];

Copy to clipboard

## Tiling a Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#tiling-a-tensor "Link to this heading")

Many of the [`Layout` algebra operations](https://github.com/NVIDIA/cutlass/blob/main/media/docs/cpp/cute/02_layout_algebra.md) can also be applied to `Tensor`.

   composition(Tensor, Tiler)
logical\_divide(Tensor, Tiler)
 zipped\_divide(Tensor, Tiler)
  tiled\_divide(Tensor, Tiler)
   flat\_divide(Tensor, Tiler)

Copy to clipboard

The above operations allows arbitrary subtensors to be “factored out” of `Tensor`s. This very commonly used in tiling for threadgroups, tiling for MMAs, and reodering tiles of data for threads.

Note that the `_product` operations are not implemented for `Tensor`s as those would often produce layouts with increased codomain sizes, which means the `Tensor` would require accessing elements unpredictably far outside its previous bounds. `Layout`s can be used in products, but not `Tensor`s.

## Slicing a Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#slicing-a-tensor "Link to this heading")

Whereas accessing a `Tensor` with a coordinate will return an element of that tensor, slicing a `Tensor` will return a subtensor of all the elements in the sliced mode(s).

Slices are performed through the same `operator()` that are used for accessing an individual element. Passing in `_` (the underscore character, an instance of the `cute::Underscore` type) has the same effect as `:` (the colon character) in Fortran or Matlab: retain that mode of the tensor as if no coordinate had been used.

Slicing a tensor performs two operations,

-   the `Layout` is evaluated on the partial coordinate and the resulting offset is accumulated into the iterator – the new iterator points to the start of the new tensor.
-   the `Layout` modes cooresponding to `_`\-elements of the coordinate are used to construct a new layout. Together, the new iterator and the new layout construct the new tensor.

// ((\_3,2),(2,\_5,\_2)):((4,1),(\_2,13,100))
Tensor A \= make\_tensor(ptr, make\_shape (make\_shape (Int<3\>{},2), make\_shape (       2,Int<5\>{},Int<2\>{})),
                            make\_stride(make\_stride(       4,1), make\_stride(Int<2\>{},      13,     100)));

// ((2,\_5,\_2)):((\_2,13,100))
Tensor B \= A(2,\_);

// ((\_3,\_2)):((4,1))
Tensor C \= A(\_,5);

// (\_3,2):(4,1)
Tensor D \= A(make\_coord(\_,\_),5);

// (\_3,\_5):(4,13)
Tensor E \= A(make\_coord(\_,1),make\_coord(0,\_,1));

// (2,2,\_2):(1,\_2,100)
Tensor F \= A(make\_coord(2,\_),make\_coord(\_,3,\_));

Copy to clipboard

![slice.png](https://docs.nvidia.com/cutlass/latest/_images/slice.png)

In the image above, a `Tensor` is sliced in various ways and the subtensors generated by those slices are highlighted within the original tensor. Note that tensor `C` and `D` contain the same elements, but have different ranks and shapes due to the use of `_` versus the use of `make_coord(_,_)`. In each case, the rank of the result is equal to the number of `Underscore`s in the slicing coordinate.

## Partitioning a Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#partitioning-a-tensor "Link to this heading")

To implement generic partitioning of a `Tensor`, we apply composition or tiling followed by a slicing. This can be performed in many ways, but we have found three ways that are particularly useful: inner-partitioning, outer-partitioning, and TV-layout-partitioning.

### Inner and outer partitioning[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#inner-and-outer-partitioning "Link to this heading")

Let’s take a tiled example and look at how we can slice it in useful ways.

Tensor A \= make\_tensor(ptr, make\_shape(8,24));  // (8,24)
auto tiler \= Shape<\_4,\_8\>{};                    // (\_4,\_8)

Tensor tiled\_a \= zipped\_divide(A, tiler);       // ((\_4,\_8),(2,3))

Copy to clipboard

Suppose that we want to give each threadgroup one of these 4x8 tiles of data. Then we can use our threadgroup coordinate to index into the second mode.

Tensor cta\_a \= tiled\_a(make\_coord(\_,\_), make\_coord(blockIdx.x, blockIdx.y));  // (\_4,\_8)

Copy to clipboard

We call this an _inner-partition_ because it keeps the inner “tile” mode. This pattern of applying a tiler and then slicing out that tile by indexing into the remainder mode is common and has been wrapped into its own function `inner_partition(Tensor, Tiler, Coord)`. You’ll often see `local_tile(Tensor, Tiler, Coord)` which is just another name for `inner_partition`. The `local_tile` partitioner is very often applied at the threadgroup level to partition tensors into tiles across threadgroups.

Alternatively, suppose that we have 32 threads and want to give each thread one element of these 4x8 tiles of data. Then we can use our thread to index into the first mode.

Tensor thr\_a \= tiled\_a(threadIdx.x, make\_coord(\_,\_)); // (2,3)

Copy to clipboard

We call this an _outer-partition_ because it keeps the outer “rest” mode. This pattern of applying a tiler and then slicing into that tile by indexing into the tile mode is common and has been wrapped into its own function `outer_partition(Tensor, Tiler, Coord)`. Sometimes you’ll see `local_partition(Tensor, Layout, Idx)`, which is a rank-sensitive wrapper around `outer_partition` that transforms the `Idx` into a `Coord` using the inverse of the `Layout` and then constructs a `Tiler` with the same top-level shape of the `Layout`. This allows the user to ask for a row-major, column-major, or arbitrary layout of threads with a given shape that can be used to partition into a tensor.

To see how these partitioning patterns are used, see the [introductory GEMM tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html).

### Thread-Value partitioning[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#thread-value-partitioning "Link to this heading")

Another common partitioning strategy is called a thread-value partitioning. In this pattern, we construct a `Layout` that represents the mapping of all threads (or any parallel agent) and all values that each thread will receive to coordinates of the target data. With `composition` the target data layout is transformed according to our TV-layout and then we can simply slice into the thread-mode of the result with our thread index.

// Construct a TV-layout that maps 8 thread indices and 4 value indices
//   to 1D coordinates within a 4x8 tensor
// (T8,V4) -> (M4,N8)
auto tv\_layout \= Layout<Shape <Shape <\_2,\_4\>,Shape <\_2, \_2\>>,
                        Stride<Stride<\_8,\_1\>,Stride<\_4,\_16\>>>{}; // (8,4)

// Construct a 4x8 tensor with any layout
Tensor A \= make\_tensor<float\>(Shape<\_4,\_8\>{}, LayoutRight{});    // (4,8)
// Compose A with the tv\_layout to transform its shape and order
Tensor tv \= composition(A, tv\_layout);                           // (8,4)
// Slice so each thread has 4 values in the shape and order that the tv\_layout prescribes
Tensor  v \= tv(threadIdx.x, \_);                                  // (4)

Copy to clipboard

![tv_layout.png](https://docs.nvidia.com/cutlass/latest/_images/tv_layout.png)

The above image is a visual representation of the above code. An arbitrary 4x8 layout of data is composed with a specific 8x4 TV-layout that represents a partitioning pattern. The result of the composition is on the right where each threads’ values are arranged across each row. The bottom layout depicts the inverse TV layout which shows the mapping of 4x8 logical coordinates to the thread id and value id they will be mapped to.

To see how these partitioning patterns are constructed and used, see the [tutorial on building MMA Traits](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html).

## Examples[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#examples "Link to this heading")

### Copy a subtile from global memory to registers[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#copy-a-subtile-from-global-memory-to-registers "Link to this heading")

The following example copies rows of a matrix (with any `Layout`) from global memory to register memory, then executes some algorithm `do_something` on the row that lives in register memory.

Tensor gmem \= make\_tensor(ptr, make\_shape(Int<8\>{}, 16));  // (\_8,16)
Tensor rmem \= make\_tensor\_like(gmem(\_, 0));                // (\_8)
for (int j \= 0; j < size<1\>(gmem); ++j) {
  copy(gmem(\_, j), rmem);
  do\_something(rmem);
}

Copy to clipboard

This code does not need to know anything about the `Layout` of `gmem` other than that it is rank-2 and that the first mode has a static size. The following code checks both of those conditions at compile time.

CUTE\_STATIC\_ASSERT\_V(rank(gmem) \== Int<2\>{});
CUTE\_STATIC\_ASSERT\_V(is\_static<decltype(shape<0\>(gmem))\>{});

Copy to clipboard

Extending this example using the tiling utilities detailed in [the `Layout` algebra section](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/02_layout_algebra.html), we can copy an arbitrary subtile of a tensor using almost the same code as above.

Tensor gmem \= make\_tensor(ptr, make\_shape(24, 16));         // (24,16)

auto tiler         \= Shape<\_8,\_4\>{};                        // 8x4 tiler
//auto tiler       = Tile<Layout<\_8,\_3>, Layout<\_4,\_2>>{};  // 8x4 tiler with stride-3 and stride-2
Tensor gmem\_tiled  \= zipped\_divide(gmem, tiler);            // ((\_8,\_4),Rest)
Tensor rmem        \= make\_tensor\_like(gmem\_tiled(\_, 0));    // ((\_8,\_4))
for (int j \= 0; j < size<1\>(gmem\_tiled); ++j) {
  copy(gmem\_tiled(\_, j), rmem);
  do\_something(rmem);
}

Copy to clipboard

This applies a statically shaped `Tiler` to the global memory `Tensor`, creates a register `Tensor` that is compatible with the shape of that tile, then loops through each tile to copy it into memory and `do_something`.

## Summary[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html#summary "Link to this heading")

-   `Tensor` is defined as an `Engine` and a `Layout`.
    
    -   `Engine` is an iterator that can be offset and dereferenced.
    -   `Layout` defines the logical domain of the tensor and maps coordinates to offsets.
-   Tile a `Tensor` using the same methods for tiling `Layout`s.
-   Slice a `Tensor` to retrieve subtensors.
-   Partitioning is tiling and/or composition followed by slicing.
# CuTe Tensor algorithms[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#cute-tensor-algorithms "Link to this heading")

This section summarizes the interfaces and implementations of common numerical algorithms performed on `Tensor`s.

The implementation of these algorithms may be found in the [include/cute/algorithm/](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm/) directory.

## `copy`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#copy "Link to this heading")

CuTe’s `copy` algorithm copies the elements of a source `Tensor` into the elements of a destination `Tensor`. The various overloads of `copy` can be found in [`include/cute/algorithm/copy.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm/copy.hpp).

### Interface and specialization opportunities[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#interface-and-specialization-opportunities "Link to this heading")

A `Tensor` encapsulates the data type, data location, and possibly also the shape and stride of the tensor at compile time. As a result, `copy` can and does dispatch, based on the types of its arguments, to use any of various synchronous or asynchronous hardware copy instructions.

The `copy` algorithm has two main overloads. The first just takes the source `Tensor` and the destination `Tensor`.

template <class SrcEngine, class SrcLayout,
          class DstEngine, class DstLayout\>
CUTE\_HOST\_DEVICE
void
copy(Tensor<SrcEngine, SrcLayout\> const& src,
     Tensor<DstEngine, DstLayout\>      & dst);

Copy to clipboard

The second takes those two parameters, plus a `Copy_Atom`.

template <class... CopyArgs,
          class SrcEngine, class SrcLayout,
          class DstEngine, class DstLayout\>
CUTE\_HOST\_DEVICE
void
copy(Copy\_Atom<CopyArgs...\>       const& copy\_atom,
     Tensor<SrcEngine, SrcLayout\> const& src,
     Tensor<DstEngine, DstLayout\>      & dst);

Copy to clipboard

The two-parameter `copy` overload picks a default implementation based only on the types of the two `Tensor` parameters. The `Copy_Atom` overload lets callers override that default by specifying a nondefault `copy` implementation.

### Parallelism and synchronization depend on parameter types[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#parallelism-and-synchronization-depend-on-parameter-types "Link to this heading")

Either the default implementation or the implementation selected by a `Copy_Atom` overload may use none or all available parallelism, and may have a variety of synchronization semantics. The behavior depends on `copy`’s parameter types. Users are expected to figure this out based on their knowledge of the architecture on which they are running. (Developers often write a custom optimized kernel for each GPU architecture.)

The `copy` algorithm may be sequential per thread, or it may be parallel across some collection of threads (e.g., a block or cluster).

If `copy` is parallel, then the collection of participating threads may need synchronization before any thread in the collection may assume that the copy operation has completed. For example, if the participating threads form a thread block, then users must invoke `__syncthreads()` or the Cooperative Groups equivalent before they may use the results of `copy`.

The `copy` algorithm may use asynchronous copy instructions, such as `cp.async`, or its C++ interface `memcpy_async`. In that case, users will need to perform the additional synchronization appropriate to that underlying implementation before they may use the results of the `copy` algorithm. [The CuTe GEMM tutorial example](https://github.com/NVIDIA/cutlass/tree/main/examples/cute/tutorial/) shows one such synchronization method. More optimized GEMM implementations use pipelining techniques to overlap asynchronous `copy` operations with other useful work.

### A generic copy implementation[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#a-generic-copy-implementation "Link to this heading")

A simple example of a generic `copy` implementation for any two `Tensor`s looks like this.

template <class TA, class ALayout,
          class TB, class BLayout\>
CUTE\_HOST\_DEVICE
void
copy(Tensor<TA, ALayout\> const& src,  // Any logical shape
     Tensor<TB, BLayout\>      & dst)  // Any logical shape
{
  for (int i \= 0; i < size(dst); ++i) {
    dst(i) \= src(i);
  }
}

Copy to clipboard

This generic `copy` algorithm addresses both `Tensor`s with 1-D logical coordinates, thus traversing both `Tensor`s in a logical column-major order. Some reasonable architecture-independent optimizations would include the following.

1.  If the two `Tensor`s have known memory spaces with optimized access instructions (like `cp.async`), then dispatch to the custom instruction.
2.  The two `Tensor`s have static layouts and it can be proven that element vectorization is valid – for example, four `ld.global.b32`s can be combined into a single `ld.global.b128` – then vectorize the source and destinations tensors.
3.  If possible, validate that the copy instruction to be used is appropriate for the source and destination tensors.

CuTe’s optimized copy implementations can do all of these.

## `copy_if`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#copy-if "Link to this heading")

CuTe’s `copy_if` algorithm lives in the same header as `copy`, [`include/cute/algorithm/copy.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm/copy.hpp). The algorithm takes source and destination `Tensor` parameters like `copy`, but it also takes a “predication `Tensor`” with the same shape as the input and output. Elements of the source `Tensor` are only copied if the corresponding predication `Tensor` element is nonzero.

For details on why and how to use `copy_if`, please refer to the [“predication” section of the tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0y_predication.html).

## `gemm`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#gemm "Link to this heading")

### What `gemm` computes[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#what-gemm-computes "Link to this heading")

The `gemm` algorithm takes three `Tensor`s, A, B, and C. What it does depends on the number of modes that its `Tensor` parameters have. We express these modes using letters.

-   V indicates a “vector,” a mode of independent elements.
-   M and N indicate the number of rows resp. columns of the matrix result C of the BLAS’s GEMM routine.
-   K indicates the “reduction mode” of GEMM, that is, the mode along which GEMM sums. Please see the [GEMM tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html) for details.

We list the modes of the input `Tensor`s A and B, and the output `Tensor` C, using a notation `(...) x (...) => (...)`. The two leftmost `(...)` describe A and B (in that order), and the `(...)` to the right of the `=>` describes C.

1.  `(V) x (V) => (V)`. The element-wise product of vectors: Cv += Av Bv. Dispatches to FMA or MMA.
2.  `(M) x (N) => (M,N)`. The outer product of vectors: Cmn += Am Bn. Dispatches to (4) with V=1.
3.  `(M,K) x (N,K) => (M,N)`. The product of matrices: Cmn += Amk Bnk. Dispatches to (2) for each K.
4.  `(V,M) x (V,N) => (V,M,N)`. The batched outer product of vectors: Cvmn += Avm Bvn. Optimizes for register reuse and dispatches to (1) for each M, N.
5.  `(V,M,K) x (V,N,K) => (V,M,N)`. The batched product of matrices: Cvmn += Avmk Bvnk. Dispatches to (4) for each K.

Please refer to the [GEMM tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html) for an overview of CuTe’s convention for ordering the modes. For example, if K appears, it always appears rightmost (“outermost”). If V appears, it always appears leftmost (“innermost”).

### Dispatch to optimized implementations[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#dispatch-to-optimized-implementations "Link to this heading")

Just like with `copy`, CuTe’s implementations of `gemm` uses its `Tensor` arguments’ types to dispatch to an appropriately optimized implementation. Also like `copy`, `gemm` takes an optional `MMA_Atom` parameter that lets callers override the default `FMA` instruction that CuTe would select based on the `Tensor` arguments’ types.

For more information on `MMA_Atom` and on specialization of `gemm` for different architectures, please refer to the [MMA section of the tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html).

## `axpby`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#axpby "Link to this heading")

The `axpby` algorithm lives in the header file [`include/cute/algorithm/axpby.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm/axpby.hpp). It assigns to $y$ the result of $\\alpha x + \\beta y$, where $\\alpha$ and $\\beta$ are scalars and $x$ and $y$ are `Tensor`s. The name stands for “Alpha times X Plus Beta times Y,” and is a generalization of the original BLAS “AXPY” routine (“Alpha times X Plus Y”).

## `fill`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#fill "Link to this heading")

The `fill` algorithm lives in the header file [`include/cute/algorithm/fill.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm/fill.hpp). It overwrites the elements of its `Tensor` output argument with a given scalar value.

## `clear`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#clear "Link to this heading")

The `clear` algorithm lives in the header file [`include/cute/algorithm/clear.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm/clear.hpp). It overwrites the elements of its `Tensor` output argument with zeros.

## Other algorithms[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/04_algorithms.html#other-algorithms "Link to this heading")

CuTe provides other algorithms. Their header files can be found in the [`include/cute/algorithm`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/algorithm) directory.

# CuTe’s support for Matrix Multiply-Accumulate instructions[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#cute-s-support-for-matrix-multiply-accumulate-instructions "Link to this heading")

In this file, we explain in detail how we support our GPUs’ Matrix Multiply-Accumulate (MMA) hardware instructions in CuTe.

MMAs are architecture-specific. Different generations of GPU architectures introduce different sets of MMA instructions. However, CuTe features such as `Layout` makes it possible to expose MMAs for use in generic CUDA C++ code. We accomplish this in multiple steps.

1.  We wrap each MMA’s PTX instruction in an “Operation” struct.
2.  For each Operation struct, we define a “Traits” struct that defines all of the meta-information needed to use the Operation.
3.  Combining the above, an “Atom” is the combination of the PTX Operation struct with the meta-information Traits struct and provides methods to construct `cute::Tensor` “fragments” for that Operation and to use that Operation on existing `cute::Tensor`s.
4.  Combining potentially multiple Atoms, a “TiledMMA” provides utilities for building more complex partitioning patterns by creating layouts and interleavings of Atoms.

## CuTe MMA Atoms[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#cute-mma-atoms "Link to this heading")

CuTe exposes each MMA to generic CUDA C++ code as a pair of structs: an “Operation” struct, and an `MMA_Traits` struct templated on the Operation struct type.

An “Operation” struct exposes the PTX instruction for that specific operation. It defines the arguments and interface it expects. Operation structs have minimal software dependencies – they do not use layouts, tensors, or non-standard numeric data types – and describe only the physical inputs and outputs to the instruction. Different structs have different names that describe what the MMA instruction does. We will explain the naming scheme below.

A corresponding `MMA_Traits` struct specialization defines meta-information about the Operation, such as the logical compute types, the logical shape of the operation, and the `Layout`s of threads and values within the operation. The `MMA_Traits` struct takes the Operation as a template parameter. CuTe specializes `MMA_Traits` for each Operation type that it supports.

Together, these two types comprise an “Atom” that decouples the complexity of thread and data layouts from the call site of the PTX instruction. The Atom’s Traits struct exposes information that is relevant to a single MMA operation, no matter the granularity at which it operates.

CuTe MMA atoms expose the semantics of a single MMA operation. This is true regardless of the hardware level at which the MMA operates. CuTe supports MMA atoms that operate at a variety of hardware levels, including

-   a single thread (e.g., fused multiply-add (FMA) instruction);
-   a quadpair (Volta);
-   a single warp (Ampere); and
-   a warpgroup (Hopper).

### Operation structs[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#operation-structs "Link to this heading")

#### Location of files[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#location-of-files "Link to this heading")

CuTe provides its Operations structs in the [`include/cute/arch`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/arch) directory, in header files starting with `mma`.

#### Operation struct’s name[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#operation-struct-s-name "Link to this heading")

A CuTe Operation struct’s name principally encodes the PTX instruction it wraps. These often include

-   its first supported architecture,
-   the M, N, and K dimensions that it accepts,
-   the types that it takes, and
-   the arrangement of the A and B inputs.

For example, the Volta section below will refer to the `SM70_8x8x4_F32F16F16F32_NT` Operation struct defined in [`include/cute/arch/mma_sm70.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/arch/mma_sm70.hpp).

-   “SM70” refers to Volta.
-   “8x8x4” refers to M = 8, N = 8, and K = 4, the dimensions of the MMA operation that the quadpair performs (see below). This is reflected in the PTX as `.m8n8k4.`.
-   “F32F16F16F32” refers to the element types of the four matrix operands A, B, C, and D. An MMA computes D = C + A \* B, so we read the types from left to right: D is F32 (`float`), A is F16 (half), B is F16 (half), and C is F32 (`float`). This is reflected in the PTX instruction name as `.f32.f16.f16.f32`.
-   “NT” means that the PTX instruction is designed for inputs A as M-major (not transposed, column-major) and inputs B as N-major (transposed, row-major). This is reflected in the PTX instruction name as `.col.row.`.

#### Contents[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#contents "Link to this heading")

An Operation struct has the following members.

##### Type aliases[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#type-aliases "Link to this heading")

An Operation struct has four public type aliases: `DRegisters`, `ARegisters`, `BRegisters`, and `CRegisters`. For example, the `SM70_8x8x4_F32F16F16F32_NT` Operation struct defined in [`include/cute/arch/mma_sm70.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/arch/mma_sm70.hpp) defines these as follows.

using DRegisters \= float\[8\];
using ARegisters \= uint32\_t\[2\];
using BRegisters \= uint32\_t\[2\];
using CRegisters \= float\[8\];

Copy to clipboard

This shows how many values each thread will pass into the PTX instruction for each of the matrices A, B, C, and D. For this Operation, each thread passes 8 F32 values each for C and D (hence `float[8]`), and 4 F16 values each for A and B (hence `uint32_t[2]`; the instruction packs two 16-bit F16 values in each of the two 32-bit `uint32_t` values).

##### `fma` static member device function[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#fma-static-member-device-function "Link to this heading")

An operation struct defines a public `static void fma` function. It is marked with the `CUTE_HOST_DEVICE` macro, which adds the `__host__ __device__` annotations. Different Operations define `fma` to take different numbers of arguments, depending on the PTX MMA instruction. The implementation protects use of the PTX instruction with a macro, and raises an `assert` if `fma` is called when the macro is not defined. This ensures that tests and examples that use this Operation in an Atom can still compile, even if the PTX instruction is not available.

### Traits[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#traits "Link to this heading")

#### Location of files[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#id1 "Link to this heading")

CuTe provides its Traits structs in the [`include/cute/atom`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/atom) directory, in header files starting with `mma_traits`.

#### Contents[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#id2 "Link to this heading")

An `MMA_Traits` specialization defines the following public type aliases.

-   `ValTypeD`: Logical compute type of the D matrix
-   `ValTypeA`: Logical compute type of the A matrix
-   `ValTypeB`: Logical compute type of the B matrix
-   `ValTypeC`: Logical compute type of the C matrix
-   `Shape_MNK`: Logical MxNxK shape of the MMA operation
-   `ThrID`: Logical thread mapping within the single MMA operation (specifying the thread, quadpair, warp, or warpgroup view)
-   `ALayout`: Mapping of (thread,value) pairs to coordinates in the MxK A matrix
-   `BLayout`: Mapping of (thread,value) pairs to coordinates in the NxK B matrix
-   `CLayout`: Mapping of (thread,value) pairs to coordinates in the MxN C matrix

#### Example[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#example "Link to this heading")

The specialization of MMA\_Traits for the `SM70_8x8x4_F32F16F16F32_NT` Operation lives in the header file [`include/cute/atom/mma_traits_sm70.hpp`](https://github.com/NVIDIA/cutlass/tree/main/include/cute/atom/mma_traits_sm70.hpp). It looks like this.

template <>
struct MMA\_Traits<SM70\_8x8x4\_F32F16F16F32\_NT\>
{
  using ValTypeD \= float;
  using ValTypeA \= half\_t;
  using ValTypeB \= half\_t;
  using ValTypeC \= float;

  using Shape\_MNK \= Shape<\_8,\_8,\_4\>;
  using ThrID   \= SM70\_QuadPair;
  using ALayout \= SM70\_8x4\_Col;
  using BLayout \= SM70\_8x4\_Col;
  using CLayout \= SM70\_8x8\_32b;
};

Copy to clipboard

The next section will explain these type aliases in detail.

## Volta[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#volta "Link to this heading")

This and the following sections show examples of how to construct MMA atoms. We don’t try to explain this for all GPU architectures and MMAs. Instead, we use selected examples to illustrate the process of developing new atoms.

Volta architecture implements an HMMA instruction where a group of 8 threads called a quadpair (QP) collaborate to share data and perform an 8x8x4 (fp32 or fp16) matrix multiply-accumulate. (since a warp is 32 threads wide, it would perform an MMA across 4 QPs for a tile size of 16x16x4).

We first take a look at how we would take the ISA semantics of thread and data partitioning for the HMMA instruction, and encode it in a Traits struct. The HMMA NT instruction has the thread-data layout:

![HMMA.8x8x4.NT.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.NT.png)

### Types[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#types "Link to this heading")

The HMMA NT above uses types:

  using ValTypeD \= float;
  using ValTypeA \= half\_t;
  using ValTypeB \= half\_t;
  using ValTypeC \= float;

Copy to clipboard

The rest of the `MMA_Traits` will be described in units of these types.

### Shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#shape "Link to this heading")

The HMMA NT above has shape 8x8x4:

  // Logical shape of the MMA
  using Shape\_MNK \= Shape <\_8,\_8,\_4\>;

Copy to clipboard

### Thread ID[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#thread-id "Link to this heading")

If the 32 threads in a warp are logically indexed by \[0 … 31\], then the above image contains threads \[0,1,2,3\]U\[16,17,18,19\]. These threads make up the 0th quadpair. We can write a thread mapping that maps eight logical thread ids \[0,1,2,3,4,5,6,7\] of the MMA to a quadpair thread index \[0,1,2,3\]U\[16,17,18,19\] of a warp. The layout function has 4 elements with a stride of 1 and 2 of those with a stride of 16. With this, we write a layout that represents a quadpair:

  // Mapping from (logical thread id) -> (thread idx)
  using ThrID \= Layout<Shape <\_4, \_2\>,
                       Stride<\_1,\_16\>>;

Copy to clipboard

Again, this layout function maps the logical thread id \[0,8) of the MMA operation onto the quadpair thread index \[0,4)U\[16,20) of a warp.

### Accumulator Mapping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#accumulator-mapping "Link to this heading")

Let us look at exactly how the 8 threads within a QP are mapped to the A, B and C matrices. For the C and D matrices, the above image is broken down a bit more below. On the left is shown the whole QP level view, and on the right is shown the values owned by just thread 0.

![HMMA.8x8x4.quadpair.C.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.quadpair.C.png)

The metainformation of this single instruction level view is what we want to encode in CuTe. Specifically, the QP level view in this diagram corresponds to the four MMA traits for [SM70\_F32F16F16F32](https://github.com/NVIDIA/cutlass/tree/main/include/cute/arch/mma_sm70.hpp). These structs contain the `Element` types, the `Shape_MNK`, and the `ThrID` mapping we constructed above. Now, let us take a look at the definition of `CLayout`, the thread-data layout of accumulators. The job of `CLayout` is to construct a mapping between the `(logical_thr_id, logical_val_id)` and `(m, n)` coordinate in the C matrix which can then be used to build up more complicated layouts and operations like the 16x16x4 WMMA.

We can start constructing a `CLayout` from the picture above. As with any CuTe layout, it is a pair of `Shape` and corresponding `Stride`. Let us just look at the shape for now. We know that the HMMA uses 8 threads each of which own 8 values. Therefore, the shape of our mapping must have a size of 8 along two modes. With this, we have

  // (T8,V8) -> (m,n)
  using CLayout \= Layout<Shape <\_8, \_8\>,
                         Stride<\_?, \_?>;  // Stride to be filled in below

Copy to clipboard

This is not to be confused with the logical 8x8 shape of the C matrix. This is 8-threads by 8-values. We now want to map those to (m,n) coordinates. Since CuTe layouts return indices rather than coordinates, we choose a column-major encoding of the (m,n) coordinates:

(logical\_thr\_id, logical\_val\_id) \-> (m, n) == m + n \* M

Copy to clipboard

With this in place, we can start thinking about how to construct the strides in `CLayout`. Let’s begin by looking at the strides between threads. Note that

-   `(T0,V0)` is located at `(m,n) = (0,0) = 0`
-   `(T1,V0)` is located at `(m,n) = (1,0) = 1`
-   `(T2,V0)` is located at `(m,n) = (0,2) = 16`
-   `(T3,V0)` is located at `(m,n) = (1,2) = 17`
-   `(T4,V0)` is located at `(m,n) = (4,0) = 4`
-   `(T5,V0)` is located at `(m,n) = (5,0) = 5`
-   `(T6,V0)` is located at `(m,n) = (4,2) = 20`
-   `(T7,V0)` is located at `(m,n) = (5,2) = 21`

where `T4`,`T5`,`T6`,`T7` are the 4th,5th,6th,7th logical thread id of the MMA corresponding to thread indices of 16,17,18,19 of the warp (recorded in the `ThrID` mapping!).

We note that the pattern can be transcribed to a layout. We can find the position of the 8 threads via

  using CLayout \= Layout<Shape <Shape <\_2,  \_2, \_2\>, \_8\>,
                         Stride<Stride<\_1, \_16, \_4\>, \_?>;

Copy to clipboard

With the exact same approach, we can construct the stride along the `logical value id` mode.

-   `(T0,V0)` is located at `(m,n) = (0,0) = 0`
-   `(T0,V1)` is located at `(m,n) = (0,1) = 8`
-   `(T0,V2)` is located at `(m,n) = (2,0) = 2`
-   `(T0,V3)` is located at `(m,n) = (2,1) = 10`
-   `(T0,V4)` is located at `(m,n) = (0,4) = 32`
-   `(T0,V5)` is located at `(m,n) = (0,5) = 40`
-   `(T0,V6)` is located at `(m,n) = (2,4) = 34`
-   `(T0,V7)` is located at `(m,n) = (2,5) = 42`

We note that this pattern can also be transcribed to a layout. We can find the position of the 8 values via

  // (T8,V8) -> (m,n)
  using CLayout \= Layout<Shape <Shape <\_2, \_2,\_2\>, Shape <\_2,\_2, \_2\>>,
                         Stride<Stride<\_1,\_16,\_4\>, Stride<\_8,\_2,\_32\>>>;

Copy to clipboard

And that’s all! We can verify that each `(tid,vid)` coordinate in this layout is reliably mapped to the correct (encoded) `(m,n)` coordinate.

In the case of F16 accumulators, the layout is way less complex. Each row of accumulators `(m, :)` is held by a single thread, which makes the layout:

  using CLayout \= Layout<Shape <\_8,\_8\>,
                         Stride<\_1,\_8\>>;

Copy to clipboard

### A and B Layout Mapping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#a-and-b-layout-mapping "Link to this heading")

A and B matrix layouts depend on whether the sources are transposed or not. The diagram below shows the thread ID to data ownership map for A and B matrices in the case of NT and TN transposes.

![HMMA.8x8x4.quadpair.AB.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.quadpair.AB.png)

Let’s look at the TN layout for A matrix first (right side in the diagram). Again, there are the same 8 logical threads, but each threads owns only 4 elements this time. The shape of `ALayout` will then be `Shape<_8, _4>`. As for the strides, we again need a similar mapping between `(m, k) == m + k * M`. Looking down the `M` mode, we go from `(T0, V0)` to `(T1, V0)` which is a stride of 1 for all 8 threads. For the `K` mode, as we go across, we go from `(T0, V0)` to `(T0, V1)`, which makes a stride of 8 for all 4 values. Therefore, the A layout is:

  // (T8,V4) -> (m,k)
  using ALayout \= Layout<Shape <\_8,\_4\>,
                         Stride<\_1,\_8\>>;

Copy to clipboard

Source B layout is constructed similarly for the TN HMMA, except that we want write it as `(N,K)` rather than `(K,N)` for convenience. For the strides, as we go across the `N` mode, we go from `(T0, V0)` to `(T1, V0)`, making this a stride of 1 for all 8 threads. As we go down the `K` mode, `(T0, V0)` to `(T0, V1)` which is a stride of 8 for all 4 values. So the B layout is the same as A:

  // (T8,V4) -> (n,k)
  using BLayout \= Layout<Shape <\_8,\_4\>,
                         Stride<\_1,\_8\>>;

Copy to clipboard

The layouts in the case of NT are a bit more complicated (left side of the diagram). Going down the `M` mode of `A`, we see the four values of `T0` first and then we see the four values of `T4`. This means we first have a stride of 1 for 4 values, followed by a stride of 4 from `T0` to `T4`. So we have two sub-strides along the `M` mode. For the `K` mode, as we go across, we simply increment the `thr_id`, keeping `val_id` the same, making the stride 8 for 4 threads. This makes the A layout:

  // (T8,V4) -> (m,k)
  using ALayout \= Layout<Shape <Shape <\_4,\_2\>,\_4\>,
                         Stride<Stride<\_8,\_4\>,\_1\>>;

Copy to clipboard

With the `(N,K)` ordering for B, the layout is the same.

  // (T8,V4) -> (n,k)
  using BLayout \= Layout<Shape <Shape <\_4,\_2\>,\_4\>,
                         Stride<Stride<\_8,\_4\>,\_1\>>;

Copy to clipboard

For the NN and TT transposes, they are simply combinations of the two layouts we have seen for A and B so far.

## Hopper[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#hopper "Link to this heading")

Now, we are ready to take a look at the much larger GMMA operation (Group MMA) first introduced with Hopper architecture. These MMA instructions operate at the granularity of 128 threads (4 warps), which are collectively referred to as a warpgroup.

### Thread ID[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#id3 "Link to this heading")

In the case of Hopper GMMAs, the thread IDs are assigned based on the simple 1D contiguous layout, which makes `thrID` trivial:

using ThrID \= Layout<\_128, \_1\>;

Copy to clipboard

### Accumulator Mapping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#id4 "Link to this heading")

Accumulators are mapped hierarchically in GMMA, starting from the concept of a core matrix and building up to a layout for the whole C matrix tile. Let’s look at this core matrix first. We only consider fp16 accumulators here, but extensions of fp32 accumulators as trivial as we will see later.

Each core matrix has the layout as shown in the diagram below. ![gmma_coremat_cd_fp16.png](https://docs.nvidia.com/cutlass/latest/_images/gmma_coremat_cd_fp16.png)

As in the Volta examples, the thread IDs are logical only, and which of the four warps they belong to in the warpgroup is not important.

Then GMMA tiles this core matrix first vertically along the M mode, and then repeats that column of core matrices along the N mode to construct the full MxN tile. This tiling is shown in the image below.

![gmma_wg_n_slice.png](https://docs.nvidia.com/cutlass/latest/_images/gmma_wg_n_slice.png)

With this image, we are again ready to start building the `CLayout` for `SM90_64x128x16_F16F16F16F16_TN` atom. Same as before, we are constructing a mapping between the `(logical_thr_id, logical_val_id) -> (m, n)` coordinate spaces.

To begin, let’s follow the first few threads and values. We immediately see that they are arranged along the `N`\-mode with pairs of values and four threads. This gives us

// (T128,V4) -> (M64,N8)
using CLayout \= Layout<Shape <Shape <  \_4, ...\>, Shape < \_2, ...\>>,
                       Stride<Stride<\_128, ...\>, Stride<\_64, ...\>>>;

Copy to clipboard

To complete the first 8x8 core matrix, the four threads repeat eight times down the `M`\-mode:

// (T128,V4) -> (M64,N8)
using CLayout \= Layout<Shape <Shape <  \_4, \_8, ...\>, Shape < \_2, ...\>>,
                       Stride<Stride<\_128, \_1, ...\>, Stride<\_64, ...\>>>;

Copy to clipboard

Then, as we go to the next core matrix, we wrap back again to `T0`, but this time to `(T0, V2)`.

// (T128,V4) -> (M64,N8)
using CLayout \= Layout<Shape <Shape <  \_4, \_8, ...\>, Shape < \_2, \_2\>>,
                       Stride<Stride<\_128, \_1, ...\>, Stride<\_64, \_8\>>>;

Copy to clipboard

Finally, we get this entire pattern repeating four times, once for each warp, down the `M`\-mode starting at `(m,n) = (16,0) = 16`, where four core matrices that belong to the same warp are stacked on top of each other. This makes the size of the final sub-mode of `thrID` 4 (there are four warps) with a stride of `16` (to take us to coordinate `(16,0) = 16`).

// (T128,V4) -> (M64,N8)
using CLayout \= Layout<Shape <Shape <  \_4, \_8,  \_4\>, Shape < \_2, \_2\>>,
                       Stride<Stride<\_128, \_1, \_16\>, Stride<\_64, \_8\>>>;

Copy to clipboard

This is the full `CLayout` for 64x8 accumulators. The GMMA instructions include 64xN variants with `N = [16,32,64,128,256]` where this 64x8 pattern is repeated giving each thread additional values. As this starts at `(m,n) = (0,8) = 512`, this is easy to account for in our `CLayout`. For example, the 64x128 `CLayout` is

// (T128,V64) -> (M64,N128)
using CLayout \= Layout<Shape <Shape <  \_4, \_8,  \_4\>, Shape < \_2, \_2,  \_16\>>,
                       Stride<Stride<\_128, \_1, \_16\>, Stride<\_64, \_8, \_512\>>>;

Copy to clipboard

where we see 16 copies of the 64x8 tile.

### A and B Layout Mapping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#id5 "Link to this heading")

GMMA atoms that consume A and B sources directly from shared memory are a bit interesting. The GMMA Descriptor is constructed on an entire tile of A and/or B data in shared memory rather than being partitioned by threads. That is, every thread sees the entire tile of data and the tile is not reordered so that the descriptor can be constructed on it. In `ALayout` form, this can be expressed

// (T128,V64x16) -> (M64,K16)
using ALayout \= Layout<Shape <\_128, Shape <\_64,\_16\>>,
                       Stride<  \_0, Stride< \_1,\_64\>>>;

Copy to clipboard

That is, all threads are mapped the to `(m,k) = (0,0) = 0` element and the values (and shape of the values) remains unchanged. The GMMA Descriptor Constructor can then inspect the `(M,K)` layout of this data and create an appropriate GMMA Descriptor or produce an error message saying the data is in an invalid layout for GMMA.

## `TiledMMA`s[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html#tiledmmas "Link to this heading")

We can make more complex patterns by combining and interleaving multiple atoms.

Let’s start with `SM70_8x8x4_F32F16F16F32_NT`.

MMA\_Atom mma \= MMA\_Atom<SM70\_8x8x4\_F32F16F16F32\_NT\>{};
print\_latex(mma);

Copy to clipboard

![HMMA.8x8x4.NT_Atom.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.NT_Atom.png)

The above is equivalent to

    TiledMMA mma \= make\_tiled\_mma(SM70\_8x8x4\_F32F16F16F32\_NT{},
                                  Layout<Shape<\_1,\_1,\_1\>>{},   // Layout of Atoms
                                  Tile<\_8,\_8,\_4\>{});           // Tiler
    print\_latex(mma);

Copy to clipboard

as it is a single atom and has a natural tile size of 8x8x4.

We can create an object akin to a WMMA by using four of these quadpair MMAs:

    TiledMMA mma \= make\_tiled\_mma(SM70\_8x8x4\_F32F16F16F32\_NT{},
                                  Layout<Shape <\_2,\_2\>,
                                         Stride<\_2,\_1\>>{});   // 2x2 n-major layout of Atoms
    print\_latex(mma);

Copy to clipboard

![HMMA.8x8x4.NT_2x2.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.NT_2x2.png) This `TiledMMA` replicates the `MMA_Atom` across threads as we can see the `T4` and `T8` and `T12` threads in the `C`\-matrix that were not used before. Each quadrant of the `C`\-matrix is a replica of the atom’s partitioning pattern for a new quadpair and this replication follows a `(2,2):(2,1)` layout.

The above represents a 16x16x4 MMA now, but we can immediately expand this “tile size” up to 32x32x4 instead:

    TiledMMA mma \= make\_tiled\_mma(SM70\_8x8x4\_F32F16F16F32\_NT{},
                                  Layout<Shape <\_2,\_2\>,
                                         Stride<\_2,\_1\>>{},  // 2x2 n-major layout of Atoms
                                  Tile<\_32,\_32,\_4\>{});      // 32x32x4 tiler
    print\_latex(mma);

Copy to clipboard

![HMMA.8x8x4.NT_2x2_32x32x4.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.NT_2x2_32x32x4.png) This `TiledMMA` replicates the previous `TiledMMA` across values instead of threads. We can see the `T0V8` and `T16V8` and `T8V8` values in the `C`\-matrix that were not used before. Each quadrant of the `C`\-matrix is a replica of the previous `TiledMMA`’s partitioning pattern for a new set of values.

Continuing, we see that there are eight values that `T0` receives from the `A`\-matrix. Those reads occur at coordinates

T0V0 => ( 0,0)
T0V1 => ( 1,0)
T0V2 => ( 2,0)
T0V3 => ( 3,0)
T0V4 => (16,0)
T0V5 => (17,0)
T0V6 => (18,0)
T0V7 => (19,0)

Copy to clipboard

which are separate, but we might prefer them to be next to each other. That is we would like to permute the `M`\-mode to create another valid `TiledMMA`.

    TiledMMA mma \= make\_tiled\_mma(SM70\_8x8x4\_F32F16F16F32\_NT{},
                                  Layout<Shape <\_2,\_2\>,
                                         Stride<\_2,\_1\>>{},       // 2x2 n-major layout of Atoms
                                  Tile<Layout<Shape <\_4,\_4,\_2\>,
                                              Stride<\_1,\_8,\_4\>>, // Permutation on M, size 32
                                       \_32,                      // Permutation on N, size 32 identity
                                       \_4\>{});                   // Permutation on K, size 4 identity
    print\_latex(mma);

Copy to clipboard

![HMMA.8x8x4.NT_2x2_32Mx32x4.png](https://docs.nvidia.com/cutlass/latest/_images/HMMA.8x8x4.NT_2x2_32Mx32x4.png)

That layout `(4,4,2):(1,8,4)` is read like a scatter permutation, telling the m-coords of the original image where to go in the new image.

old m-coord:  0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31
new m-coord:  0  1  2  3  8  9 10 11 16 17 18 19 24 25 26 27  4  5  6  7 12 13 14 15 20 21 22 23 28 29 30 31

Copy to clipboard

This permutes only the M-mode (in `A` and `C` accordingly) and brings the access of all threads to be contiguous in m-coordinates in the `A`\-matrix. This is convenient when designing layouts for shared memory or registers, for example. The MMA instructions contained within the image above are now effectively interleaved in the logical m-coordinates. Of course, permutations in the N-mode and K-mode are also valid.

To see how these `TiledMMA`s are used to partition data tensors, see the [`0x_gemm_tutorial.md`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html).

# CuTe dense matrix-matrix multiply tutorial[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#cute-dense-matrix-matrix-multiply-tutorial "Link to this heading")

In this section, we review [these examples](https://github.com/NVIDIA/cutlass/tree/main/examples/cute/tutorial/), which demonstrate a few self-contained, single-file dense matrix-matrix multiply implementations using only CuTe.

## `sgemm_1.cu`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#sgemm-1-cu "Link to this heading")

The simplest of the tutorial examples covers the basics of partitioning the global memory into tiles across the CTAs (also called threadblocks in CUDA), partitioning the data tiles across the threads of each CTA, and writing a mainloop using `cute::copy` and `cute::gemm`.

### High-level interface[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#high-level-interface "Link to this heading")

We’ll start with the kernel entry point `gemm_device` at the top of the file.

template <class ProblemShape, class CtaTiler,
          class TA, class AStride, class ASmemLayout, class AThreadLayout,
          class TB, class BStride, class BSmemLayout, class BThreadLayout,
          class TC, class CStride, class CSmemLayout, class CThreadLayout,
          class Alpha, class Beta\>
\_\_global\_\_ static
\_\_launch\_bounds\_\_(decltype(size(CThreadLayout{}))::value)
void
gemm\_device(ProblemShape shape\_MNK, CtaTiler cta\_tiler,
            TA const\* A, AStride dA, ASmemLayout sA\_layout, AThreadLayout tA,
            TB const\* B, BStride dB, BSmemLayout sB\_layout, BThreadLayout tB,
            TC      \* C, CStride dC, CSmemLayout          , CThreadLayout tC,
            Alpha alpha, Beta beta)

Copy to clipboard

There are many template parameters, let’s quickly review them and then go into more depth on their uses.

-   `ProblemShape`. The MxNxK problem shape of this matrix multiply.
-   `CtaTiler`. A CuTe [tiler concept](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/02_layout_algebra.html#composition-tilers) that determines how to extract a tile of data from the problem shape.
-   `TA const* A`, `TB const* B`, `TC* C`. The types and pointers to the A, B, and C data, respectively.
-   `AStride`, `BStride`, `CStride`. The layout strides corresponding to the `ProblemShape` for each A, B, and C.
-   `ASmemLayout`, `BSmemLayout`, `CSmemLayout`. The layouts, if needed, of shared memory to use for staging A-data, B-data, and C-data within each CTA.
-   `AThreadLayout`, `BThreadLayout`, `CThreadLayout`. The layouts of threads to be used in partitioning each stage.
-   `Alpha alpha`, `Beta beta`. The types and values of the scalar constants to compute GEMM: `C = alpha * A * B + beta * C`.

### The Full Tensors: Shapes, Strides, and Data[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#the-full-tensors-shapes-strides-and-data "Link to this heading")

Most GEMM interfaces list the matrices’ dimensions in the order M, N, K. CuTe also uses this convention, but packages them into a single `IntTuple`. In this example, they are dynamic values defined at the top of the `gemm_nt` and `gemm_tn` host functions that invoke the device kernel.

  // Define shapes (dynamic)
  auto M \= int(m);
  auto N \= int(n);
  auto K \= int(k);
  auto prob\_shape \= make\_shape(M, N, K);    // (M, N, K)

Copy to clipboard

Inside the kernel, the problem shape is checked against the preconditions and then used to construct each of the full matrices.

  // Preconditions
  CUTE\_STATIC\_ASSERT\_V(rank(shape\_MNK) \== Int<3\>{});                      // (M, N, K)

  CUTE\_STATIC\_ASSERT\_V(congruent(select<0,2\>(shape\_MNK), dA));            // dA strides for shape MK
  CUTE\_STATIC\_ASSERT\_V(congruent(select<1,2\>(shape\_MNK), dB));            // dB strides for shape NK
  CUTE\_STATIC\_ASSERT\_V(congruent(select<0,1\>(shape\_MNK), dC));            // dC strides for shape MN

  // Represent the full tensors
  Tensor mA \= make\_tensor(make\_gmem\_ptr(A), select<0,2\>(shape\_MNK), dA);  // (M,K)
  Tensor mB \= make\_tensor(make\_gmem\_ptr(B), select<1,2\>(shape\_MNK), dB);  // (N,K)
  Tensor mC \= make\_tensor(make\_gmem\_ptr(C), select<0,1\>(shape\_MNK), dC);  // (M,N)

Copy to clipboard

The appropriate modes of the `Shape` are selected to construct each of the tensors. The preconditions make sure that for every integer in the `Shape` there is a corresponding integer in the associated `Stride`.

Note that the comment after B says `(N,K)` rather than `(K,N)`. This means that B is treated as an NxK matrix instead of a KxN matrix as is typical within BLAS and most other matrix-matrix multiplications. CuTe follows the convention that the semantics of matrix modes is `(M,K)` for `A`, `(N,K)` for `B`, and `(M,N)` for `C`, which we try to record in comments everywhere.

For each of the `(M,K)`, `(N,K)`, and `(M,N)` tensors, the `gemm_nt` and `gemm_tn` construct the strides those tensors will use. In `gemm_nt` the strides are defined as

  // Define NT strides (mixed)
  auto dA \= make\_stride(Int<1\>{}, ldA);    // (dM, dK)
  auto dB \= make\_stride(Int<1\>{}, ldB);    // (dN, dK)
  auto dC \= make\_stride(Int<1\>{}, ldC);    // (dM, dN)

Copy to clipboard

and in `gemm_tn` the strides are defined as

  // Define TN strides (mixed)
  auto dA \= make\_stride(ldA, Int<1\>{});    // (dM, dK)
  auto dB \= make\_stride(ldB, Int<1\>{});    // (dN, dK)
  auto dC \= make\_stride(Int<1\>{}, ldC);    // (dM, dN)

Copy to clipboard

#### Aside: M-major, N-major, K-major[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#aside-m-major-n-major-k-major "Link to this heading")

We’ve found that the BLAS convention of using “non-transposed” (N) and “transposed” (T) flags in conjunction with the mode conventions of `MxK * KxN` to confuse the core issue of “what layout does this matrix use” and “in which mode does my matrix have a stride-1?”. Indeed, the answer to those questions can always be found by inspecting the CuTe `Layout`.

Instead of row-major or column-major (or Transposed and Not-Transposed), we have found it much more convenient to say that a matrix is “M-major” if it is stride-1 in the M-mode, “N-major” if it is stride-1 in the N-mode, or “K-major” if it is stride-1 in the K-mode. Furthermore, knowing that matrix multiply always performs a reduction in the K-mode, it is very convenient from a software perspective to always have the K-mode in the same place and adopt the mode convention `MxK * NxK`. Implementations will always reduce over the second mode (the K mode) of both input matrices and leads to cases where implementations can treat both input matrices the same way.

How do we translate this into the BLAS user’s experience?

| BLAS | A Majorness | A Layout | B Majorness | B Layout |
| --- | --- | --- | --- | --- |
| NT  | M-major | `(M,K):(1,ldA)` | N-major | `(N,K):(1,ldB)` |
| TN  | K-major | `(M,K):(ldA,1)` | K-major | `(N,K):(ldB,1)` |
| NN  | M-major | `(M,K):(1,ldA)` | K-major | `(N,K):(ldB,1)` |
| TT  | K-major | `(M,K):(ldA,1)` | N-major | `(N,K):(1,ldB)` |

Regardless, we’ll still use the BLAS “NT” and “TN” notations for high-level descriptions of kernels when it’s appropriate.

### CTA Partitioning[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#cta-partitioning "Link to this heading")

Now that we have the representations of the full matrices, it’s time to tile them and split up the work!

At the highest level, the work is distributed across CTAs. In principle, each CTA’s tile could come from the input tensors in many different ways. Many [CuTe `Tiler`s](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/02_layout_algebra.html#composition-tilers) could be used to tile the data, but for these cases it is sufficient to simply use the shape of the desired CTA tile.

  // Define CTA tile sizes (static)
  auto bM \= Int<128\>{};
  auto bN \= Int<128\>{};
  auto bK \= Int<  8\>{};
  auto cta\_tiler \= make\_shape(bM, bN, bK);  // (BLK\_M, BLK\_N, BLK\_K)

Copy to clipboard

Once the tiler has been defined, we can use it to tile and partition the tensors across the CTAs.

  // Get the appropriate blocks for this threadblock
  auto cta\_coord \= make\_coord(blockIdx.x, blockIdx.y, \_);              // (m,n,k)
  Tensor gA \= local\_tile(mA, cta\_tiler, cta\_coord, Step<\_1, X,\_1\>{});  // (BLK\_M,BLK\_K,k)
  Tensor gB \= local\_tile(mB, cta\_tiler, cta\_coord, Step< X,\_1,\_1\>{});  // (BLK\_N,BLK\_K,k)
  Tensor gC \= local\_tile(mC, cta\_tiler, cta\_coord, Step<\_1,\_1, X\>{});  // (BLK\_M,BLK\_N)

Copy to clipboard

First, the CTA coordinate is created.

-   The `m`\-coordinate of this tile is given by `blockIdx.x`.
-   The `n`\-coordinate of this tile is given by `blockIdx.y`.
-   The `k`\-coordinate of this tile is unspecified – we want all of the tiles in `K` so the coordinate is `_`, the `Underscore` value, to keep that mode.

Then, `local_tile` is used to remove the modes of the tiler and coord corresponding to the `X`s. That is, the `Step<_1, X,_1>` is just shorthand for

  // Use select<0,2> to use only the M- and K-modes of the tiler and coord
  Tensor gA \= local\_tile(mA, select<0,2\>(cta\_tiler), select<0,2\>(cta\_coord));

Copy to clipboard

This `local_tile` is simply shorthand for

1.  apply the tiler via [`zipped_divide`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/02_layout_algebra.html#zipped-tiled-flat-divides)

// ((BLK\_M,BLK\_K),(m,k))
Tensor gA\_mk \= zipped\_divide(mA, select<0,2\>(cta\_tiler));

Copy to clipboard

2.  apply the coord to the second mode, the “Rest” mode, to extract out the correct tiles for this CTA.

// (BLK\_M,BLK\_K,k)
Tensor gA \= gA\_mk(make\_coord(\_,\_), select<0,2\>(cta\_coord));

Copy to clipboard

Because the projections of the tiler and coord are symmetric and the two steps (apply a tiler and then slice into the rest-mode to produce a partition) are so common, they are wrapped together into the projective `local_tile` interface.

For tensor `A`, we are left with a rank-3 tensor of shape `(BLK_M,BLK_K,k)`. The first two modes are precisely the modes of the CTA tile and the last mode indexes over all of the tiles that will be reduced by this CTA. In the mainloop section below, this mode is iterated over via the `k_tile` loop.

### SMEM tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#smem-tensors "Link to this heading")

The shared memory layouts that are used to hold the tiles of data for A and B are also passed in as the parameters `ASmemLayout sA_layout` and `BSmemLayout sB_layout`.

These are defined in `gemm_nt` as

  // Define the smem layouts (static)
  auto sA \= make\_layout(make\_shape(bM, bK));   // (m,k) -> smem\_idx; m-major
  auto sB \= make\_layout(make\_shape(bN, bK));   // (n,k) -> smem\_idx; n-major

Copy to clipboard

which produces simple M-major and N-major layouts. In `gemm_tn` these are

  // Define the smem layouts (static)
  auto sA \= make\_layout(make\_shape(bM,bK), LayoutRight{});   // (m,k) -> smem\_idx; k-major
  auto sB \= make\_layout(make\_shape(bN,bK), LayoutRight{});   // (n,k) -> smem\_idx; k-major

Copy to clipboard

which produces simple K-major layouts.

As is evident, these smem layouts can be almost anything. Inside the kernel, they are checked for only two properties: the shared memory layouts are static and they are the same top-level shape as the `CtaTiler`.

  // Preconditions
  static\_assert(is\_static<ASmemLayout\>::value);
  static\_assert(is\_static<BSmemLayout\>::value);
  static\_assert(is\_static<CSmemLayout\>::value);

  CUTE\_STATIC\_ASSERT\_V(size<0\>(ASmemLayout{}) \== size<0\>(cta\_tiler));  // BLK\_M
  CUTE\_STATIC\_ASSERT\_V(size<0\>(CSmemLayout{}) \== size<0\>(cta\_tiler));  // BLK\_M
  CUTE\_STATIC\_ASSERT\_V(size<0\>(BSmemLayout{}) \== size<1\>(cta\_tiler));  // BLK\_N
  CUTE\_STATIC\_ASSERT\_V(size<1\>(CSmemLayout{}) \== size<1\>(cta\_tiler));  // BLK\_N
  CUTE\_STATIC\_ASSERT\_V(size<1\>(ASmemLayout{}) \== size<2\>(cta\_tiler));  // BLK\_K
  CUTE\_STATIC\_ASSERT\_V(size<1\>(BSmemLayout{}) \== size<2\>(cta\_tiler));  // BLK\_K

Copy to clipboard

Use of static layouts has a few advantages.

-   Static layouts let us statically allocate shared memory as shown below.
-   Static layouts are often more efficient and allow CuTe to dispatch to optimized implementations.
-   Static layouts makes it easier to prove correctness of the algorithm and provide checks like the above – the smem layout sizes are the same as the CTA tile sizes.

As stated, the shared memory layouts can be anything that satisfy those conditions. Optimizing kernels like these is often performed by finding a good shared memory layout that provides good access patterns for both the writes to and the reads from shared memory. This includes the ability to vectorize reads and writes as well as avoid shared memory bank conflicts.

With the static smem layouts, the `gemm_device` kernel can allocate the required shared memory and create the smem `Tensor`s.

  // Shared memory buffers
  \_\_shared\_\_ TA smemA\[cosize\_v<ASmemLayout\>\];
  \_\_shared\_\_ TB smemB\[cosize\_v<BSmemLayout\>\];
  Tensor sA \= make\_tensor(make\_smem\_ptr(smemA), sA\_layout);  // (BLK\_M,BLK\_K)
  Tensor sB \= make\_tensor(make\_smem\_ptr(smemB), sB\_layout);  // (BLK\_N,BLK\_K)

Copy to clipboard

Note how the shared memory allocation depends only on the data type and the layout. What’s a `cosize`? Because a `Layout` is a function, we can speak of its domain and codomain. The `size` of a layout is the size of its domain and the `cosize` of a layout is the size of its codomain. If we want to allocate an array for which all the offsets produced by a layout are valid, then we can use the `cosize` of the layout as the length of the array (in units of elements).

### Copy partitioning[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#copy-partitioning "Link to this heading")

The kernel now has tiles of global memory by applying the `CtaTiler` to the full tensors and it also has tiles of shared memory by allocating appropriately. We now want to create an efficient way to copy one tile of global memory to our tile of shared memory. A trivial way to do this would be to use a single thread and copy each element.

if (thread0()) {
  Tensor gA0 \= gA(\_,\_,0);  // (BLK\_M,BLK\_K), the 0th tile
  for (int i \= 0; i < size(sA); ++i) {
    sA(i) \= gA0(i);
  }
}

Copy to clipboard

This would work, but we have lots of threads to use inside this CTA, so let’s use them!

If we partition the two tiles of data across the threads in the CTA, then each thread can copy its own subtensor of data. There are lots of ways this partitioning could occur, however.

The `gemm_nt` function defines two layouts of _threads_ as

  // Define thread layouts (static)
  auto tA \= make\_layout(make\_shape(Int<32\>{},Int<8\>{}));   // (m,k) -> thr\_idx
  auto tB \= make\_layout(make\_shape(Int<32\>{},Int<8\>{}));   // (n,k) -> thr\_idx

Copy to clipboard

and the `gemm_tn` functions defines two layouts of _threads_ as

  // Define thread layouts (static)
  auto tA \= make\_layout(make\_shape(Int<32\>{},Int<8\>{}), LayoutRight{});  // (m,k) -> thr\_idx; k-major
  auto tB \= make\_layout(make\_shape(Int<32\>{},Int<8\>{}), LayoutRight{});  // (n,k) -> thr\_idx; k-major

Copy to clipboard

Both cases happen to use 32x8 threads, which will be used to partition a 128x8 tile of gmem and smem data into a 4x1 subtensor for each thread. The only difference here is that `gemm_nt` uses M-major and N-major threads to match the order of data in global memory and `gemm_tn` uses K-major threads to match the order of data in global memory.

Again, the conditions on the thread layouts are checked inside the kernel.

  static\_assert(is\_static<AThreadLayout\>::value);
  static\_assert(is\_static<BThreadLayout\>::value);

  CUTE\_STATIC\_ASSERT\_V(size(tA) \== size(tB));                          // NumThreads

  CUTE\_STATIC\_ASSERT\_V(size<0\>(cta\_tiler) % size<0\>(tA) \== Int<0\>{});  // BLK\_M / THR\_M
  CUTE\_STATIC\_ASSERT\_V(size<2\>(cta\_tiler) % size<1\>(tA) \== Int<0\>{});  // BLK\_K / THR\_K
  CUTE\_STATIC\_ASSERT\_V(size<1\>(cta\_tiler) % size<0\>(tB) \== Int<0\>{});  // BLK\_N / THR\_N
  CUTE\_STATIC\_ASSERT\_V(size<2\>(cta\_tiler) % size<1\>(tB) \== Int<0\>{});  // BLK\_K / THR\_K

Copy to clipboard

These thread layouts are then used to partition the global memory tensors data and shared memory tensors

  Tensor tAgA \= local\_partition(gA, tA, threadIdx.x);    // (THR\_M,THR\_K,k)
  Tensor tAsA \= local\_partition(sA, tA, threadIdx.x);    // (THR\_M,THR\_K)

  Tensor tBgB \= local\_partition(gB, tB, threadIdx.x);    // (THR\_N,THR\_K,k)
  Tensor tBsB \= local\_partition(sB, tB, threadIdx.x);    // (THR\_N,THR\_K)

  CUTE\_STATIC\_ASSERT\_V(size<0\>(tAgA) \== size<0\>(tAsA));  // THR\_M
  CUTE\_STATIC\_ASSERT\_V(size<1\>(tAgA) \== size<1\>(tAsA));  // THR\_K
  CUTE\_STATIC\_ASSERT\_V(size<0\>(tBgB) \== size<0\>(tBsB));  // THR\_N
  CUTE\_STATIC\_ASSERT\_V(size<1\>(tBgB) \== size<1\>(tBsB));  // THR\_K

Copy to clipboard

where `local_partition` is a lot like `local_tile`, except the coordinate slices into the tile-mode (the first mode) of the `zipped_divide` rather than the rest-mode (the second mode). That is, each thread gets one element of data assigned to it per thread tile and that thread tile is repeated to cover the entire data tile.

The naming convention `tAsA` is pretty typical across CuTe and CUTLASS. This is read as “Partitioning pattern `tA` applied to tensor `sA`”. In the next section, we’ll see a different partitioner applied to `sA` to produce `tCsA`. By applying the same partitioning pattern, `tA`, to tensors `sA` and `gA`, we preserve the _logical consistency_ of those tensors (checked by the assertions above) where logical elements between the two tensors correspond despite any differences in their data layouts. When used in `cute::copy`, for example, this naming convention let’s us lexically verify that the two tensors are using the same partitioning pattern.

With the data partitioned across the threads, _every thread_ can now participate in the copy by writing

copy(tAgA(\_,\_,0), tAsA);

Copy to clipboard

because every thread owns a different subtensor of the tile that will be copied.

### Math partitioning[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#math-partitioning "Link to this heading")

The kernel now has tiles of shared memory copied in from global memory. We now want to create an efficient way to compute and accumulate the matrix product on that tile of shared memory. A trivial way to do this would be to use a single thread and compute directly.

if (thread0()) {
  for (int m \= 0; m < size<0\>(gC); ++m) {
    for (int n \= 0; n < size<1\>(gC); ++n) {
      for (int k \= 0; k < size<1\>(sA); ++k) {
        gC(m,n) += sA(m,k) \* sB(n,k);
      }
    }
  }
}

Copy to clipboard

This would work, but we have lots of threads to use inside this CTA, so let’s use them!

If we partition the output tile `gC` across the threads in the CTA, then each thread can compute its own subtensor. There are lots of ways this partitioning could occur, however.

The `gemm_nt` and `gemm_tn` functions define one more layout of _threads_:

  // Define thread layouts (static)
  auto tC \= make\_layout(make\_shape(Int<16\>{}, Int<16\>{}));   // (m,n) -> thr\_idx; m-major

Copy to clipboard

This is a m-major 16x16 layout of threads which will be used to partition a 128x128 tile of `C`\-data, resulting in each thread computing its own 8x8 subtensor of `gC`.

Again, the conditions on the thread layouts are checked inside the kernel.

  static\_assert(is\_static<CThreadLayout\>::value);

  CUTE\_STATIC\_ASSERT\_V(size(tC) \== size(tA));                          // NumThreads

  CUTE\_STATIC\_ASSERT\_V(size<0\>(cta\_tiler) % size<0\>(tC) \== Int<0\>{});  // BLK\_M / THR\_M
  CUTE\_STATIC\_ASSERT\_V(size<1\>(cta\_tiler) % size<1\>(tC) \== Int<0\>{});  // BLK\_N / THR\_N

Copy to clipboard

These thread layouts are then used to partition the tiles of data in global memory and shared memory

  // Partition sA (M,K) by the rows of tC
  Tensor tCsA \= local\_partition(sA, tC, threadIdx.x, Step<\_1, X\>{});   // (THR\_M,BLK\_K)
  // Partition sB (N,K) by the cols of tC
  Tensor tCsB \= local\_partition(sB, tC, threadIdx.x, Step< X,\_1\>{});   // (THR\_N,BLK\_K)
  // Partition gC (M,N) by the tile of tC
  Tensor tCgC \= local\_partition(gC, tC, threadIdx.x, Step<\_1,\_1\>{});   // (THR\_M,THR\_N)

  // Allocate the accumulators -- same shape/layout as the partitioned data
  Tensor tCrC \= make\_tensor\_like(tCgC);                                // (THR\_M,THR\_N)

  CUTE\_STATIC\_ASSERT\_V(size<0\>(tCrC) \== size<0\>(tCgC));                // THR\_M
  CUTE\_STATIC\_ASSERT\_V(size<0\>(tCrC) \== size<0\>(tCsA));                // THR\_M
  CUTE\_STATIC\_ASSERT\_V(size<1\>(tCrC) \== size<1\>(tCgC));                // THR\_N
  CUTE\_STATIC\_ASSERT\_V(size<1\>(tCrC) \== size<0\>(tCsB));                // THR\_N
  CUTE\_STATIC\_ASSERT\_V(size<1\>(tCsA) \== size<1\>(tCsB));                // BLK\_K

Copy to clipboard

where we’ve used the same projection-style interface to avoid applying the `N`\-mode of `tC` to the `(BLK_M,BLK_K)` shape of `sA` and avoid applying the `M`\-mode of `tC` to the `(BLK_N,BLK_K)` shape of `sB`.

![tC_partitioning.png](https://docs.nvidia.com/cutlass/latest/_images/tC_partitioning.png) This diagram shows a `tC` layout, highlights two threads in green and blue, shows the projections of the `tC` layout, and finally highlights the subtensors within `sA`, `sB`, and `gC` that `tCsA`, `tCsB`, and `tCgC` represent.

With the data partitioned across the threads, _every thread_ can now participate in the compute step by writing

gemm(tCsA, tCsB, tCrC);

Copy to clipboard

because every thread owns different subtensors of the data to be computed.

### Mainloop[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#mainloop "Link to this heading")

The mainloop iterates over tiles of global memory, reads those tiles into shared memory, and then performs the matrix-multiply and accumulates into the accumulators.

// TUTORIAL: Example of a very simple compute mainloop
//   copy(.) operates on the global and shared memory via the tA|tB partitioning
//   gemm(.) operates on the shared and register memory via the tC partitioning

auto K\_TILE\_MAX \= size<2\>(tAgA);

for (int k\_tile \= 0; k\_tile < K\_TILE\_MAX; ++k\_tile)
{
  // Copy gmem to smem with tA|tB thread-partitioned tensors
  copy(tAgA(\_,\_,k\_tile), tAsA);      // A   (THR\_M,THR\_K) -> (THR\_M,THR\_K)
  copy(tBgB(\_,\_,k\_tile), tBsB);      // B   (THR\_N,THR\_K) -> (THR\_N,THR\_K)

  cp\_async\_fence();        // Label the end of (potential) cp.async instructions
  cp\_async\_wait<0\>();      // Sync on all (potential) cp.async instructions
  \_\_syncthreads();         // Wait for all threads to write to smem

  // Compute gemm on tC thread-partitioned smem
  gemm(tCsA, tCsB, tCrC);            // (THR\_M,THR\_N) += (THR\_M,BLK\_K) \* (THR\_N,BLK\_K)
  \_\_syncthreads();         // Wait for all threads to read from smem
}

Copy to clipboard

We can see that `k_tile` iterates over each tile of data, the `cute::copy` is performed for the current `k_tile` using the `tA` and `tB` thread-partitioned tensors, and the `cute::gemm` is computed for that current `k_tile` using the `tC` thread-partitioned tensors. Synchronization is provided so that this kernel works on any architecture.

## `sgemm_2.cu`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#sgemm-2-cu "Link to this heading")

An example that uses more complex `TiledMMA` and `TiledCopy` to perform partitioning in place of the `tA`, `tB`, and `tC` thread layouts. With this example, we try to emphasize that the shared memory layouts, the partitioning patterns, and the PTX instruction to use in each stage can be specified independently.

### TiledCopy[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#tiledcopy "Link to this heading")

First, we can replace the `tA` partitioning and `tB` partitioning with `TiledCopy` partitioning, which provides for more complex partitioning patterns and checked dispatch to specific copy instructions.

As a first example, lets look at the `TiledCopy` that `gemm_nt` generates.

  TiledCopy copyA \= make\_tiled\_copy(Copy\_Atom<UniversalCopy<uint128\_t\>, TA\>{},  // Atom: Copy TAs as if they were uint128\_t
                                    Layout<Shape<\_32,\_8\>>{},                    // Thr layout 32x8 m-major
                                    Layout<Shape< \_4,\_1\>>{});                   // Val layout  4x1 m-major
  print\_latex(copyA);

Copy to clipboard

The easiest way to see what this `TiledCopy` does is to look at the partition pattern in LaTeX. ![TiledCopyA.png](https://docs.nvidia.com/cutlass/latest/_images/TiledCopyA.png) On the left is the source-tensor partitioning and on the right is the destination-tensor partitioning. The partition patterns are the same for this case, but there exist PTX instructions which require different patterns in the source and destination. The diagram shows that each thread reads 4x1 `TA` elements and there are 32x8 threads. The `UniversalCopy<uint128_t>` forces the instruction to use a 128-bit copy instruction. If the partition (of `sA` or `gA` in this case) does not result in 4 `TA` elements that cannot be vectorized to a 128-bit load/store, then CuTe will statically fail with an error message to that effect.

To use the `TiledCopy`, the kernel writes

  ThrCopy thr\_copy\_a \= copy\_a.get\_slice(threadIdx.x);
  Tensor tAgA \= thr\_copy\_a.partition\_S(gA);            // (CPY,CPY\_M,CPY\_K,k)
  Tensor tAsA \= thr\_copy\_a.partition\_D(sA);            // (CPY,CPY\_M,CPY\_K)
  // Allocate registers same shape/layout as partitioned data
  Tensor tArA \= make\_fragment\_like(tAsA);              // (CPY,CPY\_M,CPY\_K)

Copy to clipboard

which applies the source-tensor partitioning to `gA` via `partition_S` and applies the destination-tensor partitioning to `sA` via `partition_D`. The first mode, `CPY`, of the result tensors hold all of the elements that a single instruction will consume. In this case, that mode should have size-4 since there are four `TA=float` elements in a single 128-bit `uint128_t`.

Once the partition has been performed, we can execute the `copy` on the thread-partitioned tensors using the provided instruction in `copy_a`.

cute::copy(copy\_a, tAgA, tArA);

Copy to clipboard

### TiledMMA[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#tiledmma "Link to this heading")

Next, we can replace the `tC` partitioning with `TiledMMA` partitioning, which provides for more complex partitioning patterns and checked dispatch to specific MMA instructions.

As a first example, lets look at the `TiledMMA` that `gemm_nt` generates.

  TiledMMA mmaC \= make\_tiled\_mma(UniversalFMA<TC,TA,TB\>{},
                                 Layout<Shape<\_16,\_16,\_1\>>{});  // 16x16x1 UniversalFMA
  print\_latex(mmaC);

Copy to clipboard

The easiest way to see what this `TiledMMA` does is to look at the partition pattern in LaTeX. ![TiledMmaC.png](https://docs.nvidia.com/cutlass/latest/_images/TiledMmaC.png) On the left is the A-tensor partitioning, on the top is the B-tensor partitioning, and in the middle is the C-tensor partitioning.Because the `UniversalFMA` is a 1x1x1 MMA instruction, a 16x16x1 tiling of them results in a 16x16x1 `TiledMMA`. Other MMA instructions will have different threads involved and have different instruction sizes. In this case, all threads will read a single element from `A`, `B`, and `C` each.

To use the `TiledMMA`, the kernel writes

  ThrMMA thr\_mma \= mma.get\_slice(threadIdx.x);
  Tensor tCsA \= thr\_mma.partition\_A(sA);        // (MMA,MMA\_M,MMA\_K)
  Tensor tCsB \= thr\_mma.partition\_B(sB);        // (MMA,MMA\_N,MMA\_K)
  Tensor tCgC \= thr\_mma.partition\_C(gC);        // (MMA,MMA\_M,MMA\_N)
  // Allocate the accumulators -- same size as the projected data
  Tensor tCrC \= thr\_mma.make\_fragment\_C(tCgC);  // (MMA,MMA\_M,MMA\_N)

Copy to clipboard

which applies the A-tensor partitioning to `sA` via `partition_A`, applies the B-tensor partitioning to `sB` via `partition_B`, and applies the C-tensor partitioning to `gC` via `partition_C`. The first mode, `MMA`, of the result tensors hold all of the elements that a single instruction will consume. In this case, that mode should have size-1 since `UniversalFMA` is a 1x1x1 MMA, but in general the size of the first mode can vary and not even be the same across `tCsA`, `tCsB`, and `tCgC` depending on the MMA.

Once the partition has been performed, we can execute the `gemm` on the thread-partitioned tensors using the provided instruction in `mma`.

cute::gemm(mma, tCsA, tCsB, tCrC);

Copy to clipboard

### Other changes[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#other-changes "Link to this heading")

In this version, we have also updated the shared memory layouts for `gemm_tn` from K-major to

  // Define the smem layouts (static)
  auto sA \= make\_layout(make\_shape (      bM,          bK),
                        make\_stride(Int<1\>{}, bM+Int<1\>{}));  // (m,k) -> smem\_idx; padded m-major
  auto sB \= make\_layout(make\_shape (      bN,          bK),
                        make\_stride(Int<1\>{}, bN+Int<1\>{}));  // (n,k) -> smem\_idx; padded n-major

Copy to clipboard

which produces M-major and N-major layouts, but they are padded to avoid shared memory bank conflicts. This simply improves the access pattern to and from shared memory and no other changes in the kernel are required.

## `sgemm_sm70.cu`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#sgemm-sm70-cu "Link to this heading")

An example that uses an optimized mainloop for Volta SM70 architectures that pipelines shared memory and register memory.

## `sgemm_sm80.cu`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#sgemm-sm80-cu "Link to this heading")

An example that uses an optimized mainloop for Ampere SM80 architectures that explicitly pipelines shared memory using asynchronous reads from global memory.

## Next steps[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#next-steps "Link to this heading")

All of the above examples assume that the CTA tile size divides the problem size so that global memory loads do no need to be predicated. The [predication section of the tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0y_predication.html) explains what to do if a matrix tiling doesn’t perfectly divide the matrix.

## GETT as GEMM[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html#gett-as-gemm "Link to this heading")

“GETT” here stands for “general(ized) tensor times tensor,” a tensor contraction.

CuTe permits matrices to have nested `Layout`s. This means that we can fold a `Tensor` into a “matrix” by grouping modes according to their categories.

As a result, we can implement GETT by using our existing GEMM implementation. Included below is a launcher like `gemm_nt` that uses the same device kernel contained in `sgemm_1.cu` to compute a GETT with two m-modes.

// Setup params for a GETT with two m-modes.
// The A and C tensors are assumed to be m0-major.
//   Calls sgemm\_1.cu's gemm\_device<<<>>> without modification.
template <class TA, class TB, class TC,
          class Alpha, class Beta\>
void
gett(int m0, int m1, int n, int k,
     Alpha alpha,
     TA const\* A, int ldAm1, int ldAk,  // m0-major
     TB const\* B, int ldBk,
     Beta beta,
     TC      \* C, int ldCm1, int ldCn,  // m0-major
     cudaStream\_t stream \= 0)
{
  using namespace cute;

  // Define shapes (dynamic)
  auto M \= make\_shape(m0, m1);                               // (m0,m1)-multimode M
  auto N \= int(n);
  auto K \= int(k);
  auto prob\_shape \= make\_shape(M, N, K);                     // (M, N, K)

  // Define NT strides (mixed)
  auto dA \= make\_stride(make\_stride(Int<1\>{}, ldAm1), ldAk); // (dM, dK)
  auto dB \= make\_stride(Int<1\>{}, ldB);                      // (dN, dK)
  auto dC \= make\_stride(make\_stride(Int<1\>{}, ldCm1), ldCn); // (dM, dN)

  // Define CTA tile sizes (static)
  auto bM \= Shape<\_64, \_2\>{};    // Take \_64 elements from m0 and \_2 elements from m1
  auto bN \= Int<128\>{};
  auto bK \= Int<  8\>{};
  auto cta\_tiler \= make\_shape(bM, bN, bK);                   // (BLK\_M, BLK\_N, BLK\_K)

  // Define the smem layouts (static)
  auto sA \= make\_layout(make\_shape(bM, bK));                 // (m,k) -> smem\_idx; m-major
  auto sB \= make\_layout(make\_shape(bN, bK));                 // (n,k) -> smem\_idx; n-major
  auto sC \= make\_layout(make\_shape(bM, bN));                 // (m,n) -> smem\_idx; m-major

  // Define the thread layouts (static)
  auto tA \= make\_layout(make\_shape(Int<32\>{}, Int< 8\>{}));   // (m,k) -> thr\_idx
  auto tB \= make\_layout(make\_shape(Int<32\>{}, Int< 8\>{}));   // (n,k) -> thr\_idx
  auto tC \= make\_layout(make\_shape(Int<16\>{}, Int<16\>{}));   // (m,n) -> thr\_idx

  dim3 dimBlock(size(tC));
  dim3 dimGrid(size(ceil\_div(M, bM)),
               size(ceil\_div(N, bN)));
  gemm\_device<<<dimGrid, dimBlock, 0, stream\>>>
      (prob\_shape, cta\_tiler,
       A, dA, sA, tA,
       B, dB, sB, tB,
       C, dC, sC, tC,
       alpha, beta);
}

Copy to clipboard

Note that the only changes are the definition of shape `M`, the definition of strides `dA` and `dC`, and the definition of the CTA Tiler `bM`. The above uses a multimodel problem shape `M = (m0,m1)` and a multimodal CTA Tiler `bM = <_64,_2>` to change which portion of the global memory tensors `A` and `C` each CTA will be responsible for computing.

Similar examples can be found for CUTLASS 3.x kernels that are based on CuTe, such as [this Hopper GETT example](https://github.com/NVIDIA/cutlass/tree/main/examples/51_hopper_gett).

# Predication: What to do when tiling isn’t perfect[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0y_predication.html#predication-what-to-do-when-tiling-isn-t-perfect "Link to this heading")

The [GEMM tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html) shows how we compute a matrix-matrix multiply by iterating over tiles of the input matrices and output matrix. The examples all assume that the tiles fit evenly into the matrices, with no remainder. What do we do if this is not the case? For example, we might want to tile a 41 x 55 matrix into 4 x 8 tiles, but 41 / 4 is 10 remainder 1, and 55 / 8 is 6 remainder 7. What do we do with those “leftover” parts of the matrix?

To start, we note that `logical_divide` (CuTe’s way of tiling layouts) “rounds up.” For example, if `N` is the layout `1000:1` and `B` is the layout `128:1`, then `logical_divide(N, B)` is the layout `(128, 8):(1, 128)`. This effectively rounds up the original shape `N = 1000` into an `128 x 8` matrix (as if `N = 1024`). What about those last 24 elements, that aren’t part of the original data? How is the last tile handled and how do we avoid indexing out-of-bounds?

Like other introductions to CUDA programming, the idiomatic CuTe way to address these issues is through “predication.” Rather than attempting to reason about the “remainder tiles” by trying to represent “7 tiles of size-128 and 1 tile of size-104,” CuTe instead rounds up to “8 tiles of size-128” and constructs predicates so that the kernel only tries to access data in each tile that are valid within the matrix. This corresponds well with how our GPUs optimize: branches without warp divergence are relatively fast. It also matches the usual CUDA idiom when dividing N work items in 1-D fashion over B thread blocks: first test if “my thread” is out of bounds before doing work.

Consider a generic tiling wherein a size-1000 vector is tiled into size-128 chunks. Then a predication tensor can be constructed as follows:

Tensor gmem \= ...     // e.g. size 1000
Tensor smem \= ...     // e.g. size 128

// Tile the gmem for smem
Tensor gmem\_tiled \= logical\_divide(gmem, size(smem));      // e.g. (128,8)

// Create an identity layout for gmem and tile it similarly
Layout id\_layout \= make\_layout(shape(gmem));               // e.g. 1000:1, explicitly constructed as identity function
Layout id\_tiled  \= logical\_divide(id\_layout, size(smem));  // e.g. (128,8):(1,128), but many elements aren't "valid"

// Create a predicate tensor
Tensor pred \= make\_tensor<bool\>(shape(id\_tiled));          // e.g. (128,8)
for (int i \= 0; i < size(pred); ++i) {
  pred(i) \= id\_tiled(i) < size(id\_layout);  // Predicate: Is the offset within the original shape?
}

// ... intervening code ...

// Note that gmem\_tiled, id\_tiled, and pred tensors are all congruent
// For tile tile\_i, determine if element value\_j is in-bounds and copy to smem
if (pred(value\_j,tile\_i)) { smem(value\_j) \= gmem\_tiled(value\_j,tile\_i); }

Copy to clipboard

The general procedure is that we

1.  create an “identity” layout (`Layout id_layout = make_layout(shape(gmem))`, in the above example) with the same shape as our original data;
2.  repeat the same tiling/partitioning/slicing (possibly rounding up) on that identity layout (`Layout id_tiled  = logical_divide(id_layout, size(smem));`);
3.  create a “predicate tensor” by comparing the coordinates of that reference layout with the bounds of the original layout; and then
4.  use the predicate tensor to mask off accesses to out-of-bounds elements.

As a relatively simple example, consider predicating the epilogue of a GEMM. Suppose that we’ve partitioned `mC` into cta tiles and across threads of an mma as follows.

// CTA partitioning
auto cta\_coord \= make\_coord(blockIdx.x, blockIdx.y, \_);              // (m,n,k)
Tensor gC \= local\_tile(mC, cta\_tiler, cta\_coord, Step<\_1,\_1, X\>{});  // (BLK\_M,BLK\_N)

// Thread partitioning
auto thr\_mma \= mma.get\_slice(threadIdx.x);
Tensor tCgC \= thr\_mma.partition\_C(gC);                               // (MMA,MMA\_M,MMA\_N)
Tensor tCrC \= thr\_mma.make\_fragment\_C(tCgC);                         // (MMA,MMA\_M,MMA\_N)

// ... Compute gemms and accumulate into tCrC ...

// axpby epilogue
for (int i \= 0; i < size(tCgC); ++i) {
  tCgC(i) \= alpha \* tCrC(i) + beta \* tCgC(i);
}

Copy to clipboard

Then, following the predication procedure is straightforward,

// A coordinate tensor the same shape as mC: (m,n) -> (m,n)
Tensor cC     \= make\_identity\_tensor(shape(mC));

// Repeat partitioning steps applied to mC to our coordinate tensor cC
// CTA partitioning
Tensor cta\_cC \= local\_tile(cC, cta\_tiler, cta\_coord, Step<\_1,\_1, X\>{});  // (BLK\_M,BLK\_N) -> (m,n)
// Thread partitioning
Tensor tCcC   \= thr\_mma.partition\_C(cta\_cC);                             // (MMA,MMA\_M,MMA\_N) -> (m,n)

// Predicated axpby epilogue
for (int i \= 0; i < size(tCgC); ++i) {
  if (elem\_less(tCcC(i), shape(mC))) {  // if coord is in-bounds
    tCgC(i) \= alpha \* tCrC(i) + beta \* tCgC(i);
  }
}

Copy to clipboard

Above, the cta is responsible for tiling/partitioning `mC` and the mma is responsible for tiling/partitioning `gC`, so both steps are also applied to the identity tensor. The coordinate tensor `tCcC` is congruent with the register fragment `tCrC` and the partitioned global memory tensor `tCgC`, which are this threads’ subtensors of the tile of data. However, the `tCcC` tensor retains it’s original codomain when evaluated: a global coordinate into the original tensor `mC`. This global coordinate is compared to the shape of `mC` to determine validity of the operation.

Advantages of this “reference identity tensor” or “coordinate tensor” approach include:

1.  There is no dependence on the layout/strides of the tensor being predicated, just the logical bounds imposed.
2.  The partitioning stage(s) can be anything. A CTA tiling, a thread partitioning, a TiledMMA, and a TiledCopy can all be applied to any tensor, including a coordinate tensor.
3.  It naturally extends to any-dimensional predication.
4.  It’s a natural generalization of a typical CUDA 1-D parallel vector access pattern, which computes an access index `idx` and predicates access to the vector’s `idx`\-th element, determining if `idx` is in-bounds.

int idx \= blockDim.x \* blockIdx.x + threadIdx.x;
if (idx < N)  // idx is a "coord" into gmem and N is the "bound"
  gmem\_ptr\[idx\] \= ...;

Copy to clipboard

In a SIMT programming model, the tensor extents should not be modified so that loops don’t overrun. Instead, predication is a general method to query the original coordinate and determine if that coordinate overruns. This avoids variable/dynamic loop bounds in favor of instruction-level predication, preservation of thread coherence, and maintaining load balance. It’s also general enough to extend to all ranks, all layouts of threads and data, and all tiling/partitioning patterns. Assumptions can be built into the coordinate tensors or the predicate tensors to account for special cases.

As another slightly more complex example, consider the m- and n-predication of A and B loads in a GEMM. Suppose that we’ve partitioned A and B tiles across ctas and threads as follows.

// CTA partitioning
auto cta\_coord \= make\_coord(blockIdx.x, blockIdx.y, \_);              // (m,n,k)
Tensor gA \= local\_tile(mA, cta\_tiler, cta\_coord, Step<\_1, X,\_1\>{});  // (BLK\_M,BLK\_K,k)
Tensor gB \= local\_tile(mB, cta\_tiler, cta\_coord, Step< X,\_1,\_1\>{});  // (BLK\_N,BLK\_K,k)

Tensor sA \= make\_tensor(make\_smem\_ptr(smemA), sA\_layout);            // (BLK\_M,BLK\_K)
Tensor sB \= make\_tensor(make\_smem\_ptr(smemB), sB\_layout);            // (BLK\_N,BLK\_K)

// Thread partitioning
Tensor tAgA \= local\_partition(gA, tA, thread\_idx);                   // (THR\_M,THR\_K,k)
Tensor tAsA \= local\_partition(sA, tA, thread\_idx);                   // (THR\_M,THR\_K)

Tensor tBgB \= local\_partition(gB, tB, thread\_idx);                   // (THR\_N,THR\_K,k)
Tensor tBsB \= local\_partition(sB, tB, thread\_idx);                   // (THR\_N,THR\_K)

Copy to clipboard

`gA` and `gB` are tiles of `mA` resp. `mB` according to `cta_tiler` and the `cta_coord`. `tAgA` and `tBgB` are partitions of `gA` resp. `gB` according the the thread-layouts `tA` and `tB` and `thread_idx`.

The following code creates “identity tensors” that map coordinates `(m,k) -> (m,k)` and `(n,k) -> (n,k)`.

// Coordinate tensors
Tensor cA \= make\_identity\_tensor(shape(mA));   // (m,k) -> (m,k)
Tensor cB \= make\_identity\_tensor(shape(mB));   // (n,k) -> (n,k)

Copy to clipboard

Then, the reference tensors are tiled and partitioned in exactly the same way the `mA` and `mB` tensors were tiled and partitioned into `tAgA` and `tBgB`.

// CTA partitioning
Tensor cta\_cA \= local\_tile(cA, cta\_tiler, cta\_coord, Step<\_1, X,\_1\>{});  // (BLK\_M,BLK\_K,k) -> (m,k)
Tensor cta\_cB \= local\_tile(cB, cta\_tiler, cta\_coord, Step< X,\_1,\_1\>{});  // (BLK\_N,BLK\_K,k) -> (n,k)

// Thread partitioning
Tensor tAcA \= local\_partition(cta\_cA, tA, thread\_idx);                   // (THR\_M,THR\_K,k) -> (m,k)
Tensor tBcB \= local\_partition(cta\_cB, tB, thread\_idx);                   // (THR\_N,THR\_K,k) -> (m,k)

Copy to clipboard

The following code creates predicate tensors corresponding to `tAgA` and `tBgB`. They will be computed once in the prologue. and will be used to mask off instructions in the inner loop.

Tensor tApA \= make\_tensor<bool\>(make\_shape (size<0\>(tAcA), size<1\>(tAcA)),
                                make\_stride(     Int<1\>{},      Int<0\>{}));
Tensor tBpB \= make\_tensor<bool\>(make\_shape (size<0\>(tBcB), size<1\>(tBcB)),
                                make\_stride(     Int<1\>{},      Int<0\>{}));

Copy to clipboard

Here, we make a few assumptions: we’re only interested in predicates for one tile of data at a time and we’re only interested in predicates for the m- and n-modes and will handle the k-mode predicates differently. The m- and n- predicates will be considered constant across every tile and will be reused in every iteration of the mainloop. Thus, we only store the predicates for the m- and n-modes and broadcast them across the k-mode. When populating the tensors, we carry the same assumption through:

// Populate the m- and n-predicates
CUTE\_UNROLL
for (int m \= 0; m < size<0\>(tApA); ++m) {
  tApA(m,0) \= elem\_less(get<0\>(tAcA(m,0,0)), shape<0\>(mA));  // Compare the m-coordinate
}
CUTE\_UNROLL
for (int n \= 0; n < size<0\>(tBpB); ++n) {
  tBpB(n,0) \= elem\_less(get<0\>(tBcB(n,0,0)), shape<0\>(mB));  // Compare the n-coordinate
}

Copy to clipboard

and only compare the m- and n-coordinates of the 0th k-tile and 0th k-block. The stride-0 broadcasting mode still allows us to treat this data as a predicate tensor for each and every element of the tile to be loaded.

Finally, we can then use the predicate tensors in `copy_if` to copy only the elements for which the corresponding predicate tensor elements are `true`.

// Copy a k\_tile from global memory to shared memory
copy\_if(tApA, tAgA(\_,\_,k\_tile), tAsA);
copy\_if(tBpB, tBgB(\_,\_,k\_tile), tBsB);

Copy to clipboard

[

](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html "previous page")

# CuTe TMA Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#cute-tma-tensors "Link to this heading")

Along your travels, you may find strange looking CuTe Tensors that are printed as something like

ArithTuple(0,\_0,\_0,\_0) o ((\_128,\_64),2,3,1):((\_1@0,\_1@1),\_64@1,\_1@2,\_1@3)

Copy to clipboard

What is an `ArithTuple`? Are those tensor strides? What do those mean? What is this for?

This documentation intends to answer those questions and introduce some of the more advanced features of CuTe.

## Introduction to TMA instructions[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#introduction-to-tma-instructions "Link to this heading")

The Tensor Memory Accelerator (TMA) is a set of instructions for copying possibly multidimensional arrays between global and shared memory. TMA was introduced in the Hopper architecture. A single TMA instruction can copy an entire tile of data all at once. As a result, the hardware no longer needs to compute individual memory addresses and issue a separate copy instruction for each element of the tile.

To accomplish this, the TMA instruction is given a _TMA descriptor_, which is a packed representation of a multidimensional tensor in global memory with 1, 2, 3, 4, or 5 dimensions. The TMA descriptor holds

-   the base pointer of the tensor;
-   the data type of the tensor’s elements (e.g., `int`, `float`, `double`, or `half`);
-   the size of each dimension;
-   the stride within each dimension; and
-   other flags representing the smem box size, smem swizzling patterns, and out-of-bounds access behavior.

This descriptor must be created on the host before kernel execution. It is shared between all thread blocks that will be issuing TMA instructions. Once inside the kernel, the TMA is executed with the following parameters:

-   pointer to the TMA descriptor;
-   pointer to the SMEM; and
-   coordinates into the GMEM tensor represented within the TMA descriptor.

For example, the interface for TMA-store with 3-D coordinates looks like this.

struct SM90\_TMA\_STORE\_3D {
  CUTE\_DEVICE static void
  copy(void const\* const desc\_ptr,
       void const\* const smem\_ptr,
       int32\_t const& crd0, int32\_t const& crd1, int32\_t const& crd2) {
    // ... invoke CUDA PTX instruction ...
  }
};

Copy to clipboard

We observe that the TMA instruction does not directly consume pointers to global memory. Indeed, the global memory pointer is contained in the descriptor, is considered constant, and is NOT a separate parameter to the TMA instruction. Instead, the TMA consumes TMA coordinates into the TMA’s view of global memory that is defined in the TMA descriptor.

That means that an ordinary CuTe Tensor that stores a GMEM pointer and computes offsets and new GMEM pointers is useless to the TMA.

What do we do?

## Building a TMA Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#building-a-tma-tensor "Link to this heading")

### Implicit CuTe Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#implicit-cute-tensors "Link to this heading")

All CuTe Tensors are compositions of Layouts and Iterators. An ordinary global memory tensor’s iterator is its global memory pointer. However, a CuTe Tensor’s iterator doesn’t have to be a pointer; it can be any random-access iterator.

One example of such an iterator is a _counting iterator_. This represents a possibly infinite sequence of integers that starts at some value. We call the members of this sequence _implicit integers_, because the sequence is not explicitly stored in memory. The iterator just stores its current value.

We can use a counting iterator to create a tensor of implicit integers,

Tensor A \= make\_tensor(counting\_iterator<int\>(42), make\_shape(4,5));
print\_tensor(A);

Copy to clipboard

which outputs

counting\_iter(42) o (4,5):(\_1,4):
   42   46   50   54   58
   43   47   51   55   59
   44   48   52   56   60
   45   49   53   57   61

Copy to clipboard

This tensor maps logical coordinates to on-the-fly computed integers. Because it’s still a CuTe Tensor, it can still be tiled and partitioned and sliced just like a normal tensor by accumulating integer offsets into the iterator.

But the TMA doesn’t consume pointers or integers, it consumes coordinates. Can we make a tensor of implicit TMA coordinates for the TMA instruction to consume? If so, then we could presumably also tile and partition and slice that tensor of coordinates so that we would always have the right TMA coordinate to give to the instruction.

### ArithTupleIterators and ArithTuples[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#arithtupleiterators-and-arithtuples "Link to this heading")

First, we build a `counting_iterator` equivalent for TMA coordinates. It should support

-   dereference to a TMA coordinate, and
-   offset by another TMA coordinate.

We’ll call this an `ArithmeticTupleIterator`. It stores a coordinate (a tuple of integers) that is represented as an `ArithmeticTuple`. The `ArithmeticTuple` is simply a (public subclass of) `cute::tuple` that has an overloaded `operator+` so that it can be offset by another tuple. The sum of two tuples is the tuple of the sum of the elements.

Now similar to `counting_iterator<int>(42)` we can create an implicit “iterator” (but without increment or other common iterator operations) over tuples that can be dereferenced and offset by other tuples

ArithmeticTupleIterator citer\_1 \= make\_inttuple\_iter(42, Int<2\>{}, Int<7\>{});
ArithmeticTupleIterator citer\_2 \= citer\_1 + make\_tuple(Int<0\>{}, 5, Int<2\>{});
print(\*citer\_2);

Copy to clipboard

which outputs

(42,7,\_9)

Copy to clipboard

A TMA Tensor can use an iterator like this to store the current TMA coordinate “offset”. The “offset” here is in quotes because it’s clearly not a normal 1-D array offset or pointer.

In summary, one creates a TMA descriptor for the _whole global memory tensor_. The TMA descriptor defines a view into that tensor and the instruction takes TMA coordinates into that view. In order to generate and track those TMA coordinates, we define an implicit CuTe Tensor of TMA coordinates that can be tiled, sliced, and partitioned the exact same way as an ordinary CuTe Tensor.

We can now track and offset TMA coordinates with this iterator, but how do we get CuTe Layouts to generate non-integer offsets?

### Strides aren’t just integers[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#strides-aren-t-just-integers "Link to this heading")

Ordinary tensors have a layout that maps a logical coordinate `(i,j)` into a 1-D linear index `k`. This mapping is the inner-product of the coordinate with the strides.

TMA Tensors hold iterators of TMA coordinates. Thus, a TMA Tensor’s Layout must map a logical coordinate to a TMA coordinate, rather than to a 1-D linear index.

To do this, we can abstract what a stride is. Strides need not be integers, but rather any algebraic object that supports inner-product with the integers (the logical coordinate). The obvious choice is the `ArithmeticTuple` we used earlier since they can be added to each other, but this time additionally equipped with an `operator*` so it can also be scaled by an integer.

#### Aside: Integer-module strides[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#aside-integer-module-strides "Link to this heading")

A group of objects that support addition between elements and product between elements and integers is called an integer-module.

Formally, an integer-module is an abelian group `(M,+)` equipped with `Z*M -> M`, where `Z` are the integers. That is, an integer-module `M` is a group that supports inner products with the integers. The integers are an integer-module. Rank-R tuples of integers are an integer-module.

In principle, layout strides may be any integer-module.

#### Basis elements[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#basis-elements "Link to this heading")

CuTe’s basis elements live in the header file `cute/numeric/arithmetic_tuple.hpp`. To make it easy to create `ArithmeticTuple`s that can be used as strides, CuTe defines normalized basis elements using the `E` type alias. “Normalized” means that the scaling factor of the basis element is the compile-time integer 1.

| C++ object | Description | String representation |
| --- | --- | --- |
| `E<>{}` | `1` | `1` |
| `E<0>{}` | `(1,0,...)` | `1@0` |
| `E<1>{}` | `(0,1,0,...)` | `1@1` |
| `E<0,0>{}` | `((1,0,...),0,...)` | `1@0@0` |
| `E<0,1>{}` | `((0,1,0,...),0,...)` | `1@1@0` |
| `E<1,0>{}` | `(0,(1,0,...),0,...)` | `1@0@1` |
| `E<1,1>{}` | `(0,(0,1,0,...),0,...)` | `1@1@1` |

The “description” column in the above table interprets each basis element as an infinite tuple of integers, where all the tuple’s entries not specified by the element’s type are zero. We count tuple entries from left to right, starting with zero. For example, `E<1>{}` has a 1 in position 1: `(0,1,0,...)`. `E<3>{}` has a 1 in position 3: `(0,0,0,1,0,...)`.

Basis elements can be _nested_. For instance, in the above table, `E<0,1>{}` means that in position 0 there is a `E<1>{}`: `((0,1,0,...),0,...)`. Similarly, `1@1@0` means that `1` is lifted to position 1 to create `1@1`: `(0,1,0,...)` which is then lifted again to position 0.

Basis elements can be _scaled_. That is, they can be multiplied by an integer _scaling factor_. For example, in `5*E<1>{}`, the scaling factor is `5`. `5*E<1>{}` prints as `5@1` and means `(0,5,0,...)`. The scaling factor commutes through any nesting. For instance, `5*E<0,1>{}` prints as `5@1@0` and means `((0,5,0,...),0,...)`.

Basis elements can also be added together, as long as their hierarchical structures are compatible. For example, `3*E<0>{} + 4*E<1>{}` results in `(3,4,0,...)`. Intuitively, “compatible” means that the nested structure of the two basis elements matches well enough to add the two elements together.

#### Linear combinations of strides[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#linear-combinations-of-strides "Link to this heading")

Layouts work by taking the inner product of the natural coordinate with their strides. For strides made of integer elements, e.g., `(1,100)`, the inner product of the input coordinate `(i,j)` and the stride is `i + 100j`. Offsetting an “ordinary” tensor’s pointer and this index gives the pointer to the tensor element at `(i,j)`.

For strides of basis elements, we still compute the inner product of the natural coordinate with the strides. For example, if the stride is `(1@0,1@1)`, then the inner product of the input coordinate `(i,j)` with the strides is `i@0 + j@1 = (i,j)`. That translates into the (TMA) coordinate `(i,j)`. If we wanted to reverse the coordinates, then we could use `(1@1,1@0)` as the stride. Evaluating the layout would give `i@1 + j@0 = (j,i)`.

A linear combination of basis elements can be interpreted as a possibly multidimensional and hierarchical coordinate. For instance, `2*2@1@0 + 3*1@1 + 4*5@1 + 7*1@0@0` means `((0,4,...),0,...) + (0,3,0,...) + (0,20,0,...) + ((7,...),...) = ((7,4,...),23,...)` and can be interpreted as the coordinate `((7,4),23)`.

Thus, linear combinations of these strides can be used to generate TMA coordinates. These coordinates, in turn, can be used to offset TMA coordinate iterators.

### Application to TMA Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0z_tma_tensors.html#application-to-tma-tensors "Link to this heading")

Now we can build CuTe Tensors like the one seen in the introduction.

Tensor a \= make\_tensor(make\_inttuple\_iter(0,0),
                       make\_shape (     4,      5),
                       make\_stride(E<0\>{}, E<1\>{}));
print\_tensor(a);

Tensor b \= make\_tensor(make\_inttuple\_iter(0,0),
                       make\_shape (     4,      5),
                       make\_stride(E<1\>{}, E<0\>{}));
print\_tensor(b);

Copy to clipboard

prints

ArithTuple(0,0) o (4,5):(\_1@0,\_1@1):
  (0,0)  (0,1)  (0,2)  (0,3)  (0,4)
  (1,0)  (1,1)  (1,2)  (1,3)  (1,4)
  (2,0)  (2,1)  (2,2)  (2,3)  (2,4)
  (3,0)  (3,1)  (3,2)  (3,3)  (3,4)

ArithTuple(0,0) o (4,5):(\_1@1,\_1@0):
  (0,0)  (1,0)  (2,0)  (3,0)  (4,0)
  (0,1)  (1,1)  (2,1)  (3,1)  (4,1)
  (0,2)  (1,2)  (2,2)  (3,2)  (4,2)
  (0,3)  (1,3)  (2,3)  (3,3)  (4,3)

