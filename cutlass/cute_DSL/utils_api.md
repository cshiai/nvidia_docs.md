# cutlass.utils[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass-utils "Link to this heading")

The `cutlass.utils` module contains utilities for developing kernels with CuTe DSL.

cutlass.utils.get\_smem\_capacity\_in\_bytes(

_compute\_capability: str | None \= None_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_smem_capacity_in_bytes "Link to this definition")

Get the shared memory capacity in bytes for a given compute capability.

Returns the maximum shared memory capacity in bytes available for the specified GPU compute capability.

Parameters:

**compute\_capability** (_Optional__\[__str__\]_) – The compute capability string (e.g. “70”, “75”, “80”)

Returns:

The shared memory capacity in bytes

Return type:

int

Raises:

**ValueError** – If the compute capability is not supported

_class_ cutlass.utils.SmemAllocator[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.SmemAllocator "Link to this definition")

Bases: `object`

A helper class for managing shared memory allocation on GPU.

This class manages shared memory and provides APIs for allocation of raw bytes, numeric types, arrays, and tensors with specified layouts and alignments.

Note

-   The base pointer is aligned to 1024 bytes upon initialization.
-   There is no need to explicitly specify shared memory size in kernel launch.
-   Currently only supports static layouts. Dynamic layouts are not supported.

**Examples**:

smem \= SmemAllocator()

\# Allocate raw bytes
buf\_ptr \= smem.allocate(100)  \# 100 bytes

\# Allocate numeric type
int8\_ptr \= smem.allocate(Int8)  \# 1 byte

\# Define a struct
@cute.struct
class SharedStorage:
    alpha: cutlass.Float32
    x: cutlass.Int32

\# Allocate struct
struct\_ptr \= smem.allocate(SharedStorage)  \# 8 bytes

\# use of struct members
struct\_ptr.alpha \= 1.0
struct\_ptr.x \= 2

\# Allocate array
int8\_array \= smem.allocate\_array(Int8, 10)  \# 10 bytes

\# Allocate tensor
layout \= cute.make\_layout((16, 16))
tensor \= smem.allocate\_tensor(Int8, layout)  \# 256 bytes

Copy to clipboard

_static_ capacity\_in\_bytes(

_compute\_capability: str | None \= None_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.SmemAllocator.capacity_in_bytes "Link to this definition")

Get the shared memory capacity in bytes for a given compute capability.

Returns the maximum shared memory capacity in bytes available for the specified GPU compute capability.

Parameters:

**compute\_capability** (_Optional__\[__str__\]_) – The compute capability string (e.g. “70”, “75”, “80”)

Returns:

The shared memory capacity in bytes

Return type:

int

Raises:

**ValueError** – If the compute capability is not supported

\_\_init\_\_(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.SmemAllocator.__init__ "Link to this definition")

Initialize a new SmemAllocator instance.

Creates a new shared memory allocator with a base pointer aligned to 1024 bytes. Tracks the allocator instance for memory management.

Parameters:

-   **loc** (_Optional__\[__ir.Location__\]_) – Source location information for debugging, defaults to None
-   **ip** (_Optional__\[__ir.InsertionPoint__\]_) – Insertion point for MLIR operations, defaults to None

allocate(

_size\_or\_type: int_,

_byte\_alignment: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.SmemAllocator.allocate "Link to this definition")

allocate(

_size\_or\_type: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_byte\_alignment: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer

allocate(

_size\_or\_type: [struct](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct "cutlass.cute.core.struct")_,

_byte\_alignment: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer

Allocate a block of memory with specified size and alignment.

This method allocates a block of shared memory with the specified size and alignment requirements. It supports allocating raw bytes, numeric types(as scalar value), and struct types.

Parameters:

-   **size\_or\_type** (_Union__\[__int__,_ _Type__\[__Numeric__\]__,_ [_cute.struct_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.struct "cutlass.cute.struct")_\]_) – The allocation specification, which can be: - An integer specifying the number of bytes to allocate - A Numeric type (e.g., Int8, Float32) to allocate space for one element - A struct type to allocate space for the entire struct
-   **byte\_alignment** (_int__,_ _optional_) – The minimum byte alignment requirement for the allocation, defaults to 1
-   **loc** (_Optional__\[__ir.Location__\]_) – Source location information for debugging, defaults to None
-   **ip** (_Optional__\[__ir.InsertionPoint__\]_) – Insertion point for MLIR operations, defaults to None

Returns:

For raw bytes and numeric types, returns a pointer to the allocated memory. For struct types, returns an initialized struct instance at the allocated location.

Return type:

cute.Pointer

Raises:

-   **ValueError** – If size is negative or alignment is less than 1
-   **TypeError** – If size\_or\_type is not an integer, Numeric type, or struct
-   **RuntimeError** – If allocation would exceed available shared memory

allocate\_array(

_element\_type: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_elems: int \= 1_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.SmemAllocator.allocate_array "Link to this definition")

Allocate an array of elements in shared memory.

Parameters:

-   **element\_type** (_Type__\[__Numeric__\]_) – The type of elements to allocate
-   **num\_elems** (_int__,_ _optional_) – Number of elements to allocate, defaults to 1

Returns:

Pointer to the start of the allocated array

Return type:

cute.Pointer

Raises:

-   **ValueError** – If num\_elems is less than 1
-   **TypeError** – If element\_type is not a Numeric type

allocate\_tensor(

_element\_type: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_layout: int | cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_byte\_alignment: int \= 1_,

_swizzle: cutlass.\_mlir.ir.register\_value\_caster | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.SmemAllocator.allocate_tensor "Link to this definition")

Allocate a tensor in shared memory.

Note: Currently only supports static layouts. Dynamic layouts are not supported.

Parameters:

-   **element\_type** (_Type__\[__Numeric__\]_) – The type of elements in the tensor
-   **layout** (_Union__\[__int__,_ _cute.Layout__,_ _cute.ComposedLayout__\]_) – The layout specification for the tensor. Must be a static layout.
-   **byte\_alignment** (_int__,_ _optional_) – The byte alignment requirement, defaults to 1
-   **swizzle** ([_cute.Swizzle_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.Swizzle "cutlass.cute.Swizzle")_,_ _optional_) – Swizzle for position-dependent swizzling, defaults to None

Returns:

The allocated tensor with specified properties

Return type:

cute.Tensor

Raises:

-   **TypeError** – If element\_type is not a Numeric type or if swizzle conflicts with layout
-   **ValueError** – If allocation is not byte-aligned
-   **NotImplementedError** – If dynamic layout is specified

_class_ cutlass.utils.TmemAllocator(

_alloc\_result\_dst\_smem\_ptr: cutlass.cute.typing.Pointer_,

_barrier\_for\_retrieve: [NamedBarrier](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier "cutlass.pipeline.helpers.NamedBarrier")_,

_allocator\_warp\_id: int \= 0_,

_is\_two\_cta: bool \= False_,

_num\_allocated\_columns: int \= 0_,

_two\_cta\_tmem\_dealloc\_mbar\_ptr: cutlass.cute.typing.Pointer | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TmemAllocator "Link to this definition")

Bases: `object`

A class for managing tensor memory allocation on GPUs.

This class manages allocation/deallocation of tensor memory, including the mbarrier synchronization for two cta use case.

Variables:

-   **\_alloc\_result\_dst\_smem\_ptr** – The smem pointer that holds the base address of allocated tensor memory.
-   **\_barrier\_for\_retrieve** – The barrier for retrieving tensor memory ptr.
-   **\_allocator\_warp\_id** – The warp id of the allocator warp.
-   **\_is\_two\_cta** – Whether the allocator is for two cta.
-   **\_num\_allocated\_columns** – The number of columns allocated in the tensor memory.
-   **\_two\_cta\_tmem\_dealloc\_mbar\_ptr** – The mbarrier pointer required when deallocating tensor memory for two cta.
-   **\_arch** – The architecture of the GPU.

\_\_init\_\_(

_alloc\_result\_dst\_smem\_ptr: cutlass.cute.typing.Pointer_,

_barrier\_for\_retrieve: [NamedBarrier](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier "cutlass.pipeline.helpers.NamedBarrier")_,

_allocator\_warp\_id: int \= 0_,

_is\_two\_cta: bool \= False_,

_num\_allocated\_columns: int \= 0_,

_two\_cta\_tmem\_dealloc\_mbar\_ptr: cutlass.cute.typing.Pointer | None \= None_,

_\*_,

_arch: str \= 'sm\_100'_,

_dealloc\_mbarrier\_initialized: bool \= False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TmemAllocator.__init__ "Link to this definition")

Initialize a TmemAllocator instance for managing tensor memory on Blackwell GPUs.

This initializer sets up the allocator’s state, including the shared memory (smem) pointer holding the base address of the allocated tensor memory, barrier synchronization for retrieving the tensor memory pointer, allocator warp ID, whether the allocator is being used for a 2-SM configuration, number of allocated columns in tensor memory, and the optional mbarrier pointer for deallocation in the 2-SM case.

If is\_two\_cta is set to True, this will initialize the mbarrier pointer required for tensor memory deallocation across two CTAs.

Parameters:

-   **alloc\_result\_dst\_smem\_ptr** (_cute.Pointer_) – The shared memory pointer that holds the base address of allocated tensor memory.
-   **barrier\_for\_retrieve** ([_pipeline.NamedBarrier_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier "cutlass.pipeline.NamedBarrier")) – The named barrier for retrieving the tensor memory pointer.
-   **allocator\_warp\_id** (_int__,_ _optional_) – The warp ID of the allocator warp, defaults to 0.
-   **is\_two\_cta** (_bool__,_ _optional_) – Whether the allocator should coordinate two CTAs, defaults to False.
-   **num\_allocated\_columns** (_int__,_ _optional_) – The number of columns allocated in tensor memory, defaults to 0.
-   **two\_cta\_tmem\_dealloc\_mbar\_ptr** (_cute.Pointer__,_ _optional_) – The mbarrier pointer required for two-CTA tensor memory deallocation, optional.
-   **loc** (_Any__,_ _optional_) – Optional codegen location for debugging and error reporting.
-   **ip** (_Any__,_ _optional_) – Optional insertion point for codegen.

Raises:

**AssertionError** – If two\_cta\_tmem\_dealloc\_mbar\_ptr is None while is\_two\_cta is True.

check\_valid\_num\_columns(_num\_columns: int_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TmemAllocator.check_valid_num_columns "Link to this definition")

Check if the number of columns is valid.

This method checks if the number of columns is valid. It checks if the number of columns is larger than 0, smaller than max capacity, a multiple of 32, and a power of two.

wait\_for\_alloc(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TmemAllocator.wait_for_alloc "Link to this definition")

Wait for the allocator warp to finish allocation.

This method is used to synchronize the allocator warp with the other warps before retrieving tmem ptr.

retrieve\_ptr(

_dtype: Type\[cutlass.cutlass\_dsl.Numeric\] \= cutlass.cutlass\_dsl.Float32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TmemAllocator.retrieve_ptr "Link to this definition")

Retrieve the pointer to the allocated tensor memory.

This method can be called by all warps after allocation has been performed by the allocator warp.

cutlass.utils.get\_num\_tmem\_alloc\_cols(

_tmem\_tensors: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\]_,

_rounding\=True_,

_\*_,

_arch: str \= 'sm\_100'_,

_loc\=None_,

_ip\=None_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_num_tmem_alloc_cols "Link to this definition")

Get the total number of TMEM allocation columns for the given TMEM tensors.

Parameters:

-   **tmem\_tensors** (_Union__\[__cute.Tensor__,_ _List__\[__cute.Tensor__\]__\]_) – The TMEM tensors to get the number of allocation columns for.
-   **rounding** (_bool_) – Whether to round up the number of allocation columns to the nearest power of 2.
-   **arch** (_str_) – The architecture of the GPU.

Returns:

The total number of TMEM allocation columns.

Return type:

int

Raises:

**ValueError** – If the number of TMEM allocation columns exceeds the maximum capacity or is less than 32.

_class_ cutlass.utils.LayoutEnum(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "Link to this definition")

Bases: `Enum`

An enumeration.

ROW\_MAJOR _\= 'row\_major'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.ROW_MAJOR "Link to this definition")

