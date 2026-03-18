# Data Model[#](https://docs.nvidia.com/cuda/cutile-python/data.html#data-model "Link to this heading")

cuTile is an array-based programming model. The fundamental data structure is multidimensional arrays with elements of a single homogeneous type. cuTile Python does not expose pointers, only arrays.

An array-based model was chosen because:

-   Arrays know their bounds, so accesses can be checked to ensure safety and correctness.
-   Array-based load/store operations can be efficiently lowered to speed-of-light hardware mechanisms.
-   Python programmers are used to array-based programming frameworks such as NumPy.
-   Pointers are not a natural choice for Python.

Within [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code), only the types described in this section are supported.

## Global Arrays[#](https://docs.nvidia.com/cuda/cutile-python/data.html#global-arrays "Link to this heading")

A _global array_ (or _array_) is a container of elements of a specific [dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types) arranged in a logical multidimensional space.

Array’s _shape_ is a tuple of integer values, each denoting the length of the corresponding dimension. The length of the shape tuple equals the arrays’s number of dimensions. The product of shape values equals the total logical number of elements in the array.

Arrays are stored in global memory using a _strided memory layout_: in addition to a shape, an array also has an equally sized tuple of _strides_. Strides determine the mapping of logical array indices to physical memory locations. For example, for a 3-dimensional float32 array with strides (s1, s2, s3), the memory address of the element at the logical index (i1, i2, i3) will be:

base\_addr + 4 \* (s1 \* i1 + s2 \* i2 + s3 \* i3),

where `base_addr` is the base address of the array and 4 is the byte size of a single float32 element.

