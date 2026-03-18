# Changelog for CuTe DSL API changes[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/changelog.html#changelog-for-cute-dsl-api-changes "Link to this heading")

## [4.3.0](https://github.com/NVIDIA/cutlass/releases/tree/main) (2025-10-20)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/changelog.html#id2 "Link to this heading")

-   Debuggability improvements:
    
    -   Supported source location tracking for DSL APIs
    -   Supported dumping PTX and CUBIN
-   Removed deprecated `cutlass.<arch>_utils.SMEM_CAPACITY["<arch_str>"]` and `cutlass.utils.ampere_helpers`
-   Supported calling nested functions without capturing variables inside dynamic control flow
-   Replaced usage of `cute.arch.barrier` in examples with corresponding APIs in `pipeline`
    
    -   Use `pipeline.sync` for simple cases like synchronizing the whole CTA
    -   Use `pipeline.NamedBarrier` to customize barriers with different participating threads and barrier id
-   Added new APIs `repeat` and `repeat_as_tuple`
-   Added new APIs `make_rmem_tensor` to create tensor in register memory (replace `make_fragment` with better naming)
-   Added new APIs `make_rmem_tensor_like` which create rmem tensor from a tensor using the same shape with compact col-major strides
-   Added `TmemAllocator` for allocating tensor memory
-   Updated `SmemAllocator.allocate` to support allocation of a single scalar value
-   Fixed `TensorSSA.reduce` to support static value as initial value
-   Updated docstring for following APIs to be more concise and easier to understand:
    
    -   `make_layout_tv`
    -   `is_static`
    -   `PipelineAsync`
    -   `SmemAllocator`
-   Fixed documentation for `pipeline`, `utils` and `cute.math` (`cute.math` is part of top level documentation)

## [4.2.0](https://github.com/NVIDIA/cutlass/releases/tag/v4.2.0) (2025-09-10)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/changelog.html#id4 "Link to this heading")

-   Added back `cute.make_tiled_copy` per the request from community
-   Added support for explicit and implicit broadcast in `TensorSSA`
    
    -   `cutlass.cute.TensorSSA`: support `broadcast_to` and implicit broadcasting for binary operations.
