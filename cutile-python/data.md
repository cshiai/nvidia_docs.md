# Data Model


cuTile is an array-based programming model. The fundamental data structure is multidimensional arrays with elements of a single homogeneous type. cuTile Python does not expose pointers, only arrays.


An array-based model was chosen because:


 - Arrays know their bounds, so accesses can be checked to ensure safety and correctness.
 - Array-based load/store operations can be efficiently lowered to speed-of-light hardware mechanisms.
 - Python programmers are used to array-based programming frameworks such as NumPy.
 - Pointers are not a natural choice for Python.


Within [tile code](execution.html#tile-code), only the types described in this section are supported.


## Global Arrays



### `class cuda.tile.Array`

A global array (or array) is a container of objects stored in a logical
multidimensional space.
Global arrays are always stored in memory.
Copying an array does not copy the underlying data.
Global arrays can be used in host code and tile code.
They can be kernel parameters.
Any object that implements the DLPack format or the CUDA Array Interface can be used
as a global array. Example: CuPy arrays and PyTorch tensors.

See also
Complete cuda.tile.Array class documentation


## Tiles



### `class cuda.tile.Tile`

A tile array (or tile) is an immutable multidimensional collection of values that is
local to a block.
The contents of a tile do not necessarily have a representation in memory.
Tiles can be created by loading from global arrays or with factory functions.
Tiles can also be stored into global arrays.
Tiles shall not be used in host code; they can only be used in tile code.
Tiles shall not be kernel parameters.
Each dimension of a tile shall be a power of 2.

See also
Complete cuda.tile.Tile class documentation


## Element & Tile Space

 ![_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__dark_background.svg](_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__dark_background.svg) ![_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__light_background.svg](_images/cutile__indexing__array_shape_12x16__tile_shape_2x4__tile_grid_6x4__light_background.svg) ![_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__dark_background.svg](_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__dark_background.svg) ![_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__light_background.svg](_images/cutile__indexing__array_shape_12x16__tile_shape_4x2__tile_grid_3x8__light_background.svg)
The *element space* of an array is the multidimensional space of elements contained in that array, stored in memory according to a certain layout (row major, column major, etc).


The *tile space* of an array is the multidimensional space of tiles into that array of a certain tile shape. A tile index `(i, j, ...)` with shape `S` refers to the elements of the array that belong to the `(i+1)`-th, `(j+1)`-th, … tile.


When accessing the elements of an array using tile indices, the multidimensional memory layout of the array is used. To access the tile space with a different memory layout, use the order parameter of load/store operations.


## Shape Broadcasting


*Shape broadcasting* allows [tiles](data/tile.html#cuda-tile-tile) with different shapes to be combined in arithmetic operations. When performing operations between [tiles](data/tile.html#cuda-tile-tile) of different shapes, the smaller [tile](data/tile.html#cuda-tile-tile) is automatically extended to match the shape of the larger one, following these rules:


 - [Tiles](data/tile.html#cuda-tile-tile) are aligned by their trailing dimensions.
 - If the corresponding dimensions have the same size or one of them is 1, they are compatible.
 - If one [tile](data/tile.html#cuda-tile-tile) has fewer dimensions, its shape is padded with 1s on the left.


Broadcasting follows the same semantics as [NumPy](https://numpy.org/doc/stable/), which makes code more concise and readable while maintaining computational efficiency.


## Data Types



### `class cuda.tile.DType`

A data type (or dtype) describes the type of the objects of an array, tile, or
operation.
Dtypes determine how values are stored in memory and how operations on those values are
performed.
Dtypes are immutable.
Dtypes can be used in host code and tile code.
They can be kernel parameters.

property bitwidth
The number of bits in an element of the data type.

property name
The name of the data type.



### `cuda.tile.bool_`

A 8-bit arithmetic dtype (True or False).



### `cuda.tile.uint8`

A 8-bit unsigned integer arithmetic dtype whose values exist on the interval [0, +256].



### `cuda.tile.uint16`

A 16-bit unsigned integer arithmetic dtype whose values exist on the interval [0, +65,536].



### `cuda.tile.uint32`

A 32-bit unsigned integer arithmetic dtype whose values exist on the interval [0, +4,294,967,295].



### `cuda.tile.uint64`

A 64-bit unsigned integer arithmetic dtype whose values exist on the interval [0, +18,446,744,073,709,551,615].



### `cuda.tile.int8`

A 8-bit signed integer arithmetic dtype whose values exist on the interval [−128, +127].



### `cuda.tile.int16`

A 16-bit signed integer arithmetic dtype whose values exist on the interval [−32,768, +32,767].



### `cuda.tile.int32`

A 32-bit signed integer arithmetic dtype whose values exist on the interval [−2,147,483,648, +2,147,483,647].



### `cuda.tile.int64`

A 64-bit signed integer arithmetic dtype whose values exist on the interval [−9,223,372,036,854,775,808, +9,223,372,036,854,775,807].



### `cuda.tile.float16`

A IEEE 754 half-precision (16-bit) binary floating-point arithmetic dtype (see IEEE 754-2019).



### `cuda.tile.float32`

A IEEE 754 single-precision (32-bit) binary floating-point arithmetic dtype (see IEEE 754-2019).



### `cuda.tile.float64`

A IEEE 754 double-precision (64-bit) binary floating-point arithmetic dtype (see IEEE 754-2019).



### `cuda.tile.bfloat16`

A 16-bit floating-point arithmetic dtype with 1 sign bit, 8 exponent bits, and 7 mantissa bits.



### `cuda.tile.tfloat32`

A 32-bit tensor floating-point arithmetic dtype with 1 sign bit, 8 exponent bits, and 10 mantissa bits (19-bit representation stored in 32-bit container).



### `cuda.tile.float8_e4m3fn`

A 8-bit floating-point arithmetic dtype with 1 sign bit, 4 exponent bits, and 3 mantissa bits.



### `cuda.tile.float8_e5m2`

A 8-bit floating-point arithmetic dtype with 1 sign bit, 5 exponent bits, and 2 mantissa bits.


## Numeric & Arithmetic Data Types


A *numeric* data type represents numbers. An *arithmetic* data type is a numeric data type that supports general arithmetic operations such as addition, subtraction, multiplication, and division.


## Arithmetic Promotion


Binary operations can be performed on two [tile](data/tile.html#cuda-tile-tile) or [scalar](data.html#scalars) operands of different [numeric dtypes](data.html#numeric-arithmetic-data-types).


When both operands are [loosely typed numeric constants](execution.html#constant-expressions-objects), then the result is also a loosely typed constant: for example, `5 + 7` is a loosely typed integral constant 12, and `5 + 3.0` is a loosely typed floating-point constant 8.0.


If any of the operands is not a [loosely typed numeric constant](execution.html#constant-expressions-objects), then both are *promoted* to a common dtype using the following process:


 - Each operand is classified into one of the three categories: *boolean*, *integral*, or *floating-point*. The categories are ordered as follows: *boolean* < *integral* < *floating-point*.
 - If either operand is a [loosely typed numeric constant](execution.html#constant-expressions-objects), a concrete dtype is picked for it: integral constants are treated as int32, int64, or uint64, depending on the value; floating-point constants are treated as float32.
 - If one of the two operands has a higher category than the other, then its concrete dtype is chosen as the common dtype.
 - If both operands are of the same category, but one of them is a [loosely typed numeric constant](execution.html#constant-expressions-objects), then the other operand’s dtype is picked as the common dtype.
 - Otherwise, the common dtype is computed according to the table below.


|  | b1 | u8 | u16 | u32 | u64 | i8 | i16 | i32 | i64 | f16 | f32 | f64 | bf | tf32 | f8e4m3fn | f8e5m2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| b1 | b1 | u8 | u16 | u32 | u64 | i8 | i16 | i32 | i64 | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| u8 | u8 | u8 | u16 | u32 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| u16 | u16 | u16 | u16 | u32 | u32 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| u32 | u32 | u32 | u32 | u32 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| u64 | u64 | u64 | u64 | u64 | u64 | ERR | ERR | ERR | ERR | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| i8 | i8 | ERR | ERR | ERR | ERR | i8 | i16 | i32 | i64 | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| i16 | i16 | ERR | ERR | ERR | ERR | i16 | i16 | i32 | i64 | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| i32 | i32 | ERR | ERR | ERR | ERR | i32 | i32 | i32 | i64 | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| i64 | i64 | ERR | ERR | ERR | ERR | i64 | i64 | i64 | i64 | f16 | f32 | f64 | bf | ERR | ERR | ERR |
| f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f16 | f32 | f64 | ERR | ERR | ERR | ERR |
| f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f32 | f64 | f32 | ERR | ERR | ERR |
| f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | f64 | ERR | ERR | ERR |
| bf | bf | bf | bf | bf | bf | bf | bf | bf | bf | ERR | f32 | f64 | bf | ERR | ERR | ERR |
| tf32 | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | tf32 | ERR | ERR |
| f8e4m3fn | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | f8e4m3fn | ERR |
| f8e5m2 | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | ERR | f8e5m2 |


Legend:


 - b1: `bool_`
 - u8: `uint8`
 - u16: `uint16`
 - u32: `uint32`
 - u64: `uint64`
 - i8: `int8`
 - i16: `int16`
 - i32: `int32`
 - i64: `int64`
 - f16: `float16`
 - f32: `float32`
 - f64: `float64`
 - bf: `bfloat16`
 - tf32: `tfloat32`
 - f8e4m3fn: `float8_e4m3fn`
 - f8e5m2: `float8_e5m2`
 - ERR: Implicit promotion between these types is not supported


## Scalars


A *scalar* is a single immutable value of a specific [data type](data.html#data-types). A *scalar* and *0D-tile* can be used interchangably in a tile [kernel](execution.html#tile-kernels). They can also be [kernel](execution.html#tile-kernels) parameters.


Typing of a *scalar* has the following rules:


 - Constant scalars are [loosely typed](execution.html#constant-expressions-objects) by default, for example, a literal `2` or a constant property like `Tile.ndim`, `Tile.shape`, or `Array.ndim`.
 - `Array.shape` and `Array.stride` are not constant by default and has default int type int32. Using default int32 makes kernel more performant at the cost of limiting max representable shape. This limitation will be lifted in the near future.


## Tuples


Tuples can be used in [tile code](execution.html#tile-code). They cannot be [kernel](execution.html#tile-kernels) parameters.


## Rounding Modes



### `class cuda.tile.RoundingMode`

Rounding mode for floating-point operations.

RN = 'nearest_even'
Rounds the nearest (ties to even).

RZ = 'zero'
Round towards zero (truncate).

RM = 'negative_inf'
Round towards negative infinity.

RP = 'positive_inf'
Round towards positive infinity.

FULL = 'full'
Full precision rounding mode.

APPROX = 'approx'
Approximate rounding mode.

RZI = 'nearest_int_to_zero'
Round towards zero to the nearest integer.


## Padding Modes



### `class cuda.tile.PaddingMode`

Padding mode for load operation.

UNDETERMINED = 'undetermined'
The padding value is not determined.

ZERO = 'zero'
The padding value is zero.

NEG_ZERO = 'neg_zero'
The padding value is negative zero.

NAN = 'nan'
The padding value is NaN.

POS_INF = 'pos_inf'
The padding value is positive infinity.

NEG_INF = 'neg_inf'
The padding value is negative infinity.