COL\_MAJOR _\= 'col\_major'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.COL_MAJOR "Link to this definition")

mma\_major\_mode()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.mma_major_mode "Link to this definition")

sm90\_mma\_major\_mode()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.sm90_mma_major_mode "Link to this definition")

is\_k\_major\_a()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.is_k_major_a "Link to this definition")

is\_m\_major\_a()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.is_m_major_a "Link to this definition")

is\_n\_major\_b()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.is_n_major_b "Link to this definition")

is\_k\_major\_b()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.is_k_major_b "Link to this definition")

is\_n\_major\_c()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.is_n_major_c "Link to this definition")

is\_m\_major\_c()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.is_m_major_c "Link to this definition")

_static_ from\_tensor(

_tensor: cutlass.cute.typing.Tensor_,

) → [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum.from_tensor "Link to this definition")

_class_ cutlass.utils.WorkTileInfo(

_tile\_idx: cutlass.cute.typing.Coord_,

_is\_valid\_tile: cutlass.cutlass\_dsl.Boolean_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "Link to this definition")

Bases: `object`

A class to represent information about a work tile.

Variables:

-   **tile\_idx** – The index of the tile.
-   **is\_valid\_tile** – Whether the tile is valid.

\_\_init\_\_(

_tile\_idx: cutlass.cute.typing.Coord_,

_is\_valid\_tile: cutlass.cutlass\_dsl.Boolean_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo.__init__ "Link to this definition")

_property_ is\_valid\_tile_: cutlass.cutlass\_dsl.Boolean_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo.is_valid_tile "Link to this definition")

Check latest tile returned by the scheduler is valid or not. Any scheduling requests after all tasks completed will return an invalid tile.

Returns:

The validity of the tile.

Return type:

Boolean

_property_ tile\_idx_: cutlass.cute.typing.Coord_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo.tile_idx "Link to this definition")

Get the index of the tile.

Returns:

The index of the tile.

Return type:

cute.Coord

_class_ cutlass.utils.PersistentTileSchedulerParams[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "Link to this definition")

Bases: `object`

A class to represent parameters for a persistent tile scheduler.

This class is designed to manage and compute the layout of clusters and tiles in a batched gemm problem.

Variables:

-   **cluster\_shape\_mn** – Shape of the cluster in (m, n) dimensions (K dimension cta count must be 1).
-   **problem\_layout\_ncluster\_mnl** – Layout of the problem in terms of number of clusters in (m, n, l) dimensions.

\_\_init\_\_(

_problem\_shape\_ntile\_mnl: cutlass.cute.typing.Shape_,

_cluster\_shape\_mnk: cutlass.cute.typing.Shape_,

_swizzle\_size: int \= 1_,

_raster\_along\_m: bool \= True_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams.__init__ "Link to this definition")

Initializes the PersistentTileSchedulerParams with the given parameters.

Parameters:

-   **problem\_shape\_ntile\_mnl** (_cute.Shape_) – The shape of the problem in terms of number of CTA (Cooperative Thread Array) in (m, n, l) dimensions.
-   **cluster\_shape\_mnk** (_cute.Shape_) – The shape of the cluster in (m, n) dimensions.
-   **swizzle\_size** (_int_) – Swizzling size in the unit of cluster. 1 means no swizzle
-   **raster\_along\_m** (_bool_) – Rasterization order of clusters. Only used when swizzle\_size > 1. True means along M, false means along N.

Raises:

**ValueError** – If cluster\_shape\_k is not 1.

get\_grid\_shape(

_max\_active\_clusters: cutlass.cutlass\_dsl.Int32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams.get_grid_shape "Link to this definition")

Computes the grid shape based on the maximum active clusters allowed.

Parameters:

**max\_active\_clusters** (_Int32_) – The maximum number of active clusters that can run in one wave.

Returns:

A tuple containing the grid shape in (m, n, persistent\_clusters). - m: self.cluster\_shape\_m. - n: self.cluster\_shape\_n. - persistent\_clusters: Number of persistent clusters that can run.

_class_ cutlass.utils.StaticPersistentTileScheduler(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_num\_persistent\_clusters: cutlass.cutlass\_dsl.Int32_,

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_id\_in\_cluster: cutlass.cute.typing.Coord_,

_num\_tiles\_executed: cutlass.cutlass\_dsl.Int32_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler "Link to this definition")

Bases: `object`

A scheduler for static persistent tile execution in CUTLASS/CuTe kernels.

Variables:

-   **params** – Tile schedule related params, including cluster shape and problem\_layout\_ncluster\_mnl
-   **num\_persistent\_clusters** – Number of persistent clusters that can be launched
-   **cta\_id\_in\_cluster** – ID of the CTA within its cluster
-   **\_num\_tiles\_executed** – Counter for executed tiles
-   **\_current\_work\_linear\_idx** – Current cluster index

\_\_init\_\_(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_num\_persistent\_clusters: cutlass.cutlass\_dsl.Int32_,

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_id\_in\_cluster: cutlass.cute.typing.Coord_,

_num\_tiles\_executed: cutlass.cutlass\_dsl.Int32_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.__init__ "Link to this definition")

Initializes the StaticPersistentTileScheduler with the given parameters.

Parameters:

