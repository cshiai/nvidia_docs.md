5. Type System
All values and operations in Tile IR are statically typed. This section defines Tile IR’s types, as well as their equivalence, layouts, and other type system details that may be relevant for DSL and compiler authors.

Notably Tile IR is tensor valued: all values are tensors. We have two concrete tensor types: tile, a pure tensor value, and view, a structured pointer to a tensor in memory. Additionally, we use element types in the formulation of our type system. They do not describe a value on their own.

5.1. Element Types
Element types are the native data types supported by Tile IR. By themselves they do not describe a value. As Tile IR operates over tensors, these types describe the hardware accelerated, primitive values that can be contained by a tensor. They specify how a sequence of bits are to be interpreted. Each element type has a size associated with it that represents the number of bits required to represent it.

Note

Note that this is different from a potential storage size, which is specified by the data layout of the tensor which contains these values.

Element types come in two flavors, general purpose fundamental types that come without restriction, and specialized alternative types which each come with a set of restrictions.

5.1.1. Fundamental Types
Tile IR supports a set of general purpose integer and floating-point types that are supported by all operations and have no restrictions. These can be contained in arbitrary rank, and shape tensors, and 0-rank values of this type can be treated as scalars.

Fundamental Types
Type

Sizes

Description

i1, i8, i16, i32, i64

1, 8, 16, 32, 64

signless integer type of specified size

f16, f32, f64

16, 32, 64

IEEE floating-point type of specified size

Primary elemental types are supported in all arithmetic operations.

Warning

Integer types are signless, i.e., the type does not encode whether the represented value is to be interpreted as a signed or unsigned value. For operations where this distinction is semantically meaningful signedness is controlled via flags on each arithmetic operation.

5.1.2. Alternative Types
Tile IR also supports a set of non-standard but hardware accelerated floating-point types. Due to the nature of these types and hardware they each come with a set of restrictions.

Alternative Types
Type

Size

Description

tf32

32

floating-point format with 8 bits for exponent and 10 bits for mantissa. Storage size is 4 bytes with 4-byte alignment

bf16

16

floating-point format with 8 bits for exponent and 7 bits for mantissa

e4m3

8

floating-point format with 4 bits for exponent and 3 bits for mantissa

e5m2

8

floating-point format with 5 bits for exponent and 2 bits for mantissa

Tensors of these types may be created, manipulated and loaded and stored from global memory, but certain computations on them are restricted.

5.1.3. Floating-Point Conversion Semantics
When converting values to a floating-point type (via cuda_tile.ftof or cuda_tile.itof), the behavior for out-of-finite-range values and special values depends on the target type.

f16, f32, f64 (IEEE types) and bf16, tf32 (IEEE-like types): the closest representable value is selected according to the specified rounding mode. This may produce Inf when the source value exceeds the target’s finite range. NaN values are preserved.

e4m3, e5m2 (low-precision float types): use saturation-to-finite (satfinite) semantics, meaning the closest representable finite value is selected according to the specified rounding mode. Inf is never produced, even if the source value was Inf.

Table Floating-Point Conversion: Special Value and Saturation Behavior enumerates the behavior for the different supported floating-point types when converting various “corner case” values.

Floating-Point Conversion: Special Value and Saturation Behavior
Target Type

Out-of-Range Finite Source

Source is ±Inf

Source is NaN

f16, f32, f64, bf16, tf32

Nearest representable value (may produce Inf)

±Inf

NaN

e5m2

Nearest representable finite value (±MAX_NORM)

±MAX_NORM

NaN

e4m3

Nearest representable finite value (±MAX_NORM)

±MAX_NORM

+MAX_NORM

Note

The e4m3 type does not support NaN; NaN inputs are converted to positive MAX_NORM.

5.2. Pointers
Pointers, or values which contain memory addresses, are typed as pointers to a specific pointee type.

Pointer Types
Type

Size

Description

ptr<E>

64

a pointer to a location in memory; the data at the location represents a value of non-pointer element type E

The pointer points to a location in memory. The data at that location will be interpreted as being of element type E when loaded.

Pointer arithmetic also assumes the storage size of the type E for offset computations. Pointer types are parameterized by element types (i.e., nested pointer types are not supported). For details about converting between different pointer types, or integers see cuda_tile.bitcast.

5.3. Tensor Types
A tensor is a multi-dimensional, rectangular array described by a shape and element type. The shape is a vector that describes the number of elements across each axis of the tensor. The length of said vector describes the rank of the tensor, i.e., the number of its dimensions. All tensors in Tile IR have a statically known rank. Tile IR has two kinds of tensor types tiles and views.

5.3.1. Tile Type
A tile is a tensor with static shape, i.e., the extent across each dimension is known at compile time. Each extent must be a power of two.

Note

In Tile IR, all data values to be operated on are expressed as a tile. In particular, even scalar values are represented as a tile of rank zero.

We use tile<MxNxKxE> where M, N, K are integer numbers and E is an element type as syntax for tile types, see Syntax for more details.

Example Tile Types
Example Tile Type

Description

tile<2x8xf32>

a 2-dimensional tensor with 2 rows and 8 columns of f32 values

tile<f32>

a single value of type f32

tile<ptr<f32>>

a pointer to a value of type f32

tile<4x8xptr<f32>>

a 2-dimensional tensor with 4 rows and 8 columns of pointers to values of type f32

Note

A tile/tensor of pointers is typically used to load from or store to a batch of locations. The tile of pointers defines the shape of the values that are loaded or stored, with one pointer element mapping to one scalar value loaded or stored. It does not imply any structure on the locations themselves. For example, two consecutive pointers in the tile may not point to consecutive locations in memory. Even more, the same location may be present multiple times within a single tile of pointers. See Memory Model for a discussion of implications.