New arrays can only be allocated by the host, and passed to the tile kernel as arguments. [Tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code) can only create new views of existing arrays, for example using [`Array.slice()`](https://docs.nvidia.com/cuda/cutile-python/data/array.html#cuda.tile.Array.slice "cuda.tile.Array.slice"). Like in Python, assigning an array object to another variable does not copy the underlying data, but creates another reference to the array object.

Any object that implements the [DLPack](https://dmlc.github.io/dlpack/latest/) interface or the [CUDA Array Interface](https://numba.readthedocs.io/en/stable/cuda/cuda_array_interface.html) can be passed to the kernel as an argument. Example: [CuPy](https://docs.cupy.dev/en/stable/) arrays and [PyTorch](https://pytorch.org/docs/stable/) tensors.

If two or more array arguments are passed to the kernel, their memory storage must not overlap. Otherwise, behavior is undefined.

Array’s shape can be queried using the [`Array.shape`](https://docs.nvidia.com/cuda/cutile-python/data/array.html#cuda.tile.Array.shape "cuda.tile.Array.shape") attribute, which returns a tuple of int32 scalars. These scalars are non-constant, runtime values. Using int32 makes the tile code more performant at the cost of limiting the maximum representable shape at 2,147,483,647 elements. This limitation will be lifted in the future.

See also

[cuda.tile.Array class documentation](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array)

## Tiles and Scalars[#](https://docs.nvidia.com/cuda/cutile-python/data.html#tiles-and-scalars "Link to this heading")

A _tile_ is an immutable multidimensional collection of elements of a specific [dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types).

Tile’s _shape_ is a tuple of integer values, each denoting the length of the corresponding dimension. The length of the shape tuple equals the tile’s number of dimensions. The product of shape values equals the total number of elements in the tile.

The shape of a tile must be known at compile time. Each dimension of a tile must be a power of 2.

Tile’s dtype and shape can be queried with the `dtype` and `shape` attributes, respectively. For example, if `x` is a float32 tile, the expression `x.dtype` will return a compile-time constant equal to [`cuda.tile.float32`](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.float32 "cuda.tile.float32").

A zero-dimensional tile is called a _scalar_. Such tile has exactly one element. The shape of a scalar is the empty tuple (). Numeric literals like 7 or 3.14 are treated as constant scalars, i.e. zero-dimensional tiles.

Since scalars are tiles, they slightly differ in behavior from Python’s `int`/`float` objects. For example, they have `dtype` and `shape` attributes:

a \= 0
\# The following line will evaluate to cuda.tile.int32 in cuTile,
\# but would raise an AttributeError in Python:
a.dtype

Tiles can only be used in [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code), not host code. The contents of a tile do not necessarily have a physical representation in memory. Non-scalar tiles can be created by loading from [global arrays](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array) using functions such as [`cuda.tile.load()`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.load.html#cuda.tile.load "cuda.tile.load") and [`cuda.tile.gather()`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.gather.html#cuda.tile.gather "cuda.tile.gather") or with [factory](https://docs.nvidia.com/cuda/cutile-python/operations.html#operations-factory) functions such as [`cuda.tile.zeros()`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.zeros.html#cuda.tile.zeros "cuda.tile.zeros").

Tiles can also be stored into global arrays using functions such as [`cuda.tile.store()`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.store.html#cuda.tile.store "cuda.tile.store") or [`cuda.tile.scatter()`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.scatter.html#cuda.tile.scatter "cuda.tile.scatter").

Only scalars (i.e. 0-dimensional tiles) can be used as [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) parameters.

Scalar constants are [loosely typed](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-expressions-objects) by default, for example, a literal `2` or a constant attribute like `Tile.ndim`, `Tile.shape`, or `Array.ndim`.

See also

[cuda.tile.Tile class documentation](https://docs.nvidia.com/cuda/cutile-python/data/tile.html#data-tile-cuda-tile-tile)

## Element & Tile Space[#](https://docs.nvidia.com/cuda/cutile-python/data.html#element-tile-space "Link to this heading")

![_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__dark_background.svg](https://docs.nvidia.com/cuda/cutile-python/_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__dark_background.svg) ![_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__light_background.svg](https://docs.nvidia.com/cuda/cutile-python/_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__light_background.svg) ![_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__dark_background.svg](https://docs.nvidia.com/cuda/cutile-python/_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__dark_background.svg) ![_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__light_background.svg](https://docs.nvidia.com/cuda/cutile-python/_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__light_background.svg)

The _element space_ of an array is the multidimensional space of elements contained in that array, stored in memory according to a certain layout (row major, column major, etc).

The _tile space_ of an array is the multidimensional space of tiles into that array of a certain tile shape. A tile index `(i, j, ...)` with shape `S` refers to the elements of the array that belong to the `(i+1)`\-th, `(j+1)`\-th, … tile.

When accessing the elements of an array using tile indices, the multidimensional memory layout of the array is used. To access the tile space with a different memory layout, use the order parameter of load/store operations.

## Shape Broadcasting[#](https://docs.nvidia.com/cuda/cutile-python/data.html#shape-broadcasting "Link to this heading")

_Shape broadcasting_ allows [tiles](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) with different shapes to be combined in arithmetic operations. When performing operations between [tiles](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) of different shapes, the smaller [tile](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) is automatically extended to match the shape of the larger one, following these rules:

-   [Tiles](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) are aligned by their trailing dimensions.
-   If the corresponding dimensions have the same size or one of them is 1, they are compatible.
-   If one [tile](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) has fewer dimensions, its shape is padded with 1s on the left.

Broadcasting follows the same semantics as [NumPy](https://numpy.org/doc/stable/), which makes code more concise and readable while maintaining computational efficiency.

## Data Types[#](https://docs.nvidia.com/cuda/cutile-python/data.html#data-types "Link to this heading")

_class_ cuda.tile.DType[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.DType "Link to this definition")

A _data type_ (or _dtype_) describes the type of the objects of an [array](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array), [tile](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars), or operation.

[Dtypes](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types) determine how values are stored in memory and how operations on those values are performed. [Dtypes](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types) are immutable.

[Dtypes](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types) can be used in [host code](https://docs.nvidia.com/cuda/cutile-python/execution.html#host-code) and [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code). They can be [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) parameters.

_property_ bitwidth[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.DType.bitwidth "Link to this definition")

The number of bits in an element of the [data type](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types).

_property_ name[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.DType.name "Link to this definition")

The name of the [data type](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types).

cuda.tile.bool\_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.bool_ "Link to this definition")

A 8-bit [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) (`True` or `False`).

cuda.tile.uint8[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.uint8 "Link to this definition")

A 8-bit unsigned integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[0, +256\].

cuda.tile.uint16[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.uint16 "Link to this definition")

A 16-bit unsigned integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[0, +65,536\].

cuda.tile.uint32[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.uint32 "Link to this definition")

A 32-bit unsigned integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[0, +4,294,967,295\].

cuda.tile.uint64[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.uint64 "Link to this definition")

A 64-bit unsigned integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[0, +18,446,744,073,709,551,615\].

cuda.tile.int8[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.int8 "Link to this definition")

A 8-bit signed integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[−128, +127\].

cuda.tile.int16[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.int16 "Link to this definition")

A 16-bit signed integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[−32,768, +32,767\].

cuda.tile.int32[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.int32 "Link to this definition")

A 32-bit signed integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[−2,147,483,648, +2,147,483,647\].

cuda.tile.int64[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.int64 "Link to this definition")

A 64-bit signed integer [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) whose values exist on the interval \[−9,223,372,036,854,775,808, +9,223,372,036,854,775,807\].

cuda.tile.float16[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.float16 "Link to this definition")

A IEEE 754 half-precision (16-bit) binary floating-point [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) (see [IEEE 754-2019](https://standards.ieee.org/standard/754-2019.html)).

cuda.tile.float32[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.float32 "Link to this definition")

A IEEE 754 single-precision (32-bit) binary floating-point [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) (see [IEEE 754-2019](https://standards.ieee.org/standard/754-2019.html)).

cuda.tile.float64[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.float64 "Link to this definition")

A IEEE 754 double-precision (64-bit) binary floating-point [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) (see [IEEE 754-2019](https://standards.ieee.org/standard/754-2019.html)).

cuda.tile.bfloat16[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.bfloat16 "Link to this definition")

A 16-bit floating-point [arithmetic dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) with 1 sign bit, 8 exponent bits, and 7 mantissa bits.

cuda.tile.tfloat32[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.tfloat32 "Link to this definition")

A 32-bit tensor floating-point [numeric dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) with 1 sign bit, 8 exponent bits, and 10 mantissa bits (19-bit representation stored in 32-bit container).

cuda.tile.float8\_e4m3fn[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.float8_e4m3fn "Link to this definition")

An 8-bit floating-point [numeric dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) with 1 sign bit, 4 exponent bits, and 3 mantissa bits.

cuda.tile.float8\_e5m2[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.float8_e5m2 "Link to this definition")

An 8-bit floating-point [numeric dtype](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types) with 1 sign bit, 5 exponent bits, and 2 mantissa bits.

## Numeric & Arithmetic Data Types[#](https://docs.nvidia.com/cuda/cutile-python/data.html#numeric-arithmetic-data-types "Link to this heading")

A _numeric_ data type represents numbers. An _arithmetic_ data type is a numeric data type that supports general arithmetic operations such as addition, subtraction, multiplication, and division.

## Arithmetic Promotion[#](https://docs.nvidia.com/cuda/cutile-python/data.html#arithmetic-promotion "Link to this heading")

Binary operations can be performed on two [tile](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) or [scalar](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) operands of different [numeric dtypes](https://docs.nvidia.com/cuda/cutile-python/data.html#data-numeric-arithmetic-data-types).

When both operands are [loosely typed numeric constants](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-expressions-objects), then the result is also a loosely typed constant: for example, `5 + 7` is a loosely typed integral constant 12, and `5 + 3.0` is a loosely typed floating-point constant 8.0.

If any of the operands is not a [loosely typed numeric constant](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-expressions-objects), then both are _promoted_ to a common dtype using the following process:

-   Each operand is classified into one of the three categories: _boolean_, _integral_, or _floating-point_. The categories are ordered as follows: _boolean_ < _integral_ < _floating-point_.
-   If either operand is a [loosely typed numeric constant](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-expressions-objects), a concrete dtype is picked for it: integral constants are treated as int32, int64, or uint64, depending on the value; floating-point constants are treated as float32.
-   If one of the two operands has a higher category than the other, then its concrete dtype is chosen as the common dtype.
-   If both operands are of the same category, but one of them is a [loosely typed numeric constant](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-expressions-objects), then the other operand’s dtype is picked as the common dtype.
-   Otherwise, the common dtype is computed according to the table below.

|     | b1  | u8  | u16 | u32 | u64 | i8  | i16 | i32 | i64 | f16 | f32 | f64 | bf  | tf32 | f8e4m3fn | f8e5m2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| b1  | b1  | u8  | u16 | u32 | u64 | i8  | i16 | i32 | i64 | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| u8  | u8  | u8  | u16 | u32 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| u16 | u16 | u16 | u16 | u32 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| u32 | u32 | u32 | u32 | u32 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| u64 | u64 | u64 | u64 | u64 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| i8  | i8  | ERR | ERR | ERR | ERR | i8  | i16 | i32 | i64 | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| i16 | i16 | ERR | ERR | ERR | ERR | i16 | i16 | i32 | i64 | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| i32 | i32 | ERR | ERR | ERR | ERR | i32 | i32 | i32 | i64 | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| i64 | i64 | ERR | ERR | ERR | ERR | i64 | i64 | i64 | i64 | f16 | f32 | f64 | bf  | ERR | ERR | ERR |
| f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f32 | f64 | ERR | ERR | ERR | ERR |
| f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f64 | f32 | ERR | ERR | ERR |
| f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | ERR | ERR | ERR |
| bf  | bf  | bf  | bf  | bf  | bf  | bf  | bf  | bf  | bf  | ERR | f32 | f64 | bf  | ERR | ERR | ERR |
| tf32 | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | tf32 | ERR | ERR |
| f8e4m3fn | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | f8e4m3fn | ERR |
| f8e5m2 | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | f8e5m2 |

Legend:

-   b1: `bool_`
-   u8: `uint8`
-   u16: `uint16`
-   u32: `uint32`
-   u64: `uint64`
-   i8: `int8`
-   i16: `int16`
-   i32: `int32`
-   i64: `int64`
-   f16: `float16`
-   f32: `float32`
-   f64: `float64`
-   bf: `bfloat16`
-   tf32: `tfloat32`
-   f8e4m3fn: `float8_e4m3fn`
-   f8e5m2: `float8_e5m2`
-   f8e8m0fnu: `float8_e8m0fnu`
-   f4e2m1fn: `float4_e2m1fn`
-   ERR: Implicit promotion between these types is not supported

## Tuples[#](https://docs.nvidia.com/cuda/cutile-python/data.html#tuples "Link to this heading")

Tuples can be used in [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code). They cannot be [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) parameters.

## Rounding Modes[#](https://docs.nvidia.com/cuda/cutile-python/data.html#rounding-modes "Link to this heading")

_class_ cuda.tile.RoundingMode[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode "Link to this definition")

Rounding mode for floating-point operations.

RN _\= 'nearest\_even'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.RN "Link to this definition")

Rounds the nearest (ties to even).

RZ _\= 'zero'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.RZ "Link to this definition")

Round towards zero (truncate).

RM _\= 'negative\_inf'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.RM "Link to this definition")

Round towards negative infinity.

RP _\= 'positive\_inf'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.RP "Link to this definition")

Round towards positive infinity.

FULL _\= 'full'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.FULL "Link to this definition")

Full precision rounding mode.

APPROX _\= 'approx'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.APPROX "Link to this definition")

Approximate rounding mode.

RZI _\= 'nearest\_int\_to\_zero'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.RoundingMode.RZI "Link to this definition")

Round towards zero to the nearest integer.

## Padding Modes[#](https://docs.nvidia.com/cuda/cutile-python/data.html#padding-modes "Link to this heading")

_class_ cuda.tile.PaddingMode[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode "Link to this definition")

Padding mode for load operation.

UNDETERMINED _\= 'undetermined'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode.UNDETERMINED "Link to this definition")

The padding value is not determined.

ZERO _\= 'zero'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode.ZERO "Link to this definition")

The padding value is zero.

NEG\_ZERO _\= 'neg\_zero'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode.NEG_ZERO "Link to this definition")

The padding value is negative zero.

NAN _\= 'nan'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode.NAN "Link to this definition")

The padding value is NaN.

POS\_INF _\= 'pos\_inf'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode.POS_INF "Link to this definition")

The padding value is positive infinity.

NEG\_INF _\= 'neg\_inf'_[#](https://docs.nvidia.com/cuda/cutile-python/data.html#cuda.tile.PaddingMode.NEG_INF "Link to this definition")

The padding value is negative infinity.