-   **params** ([_PersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.PersistentTileSchedulerParams")) – Tile schedule related params, including cluster shape and problem\_layout\_ncluster\_mnl.
-   **num\_persistent\_clusters** (_Int32_) – Number of persistent clusters that can be launched.
-   **current\_work\_linear\_idx** (_Int32_) – Current cluster index.
-   **cta\_id\_in\_cluster** (_cute.Coord_) – ID of the CTA within its cluster.
-   **num\_tiles\_executed** (_Int32_) – Counter for executed tiles.

_static_ create(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_block\_idx: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

_grid\_dim: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.create "Link to this definition")

Initialize the static persistent tile scheduler.

Parameters:

-   **params** ([_PersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.PersistentTileSchedulerParams")) – Parameters for the persistent tile scheduler.
-   **block\_idx** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The 3d block index in the format (bidx, bidy, bidz).
-   **grid\_dim** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The 3d grid dimensions for kernel launch.

Returns:

A StaticPersistentTileScheduler object.

Return type:

[StaticPersistentTileScheduler](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler "cutlass.utils.StaticPersistentTileScheduler")

_static_ get\_grid\_shape(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_max\_active\_clusters: cutlass.cutlass\_dsl.Int32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.get_grid_shape "Link to this definition")

Calculates the grid shape to be launched on GPU using problem shape, threadblock shape, and active cluster size.

Parameters:

-   **params** ([_PersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.PersistentTileSchedulerParams")) – Parameters for grid shape calculation.
-   **max\_active\_clusters** (_Int32_) – Maximum active clusters allowed.

Returns:

The calculated 3d grid shape.

Return type:

Tuple\[Integer, Integer, Integer\]

\_get\_current\_work\_for\_linear\_idx(

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler._get_current_work_for_linear_idx "Link to this definition")

Compute current tile coord given current\_work\_linear\_idx and cta\_id\_in\_cluster.

Parameters:

**current\_work\_linear\_idx** (_Int32_) – The linear index of the current work.

Returns:

An object containing information about the current tile coordinates and validity status.

Return type:

[WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.WorkTileInfo")

\_get\_cluster\_work\_idx\_with\_fastdivmod(

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cutlass\_dsl.Int32, cutlass.cutlass\_dsl.Int32, cutlass.cutlass\_dsl.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler._get_cluster_work_idx_with_fastdivmod "Link to this definition")

FastDivmod optimized CLUSTER coordinate calculation.

CRITICAL: This should mimic problem\_layout\_ncluster\_mnl.get\_hier\_coord() which returns CLUSTER coordinates, not tile coordinates!

Parameters:

**current\_work\_linear\_idx** (_Int32_) – Linear index in the work space

Returns:

Cluster coordinates (m, n, l) or None if FastDivmod not available

Return type:

Tuple\[Int32, Int32, Int32\] or None

get\_current\_work(

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.get_current_work "Link to this definition")

initial\_work\_tile\_info(

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.initial_work_tile_info "Link to this definition")

advance\_to\_next\_work(

_\*_,

_advance\_count: int \= 1_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.advance_to_next_work "Link to this definition")

_property_ num\_tiles\_executed_: cutlass.cutlass\_dsl.Int32_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler.num_tiles_executed "Link to this definition")

_class_ cutlass.utils.StaticPersistentRuntimeTileScheduler(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_num\_persistent\_clusters: cutlass.cutlass\_dsl.Int32_,

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_id\_in\_cluster: cutlass.cute.typing.Coord_,

_num\_tiles\_executed: cutlass.cutlass\_dsl.Int32_,

_inner\_mode: int \= 1_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentRuntimeTileScheduler "Link to this definition")

Bases: [`StaticPersistentTileScheduler`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentTileScheduler "cutlass.utils.static_persistent_tile_scheduler.StaticPersistentTileScheduler")

A scheduler for static persistent runtime tile execution in CUTLASS/CuTe kernels. This scheduler will always launch all the SMs and the scheduler will generate the real tile info for each SM.

Variables:

-   **params** – Tile schedule related params, including cluster shape and problem\_layout\_ncluster\_mnl
-   **num\_persistent\_clusters** – Number of persistent clusters that can be launched
-   **cta\_id\_in\_cluster** – ID of the CTA within its cluster
-   **\_num\_tiles\_executed** – Counter for executed tiles
-   **\_current\_work\_linear\_idx** – Current cluster index

\_\_init\_\_(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_num\_persistent\_clusters: cutlass.cutlass\_dsl.Int32_,

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_id\_in\_cluster: cutlass.cute.typing.Coord_,

_num\_tiles\_executed: cutlass.cutlass\_dsl.Int32_,

_inner\_mode: int \= 1_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentRuntimeTileScheduler.__init__ "Link to this definition")

Initializes the StaticPersistentTileScheduler with the given parameters.

Parameters:

-   **params** ([_PersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.PersistentTileSchedulerParams")) – Tile schedule related params, including cluster shape and problem\_layout\_ncluster\_mnl.
-   **num\_persistent\_clusters** (_Int32_) – Number of persistent clusters that can be launched.
-   **current\_work\_linear\_idx** (_Int32_) – Current cluster index.
-   **cta\_id\_in\_cluster** (_cute.Coord_) – ID of the CTA within its cluster.
-   **num\_tiles\_executed** (_Int32_) – Counter for executed tiles.
-   **inner\_mode** (_int_) – The inner mode along which the linear index will be decomposed first.

_static_ create(

_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_block\_idx: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

_grid\_dim: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

_inner\_mode: int \= 1_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentRuntimeTileScheduler.create "Link to this definition")

Initialize the static persistent tile scheduler.

Parameters:

-   **params** ([_PersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.PersistentTileSchedulerParams")) – Parameters for the persistent tile scheduler.
-   **block\_idx** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The 3d block index in the format (bidx, bidy, bidz).
-   **grid\_dim** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The 3d grid dimensions for kernel launch.
-   **inner\_mode** (_int_) – The inner mode along which the linear index will be decomposed first.

Returns:

A StaticPersistentRuntimeTileScheduler object.

Return type:

[StaticPersistentRuntimeTileScheduler](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentRuntimeTileScheduler "cutlass.utils.StaticPersistentRuntimeTileScheduler")

\_get\_current\_work\_for\_linear\_idx(

_current\_work\_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.StaticPersistentRuntimeTileScheduler._get_current_work_for_linear_idx "Link to this definition")

Compute current tile coord given current\_work\_linear\_idx and cta\_id\_in\_cluster.

Parameters:

**current\_work\_linear\_idx** (_Int32_) – The linear index of the current work.

Returns:

An object containing information about the current tile coordinates and validity status.

Return type:

[WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.WorkTileInfo")

_class_ cutlass.utils.TensorMapUpdateMode(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapUpdateMode "Link to this definition")

Bases: `Enum`

Enum class defining tensor map update modes.

Modes: GMEM: Update tensormap in global memory SMEM: Load tensormap from global memory to shared memory, update it in shared memory, then store back to global memory

GMEM _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapUpdateMode.GMEM "Link to this definition")

SMEM _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapUpdateMode.SMEM "Link to this definition")

_class_ cutlass.utils.TensorMapManager(

_tensormap\_update\_mode: [TensorMapUpdateMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapUpdateMode "cutlass.utils.tensormap_manager.TensorMapUpdateMode")_,

_bytes\_per\_tensormap: int_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager "Link to this definition")

Bases: `object`

Manages TensorMap operations including initialization and updates. Provides utilities to convert tensormap pointer to across different memory spaces.

tensormap\_update\_mode_: [TensorMapUpdateMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapUpdateMode "cutlass.utils.tensormap_manager.TensorMapUpdateMode")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager.tensormap_update_mode "Link to this definition")

bytes\_per\_tensormap_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager.bytes_per_tensormap "Link to this definition")

get\_tensormap\_ptr(

_ptr: cutlass.cute.typing.Pointer_,

_address\_space\=cutlass.\_mlir.dialects.cute.AddressSpace.gmem_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager.get_tensormap_ptr "Link to this definition")

fence\_tensormap\_initialization(

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager.fence_tensormap_initialization "Link to this definition")

fence\_tensormap\_update(

_tensormap\_ptr: cutlass.cute.typing.Pointer_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager.fence_tensormap_update "Link to this definition")

\_\_init\_\_(

_tensormap\_update\_mode: [TensorMapUpdateMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapUpdateMode "cutlass.utils.tensormap_manager.TensorMapUpdateMode")_,

_bytes\_per\_tensormap: int_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TensorMapManager.__init__ "Link to this definition")

_class_ cutlass.utils.GroupSearchResult(

_group\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_idx\_m: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_idx\_n: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_m: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_n: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_k: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_count\_k: cutlass.cutlass\_dsl.Int32_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupSearchResult "Link to this definition")

Bases: `object`

The result of the group search for grouped gemm.

Parameters:

-   **group\_idx** (_Int32_) – The result group index
-   **cta\_tile\_idx\_m** (_Int32_) – CTA tile index along M dimension after rasterization
-   **cta\_tile\_idx\_n** (_Int32_) – CTA tile index along N dimension after rasterization
-   **problem\_shape\_m** (_Int32_) – The M dimension of the gemm problem
-   **problem\_shape\_n** (_Int32_) – The N dimension of the gemm problem
-   **problem\_shape\_k** (_Int32_) – The K dimension of the gemm problem
-   **cta\_tile\_count\_k** (_Int32_) – Number of tiles along K dimension

\_\_init\_\_(

_group\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_idx\_m: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_idx\_n: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_m: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_n: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_k: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_count\_k: cutlass.cutlass\_dsl.Int32_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupSearchResult.__init__ "Link to this definition")

_class_ cutlass.utils.GroupedGemmGroupSearchState(

_start\_group\_idx: cutlass.cutlass\_dsl.Int32_,

_tile\_count\_prev\_group: cutlass.cutlass\_dsl.Int32_,

_tile\_count\_searched: cutlass.cutlass\_dsl.Int32_,

_found: cutlass.cutlass\_dsl.Boolean_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "Link to this definition")

Bases: `object`

The state of group index search for grouped gemm.

The state will be initialized once and updated in every round of group index search.

Parameters:

-   **start\_group\_idx** (_Int32_) – The group idx to start the search with
-   **tile\_count\_prev\_group** (_Int32_) – Number of tiles before the matched group
-   **tile\_count\_searched** (_Int32_) – Number of tiles we have searched. When the matched group is found, it records the number of tiles including the matched group

\_\_init\_\_(

_start\_group\_idx: cutlass.cutlass\_dsl.Int32_,

_tile\_count\_prev\_group: cutlass.cutlass\_dsl.Int32_,

_tile\_count\_searched: cutlass.cutlass\_dsl.Int32_,

_found: cutlass.cutlass\_dsl.Boolean_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState.__init__ "Link to this definition")

cutlass.utils.create\_initial\_search\_state() → [GroupedGemmGroupSearchState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "cutlass.utils.grouped_gemm_persistent_tile_scheduler.GroupedGemmGroupSearchState")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.create_initial_search_state "Link to this definition")

Create an initial search state for grouped gemm.

Returns:

A new search state with initial values

Return type:

[GroupedGemmGroupSearchState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "cutlass.utils.GroupedGemmGroupSearchState")

_class_ cutlass.utils.GroupedGemmTileSchedulerHelper(_\*\*kwargs_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper "Link to this definition")

Bases: `object`

A helper to translate the raw block index (x, y, z) from tile scheduler to real CTA tile index for grouped gemm.

Parameters:

-   **group\_count** (_int_) – Number of groups in current grouped gemm problem
-   **tile\_sched\_params** ([_PersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.PersistentTileSchedulerParams")) – Parameter used to create the tile scheduler this helper works with
-   **cluster\_tile\_shape\_mnk** (_tuple__\[__int__,_ _int__,_ _int__\]_) – The shape of cluster tile as (m, n, k)
-   **search\_state** ([_GroupedGemmGroupSearchState_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "cutlass.utils.GroupedGemmGroupSearchState")) – The initial search state

\_\_init\_\_(

_group\_count: int_,

_tile\_sched\_params: [PersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.PersistentTileSchedulerParams "cutlass.utils.static_persistent_tile_scheduler.PersistentTileSchedulerParams")_,

_cluster\_tile\_shape\_mnk: tuple\[int, int, int\]_,

_search\_state: [GroupedGemmGroupSearchState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "cutlass.utils.grouped_gemm_persistent_tile_scheduler.GroupedGemmGroupSearchState")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper.__init__ "Link to this definition")

delinearize\_z(

_cta\_tile\_coord: tuple_,

_problem\_shape\_mnkl: cutlass.cute.typing.Tensor_,

) → [GroupSearchResult](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupSearchResult "cutlass.utils.grouped_gemm_persistent_tile_scheduler.GroupSearchResult")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper.delinearize_z "Link to this definition")

Delinearize the linear z index and return GroupSearchResult.

This function should be used by warps that need to know the CTA tile index on M and N dimensions.

Parameters:

-   **cta\_tile\_coord** (_tuple_ _of_ _Int32_) – The raw CTA coordinate from tile scheduler
-   **problem\_shape\_mnkl** (_cute.Tensor_) – Tensor containing gemm problem size (M, N, K, L) for each group

Returns:

The search result containing group index and tile coordinates

Return type:

[GroupSearchResult](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupSearchResult "cutlass.utils.GroupSearchResult")

search\_cluster\_tile\_count\_k(

_cta\_tile\_coord: tuple_,

_problem\_shape\_mnkl: cutlass.cute.typing.Tensor_,

) → Tuple\[cutlass.cutlass\_dsl.Int32, cutlass.cutlass\_dsl.Int32\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper.search_cluster_tile_count_k "Link to this definition")

Search the matched group for given linear index and compute the number of tiles along K dimension for the matched group.

This function should be used by warps that are only interested in the number of tiles along K dimension.

Parameters:

-   **cta\_tile\_coord** (_tuple_ _of_ _Int32_) – The raw CTA coordinate from tile scheduler
-   **problem\_shape\_mnkl** (_cute.Tensor_) – Tensor containing gemm problem size (M, N, K, L) for all groups

Returns:

A tuple containing cluster count along K dimension and the group index

Return type:

Tuple\[Int32, Int32\]

\_prefix\_sum(

_value\_per\_thread: cutlass.cutlass\_dsl.Int32_,

) → cutlass.cutlass\_dsl.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper._prefix_sum "Link to this definition")

Perform prefix sum within a full warp.

Parameters:

**value\_per\_thread** (_Int32_) – The value for this thread to contribute to the prefix sum

Returns:

The prefix sum result for this thread

Return type:

Int32

\_get\_problem\_for\_group(

_problem\_shape\_mnkl: cutlass.cute.typing.Tensor_,

_group\_idx: cutlass.cutlass\_dsl.Int32_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper._get_problem_for_group "Link to this definition")

Load gemm problem (m,n,k,l) for the specified group from global memory to register.

Parameters:

-   **problem\_shape\_mnkl** (_cute.Tensor_) – Tensor in global memory with layout (group\_count, 4):(4, 1)
-   **group\_idx** (_Int32_) – The index of the group to load

Returns:

The problem shape tensor for the specified group

Return type:

cute.Tensor

\_get\_cluster\_tile\_count\_mn(

_problem\_shape: cutlass.cute.typing.Tensor_,

) → cutlass.cutlass\_dsl.Int32[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper._get_cluster_tile_count_mn "Link to this definition")

Compute total cluster count.

Parameters:

**problem\_shape** (_cute.Tensor_) – Tensor containing problem shape (m, n, k, l)

Returns:

The total cluster tile count for M and N dimensions

Return type:

Int32

\_compute\_cta\_tile\_coord(

_cluster\_tile\_idx: cutlass.cutlass\_dsl.Int32_,

_cta\_tile\_coord\_in\_cluster: tuple_,

_cluster\_tile\_count\_m: cutlass.cutlass\_dsl.Int32_,

_cluster\_tile\_count\_n: cutlass.cutlass\_dsl.Int32_,

) → tuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper._compute_cta_tile_coord "Link to this definition")

Compute CTA tile indices along M and N dimensions based on the linear index within a group.

It uses the AlongM mode to decompose the linear index onto M and N dimensions.

Parameters:

-   **cluster\_tile\_idx** (_Int32_) – The linear index within a group
-   **cta\_tile\_coord\_in\_cluster** (_tuple_ _of_ _Int32_) – CTA indices along M and N dimensions within a cluster
-   **cluster\_tile\_count\_m** (_Int32_) – The number of clusters along M dimension of the matched group
-   **cluster\_tile\_count\_n** (_Int32_) – The number of clusters along N dimension of the matched group

Returns:

A tuple containing CTA tile indices along M and N dimensions

Return type:

tuple of (Int32, Int32)

\_group\_search(

_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_mnkl: cutlass.cute.typing.Tensor_,

_init\_group\_idx: cutlass.cutlass\_dsl.Int32_,

_init\_tile\_count\_searched: cutlass.cutlass\_dsl.Int32_,

) → [GroupedGemmGroupSearchState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "cutlass.utils.grouped_gemm_persistent_tile_scheduler.GroupedGemmGroupSearchState")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper._group_search "Link to this definition")

Search which group the linear index belongs to.

Parameters:

-   **linear\_idx** (_Int32_) – The linear index to be decomposed
-   **problem\_shape\_mnkl** (_cute.Tensor_) – Tensor containing gemm problem size (M, N, K, L) for all groups
-   **init\_group\_idx** (_Int32_) – The group idx to start the search with
-   **init\_tile\_count\_searched** (_Int32_) – The number of tiles we have searched

Returns:

The updated search state

Return type:

[GroupedGemmGroupSearchState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmGroupSearchState "cutlass.utils.GroupedGemmGroupSearchState")

\_group\_search\_and\_load\_problem\_shape(

_linear\_idx: cutlass.cutlass\_dsl.Int32_,

_problem\_shape\_mnkl: cutlass.cute.typing.Tensor_,

_start\_group\_idx: cutlass.cutlass\_dsl.Int32_,

_tile\_count\_searched: cutlass.cutlass\_dsl.Int32_,

) → Tuple\[cutlass.cutlass\_dsl.Int32, cutlass.cute.typing.Tensor\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.GroupedGemmTileSchedulerHelper._group_search_and_load_problem_shape "Link to this definition")

Perform group search and load problem shape for the matched group.

Parameters:

-   **linear\_idx** (_Int32_) – The linear index to be decomposed
-   **problem\_shape\_mnkl** (_cute.Tensor_) – Tensor containing gemm problem size (M, N, K, L) for all groups
-   **start\_group\_idx** (_Int32_) – The group idx to start the search with
-   **tile\_count\_searched** (_Int32_) – The number of tiles we have searched

Returns:

A tuple containing the final group index and the problem shape tensor

Return type:

Tuple\[Int32, cute.Tensor\]

_class_ cutlass.utils.HardwareInfo(_device\_id: int \= 0_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo "Link to this definition")

Bases: `object`

device\_id: CUDA device ID to get the hardware info.

\_\_init\_\_(_device\_id: int \= 0_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo.__init__ "Link to this definition")

get\_max\_active\_clusters(

_cluster\_size: int_,

_stream: cuda.bindings.driver.CUstream | None \= None_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo.get_max_active_clusters "Link to this definition")

Get the maximum number of active clusters for a given cluster size.

When a stream from a green context is provided, the occupancy calculation will reflect the reduced SM partition of the green context.

Parameters:

-   **cluster\_size** (_int_) – Number of blocks per cluster (must be between 1 and 32)
-   **stream** (_driver.CUstream__,_ _optional_) – Optional CUDA stream handle. If provided (especially from a green context), the occupancy calculation reflects the stream’s SM partition.

Returns:

Maximum number of active clusters

Return type:

int

get\_l2\_cache\_size\_in\_bytes() → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo.get_l2_cache_size_in_bytes "Link to this definition")

get\_device\_multiprocessor\_count() → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo.get_device_multiprocessor_count "Link to this definition")

\_checkCudaErrors(_result_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._checkCudaErrors "Link to this definition")

\_cudaGetErrorEnum(_error_) → str[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._cudaGetErrorEnum "Link to this definition")

\_cuda\_driver\_version\_ge(_major: int_, _minor: int_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._cuda_driver_version_ge "Link to this definition")

\_cuda\_driver\_version\_lt(_major: int_, _minor: int_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._cuda_driver_version_lt "Link to this definition")

\_empty\_kernel()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._empty_kernel "Link to this definition")

\_host\_function()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._host_function "Link to this definition")