5.3.2. Tensor View
It is common that data in global memory follows a strided structure. For example, the widely adopted row-major or column-major layouts are strided. It is beneficial for the compiler to be aware of the strided layout of data in memory. Tile IR features a tensor view type to describe such structure in global memory.

Conceptually, a tensor view type describes an abstracted tensor of pointers. Like a regular tensor, it is described by a shape and the type of elements it points to. It in addition has a vector of striding factors.

The striding factors describe the relative position of locations the elements of the tensor view point to. If an element is 
 elements apart in dimension 
 of the tensor view, the corresponding locations in memory will be 
 elements away. This information can be used by the compiler to reason about access patterns and layouts of data in memory.

Values of type tensor view are typically never materialized in memory. Rather, they are stored as a compact description of a base-location, shape and striding factors. From this information, a tensor of pointers corresponding to the full view value can be computed using the following formula

where the 
 are the striding factors of the tensor view and 
 is the start address in global memory.

Other than the tile type, a tensor view supports dynamic extents in the shape and stride vectors. We use the ? character to denote these. Dynamic extents are bound at runtime to values when the view type is constructed using a cuda_tile.make_tensor_view operation.

A tensor view cannot be directly used to access memory. It first needs to be divided into tiles of static size. See Subview Types for options to do so.

A tensor view is constructed using the cuda_tile.make_tensor_view operation and consists of the components:

element_type, the type of the elements in the view

shape, an array of 64-bit integer describing the size of each dimension

strides, an array of 64-bit integer describing the stride of each dimension

Examples
!cuda_tile.tensor_view<1024x1024xf16, strides=[1024,1]>
!cuda_tile.tensor_view<32x16x32xf16, strides=[512,1,16]>
!cuda_tile.tensor_view<?x?xf16, strides=[?,1]>
!cuda_tile.tensor_view<?x16xf32, strides=[1,?]>
5.3.3. Subview Types
A tensor view is often too large to be loaded as a single tile for processing. Instead, it must first be subdivided into tiles. In Tile IR this is expressed using subview types.

Subviews describe a mapping from an index space to a space of statically-sized tiles loaded from a tensor view. They define the necessary index computations performed by a cuda_tile.load_view_tko and cuda_tile.store_view_tko when accessing elements from a tensor view.

Tile IR currently provides a single subview for partitioning a view into a grid of non-overlapping tiles but is designed to support additional subview types in the future that support different indexing patterns.

Partition View
partition_view is a subview type that represents a view partitioned into a grid of non-overlapping tiles. The index space in this case is the position of the tile in the grid. A tile partition view is specified by providing the size of the loaded tile. Like all tiles, the tile size needs to be a power of two.

Partition views are particularly useful in patterns like matrix multiplication, where a large tensor in global memory is traversed as non-overlapping tiles to form the final result.

The partition view structure is created using the cuda_tile.make_partition_view constructor.

It consists of:

tile_shape, the shape of the individual tiles in the view

view, the type of the view from which the subview is constructed

dim_map, an array of 32-bit integers mapping the tiles dimensions to the dimensions of the view.

padding_value, a flag defining the behavior of memory loading at the edges of the underlying tensor view.

These fields are all encoded as part of the type.

Concretely, a tensor view type of tensor_view<8192x128xf32, strides=[128,1]> can be partitioned into a grid of (64x32) tiles of size (128x4) each, which when loaded produce tiles with the type tile<128x4xf32>. When loading a tile form such a partition view, the index is the position in the (64, 32) grid. Loading element (4, 2) hence would return the tile starting at position (256, 64) in the underlying view.

Formally, given a tensor view with shape 
 and strides 
 and a partition view with tile size 
, a load or store at position 
 will load the elements at location

The index space of a partition view covers all tiles that would contain at least one element within the bounds of the underlying tensor view. For example, with a tensor view of shape (64, 256) and a partition view of tile shape (128, 128), the index space of the partition will have a shape of (1, 2) (and not, for example, (0, 2)).

Formally, given a tensor view with shape 
 and a partition view with tile size 
, the index space shape 
 is defined as

Warning

Indices into the partition view must lie within the index space of the partition view. Otherwise, the behavior is undefined.

When indices are within the index space but map to data that is partially out of the bounds of the underlying tensor view:

When loading, the out-of-bound values will be replaced with the partition view’s padding value (or unspecified values if no padding value is provided).

When storing, the out-of-bound values will be masked out.

Examples
!cuda_tile.partition_view<
  tile=(2),
  view=!cuda_tile.tensor_view<16xf32, strides=[1]>
>

!cuda_tile.partition_view<
  tile=(2x2),
  view=!cuda_tile.tensor_view<16x16xf32, strides=[16,1]>
>

!cuda_tile.partition_view<
  tile=(2x2),
  view=!cuda_tile.tensor_view<16x16xf32, strides=[16,1]>,
  dim_map=[1, 0]
>

!cuda_tile.partition_view<
  tile=(32x32),
  view=!cuda_tile.tensor_view<16x16xf32, strides=[16,1]>,
  padding_value=zero
>
5.4. Type Equivalence
Tile IR does not provide means to name types. Equivalence of types hence is a purely structural property: Two types are considered equal if they are structurally identical.

Note that some types form a natural subtype relationship. Types with dynamic shapes and strides like view cover the values that an identical type with all dynamic shapes and strides substituted with static values would cover. However, we consider these types distinct in Tile IR.