-   Supported printing `TensorSSA` value in `cutlass.cute.print_tensor`
-   Updated `cute.gemm` to support all dispatch patterns and improved checks for illegal inputs
-   Introduced automatic kernel smem usage calculation for launch config.
-   Introduced per op fast-math control for math ops(e.g. `exp`, `exp2`, `log2`, `log`)
-   Introduced `CopyReduceBulkTensorTileS2GOp` in [tcgen05/copy.py](https://github.com/NVIDIA/cutlass/blob/main/python/CuTeDSL/cutlass/cute/nvgpu/tcgen05/copy.py) to support TMA Reduce.

## [4.1.0](https://github.com/NVIDIA/cutlass/releases/tag/v4.1.0) (2025-07-16)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/changelog.html#id6 "Link to this heading")

-   for loop
    
    -   Python built-in `range` now always generates codes and executes at runtime
    -   `cutlass.range` is advanced `range` with kernel code level unrolling and pipelining control
    -   Deprecated `cutlass.range_dynamic`, please replace with `range` or `cutlass.range`
    -   **Experimental** Added `pipelining` control for compiler generated software pipeline code
-   while/if
    
    -   `while`/`if` now by default generates codes and executes at runtime unless `cutlass.const_expr` is specified for the predicate
    -   Deprecated `cutlass.dynamic_expr`, please remove it
-   Rename mbarrier functions to reduce ambiguity
-   Modify SyncObject API (`MbarrierArray`, `NamedBarrier`, `TmaStoreFence`) to match `std::barrier`
-   Change pipeline `create` function to take only keyword arguments, and make `barrier_storage` optional.
-   Introduce `cutlass.cute.arch.get_dyn_smem_size` api to get runtime dynamic shared memory size.
-   Various API Support for SM100 BlockScaled Gemm
    
    -   Introduce BlockScaled MmaOps in [tcgen05/mma.py](https://github.com/NVIDIA/cutlass/blob/main/python/CuTeDSL/cutlass/cute/nvgpu/tcgen05/mma.py), and provide a `make_blockscaled_trivial_tiled_mma` function in [blackwell\_helpers.py](https://github.com/NVIDIA/cutlass/blob/main/python/CuTeDSL/cutlass/utils/blackwell_helpers.py) to help construct a BlockScaled TiledMma.
    -   Introduce S2T CopyOps in [tcgen05/copy.py](https://github.com/NVIDIA/cutlass/blob/main/python/CuTeDSL/cutlass/cute/nvgpu/tcgen05/copy.py).
    -   Introduce BlockScaled layout utilities in [blockscaled\_layout.py](https://github.com/NVIDIA/cutlass/blob/main/python/CuTeDSL/cutlass/utils/blockscaled_layout.py) for creating the required scale factor layouts in global memory, shared memory and tensor memory.
-   `cutlass.cute.compile` now supports compilation options. Refer to [JIT compilation options](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_compilation_options.html) for more details.
-   `cutlass.cute.testing.assert_` now works for device JIT function. Specify `--enable-assertions` as compilation option to enable.
-   `cutlass.cute.make_tiled_copy` is now deprecated. Please use `cutlass.cute.make_tiled_copy_tv` instead.
-   Shared memory capacity query
    
    -   Introduce `cutlass.utils.get_smem_capacity_in_bytes` for querying the shared memory capacity.
    -   `<arch>_utils.SMEM_CAPACITY["<arch_str>"]` is now deprecated.

## [4.0.0](https://github.com/NVIDIA/cutlass/releases/tag/v4.0.0) (2025-06-03)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/changelog.html#id9 "Link to this heading")

-   Fixed API mismatch in class `cute.runtime.Pointer`: change `element_type` to `dtype` to match `typing.Pointer`


# cutlass.cute[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#module-cutlass.cute "Link to this heading")

_class_ cutlass.cute.Swizzle(_\*args: Any_, _\*\*kwargs: Any_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Swizzle "Link to this definition")

Bases: `Value`

Swizzle is a transformation that permutes the elements of a layout.

Swizzles are used to rearrange data elements to improve memory access patterns and computational efficiency.

Swizzle is defined by three parameters: - MBase: The number of least-significant bits to keep constant - BBits: The number of bits in the mask - SShift: The distance to shift the mask

The mask is applied to the least-significant bits of the layout.

0bxxxxxxxxxxxxxxxYYYxxxxxxxZZZxxxx
                              ^--^ MBase is the number of least-sig bits to keep constant
                 ^-^       ^-^     BBits is the number of bits in the mask
                   ^---------^     SShift is the distance to shift the YYY mask
                                      (pos shifts YYY to the right, neg shifts YYY to the left)

e.g. Given
0bxxxxxxxxxxxxxxxxYYxxxxxxxxxZZxxx

the result is
0bxxxxxxxxxxxxxxxxYYxxxxxxxxxAAxxx where AA = ZZ \`xor\` YY

Copy to clipboard

_class_ cutlass.cute.struct(_cls_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct "Link to this definition")

Bases: `object`

Decorator to abstract C structure in Python DSL.

**Usage:**

\# Supports base\_dsl scalar int/float elements, array and nested struct:
@cute.struct
class complex:
    real : cutlass.Float32
    imag : cutlass.Float32

@cute.struct
class StorageA:
    mbarA : cute.struct.MemRange\[cutlass.Int64, stage\]
    compA : complex
    intA : cutlass.Int16

\# Supports alignment for its elements:
@cute.struct
class StorageB:
    a: cute.struct.Align\[
        cute.struct.MemRange\[cutlass.Float32, size\_a\], 1024
    \]
    b: cute.struct.Align\[
        cute.struct.MemRange\[cutlass.Float32, size\_b\], 1024
    \]
    x: cute.struct.Align\[cutlass.Int32, 16\]
    compA: cute.struct.Align\[complex, 16\]

\# Statically get size and alignment:
size \= StorageB.\_\_sizeof\_\_()
align \= StorageB.\_\_alignof\_\_()

\# Allocate and referencing elements:
storage \= allocator.allocate(StorageB)

storage.a\[0\] ...
storage.x ...
storage.compA.real ...

Copy to clipboard

Parameters:

**cls** – The struct class with annotations.

Returns:

The decorated struct class.

_class_ \_MemRangeMeta(_name_, _bases_, _dct_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeMeta "Link to this definition")

Bases: `type`

A metaclass for creating MemRange classes.

This metaclass is used to dynamically create MemRange classes with specific data types and sizes.

Variables:

-   **\_dtype** – The data type of the MemRange.
-   **\_size** – The size of the MemRange.

\_dtype _\= None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeMeta._dtype "Link to this definition")

\_size _\= None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeMeta._size "Link to this definition")

_property_ size[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeMeta.size "Link to this definition")

_property_ elem\_width[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeMeta.elem_width "Link to this definition")

_property_ size\_in\_bytes[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeMeta.size_in_bytes "Link to this definition")

_class_ MemRange[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct.MemRange "Link to this definition")

Bases: `object`

Defines a range of memory by MemRange\[T, size\].

_class_ \_MemRangeData(_dtype_, _size_, _base_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeData "Link to this definition")

Bases: `object`

Represents a range of memory.

Parameters:

-   **dtype** – The data type.
-   **size** – The size of the memory range in bytes.
-   **base** – The base address of the memory range.

\_\_init\_\_(_dtype_, _size_, _base_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeData.__init__ "Link to this definition")

Initializes a new memory range.

Parameters:

-   **dtype** – The data type.
-   **size** – Size of the memory range in bytes. A size of **0** is accepted, but in that case the range can only be used for its address (e.g. as a partition marker).
-   **base** – The base address of the memory range.

data\_ptr(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeData.data_ptr "Link to this definition")

Returns start pointer to the data in this memory range.

Returns:

A pointer to the start of the memory range.

Raises:

**AssertionError** – If the size of the memory range is negative.

get\_tensor(

_layout_,

_swizzle\=None_,

_dtype\=None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._MemRangeData.get_tensor "Link to this definition")

Creates a tensor from the memory range.

Parameters:

-   **layout** – The layout of the tensor.
-   **swizzle** – Optional swizzle pattern.
-   **dtype** – Optional data type; defaults to the memory range’s data type if not specified.

Returns:

A tensor representing the memory range.

Raises:

-   **TypeError** – If the layout is incompatible with the swizzle.
-   **AssertionError** – If the size of the memory range is not greater than zero.

_class_ \_AlignMeta(_name_, _bases_, _dct_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._AlignMeta "Link to this definition")

Bases: `type`

Aligns the given object by setting its alignment attribute.

Parameters:

-   **v** – The object to align. Must be a struct, MemRange, or a scalar type.
-   **align** – The alignment value to set.

Raises:

**TypeError** – If the object is not a struct, MemRange, or a scalar type.

Variables:

-   **\_dtype** – The data type to be aligned.
-   **\_align** – The alignment of the data type.

\_dtype _\= None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._AlignMeta._dtype "Link to this definition")

\_align _\= None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._AlignMeta._align "Link to this definition")

_property_ dtype[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._AlignMeta.dtype "Link to this definition")

_property_ align[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._AlignMeta.align "Link to this definition")

_class_ Align[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct.Align "Link to this definition")

Bases: `object`

Aligns the given type by Align\[T, alignment\].

_static_ \_is\_scalar\_type(_dtype_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct._is_scalar_type "Link to this definition")

Checks if the given type is a scalar numeric type.

Parameters:

**dtype** – The type to check.

Returns:

True if the type is a subclass of Numeric, False otherwise.

\_\_init\_\_(_cls_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct.__init__ "Link to this definition")

Initializes a new struct decorator instance.

Parameters:

**cls** – The class representing the structured data type.

Raises:

**TypeError** – If the struct is empty.

size\_in\_bytes() → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct.size_in_bytes "Link to this definition")

Returns the size of the struct in bytes.

Returns:

The size of the struct.

_static_ align\_offset(_offset_, _align_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct.align_offset "Link to this definition")

Return the round-up offset up to the next multiple of align.

cutlass.cute.E(_mode: int | List\[int\]_) → ScaledBasis[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.E "Link to this definition")

Create a unit ScaledBasis element with the specified mode.

This function creates a ScaledBasis with value 1 and the given mode. The mode represents the coordinate axis or dimension in the layout.

Parameters:

**mode** (_Union__\[__int__,_ _List__\[__int__\]__\]_) – The mode (dimension) for the basis element, either a single integer or a list of integers

Returns:

A ScaledBasis with value 1 and the specified mode

Return type:

ScaledBasis

Raises:

**TypeError** – If mode is not an integer or a list

**Examples:**

\# Create a basis element for the first dimension (mode 0)
e0 \= E(0)

\# Create a basis element for the second dimension (mode 1)
e1 \= E(1)

\# Create a basis element for a hierarchical dimension
e\_hier \= E(\[0, 1\])

Copy to clipboard

cutlass.cute.get\_divisibility(_x: int | cutlass.cute.typing.Integer_) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.get_divisibility "Link to this definition")

cutlass.cute.is\_static(_x: Any_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.is_static "Link to this definition")

Check if a value is statically known at compile time.

In CuTe, static values are those whose values are known at compile time, as opposed to dynamic values which are only known at runtime.

This function checks if a value is static by recursively traversing its type hierarchy and checking if all components are static.

Static values include: - Python literals (bool, int, float, None) - Static ScaledBasis objects - Static ComposedLayout objects - Static IR types - Tuples containing only static values

Dynamic values include: - Numeric objects (representing runtime values) - Dynamic expressions - Any tuple containing dynamic values

Parameters:

**x** (_Any_) – The value to check

Returns:

True if the value is static, False otherwise

Return type:

bool

Raises:

**TypeError** – If an unsupported type is provided

cutlass.cute.has\_underscore(_a: cutlass.cute.typing.XTuple_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.has_underscore "Link to this definition")

cutlass.cute.pretty\_str(_arg_) → str[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.pretty_str "Link to this definition")

Constructs a concise readable pretty string.

cutlass.cute.printf(_\*args_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.printf "Link to this definition")

Print one or more values with optional formatting.

This function provides printf-style formatted printing capabilities. It can print values directly or format them using C-style format strings. The function supports printing various types including layouts, numeric values, tensors, and other CuTe objects.

The function accepts either: 1. A list of values to print directly 2. A format string followed by values to format

Parameters:

-   **args** (_Any_) – Variable length argument list containing either: - One or more values to print directly - A format string followed by values to format
-   **loc** (_Optional__\[__Location__\]_) – Source location information for debugging, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for code generation, defaults to None

Raises:

-   **ValueError** – If no arguments are provided
-   **TypeError** – If an unsupported argument type is passed

**Examples:**

Direct printing of values:

a \= cute.make\_layout(shape\=(10, 10), stride\=(10, 1))
b \= cutlass.Float32(1.234)
cute.printf(a, b)  \# Prints values directly

Copy to clipboard

Formatted printing:

\# Using format string with generic format specifiers
cute.printf("a={}, b={}", a, b)

\# Using format string with C-style format specifiers
cute.printf("a={}, b=%.2f", a, b)

Copy to clipboard

cutlass.cute.front(_input_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.front "Link to this definition")

Recursively get the first element of input.

This function traverses a hierarchical structure (like a layout or tensor) and returns the first element at the deepest level. It’s particularly useful for accessing the first stride value in a layout to determine properties like majorness.

Parameters:

-   **input** (_Union__\[__Tensor__,_ _Layout__,_ _Stride__\]_) – The hierarchical structure to traverse
-   **loc** (_source location__,_ _optional_) – Source location where it’s called, defaults to None
-   **ip** (_insertion pointer__,_ _optional_) – Insertion pointer for IR generation, defaults to None

Returns:

The first element at the deepest level of the input structure

Return type:

Union\[int, float, bool, ir.Value\]

cutlass.cute.is\_major(

_mode_,

_stride: cutlass.cute.typing.Stride_,

_\*_,

_loc\=None_,

_ip\=None_,

) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.is_major "Link to this definition")

Check whether a mode in stride is the major mode.

cutlass.cute.assume(_src_, _divby\=None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.assume "Link to this definition")

cutlass.cute.make\_swizzle(_b_, _m_, _s_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_swizzle "Link to this definition")

cutlass.cute.static(_value_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.static "Link to this definition")

cutlass.cute.get\_leaves(_value_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.get_leaves "Link to this definition")

cutlass.cute.depth(

_a: cutlass.cute.typing.XTuple | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.depth "Link to this definition")

Returns the depth (nesting level) of a tuple, layout, or tensor.

The depth of a tuple is the maximum depth of its elements plus 1. For an empty tuple, the depth is 1. For layouts and tensors, the depth is determined by the depth of their shape. For non-tuple values (e.g., integers), the depth is considered 0.

Parameters:

**a** (_Union__\[__XTuple__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__,_ _Any__\]_) – The object whose depth is to be determined

Returns:

The depth of the input object

Return type:

int

**Example:**

\>>> depth(1)
0
\>>> depth((1, 2))
1
\>>> depth(((1, 2), (3, 4)))
2

Copy to clipboard

cutlass.cute.rank(

_a: cutlass.cute.typing.XTuple | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_mode: List\[int\] \= \[\]_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.rank "Link to this definition")

Returns the rank (dimensionality) of a tuple, layout, or tensor.

The rank of a tuple is its length. For layouts and tensors, the rank is determined by the rank of their shape. For non-tuple values (e.g., integers), the rank is considered 1 for convenience.

Parameters:

**a** (_Union__\[__XTuple__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__,_ _Any__\]_) – The object whose rank is to be determined

Returns:

The rank of the input object

Return type:

int

This function is used in layout algebra to determine the dimensionality of tensors and layouts for operations like slicing and evaluation.

cutlass.cute.is\_congruent(

_a: cutlass.cute.typing.XTuple | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor_,

_b: cutlass.cute.typing.XTuple | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor_,

) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.is_congruent "Link to this definition")

Returns whether a is congruent to b.

Congruence is an equivalence relation between hierarchical structures.

Two objects are congruent if: \* They have the same rank, AND \* They are both non-tuple values, OR \* They are both tuples AND all corresponding elements are congruent.

Congruence requires type matching at each level – scalar values match with scalar values, and tuples match with tuples of the same rank.

Parameters:

-   **a** (_Union__\[__XTuple__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – First object to compare
-   **b** (_Union__\[__XTuple__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – Second object to compare

Returns:

True if a and b are congruent, False otherwise

Return type:

bool

cutlass.cute.is\_weakly\_congruent(

_a: cutlass.cute.typing.XTuple | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor_,

_b: cutlass.cute.typing.XTuple | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor_,

) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.is_weakly_congruent "Link to this definition")

Returns whether a is weakly congruent to b.

Weak congruence is a partial order on hierarchical structures.

Object X is weakly congruent to object Y if: \* X is a non-tuple value, OR \* X and Y are both tuples of the same rank AND all corresponding elements are weakly congruent.

Weak congruence allows scalar values to match with tuples, making it useful for determining whether an object has a hierarchical structure “up to” another.

Parameters:

-   **a** (_Union__\[__XTuple__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – First object to compare
-   **b** (_Union__\[__XTuple__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – Second object to compare

Returns:

True if a and b are weakly congruent, False otherwise

Return type:

bool

cutlass.cute.get(_input_, _mode: List\[int\]_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.get "Link to this definition")

Extract a specific element or sub-layout from a layout or tuple.

This function recursively traverses the input according to the mode indices, extracting the element at the specified path. For layouts, this operation corresponds to extracting a specific sub-layout.

Parameters:

-   **input** (_Layout__,_ _ComposedLayout__,_ _tuple_) – The input layout or tuple to extract from
-   **mode** (_List__\[__int__\]_) – Indices specifying the path to traverse for extraction
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

The extracted element or sub-layout

Return type:

Layout, ComposedLayout, or element type

Raises:

-   **ValueError** – If any index in mode is out of range
-   **TypeError** – If mode contains non-integer elements or if input has unsupported type

Postcondition:

`get(t, mode=find(x,t)) == x if find(x,t) != None else True`

**Examples:**

layout \= make\_layout(((4, 8), (16, 1), 8), stride\=((1, 4), (32, 0), 512))
sub\_layout \= get(layout, mode\=\[0, 1\])   \# 8:4
sub\_layout \= get(layout, mode\=\[1\])      \# (16, 1):(32, 0)

Copy to clipboard

cutlass.cute.select(_input_, _mode: List\[int\]_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.select "Link to this definition")

Select modes from input.

Parameters:

-   **input** (_Layout__,_ _ComposedLayout__,_ _tuple_) – Input to select from
-   **mode** (_List__\[__int__\]_) – Indices specifying which dimensions or elements to select
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

A new instance with selected dimensions/elements

Return type:

Layout, ComposedLayout, tuple

Raises:

-   **ValueError** – If any index in mode is out of range
-   **TypeError** – If the input type is invalid

**Examples:**

\# Select specific dimensions from a layout
layout \= make\_layout((4, 8, 16), stride\=(32, 4, 1))
selected \= select(layout, mode\=\[0, 2\])  \# Select mode 0 and mode 2
\# Result: (4, 16):(32, 1)

\# Select elements from a tuple
t \= (1, 2, 3, 4, 5)
selected \= select(t, mode\=\[0, 2, 4\])  \# Select mode 0, mode 2, and mode 4
\# Result: (1, 3, 5)

Copy to clipboard

cutlass.cute.group\_modes(

_input_,

_begin: int_,

_end: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.group_modes "Link to this definition")

Group modes of a hierarchical tuple or layout into a single mode.

This function groups a range of modes from the input object into a single mode, creating a hierarchical structure. For tuples, it creates a nested tuple containing the specified range of elements. For layouts and other CuTe objects, it creates a hierarchical representation where the specified modes are grouped together.

Parameters:

-   **input** (_Layout__,_ _ComposedLayout__,_ _tuple__,_ _Shape__,_ _Stride__,_ _etc._) – Input object to group modes from (layout, tuple, etc.)
-   **beg** (_int_) – Beginning index of the range to group (inclusive)
-   **end** (_int_) – Ending index of the range to group (exclusive)
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

A new object with the specified modes grouped

Return type:

Same type as input with modified structure

**Examples:**

\# Group modes in a tuple
t \= (2, 3, 4, 5)
grouped \= group\_modes(t, 1, 3)  \# (2, (3, 4), 5)

\# Group modes in a layout
layout \= make\_layout((2, 3, 4, 5))
grouped\_layout \= group\_modes(layout, 1, 3)  \# Layout with shape (2, (3, 4), 5)

\# Group modes in a shape
shape \= make\_shape(2, 3, 4, 5)
grouped\_shape \= group\_modes(shape, 0, 2)  \# Shape ((2, 3), 4, 5)

Copy to clipboard

cutlass.cute.slice\_(_src_, _coord: cutlass.cute.typing.Coord_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.slice_ "Link to this definition")

Perform a slice operation on a source object using the given coordinate.

This function implements CuTe’s slicing operation which extracts a subset of elements from a source object (tensor, layout, etc.) based on a coordinate pattern. The slice operation preserves the structure of the source while selecting specific elements.

Parameters:

-   **src** (_Union__\[__Tensor__,_ _Layout__,_ _IntTuple__,_ _Value__\]_) – Source object to be sliced (tensor, layout, tuple, etc.)
-   **coord** (_Coord_) – Coordinate pattern specifying which elements to select
-   **loc** (_Optional__\[__Location__\]_) – Source location information, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for IR generation, defaults to None

Returns:

A new object containing the sliced elements

Return type:

Union\[Tensor, Layout, IntTuple, tuple\]

Raises:

**ValueError** – If the coordinate pattern is incompatible with source

**Examples:**

\# Layout slicing
layout \= make\_layout((4,4))

\# Select 1st index of first mode and keep all elements in second mode
sub\_layout \= slice\_(layout, (1, None))

Copy to clipboard

\# Basic tensor slicing
tensor \= make\_tensor(...)           \# Create a 2D tensor

\# Select 1st index of first mode and keep all elements in second mode
sliced \= slice\_(tensor, (1, None))

Copy to clipboard

\# Select 2nd index of second mode and keep all elements in first mode
sliced \= slice\_(tensor, (None, 2))

Copy to clipboard

Note

-   None represents keeping all elements in that mode
-   Slicing preserves the layout/structure of the original object
-   Can be used for: \* Extracting sub-tensors/sub-layouts \* Creating views into data \* Selecting specific patterns of elements

cutlass.cute.prepend(

_input_,

_elem_,

_up\_to\_rank: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.prepend "Link to this definition")

Extend input to rank up\_to\_rank by prepending elem in front of input.

This function extends the input object by prepending elements to reach a desired rank. It supports various CuTe types including shapes, layouts, tensors etc.

Parameters:

-   **input** (_Union__\[__Shape__,_ _Stride__,_ _Coord__,_ _IntTuple__,_ _Tile__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – Source to be prepended to
-   **elem** (_Union__\[__Shape__,_ _Stride__,_ _Coord__,_ _IntTuple__,_ _Tile__,_ _Layout__\]_) – Element to prepend to input
-   **up\_to\_rank** (_Union__\[__None__,_ _int__\]__,_ _optional_) – The target rank after extension, defaults to None
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point, defaults to None

Returns:

The extended result with prepended elements

Return type:

Union\[Shape, Stride, Coord, IntTuple, Tile, Layout, ComposedLayout, Tensor\]

Raises:

-   **ValueError** – If up\_to\_rank is less than input’s current rank
-   **TypeError** – If input or elem has unsupported type

**Examples:**

\# Prepend to a Shape
shape \= (4,4)
prepend(shape, 2)                   \# Returns (2,4,4)

\# Prepend to a Layout
layout \= make\_layout((8,8))
prepend(layout, make\_layout((2,)))  \# Returns (2,8,8):(1,1,8)

\# Prepend with target rank
coord \= (1,1)
prepend(coord, 0, up\_to\_rank\=4)     \# Returns (0,0,1,1)

Copy to clipboard

cutlass.cute.append(

_input_,

_elem_,

_up\_to\_rank: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.append "Link to this definition")

Extend input to rank up\_to\_rank by appending elem to the end of input.

This function extends the input object by appending elements to reach a desired rank. It supports various CuTe types including shapes, layouts, tensors etc.

Parameters:

-   **input** (_Union__\[__Shape__,_ _Stride__,_ _Coord__,_ _IntTuple__,_ _Tile__,_ _Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – Source to be appended to
-   **elem** (_Union__\[__Shape__,_ _Stride__,_ _Coord__,_ _IntTuple__,_ _Tile__,_ _Layout__\]_) – Element to append to input
-   **up\_to\_rank** (_Union__\[__None__,_ _int__\]__,_ _optional_) – The target rank after extension, defaults to None
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point, defaults to None

Returns:

The extended result with appended elements

Return type:

Union\[Shape, Stride, Coord, IntTuple, Tile, Layout, ComposedLayout, Tensor\]

Raises:

-   **ValueError** – If up\_to\_rank is less than input’s current rank
-   **TypeError** – If input or elem has unsupported type

**Examples:**

\# Append to a Shape
shape \= (4,4)
append(shape, 2)                   \# Returns (4,4,2)

\# Append to a Layout
layout \= make\_layout((8,8))
append(layout, make\_layout((2,)))  \# Returns (8,8,2):(1,8,1)

\# Append with target rank
coord \= (1,1)
append(coord, 0, up\_to\_rank\=4)     \# Returns (1,1,0,0)

Copy to clipboard

Note

-   The function preserves the structure of the input while extending it
-   Can be used to extend tensors, layouts, shapes and other CuTe types
-   When up\_to\_rank is specified, fills remaining positions with elem
-   Useful for tensor reshaping and layout transformations

cutlass.cute.prepend\_ones(

_t: cutlass.cute.typing.Tensor_,

_up\_to\_rank: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.prepend_ones "Link to this definition")

cutlass.cute.append\_ones(_t_, _up\_to\_rank: int | None \= None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.append_ones "Link to this definition")

cutlass.cute.repeat\_as\_tuple(_x_, _n_) → tuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.repeat_as_tuple "Link to this definition")

Creates a tuple with x repeated n times.

This function creates a tuple by repeating the input value x n times.

Parameters:

-   **x** (_Any_) – The value to repeat
-   **n** (_int_) – Number of times to repeat x

Returns:

A tuple containing x repeated n times

Return type:

tuple

**Examples:**

repeat\_as\_tuple(1, 1)     \# Returns (1,)
repeat\_as\_tuple(1, 3)     \# Returns (1, 1, 1)
repeat\_as\_tuple(None, 4)  \# Returns (None, None, None, None)

Copy to clipboard

cutlass.cute.repeat(_x_, _n_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.repeat "Link to this definition")

Creates an object by repeating x n times.

This function creates an object by repeating the input value x n times. If n=1, returns x directly, otherwise returns a tuple of x repeated n times.

Parameters:

-   **x** (_Any_) – The value to repeat
-   **n** (_int_) – Number of times to repeat x

Returns:

x if n=1, otherwise a tuple containing x repeated n times

Return type:

Union\[Any, tuple\]

Raises:

**ValueError** – If n is less than 1

**Examples:**

repeat(1, 1)     \# Returns 1
repeat(1, 3)     \# Returns (1, 1, 1)
repeat(None, 4)  \# Returns (None, None, None, None)

Copy to clipboard

cutlass.cute.repeat\_like(_x_, _target_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.repeat_like "Link to this definition")

Creates an object congruent to target and filled with x.

This function recursively creates a nested tuple structure that matches the structure of the target, with each leaf node filled with the value x.

Parameters:

-   **x** (_Any_) – The value to fill the resulting structure with
-   **target** (_Union__\[__tuple__,_ _Any__\]_) – The structure to mimic

Returns:

A structure matching target but filled with x

Return type:

Union\[tuple, Any\]

**Examples:**

repeat\_like(0, (1, 2, 3))      \# Returns (0, 0, 0)
repeat\_like(1, ((1, 2), 3))    \# Returns ((1, 1), 1)
repeat\_like(2, 5)              \# Returns 2

Copy to clipboard

cutlass.cute.flatten(_a_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.flatten "Link to this definition")

Flattens a CuTe data structure into a simpler form.

For tuples, this function flattens the structure into a single-level tuple. For layouts, it returns a new layout with flattened shape and stride. For tensors, it returns a new tensor with flattened layout. For other types, it returns the input unchanged.

Parameters:

**a** (_Union__\[__IntTuple__,_ _Coord__,_ _Shape__,_ _Stride__,_ _Layout__,_ _Tensor__\]_) – The structure to flatten

Returns:

The flattened structure

Return type:

Union\[tuple, Any\]

**Examples:**

flatten((1, 2, 3))                      \# Returns (1, 2, 3)
flatten(((1, 2), (3, 4)))               \# Returns (1, 2, 3, 4)
flatten(5)                              \# Returns 5
flatten(Layout(shape, stride))          \# Returns Layout(flatten(shape), flatten(stride))
flatten(Tensor(layout))                 \# Returns Tensor(flatten(layout))

Copy to clipboard

cutlass.cute.filter\_zeros(_input_, _\*_, _target\_profile\=None_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.filter_zeros "Link to this definition")

Filter out zeros from a layout or tensor.

This function removes zero-stride dimensions from a layout or tensor. Refer to [NVIDIA/cutlass](https://github.com/NVIDIA/cutlass/blob/main/media/docs/cpp/cute/02_layout_algebra.md) for more layout algebra operations.

Parameters:

-   **input** (_Layout_ _or_ _Tensor_) – The input layout or tensor to filter
-   **target\_profile** (_Stride__,_ _optional_) – Target stride profile for the filtered result, defaults to None
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

The filtered layout or tensor with zeros removed

Return type:

Layout or Tensor

Raises:

**TypeError** – If input is not a Layout or Tensor

cutlass.cute.filter(_input_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.filter "Link to this definition")

Filter a layout or tensor.

This function filters a layout or tensor according to CuTe’s filtering rules.

Parameters:

-   **input** (_Layout_ _or_ _Tensor_) – The input layout or tensor to filter
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

The filtered layout or tensor

Return type:

Layout or Tensor

Raises:

**TypeError** – If input is not a Layout or Tensor

cutlass.cute.size(

_a: cutlass.cute.typing.IntTuple | cutlass.cute.typing.Shape | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor_,

_mode: List\[int\] \= \[\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.size "Link to this definition")

Return size of domain of layout or tensor.

Computes the size (number of elements) in the domain of a layout or tensor. For layouts, this corresponds to the shape of the coordinate space. See [NVIDIA/cutlass](https://github.com/NVIDIA/cutlass/blob/main/media/docs/cpp/cute/01_layout.md) for more details on layout domains.

Parameters:

-   **a** (_IntTuple__,_ _Shape__,_ _Layout__,_ _ComposedLayout_ _or_ _Tensor_) – The input object whose size to compute
-   **mode** (_list_ _of_ _int__,_ _optional_) – List of mode(s) for size calculation. If empty, computes total size, defaults to \[\]
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

Static size of layout or tensor if static, otherwise a Value

Return type:

int or Value

Raises:

**ValueError** – If mode contains non-integer elements

cutlass.cute.shape\_div(

_lhs: cutlass.cute.typing.Shape_,

_rhs: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.shape_div "Link to this definition")

Perform element-wise division of shapes.

This function performs element-wise division between two shapes.

Parameters:

-   **lhs** (_Shape_) – Left-hand side shape
-   **rhs** (_Shape_) – Right-hand side shape
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

The result of element-wise division

Return type:

Shape

cutlass.cute.ceil\_div(

_input: cutlass.cute.typing.Shape_,

_tiler: cutlass.cute.typing.Tiler_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ceil_div "Link to this definition")

Compute the ceiling division of a target shape by a tiling specification.

This function computes the number of tiles required to cover the target domain. It is equivalent to the second mode of zipped\_divide(input, tiler).

Parameters:

-   **input** (_Shape_) – A tuple of integers representing the dimensions of the target domain.
-   **tiler** (_Union__\[__Layout__,_ _Shape__,_ _Tile__\]_) – The tiling specification.
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional instruction pointer or context for underlying IR functions.

Returns:

A tuple of integers representing the number of tiles required along each dimension, i.e. the result of the ceiling division of the input dimensions by the tiler dimensions.

Return type:

Shape

Example:

import cutlass.cute as cute
@cute.jit
def foo():
    input \= (10, 6)
    tiler \= (3, 4)
    result \= cute.ceil\_div(input, tiler)
    print(result)  \# Outputs: (4, 2)

Copy to clipboard

cutlass.cute.round\_up(

_a: cutlass.cute.typing.IntTuple_,

_b: cutlass.cute.typing.IntTuple_,

) → cutlass.cute.typing.IntTuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.round_up "Link to this definition")

Rounds up elements of a using elements of b.

cutlass.cute.make\_layout(

_shape: cutlass.cute.typing.Shape_,

_\*_,

_stride: cutlass.cute.typing.Stride | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_layout "Link to this definition")

Create a CuTe Layout object from shape and optional stride information.

A Layout in CuTe represents the mapping between logical and physical coordinates of a tensor. This function creates a Layout object that defines how tensor elements are arranged in memory.

Parameters:

-   **shape** (_Shape_) – Shape of the layout defining the size of each mode
-   **stride** (_Union__\[__Stride__,_ _None__\]_) – Optional stride values for each mode, defaults to None
-   **loc** (_Optional__\[__Location__\]_) – Source location information, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for IR generation, defaults to None

Returns:

A new Layout object with the specified shape and stride

Return type:

Layout

**Examples:**

\# Create a 2D compact left-most layout with shape (4,4)
layout \= make\_layout((4,4))                     \# compact left-most layout

\# Create a left-most layout with custom strides
layout \= make\_layout((4,4), stride\=(1,4))       \# left-most layout with strides (1,4)

\# Create a layout for a 3D tensor
layout \= make\_layout((32,16,8))                 \# left-most layout

\# Create a layout with custom strides
layout \= make\_layout((2,2,2), stride\=(4,1,2))   \# layout with strides (4,1,2)

Copy to clipboard

Note

-   If stride is not provided, a default compact left-most stride is computed based on the shape
-   The resulting layout maps logical coordinates to physical memory locations
-   The layout object can be used for tensor creation and memory access patterns
-   Strides can be used to implement: \* Row-major vs column-major layouts \* Padding and alignment \* Blocked/tiled memory arrangements \* Interleaved data formats
-   Stride is keyword only argument to improve readability, e.g. \* make\_layout((3,4), (1,4)) can be confusing with make\_layout(((3,4), (1,4))) \* make\_layout((3,4), stride=(1,4)) is more readable

cutlass.cute.make\_identity\_layout(

_shape: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_identity_layout "Link to this definition")

Create an identity layout with the given shape.

An identity layout maps logical coordinates directly to themselves without any transformation. This is equivalent to a layout with stride (1@0,1@1,…,1@(N-1)).

Parameters:

-   **shape** (_Shape_) – The shape of the layout
-   **loc** (_Optional__\[__Location__\]_) – Source location information, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for IR generation, defaults to None

Returns:

A new identity Layout object with the specified shape

Return type:

Layout

**Examples:**

\# Create a 2D identity layout with shape (4,4)
layout \= make\_identity\_layout((4,4))     \# stride=(1@0,1@1)

\# Create a 3D identity layout
layout \= make\_identity\_layout((32,16,8)) \# stride=(1@0,1@1,1@2)

Copy to clipboard

Note

-   An identity layout is a special case where each coordinate maps to itself
-   Useful for direct coordinate mapping without any transformation

cutlass.cute.make\_ordered\_layout(

_shape: cutlass.cute.typing.Shape_,

_order: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_ordered_layout "Link to this definition")

Create a layout with a specific ordering of dimensions.

This function creates a layout where the dimensions are ordered according to the specified order parameter, allowing for custom dimension ordering in the layout.

Parameters:

-   **shape** (_Shape_) – The shape of the layout
-   **order** (_Shape_) – The ordering of dimensions
-   **loc** (_Optional__\[__Location__\]_) – Source location information, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for IR generation, defaults to None

Returns:

A new Layout object with the specified shape and dimension ordering

Return type:

Layout

**Examples:**

\# Create a row-major layout
layout \= make\_ordered\_layout((4,4), order\=(1,0))

\# Create a column-major layout
layout \= make\_ordered\_layout((4,4), order\=(0,1))         \# stride=(1,4)

\# Create a layout with custom dimension ordering for a 3D tensor
layout \= make\_ordered\_layout((32,16,8), order\=(2,0,1))   \# stride=(128,1,16)

Copy to clipboard

Note

-   The order parameter specifies the ordering of dimensions from fastest-varying to slowest-varying
-   For a 2D tensor, (0,1) creates a column-major layout, while (1,0) creates a row-major layout
-   The length of order must match the rank of the shape

cutlass.cute.make\_layout\_like(

_input: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_layout_like "Link to this definition")

cutlass.cute.make\_composed\_layout(

_inner_,

_offset: cutlass.cute.typing.IntTuple_,

_outer: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_composed_layout "Link to this definition")

Create a composed layout by composing an inner transformation with an outer layout.

A composed layout applies a sequence of transformations to coordinates. The composition is defined as (inner ∘ offset ∘ outer), where the operations are applied from right to left.

Parameters:

-   **inner** (_Union__\[__Layout__,_ [_Swizzle_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Swizzle "cutlass.cute.Swizzle")_\]_) – The inner transformation (can be a Layout or Swizzle)
-   **offset** (_IntTuple_) – An integral offset applied between transformations
-   **outer** (_Layout_) – The outer (right-most) layout that is applied first
-   **loc** (_Optional__\[__Location__\]_) – Source location information, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for IR generation, defaults to None

Returns:

A new ComposedLayout representing the composition

Return type:

ComposedLayout

**Examples:**

\# Create a basic layout
inner \= make\_layout(...)
outer \= make\_layout((4,4), stride\=(E(0), E(1)))

\# Create a composed layout with an offset
composed \= make\_composed\_layout(inner, (2,0), outer)

Copy to clipboard

Note

-   The composition applies transformations in the order: outer → offset → inner
-   The stride divisibility condition must be satisfied for valid composition
-   Certain compositions (like Swizzle with scaled basis) are invalid and will raise errors
-   Composed layouts inherit many properties from the outer layout

cutlass.cute.cosize(

_a: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor_,

_mode: List\[int\] \= \[\]_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.cosize "Link to this definition")

Return size of codomain of layout or tensor. Return static value if type is static.

For a layout `L = S:D` where `S` is the shape and `D` is the stride, the codomain size is the minimum size needed to store all possible offsets generated by the layout. This is calculated by taking the maximum offset plus 1.

For example, given a layout `L = (4,(3,2)):(2,(8,1))`:

-   Shape `S = (4,(3,2))`
-   Stride `D = (2,(8,1))`
-   Maximum offset = `2*(4-1) + 8*(3-1) + 1*(2-1) = 6 + 16 + 1 = 23`
-   Therefore `cosize(L) = 24`

**Examples:**

L \= cute.make\_layout((4,(3,2)), stride\=(2,(8,1))) \# L = (4,(3,2)):(2,(8,1))
print(cute.cosize(L))  \# => 24

Copy to clipboard

Parameters:

-   **a** (_Union__\[__Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – Layout, ComposedLayout, or Tensor object
-   **mode** (_List__\[__int__\]__,_ _optional_) – List of mode(s) for cosize calculation. If empty, calculates over all modes. If specified, calculates cosize only for the given modes.
-   **loc** (_optional_) – Location information for diagnostics, defaults to None
-   **ip** (_optional_) – Instruction pointer for diagnostics, defaults to None

Returns:

Static size of layout or tensor (fast fold) if static, or a dynamic Value

Return type:

Union\[int, Value\]

cutlass.cute.size\_in\_bytes(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_layout: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → int | cutlass.cute.typing.Integer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.size_in_bytes "Link to this definition")

Calculate the size in bytes based on its data type and layout. The result is rounded up to the nearest byte.

Parameters:

-   **dtype** (_Type__\[__Numeric__\]_) – The DSL numeric data type
-   **layout** (_Layout__,_ _optional_) – The layout of the elements. If None, the function returns 0
-   **loc** (_optional_) – Location information for diagnostics, defaults to None
-   **ip** (_optional_) – Instruction pointer for diagnostics, defaults to None

Returns:

The total size in bytes. Returns 0 if the layout is None

Return type:

int

cutlass.cute.coalesce(

_input_,

_\*_,

_target\_profile: cutlass.cute.typing.Coord | None \= None_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.coalesce "Link to this definition")

cutlass.cute.crd2idx(

_coord: cutlass.cute.typing.Coord_,

_layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.crd2idx "Link to this definition")

Convert a multi-dimensional coordinate into a value using the specified layout.

This function computes the inner product of the flattened coordinate and stride:

> index = sum(flatten(coord)\[i\] \* flatten(stride)\[i\] for i in range(len(coord)))

Parameters:

-   **coord** (_Coord_) – A tuple or list representing the multi-dimensional coordinate (e.g., (i, j) for a 2D layout).
-   **layout** (_Layout_ _or_ _ComposedLayout_) – A layout object that defines the memory storage layout, including shape and stride, used to compute the inner product.
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional instruction pointer or context for underlying IR functions.

Returns:

The result of applying the layout transformation to the provided coordinate.

Return type:

Any type that the layout maps to

**Example:**

import cutlass.cute as cute
@cute.jit
def foo():
    L \= cute.make\_layout((5, 4), stride\=(4, 1))
    idx \= cute.crd2idx((2, 3), L)
    \# Computed as: 2 \* 4 + 3 = 11
    print(idx)
foo()  \# Expected output: 11

Copy to clipboard

cutlass.cute.idx2crd(_idx_, _shape_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.idx2crd "Link to this definition")

Convert a linear index back into a multi-dimensional coordinate using the specified layout.

Mapping from a linear index to the corresponding multi-dimensional coordinate in the layout’s coordinate space. It essentially “unfolds” a linear index into its constituent coordinate components.

Parameters:

-   **idx** (_: int/Integer/Tuple_) – The linear index to convert back to coordinates.
-   **shape** (_Shape_) – Shape of the layout defining the size of each mode
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional instruction pointer or context for underlying IR functions.

Returns:

The result of applying the layout transformation to the provided coordinate.

Return type:

Coord

**Examples:**

import cutlass.cute as cute
@cute.jit
def foo():
    coord \= cute.idx2crd(11, (5, 4))
    \# idx2crd is always col-major
    \# For shape (m, n, l, ...), coord = (idx % m, idx // m % n, idx // m // n % l, ...
    \# Computed as: (11 % 5, 11 // 5 % 4) = (1, 2)
    print(coord)

foo()  \# Expected output: (1, 2)

Copy to clipboard

cutlass.cute.recast\_layout(

_new\_type\_bits: int_,

_old\_type\_bits: int_,

_src\_layout: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.recast_layout "Link to this definition")

Recast a layout from one data type to another.

Parameters:

-   **new\_type\_bits** (_int_) – The new data type bits
-   **old\_type\_bits** (_int_) – The old data type bits
-   **src\_layout** (_Union__\[__Layout__,_ _ComposedLayout__\]_) – The layout to recast
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional instruction pointer or context for underlying IR functions.

Returns:

The recast layout

Return type:

Layout or ComposedLayout

**Example:**

import cutlass.cute as cute
@cute.jit
def foo():
    \# Create a layout
    L \= cute.make\_layout((2, 3, 4))
    \# Recast the layout to a different data type
    L\_recast \= cute.recast\_layout(16, 8, L)
    print(L\_recast)
foo()  \# Expected output: (2, 3, 4)

Copy to clipboard

cutlass.cute.slice\_and\_offset(_coord_, _src_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.slice_and_offset "Link to this definition")

cutlass.cute.recast\_ptr(

_ptr: cutlass.cute.typing.Pointer_,

_swizzle\_\=None_,

_dtype: Type\[cutlass.cute.typing.Numeric\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.recast_ptr "Link to this definition")

cutlass.cute.make\_ptr(

_dtype: Type\[cutlass.cute.typing.Numeric\] | None_,

_value_,

_mem\_space: cutlass.cute.typing.AddressSpace \= cutlass.cute.typing.AddressSpace.generic_,

_\*_,

_assumed\_align\=None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_ptr "Link to this definition")

cutlass.cute.composition(

_lhs_,

_rhs: cutlass.cute.typing.Layout | cutlass.cute.typing.Shape | cutlass.cute.typing.Tile_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.composition "Link to this definition")

Compose two layout representations using the CuTe layout algebra.

Compose a left-hand layout (or tensor) with a right-hand operand into a new layout R, such that for every coordinate c in the domain of the right-hand operand, the composed layout satisfies:

> R(c) = A(B(c))

where A is the left-hand operand provided as `lhs` and B is the right-hand operand provided as `rhs`. In this formulation, B defines the coordinate domain while A applies its transformation to B’s output, and the resulting layout R inherits the stride and shape adjustments from A.

Satisfies:

cute.shape(cute.composition(lhs, rhs)) is compatible with cute.shape(rhs)

Parameters:

-   **lhs** (_Layout_ _or_ _Tensor_) – The left-hand operand representing the transformation to be applied.
-   **rhs** (_Layout__,_ _Shape__, or_ _Tile__, or_ _int_ _or_ _tuple_) – The right-hand operand defining the coordinate domain. If provided as an int or tuple, it will be converted to a tile layout.
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional instruction pointer or context for underlying IR functions.

Returns:

A new composed layout R, such that for all coordinates c in the domain of `rhs`, R(c) = lhs(rhs(c)).

Return type:

Layout or Tensor

**Example:**

import cutlass.cute as cute
@cute.jit
def foo():
    \# Create a layout that maps (i,j) to i\*4 + j
    L1 \= cute.make\_layout((2, 3), stride\=(4, 1))
    \# Create a layout that maps (i,j) to i\*3 + j
    L2 \= cute.make\_layout((3, 4), stride\=(3, 1))
    \# Compose L1 and L2
    L3 \= cute.composition(L1, L2)
    \# L3 now maps coordinates through L2 then L1

Copy to clipboard

cutlass.cute.complement(

_input: cutlass.cute.typing.Layout_,

_cotarget: cutlass.cute.typing.Layout | cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.complement "Link to this definition")

Compute the complement layout of the input layout with respect to the cotarget.

The complement of a layout A with respect to cotarget n is a layout A\* such that for every k in Z\_n and c in the domain of A, there exists a unique c\* in the domain of A\* where k = A(c) + A\*(c\*).

This operation is useful for creating layouts that partition a space in complementary ways, such as row and column layouts that together cover a matrix.

Parameters:

-   **input** (_Layout_) – The layout to compute the complement of
-   **cotarget** (_Union__\[__Layout__,_ _Shape__\]_) – The target layout or shape that defines the codomain
-   **loc** (_optional_) – Optional location information for IR diagnostics
-   **ip** (_optional_) – Optional instruction pointer or context for underlying IR functions

Returns:

The complement layout

Return type:

Layout

**Example:**

import cutlass.cute as cute
@cute.jit
def foo():
    \# Create a right-major layout for a 4x4 matrix
    row\_layout \= cute.make\_layout((4, 4), stride\=(4, 1))
    \# Create a left-major layout that complements the row layout
    col\_layout \= cute.complement(row\_layout, 16)
    \# The two layouts are complementary under 16

Copy to clipboard

cutlass.cute.right\_inverse(

_input: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.right_inverse "Link to this definition")

cutlass.cute.left\_inverse(

_input: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.left_inverse "Link to this definition")

cutlass.cute.logical\_product(

_block_,

_tiler: cutlass.cute.typing.Tile_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.logical_product "Link to this definition")

cutlass.cute.zipped\_product(

_block_,

_tiler: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.zipped_product "Link to this definition")

cutlass.cute.tiled\_product(

_block_,

_tiler: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.tiled_product "Link to this definition")

cutlass.cute.flat\_product(

_block_,

_tiler: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.flat_product "Link to this definition")

cutlass.cute.raked\_product(

_block_,

_tiler: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.raked_product "Link to this definition")

cutlass.cute.blocked\_product(

_block_,

_tiler: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.blocked_product "Link to this definition")

cutlass.cute.logical\_divide(

_target_,

_tiler: cutlass.cute.typing.Tiler_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.logical_divide "Link to this definition")

cutlass.cute.zipped\_divide(

_target_,

_tiler: cutlass.cute.typing.Tiler_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.zipped_divide "Link to this definition")

`zipped_divide` is `logical_divide` with Tiler modes and Rest modes gathered together: `(Tiler,Rest)`

-   When Tiler is Layout, this has no effect as `logical_divide` results in the same.
-   When Tiler is `Tile` (nested tuple of `Layout`) or `Shape`, this zips modes into standard form `((BLK_A,BLK_B),(a,b,x,y))`

For example, if `target` has shape `(s, t, r)` and `tiler` has shape `(BLK_A, BLK_B)`, then the result will have shape `((BLK_A, BLK_B), (ceil_div(s, BLK_A), ceil_div(t, BLK_B), r))`.

Parameters:

-   **target** (_Layout_ _or_ _Tensor_) – The layout or tensor to partition.
-   **tiler** (_Tiler_) – The tiling specification (can be a Layout, Shape, Tile).
-   **loc** (_optional_) – Optional MLIR IR location information.
-   **ip** (_optional_) – Optional MLIR IR insertion point.

Returns:

A zipped (partitioned) version of the target.

Return type:

Layout or Tensor

**Example:**

layout \= cute.make\_layout((128, 64), stride\=(64, 1))
tiler \= (8, 8)
result \= cute.zipped\_divide(layout, tiler)  \# result shape: ((8, 8), (16, 8))

Copy to clipboard

cutlass.cute.tiled\_divide(

_target_,

_tiler: cutlass.cute.typing.Tiler_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.tiled_divide "Link to this definition")

cutlass.cute.flat\_divide(

_target_,

_tiler: cutlass.cute.typing.Tile_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.flat_divide "Link to this definition")

cutlass.cute.max\_common\_layout(

_a: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_b: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.max_common_layout "Link to this definition")

cutlass.cute.max\_common\_vector(

_a: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_b: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.max_common_vector "Link to this definition")

cutlass.cute.tile\_to\_shape(

_atom_,

_trg\_shape: cutlass.cute.typing.Shape_,

_order: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.tile_to_shape "Link to this definition")

cutlass.cute.local\_partition(

_target: cutlass.cute.typing.Tensor_,

_tiler: cutlass.cute.typing.Layout | cutlass.cute.typing.Shape_,

_index: int | cutlass.cute.typing.Numeric_,

_proj: cutlass.cute.typing.XTuple \= 1_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.local_partition "Link to this definition")

cutlass.cute.local\_tile(

_input: cutlass.cute.typing.Tensor_,

_tiler: cutlass.cute.typing.Tiler_,

_coord: cutlass.cute.typing.Coord_,

_proj: cutlass.cute.typing.XTuple | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.local_tile "Link to this definition")

Partition a tensor into tiles using a tiler and extract a single tile at the provided coordinate.

The `local_tile` operation applies a `zipped_divide` to split the `input` tensor by the `tiler` and then slices out a single tile using the provided coord. This is commonly used for extracting block-, thread-, or CTA-level tiles for parallel operations.

local\_tile(input,tiler,coord)\=zipped\_divide(input,tiler)\[coord\]

This function corresponds to the CUTE/C++ local\_tile utility: [https://docs.nvidia.com/cutlass/media/docs/cpp/cute/03\_tensor.html#local-tile](https://docs.nvidia.com/cutlass/media/docs/cpp/cute/03_tensor.html#local-tile)

Parameters:

-   **input** (_Tensor_) – The input tensor to partition into tiles.
-   **tiler** (_Tiler_) – The tiling specification (can be a Layout, Shape, Tile).
-   **coord** (_Coord_) – The coordinate to select within the remainder (“rest”) modes after tiling. This selects which tile to extract.
-   **proj** (_XTuple__,_ _optional_) – (Optional) Projection onto tiling modes; specify to project out unused tiler modes, e.g., when working with projections of tilers in multi-mode partitioning. Default is None for no projection.
-   **loc** (_Any__,_ _optional_) – (Optional) MLIR location, for diagnostic/debugging.
-   **ip** (_Any__,_ _optional_) – (Optional) MLIR insertion point, used in IR building context.

Returns:

A new tensor representing the local tile selected at the given coordinate.

Return type:

Tensor

**Examples**

1.  Tiling a 2D tensor and extracting a tile:
    
    > \# input: (16, 24)
    > tensor : cute.Tensor
    > tiler \= (2, 4)
    > coord \= (1, 1)
    > 
    > \# output: (8, 6)
    > \# - zipped\_divide(tensor, tiler)     -> ((2, 4), (8, 6))
    > \# - local\_tile(tensor, tiler, coord) -> (8, 6)
    > result \= cute.local\_tile(tensor, tiler\=tiler, coord\=coord)
    > 
    > Copy to clipboard
    
2.  Using a stride projection for specialized tiling:
    
    > \# input: (16, 24)
    > tensor : cute.Tensor
    > tiler \= (2, 2, 4)
    > coord \= (0, 1, 1)
    > proj \= (1, None, 1)
    > 
    > \# output: (8, 6)
    > \# projected\_tiler: (2, 4)
    > \# projected\_coord: (0, 1)
    > \# - zipped\_divide(tensor, projected\_tiler)               -> ((2, 4), (8, 6))
    > \# - local\_tile(tensor, projected\_tiler, projected\_coord) -> (8, 6)
    > result \= cute.local\_tile(tensor, tiler\=tiler, coord\=coord, proj\=proj)
    > 
    > Copy to clipboard
    

cutlass.cute.make\_layout\_image\_mask(

_lay: cutlass.cute.typing.Layout_,

_coord: cutlass.cute.typing.Coord_,

_mode: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Int16[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_layout_image_mask "Link to this definition")

Makes a 16-bit integer mask of the image of a layout sliced at a given mode and accounting for the offset given by the input coordinate for the other modes.

cutlass.cute.leading\_dim(

_shape: cutlass.cute.typing.Shape_,

_stride: cutlass.cute.typing.Stride_,

) → int | Tuple\[int, ...\] | None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.leading_dim "Link to this definition")

Find the leading dimension of a shape and stride.

Parameters:

-   **shape** (_Shape_) – The shape of the tensor or layout
-   **stride** (_Stride_) – The stride of the tensor or layout

Returns:

The leading dimension index or indices

Return type:

Union\[int, Tuple\[int, …\], None\]

The return value depends on the stride pattern:

> -   If a single leading dimension is found, returns an integer index
> -   If nested leading dimensions are found, returns a tuple of indices
> -   If no leading dimension is found, returns None

cutlass.cute.make\_layout\_tv(

_thr\_layout: cutlass.cute.typing.Layout_,

_val\_layout: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Shape, cutlass.cute.typing.Layout\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_layout_tv "Link to this definition")

Create a thread-value layout by repeating the val\_layout over the thr\_layout.

This function creates a thread-value layout that maps between `(thread_idx, value_idx)` coordinates and logical `(M,N)` coordinates. The thread and value layouts must be compact to ensure proper partitioning.

This implements the thread-value partitioning pattern where data is partitioned across threads and values within each thread.

Parameters:

-   **thr\_layout** (_Layout_) – Layout mapping from `(TileM,TileN)` coordinates to thread IDs (must be compact)
-   **val\_layout** (_Layout_) – Layout mapping from `(ValueM,ValueN)` coordinates to value IDs within each thread
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tuple containing `tiler_mn` and `layout_tv`

Return type:

Tuple\[Shape, Layout\]

where:

-   `tiler_mn` is tiler and `shape(tiler_mn)` is compatible with `shape(zipped_divide(x, tiler_mn))[0]`
-   `layout_tv`: Thread-value layout mapping (thread\_idx, value\_idx) -> (M,N)

**Example:**

The below code creates a TV Layout that maps thread/value coordinates to the logical coordinates in a `(4,6)` tensor:

-   _Tiler MN_: `(4,6)`
-   _TV Layout_: `((3,2),(2,2)):((8,2),(4,1))`

thr\_layout \= cute.make\_layout((2, 3), stride\=(3, 1))
val\_layout \= cute.make\_layout((2, 2), stride\=(2, 1))
tiler\_mn, layout\_tv \= cute.make\_layout\_tv(thr\_layout, val\_layout)

Copy to clipboard

|     | 0   | 1   | 2   | 3   | 4   | 5   |
| --- | --- | --- | --- | --- | --- | --- |
| 0   | T0, V0 | T0, V1 | T1, V0 | T1, V1 | T2, V0 | T2, V1 |
| 1   | T0, V2 | T0, V3 | T1, V2 | T1, V3 | T2, V2 | T2, V3 |
| 2   | T3, V0 | T3, V1 | T4, V0 | T4, V1 | T5, V0 | T5, V1 |
| 3   | T3, V2 | T3, V3 | T4, V2 | T4, V3 | T5, V2 | T5, V3 |

cutlass.cute.get\_nonswizzle\_portion(

_layout: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.get_nonswizzle_portion "Link to this definition")

Extract the non-swizzle portion from a layout.

For a simple Layout, the entire layout is considered non-swizzled and is returned as-is. For a ComposedLayout, the inner layout (non-swizzled portion) is extracted and returned, effectively separating the base layout from any swizzle transformation that may be applied.

Parameters:

-   **layout** (_Union__\[__Layout__,_ _ComposedLayout__\]_) – A Layout or ComposedLayout from which to extract the non-swizzle portion.
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional

Returns:

The non-swizzle portion of the input layout. For Layout objects, returns the layout itself. For ComposedLayout objects, returns the outer layout component.

Return type:

Layout

Raises:

**TypeError** – If the layout is neither a Layout nor a ComposedLayout.

cutlass.cute.get\_swizzle\_portion(

_layout: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.\_mlir.ir.register\_value\_caster[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.get_swizzle_portion "Link to this definition")

Extract or create the swizzle portion from a layout.

For a simple Layout (which has no explicit swizzle), a default identity swizzle is created. For a ComposedLayout, the outer layout is checked and returned if it is a Swizzle object. Otherwise, a default identity swizzle is created. The default identity swizzle has parameters (0, 4, 3), which represents a no-op swizzle transformation.

Parameters:

-   **layout** (_Union__\[__Layout__,_ _ComposedLayout__\]_) – A Layout or ComposedLayout from which to extract the swizzle portion.
-   **loc** (_optional_) – Optional location information for IR diagnostics.
-   **ip** (_optional_) – Optional

Returns:

The swizzle portion of the layout. For Layout objects or ComposedLayout objects without a Swizzle outer component, returns a default identity swizzle (0, 4, 3). For ComposedLayout objects with a Swizzle outer component, returns that swizzle.

Return type:

[Swizzle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Swizzle "cutlass.cute.Swizzle")

Raises:

**TypeError** – If the layout is neither a Layout nor a ComposedLayout.

cutlass.cute.transform\_leaf(_f_, _\*args_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.transform_leaf "Link to this definition")

Apply a function to the leaf nodes of nested tuple structures.

This function traverses nested tuple structures in parallel and applies the function f to corresponding leaf nodes. All input tuples must have the same nested structure.

Parameters:

-   **f** (_Callable_) – Function to apply to leaf nodes
-   **args** – One or more nested tuple structures with matching profiles

Returns:

A new nested tuple with the same structure as the inputs, but with leaf values transformed by f

Raises:

**TypeError** – If the input tuples have different nested structures

**Example:**

\>>> transform\_leaf(lambda x: x + 1, (1, 2))
(2, 3)
\>>> transform\_leaf(lambda x, y: x + y, (1, 2), (3, 4))
(4, 6)
\>>> transform\_leaf(lambda x: x \* 2, ((1, 2), (3, 4)))
((2, 4), (6, 8))

Copy to clipboard

cutlass.cute.find\_if(

_t: tuple | cutlass.\_mlir.ir.Value | int_,

_pred\_fn: Callable\[\[tuple | cutlass.\_mlir.ir.Value | int, int\], bool\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → int | Tuple\[int, ...\] | None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.find_if "Link to this definition")

cutlass.cute.find(

_t: tuple | cutlass.\_mlir.ir.Value | int_,

_x: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → int | Tuple\[int, ...\] | None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.find "Link to this definition")

Find the first position of a value `x` in a hierarchical structure `t`.

Searches for the first occurrence of x in t, optionally excluding positions where a comparison value matches. The search can traverse nested structures and returns either a single index or a tuple of indices for nested positions.

Parameters:

-   **t** (_Union__\[__tuple__,_ _ir.Value__,_ _int__\]_) – The search space
-   **x** (_int_) – The static integer x to search for

Returns:

Index if found at top level, tuple of indices showing nested position, or None if not found

Return type:

Union\[int, Tuple\[int, …\], None\]

cutlass.cute.flatten\_to\_tuple(

_a: cutlass.cute.typing.XTuple_,

) → Tuple\[Any, ...\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.flatten_to_tuple "Link to this definition")

Flattens a potentially nested tuple structure into a flat tuple.

This function recursively traverses the input structure and flattens it into a single-level tuple, preserving the order of elements.

Parameters:

**a** (_Union__\[__IntTuple__,_ _Coord__,_ _Shape__,_ _Stride__\]_) – The structure to flatten

Returns:

A flattened tuple containing all elements from the input

Return type:

tuple

**Examples:**

flatten\_to\_tuple((1, 2, 3))       \# Returns (1, 2, 3)
flatten\_to\_tuple(((1, 2), 3))     \# Returns (1, 2, 3)
flatten\_to\_tuple((1, (2, (3,))))  \# Returns (1, 2, 3)

Copy to clipboard

cutlass.cute.unflatten(

_sequence: Tuple\[Any, ...\] | List\[Any\] | Iterable\[Any\]_,

_profile: cutlass.cute.typing.XTuple_,

) → cutlass.cute.typing.XTuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.unflatten "Link to this definition")

Unflatten a flat tuple into a nested tuple structure according to a profile.

This function transforms a flat sequence of elements into a nested tuple structure that matches the structure defined by the profile parameter. It traverses the profile structure and populates it with elements from the sequence.

sequence must be long enough to fill the profile. Raises RuntimeError if it is not.

Parameters:

-   **sequence** (_Union__\[__Tuple__\[__Any__,_ _...__\]__,_ _List__\[__Any__\]__,_ _Iterable__\[__Any__\]__\]_) – A flat sequence of elements to be restructured
-   **profile** (_XTuple_) – A nested tuple structure that defines the shape of the output

Returns:

A nested tuple with the same structure as profile but containing elements from sequence

Return type:

XTuple

**Examples:**

unflatten(\[1, 2, 3, 4\], ((0, 0), (0, 0)))  \# Returns ((1, 2), (3, 4))

Copy to clipboard

cutlass.cute.product(

_a: cutlass.cute.typing.IntTuple | cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.product "Link to this definition")

cutlass.cute.product\_like(

_a: cutlass.cute.typing.IntTuple_,

_target\_profile: cutlass.cute.typing.XTuple_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.IntTuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.product_like "Link to this definition")

Return product of the given IntTuple or Shape at leaves of target\_profile.

This function computes products according to the structure defined by target\_profile.

Parameters:

-   **a** (_IntTuple_ _or_ _Shape_) – The input tuple or shape
-   **target\_profile** (_XTuple_) – The profile that guides how products are computed
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

The resulting tuple with products computed according to target\_profile

Return type:

IntTuple or Shape

Raises:

-   **TypeError** – If inputs have incompatible types
-   **ValueError** – If inputs have incompatible shapes

cutlass.cute.product\_each(

_a: cutlass.cute.typing.IntTuple_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.IntTuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.product_each "Link to this definition")

cutlass.cute.elem\_less(

_lhs: cutlass.cute.typing.Shape | cutlass.cute.typing.IntTuple | cutlass.cute.typing.Coord_,

_rhs: cutlass.cute.typing.Shape | cutlass.cute.typing.IntTuple | cutlass.cute.typing.Coord_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.elem_less "Link to this definition")

cutlass.cute.tuple\_cat(_\*tuples_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.tuple_cat "Link to this definition")

Concatenate multiple tuples into a single tuple.

This function takes any number of tuples and concatenates them into a single tuple. Non-tuple arguments are treated as single-element tuples.

Parameters:

**tuples** (_tuple_ _or_ _any_) – Variable number of tuples to concatenate

Returns:

A single concatenated tuple

Return type:

tuple

**Examples:**

\>>> tuple\_cat((1, 2), (3, 4))
(1, 2, 3, 4)
\>>> tuple\_cat((1,), (2, 3), (4,))
(1, 2, 3, 4)
\>>> tuple\_cat(1, (2, 3))
(1, 2, 3)

Copy to clipboard

cutlass.cute.transform\_apply(_\*args_, _f: Callable_, _g: Callable_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.transform_apply "Link to this definition")

Transform elements of tuple(s) with f, then apply g to all results.

This function applies f to corresponding elements across input tuple(s), then applies g to all transformed results. It mimics the C++ CuTe implementation.

Supports multiple signatures: - transform\_apply(t, f, g): For single tuple, computes g(f(t\[0\]), f(t\[1\]), …) - transform\_apply(t0, t1, f, g): For two tuples, computes g(f(t0\[0\], t1\[0\]), f(t0\[1\], t1\[1\]), …) - transform\_apply(t0, t1, t2, …, f, g): For multiple tuples of same length

For non-tuple inputs, f is applied to the input(s) and g is applied to that single result.

Parameters:

-   **args** – One or more tuples (or non-tuples) to transform
-   **f** (_Callable_) – The function to apply to each element (or corresponding elements across tuples)
-   **g** (_Callable_) – The function to apply to all transformed elements
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

The result of applying g to all transformed elements

Return type:

any

**Examples:**

\>>> transform\_apply((1, 2, 3), f\=lambda x: x \* 2, g\=lambda \*args: sum(args))
12  # (1\*2 + 2\*2 + 3\*2) = 12
\>>> transform\_apply((1, 2), f\=lambda x: (x, x+1), g\=tuple\_cat)
(1, 2, 2, 3)
\>>> transform\_apply((1, 2), (3, 4), f\=lambda x, y: x + y, g\=lambda \*args: args)
(4, 6)

Copy to clipboard

cutlass.cute.filter\_tuple(_\*args_, _f: Callable_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.filter_tuple "Link to this definition")

Filter and flatten tuple elements by applying a function.

The function f should return tuples, which are then concatenated together to produce the final result. This is useful for filtering and transforming tuple structures in a single pass.

Parameters:

-   **t** (_Union__\[__tuple__,_ _ir.Value__,_ _int__\]_) – The tuple to filter
-   **f** (_Callable_) – The function to apply to each element of t
-   **loc** (_optional_) – Source location for MLIR, defaults to None
-   **ip** (_optional_) – Insertion point, defaults to None

Returns:

A concatenated tuple of all results

Return type:

tuple

**Examples:**

\>>> \# Keep only even numbers, wrapped in tuples
\>>> filter\_tuple((1, 2, 3, 4), lambda x: (x,) if x % 2 \== 0 else ())
(2, 4)
\>>> \# Duplicate each element
\>>> filter\_tuple((1, 2, 3), lambda x: (x, x))
(1, 1, 2, 2, 3, 3)

Copy to clipboard

_class_ cutlass.cute.TensorSSA(_\*args: Any_, _\*\*kwargs: Any_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "Link to this definition")

Bases: `ArithValue`

A class representing thread local data from CuTe Tensor in value semantic and immutable.

Parameters:

-   **value** (_ir.Value_) – Flatten vector as ir.Value holding logic data of SSA Tensor
-   **shape** (_Shape_) – The nested shape in CuTe of the vector
-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the tensor elements

Variables:

-   **\_shape** – The nested shape in CuTe of the vector
-   **\_dtype** – Data type of the tensor elements

Raises:

**ValueError** – If shape is not static

\_\_init\_\_(

_value_,

_shape: cutlass.cute.typing.Shape_,

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.__init__ "Link to this definition")

Initialize a new TensorSSA object.

Parameters:

-   **value** (_ir.Value_) – Flatten vector as ir.Value holding logic data of SSA Tensor
-   **shape** (_Shape_) – The nested shape in CuTe of the vector
-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the tensor elements

Raises:

**ValueError** – If shape is not static

_property_ dtype_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.dtype "Link to this definition")

_property_ element\_type_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.element_type "Link to this definition")

_property_ shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.shape "Link to this definition")

\_apply\_op(

_op_,

_other: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")_,

_flip\=False_,

_\*_,

_loc_,

_ip_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA._apply_op "Link to this definition")

\_apply\_op(

_op_,

_other: cutlass.cutlass\_dsl.cutlass\_arith.ArithValue_,

_flip\=False_,

_\*_,

_loc_,

_ip_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")

\_apply\_op(

_op_,

_other: int | float | bool_,

_flip\=False_,

_\*_,

_loc_,

_ip_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")

apply\_op(

_op_,

_other_,

_flip\=False_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.apply_op "Link to this definition")

Apply a binary operation to this tensor and another operand.

This is a public interface to the internal \_apply\_op method, providing a stable API for external users who need to apply custom operations.

Parameters:

-   **op** – The operation function (e.g., operator.add, operator.mul, etc.)
-   **other** – The other operand (TensorSSA, ArithValue, or scalar)
-   **flip** – Whether to flip the operands (for right-hand operations)
-   **loc** – MLIR location (optional)
-   **ip** – MLIR insertion point (optional)

Returns:

The result of the operation

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

Example

\>>> tensor1 \= cute.Tensor(...)
\>>> tensor2 \= cute.Tensor(...)
\>>> result \= tensor1.apply\_op(operator.add, tensor2)
\>>> \# Equivalent to: tensor1 + tensor2

Copy to clipboard

broadcast\_to(

_target\_shape: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.broadcast_to "Link to this definition")

Broadcast the tensor to the target shape.

\_flatten\_shape\_and\_coord(_crd_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA._flatten_shape_and_coord "Link to this definition")

\_build\_result(

_res\_vect_,

_res\_shp_,

_\*_,

_row\_major\=False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA._build_result "Link to this definition")

reshape(

_shape: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.reshape "Link to this definition")

Reshape the tensor to a new shape.

Parameters:

**shape** (_Shape_) – The new shape to reshape to.

Returns:

A new tensor with the same elements but with the new shape.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

Raises:

-   **NotImplementedError** – If dynamic size is not supported
-   **ValueError** – If the new shape is not compatible with the current shape

to(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.to "Link to this definition")

Convert the tensor to a different numeric type.

Parameters:

**dtype** (_Type__\[__Numeric__\]_) – The target numeric type to cast to.

Returns:

A new tensor with the same shape but with elements cast to the target type.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

Raises:

-   **TypeError** – If dtype is not a subclass of Numeric.
-   **NotImplementedError** – If dtype is an unsigned integer type.

ir\_value(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.ir_value "Link to this definition")

ir\_value\_int8(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.ir_value_int8 "Link to this definition")

Returns int8 ir value of Boolean tensor. When we need to store Boolean tensor ssa, use ir\_value\_int8().

Parameters:

-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location information, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point for MLIR operations, defaults to None

Returns:

The int8 value of this Boolean

Return type:

ir.Value

reduce(

_op_,

_init\_val_,

_reduction\_profile: cutlass.cute.typing.Coord_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA.reduce "Link to this definition")

Perform reduce on selected modes with given predefined reduction op.

Parameters:

-   **op** (_operator_) – The reduction operator to use (operator.add or operator.mul)
-   **init\_val** (_numeric_) – The initial value for the reduction
-   **reduction\_profile** (_Coord_) – Specifies which dimensions to reduce. Dimensions marked with None are kept.

Returns:

The reduced tensor

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

**Examples:**

reduce(f32 o (4,))
  \=> f32

reduce(f32 o (4, 5))
  \=> f32
reduce(f32 o (4, (5, 4)), reduction\_profile\=(None, 1))
  \=> f32 o (4,)
reduce(f32 o (4, (5, 4)), reduction\_profile\=(None, (None, 1)))
  \=> f32 o (4, (5,))

Copy to clipboard

cutlass.cute.make\_tensor(

_iterator_,

_layout: cutlass.cute.typing.Shape | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tensor "Link to this definition")

Creates a tensor by composing an engine (iterator/pointer) with a layout.

A tensor is defined as T = E ∘ L, where E is an engine (array, pointer, or counting iterator) and L is a layout that maps logical coordinates to physical offsets. The tensor evaluates coordinates by applying the layout mapping and dereferencing the engine at the resulting offset.

Parameters:

-   **iterator** (_Union__\[__Pointer__,_ _IntTuple__,_ _ir.Value__\]_) – Engine component that provides data access capabilities. Can be: - A pointer (Pointer type) - An integer or integer tuple for coordinate tensors - A shared memory descriptor (SmemDescType)
-   **layout** (_Union__\[__Shape__,_ _Layout__,_ _ComposedLayout__\]_) – Layout component that defines the mapping from logical coordinates to physical offsets. Can be: - A shape tuple that will be converted to a layout - A Layout object - A ComposedLayout object (must be a normal layout)
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR operation tracking, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for MLIR operation, defaults to None

Returns:

A tensor object representing the composition E ∘ L

Return type:

Tensor

Raises:

-   **TypeError** – If iterator type is not a supported type
-   **ValueError** – If layout is a composed layout with customized inner functions

**Examples:**

\# Create a tensor with row-major layout from a pointer
ptr \= make\_ptr(Float32, base\_ptr, AddressSpace.gmem)
layout \= make\_layout((64, 128), stride\=(128, 1))
tensor \= make\_tensor(ptr, layout)

\# Create a tensor with hierarchical layout in shared memory
smem\_ptr \= make\_ptr(Float16, base\_ptr, AddressSpace.smem)
layout \= make\_layout(((128, 8), (1, 4, 1)), stride\=((32, 1), (0, 8, 4096)))
tensor \= make\_tensor(smem\_ptr, layout)

\# Create a coordinate tensor
layout \= make\_layout(2, stride\=16 \* E(0))
tensor \= make\_tensor(5, layout)  \# coordinate tensor with iterator starting at 5

Copy to clipboard

Notes

-   The engine (iterator) must support random access operations
-   Common engine types include raw pointers, arrays, and random-access iterators
-   The layout defines both the shape (logical dimensions) and stride (physical mapping)
-   Supports both direct coordinate evaluation T(c) and partial evaluation (slicing)
-   ComposedLayouts must be “normal” layouts (no inner functions)
-   For coordinate tensors, the iterator is converted to a counting sequence

cutlass.cute.make\_identity\_tensor(

_shape: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_identity_tensor "Link to this definition")

Creates an identity tensor with the given shape.

An identity tensor maps each coordinate to itself, effectively creating a counting sequence within the shape’s bounds. This is useful for generating coordinate indices or creating reference tensors for layout transformations.

Parameters:

-   **shape** (_Shape_) – The shape defining the tensor’s dimensions. Can be a simple integer sequence or a hierarchical structure ((m,n),(p,q))
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR operation tracking, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for MLIR operation, defaults to None

Returns:

A tensor that maps each coordinate to itself

Return type:

Tensor

**Examples:**

\# Create a simple 1D coord tensor
tensor \= make\_identity\_tensor(6)  \# \[0,1,2,3,4,5\]

\# Create a 2D coord tensor
tensor \= make\_identity\_tensor((3,2))  \# \[(0,0),(1,0),(2,0),(0,1),(1,1),(2,1)\]

\# Create hierarchical coord tensor
tensor \= make\_identity\_tensor(((2,1),3))
\# \[((0,0),0),((1,0),0),((0,0),1),((1,0),1),((0,0),2),((1,0),2)\]

Copy to clipboard

Notes

-   The shape parameter follows CuTe’s IntTuple concept
-   Coordinates are ordered colexicographically
-   Useful for generating reference coordinates in layout transformations

cutlass.cute.make\_fragment(

_layout\_or\_shape: cutlass.cute.typing.Layout | cutlass.cute.typing.Shape_,

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_fragment "Link to this definition")

cutlass.cute.make\_fragment\_like(_src_, _dtype\=None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_fragment_like "Link to this definition")

cutlass.cute.make\_rmem\_tensor\_like(

_src: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout | cutlass.cute.typing.Tensor | [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")_,

_dtype: Type\[cutlass.cute.typing.Numeric\] | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_rmem_tensor_like "Link to this definition")

Creates a tensor in register memory with the same shape as the input layout but

compact col-major strides. This is equivalent to calling make\_rmem\_tensor(make\_layout\_like(tensor)).

This function allocates a tensor in register memory (rmem) usually on stack with with the compact layout like the source. The tensor will have elements of the specified numeric data type or the same as the source.

Parameters:

-   **src** (_Union__\[__Layout__,_ _ComposedLayout__,_ _Tensor__\]_) – The source layout or tensor whose shape will be matched
-   **dtype** (_Type__\[__Numeric__\]__,_ _optional_) – The element type for the fragment tensor, defaults to None
-   **loc** (_Location__,_ _optional_) – Source location for MLIR operations, defaults to None
-   **ip** (_InsertionPoint__,_ _optional_) – Insertion point for MLIR operations, defaults to None

Returns:

A new layout or fragment tensor with matching shape

Return type:

Union\[Layout, Tensor\]

**Examples:**

Creating a rmem tensor from a tensor:

smem\_tensor \= cute.make\_tensor(smem\_ptr, layout)
rmem\_tensor \= cute.make\_rmem\_tensor\_like(smem\_tensor, cutlass.Float32)
\# frag\_tensor will be a register-backed tensor with the same shape

Copy to clipboard

Creating a fragment with a different element type:

tensor \= cute.make\_tensor(gmem\_ptr, layout)
rmem\_bool\_tensor \= cute.make\_rmem\_tensor\_like(tensor, cutlass.Boolean)
\# bool\_frag will be a register-backed tensor with Boolean elements

Copy to clipboard

**Notes**

-   When used with a Tensor, if a type is provided, it will create a new fragment tensor with that element type.
-   For layouts with ScaledBasis strides, the function creates a fragment from the shape only.
-   This function is commonly used in GEMM and other tensor operations to create register storage for intermediate results.

cutlass.cute.make\_rmem\_tensor(

_layout\_or\_shape: cutlass.cute.typing.Layout | cutlass.cute.typing.Shape_,

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_rmem_tensor "Link to this definition")

Creates a tensor in register memory with the specified layout/shape and data type.

This function allocates a tensor in register memory (rmem) usually on stack with either a provided layout or creates a new layout from the given shape. The tensor will have elements of the specified numeric data type.

Parameters:

-   **layout\_or\_shape** (_Union__\[__Layout__,_ _Shape__\]_) – Either a Layout object defining the tensor’s memory organization, or a Shape defining its dimensions
-   **dtype** (_Type__\[__Numeric__\]_) – The data type for tensor elements (must be a Numeric type)
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR operation tracking, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for MLIR operation, defaults to None

Returns:

A tensor allocated in register memory

Return type:

Tensor

**Examples:**

\# Create rmem tensor with explicit layout
layout \= make\_layout((128, 32))
tensor \= make\_rmem\_tensor(layout, cutlass.Float16)

\# Create rmem tensor directly from shape
tensor \= make\_rmem\_tensor((64, 64), cutlass.Float32)

Copy to clipboard

Notes

-   Uses 32-byte alignment to support .128 load/store operations
-   Boolean types are stored as 8-bit integers
-   Handles both direct shapes and Layout objects

cutlass.cute.recast\_tensor(

_src: cutlass.cute.typing.Tensor_,

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_swizzle\_\=None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.recast_tensor "Link to this definition")

Recast a tensor to a different data type by changing the element interpretation.

This function reinterprets the memory of a tensor with a different element type, adjusting both the iterator pointer type and the layout to maintain consistency.

Parameters:

-   **src** (_Tensor_) – The source tensor to recast
-   **dtype** (_Type__\[__Numeric__\]_) – The target data type for tensor elements
-   **swizzle** (_Optional__,_ _unused_) – Optional swizzle parameter (reserved for future use), defaults to None
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR operation tracking, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for MLIR operation, defaults to None

Returns:

A new tensor with the same memory but reinterpreted as dtype

Return type:

Tensor

Raises:

**TypeError** – If dtype is not a subclass of Numeric

**Examples:**

\# Create a Float32 tensor
tensor\_f32 \= make\_rmem\_tensor((4, 8), Float32)

\# Recast to Int32 to manipulate bits
tensor\_i32 \= recast\_tensor(tensor\_f32, Int32)

\# Both tensors share the same memory, but interpret it differently

Copy to clipboard

cutlass.cute.domain\_offset(

_coord: cutlass.cute.typing.Coord_,

_tensor: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.domain_offset "Link to this definition")

Offset the tensor domain by the given coordinate.

This function creates a new tensor by offsetting the iterator/pointer of the input tensor by the amount corresponding to the given coordinate in its layout.

Parameters:

-   **coord** (_Coord_) – The coordinate offset to apply
-   **tensor** (_Tensor_) – The source tensor to offset
-   **loc** (_Optional__\[__Location__\]_) – Source location for MLIR operation tracking, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]_) – Insertion point for MLIR operation, defaults to None

Returns:

A new tensor with the offset iterator

Return type:

Tensor

Raises:

**ValueError** – If the tensor type doesn’t support domain offsetting

**Examples:**

\# Create a tensor with a row-major layout
ptr \= make\_ptr(Float32, base\_ptr, AddressSpace.gmem)
layout \= make\_layout((64, 128), stride\=(128, 1))
tensor \= make\_tensor(ptr, layout)

\# Offset by coordinate (3, 5)
offset\_tensor \= domain\_offset((3, 5), tensor)
\# offset\_tensor now points to element at (3, 5)

Copy to clipboard

cutlass.cute.print\_tensor(

_tensor: cutlass.cute.typing.Tensor | [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")_,

_\*_,

_verbose: bool \= False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.print_tensor "Link to this definition")

Print content of the tensor in human readable format.

Outputs the tensor data in a structured format showing both metadata and the actual data values. The output includes tensor type information, layout details, and a formatted array representation of the values.

Parameters:

-   **tensor** (_Tensor_) – The tensor to print
-   **verbose** (_bool_) – If True, includes additional debug information in the output
-   **loc** (_source location__,_ _optional_) – Source location where it’s called, defaults to None
-   **ip** (_insertion pointer__,_ _optional_) – Insertion pointer for IR generation, defaults to None

Raises:

**NotImplementedError** – If the tensor type doesn’t support trivial dereferencing

**Example output:**

tensor(raw\_ptr<@..., Float32, generic, align(4)> o (8,5):(5,1), data=
       \[\[-0.4326, -0.5434,  0.1238,  0.7132,  0.8042\],
        \[-0.8462,  0.9871,  0.4389,  0.7298,  0.6948\],
        \[ 0.3426,  0.5856,  0.1541,  0.2923,  0.6976\],
        \[-0.1649,  0.8811,  0.1788,  0.1404,  0.2568\],
        \[-0.2944,  0.8593,  0.4171,  0.8998,  0.1766\],
        \[ 0.8814,  0.7919,  0.7390,  0.4566,  0.1576\],
        \[ 0.9159,  0.7577,  0.6918,  0.0754,  0.0591\],
        \[ 0.6551,  0.1626,  0.1189,  0.0292,  0.8655\]\])

Copy to clipboard

cutlass.cute.full(

_shape_,

_fill\_value_,

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.full "Link to this definition")

Return a new TensorSSA of given shape and type, filled with fill\_value.

Parameters:

-   **shape** (_tuple_) – Shape of the new tensor.
-   **fill\_value** (_scalar_) – Value to fill the tensor with.
-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the tensor.

Returns:

Tensor of fill\_value with the specified shape and dtype.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

cutlass.cute.full\_like(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Tensor_,

_fill\_value_,

_dtype: Type\[cutlass.cute.typing.Numeric\] | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.full_like "Link to this definition")

Return a full TensorSSA with the same shape and type as a given array.

Parameters:

-   **a** (_array\_like_) – The shape and data-type of a define these same attributes of the returned array.
-   **fill\_value** (_array\_like_) – Fill value.
-   **dtype** (_Union__\[__None__,_ _Type__\[__Numeric__\]__\]__,_ _optional_) – Overrides the data type of the result, defaults to None

Returns:

Tensor of fill\_value with the same shape and type as a.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

See also

[`empty_like()`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.empty_like "cutlass.cute.empty_like"): Return an empty array with shape and type of input. [`ones_like()`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ones_like "cutlass.cute.ones_like"): Return an array of ones with shape and type of input. [`zeros_like()`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.zeros_like "cutlass.cute.zeros_like"): Return an array of zeros with shape and type of input. [`full()`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.full "cutlass.cute.full"): Return a new array of given shape filled with value.

**Examples:**

frg \= cute.make\_rmem\_tensor((2, 3), Float32)
a \= frg.load()
b \= cute.full\_like(a, 1.0)

Copy to clipboard

cutlass.cute.empty\_like(_a_, _dtype\=None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.empty_like "Link to this definition")

Return a new TensorSSA with the same shape and type as a given array, without initializing entries.

Parameters:

-   **a** ([_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")) – The shape and data-type of a define these same attributes of the returned array.
-   **dtype** (_Type__\[__Numeric__\]__,_ _optional_) – Overrides the data type of the result, defaults to None

Returns:

Uninitialized tensor with the same shape and type (unless overridden) as a.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

cutlass.cute.ones\_like(_a_, _dtype\=None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ones_like "Link to this definition")

Return a TensorSSA of ones with the same shape and type as a given array.

Parameters:

-   **a** ([_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")) – The shape and data-type of a define these same attributes of the returned array.
-   **dtype** (_Type__\[__Numeric__\]__,_ _optional_) – Overrides the data type of the result, defaults to None

Returns:

Tensor of ones with the same shape and type (unless overridden) as a.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

cutlass.cute.zeros\_like(_a_, _dtype\=None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.zeros_like "Link to this definition")

Return a TensorSSA of zeros with the same shape and type as a given array.

Parameters:

-   **a** ([_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")) – The shape and data-type of a define these same attributes of the returned array.
-   **dtype** (_Type__\[__Numeric__\]__,_ _optional_) – Overrides the data type of the result, defaults to None

Returns:

Tensor of zeros with the same shape and type (unless overridden) as a.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

cutlass.cute.where(

_cond: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")_,

_x: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_y: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.where "Link to this definition")

Return elements chosen from x or y depending on condition; will auto broadcast x or y if needed.

Parameters:

-   **cond** ([_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")) – Where True, yield x, where False, yield y.
-   **x** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Values from which to choose when condition is True.
-   **y** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Values from which to choose when condition is False.

Returns:

A tensor with elements from x where condition is True, and elements from y where condition is False.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

cutlass.cute.any\_(

_x: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.any_ "Link to this definition")

Test whether any tensor element evaluates to True.

Parameters:

**x** ([_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")) – Input tensor.

Returns:

Returns a TensorSSA scalar containing True if any element of x is True, False otherwise.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

cutlass.cute.all\_(

_x: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.all_ "Link to this definition")

Test whether all tensor elements evaluate to True.

Parameters:

**x** ([_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")) – Input tensor.

Returns:

Returns a TensorSSA scalar containing True if all elements of x are True, False otherwise.

Return type:

[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")

_class_ cutlass.cute.Atom(_op: Op_, _trait: Trait_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom "Link to this definition")

Bases: `ABC`

Atom base class.

An Atom is the composition of

-   a MMA or Copy Operation;
-   an internal MMA or Copy Trait.

An Operation is a pure Python class that is used to model a specific MMA or Copy instruction. The Trait wraps the underlying IR Value and provides access to the metadata of the instruction encoded using CuTe Layouts. When the Trait can be constructed straighforwardly from an Operation, the `make_mma_atom` or `make_copy_atom` API should be used. There are cases where constructing the metadata is not trivial and requires more information, for example to determine the number of bytes copied per TMA instruction (“the TMA vector length”). In such cases, dedicated helper functions are provided with an appropriate API such that the Atom is constructed internally in an optimal fashion for the user.

\_\_init\_\_(

_op: Op_,

_trait: Trait_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom.__init__ "Link to this definition")

_property_ op_: Op_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom.op "Link to this definition")

_property_ type[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom.type "Link to this definition")

set(_modifier_, _value_, _\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom.set "Link to this definition")

Sets runtime fields of the Atom.

Some Atoms have runtime state, for example a tcgen05 MMA Atom

tiled\_mma \= cute.make\_tiled\_mma(some\_tcgen05\_mma\_op)
tiled\_mma.set(cute.nvgpu.tcgen05.Field.ACCUMULATE, True)

Copy to clipboard

The `set` method provides a way to the user to modify such runtime state. Modifiable fields are provided by arch-specific enumerations, for example `tcgen05.Field`. The Atom instance internally validates the field as well as the value provided by the user to set the field to.

get(_field_, _\*_, _loc\=None_, _ip\=None_) → Any[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom.get "Link to this definition")

Gets runtime fields of the Atom.

Some Atoms have runtime state, for example a tcgen05 MMA Atom

tiled\_mma \= cute.make\_tiled\_mma(some\_tcgen05\_mma\_op)
accum \= tiled\_mma.get(cute.nvgpu.tcgen05.Field.ACCUMULATE)

Copy to clipboard

The `get` method provides a way to the user to access such runtime state. Modifiable fields are provided by arch-specific enumerations, for example `tcgen05.Field`. The Atom instance internally validates the field as well as the value provided by the user to set the field to.

with\_(_\*_, _loc\=None_, _ip\=None_, _\*\*kwargs_) → [Atom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom "cutlass.cute.atom.Atom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom.with_ "Link to this definition")

Returns a new Atom with the new Operation and Trait with the given runtime state. The runtime state is provided as keyword arguments and it is Atom-specific.

tiled\_copy \= cute.make\_tiled\_copy(tma\_copy\_op)
new\_tiled\_copy \= tiled\_copy.with\_(tma\_bar\_ptr\=tma\_bar\_ptr, cache\_policy\=cute.CacheEvictionPriority.EVICT\_LAST)

Copy to clipboard

The `with_` method provides a way to the user to modify such runtime state or create an executable Atom (e.g. an Executable TMA Load Atom).

\_unpack(_\*_, _loc\=None_, _ip\=None_, _\*\*kwargs_) → cutlass.\_mlir.ir.Value[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom._unpack "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom._abc_impl "Link to this definition")

_class_ cutlass.cute.MmaAtom(_op: Op_, _trait: Trait_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "Link to this definition")

Bases: [`Atom`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom "cutlass.cute.atom.Atom")

The MMA Atom class.

_property_ thr\_id[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.thr_id "Link to this definition")

_property_ shape\_mnk[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.shape_mnk "Link to this definition")

_property_ tv\_layout\_A[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.tv_layout_A "Link to this definition")

_property_ tv\_layout\_B[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.tv_layout_B "Link to this definition")

_property_ tv\_layout\_C[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.tv_layout_C "Link to this definition")

make\_fragment\_A(_input_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.make_fragment_A "Link to this definition")

make\_fragment\_B(_input_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.make_fragment_B "Link to this definition")

make\_fragment\_C(_input_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom.make_fragment_C "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom._abc_impl "Link to this definition")

_class_ cutlass.cute.CopyAtom(_op: Op_, _trait: Trait_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "Link to this definition")

Bases: [`Atom`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Atom "cutlass.cute.atom.Atom")

The Copy Atom class.

_property_ value\_type_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom.value_type "Link to this definition")

_property_ thr\_id_: cutlass.cute.typing.Layout_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom.thr_id "Link to this definition")

_property_ layout\_src\_tv_: cutlass.cute.typing.Layout_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom.layout_src_tv "Link to this definition")

_property_ layout\_dst\_tv_: cutlass.cute.typing.Layout_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom.layout_dst_tv "Link to this definition")

_property_ smem\_layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom.smem_layout "Link to this definition")

Convenience property to access the SMEM layout for TMA copy atoms.

This is a shortcut for `atom.op.smem_layout` that checks if the operation is a TMA operation and provides a clearer error message if not.

Returns:

The SMEM layout

Return type:

Layout or ComposedLayout

Raises:

-   **TypeError** – If the operation is not a TMA operation
-   **ValueError** – If the SMEM layout is not set

Example

\>>> layout \= tma\_atom.smem\_layout  \# Instead of tma\_atom.op.smem\_layout

Copy to clipboard

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom._abc_impl "Link to this definition")

_class_ cutlass.cute.TiledCopy(_op: Op_, _trait: Trait_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "Link to this definition")

Bases: [`CopyAtom`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")

The tiled Copy class.

_property_ layout\_tv\_tiled_: cutlass.cute.typing.Layout_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.layout_tv_tiled "Link to this definition")

_property_ tiler\_mn_: cutlass.cute.typing.Tile_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.tiler_mn "Link to this definition")

_property_ layout\_src\_tv\_tiled_: cutlass.cute.typing.Layout_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.layout_src_tv_tiled "Link to this definition")

_property_ layout\_dst\_tv\_tiled_: cutlass.cute.typing.Layout_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.layout_dst_tv_tiled "Link to this definition")

_property_ size_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.size "Link to this definition")

get\_slice(

_thr\_idx: int | cutlass.cute.typing.Int32_,

) → [ThrCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy "cutlass.cute.atom.ThrCopy")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.get_slice "Link to this definition")

retile(_src_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy.retile "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy._abc_impl "Link to this definition")

_class_ cutlass.cute.TiledMma(_op: Op_, _trait: Trait_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "Link to this definition")

Bases: [`MmaAtom`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.atom.MmaAtom")

The tiled MMA class.

_property_ tv\_layout\_A\_tiled[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.tv_layout_A_tiled "Link to this definition")

_property_ tv\_layout\_B\_tiled[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.tv_layout_B_tiled "Link to this definition")

_property_ tv\_layout\_C\_tiled[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.tv_layout_C_tiled "Link to this definition")

_property_ permutation\_mnk[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.permutation_mnk "Link to this definition")

_property_ thr\_layout\_vmnk[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.thr_layout_vmnk "Link to this definition")

_property_ size_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.size "Link to this definition")

get\_tile\_size(_mode\_idx: int_) → cutlass.cute.typing.Shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.get_tile_size "Link to this definition")

get\_slice(

_thr\_idx: int | cutlass.cute.typing.Int32_,

) → [ThrMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma "cutlass.cute.atom.ThrMma")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.get_slice "Link to this definition")

\_partition\_shape(_operand\_id_, _shape_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma._partition_shape "Link to this definition")

partition\_shape\_A(_shape\_mk_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.partition_shape_A "Link to this definition")

partition\_shape\_B(_shape\_nk_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.partition_shape_B "Link to this definition")

partition\_shape\_C(_shape\_mn_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma.partition_shape_C "Link to this definition")

\_thrfrg(

_operand\_id_,

_input: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma._thrfrg "Link to this definition")

\_thrfrg(

_operand\_id_,

_input: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor

\_thrfrg\_A(

_input: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma._thrfrg_A "Link to this definition")

\_thrfrg\_B(

_input: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma._thrfrg_B "Link to this definition")

\_thrfrg\_C(

_input: cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma._thrfrg_C "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma._abc_impl "Link to this definition")

_class_ cutlass.cute.ThrMma(

_op: Op_,

_trait: Trait_,

_thr\_idx: int | cutlass.cute.typing.Int32_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma "Link to this definition")

Bases: [`TiledMma`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")

The thread MMA class for modeling a thread-slice of a tiled MMA.

\_\_init\_\_(

_op: Op_,

_trait: Trait_,

_thr\_idx: int | cutlass.cute.typing.Int32_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma.__init__ "Link to this definition")

_property_ thr\_idx[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma.thr_idx "Link to this definition")

partition\_A(

_input\_mk: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma.partition_A "Link to this definition")

partition\_B(

_input\_nk: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma.partition_B "Link to this definition")

partition\_C(

_input\_mn: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma.partition_C "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrMma._abc_impl "Link to this definition")

_class_ cutlass.cute.ThrCopy(

_op: Op_,

_trait: Trait_,

_thr\_idx: int | cutlass.cute.typing.Int32_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy "Link to this definition")

Bases: [`TiledCopy`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")

The thread Copy class for modeling a thread-slice of a tiled Copy.

\_\_init\_\_(

_op: Op_,

_trait: Trait_,

_thr\_idx: int | cutlass.cute.typing.Int32_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy.__init__ "Link to this definition")

_property_ thr\_idx[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy.thr_idx "Link to this definition")

partition\_S(

_src: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy.partition_S "Link to this definition")

partition\_D(

_dst: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy.partition_D "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ThrCopy._abc_impl "Link to this definition")

cutlass.cute.make\_atom(_ty_, _values\=None_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_atom "Link to this definition")

This is a wrapper around the \_cute\_ir.make\_atom operation, providing default value for the values argument.

cutlass.cute.make\_mma\_atom(

_op: MmaOp_,

_\*_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → [MmaAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.atom.MmaAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_mma_atom "Link to this definition")

Makes an MMA Atom from an MMA Operation.

This function creates an MMA Atom from a given MMA Operation. Arbitrary kw arguments can be provided for Op-specific additional parameters. They are not used as of today.

Parameters:

**op** (_MmaOp_) – The MMA Operation to construct an Atom for

Returns:

The MMA Atom

Return type:

[MmaAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.MmaAtom")

cutlass.cute.make\_tiled\_mma(

_op\_or\_atom: Op | [MmaAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.atom.MmaAtom")_,

_atom\_layout\_mnk\=(1, 1, 1)_,

_permutation\_mnk\=None_,

_\*_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_mma "Link to this definition")

Makes a tiled MMA from an MMA Operation or an MMA Atom.

Parameters:

-   **op\_or\_atom** (_Union__\[__Op__,_ [_MmaAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.MmaAtom")_\]_) – The MMA Operation or Atom
-   **atom\_layout\_mnk** (_Layout_) – A Layout describing the tiling of Atom across threads
-   **permutation\_mnk** (_Tiler_) – A permutation Tiler describing the tiling of Atom across values including any permutation of such tiling

Returns:

The resulting tiled MMA

Return type:

[TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")

cutlass.cute.make\_copy\_atom(

_op: CopyOp_,

_copy\_internal\_type: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_copy_atom "Link to this definition")

Makes a Copy Atom from a Copy Operation.

This function creates a Copy Atom from a given Copy Operation. Arbitrary kw arguments can be provided for Op-specific additional parameters.

Example:

op \= cute.nvgpu.CopyUniversalOp()
atom \= cute.make\_copy\_atom(op, tensor\_dtype, num\_bits\_per\_copy\=64)

Copy to clipboard

Parameters:

-   **op** (_CopyOp_) – The Copy Operation to construct an Atom for
-   **copy\_internal\_type** (_Type__\[__Numeric__\]_) – An internal data type used to construct the source/destination layouts in unit of tensor elements

Returns:

The Copy Atom

Return type:

[CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")

cutlass.cute.make\_tiled\_copy\_tv(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_thr\_layout: cutlass.cute.typing.Layout_,

_val\_layout: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_tv "Link to this definition")

Create a tiled copy given separate thread and value layouts.

A TV partitioner is inferred based on the input layouts. The input thread layout must be compact.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **thr\_layout** (_Layout_) – Layout mapping from `(TileM,TileN)` coordinates to thread IDs (must be compact)
-   **val\_layout** (_Layout_) – Layout mapping from `(ValueM,ValueN)` coordinates to value IDs
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy(_atom_, _layout\_tv_, _tiler\_mn_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy "Link to this definition")

Create a tiled type given a TV partitioner and tiler.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom, e.g. smit\_copy and simt\_async\_copy, tma\_load, etc.
-   **layout\_tv** (_Layout_) – Thread-value layout
-   **tiler\_mn** (_Tiler_) – Tile size
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy\_S(_atom_, _tiled\_copy_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_S "Link to this definition")

Create a tiled copy out of the copy\_atom that matches the Src-Layout of tiled\_copy.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **tiled\_copy** ([_TiledCopy_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")) – Tiled copy
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy\_D(_atom_, _tiled\_copy_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_D "Link to this definition")

Create a tiled copy out of the copy\_atom that matches the Dst-Layout of tiled\_copy.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **tiled\_copy** ([_TiledCopy_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")) – Tiled copy
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy\_A(_atom_, _tiled\_mma_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_A "Link to this definition")

Create a tiled copy out of the copy\_atom that matches the A-Layout of tiled\_mma.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **tiled\_mma** ([_TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – Tiled MMA
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy\_B(_atom_, _tiled\_mma_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_B "Link to this definition")

Create a tiled copy out of the copy\_atom that matches the B-Layout of tiled\_mma.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **tiled\_mma** ([_TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – Tiled MMA
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy\_C(_atom_, _tiled\_mma_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_C "Link to this definition")

Create a tiled copy out of the copy\_atom that matches the C-Layout of tiled\_mma.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **tiled\_mma** ([_TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – Tiled MMA
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for the partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

cutlass.cute.make\_tiled\_copy\_C\_atom(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_tiled_copy_C_atom "Link to this definition")

Create the smallest tiled copy that can retile LayoutC\_TV for use with pipelined epilogues with subtiled stores.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom
-   **mma** ([_TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – Tiled MMA
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Returns:

A tiled copy for partitioner

Return type:

[TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")

Raises:

**ValueError** – If the number value of CopyAtom’s source layout is greater than the size of TiledMma’s LayoutC\_TV

cutlass.cute.make\_cotiled\_copy(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_atom\_layout\_tv: cutlass.cute.typing.Layout_,

_data\_layout: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.make_cotiled_copy "Link to this definition")

Produce a TiledCopy from thread and value offset maps. The TV Layout maps threads and values to the codomain of the data\_layout. It is verified that the intended codomain is valid within data\_layout. Useful when threads and values don’t care about owning specific coordinates, but care more about the vector-width and offsets between them.

Parameters:

-   **atom** (_copy atom__,_ _e.g. simt\_copy and simt\_async\_copy__,_ _tgen05.st__,_ _etc._)
-   **atom\_layout\_tv** (_(__tid__,_ _vid__)_ _\-> data addr_)
-   **data\_layout** (_data coord -> data addr_)
-   **loc** (_source location for mlir_ _(__optional__)_)
-   **ip** (_insertion point_ _(__optional__)_)

Returns:

A tuple of A tiled copy and atom

Return type:

tiled\_copy

cutlass.cute.copy\_atom\_call(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_src: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\] | Tuple\[cutlass.cute.typing.Tensor, ...\]_,

_dst: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\] | Tuple\[cutlass.cute.typing.Tensor, ...\]_,

_\*_,

_pred: cutlass.cute.typing.Tensor | None \= None_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.copy_atom_call "Link to this definition")

Execute a single copy atom operation.

The copy\_atom\_call operation executes a copy atom with the given operands. Source and destination tensors have layout profile `(V)`.

The `V-mode` represents either:

-   A singular mode directly consumable by the provided Copy Atom
-   A composite mode requiring recursive decomposition, structured as `(V, Rest...)`,

For src/dst layout like `(V, Rest...)`, the layout profile of `pred` must match `(Rest...)`.

> -   Certain Atoms may require additional operation-specific keyword arguments.
> -   Current implementation limits `V-mode` rank to 2 or less. Support for higher ranks is planned for future releases.

Both `src` and `dst` operands are variadic, containing a variable number of tensors:

-   For regular copy, `src` and `dst` each contain a single tensor.
-   For copy with auxiliary operands, they contain the main tensor followed by auxiliary tensors. For example:

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom specifying the transfer operation
-   **src** (_Union__\[__Tensor__,_ _List__\[__Tensor__\]__,_ _Tuple__\[__Tensor__,_ _...__\]__\]_) – Source tensor(s) with layout profile `(V)`. Can be a single Tensor or a list/tuple of Tensors for operations with auxiliary source operands.
-   **dst** (_Union__\[__Tensor__,_ _List__\[__Tensor__\]__,_ _Tuple__\[__Tensor__,_ _...__\]__\]_) – Destination tensor(s) with layout profile `(V)`. Can be a single Tensor or a list/tuple of Tensors for operations with auxiliary destination operands.
-   **pred** (_Optional__\[__Tensor__\]__,_ _optional_) – Optional predication tensor for conditional transfers, defaults to None
-   **loc** (_Any__,_ _optional_) – Source location information, defaults to None
-   **ip** (_Any__,_ _optional_) – Insertion point, defaults to None
-   **kwargs** (_Dict__\[__str__,_ _Any__\]_) – Additional copy atom specific arguments

Raises:

**TypeError** – If source and destination element type bit widths differ

Returns:

None

Return type:

None

**Examples**:

\# Regular copy atom operation
cute.copy\_atom\_call(copy\_atom, src, dst)

\# Predicated copy atom operation
cute.copy\_atom\_call(copy\_atom, src, dst, pred\=pred)

Copy to clipboard

cutlass.cute.mma\_atom\_call(

_atom: [MmaAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.atom.MmaAtom")_,

_d: cutlass.cute.typing.Tensor_,

_a: cutlass.cute.typing.Tensor_,

_b: cutlass.cute.typing.Tensor_,

_c: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.mma_atom_call "Link to this definition")

Execute a single MMA atom operation.

The mma\_atom\_call operation executes an MMA atom with the given operands. This performs a matrix multiplication and accumulation operation: D = A \* B + C

Note: The tensors ‘d’, ‘a’, ‘b’, and ‘c’ must only have a single fragment.

Parameters:

-   **atom** ([_MmaAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.MmaAtom")) – The MMA atom to execute
-   **d** (_Tensor_) – Destination tensor (output accumulator)
-   **a** (_Tensor_) – First source tensor (matrix A)
-   **b** (_Tensor_) – Second source tensor (matrix B)
-   **c** (_Tensor_) – Third source tensor (input accumulator C)
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

Examples:

\# Call an MMA atom operation
cute.mma\_atom\_call(mma\_atom, d\_tensor, a\_tensor, b\_tensor, c\_tensor)

Copy to clipboard

cutlass.cute.gemm(

_atom: [MmaAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.atom.MmaAtom")_,

_d: cutlass.cute.typing.Tensor_,

_a: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\] | Tuple\[cutlass.cute.typing.Tensor, ...\]_,

_b: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\] | Tuple\[cutlass.cute.typing.Tensor, ...\]_,

_c: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.gemm "Link to this definition")

The GEMM algorithm.

Computes `D <- A * B + C` where `C` and `D` can alias. Note that some MMA Atoms (e.g. warpgroup-wide or tcgen05 MMAs) require manually setting an “accumulate” boolean field.

All tensors must be partitioned according to the provided MMA Atom.

For MMA Atoms that require single-threaded execution, the gemm op automatically handles thread election internally. Manual thread selection is not required in such cases.

Following dispatch rules are supported:

-   Dispatch \[1\]: (V) x (V) => (V) => (V,1,1) x (V,1,1) => (V,1,1)
-   Dispatch \[2\]: (M) x (N) => (M,N) => (1,M,1) x (1,N,1) => (1,M,N)
-   Dispatch \[3\]: (M,K) x (N,K) => (M,N) => (1,M,K) x (1,N,K) => (1,M,N)
-   Dispatch \[4\]: (V,M) x (V,N) => (V,M,N) => (V,M,1) x (V,N,1) => (V,M,N)
-   Dispatch \[5\]: (V,M,K) x (V,N,K) => (V,M,N)

Operand flexibility: - a and b can be a single Tensor (regular GEMM) or a sequence \[operand, scale\_factor\] for block-scaled GEMM.

Parameters:

-   **atom** ([_MmaAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.MmaAtom "cutlass.cute.MmaAtom")) – MMA atom
-   **d** (_Tensor_) – Destination tensor
-   **a** (_Union__\[__Tensor__,_ _List__\[__Tensor__\]__,_ _Tuple__\[__Tensor__,_ _...__\]__\]_) – First source tensor or sequence for advanced modes (e.g., \[a, sfa\])
-   **b** (_Union__\[__Tensor__,_ _List__\[__Tensor__\]__,_ _Tuple__\[__Tensor__,_ _...__\]__\]_) – Second source tensor or sequence for advanced modes (e.g., \[b, sfb\])
-   **c** (_Tensor_) – Third source tensor
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point for MLIR, defaults to None
-   **kwargs** (_dict_) – Additional keyword arguments

Returns:

None

Return type:

None

cutlass.cute.copy(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_src: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\] | Tuple\[cutlass.cute.typing.Tensor, ...\]_,

_dst: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\] | Tuple\[cutlass.cute.typing.Tensor, ...\]_,

_\*_,

_pred: cutlass.cute.typing.Tensor | None \= None_,

_loc\=None_,

_ip\=None_,

_\*\*kwargs_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.copy "Link to this definition")

Facilitates data transfer between two tensors conforming to layout profile `(V, Rest...)`.

Parameters:

-   **atom** ([_CopyAtom_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")) – Copy atom specifying the transfer operation
-   **src** (_Union__\[__Tensor__,_ _List__\[__Tensor__\]__,_ _Tuple__\[__Tensor__,_ _...__\]__\]_) – Source tensor or list of tensors with layout profile `(V, Rest...)`
-   **dst** (_Union__\[__Tensor__,_ _List__\[__Tensor__\]__,_ _Tuple__\[__Tensor__,_ _...__\]__\]_) – Destination tensor or list of tensors with layout profile `(V, Rest...)`
-   **pred** (_Optional__\[__Tensor__\]__,_ _optional_) – Optional predication tensor for conditional transfers, defaults to None
-   **loc** (_Any__,_ _optional_) – Source location information, defaults to None
-   **ip** (_Any__,_ _optional_) – Insertion point, defaults to None
-   **kwargs** (_Dict__\[__str__,_ _Any__\]_) – Additional copy atom specific arguments

Raises:

-   **TypeError** – If source and destination element type bit widths differ
-   **ValueError** – If source and destination ranks differ
-   **ValueError** – If source and destination mode-1 sizes differ
-   **NotImplementedError** – If `V-mode` rank exceeds 2

Returns:

None

Return type:

None

The `V-mode` represents either:

-   A singular mode directly consumable by the provided Copy Atom
-   A composite mode requiring recursive decomposition, structured as `(V, Rest...)`, and src/dst layout like `((V, Rest...), Rest...)`

The algorithm recursively processes the `V-mode`, decomposing it until reaching the minimum granularity compatible with the provided Copy Atom’s requirements.

Source and destination tensors must be partitioned in accordance with the Copy Atom specifications. Post-partitioning, both tensors will exhibit a `(V, Rest...)` layout profile.

The operands src and dst are variadic, each containing a variable number of tensors:

-   For regular copy, src and dst contain single source and destination tensors respectively.
-   For copy with auxiliary operands, src and dst contain the primary tensors followed by their respective auxiliary tensors.

**Precondition:** The size of mode 1 must be equal for both source and destination tensors: `size(src, mode=[1]) == size(dst, mode=[1])`

**Examples**:

TMA copy operation with multicast functionality:

cute.copy(tma\_atom, src, dst, tma\_bar\_ptr\=mbar\_ptr, mcast\_mask\=mask, cache\_policy\=policy)

Copy to clipboard

Optional predication is supported through an additional tensor parameter. For partitioned tensors with logical profile `((ATOM_V,ATOM_REST),REST,...)`, the predication tensor must maintain profile compatibility with `(ATOM_REST,REST,...)`.

For Copy Atoms requiring single-threaded execution, thread election is managed automatically by the copy operation. External thread selection mechanisms are not necessary.

Note

-   Certain Atoms may require additional operation-specific keyword arguments.
-   Current implementation limits `V-mode` rank to 2 or less. Support for higher ranks is planned for future releases.

cutlass.cute.basic\_copy(

_src: cutlass.cute.typing.Tensor_,

_dst: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.basic_copy "Link to this definition")

Performs a basic element-wise copy.

This functions **assumes** the following pre-conditions: 1. size(src) == size(dst)

When the src and dst shapes are static, the pre-conditions are actually verified and the element-wise loop is fully unrolled.

Parameters:

-   **src** (_Tensor_) – Source tensor
-   **dst** (_Tensor_) – Destination tensor
-   **loc** (_Optional__\[__Location__\]__,_ _optional_) – Source location for MLIR, defaults to None
-   **ip** (_Optional__\[__InsertionPoint__\]__,_ _optional_) – Insertion point, defaults to None

cutlass.cute.basic\_copy\_if(

_pred: cutlass.cute.typing.Tensor_,

_src: cutlass.cute.typing.Tensor_,

_dst: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.basic_copy_if "Link to this definition")

Performs a basic predicated element-wise copy.

This functions **assumes** the following pre-conditions: 1. size(src) == size(dst) 2. size(src) == size(pred)

When all shapes are static, the pre-conditions are actually verified and the element-wise loop is fully unrolled.

cutlass.cute.autovec\_copy(

_src: cutlass.cute.typing.Tensor_,

_dst: cutlass.cute.typing.Tensor_,

_\*_,

_l1c\_evict\_priority: [CacheEvictionPriority](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.CacheEvictionPriority "cutlass.cute.nvgpu.common.CacheEvictionPriority") \= cutlass.\_mlir.dialects.cute.CacheEvictionPriority.EVICT\_NORMAL_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.autovec_copy "Link to this definition")

Auto-vectorization SIMT copy policy.

Given a source and destination tensors that are statically shaped, this policy figures out the largest safe vector width that the copy instruction can take and performs the copy.

cutlass.cute.prefetch(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_src: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.prefetch "Link to this definition")

The Prefetch algorithm.

The “prefetch” expects source tensors to be partitioned according to the provided Copy Atom. Prefetch is used for loading tensors from global memory to L2.

Prefetch accepts Copy Atom but not all are allowed. Currently, only supports TMA prefetch.

cute.prefetch(tma\_prefetch, src)

Copy to clipboard

For Copy Atoms that require single-threaded execution, the copy op automatically handles thread election internally. Manual thread selection is not required in such cases.

cutlass.cute.acos(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.acos "Link to this definition")

Compute element-wise arc cosine of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the arc cosine of each element in input tensor

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = acos(y)  # Compute arc cosine

Copy to clipboard

cutlass.cute.asin(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.asin "Link to this definition")

Compute element-wise arc sine of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the arc sine of each element in input tensor

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = asin(y)  # Compute arc sine

Copy to clipboard

cutlass.cute.atan(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.atan "Link to this definition")

Compute element-wise arc tangent of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the arc tangent of each element in input tensor

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = atan(y)  # Compute arc tangent

Copy to clipboard

cutlass.cute.atan2(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_b: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.atan2 "Link to this definition")

Compute element-wise arc tangent of two tensors.

Computes atan2(a, b) element-wise. The function atan2(a, b) is the angle in radians between the positive x-axis and the point given by the coordinates (b, a).

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – First input tensor (y-coordinates)
-   **b** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Second input tensor (x-coordinates)
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the arc tangent of a/b element-wise

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

y = cute.make\_rmem\_tensor(ptr1, layout).load()  # y coordinates
x = cute.make\_rmem\_tensor(ptr2, layout).load()  # x coordinates
theta = atan2(y, x)  # Compute angles

Copy to clipboard

cutlass.cute.cos(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.cos "Link to this definition")

Compute element-wise cosine of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor (in radians)
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the cosine of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = cos(y)  # Compute cosine

Copy to clipboard

cutlass.cute.erf(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.erf "Link to this definition")

Compute element-wise error function of the input tensor.

The error function is defined as: erf(x) = 2/√π ∫\[0 to x\] exp(-t²) dt

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the error function value for each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = erf(y)  # Compute error function

Copy to clipboard

cutlass.cute.exp(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.exp "Link to this definition")

Compute element-wise exponential of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the exponential of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = exp(y)  # Compute exponential

Copy to clipboard

cutlass.cute.exp2(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.exp2 "Link to this definition")

Compute element-wise base-2 exponential of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing 2 raised to the power of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = exp2(y)  # Compute 2^x

Copy to clipboard

cutlass.cute.log(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.log "Link to this definition")

Compute element-wise natural logarithm of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the natural logarithm of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = log(y)  # Compute natural logarithm

Copy to clipboard

cutlass.cute.log10(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.log10 "Link to this definition")

Compute element-wise base-10 logarithm of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the base-10 logarithm of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = log10(y)  # Compute log base 10

Copy to clipboard

cutlass.cute.log2(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.log2 "Link to this definition")

Compute element-wise base-2 logarithm of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the base-2 logarithm of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = log2(y)  # Compute log base 2

Copy to clipboard

cutlass.cute.rsqrt(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.rsqrt "Link to this definition")

Compute element-wise reciprocal square root of the input tensor.

Computes 1/√x element-wise.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the reciprocal square root of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = rsqrt(y)  # Compute 1/√x

Copy to clipboard

cutlass.cute.sin(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.sin "Link to this definition")

Compute element-wise sine of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor (in radians)
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the sine of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = sin(y)  # Compute sine

Copy to clipboard

cutlass.cute.sqrt(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.sqrt "Link to this definition")

Compute element-wise square root of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the square root of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = sqrt(y)  # Compute square root

Copy to clipboard

cutlass.cute.tan(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.tan "Link to this definition")

Compute element-wise tangent of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor (in radians)
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the tangent of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = tan(y)  # Compute tangent

Copy to clipboard

cutlass.cute.tanh(

_a: [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric_,

_fastmath: bool \= False_,

) → [TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.tensor.TensorSSA") | cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.tanh "Link to this definition")

Compute element-wise hyperbolic tangent of the input tensor.

Parameters:

-   **a** (_Union__\[_[_TensorSSA_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA")_,_ _Numeric__\]_) – Input tensor
-   **fastmath** (_bool__,_ _optional_) – Enable fast math optimizations, defaults to False

Returns:

Tensor containing the hyperbolic tangent of each element

Return type:

Union\[[TensorSSA](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TensorSSA "cutlass.cute.TensorSSA"), Numeric\]

Example:

x = cute.make\_rmem\_tensor(layout)  # Create tensor
y = x.load()  # Load values
z = tanh(y)  # Compute hyperbolic tangent

Copy to clipboard

_class_ cutlass.cute.ffi(_\*_, _name: str_, _params\_types: list \= \[\]_, _return\_type\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi "Link to this definition")

Bases: `object`

Foreign Function Interface (FFI) wrapper for external function invocation in the CUTLASS Python DSL.

This class enables calling external MLIR function prototypes from Python code, handling type conversion, prototype registration, and dynamic insertion of function symbols into MLIR modules as needed.

Parameters:

-   **name** (_str_) – Name of the external function. This will be used as the symbol name when calling or registering a prototype in the MLIR module.
-   **params\_types** (_list__,_ _optional_) – List of argument types for the external function. These can be CUTLASS numeric types, numeric meta types, or types convertible via get\_mlir\_types.
-   **return\_type** (_optional_) – The return type of the external function. If not specified, the function is assumed to have no return value.

\_\_call\_\_(_\*args_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi.__call__ "Link to this definition")

Calls the external function with the given arguments, ensuring argument and result types match the prototype.

\_\_init\_\_(_\*_, _name: str_, _params\_types: list \= \[\]_, _return\_type\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi.__init__ "Link to this definition")

\_get\_prototype\_region(_current\_op_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi._get_prototype_region "Link to this definition")

Helper method to determine the appropriate MLIR module and region for inserting a function prototype.

This method recursively traverses the current operation’s parent hierarchy to find the correct module and region where the function prototype should be inserted. It supports both builtin.module and gpu.module. :param current\_op: The current operation to check. :type current\_op: Operation

Returns:

A tuple containing the module operation and the insertion region.

Return type:

tuple

_static_ \_to\_mlir\_types(_args_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi._to_mlir_types "Link to this definition")

Helper method to convert a list of arguments to their corresponding MLIR types.

This method converts CUTLASS numeric types, numeric meta types, and types convertible via get\_mlir\_types to their corresponding MLIR types. :param args: The list of arguments to convert to MLIR types. :type args: list

Returns:

A list of MLIR types.

Return type:

list

_static_ \_type\_check(_callee_, _exec\_types_, _returns\_types_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi._type_check "Link to this definition")

Helper method to check if the function prototype types match the expected types.

This method compares the input and output types of the function prototype with the provided expected types. :param callee: The function prototype operation to check. :type callee: func.FuncOp :param exec\_types: The expected input types. :type exec\_types: list :param returns\_types: The expected output types. :type returns\_types: list

\_create\_prototype\_in\_region(_op_, _region_, _exec\_args_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.ffi._create_prototype_in_region "Link to this definition")

Helper method to create or retrieve a function prototype in the current module.

This method checks if a function prototype with the given name already exists in the symbol table of the current module. If it does, it checks if the prototype’s types match the expected types. If it does not, it raises an error. If it does not exist, it creates a new function prototype and inserts it into the current region. :param op: The module operation to check. :type op: Operation :param region: The region to insert the function prototype into. :type region: Region :param exec\_args: The arguments to pass to the function prototype. :type exec\_args: list

# arch[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#arch "Link to this heading")

The `cute.arch` module provides lightweight wrappers for NVVM Operation builders which implement CUDA built-in device functions such as `thread_idx`. It integrates seamlessly with CuTe DSL types.

These wrappers enable source location tracking through the `@dsl_user_op` decorator. The module includes the following functionality:

-   Core CUDA built-in functions such as `thread_idx`, `warp_idx`, `block_dim`, `grid_dim`, `cluster_dim`, and related functions
-   Memory barrier management functions including `mbarrier_init`, `mbarrier_arrive`, `mbarrier_wait`, and associated operations
-   Low-level shared memory (SMEM) management capabilities, with `SmemAllocator` as the recommended interface
-   Low-level tensor memory (TMEM) management capabilities, with `TmemAllocator` as the recommended interface

## API documentation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#module-cutlass.cute.arch "Link to this heading")

cutlass.cute.arch.make\_warp\_uniform(

_value: cutlass.cute.typing.Int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.make_warp_uniform "Link to this definition")

Provides a compiler hint indicating that the specified value is invariant across all threads in the warp, which may enable performance optimizations.

Parameters:

**value** (_Int_) – The integer value to be marked as warp-uniform.

Returns:

The input value, marked as warp-uniform.

Return type:

Int32

cutlass.cute.arch.elect\_one(_\*_, _loc\=None_, _ip\=None_) → IfOpRegion[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.elect_one "Link to this definition")

Elects one thread within a warp.

with elect\_one():
    \# Only one thread in the warp executes the code in this context
    pass

Copy to clipboard

cutlass.cute.arch.mbarrier\_init(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_cnt: cutlass.cute.typing.Int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_init "Link to this definition")

Initializes a mbarrier with the specified thread arrival count.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **cnt** (_Int_) – The arrival count of the mbarrier

cutlass.cute.arch.mbarrier\_init\_fence(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_init_fence "Link to this definition")

A fence operation that applies to the mbarrier initializations.

cutlass.cute.arch.mbarrier\_arrive\_and\_expect\_tx(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_bytes: cutlass.cute.typing.Int_,

_peer\_cta\_rank\_in\_cluster\=None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_arrive_and_expect_tx "Link to this definition")

Arrives on a mbarrier and expects a specified number of transaction bytes.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **bytes** (_Int_) – The number of transaction bytes
-   **peer\_cta\_rank\_in\_cluster** – An optional CTA rank in cluster. If provided, the pointer to the mbarrier is converted to a remote address in the peer CTA’s SMEM.

cutlass.cute.arch.mbarrier\_expect\_tx(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_bytes: cutlass.cute.typing.Int_,

_peer\_cta\_rank\_in\_cluster\=None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_expect_tx "Link to this definition")

Expects a specified number of transaction bytes without an arrive.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **bytes** (_Int_) – The number of transaction bytes
-   **peer\_cta\_rank\_in\_cluster** – An optional CTA rank in cluster. If provided, the pointer to the mbarrier is converted to a remote address in the peer CTA’s SMEM.

cutlass.cute.arch.mbarrier\_wait(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_phase: cutlass.cute.typing.Int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_wait "Link to this definition")

Waits on a mbarrier with a specified phase.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **phase** (_Int_) – The phase to wait for (either 0 or 1)

cutlass.cute.arch.mbarrier\_try\_wait(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_phase: cutlass.cute.typing.Int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_try_wait "Link to this definition")

Attempts to wait on a mbarrier with a specified phase in a non-blocking fashion.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **phase** (_Int_) – The phase to wait for (either 0 or 1)

Returns:

A boolean value indicating whether the wait operation was successful

Return type:

Boolean

cutlass.cute.arch.mbarrier\_conditional\_try\_wait(

_cond_,

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_phase: cutlass.cute.typing.Int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_conditional_try_wait "Link to this definition")

Conditionally attempts to wait on a mbarrier with a specified phase in a non-blocking fashion.

Parameters:

-   **cond** – A boolean predicate
-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **phase** (_Int_) – The phase to wait for (either 0 or 1)

Returns:

A boolean value indicating whether the wait operation was successful

Return type:

Boolean

cutlass.cute.arch.mbarrier\_arrive(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_peer\_cta\_rank\_in\_cluster: cutlass.cute.typing.Int | None \= None_,

_arrive\_count: cutlass.cute.typing.Int \= 1_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.mbarrier_arrive "Link to this definition")

Arrives on an mbarrier.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **peer\_cta\_rank\_in\_cluster** – An optional CTA rank in cluster. If provided, the pointer to the mbarrier is converted to a remote address in the peer CTA’s SMEM.

cutlass.cute.arch.lane\_idx(_\*_, _loc\=None_, _ip\=None_) → cutlass.cute.typing.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.lane_idx "Link to this definition")

Returns the lane index of the current thread within the warp.

cutlass.cute.arch.warp\_idx(_\*_, _loc\=None_, _ip\=None_) → cutlass.cute.typing.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.warp_idx "Link to this definition")

Returns the warp index within a CTA.

cutlass.cute.arch.thread\_idx(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.thread_idx "Link to this definition")

Returns the thread index within a CTA.

cutlass.cute.arch.block\_dim(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.block_dim "Link to this definition")

Returns the number of threads in each dimension of the CTA.

cutlass.cute.arch.block\_idx(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.block_idx "Link to this definition")

Returns the CTA identifier within a grid.

cutlass.cute.arch.grid\_dim(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.grid_dim "Link to this definition")

Returns the number of CTAs in each dimension of the grid.

cutlass.cute.arch.cluster\_idx(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cluster_idx "Link to this definition")

Returns the cluster identifier within a grid.

cutlass.cute.arch.cluster\_dim(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cluster_dim "Link to this definition")

Returns the number of clusters in each dimension of the grid.

cutlass.cute.arch.cluster\_size(_\*_, _loc\=None_, _ip\=None_) → cutlass.cute.typing.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cluster_size "Link to this definition")

Returns the number of CTA within the cluster.

cutlass.cute.arch.block\_in\_cluster\_idx(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.block_in_cluster_idx "Link to this definition")

Returns the CTA index within a cluster across all dimensions.

cutlass.cute.arch.block\_in\_cluster\_dim(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.block_in_cluster_dim "Link to this definition")

Returns the dimensions of the cluster.

cutlass.cute.arch.block\_idx\_in\_cluster(

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.block_idx_in_cluster "Link to this definition")

Returns the linearized identifier of the CTA within the cluster.

cutlass.cute.arch.barrier(

_\*_,

_barrier\_id\=None_,

_number\_of\_threads\=None_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.barrier "Link to this definition")

Creates a barrier, optionally named.

cutlass.cute.arch.barrier\_arrive(

_\*_,

_barrier\_id\=None_,

_number\_of\_threads\=None_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.barrier_arrive "Link to this definition")

cutlass.cute.arch.sync\_threads(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.sync_threads "Link to this definition")

Synchronizes all threads within a CTA.

cutlass.cute.arch.sync\_warp(

_mask: cutlass.cute.typing.Int \= 4294967295_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.sync_warp "Link to this definition")

Performs a warp-wide sync with an optional mask.

cutlass.cute.arch.fence\_acq\_rel\_cta(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.fence_acq_rel_cta "Link to this definition")

Fence operation with acquire-release semantics.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-membar).

cutlass.cute.arch.fence\_acq\_rel\_cluster(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.fence_acq_rel_cluster "Link to this definition")

Fence operation with acquire-release semantics.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-membar).

cutlass.cute.arch.fence\_acq\_rel\_gpu(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.fence_acq_rel_gpu "Link to this definition")

Fence operation with acquire-release semantics.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-membar).

cutlass.cute.arch.fence\_acq\_rel\_sys(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.fence_acq_rel_sys "Link to this definition")

Fence operation with acquire-release semantics.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-membar).

cutlass.cute.arch.cp\_async\_commit\_group(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cp_async_commit_group "Link to this definition")

Commits all prior initiated but uncommitted cp.async instructions.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#data-movement-and-conversion-instructions-cp-async-commit-group).

cutlass.cute.arch.cp\_async\_wait\_group(_n_, _\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cp_async_wait_group "Link to this definition")

Waits till only a specified numbers of cp.async groups are pending.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#data-movement-and-conversion-instructions-cp-async-wait-group-cp-async-wait-all).

cutlass.cute.arch.cp\_async\_bulk\_commit\_group(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cp_async_bulk_commit_group "Link to this definition")

Commits all prior initiated but uncommitted cp.async.bulk instructions.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#data-movement-and-conversion-instructions-cp-async-bulk-commit-group).

cutlass.cute.arch.cp\_async\_bulk\_wait\_group(

_group_,

_\*_,

_read\=None_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cp_async_bulk_wait_group "Link to this definition")

Waits till only a specified numbers of cp.async.bulk groups are pending.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#data-movement-and-conversion-instructions-cp-async-bulk-wait-group).

cutlass.cute.arch.cluster\_wait(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cluster_wait "Link to this definition")

A cluster-wide wait operation.

cutlass.cute.arch.cluster\_arrive(_\*_, _aligned\=None_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cluster_arrive "Link to this definition")

A cluster-wide arrive operation.

cutlass.cute.arch.cluster\_arrive\_relaxed(_\*_, _aligned\=None_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cluster_arrive_relaxed "Link to this definition")

A cluster-wide arrive operation with relaxed semantics.

cutlass.cute.arch.vote\_ballot\_sync(

_pred: cutlass.cute.typing.Boolean_,

_mask: cutlass.cute.typing.Int \= 4294967295_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.vote_ballot_sync "Link to this definition")

Performs a ballot operation across the warp.

It copies the predicate from each thread in mask into the corresponding bit position of destination register d, where the bit position corresponds to the thread’s lane id.

Parameters:

-   **pred** (_Boolean_) – The predicate value for the current thread
-   **mask** (_Int__,_ _optional_) – A 32-bit integer mask specifying which threads participate, defaults to all threads (0xFFFFFFFF)

Returns:

A 32-bit integer where each bit represents a thread’s predicate value

Return type:

Int32

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-vote-sync).

cutlass.cute.arch.vote\_any\_sync(

_pred: cutlass.cute.typing.Boolean_,

_mask: cutlass.cute.typing.Int \= 4294967295_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.vote_any_sync "Link to this definition")

True if source predicate is True for any non-exited threads in mask. Negate the source predicate to compute .none.

Parameters:

-   **pred** (_Boolean_) – The predicate value for the current thread
-   **mask** (_Int__,_ _optional_) – A 32-bit integer mask specifying which threads participate, defaults to all threads (0xFFFFFFFF)

Returns:

A boolean value indicating if the source predicate is True for all non-exited threads in mask

Return type:

Boolean

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-vote-sync).

cutlass.cute.arch.vote\_all\_sync(

_pred: cutlass.cute.typing.Boolean_,

_mask: cutlass.cute.typing.Int \= 4294967295_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.vote_all_sync "Link to this definition")

True if source predicate is True for all non-exited threads in mask. Negate the source predicate to compute .none.

Parameters:

-   **pred** (_Boolean_) – The predicate value for the current thread
-   **mask** (_Int__,_ _optional_) – A 32-bit integer mask specifying which threads participate, defaults to all threads (0xFFFFFFFF)

Returns:

A boolean value indicating if the source predicate is True for all non-exited threads in mask

Return type:

Boolean

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-vote-sync).

cutlass.cute.arch.vote\_uni\_sync(

_pred: cutlass.cute.typing.Boolean_,

_mask: cutlass.cute.typing.Int \= 4294967295_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.vote_uni_sync "Link to this definition")

True f source predicate has the same value in all non-exited threads in mask. Negating the source predicate also computes .uni

Parameters:

-   **pred** (_Boolean_) – The predicate value for the current thread
-   **mask** (_Int__,_ _optional_) – A 32-bit integer mask specifying which threads participate, defaults to all threads (0xFFFFFFFF)

Returns:

A boolean value indicating if the source predicate is True for all non-exited threads in mask

Return type:

Boolean

cutlass.cute.arch.warp\_redux\_sync(

_value: cutlass.cute.typing.Numeric_,

_kind: Literal\['fmax', 'fmin', 'max', 'min', 'add', 'xor', 'or', 'and'\]_,

_mask\_and\_clamp: cutlass.cute.typing.Int \= 4294967295_,

_\*_,

_abs: bool | None \= None_,

_nan: bool | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.warp_redux_sync "Link to this definition")

Perform warp-level reduction operation across threads.

Reduces values from participating threads in a warp according to the specified operation. All threads in the mask receive the same result.

Parameters:

-   **value** (_Numeric_) – Input value to reduce
-   **kind** (_Literal__\[__"add"__,_ _"and"__,_ _"max"__,_ _"min"__,_ _"or"__,_ _"xor"__,_ _"fmin"__,_ _"fmax"__\]_) – Reduction operation. Supported operations: - Integer types (Int32/Uint32): “add”, “and”, “max”, “min”, “or”, “xor” - Float types (Float32): “fmax”, “fmin” (or “max”/”min” which auto-convert to “fmax”/”fmin”)
-   **mask\_and\_clamp** (_Int_) – Warp participation mask (default: FULL\_MASK = 0xFFFFFFFF)
-   **abs** (_bool_) – Apply absolute value before reduction (float types only)
-   **nan** (_Optional__\[__bool__\]_) – Enable NaN propagation for fmax/fmin operations (float types only)

Returns:

Reduced value (same for all participating threads)

Return type:

Numeric

cutlass.cute.arch.atomic\_max\_float32(

_ptr_,

_value: cutlass.cute.typing.Float32_,

_\*_,

_positive\_only: bool \= True_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Float32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_max_float32 "Link to this definition")

Performs an atomic max operation on a float32 value in global memory.

This implementation works correctly for non-negative values (>= 0) using direct bitcast.

Parameters:

-   **ptr** – Pointer to the memory location
-   **value** (_Float32_) – The float32 value to compare and potentially store (should be >= 0 for correct results)
-   **positive\_only** (_bool_) – If True (default), assumes input values are non-negative. This parameter is provided for API compatibility and future extensions.

Returns:

The old value at the memory location

Return type:

Float32

cutlass.cute.arch.atomic\_add(

_ptr_,

_val: cutlass.cute.typing.Numeric | cutlass.\_mlir.ir.Value_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric | cutlass.\_mlir.ir.Value[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_add "Link to this definition")

Performs an atomic addition operation.

Atomically adds val to the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Union__\[__Numeric__,_ _ir.Value__\]_) – Value to add (scalar Numeric or vector ir.Value)
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Union\[Numeric, ir.Value\]

cutlass.cute.arch.atomic\_and(

_ptr_,

_val: cutlass.cute.typing.Numeric_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_and "Link to this definition")

Performs an atomic bitwise AND operation.

Atomically computes bitwise AND of val with the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Numeric_) – Value for AND operation
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.atomic\_or(

_ptr_,

_val: cutlass.cute.typing.Numeric_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_or "Link to this definition")

Performs an atomic bitwise OR operation.

Atomically computes bitwise OR of val with the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Numeric_) – Value for OR operation
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.atomic\_xor(

_ptr_,

_val: cutlass.cute.typing.Numeric_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_xor "Link to this definition")

Performs an atomic bitwise XOR operation.

Atomically computes bitwise XOR of val with the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Numeric_) – Value for XOR operation
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.atomic\_max(

_ptr_,

_val: cutlass.cute.typing.Numeric_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_max "Link to this definition")

Performs an atomic maximum operation.

Atomically computes maximum of val and the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Numeric_) – Value for MAX operation
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.atomic\_min(

_ptr_,

_val: cutlass.cute.typing.Numeric_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_min "Link to this definition")

Performs an atomic minimum operation.

Atomically computes minimum of val and the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Numeric_) – Value for MIN operation
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.atomic\_exch(

_ptr_,

_val: cutlass.cute.typing.Numeric_,

_\*_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_exch "Link to this definition")

Performs an atomic exchange operation.

Atomically exchanges val with the value at memory location ptr and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location
-   **val** (_Numeric_) – Value to exchange
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.atomic\_cas(

_ptr_,

_\*_,

_cmp: cutlass.cute.typing.Numeric_,

_val: cutlass.cute.typing.Numeric_,

_sem: Literal\['relaxed', 'release', 'acquire', 'acq\_rel'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.atomic_cas "Link to this definition")

Performs an atomic compare-and-swap (CAS) operation.

Atomically compares the value at the memory location with cmp. If they are equal, stores val at the memory location and returns the old value.

Parameters:

-   **ptr** – Pointer to memory location. Supports: - ir.Value (LLVM pointer) - cute.ptr (\_Pointer instance)
-   **cmp** (_Numeric_) – Value to compare against current memory value
-   **val** (_Numeric_) – Value to store if comparison succeeds
-   **sem** (_Optional__\[__Literal__\[__"relaxed"__,_ _"release"__,_ _"acquire"__,_ _"acq\_rel"__\]__\]_) – Memory semantic (“relaxed”, “release”, “acquire”, “acq\_rel”)
-   **scope** (_Optional__\[__Literal__\[__"gpu"__,_ _"cta"__,_ _"cluster"__,_ _"sys"__\]__\]_) – Memory scope (“gpu”, “cta”, “cluster”, “sys”)

Returns:

Old value at memory location

Return type:

Numeric

cutlass.cute.arch.store(

_ptr_,

_val: cutlass.cute.typing.Numeric | cutlass.\_mlir.ir.Value_,

_\*_,

_level1\_eviction\_priority: Literal\['evict\_normal', 'evict\_first', 'evict\_last', 'evict\_no\_allocate', 'evict\_unchanged'\] | None \= None_,

_cop: Literal\['wb', 'cg', 'cs', 'wt'\] | None \= None_,

_ss: Literal\['cta', 'cluster'\] | None \= None_,

_sem: Literal\['relaxed', 'release'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.store "Link to this definition")

Store a value to a memory location.

Parameters:

-   **ptr** – Pointer to store to. Supports: - ir.Value (LLVM pointer) - cute.ptr (\_Pointer instance)
-   **val** (_Union__\[__Numeric__,_ _ir.Value__\]_) – Value to store (scalar Numeric or vector ir.Value)
-   **level1\_eviction\_priority** – L1 cache eviction policy string literal: “evict\_normal” : .level1::eviction\_priority = .L1::evict\_normal “evict\_first” : .level1::eviction\_priority = .L1::evict\_first “evict\_last” : .level1::eviction\_priority = .L1::evict\_last “evict\_no\_allocate” : .level1::eviction\_priority = .L1::no\_allocate “evict\_unchanged” : .level1::eviction\_priority = .L1::evict\_unchanged
-   **cop** – Store cache modifier string literal:
-   **ss** – Shared memory space string literal: “cta” : .ss = .shared::cta “cluster” : .ss = .shared::cluster None : .ss = .global
-   **sem** – Memory semantic string literal:
-   **scope** – Memory scope string literal:

cutlass.cute.arch.load(

_ptr_,

_dtype: type\[cutlass.cute.typing.Numeric\] | cutlass.\_mlir.ir.VectorType_,

_\*_,

_sem: Literal\['relaxed', 'acquire'\] | None \= None_,

_scope: Literal\['gpu', 'cta', 'cluster', 'sys'\] | None \= None_,

_level1\_eviction\_priority: Literal\['evict\_normal', 'evict\_first', 'evict\_last', 'evict\_no\_allocate', 'evict\_unchanged'\] | None \= None_,

_cop: Literal\['ca', 'cg', 'cs', 'lu', 'cv'\] | None \= None_,

_ss: Literal\['cta', 'cluster'\] | None \= None_,

_level\_prefetch\_size: Literal\['size\_64b', 'size\_128b', 'size\_256b'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric | cutlass.\_mlir.ir.Value[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.load "Link to this definition")

Load a value from a memory location.

Parameters:

-   **ptr** – Pointer to load from. Supports: - ir.Value (LLVM pointer) - cute.ptr (\_Pointer instance)
-   **dtype** (_Union__\[__type__\[__Numeric__\]__,_ _ir.VectorType__\]_) – Data type to load. Can be: - Scalar: Numeric type class (Int8, Uint8, Int32, Float32, etc.) - Vector: ir.VectorType for vectorized load (e.g., ir.VectorType.get(\[4\], Int64.mlir\_type))
-   **sem** – Memory semantic string literal:
-   **scope** – Memory scope string literal:
-   **level1\_eviction\_priority** – L1 cache eviction policy string literal: “evict\_normal” : .level1::eviction\_priority = .L1::evict\_normal “evict\_first” : .level1::eviction\_priority = .L1::evict\_first “evict\_last” : .level1::eviction\_priority = .L1::evict\_last “evict\_no\_allocate” : .level1::eviction\_priority = .L1::no\_allocate “evict\_unchanged” : .level1::eviction\_priority = .L1::evict\_unchanged
-   **cop** – Load cache modifier string literal:
-   **ss** – Shared memory space string literal: “cta” : .ss = .shared::cta “cluster” : .ss = .shared::cluster None : .ss = .global
-   **level\_prefetch\_size** – L2 cache prefetch size hint string literal: “size\_64b” : .level::prefetch\_size = .L2::64B “size\_128b” : .level::prefetch\_size = .L2::128B “size\_256b” : .level::prefetch\_size = .L2::256B

Returns:

Loaded value (scalar Numeric or vector ir.Value)

Return type:

Union\[Numeric, ir.Value\]

cutlass.cute.arch.popc(

_value: cutlass.cute.typing.Numeric_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Numeric[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.popc "Link to this definition")

Performs a population count operation.

cutlass.cute.arch.fence\_proxy(

_kind: Literal\['alias', 'async', 'async.global', 'async.shared', 'tensormap', 'generic'\]_,

_\*_,

_space: Literal\['cta', 'cluster'\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.fence_proxy "Link to this definition")

Fence operation to ensure memory consistency between proxies.

Parameters:

-   **kind** (_Literal__\[__"alias"__,_ _"async"__,_ _"async.global"__,_ _"async.shared"__,_ _"tensormap"__,_ _"generic"__\]_) – Proxy kind string literal: - “alias” : Alias proxy - “async” : Async proxy - “async.global” : Async global proxy - “async.shared” : Async shared proxy - “tensormap” : Tensormap proxy - “generic” : Generic proxy
-   **space** (_Optional__\[__Literal__\[__"cta"__,_ _"cluster"__\]__\]_) – Shared memory space scope string literal (optional): - “cta” : CTA (Cooperative Thread Array) scope - “cluster” : Cluster scope

cutlass.cute.arch.warpgroup\_reg\_alloc(_reg\_count: int_, _\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.warpgroup_reg_alloc "Link to this definition")

cutlass.cute.arch.warpgroup\_reg\_dealloc(_reg\_count: int_, _\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.warpgroup_reg_dealloc "Link to this definition")

cutlass.cute.arch.setmaxregister\_increase(_reg\_count: int_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.setmaxregister_increase "Link to this definition")

cutlass.cute.arch.setmaxregister\_decrease(_reg\_count: int_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.setmaxregister_decrease "Link to this definition")

cutlass.cute.arch.fmax(

_a: float | cutlass.cute.typing.Float32_,

_b: float | cutlass.cute.typing.Float32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Float32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.fmax "Link to this definition")

cutlass.cute.arch.rcp\_approx(

_a: float | cutlass.cute.typing.Float32_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.rcp_approx "Link to this definition")

cutlass.cute.arch.exp2(

_a: float | cutlass.cute.typing.Float32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Float32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.exp2 "Link to this definition")

cutlass.cute.arch.cvt\_i8x4\_to\_f32x4(_src\_vec4_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i8x4_to_f32x4 "Link to this definition")

cutlass.cute.arch.cvt\_i8x2\_to\_f32x2(_src\_vec2_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i8x2_to_f32x2 "Link to this definition")

cutlass.cute.arch.cvt\_i8\_bf16(_src\_i8_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i8_bf16 "Link to this definition")

cutlass.cute.arch.cvt\_i8x2\_to\_bf16x2(_src\_vec2_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i8x2_to_bf16x2 "Link to this definition")

cutlass.cute.arch.cvt\_i8x4\_to\_bf16x4(_src\_vec4_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i8x4_to_bf16x4 "Link to this definition")

cutlass.cute.arch.cvt\_f32x2\_bf16x2(_src\_vec2_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_f32x2_bf16x2 "Link to this definition")

cutlass.cute.arch.alloc\_smem(

_element\_type: Type\[cutlass.cute.typing.Numeric\]_,

_size\_in\_elems: int_,

_alignment: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.alloc_smem "Link to this definition")

Statically allocates SMEM.

Parameters:

-   **element\_type** (_Type__\[__Numeric__\]_) – The pointee type of the pointer.
-   **size\_in\_elems** (_int_) – The size of the allocation in terms of number of elements of the pointee type
-   **alignment** (_int_) – An optional pointer alignment for the allocation

Returns:

A pointer to the start of the allocation

Return type:

Pointer

cutlass.cute.arch.get\_dyn\_smem(

_element\_type: Type\[cutlass.cute.typing.Numeric\]_,

_alignment: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.get_dyn_smem "Link to this definition")

Retrieves a pointer to a dynamic SMEM allocation.

Parameters:

-   **element\_type** (_Type__\[__Numeric__\]_) – The pointee type of the pointer.
-   **alignment** (_int_) – An optional pointer alignment, the result pointer is offset appropriately

Returns:

A pointer to the start of the dynamic SMEM allocation with a correct alignement

Return type:

Pointer

cutlass.cute.arch.get\_dyn\_smem\_size(_\*_, _loc\=None_, _ip\=None_) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.get_dyn_smem_size "Link to this definition")

Gets the size in bytes of the dynamic shared memory that was specified at kernel launch time. This can be used for bounds checking during shared memory allocation.

Returns:

The size of dynamic shared memory in bytes

Return type:

int

cutlass.cute.arch.get\_max\_tmem\_alloc\_cols(_compute\_capability: str_) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.get_max_tmem_alloc_cols "Link to this definition")

Get the tensor memory capacity in columns for a given compute capability.

Returns the maximum TMEM capacity in columns available for the specified GPU compute capability.

Parameters:

**compute\_capability** (_str_) – The compute capability string (e.g. “sm\_100”, “sm\_103”)

Returns:

The TMEM capacity in columns

Return type:

int

Raises:

**ValueError** – If the compute capability is not supported

cutlass.cute.arch.get\_min\_tmem\_alloc\_cols(_compute\_capability: str_) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.get_min_tmem_alloc_cols "Link to this definition")

Get the minimum TMEM allocation columns for a given compute capability.

Returns the minimum TMEM allocation columns available for the specified GPU compute capability.

Parameters:

**compute\_capability** (_str_) – The compute capability string (e.g. “sm\_100”, “sm\_103”)

Returns:

The minimum TMEM allocation columns

Return type:

int

Raises:

**ValueError** – If the compute capability is not supported

cutlass.cute.arch.retrieve\_tmem\_ptr(

_element\_type: Type\[cutlass.cute.typing.Numeric\]_,

_alignment: int_,

_ptr\_to\_buffer\_holding\_addr: cutlass.cute.typing.Pointer_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.retrieve_tmem_ptr "Link to this definition")

Retrieves a pointer to TMEM with the provided element type and alignment.

Parameters:

-   **element\_type** (_Type__\[__Numeric__\]_) – The pointee type of the pointer.
-   **alignment** (_int_) – The alignment of the result pointer
-   **ptr\_to\_buffer\_holding\_addr** (_Pointer_) – A pointer to a SMEM buffer holding the TMEM address of the start of the allocation allocation

Returns:

A pointer to TMEM

Return type:

Pointer

cutlass.cute.arch.alloc\_tmem(

_num\_columns: cutlass.cute.typing.Int_,

_smem\_ptr\_to\_write\_address: cutlass.cute.typing.Pointer_,

_is\_two\_cta\=None_,

_\*_,

_arch: str \= 'sm\_100'_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.alloc_tmem "Link to this definition")

Allocates TMEM.

Parameters:

-   **num\_columns** (_Int_) – The number of TMEM columns to allocate
-   **smem\_ptr\_to\_write\_address** (_Pointer_) – A pointer to a SMEM buffer where the TMEM address is written to
-   **is\_two\_cta** – Optional boolean parameter for 2-CTA MMAs
-   **arch** (_str_) – The architecture of the GPU.

cutlass.cute.arch.relinquish\_tmem\_alloc\_permit(

_is\_two\_cta\=None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.relinquish_tmem_alloc_permit "Link to this definition")

Relinquishes the right to allocate TMEM so that other CTAs potentially in a different grid can allocate.

cutlass.cute.arch.dealloc\_tmem(

_tmem\_ptr: cutlass.cute.typing.Pointer_,

_num\_columns: cutlass.cute.typing.Int_,

_is\_two\_cta\=None_,

_\*_,

_arch: str \= 'sm\_100'_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.dealloc_tmem "Link to this definition")

Deallocates TMEM using the provided pointer and number of columns.

Parameters:

-   **tmem\_ptr** (_Pointer_) – A pointer to the TMEM allocation to de-allocate
-   **num\_columns** (_Int_) – The number of columns in the TMEM allocation
-   **is\_two\_cta** – Optional boolean parameter for 2-CTA MMAs

cutlass.cute.arch.prmt(_src_, _src\_reg\_shifted_, _prmt\_indices_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.prmt "Link to this definition")

cutlass.cute.arch.cvt\_i8\_bf16\_intrinsic(_vec\_i8_, _length_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i8_bf16_intrinsic "Link to this definition")

Fast conversion from int8 to bfloat16. It converts a vector of int8 to a vector of bfloat16.

Parameters:

-   **vec\_i8** (_1D vector_ _of_ _int8_) – The input vector of int8.
-   **length** (_int_) – The length of the input vector.

Returns:

The output 1D vector of bfloat16 with the same length as the input vector.

Return type:

1D vector of bfloat16

cutlass.cute.arch.cvt\_i4\_bf16\_intrinsic(

_vec\_i4_,

_length_,

_\*_,

_with\_shuffle\=False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.cvt_i4_bf16_intrinsic "Link to this definition")

Fast conversion from int4 to bfloat16. It converts a vector of int4 to a vector of bfloat16.

Parameters:

-   **vec\_i4** (_1D vector_ _of_ _int4_) – The input vector of int4.
-   **length** (_int_) – The length of the input vector.
-   **with\_shuffle** (_bool_) – Whether the input vec\_i4 follows a specific shuffle pattern. If True, for consecutive 8 int4 values with indices of (0, 1, 2, 3, 4, 5, 6, 7), the input elements are shuffled to (0, 2, 1, 3, 4, 6, 5, 7). For tailing elements less than 8, the shuffle pattern is (0, 2, 1, 3) for 4 elements. No shuffle is needed for less than 4 elements. Shuffle could help to produce converted bf16 values in the natural order of (0, 1, 2 ,3 ,4 ,5 ,6 ,7) without extra prmt instructions and thus better performance.

Returns:

The output 1D vector of bfloat16 with the same length as the input vector.

Return type:

1D vector of bfloat16

cutlass.cute.arch.issue\_clc\_query(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_clc\_response\_ptr: cutlass.cute.typing.Pointer_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.issue_clc_query "Link to this definition")

The clusterlaunchcontrol.try\_cancel instruction requests atomically cancelling the launch of a cluster that has not started running yet. It asynchronously writes an opaque response to shared memory indicating whether the operation succeeded or failed. On success, the opaque response contains the ctaid of the first CTA of the canceled cluster.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier address in SMEM
-   **clc\_response\_ptr** (_Pointer_) – A pointer to the cluster launch control response address in SMEM

cutlass.cute.arch.clc\_response(

_result\_addr: cutlass.cute.typing.Pointer_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32, cutlass.cute.typing.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_arch.html#cutlass.cute.arch.clc_response "Link to this definition")

After loading response from clusterlaunchcontrol.try\_cancel instruction into 16-byte register, it can be further queried using clusterlaunchcontrol.query\_cancel instruction. If the cluster is canceled successfully, predicate p is set to true; otherwise, it is set to false. If the request succeeded, clusterlaunchcontrol.query\_cancel.get\_first\_ctaid extracts the CTA id of the first CTA in the canceled cluster. By default, the instruction returns a .v4 vector whose first three elements are the x, y and z coordinate of first CTA in canceled cluster.

Parameters:

**result\_addr** (_Pointer_) – A pointer to the cluster launch control response address in SMEM

# Runtime[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#runtime "Link to this heading")

Description

## API documentation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#module-cutlass.cute.runtime "Link to this heading")

_class_ cutlass.cute.runtime.\_Pointer(_\*args: Any_, _\*\*kwargs: Any_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer "Link to this definition")

Bases: `Pointer`

Runtime representation of a pointer that can inter-operate with various data structures, including numpy arrays and device memory.

Parameters:

-   **pointer** (_int_ _or_ _pointer-like object_) – The pointer to the data
-   **dtype** (_Type_) – Data type of the elements pointed to
-   **mem\_space** (_\_cute\_ir.AddressSpace__,_ _optional_) – Memory space where the pointer resides, defaults to generic
-   **assumed\_align** (_int__,_ _optional_) – Assumed alignment of input pointer in bytes, defaults to None

Variables:

-   **\_pointer** – The underlying pointer
-   **\_dtype** – Data type of the elements
-   **\_addr\_space** – Memory space of the pointer
-   **\_assumed\_align** – Alignment of the pointer in bytes
-   **\_desc** – C-type descriptor for the pointer
-   **\_c\_pointer** – C-compatible pointer representation

\_\_init\_\_(

_pointer_,

_dtype_,

_mem\_space: cutlass.\_mlir.dialects.cute.AddressSpace \= cutlass.\_mlir.dialects.cute.AddressSpace.generic_,

_assumed\_align\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer.__init__ "Link to this definition")

size\_in\_bytes() → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer.size_in_bytes "Link to this definition")

_property_ mlir\_type_: cutlass.\_mlir.ir.Type_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer.mlir_type "Link to this definition")

_property_ dtype_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer.dtype "Link to this definition")

_property_ memspace[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer.memspace "Link to this definition")

align(

_min\_align: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Pointer.align "Link to this definition")

_class_ cutlass.cute.runtime.\_Tensor(_\*args: Any_, _\*\*kwargs: Any_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor "Link to this definition")

Bases: `Tensor`

\_\_init\_\_(

_tensor_,

_assumed\_align\=None_,

_use\_32bit\_stride\=False_,

_\*_,

_enable\_tvm\_ffi\=False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.__init__ "Link to this definition")

load\_dltensor()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.load_dltensor "Link to this definition")

Lazily load the DLTensorWrapper.

This function loads the DLTensorWrapper when needed, avoiding overhead in the critical path of calling JIT functions.

mark\_layout\_dynamic(_leading\_dim: int | None \= None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.mark_layout_dynamic "Link to this definition")

Marks the tensor layout as dynamic based on the leading dimension.

Parameters:

**leading\_dim** (_int__,_ _optional_) – The leading dimension of the layout, defaults to None

When `leading_dim` is None, the leading dimension is deduced as follows.

1.  If exactly one dimension has stride 1, that dimension is used.
2.  If multiple dimensions have stride 1 but exactly one of them has size > 1, that dimension is used.
3.  If multiple dimensions have stride 1 but none or more than one has size > 1, an error is raised.
4.  If no dimension has stride 1, all strides remain dynamic.

When `leading_dim` is explicitly specified, marks the layout as dynamic while setting the stride at `leading_dim` to 1. Also validates that the specified `leading_dim` is consistent with the existing layout by checking that the corresponding stride of that dimension is 1.

Limitation: only support flat layout for now. Will work on supporting nested layout in the future.

Returns:

The tensor with dynamic layout

Return type:

[\_Tensor](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor "cutlass.cute.runtime._Tensor")

mark\_compact\_shape\_dynamic(

_mode: int_,

_stride\_order: tuple\[int, ...\] | None \= None_,

_divisibility: int \= 1_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.mark_compact_shape_dynamic "Link to this definition")

Marks the tensor shape as dynamic and propagates dynamic and divisibility information to the corresponding strides.

Parameters:

-   **mode** (_int_) – The mode of the compact shape, defaults to 0
-   **stride\_order** – Consistent with torch.Tensor.dim\_order. Defaults to None.

Indicates the order of the modes (dimensions) if the current layout were converted to row-major order. It starts from the outermost to the innermost dimension. :type stride\_order: tuple\[int, …\], optional :param divisibility: The divisibility constraint for the compact shape, defaults to 1 :type divisibility: int, optional :return: The tensor with dynamic compact shape :rtype: \_Tensor

If `stride_order` is not provided, the stride ordering will be automatically deduced from the layout. Automatic deduction is only possible when exactly one dimension has a stride of 1 (compact layout). An error is raised if automatic deduction fails.

If `stride_order` is explicitly specified, it does the consistency check with the layout.

For example: - Layout: (4,2):(1,4) has stride\_order: (1,0) indicates the innermost dimension is 0(4:1), the outermost dimension is 1(2:4) - Layout: (5,3,2,4):(3,1,15,30) has stride\_order: (3,2,0,1) indicates the innermost dimension is 1(3:1), the outermost dimension is 3(4:30).

Using torch.Tensor.dim\_order() to get the stride order of the torch tensor. .. code-block:: python a = torch.empty(3, 4) t = cute.runtime.from\_dlpack(a) t = t.mark\_compact\_shape\_dynamic(mode=0, stride\_order=a.dim\_order())

_property_ element\_type_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.element_type "Link to this definition")

_property_ memspace[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.memspace "Link to this definition")

_property_ size\_in\_bytes_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.size_in_bytes "Link to this definition")

_property_ mlir\_type_: cutlass.\_mlir.ir.Type_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.mlir_type "Link to this definition")

_property_ iterator[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.iterator "Link to this definition")

_property_ layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.layout "Link to this definition")

_property_ shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.shape "Link to this definition")

_property_ stride[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.stride "Link to this definition")

_property_ leading\_dim[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.leading_dim "Link to this definition")

Get the leading dimension of this Tensor.

Returns:

The leading dimension index or indices

Return type:

int or tuple or None

The return value depends on the tensor’s stride pattern:

-   If a single leading dimension is found, returns an integer index
-   If nested leading dimensions are found, returns a tuple of indices
-   If no leading dimension is found, returns None

fill(_value: cutlass.cute.typing.Numeric_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.fill "Link to this definition")

_property_ data\_ptr[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.data_ptr "Link to this definition")

_property_ dynamic\_shapes\_mask[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.dynamic_shapes_mask "Link to this definition")

Get the mask of dynamic shapes in the tensor.

_property_ dynamic\_strides\_mask[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._Tensor.dynamic_strides_mask "Link to this definition")

Get the mask of dynamic strides in the tensor.

cutlass.cute.runtime.\_get\_cute\_type\_str(_inp_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._get_cute_type_str "Link to this definition")

_class_ cutlass.cute.runtime.\_FakeTensor(_\*args: Any_, _\*\*kwargs: Any_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor "Link to this definition")

Bases: `Tensor`

Fake Tensor implementation as a placeholder. It mimics the interface of Tensor, but does not hold real data or allow indexing. Used for compilation or testing situations where only shape/type/layout information is needed. All attempts to access or mutate data will raise errors.

\_\_init\_\_(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_shape: tuple\[int | cutlass.cute.typing.SymInt, ...\]_,

_\*_,

_stride: tuple\[int | cutlass.cute.typing.SymInt, ...\]_,

_memspace: cutlass.cute.typing.AddressSpace \= cutlass.cute.typing.AddressSpace.gmem_,

_assumed\_align: int | None \= None_,

_use\_32bit\_stride: bool \= False_,

_compact: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.__init__ "Link to this definition")

_property_ mlir\_type_: cutlass.\_mlir.ir.Type_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.mlir_type "Link to this definition")

_property_ element\_type_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.element_type "Link to this definition")

_property_ memspace[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.memspace "Link to this definition")

_property_ iterator[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.iterator "Link to this definition")

_property_ shape[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.shape "Link to this definition")

_property_ stride[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.stride "Link to this definition")

_property_ leading\_dim[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.leading_dim "Link to this definition")

_property_ dynamic\_shapes\_mask[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.dynamic_shapes_mask "Link to this definition")

_property_ dynamic\_strides\_mask[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.dynamic_strides_mask "Link to this definition")

fill(_value: cutlass.cute.typing.Numeric_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor.fill "Link to this definition")

cutlass.cute.runtime.make\_fake\_compact\_tensor(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_shape: tuple\[int | cutlass.cute.typing.SymInt, ...\]_,

_\*_,

_stride\_order: tuple\[int, ...\] | None \= None_,

_memspace: cutlass.cute.typing.AddressSpace \= cutlass.cute.typing.AddressSpace.gmem_,

_assumed\_align: int | None \= None_,

_use\_32bit\_stride: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.make_fake_compact_tensor "Link to this definition")

Create a fake tensor with the specified shape, element type, and a compact memory layout.

Parameters:

-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the tensor elements.
-   **shape** (_tuple__\[__Union__\[__int__,_ _SymInt__\]__,_ _...__\]_) – Shape of the tensor, consisting of static (int) or dynamic (SymInt) dimensions.
-   **stride\_order** (_tuple__\[__int__,_ _...__\]__,_ _optional_) – Order in which strides (memory layout) are assigned to the tensor dimensions. If None, the default layout is left-to-right order (known as column-major order for flatten layout). Otherwise, it should be a permutation order of the dimension indices. The mode with stride\_order 0 is the fastest changing (leading) dimension, and N-1 is the slowest changing.
-   **memspace** (_AddressSpace__,_ _optional_) – Memory space where the fake tensor resides. Defaults to AddressSpace.gmem.
-   **assumed\_align** (_int__,_ _optional_) – Assumed byte alignment for the tensor data. If None, the default alignment is the dtype width, & at least 1 byte.
-   **use\_32bit\_stride** (_bool__,_ _optional_) – Whether to use 32-bit stride for dynamic dimensions. If True and the total size of the layout (cosize(layout)) fits within int32, then dynamic strides will use 32-bit integers for improved performance. Only applies when dimensions are dynamic. Defaults to False.

Returns:

An instance of a fake tensor with the given properties and compact layout.

Return type:

[\_FakeTensor](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor "cutlass.cute.runtime._FakeTensor")

**Examples:**

@cute.jit
def foo(x: cute.Tensor):
    ...

x \= make\_fake\_compact\_tensor(
    cutlass.Float32, (100, cute.sym\_int32(divisibility\=8)), stride\_order\=(1, 0)
)

\# Compiled function will take a tensor with the type:
\#   tensor<ptr<f32, generic> o (100,?{div=8}):(?{i32 div=8},1)>
compiled\_foo \= cute.compile(foo, x)

\# Default stride order is left-to-right order (0, 1, ..., n-1)
y \= make\_fake\_compact\_tensor(cutlass.Float32, (8, 3, 2)) \# y.stride == (1, 8, 24)

Copy to clipboard

cutlass.cute.runtime.make\_fake\_tensor(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_shape: tuple\[int | cutlass.cute.typing.SymInt, ...\]_,

_stride: tuple\[int | cutlass.cute.typing.SymInt, ...\]_,

_\*_,

_memspace: cutlass.cute.typing.AddressSpace \= cutlass.cute.typing.AddressSpace.gmem_,

_assumed\_align: int | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.make_fake_tensor "Link to this definition")

Create a fake tensor with the specified element type, shape, and stride.

Parameters:

-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the tensor elements.
-   **shape** (_tuple__\[__Union__\[__int__,_ _SymInt__\]__,_ _...__\]_) – Shape of the tensor, consisting of static (int) or dynamic (SymInt) dimensions.
-   **stride** (_tuple__\[__Union__\[__int__,_ _SymInt__\]__,_ _...__\]_) – Stride of the tensor, consisting of static (int) or dynamic (SymInt) values.
-   **memspace** (_AddressSpace__,_ _optional_) – Memory space where the fake tensor resides. Defaults to AddressSpace.gmem.
-   **assumed\_align** (_int__,_ _optional_) – Assumed byte alignment for the tensor data. If None, the default alignment is the dtype width, & at least 1 byte.

Returns:

An instance of a fake tensor with the given properties.

Return type:

[\_FakeTensor](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeTensor "cutlass.cute.runtime._FakeTensor")

_class_ cutlass.cute.runtime.\_FakeStream(_\*_, _use\_tvm\_ffi\_env\_stream: bool \= False_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeStream "Link to this definition")

Bases: `object`

A fake stream that can be used as a placeholder for a stream in compilation.

When use\_tvm\_ffi\_env\_stream is True and the function is compiled with TVM-FFI, the argument will be skipped from the function signature and we pass in this value through the environment stream obtained from caller context (e.g. torch.cuda.current\_stream()).

\_\_init\_\_(_\*_, _use\_tvm\_ffi\_env\_stream: bool \= False_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeStream.__init__ "Link to this definition")

use\_tvm\_ffi\_env\_stream_: bool_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime._FakeStream.use_tvm_ffi_env_stream "Link to this definition")

cutlass.cute.runtime.make\_fake\_stream(_\*_, _use\_tvm\_ffi\_env\_stream: bool \= False_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.make_fake_stream "Link to this definition")

Create a fake stream that can be used as a placeholder for a stream in compilation.

When use\_tvm\_ffi\_env\_stream is True and the function is compiled with TVM-FFI, the argument will be skipped from the function signature and we pass in this value through the environment stream obtained from caller context (e.g. torch.cuda.current\_stream()). This can speedup the calling process since we no longer need to do stream query in python.

Parameters:

**use\_tvm\_ffi\_env\_stream** (_bool_) – Whether to skip this parameter use environment stream instead.

cutlass.cute.runtime.from\_dlpack(

_tensor\_dlpack_,

_assumed\_align\=None_,

_use\_32bit\_stride\=False_,

_\*_,

_enable\_tvm\_ffi\=False_,

_force\_tf32\=False_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.from_dlpack "Link to this definition")

Convert from tensor object supporting \_\_dlpack\_\_() to a CuTe Tensor.

Parameters:

-   **tensor\_dlpack** (_object_) – Tensor object that supports the DLPack protocol
-   **assumed\_align** (_int__,_ _optional_) – Assumed alignment of the tensor (bytes), defaults to None, if None, will use the element size bytes as the assumed alignment.
-   **use\_32bit\_stride** (_bool__,_ _optional_) – Whether to use 32-bit stride, defaults to False. When True, the dynamic stride bitwidth will be set to 32 for small problem size (cosize(layout) <= Int32\_max) for better performance. This is only applied when the dimension is dynamic.
-   **enable\_tvm\_ffi** (_bool__,_ _optional_) – Whether to enable TVM-FFI, defaults to False. When True, the tensor will be converted to a TVM-FFI function compatible tensor.
-   **force\_tf32** (_bool__,_ _optional_) – Whether to force the element type to TFloat32 if the element type is Float32.

Returns:

A CuTe Tensor object

Return type:

Tensor

**Examples:**

import torch
from cutlass.cute.runtime import from\_dlpack
x \= torch.randn(100, 100)
y \= from\_dlpack(x)
y.shape
\# (100, 100)
type(y)
\# <class 'cutlass.cute.Tensor'>

Copy to clipboard

cutlass.cute.runtime.make\_ptr(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_value: int | \_Pointer_,

_mem\_space: cutlass.cute.typing.AddressSpace \= cutlass.cute.typing.AddressSpace.generic_,

_assumed\_align\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.make_ptr "Link to this definition")

Create a pointer from a memory address

Parameters:

-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the pointer elements
-   **value** (_Union__\[__int__,_ _ctypes.\_Pointer__\]_) – Memory address as integer or ctypes pointer
-   **mem\_space** (_AddressSpace__,_ _optional_) – Memory address space, defaults to AddressSpace.generic
-   **align\_bytes** (_int__,_ _optional_) – Alignment in bytes, defaults to None

Returns:

A pointer object

Return type:

Pointer

import numpy as np
import ctypes

from cutlass import Float32
from cutlass.cute.runtime import make\_ptr

\# Create a numpy array
a \= np.random.randn(16, 32).astype(np.float32)

\# Get pointer address as integer
ptr\_address \= a.ctypes.data\_as(ctypes.POINTER(ctypes.c\_float))

\# Create pointer from address
y \= make\_ptr(cutlass.Float32, ptr\_address)

\# Check properties
print(y.element\_type)
print(type(y))  \# <class 'cutlass.cute.Pointer'>

Copy to clipboard

cutlass.cute.runtime.nullptr(

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_mem\_space: cutlass.cute.typing.AddressSpace \= cutlass.cute.typing.AddressSpace.generic_,

_assumed\_align\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.nullptr "Link to this definition")

Create a null pointer which is useful for compilation

Parameters:

-   **dtype** (_Type__\[__Numeric__\]_) – Data type of the pointer elements
-   **mem\_space** (_AddressSpace__,_ _optional_) – Memory address space, defaults to AddressSpace.generic

Returns:

A null pointer object

Return type:

Pointer

_class_ cutlass.cute.runtime.TensorAdapter(_arg_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.TensorAdapter "Link to this definition")

Bases: `object`

Convert a DLPack protocol supported tensor/array to a cute tensor.

\_\_init\_\_(_arg_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.TensorAdapter.__init__ "Link to this definition")

cutlass.cute.runtime.find\_runtime\_libraries(

_\*_,

_enable\_tvm\_ffi: bool \= True_,

) → List\[str\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.find_runtime_libraries "Link to this definition")

Find the runtime libraries that needs to be available for loading modules.

Parameters:

**enable\_tvm\_ffi** (_bool__,_ _optional_) – Whether to enable TVM-FFI.

Returns:

A list of runtime libraries that needs to be available for loading modules.

Return type:

list

cutlass.cute.runtime.load\_module(_file\_path: str_, _\*_, _enable\_tvm\_ffi: bool \= False_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_runtime.html#cutlass.cute.runtime.load_module "Link to this definition")

Load a module from a file path.

Parameters:

-   **file\_path** (_str_) – The path to the module file
-   **enable\_tvm\_ffi** (_bool__,_ _optional_) – Whether to enable TVM-FFI, defaults to True. When True, the module will be loaded as a TVM-FFI module.

Returns:

A module object

Return type:

module