\_get\_device\_function() → cuda.bindings.driver.CUfunction[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.HardwareInfo._get_device_function "Link to this definition")

Get a device function by compiling a dummy kernel using cuteDSL pipeline.

_class_ cutlass.utils.TransformMode(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TransformMode "Link to this definition")

Bases: `Enum`

An enumeration for the possible transform modes of a mixed-input GEMM.

ConvertOnly _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TransformMode.ConvertOnly "Link to this definition")

ConvertScale _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TransformMode.ConvertScale "Link to this definition")

cutlass.utils.scale\_tma\_partition(

_tCsS: cutlass.cute.typing.Tensor_,

_tCgS: cutlass.cute.typing.Tensor_,

_tma\_atom\_s: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_block\_in\_cluster\_coord\_vmnk: cutlass.cute.typing.Coord_,

_scale\_cta\_layout: cutlass.cute.typing.Layout_,

) → tuple\[cutlass.cute.typing.Tensor, cutlass.cute.typing.Tensor\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.scale_tma_partition "Link to this definition")

Perform TMA partition for scale tensor. This method partitions the global memory and shared memory buffer for the scale tensor for TMA load. :param tCsS: Input scale shared memory tensor :type tCsS: cute.Tensor :param tCgS: Input scale global memory tensor :type tCgS: cute.Tensor :param tma\_atom\_s: TMA copy atom for scale tensor :type tma\_atom\_s: cute.CopyAtom :param block\_in\_cluster\_coord\_vmnk: CTA coord in the cluster :type block\_in\_cluster\_coord\_vmnk: cute.Coord :param scale\_cta\_layout: Layout of CTA from the view of the scale tensor :type scale\_cta\_layout: cute.Layout :return: A tuple containing (tSsS, tSgS) where:

> -   tSsS: Partitioned scale tensor in shared memory
> -   tSgS: Partitioned scale tensor in global memory

Return type:

tuple\[cute.Tensor, cute.Tensor\]

cutlass.utils.transform\_partition(

_transform\_a\_source: [tcgen05.OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.OperandSource")_,

_scale\_mode: [TransformMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.TransformMode "cutlass.utils.TransformMode")_,

_copy\_atom\_a\_input: [cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")_,

_copy\_atom\_a\_transform: [cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")_,

_sA\_input: cute.Tensor_,

_A\_transform: cute.Tensor_,

_transform\_local\_tidx: cutlass.Int32_,

) → tuple\[[cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy") | None, [cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy") | None, cute.Tensor, cute.Tensor\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.transform_partition "Link to this definition")

Partition tensors for transform input and output. This method sets up the copy atoms and partitions the shared/tensor memory for the transformation of tensor A. :param transform\_a\_source: Where the transformed tensor A is stored (TMEM or SMEM) :type transform\_a\_source: tcgen05.OperandSource :param scale\_mode: The transform mode (ConvertOnly or ConvertScale) :type scale\_mode: TransformMode :param copy\_atom\_a\_input: Copy atom for loading A from shared memory :type copy\_atom\_a\_input: cute.CopyAtom :param copy\_atom\_a\_transform: Copy atom for storing transformed A :type copy\_atom\_a\_transform: cute.CopyAtom :param sA\_input: Input tensor A in shared memory :type sA\_input: cute.Tensor :param A\_transform: Transformed tensor A in tensor or shared memory :type A\_transform: cute.Tensor :param transform\_local\_tidx: Local thread index for transformation warps :type transform\_local\_tidx: cutlass.Int32 :return: A tuple containing (src\_copy\_a, dst\_copy\_a, tAsA\_input, tA\_transform) where:

> -   src\_copy\_a: Tiled copy for source tensor
> -   dst\_copy\_a: Tiled copy for destination tensor
> -   tAsA\_input: Partitioned input tensor A
> -   tA\_transform: Partitioned transformed tensor A

Return type:

tuple\[Optional\[[cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")\], Optional\[[cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")\], cute.Tensor, cute.Tensor\]

cutlass.utils.scale\_partition(

_src\_copy\_a: [cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")_,

_tCsS: cute.Tensor_,

_transform\_local\_tidx: cutlass.Int32_,

_mma\_dtype: type\[cutlass.Numeric\]_,

) → tuple\[[cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy"), cute.Tensor, cute.Tensor, cute.Tensor\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.scale_partition "Link to this definition")

Partition the scale tensor for transformation. This method prepares the copy atom and partitions the shared memory for the scale tensor. :param src\_copy\_a: Tiled copy for the source tensor :type src\_copy\_a: cute.TiledCopy :param tCsS: Scale tensor in shared memory :type tCsS: cute.Tensor :param transform\_local\_tidx: Local thread index for transformation warps :type transform\_local\_tidx: cutlass.Int32 :param mma\_dtype: Data type for the MMA operation :type mma\_dtype: type\[cutlass.Numeric\] :return: A tuple containing (smem\_thr\_copy\_S, tSsS\_trans, tSrS\_copy, tSrS) where:

> -   smem\_thr\_copy\_S: Tiled copy for the scale tensor
> -   tSsS\_trans: Partitioned scale tensor for transformation
> -   tSrS\_copy: Register fragment for the scale tensor
> -   tSrS: View of scale tensor used for transformation computation

Return type:

tuple\[[cute.TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy"), cute.Tensor, cute.Tensor, cute.Tensor\]

cutlass.utils.get\_gmem\_layout\_scale(

_scale\_shape\_mkl: tuple\[int, int, int\]_,

_scale\_granularity\_m: int_,

_scale\_granularity\_k: int_,

_scale\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → cutlass.cute.typing.Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_gmem_layout_scale "Link to this definition")

Get the layout of the scale tensor in global memory. :param scale\_shape\_mkl: The shape of the scale tensor (M, K, L). :type scale\_shape\_mkl: tuple\[int, int, int\] :return: The layout of the scale tensor in global memory. :rtype: cute.Layout

cutlass.utils.get\_smem\_layout\_scale(

_mma\_tiler: tuple\[int, int, int\]_,

_use\_2cta\_instrs: bool_,

_scale\_granularity\_m: int_,

_scale\_granularity\_k: int_,

_scale\_major\_mode: [tcgen05.OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")_,

_a\_scale\_dtype: type\[cutlass.Numeric\]_,

_num\_scale\_load2trans\_stage: int_,

) → tuple\[tuple\[int, int\], cute.ComposedLayout, cute.ComposedLayout\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_smem_layout_scale "Link to this definition")

Get the layout of the scale tensor in shared memory. :return: A tuple containing (scale\_tile\_shape, smem\_layout\_scale\_per\_stage, smem\_layout\_scale) where:

> -   scale\_tile\_shape: The tile shape
> -   smem\_layout\_scale\_per\_stage: Shared memory layout for scale tensor per stage
> -   smem\_layout\_scale: Shared memory layout for scale tensor

Return type:

tuple\[tuple\[int, int\], cute.ComposedLayout, cute.ComposedLayout\]

cutlass.utils.compute\_smem\_layout(

_tiled\_mma: [cute.TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")_,

_mma\_tiler\_mnk: tuple\[int, int, int\]_,

_a\_dtype: type\[cutlass.Numeric\]_,

_b\_dtype: type\[cutlass.Numeric\]_,

_load2trans\_stage\_count: int_,

_trans2mma\_stage\_count: int_,

) → tuple\[cute.ComposedLayout, cute.ComposedLayout, cute.ComposedLayout\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.compute_smem_layout "Link to this definition")

Compute shared memory layouts for tensor A, transformed A and tensor B. :param tiled\_mma: The tiled MMA object defining the core computation. :type tiled\_mma: cute.TiledMma :param mma\_tiler\_mnk: The shape (M, N, K) of the MMA tiler. :type mma\_tiler\_mnk: tuple\[int, int, int\] :param a\_dtype: Data type of operand A. :type a\_dtype: type\[cutlass.Numeric\] :param b\_dtype: Data type of operand B. :type b\_dtype: type\[cutlass.Numeric\] :param load2trans\_stage\_count: Number of stages for load-to-transform pipeline. :type load2trans\_stage\_count: int :param trans2mma\_stage\_count: Number of stages for transform-to-MMA pipeline. :type trans2mma\_stage\_count: int :return: A tuple containing (smem\_layout\_a, smem\_layout\_a\_transform, smem\_layout\_b) where:

> -   smem\_layout\_a: Shared memory layout for tensor A
> -   smem\_layout\_a\_transform: Shared memory layout for transformed tensor A
> -   smem\_layout\_b: Shared memory layout for tensor B

Return type:

tuple\[cute.ComposedLayout, cute.ComposedLayout, cute.ComposedLayout\]

cutlass.utils.get\_transform\_a\_source(

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_transform_a_source "Link to this definition")

Determine the operand source for transformed A tensor based on the operand major mode.

cutlass.utils.get\_tma\_atom\_kind(

_mcast: cutlass.Boolean_,

_use\_2cta\_instrs: bool_,

_is\_b: bool_,

) → [cpasync.CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp") | [cpasync.CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_tma_atom_kind "Link to this definition")

Get the TMA atom kind based on 1) whether it’s a multicast operation, 2) whether 2CTA tcgen05.mma instruction is enabled, and 3) whether it’s a B tensor

cutlass.utils.get\_copy\_atom\_a\_transform(

_mma\_dtype: type\[cutlass.Numeric\]_,

_use\_2cta\_instrs: bool_,

_transform\_a\_source: [tcgen05.OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.OperandSource")_,

_a\_smem\_shape: cute.Shape_,

_a\_dtype: type\[cutlass.Numeric\]_,

) → [cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_copy_atom_a_transform "Link to this definition")

Determine the copy atom for transformed A tensor based on the operand source and tile size.

cutlass.utils.is\_valid\_scale\_granularity(

_scale\_granularity\_m: int_,

_scale\_granularity\_k: int_,

_a\_dtype: type\[cutlass.Numeric\]_,

_k: int_,

_mma\_tiler\_k: int_,

) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.is_valid_scale_granularity "Link to this definition")

Check if the scale granularity settings are valid for the given data type and problem size.

cutlass.utils.get\_divisibility(

_contiguous\_dim\_size: int_,

_upper\_bound: int \= 128_,

) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_divisibility "Link to this definition")

Calculate the largest power of 2 divisibility factor for memory alignment.

cutlass.utils.compute\_epilogue\_tile\_shape(

_cta\_tile\_shape: cutlass.cute.typing.Shape_,

_use\_2cta\_instrs: bool_,

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_\*_,

_layout\_c: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum") | None \= None_,

_elem\_ty\_c: Type\[cutlass.cutlass\_dsl.Numeric\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tile[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.compute_epilogue_tile_shape "Link to this definition")

Attempts to compute a reasonable epilogue tile based on block tile shape or allows the user to provide one.

Parameters:

-   **cta\_tile\_shape** (_cute.Shape_) – A tuple or list representing the dimensions of the CTA tile, where cta\_tile\_shape\[0\] corresponds to the height (M) and cta\_tile\_shape\[1\] corresponds to the width (N) of the tile.
-   **use\_2cta\_instrs** (_bool_) – A flag indicating whether the configuration is for a 2SM setup.
-   **layout\_d** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum of the output tensor D.
-   **elem\_ty\_d** (_Type__\[__Numeric__\]_) – The element type of output tensor D.
-   **layout\_c** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")_,_ _optional_) – The layout enum of the input tensor C. Defaults to None.
-   **elem\_ty\_c** (_Union__\[__Type__\[__Numeric__\]__,_ _None__\]__,_ _optional_) – The element type for input tensor C. Defaults to None.

Returns:

Returns epilog tiler, which is used in subsequent epilog partitions.

Return type:

cute.Tile

Raises:

**ValueError** – If the computed tile cute.size does not meet minimum requirements based on CTA dimensions.

cutlass.utils.get\_smem\_store\_op(

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_elem\_ty\_acc: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_tiled\_tmem\_load: [TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_smem_store_op "Link to this definition")

Selects the largest vectorized smem store atom available subject to constraint of gmem layout and chosen TMEM\_LOAD’s thread-value ownership.

Parameters:

-   **layout\_d** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum of the output tensor D.
-   **elem\_ty\_d** (_Type__\[__Numeric__\]_) – The element type for output tensor D.
-   **elem\_ty\_acc** (_Type__\[__Numeric__\]_) – The element type for accumulator.
-   **tiled\_tmem\_load** ([_cute.TiledCopy_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")) – An instance of TiledCopy that represents the tmem load operation.

Returns:

Either SmemStoreMatrix or SimtSyncCopy, based on the input parameters.

Return type:

[cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")

cutlass.utils.get\_tmem\_load\_op(

_cta\_tile\_shape: cutlass.cute.typing.Shape_,

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_elem\_ty\_acc: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_epi\_tile: cutlass.cute.typing.Tile_,

_use\_2cta\_instrs: bool_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.get_tmem_load_op "Link to this definition")

Finds a performant TMEM\_LOAD copy op for the selected epilogue tile (epi\_tile), element types, and tcgen05.mma instruction used.

Parameters:

-   **cta\_tile\_shape** (_cute.Shape_) – A tuple or list representing the dimensions of the CTA tile.
-   **layout\_d** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum of the output tensor D.
-   **elem\_ty\_d** (_Type__\[__Numeric__\]_) – The element type for output tensor D.
-   **elem\_ty\_acc** (_Type__\[__Numeric__\]_) – The element type for accumulation.
-   **epi\_tile** (_cute.Tile_) – The epilogue tile configuration.
-   **use\_2cta\_instrs** (_bool_) – A flag indicating whether the configuration is for 2 SMs.

Returns:

An instance of Sm100TmemLoad with the computed configuration.

Return type:

[cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")

Raises:

**ValueError** – If the function cannot handle the given combination of accumulation and dimension types, or if it cannot determine the appropriate configuration based on the input parameters.

cutlass.utils.make\_smem\_layout\_a(

_tiled\_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_mma\_tiler\_mnk: cutlass.cute.typing.Tile_,

_a\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_stages: int_,

_\*_,

_is\_k\_major\=None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.make_smem_layout_a "Link to this definition")

This function helps with:

1.  Get the partitioned shape of the A tensor based on the tiled\_mma & MMA tiler.
2.  Select the heuristic SMEM layout atom based on the A tensor’s majorness, the data type, and the major mode size.
3.  cute.Tile the SMEM layout atom to the MMA tile shape.
4.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **tiled\_mma** ([_cute.TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – The tiled MMA used to partition tensor A
-   **mma\_tiler\_mnk** (_cute.cute.Tile_) – The MMA tile shape
-   **a\_dtype** (_Type__\[__Numeric__\]_) – The element type for tensor A
-   **num\_stages** (_int_) – The number of pipeline stages for tensor A

Returns:

SMEM layout for tensor A

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.make\_smem\_layout\_b(

_tiled\_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_mma\_tiler\_mnk: cutlass.cute.typing.Tile_,

_b\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_stages: int_,

_\*_,

_is\_k\_major\=None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.make_smem_layout_b "Link to this definition")

This function helps:

1.  Get the partitioned shape of the B tensor based on the tiled\_mma & MMA tiler.
2.  Select the heuristic SMEM layout atom based on the B tensor’s majorness, the data type, and the major mode size.
3.  cute.Tile the SMEM layout atom to the MMA tile shape.
4.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **tiled\_mma** ([_cute.TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – The tiled MMA which is used to partition the B tensor.
-   **mma\_tiler\_mnk** (_cute.cute.Tile_) – The MMA tile shape.
-   **b\_dtype** (_Type__\[__Numeric__\]_) – The element type for the B tensor.
-   **num\_stages** (_int_) – The stage of the B tensor.

Returns:

SMEM layout for the B tensor.

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.make\_smem\_layout\_epi(

_epi\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_epi\_layout: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_epi\_tile: cutlass.cute.typing.Tile_,

_epi\_stage: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.make_smem_layout_epi "Link to this definition")

This function helps:

1.  Select the heuristic SMEM layout atom based on the epilog tile shape, the epilog tensor’s majorness, and the element type.
2.  cute.Tile the SMEM layout atom to the epilog tile shape.
3.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **epi\_dtype** (_Type__\[__Numeric__\]_) – The element type for the epilog tensor.
-   **epi\_layout** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum for the epilog tensor.
-   **epi\_tile** (_cute.cute.Tile_) – The epilogue tile shape.
-   **epi\_stage** (_int_) – The stage of the epilog tensor.

Returns:

SMEM layout for epilog tensors (usually C & D which are processed in the epilog)

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.make\_trivial\_tiled\_mma(

_ab\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_a\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_acc\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_mma\_tiler\_mn: Tuple\[int, int\]_,

_a\_source: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource") \= cutlass.\_mlir.dialects.cute.MmaFragKind.smem\_desc_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.make_trivial_tiled_mma "Link to this definition")

Make a tiled MMA atom with given data type, leading dimension, cta group and mma tile shape. By default, the MMA atom is created with SMEM operand source for A.

Parameters:

-   **ab\_dtype** (_type__\[__Numeric__\]_) – Data type of operands A and B.
-   **a\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand A (1 for K, 0 for M/N).
-   **b\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand B (1 for K, 0 for M/N).
-   **acc\_dtype** (_type__\[__Numeric__\]_) – Data type of the accumulator.
-   **cta\_group** ([_tcgen05.CtaGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.CtaGroup")) – The CTA group to use.
-   **mma\_tiler\_mn** (_Tuple__\[__int__,_ _int__\]_) – The shape (M, N, K) of the MMA tiler.
-   **a\_source** ([_cutlass.cute.nvgpu.tcgen05.OperandSource_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.OperandSource")) – The source of operand A (SMEM by default or TMEM).

Returns:

A tiled MMA atom.

Return type:

[cute.TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")

Raises:

**TypeError** – If the data type is not supported.

cutlass.utils.make\_blockscaled\_trivial\_tiled\_mma(

_ab\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_a\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_sf\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_sf\_vec\_size: int_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_mma\_tiler\_mn: Tuple\[int, int\]_,

_a\_source: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource") \= cutlass.\_mlir.dialects.cute.MmaFragKind.smem\_desc_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.make_blockscaled_trivial_tiled_mma "Link to this definition")

Make a BlockScaled tiled MMA atom with given data type, leading dimension, cta group and mma tile shape. By default, the MMA atom is created with SMEM operand source for A.

Parameters:

-   **ab\_dtype** (_type__\[__Numeric__\]_) – Data type of operands A and B.
-   **a\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand A (1 for K, 0 for M/N).
-   **b\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand B (1 for K, 0 for M/N).
-   **sf\_dtype** (_type__\[__Numeric__\]_) – Data type of the Scale Factor.
-   **sf\_vec\_size** (_int_) – The vector size of the Scale Factor.
-   **cta\_group** ([_tcgen05.CtaGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.CtaGroup")) – The CTA group to use.
-   **mma\_tiler\_mn** (_Tuple__\[__int__,_ _int__\]_) – The shape (M, N, K) of the MMA tiler.
-   **a\_source** ([_cutlass.cute.nvgpu.tcgen05.OperandSource_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.OperandSource")) – The source of operand A (SMEM by default or TMEM).

Returns:

A tiled MMA atom.

Return type:

[cute.TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")

Raises:

**TypeError** – If the data type is not supported.

_class_ cutlass.utils.ClcDynamicPersistentTileSchedulerParams(

_problem\_shape\_ntile\_mnl: cutlass.cute.typing.Shape_,

_cluster\_shape\_mnk: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "Link to this definition")

Bases: `object`

A class to represent parameters for a dynamic persistent tile scheduler.

This class is designed to manage and compute the layout of clusters and tiles in a batched gemm problem.

Variables:

**cluster\_shape\_mn** – Shape of the cluster in (m, n) dimensions (K dimension cta count must be 1).

\_\_init\_\_(

_problem\_shape\_ntile\_mnl: cutlass.cute.typing.Shape_,

_cluster\_shape\_mnk: cutlass.cute.typing.Shape_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams.__init__ "Link to this definition")

Initializes the ClcDynamicPersistentTileSchedulerParams with the given parameters.

Parameters:

-   **problem\_shape\_ntile\_mnl** (_cute.Shape_) – The shape of the problem in terms of number of CTA (Cooperative Thread Array) in (m, n, l) dimensions.
-   **cluster\_shape\_mnk** (_cute.Shape_) – The shape of the cluster in (m, n) dimensions.

Raises:

**ValueError** – If cluster\_shape\_k is not 1.

get\_grid\_shape(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams.get_grid_shape "Link to this definition")

Computes the grid shape based on the problem shape and cluster shape.

Returns:

the grid is the CTA numbers that has aligned with cluster shape.

_class_ cutlass.utils.ClcDynamicPersistentTileScheduler(

_params: [ClcDynamicPersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "cutlass.utils.dynamic_persistent_tile_scheduler.ClcDynamicPersistentTileSchedulerParams")_,

_cta\_id\_in\_cluster: cutlass.cute.typing.Coord_,

_num\_tiles\_executed: cutlass.cutlass\_dsl.Int32_,

_clc\_response\_ptr: cutlass.cute.typing.Pointer_,

_block\_idx: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler "Link to this definition")

Bases: `object`

A scheduler for dynamic persistent tile execution in CUTLASS/CuTe kernels.

Variables:

-   **params** – Tile schedule related params, including cluster shape.
-   **cta\_id\_in\_cluster** – ID of the CTA within its cluster
-   **\_num\_tiles\_executed** – Counter for executed tiles

\_\_init\_\_(

_params: [ClcDynamicPersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "cutlass.utils.dynamic_persistent_tile_scheduler.ClcDynamicPersistentTileSchedulerParams")_,

_cta\_id\_in\_cluster: cutlass.cute.typing.Coord_,

_num\_tiles\_executed: cutlass.cutlass\_dsl.Int32_,

_clc\_response\_ptr: cutlass.cute.typing.Pointer_,

_block\_idx: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.__init__ "Link to this definition")

Initializes the ClcDynamicPersistentTileScheduler with the given parameters.

Parameters:

-   **params** ([_ClcDynamicPersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "cutlass.utils.ClcDynamicPersistentTileSchedulerParams")) – Tile schedule related params, including cluster shape.
-   **cta\_id\_in\_cluster** (_cute.Coord_) – ID of the CTA within its cluster.
-   **num\_tiles\_executed** (_Int32_) – Counter for executed tiles.
-   **clc\_response\_ptr** (_cute.Pointer_) – Pointer of the clc rsponse.
-   **block\_idx** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The block index.

create(

_params: [ClcDynamicPersistentTileSchedulerParams](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "cutlass.utils.dynamic_persistent_tile_scheduler.ClcDynamicPersistentTileSchedulerParams")_,

_block\_idx: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

_grid\_dim: Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\]_,

_clc\_response\_ptr: cutlass.cute.typing.Pointer_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.create "Link to this definition")

Initialize the dynamic persistent tile scheduler.

Parameters:

-   **params** ([_ClcDynamicPersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "cutlass.utils.ClcDynamicPersistentTileSchedulerParams")) – Parameters for the persistent tile scheduler.
-   **block\_idx** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The 3d block index in the format (bidx, bidy, bidz).
-   **grid\_dim** (_Tuple__\[__Integer__,_ _Integer__,_ _Integer__\]_) – The 3d grid dimensions for kernel launch.

Returns:

A ClcDynamicPersistentTileScheduler object.

Return type:

[ClcDynamicPersistentTileScheduler](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler "cutlass.utils.ClcDynamicPersistentTileScheduler")

get\_grid\_shape(

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer, cutlass.cutlass\_dsl.Integer\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.get_grid_shape "Link to this definition")

Calculates the grid shape to be launched on GPU using problem shape, threadblock shape, and active cluster size.

Parameters:

**params** ([_ClcDynamicPersistentTileSchedulerParams_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileSchedulerParams "cutlass.utils.ClcDynamicPersistentTileSchedulerParams")) – Parameters for grid shape calculation.

Returns:

The calculated 3d grid shape.

Return type:

Tuple\[Integer, Integer, Integer\]

work\_tile\_info\_from\_clc\_response(

_result\_addr: cutlass.cute.typing.Pointer_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.work_tile_info_from_clc_response "Link to this definition")

Simulates parsing CLC response data in Python. result\_addr: 16-byte response data (simulating shared memory access)

get\_current\_work(

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.get_current_work "Link to this definition")

initial\_work\_tile\_info(

_\*_,

_loc\=None_,

_ip\=None_,

) → [WorkTileInfo](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.WorkTileInfo "cutlass.utils.static_persistent_tile_scheduler.WorkTileInfo")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.initial_work_tile_info "Link to this definition")

advance\_to\_next\_work(

_mbarrier\_addr_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.advance_to_next_work "Link to this definition")

_property_ num\_tiles\_executed_: cutlass.cutlass\_dsl.Int32_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.ClcDynamicPersistentTileScheduler.num_tiles_executed "Link to this definition")

cutlass.utils.print\_latex(

_x: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_\*_,

_color: ~typing.Callable \= <function tikz\_color\_bwx8>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.print_latex "Link to this definition")

Prints a layout. :param x: A layout :type x: Union\[Layout, ComposedLayout\] :param color: A function that returns TiKZ colors :type color: Callable

cutlass.utils.print\_latex\_tv(

_layout\_tv: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_tile\_mn: cutlass.cute.typing.IntTuple | cutlass.cute.typing.Layout_,

_\*_,

_color: ~typing.Callable \= <function tikz\_color\_tv>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.print_latex_tv "Link to this definition")

Prints a tv layout for a tile M N. Everything must be static. :param layout\_tv: A static thread value layout :type layout\_tv: Union\[Layout, ComposedLayout\] :param tile\_mn: A static M N tile :type tile\_mn: Union\[IntTuple, Layout\] :param color: A function that returns TiKZ colors :type color: Callable

cutlass.utils.is\_fp8\_dtype(_dtype: Type\[cutlass.cute.typing.Numeric\]_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.is_fp8_dtype "Link to this definition")

Check if dtype is a float8 type that doesn’t support dlpack. params dtype: The cutlass numeric type to check type dtype: Type\[cutlass.Numeric\] return: True if the dtype is Float8E5M2 or Float8E4M3FN, False otherwise

cutlass.utils.create\_cute\_tensor\_for\_fp8(

_storage\_tensor_,

_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_leading\_dim: int_,

_source\_f32\_tensor\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.create_cute_tensor_for_fp8 "Link to this definition")

Create cute tensor, handling float8 types that don’t support dlpack.

For float8 types, the storage\_tensor should be uint8 (for DLPack compatibility). The source\_f32\_tensor provides the actual float32 values to convert to fp8.

params storage\_tensor: Tensor for DLPack (uint8 for fp8, otherwise the actual dtype) params dtype: Target cutlass dtype params leading\_dim: Leading dimension for dynamic layout paramas source\_f32\_tensor: Float32 source data for fp8 conversion (required for fp8) return: A cute tensor with the appropriate dtype and layout

# Utilities for SM90[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#module-cutlass.utils.sm90 "Link to this heading")

cutlass.utils.sm90.get\_smem\_store\_op(

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_elem\_ty\_acc: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#cutlass.utils.sm90.get_smem_store_op "Link to this definition")

Selects the largest vectorized smem store atom available subject to constraint of gmem layout.

## Parameters:[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#parameters "Link to this heading")

layout\_dLayoutEnum

The layout enum of the output tensor D.

elem\_ty\_dType\[Numeric\]

The element type for output tensor D.

elem\_ty\_accType\[Numeric\]

The element type for accumulator.

## Returns:[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#returns "Link to this heading")

Either SmemStoreMatrix or SimtSyncCopy, based on the input parameters.

cutlass.utils.sm90.make\_smem\_layout\_a(

_a\_layout: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_mma\_tiler\_mnk: cutlass.cute.typing.Tile_,

_a\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_stages: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#cutlass.utils.sm90.make_smem_layout_a "Link to this definition")

This function helps with:

1.  Get the partitioned shape of the A tensor based on the MMA tiler.
2.  Select the heuristic SMEM layout atom based on the A tensor’s majorness, the data type, and the major mode size.
3.  cute.Tile the SMEM layout atom to the MMA tile shape.
4.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **a\_layout** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum for tensor A
-   **mma\_tiler\_mnk** (_cute.cute.Tile_) – The MMA tile shape
-   **a\_dtype** (_Type__\[__Numeric__\]_) – The element type for tensor A
-   **num\_stages** (_int_) – The number of pipeline stages for tensor A

Returns:

SMEM layout for tensor A

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.sm90.make\_smem\_layout\_b(

_b\_layout: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_mma\_tiler\_mnk: cutlass.cute.typing.Tile_,

_b\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_stages: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#cutlass.utils.sm90.make_smem_layout_b "Link to this definition")

This function helps with:

1.  Get the partitioned shape of the B tensor based on the MMA tiler.
2.  Select the heuristic SMEM layout atom based on the B tensor’s majorness, the data type, and the major mode size.
3.  cute.Tile the SMEM layout atom to the MMA tile shape.
4.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **b\_layout** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum for tensor B
-   **mma\_tiler\_mnk** (_cute.cute.Tile_) – The MMA tile shape
-   **b\_dtype** (_Type__\[__Numeric__\]_) – The element type for tensor B
-   **num\_stages** (_int_) – The number of pipeline stages for tensor B

Returns:

SMEM layout for tensor B

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.sm90.make\_smem\_layout\_epi(

_epi\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_epi\_layout: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_epi\_tile: cutlass.cute.typing.Tile_,

_epi\_stage: int_,

_smem\_trg\_shape: cutlass.cute.typing.Layout | None \= None_,

_smem\_order: tuple | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#cutlass.utils.sm90.make_smem_layout_epi "Link to this definition")

This function helps:

1.  Select the heuristic SMEM layout atom based on the epilog tile shape, the epilog tensor’s majorness, and the element type.
2.  cute.Tile the SMEM layout atom to the epilog tile shape.
3.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **epi\_dtype** (_Type__\[__Numeric__\]_) – The element type for the epilog tensor.
-   **epi\_layout** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum for the epilog tensor.
-   **epi\_tile** (_cute.cute.Tile_) – The epilogue tile shape.
-   **epi\_stage** (_int_) – The stage of the epilog tensor.
-   **smem\_trg\_shape** (_cute.Layout_ _|_ _None_) – Target shape for SMEM layout (optional).
-   **smem\_order** (_tuple_ _|_ _None_) – Order for SMEM layout (optional).

Returns:

SMEM layout for epilog tensors (usually C & D which are processed in the epilog)

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.sm90.compute\_tile\_shape\_or\_override(

_tile\_shape\_mnk: tuple\[int, int, int\]_,

_element\_type: type\[cutlass.cutlass\_dsl.Numeric\]_,

_is\_cooperative: bool \= False_,

_epi\_tile\_override: tuple\[int, int\] | None \= None_,

) → tuple\[int, int\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm90.html#cutlass.utils.sm90.compute_tile_shape_or_override "Link to this definition")

Compute the epilogue tile shape or use override if provided.

Parameters:

-   **tile\_shape\_mnk** (_Tuple__\[__int__,_ _int__,_ _int__\]_) – CTA tile shape (M,N,K)
-   **element\_type** (_type__\[__Numeric__\]_) – Data type of elements
-   **is\_cooperative** (_bool_) – Whether to use cooperative approach
-   **epi\_tile\_override** (_Tuple__\[__int__,_ _int__\] or_ _None_) – Optional override for epilogue tile shape

Returns:

Computed epilogue tile shape

Return type:

Tuple\[int, int\]

# Utilities for SM100[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#module-cutlass.utils.sm100 "Link to this heading")

cutlass.utils.sm100.compute\_epilogue\_tile\_shape(

_cta\_tile\_shape: cutlass.cute.typing.Shape_,

_use\_2cta\_instrs: bool_,

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_\*_,

_layout\_c: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum") | None \= None_,

_elem\_ty\_c: Type\[cutlass.cutlass\_dsl.Numeric\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tile[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.compute_epilogue_tile_shape "Link to this definition")

Attempts to compute a reasonable epilogue tile based on block tile shape or allows the user to provide one.

Parameters:

-   **cta\_tile\_shape** (_cute.Shape_) – A tuple or list representing the dimensions of the CTA tile, where cta\_tile\_shape\[0\] corresponds to the height (M) and cta\_tile\_shape\[1\] corresponds to the width (N) of the tile.
-   **use\_2cta\_instrs** (_bool_) – A flag indicating whether the configuration is for a 2SM setup.
-   **layout\_d** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum of the output tensor D.
-   **elem\_ty\_d** (_Type__\[__Numeric__\]_) – The element type of output tensor D.
-   **layout\_c** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")_,_ _optional_) – The layout enum of the input tensor C. Defaults to None.
-   **elem\_ty\_c** (_Union__\[__Type__\[__Numeric__\]__,_ _None__\]__,_ _optional_) – The element type for input tensor C. Defaults to None.

Returns:

Returns epilog tiler, which is used in subsequent epilog partitions.

Return type:

cute.Tile

Raises:

**ValueError** – If the computed tile cute.size does not meet minimum requirements based on CTA dimensions.

cutlass.utils.sm100.get\_smem\_store\_op(

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_elem\_ty\_acc: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_tiled\_tmem\_load: [TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.get_smem_store_op "Link to this definition")

Selects the largest vectorized smem store atom available subject to constraint of gmem layout and chosen TMEM\_LOAD’s thread-value ownership.

Parameters:

-   **layout\_d** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum of the output tensor D.
-   **elem\_ty\_d** (_Type__\[__Numeric__\]_) – The element type for output tensor D.
-   **elem\_ty\_acc** (_Type__\[__Numeric__\]_) – The element type for accumulator.
-   **tiled\_tmem\_load** ([_cute.TiledCopy_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.TiledCopy")) – An instance of TiledCopy that represents the tmem load operation.

Returns:

Either SmemStoreMatrix or SimtSyncCopy, based on the input parameters.

Return type:

[cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")

cutlass.utils.sm100.get\_tmem\_load\_op(

_cta\_tile\_shape: cutlass.cute.typing.Shape_,

_layout\_d: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_elem\_ty\_d: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_elem\_ty\_acc: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_epi\_tile: cutlass.cute.typing.Tile_,

_use\_2cta\_instrs: bool_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.get_tmem_load_op "Link to this definition")

Finds a performant TMEM\_LOAD copy op for the selected epilogue tile (epi\_tile), element types, and tcgen05.mma instruction used.

Parameters:

-   **cta\_tile\_shape** (_cute.Shape_) – A tuple or list representing the dimensions of the CTA tile.
-   **layout\_d** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum of the output tensor D.
-   **elem\_ty\_d** (_Type__\[__Numeric__\]_) – The element type for output tensor D.
-   **elem\_ty\_acc** (_Type__\[__Numeric__\]_) – The element type for accumulation.
-   **epi\_tile** (_cute.Tile_) – The epilogue tile configuration.
-   **use\_2cta\_instrs** (_bool_) – A flag indicating whether the configuration is for 2 SMs.

Returns:

An instance of Sm100TmemLoad with the computed configuration.

Return type:

[cute.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.CopyAtom")

Raises:

**ValueError** – If the function cannot handle the given combination of accumulation and dimension types, or if it cannot determine the appropriate configuration based on the input parameters.

cutlass.utils.sm100.make\_smem\_layout\_a(

_tiled\_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_mma\_tiler\_mnk: cutlass.cute.typing.Tile_,

_a\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_stages: int_,

_\*_,

_is\_k\_major\=None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.make_smem_layout_a "Link to this definition")

This function helps with:

1.  Get the partitioned shape of the A tensor based on the tiled\_mma & MMA tiler.
2.  Select the heuristic SMEM layout atom based on the A tensor’s majorness, the data type, and the major mode size.
3.  cute.Tile the SMEM layout atom to the MMA tile shape.
4.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **tiled\_mma** ([_cute.TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – The tiled MMA used to partition tensor A
-   **mma\_tiler\_mnk** (_cute.cute.Tile_) – The MMA tile shape
-   **a\_dtype** (_Type__\[__Numeric__\]_) – The element type for tensor A
-   **num\_stages** (_int_) – The number of pipeline stages for tensor A

Returns:

SMEM layout for tensor A

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.sm100.make\_smem\_layout\_b(

_tiled\_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_mma\_tiler\_mnk: cutlass.cute.typing.Tile_,

_b\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_num\_stages: int_,

_\*_,

_is\_k\_major\=None_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.make_smem_layout_b "Link to this definition")

This function helps:

1.  Get the partitioned shape of the B tensor based on the tiled\_mma & MMA tiler.
2.  Select the heuristic SMEM layout atom based on the B tensor’s majorness, the data type, and the major mode size.
3.  cute.Tile the SMEM layout atom to the MMA tile shape.
4.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **tiled\_mma** ([_cute.TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")) – The tiled MMA which is used to partition the B tensor.
-   **mma\_tiler\_mnk** (_cute.cute.Tile_) – The MMA tile shape.
-   **b\_dtype** (_Type__\[__Numeric__\]_) – The element type for the B tensor.
-   **num\_stages** (_int_) – The stage of the B tensor.

Returns:

SMEM layout for the B tensor.

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.sm100.make\_smem\_layout\_epi(

_epi\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_epi\_layout: [LayoutEnum](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.layout.LayoutEnum")_,

_epi\_tile: cutlass.cute.typing.Tile_,

_epi\_stage: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.make_smem_layout_epi "Link to this definition")

This function helps:

1.  Select the heuristic SMEM layout atom based on the epilog tile shape, the epilog tensor’s majorness, and the element type.
2.  cute.Tile the SMEM layout atom to the epilog tile shape.
3.  Stage the SMEM layout based on the number of stages.

Parameters:

-   **epi\_dtype** (_Type__\[__Numeric__\]_) – The element type for the epilog tensor.
-   **epi\_layout** ([_LayoutEnum_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils.html#cutlass.utils.LayoutEnum "cutlass.utils.LayoutEnum")) – The layout enum for the epilog tensor.
-   **epi\_tile** (_cute.cute.Tile_) – The epilogue tile shape.
-   **epi\_stage** (_int_) – The stage of the epilog tensor.

Returns:

SMEM layout for epilog tensors (usually C & D which are processed in the epilog)

Return type:

Union\[cute.Layout, cute.ComposedLayout\]

cutlass.utils.sm100.make\_trivial\_tiled\_mma(

_ab\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_a\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_acc\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_mma\_tiler\_mn: Tuple\[int, int\]_,

_a\_source: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource") \= cutlass.\_mlir.dialects.cute.MmaFragKind.smem\_desc_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.make_trivial_tiled_mma "Link to this definition")

Make a tiled MMA atom with given data type, leading dimension, cta group and mma tile shape. By default, the MMA atom is created with SMEM operand source for A.

Parameters:

-   **ab\_dtype** (_type__\[__Numeric__\]_) – Data type of operands A and B.
-   **a\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand A (1 for K, 0 for M/N).
-   **b\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand B (1 for K, 0 for M/N).
-   **acc\_dtype** (_type__\[__Numeric__\]_) – Data type of the accumulator.
-   **cta\_group** ([_tcgen05.CtaGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.CtaGroup")) – The CTA group to use.
-   **mma\_tiler\_mn** (_Tuple__\[__int__,_ _int__\]_) – The shape (M, N, K) of the MMA tiler.
-   **a\_source** ([_cutlass.cute.nvgpu.tcgen05.OperandSource_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.OperandSource")) – The source of operand A (SMEM by default or TMEM).

Returns:

A tiled MMA atom.

Return type:

[cute.TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")

Raises:

**TypeError** – If the data type is not supported.

cutlass.utils.sm100.make\_blockscaled\_trivial\_tiled\_mma(

_ab\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_a\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_leading\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_sf\_dtype: Type\[cutlass.cutlass\_dsl.Numeric\]_,

_sf\_vec\_size: int_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_mma\_tiler\_mn: Tuple\[int, int\]_,

_a\_source: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource") \= cutlass.\_mlir.dialects.cute.MmaFragKind.smem\_desc_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.make_blockscaled_trivial_tiled_mma "Link to this definition")

Make a BlockScaled tiled MMA atom with given data type, leading dimension, cta group and mma tile shape. By default, the MMA atom is created with SMEM operand source for A.

Parameters:

-   **ab\_dtype** (_type__\[__Numeric__\]_) – Data type of operands A and B.
-   **a\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand A (1 for K, 0 for M/N).
-   **b\_leading\_mode** ([_tcgen05.OperandMajorMode_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.OperandMajorMode")) – Leading dimension of operand B (1 for K, 0 for M/N).
-   **sf\_dtype** (_type__\[__Numeric__\]_) – Data type of the Scale Factor.
-   **sf\_vec\_size** (_int_) – The vector size of the Scale Factor.
-   **cta\_group** ([_tcgen05.CtaGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.CtaGroup")) – The CTA group to use.
-   **mma\_tiler\_mn** (_Tuple__\[__int__,_ _int__\]_) – The shape (M, N, K) of the MMA tiler.
-   **a\_source** ([_cutlass.cute.nvgpu.tcgen05.OperandSource_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.OperandSource")) – The source of operand A (SMEM by default or TMEM).

Returns:

A tiled MMA atom.

Return type:

[cute.TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.TiledMma")

Raises:

**TypeError** – If the data type is not supported.

cutlass.utils.sm100.cluster\_shape\_to\_tma\_atom\_A(

_cluster\_shape\_mnk: cutlass.cute.typing.Shape_,

_atom\_thr\_id: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SMulticastOp") | [CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SOp")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.cluster_shape_to_tma_atom_A "Link to this definition")

Select the appropriate TMA copy atom for A based on the number of SMs and the multicast flag.

Parameters:

-   **cluster\_shape\_mnk** (_cute.Shape_) – The shape of the cluster
-   **atom\_thr\_id** (_cute.Layout_) – The thread ID of the atom

Returns:

The appropriate TMA copy atom kind

Return type:

[cpasync.CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp") or [cpasync.CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp")

Raises:

-   **ValueError** – If the atom\_sm\_cnt is invalid
-   **ValueError** – If the cluster shape is not divisible by the atom SM count

cutlass.utils.sm100.cluster\_shape\_to\_tma\_atom\_B(

_cluster\_shape\_mnk: cutlass.cute.typing.Shape_,

_atom\_thr\_id: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SMulticastOp") | [CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SOp")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.cluster_shape_to_tma_atom_B "Link to this definition")

Select the appropriate TMA copy atom for Bbased on the number of SMs and the multicast flag.

Parameters:

-   **cluster\_shape\_mnk** (_cute.Shape_) – The shape of the cluster
-   **atom\_thr\_id** (_cute.Layout_) – The thread ID of the atom

Returns:

The appropriate TMA copy atom kind

Return type:

[cpasync.CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp") or [cpasync.CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp")

Raises:

-   **ValueError** – If the atom\_sm\_cnt is invalid
-   **ValueError** – If the cluster shape is not divisible by the atom SM count

cutlass.utils.sm100.cluster\_shape\_to\_tma\_atom\_SFB(

_cluster\_shape\_mnk: cutlass.cute.typing.Shape_,

_atom\_thr\_id: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SMulticastOp") | [CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SOp")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.cluster_shape_to_tma_atom_SFB "Link to this definition")

Select the appropriate TMA copy atom for SFB based on the number of SMs and the multicast flag.

Parameters:

-   **cluster\_shape\_mnk** (_cute.Shape_) – The shape of the cluster
-   **atom\_thr\_id** (_cute.Layout_) – The thread ID of the atom

Returns:

The appropriate TMA copy atom kind

Return type:

[cpasync.CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp") or [cpasync.CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp")

Raises:

-   **ValueError** – If the atom\_sm\_cnt is invalid
-   **ValueError** – If the cluster shape is not divisible by the atom SM count

cutlass.utils.sm100.get\_permutation\_mnk(

_tile\_shape\_mnk: cutlass.cute.typing.Shape_,

_sf\_vec\_size: int_,

_use\_mxf8f6f4: bool_,

_\*_,

_loc\=None_,

_ip\=None_,

) → Tuple\[int, int, int\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/utils_sm100.html#cutlass.utils.sm100.get_permutation_mnk "Link to this definition")

Get the permutation of M, N, K for the tiled MMA.

Parameters:

-   **tile\_shape\_mnk** (_cute.Shape_) – The shape of the tile
-   **sf\_vec\_size** (_int_) – The vector size of the Scale Factor.
-   **use\_mxf8f6f4** (_bool_) – Whether to use MXF8F6F4 or MXF4NVF4.

Returns:

The permutation of M, N, K

Return type:

Tuple\[int, int, int\]

Raises:

**ValueError** – If the tile shape is not divisible by the sf\_vec\_size

cutlass.utils.sm100.get\_num\_tmem\_alloc\_cols(

_tmem\_tensors: cutlass.cute.typing.Tensor | List\[cutlass.cute.typing.Tensor\]_,

_rounding\=True_,

_\*_,

_loc\=None_,

_ip\=None_,

) → int