
# cutlass.cute.nvgpu[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu.html#cutlass-cute-nvgpu "Link to this heading")

The `cute.nvgpu` module contains MMA and Copy Operations as well as Operation-specific helper functions. The arch-agnostic Operations are exposed at the top-level while arch-specific Operations are grouped into submodules like `tcgen05`.

# Common[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#module-cutlass.cute.nvgpu "Link to this heading")

_class_ cutlass.cute.nvgpu.OpError(_\*args: Any_, _\*\*kwargs: Any_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.OpError "Link to this definition")

Bases: `DSLBaseError`

An exception class for Op construction errors.

cutlass.cute.nvgpu.normalize\_field\_to\_ir\_name(_field_, _admissible\_fields_) → str[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.normalize_field_to_ir_name "Link to this definition")

Normalize a field specifier to its IR logical field name.

Accepted inputs:

-   Enum value present in admissible\_fields (must expose \_to\_ir\_field\_name()).
-   Exact string IR name (e.g., “accum\_c”, “neg\_a”, “sf\_a”).

Any other form is rejected.

_class_ cutlass.cute.nvgpu.MmaUniversalOp(_abacc\_dtype: Type\[cutlass.cute.typing.Numeric\]_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.MmaUniversalOp "Link to this definition")

Bases: `MmaOp`

The universal MMA Operation.

This Operation currently expects the A/B operands as well as the accumulator to share the same data types.

Parameters:

**abacc\_dtype** (_Type__\[__Numeric__\]_) – The data type for the A/B operands and the accumulator

abacc\_dtype_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.MmaUniversalOp.abacc_dtype "Link to this definition")

_class_ cutlass.cute.nvgpu.MmaUniversalTrait(_value: cutlass.\_mlir.ir.Value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.MmaUniversalTrait "Link to this definition")

Bases: `Trait`

_class_ cutlass.cute.nvgpu.CopyUniversalOp[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.CopyUniversalOp "Link to this definition")

Bases: `CopyOp`

The universal Copy Operation.

When creating a Copy Atom out of this operation, the expected usage pattern is

op \= cute.nvgpu.CopyUniversalOp()
atom \= cute.make\_copy\_atom(
    op,
    tensor\_dtype,
    num\_bits\_per\_copy\=64,
    l1c\_evict\_priority\=cute.nvgpu.CacheEvictionPriority.EVICT\_NORMAL
)

Copy to clipboard

-   `tensor_dtype` is the data type used to build the reference TV Layout (either the source or the destination TV Layout) in unit of tensor elements and is used for partitioning by `TiledCopy` for example
-   `num_bits_per_copy` is a kw argument specifying the number of bits to copy per Atom execution. This can be larger than the width of the above data type. When not provided, the compiler will do a best effort at auto-vectorizing.
-   `l1c_evict_priority` is a kw argument specifying the L1 cache eviction priority hint for the copy operation. Defaults to `EVICT_NORMAL` if not provided.
-   `invariant` is a kw argument specifying whether the load is invariant (read-only data that never changes). This enables compiler optimizations like instruction reordering. Defaults to `False` if not provided.

_class_ cutlass.cute.nvgpu.CopyUniversalTrait(_value: cutlass.\_mlir.ir.Value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.CopyUniversalTrait "Link to this definition")

Bases: `Trait`

_class_ cutlass.cute.nvgpu.MemoryOrder(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.MemoryOrder "Link to this definition")

Bases: `Enum`

An enumeration.

_class_ cutlass.cute.nvgpu.MemoryScope(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.MemoryScope "Link to this definition")

Bases: `Enum`

An enumeration.

_class_ cutlass.cute.nvgpu.CacheEvictionPriority(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.CacheEvictionPriority "Link to this definition")

Bases: `Enum`

An enumeration.

cutlass.cute.nvgpu.make\_tiled\_tma\_atom\_A(

_op: [CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SOp") | [CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SMulticastOp")_,

_gmem\_tensor: cutlass.cute.typing.Tensor_,

_smem\_layout: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_mma\_tiler\_mnk: cutlass.cute.typing.Shape_,

_tiled\_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_cluster\_shape\_vmnk: cutlass.cute.typing.Shape | None \= None_,

_\*_,

_internal\_type: Type\[cutlass.cute.typing.Numeric\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → Tuple\[[CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom"), cutlass.cute.typing.Tensor\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.make_tiled_tma_atom_A "Link to this definition")

Makes a TMA Copy atom mapping to `.tile` mode for `cp.async.bulk.tensor` PTX operation accounting for the MK projections of the TiledMMA for A tensor loads.

Given

-   a GMEM tensor
-   a SMEM layout
-   a MMA Tiler
-   a TiledMma
-   a Cluster-level shape

this function figures out the bulk tensor asynchronous copy instruction to use with the maximum “TMA vector length” to copy tiles of the GMEM tensor to an SMEM buffer with the provided layout and consistent with the provided Tiler & tiled\_mma (considering the M-mode & K-mode). The Cluster-level shape is used to determine the multicast factor across the N-mode for A tensor loads.

This function returns two results:

1.  the Copy Atom
2.  the so-called TMA tensor used to map logical coordinates of the GMEM tensor to coordinates that the TMA unit can consume. TMA tensors have so-called basis stride elements so that the associated layout can output coordinates. Otherwise, TMA tensors can be partitioned similarly to any other CuTe tensors using the algebra.

Parameters:

-   **op** (_Union__\[_[_CopyBulkTensorTileG2SOp_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp")_,_ [_CopyBulkTensorTileG2SMulticastOp_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp")_\]_) – The Copy Operation to construct an Atom for
-   **gmem\_tensor** (_Tensor_) – The GMEM tensor to be loaded by this copy atom
-   **smem\_layout** (_Union__\[__Layout__,_ _ComposedLayout__\]_) – Shared memory layout to load the tensor into (PDSL)
-   **mma\_tiler\_mnk** (_Shape_) – The MMA Tiler shape (TILE\_M, TILE\_N, TILE\_K) in MNK dimensions
-   **tiled\_mma** ([_atom.TiledMma_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")) – The TiledMMA that will consume the load as operands
-   **cluster\_shape\_vmnk** (_Shape_) – The Cluster-level shape in VMNK dimensions
-   **internal\_type** (_Type__\[__Numeric__\]_) – An optional parameter for the internal data type to when element type does not match the copy type

Returns:

A copy atom for this operation and the associated TMA coord tensor

Return type:

Tuple\[[atom.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom"), Tensor\]

cutlass.cute.nvgpu.make\_tiled\_tma\_atom\_B(

_op: [CopyBulkTensorTileG2SOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SOp") | [CopyBulkTensorTileG2SMulticastOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.copy.CopyBulkTensorTileG2SMulticastOp")_,

_gmem\_tensor: cutlass.cute.typing.Tensor_,

_smem\_layout: cutlass.cute.typing.Layout | cutlass.cute.typing.ComposedLayout_,

_mma\_tiler\_mnk: cutlass.cute.typing.Shape_,

_tiled\_mma: [TiledMma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledMma "cutlass.cute.atom.TiledMma")_,

_cluster\_shape\_vmnk: cutlass.cute.typing.Shape | None \= None_,

_\*_,

_internal\_type: Type\[cutlass.cute.typing.Numeric\] | None \= None_,

_loc\=None_,

_ip\=None_,

) → Tuple\[[CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom"), cutlass.cute.typing.Tensor\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_common.html#cutlass.cute.nvgpu.make_tiled_tma_atom_B "Link to this definition")

Makes a TMA Copy atom mapping to `.tile` mode for `cp.async.bulk.tensor` PTX operation accounting for the NK projections of the TiledMMA for B tensor loads.

Given

-   a GMEM tensor
-   a SMEM layout
-   a MMA Tiler
-   a TiledMma
-   a Cluster-level shape

this function figures out the bulk tensor asynchronous copy instruction to use with the maximum “TMA vector length” to copy tiles of the GMEM tensor to an SMEM buffer with the provided layout and consistent with the provided Tiler & tiled\_mma (considering the N-mode & K-mode). The Cluster-level shape is used to determine the multicast factor across the M-mode for B tensor loads.

This function returns two results:

1.  the Copy Atom
2.  the so-called TMA tensor used to map logical coordinates of the GMEM tensor to coordinates that the TMA unit can consume. TMA tensors have so-called basis stride elements so that the associated layout can output coordinates. Otherwise, TMA tensors can be partitioned similarly to any other CuTe tensors using the algebra.

Parameters:

-   **op** (_Union__\[_[_CopyBulkTensorTileG2SOp_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SOp")_,_ [_CopyBulkTensorTileG2SMulticastOp_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_cpasync.html#cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp "cutlass.cute.nvgpu.cpasync.CopyBulkTensorTileG2SMulticastOp")_\]_) – The Copy Operation to construct an Atom for
-   **gmem\_tensor** (_Tensor_) – The GMEM tensor to be loaded by this copy atom
-   **smem\_layout** (_Union__\[__Layout__,_ _ComposedLayout__\]_) – Shared memory layout to load the tensor into (PDSL)
-   **mma\_tiler\_mnk** (_Shape_) – The MMA Tiler shape (TILE\_M, TILE\_N, TILE\_K) in MNK dimensions
-   **tiled\_mma** (_core.TiledMma_) – The TiledMMA that will consume the load as operands
-   **cluster\_shape\_vmnk** (_Shape_) – The Cluster-level shape in VMNK dimensions
-   **internal\_type** (_Type__\[__Numeric__\]_) – An optional parameter for the internal data type to when element type does not match the copy type

Returns:

A Copy Atom for this Operation and the associated TMA tensor

Return type:

Tuple\[[atom.CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom"), Tensor\]

# warp submodule[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#module-cutlass.cute.nvgpu.warp "Link to this heading")

_class_ cutlass.cute.nvgpu.warp.Field(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.Field "Link to this definition")

Bases: `Enum`

An enumeration for the fields of the MMA Atom that can be modified at runtime.

ACCUMULATE _\= 'accum\_c'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.Field.ACCUMULATE "Link to this definition")

SFA _\= 'sf\_a'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.Field.SFA "Link to this definition")

SFB _\= 'sf\_b'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.Field.SFB "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.MmaF16BF16Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_shape\_mnk: cutlass.cute.typing.Shape_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaF16BF16Op "Link to this definition")

Bases: `WarpMmaOp`

F16/BF16 warp-level MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-instructions-mma). This Operation covers the instructions using the `.f16` or `.bf16` qualifiers for the input operands.

ab\_dtype_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaF16BF16Op.ab_dtype "Link to this definition")

acc\_dtype_: Type\[cutlass.cute.typing.Numeric\]_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaF16BF16Op.acc_dtype "Link to this definition")

shape\_mnk_: cutlass.cute.typing.Shape_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaF16BF16Op.shape_mnk "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_shape\_mnk: cutlass.cute.typing.Shape_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaF16BF16Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.MmaMXF4Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_sf\_type: Type\[cutlass.cute.typing.Numeric\]_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaMXF4Op "Link to this definition")

Bases: `MmaSM120BlockScaledOp`

MXF4 warp-level MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-instructions-mma). This Operation covers the instructions using the `.e2m1` qualifiers for the input operands. .kind = {.kind::mxf4}; .scale\_vec\_size = {.scale\_vec::2X}; .stype = {.ue8m0};

descriptive\_name _\= 'warp-level MXF4 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaMXF4Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_sf\_type: Type\[cutlass.cute.typing.Numeric\]_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaMXF4Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.MmaMXF4NVF4Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_sf\_type: Type\[cutlass.cute.typing.Numeric\]_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaMXF4NVF4Op "Link to this definition")

Bases: `MmaSM120BlockScaledOp`

MXF4NVF4 warp-level MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-instructions-mma). This Operation covers the instructions using the `.e2m1` qualifiers for the input operands. .kind = {.kind::mxf4nvf4}; .scale\_vec\_size = {.scale\_vec::2X, .scale\_vec::4X}; .stype = {.ue8m0, .ue4m3};

descriptive\_name _\= 'warp-level MXF4NVF4 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaMXF4NVF4Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_sf\_type: Type\[cutlass.cute.typing.Numeric\]_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.MmaMXF4NVF4Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.LdMatrix8x8x16bOp(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.LdMatrix8x8x16bOp "Link to this definition")

Bases: `BaseOp`

8x8 `ldmatrix` Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-load-instruction-ldmatrix). This operation corresponds to the `.m8n8` qualifier.

\_\_init\_\_(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.LdMatrix8x8x16bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.LdMatrix16x8x8bOp(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.LdMatrix16x8x8bOp "Link to this definition")

Bases: `BaseOp`

16x8 8b `ldmatrix` Operation with transpose

There is no direct PTX correspondance to this Op. This actually lowers to ldmatrix with the `.m16n16` qualifier and additional address and value permutations to match stmatrix.m16n8.trans. Useful for vectorizing with Ampere-style 8x8 matrix thread-value layouts

\_\_init\_\_(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.LdMatrix16x8x8bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.LdMatrix16x16x8bOp(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.LdMatrix16x16x8bOp "Link to this definition")

Bases: `BaseOp`

16x16 `ldmatrix` Operation with transpose and optional unpacking to 8b container. Packed source container is 16x4b elements with 64b padding or 16x6b elements with 32b padding (total 128b per 16 elements)

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-load-instruction-ldmatrix). This operation corresponds to the `.m16n16` and the `.b4x16_p64`,\`\`.b6x16\_p32\`\`,\`\`.b8\`\` qualifiers.

\_\_init\_\_(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.LdMatrix16x16x8bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.StMatrix8x8x16bOp(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.StMatrix8x8x16bOp "Link to this definition")

Bases: `BaseOp`

8x8 `stmatrix` Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-instructions-stmatrix). This operation corresponds to the `m8n8` qualifier.

\_\_init\_\_(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.StMatrix8x8x16bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warp.StMatrix16x8x8bOp(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warp.html#cutlass.cute.nvgpu.warp.StMatrix16x8x8bOp "Link to this definition")

Bases: `BaseOp`

16x8 `stmatrix` Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#warp-level-matrix-instructions-stmatrix). This operation corresponds to the `m16n8` qualifier.

\_\_init\_\_(

_transpose: bool \= False_,

_num\_matrices: int \= 1_,

_unpack\_bits: cutlass.cute.typing.Optional.<class 'int'> | None \= None_,

) → None

# warpgroup submodule[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#module-cutlass.cute.nvgpu.warpgroup "Link to this heading")

_class_ cutlass.cute.nvgpu.warpgroup.OperandMajorMode(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "Link to this definition")

Bases: `Enum`

An enumeration for the majorness of the input operands of the MMA.

_class_ cutlass.cute.nvgpu.warpgroup.OperandSource(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "Link to this definition")

Bases: `Enum`

An enumeration for the source memory location of the A input operand of the MMA.

_class_ cutlass.cute.nvgpu.warpgroup.Field(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.Field "Link to this definition")

Bases: `Enum`

An enumeration for the fields of the MMA Atom that can be modified at runtime.

ACCUMULATE _\= 'accum\_c'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.Field.ACCUMULATE "Link to this definition")

_class_ cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op "Link to this definition")

Bases: `MmaOp`

F16/BF16 warpgroup MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-warpgroup-level-matrix-instructions-wgmma-mma). This Operation covers the instructions using the `.f16` or `.bf16` qualifiers for the input operands.

descriptive\_name _\= 'warpgroup F16/BF16 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warpgroup.MmaF8Op(

_a\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_b\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF8Op "Link to this definition")

Bases: `MmaOp`

F8 warpgroup MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-warpgroup-level-matrix-instructions-wgmma-mma). This Operation covers the instructions using the `.e4m3` or `.e5m2` qualifiers for the input operands.

descriptive\_name _\= 'warpgroup F8 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF8Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_a\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_b\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF8Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind "Link to this definition")

Bases: `Enum`

Enum class for the kinds of SMEM layout atoms for SM90.

Given a swizzle kind, an SMEM layout atom is the compact layout of smallest size that can be used to construct an SMEM layout using blocked product for operand A or B such that the resulting layout is legal for both TMA and UMMA.

Note that there are other ways of creating legal layouts for operand A and B.

MN\_INTER _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_INTER "Link to this definition")

MN\_SW32 _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_SW32 "Link to this definition")

MN\_SW64 _\= 3_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_SW64 "Link to this definition")

MN\_SW128 _\= 4_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_SW128 "Link to this definition")

K\_INTER _\= 5_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_INTER "Link to this definition")

K\_SW32 _\= 6_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_SW32 "Link to this definition")

K\_SW64 _\= 7_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_SW64 "Link to this definition")

K\_SW128 _\= 8_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_SW128 "Link to this definition")

cutlass.cute.nvgpu.warpgroup.make\_smem\_layout\_atom(

_kind: [SmemLayoutAtomKind](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind "cutlass.cute.nvgpu.warpgroup.mma.SmemLayoutAtomKind")_,

_element\_type: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.make_smem_layout_atom "Link to this definition")

Makes a SMEM layout Atom.

This function creates a composed layout in unit of elements consistent with the requested layout Atom kind and element data type.

Parameters:

-   **kind** ([_SmemLayoutAtomKind_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind "cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind")) – The kind of layout Atom
-   **element\_type** (_Type__\[__Numeric__\]_) – The element data type to construct the layout for

Returns:

The SMEM layout atom

Return type:

ComposedLayout

cutlass.cute.nvgpu.warpgroup.fence(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.fence "Link to this definition")

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-multiply-and-accumulate-instruction-wgmma-fence).

cutlass.cute.nvgpu.warpgroup.commit\_group(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.commit_group "Link to this definition")

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-warpgroup-level-matrix-instructions-wgmma-commit-group).

cutlass.cute.nvgpu.warpgroup.wait\_group(_group_, _\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.wait_group "Link to this definition")

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-multiply-and-accumulate-instruction-wgmma-wait-group).

# warpgroup submodule[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#module-cutlass.cute.nvgpu.warpgroup "Link to this heading")

_class_ cutlass.cute.nvgpu.warpgroup.OperandMajorMode(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "Link to this definition")

Bases: `Enum`

An enumeration for the majorness of the input operands of the MMA.

_class_ cutlass.cute.nvgpu.warpgroup.OperandSource(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "Link to this definition")

Bases: `Enum`

An enumeration for the source memory location of the A input operand of the MMA.

_class_ cutlass.cute.nvgpu.warpgroup.Field(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.Field "Link to this definition")

Bases: `Enum`

An enumeration for the fields of the MMA Atom that can be modified at runtime.

ACCUMULATE _\= 'accum\_c'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.Field.ACCUMULATE "Link to this definition")

_class_ cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op "Link to this definition")

Bases: `MmaOp`

F16/BF16 warpgroup MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-warpgroup-level-matrix-instructions-wgmma-mma). This Operation covers the instructions using the `.f16` or `.bf16` qualifiers for the input operands.

descriptive\_name _\= 'warpgroup F16/BF16 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF16BF16Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warpgroup.MmaF8Op(

_a\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_b\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF8Op "Link to this definition")

Bases: `MmaOp`

F8 warpgroup MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-warpgroup-level-matrix-instructions-wgmma-mma). This Operation covers the instructions using the `.e4m3` or `.e5m2` qualifiers for the input operands.

descriptive\_name _\= 'warpgroup F8 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF8Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_a\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_b\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandSource "cutlass.cute.nvgpu.warpgroup.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.OperandMajorMode "cutlass.cute.nvgpu.warpgroup.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.MmaF8Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind "Link to this definition")

Bases: `Enum`

Enum class for the kinds of SMEM layout atoms for SM90.

Given a swizzle kind, an SMEM layout atom is the compact layout of smallest size that can be used to construct an SMEM layout using blocked product for operand A or B such that the resulting layout is legal for both TMA and UMMA.

Note that there are other ways of creating legal layouts for operand A and B.

MN\_INTER _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_INTER "Link to this definition")

MN\_SW32 _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_SW32 "Link to this definition")

MN\_SW64 _\= 3_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_SW64 "Link to this definition")

MN\_SW128 _\= 4_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.MN_SW128 "Link to this definition")

K\_INTER _\= 5_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_INTER "Link to this definition")

K\_SW32 _\= 6_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_SW32 "Link to this definition")

K\_SW64 _\= 7_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_SW64 "Link to this definition")

K\_SW128 _\= 8_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind.K_SW128 "Link to this definition")

cutlass.cute.nvgpu.warpgroup.make\_smem\_layout\_atom(

_kind: [SmemLayoutAtomKind](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind "cutlass.cute.nvgpu.warpgroup.mma.SmemLayoutAtomKind")_,

_element\_type: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.make_smem_layout_atom "Link to this definition")

Makes a SMEM layout Atom.

This function creates a composed layout in unit of elements consistent with the requested layout Atom kind and element data type.

Parameters:

-   **kind** ([_SmemLayoutAtomKind_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind "cutlass.cute.nvgpu.warpgroup.SmemLayoutAtomKind")) – The kind of layout Atom
-   **element\_type** (_Type__\[__Numeric__\]_) – The element data type to construct the layout for

Returns:

The SMEM layout atom

Return type:

ComposedLayout

cutlass.cute.nvgpu.warpgroup.fence(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.fence "Link to this definition")

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-multiply-and-accumulate-instruction-wgmma-fence).

cutlass.cute.nvgpu.warpgroup.commit\_group(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.commit_group "Link to this definition")

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-warpgroup-level-matrix-instructions-wgmma-commit-group).

cutlass.cute.nvgpu.warpgroup.wait\_group(_group_, _\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_warpgroup.html#cutlass.cute.nvgpu.warpgroup.wait_group "Link to this definition")

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#asynchronous-multiply-and-accumulate-instruction-wgmma-wait-group).

# tcgen05 submodule[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#module-cutlass.cute.nvgpu.tcgen05 "Link to this heading")

_class_ cutlass.cute.nvgpu.tcgen05.Repetition(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition "Link to this definition")

Bases: `Enum`

An enumeration for the number of repetitions of a given TMEM copy within the instruction.

x1 _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x1 "Link to this definition")

x2 _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x2 "Link to this definition")

x4 _\= 4_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x4 "Link to this definition")

x8 _\= 8_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x8 "Link to this definition")

x16 _\= 16_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x16 "Link to this definition")

x32 _\= 32_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x32 "Link to this definition")

x64 _\= 64_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x64 "Link to this definition")

x128 _\= 128_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Repetition.x128 "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.TmemLoadRedOp(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.TmemLoadRedOp "Link to this definition")

Bases: `Enum`

An enumeration for the possible reduce operations for TMEM load operations.

_class_ cutlass.cute.nvgpu.tcgen05.Pack(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Pack "Link to this definition")

Bases: `Enum`

An enumeration for the possible packing patterns for TMEM to RMEM copies.

NONE _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Pack.NONE "Link to this definition")

PACK\_16b\_IN\_32b _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Pack.PACK_16b_IN_32b "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Unpack(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Unpack "Link to this definition")

Bases: `Enum`

An enumeration for the possible unpacking patterns for RMEM to TMEM copies.

NONE _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Unpack.NONE "Link to this definition")

UNPACK\_32b\_IN\_16b _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Unpack.UNPACK_32b_IN_16b "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Ld16x64bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x64bOp "Link to this definition")

Bases: `_LdBase`

16x64b TMEM load Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-ld). This Operation corresponds to the `.16x64b` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x64bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Ld16x128bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x128bOp "Link to this definition")

Bases: `_LdBase`

16x128b TMEM load Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-ld). This Operation corresponds to the `.16x128b` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x128bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Ld16x256bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x256bOp "Link to this definition")

Bases: `_LdBase`

16x256b TMEM load Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-ld). This Operation corresponds to the `.16x256b` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x256bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Ld16x32bx2Op(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x32bx2Op "Link to this definition")

Bases: `_LdBase`

16x32bx2 TMEM load Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-ld). This Operation corresponds to the `.16x32bx2` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld16x32bx2Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Ld32x32bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld32x32bOp "Link to this definition")

Bases: `_LdBase`

32x32b TMEM load Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-ld). This Operation corresponds to the `.32x32` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition \= <Repetition.x1>_,

_pack: ~cutlass.cute.nvgpu.tcgen05.copy.Pack \= <Pack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Ld32x32bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.St16x64bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x64bOp "Link to this definition")

Bases: `_StBase`

16x64b TMEM store Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-st). This Operation corresponds to the `.16x64` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x64bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.St16x128bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x128bOp "Link to this definition")

Bases: `_StBase`

16x128b TMEM store Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-st). This Operation corresponds to the `.16x128` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x128bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.St16x256bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x256bOp "Link to this definition")

Bases: `_StBase`

16x256b TMEM store Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-st). This Operation corresponds to the `.16x256` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x256bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.St16x32bx2Op(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x32bx2Op "Link to this definition")

Bases: `_StBase`

16x32x2b TMEM store Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-st). This Operation corresponds to the `.16x32x2` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St16x32bx2Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.St32x32bOp(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St32x32bOp "Link to this definition")

Bases: `_StBase`

32x32b TMEM store Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-st). This Operation corresponds to the `.32x32` qualifier.

\_\_init\_\_(

_repeat: ~cutlass.cute.nvgpu.tcgen05.copy.Repetition_,

_unpack: ~cutlass.cute.nvgpu.tcgen05.copy.Unpack \= <Unpack.NONE>_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.St32x32bOp.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.OperandMajorMode(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "Link to this definition")

Bases: `Enum`

An enumeration for the majorness of the input operands of the MMA.

_class_ cutlass.cute.nvgpu.tcgen05.OperandSource(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "Link to this definition")

Bases: `Enum`

An enumeration for the source memory location of the A input operand of the MMA.

_class_ cutlass.cute.nvgpu.tcgen05.CtaGroup(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "Link to this definition")

Bases: `Enum`

An enumeration for the `cta_group` qualifier of the MMA.

ONE _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup.ONE "Link to this definition")

TWO _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup.TWO "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.Field(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Field "Link to this definition")

Bases: `Enum`

An enumeration for the fields of the MMA Atom that can be modified at runtime.

NEGATE\_A _\= 'neg\_a'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Field.NEGATE_A "Link to this definition")

NEGATE\_B _\= 'neg\_b'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Field.NEGATE_B "Link to this definition")

ACCUMULATE _\= 'accum\_c'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Field.ACCUMULATE "Link to this definition")

SFA _\= 'sf\_a'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Field.SFA "Link to this definition")

SFB _\= 'sf\_b'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Field.SFB "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaTF32Op(

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaTF32Op "Link to this definition")

Bases: `MmaOp`

TF32 tcgen05 MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma). This Operation corresponds to the `.kind::tf32` qualifier.

descriptive\_name _\= 'tcgen05 TF32 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaTF32Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaTF32Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaF16BF16Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaF16BF16Op "Link to this definition")

Bases: `MmaOp`

F16/BF16 tcgen05 MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma). This Operation corresponds to the `.kind::f16` qualifier.

descriptive\_name _\= 'tcgen05 F16/BF16 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaF16BF16Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaF16BF16Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaI8Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaI8Op "Link to this definition")

Bases: `MmaOp`

I8 tcgen05 MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma). This Operation corresponds to the `.kind::i8` qualifier.

descriptive\_name _\= 'tcgen05 I8 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaI8Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaI8Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaFP8Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaFP8Op "Link to this definition")

Bases: `MmaOp`

F8 tcgen05 MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma).

descriptive\_name _\= 'tcgen05 F8 MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaFP8Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_acc\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaFP8Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaMXF8Op(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF8Op "Link to this definition")

Bases: `BlockScaledMmaOp`

MXF8 tcgen05 BlockScaled MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma). This Operation corresponds to the `.kind::mxf8f6f4` qualifier.

descriptive\_name _\= 'tcgen05 MXF8 BlockScaled MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF8Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_ab\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

_a\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

_b\_major\_mode: [OperandMajorMode](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandMajorMode "cutlass.cute.nvgpu.tcgen05.mma.OperandMajorMode")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF8Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaMXF4Op(

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF4Op "Link to this definition")

Bases: `BlockScaledMmaOp`

MXF4 tcgen05 BlockScaled MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma). This Operation corresponds to the `.kind::mxf4` qualifier.

descriptive\_name _\= 'tcgen05 MXF4 BlockScaled MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF4Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF4Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.MmaMXF4NVF4Op(

_sf\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF4NVF4Op "Link to this definition")

Bases: `BlockScaledMmaOp`

MXF4NVF4 tcgen05 BlockScaled MMA Operation.

See the [PTX documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-mma-instructions-mma). This Operation corresponds to the `.kind::mxf4nvf4` qualifier.

descriptive\_name _\= 'tcgen05 MXF4NVF4 BlockScaled MMA Operation'_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF4NVF4Op.descriptive_name "Link to this definition")

\_\_init\_\_(

_sf\_dtype: Type\[cutlass.cute.typing.Numeric\]_,

_instruction\_shape: cutlass.cute.typing.Shape_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_a\_src: [OperandSource](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.OperandSource "cutlass.cute.nvgpu.tcgen05.mma.OperandSource")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.MmaMXF4NVF4Op.__init__ "Link to this definition")

_class_ cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind "Link to this definition")

Bases: `Enum`

Enum class for the kinds of SMEM layout atoms for SM100.

Given a swizzle kind, an SMEM layout atom is the compact layout of smallest size that can be used to construct an SMEM layout using blocked product for operand A or B such that the resulting layout is legal for both TMA and UMMA.

Note that there are other ways of creating legal layouts for operand A and B.

MN\_INTER _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.MN_INTER "Link to this definition")

MN\_SW32 _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.MN_SW32 "Link to this definition")

MN\_SW64 _\= 3_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.MN_SW64 "Link to this definition")

MN\_SW128 _\= 4_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.MN_SW128 "Link to this definition")

MN\_SW128\_32B _\= 5_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.MN_SW128_32B "Link to this definition")

K\_INTER _\= 6_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.K_INTER "Link to this definition")

K\_SW32 _\= 7_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.K_SW32 "Link to this definition")

K\_SW64 _\= 8_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.K_SW64 "Link to this definition")

K\_SW128 _\= 9_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind.K_SW128 "Link to this definition")

cutlass.cute.nvgpu.tcgen05.make\_smem\_layout\_atom(

_kind: [SmemLayoutAtomKind](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind "cutlass.cute.nvgpu.tcgen05.mma.SmemLayoutAtomKind")_,

_element\_type: Type\[cutlass.cute.typing.Numeric\]_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.ComposedLayout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.make_smem_layout_atom "Link to this definition")

Makes a SMEM layout Atom.

This function creates a composed layout in unit of elements consistent with the requested layout Atom kind and element data type.

Parameters:

-   **kind** ([_SmemLayoutAtomKind_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind "cutlass.cute.nvgpu.tcgen05.SmemLayoutAtomKind")) – The kind of layout Atom
-   **element\_type** (_Type__\[__Numeric__\]_) – The element data type to construct the layout for

Returns:

The SMEM layout atom

Return type:

ComposedLayout

cutlass.cute.nvgpu.tcgen05.tile\_to\_mma\_shape(

_atom_,

_mma\_tile\_shape: cutlass.cute.typing.Shape_,

_order: cutlass.cute.typing.IntTuple | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.tile_to_mma_shape "Link to this definition")

Tiles a layout to an MMA shape.

cutlass.cute.nvgpu.tcgen05.commit(

_mbar\_ptr: cutlass.cute.typing.Pointer_,

_mask=None_,

_cta\_group: ~cutlass.cute.nvgpu.tcgen05.mma.CtaGroup \= <CtaGroup.ONE>_,

_\*_,

_loc=None_,

_ip=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.commit "Link to this definition")

Perform an arrive operation on a mbarrier upon completion of previous MMA operations.

Parameters:

-   **mbar\_ptr** (_Pointer_) – A pointer to the mbarrier in SMEM
-   **mask** (_Int_) – An optional multicast mask for the CTAs in the cluster to signal arrival to

cutlass.cute.nvgpu.tcgen05.is\_tmem\_load(_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.is_tmem_load "Link to this definition")

Returns whether a CopyAtom instance is a TMEM load.

cutlass.cute.nvgpu.tcgen05.is\_tmem\_store(_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_) → bool[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.is_tmem_store "Link to this definition")

Returns whether a CopyAtom instance is a TMEM store.

cutlass.cute.nvgpu.tcgen05.get\_tmem\_copy\_properties(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

) → Tuple\[int, int, int, [Pack](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Pack "cutlass.cute.nvgpu.tcgen05.copy.Pack") | [Unpack](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.Unpack "cutlass.cute.nvgpu.tcgen05.copy.Unpack")\][#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.get_tmem_copy_properties "Link to this definition")

Returns the properties of a TMEM copy atom (number of data paths, bits, repetitions, and whether packing/unpacking is used).

cutlass.cute.nvgpu.tcgen05.find\_tmem\_tensor\_col\_offset(

_tmem\_tensor: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.find_tmem_tensor_col_offset "Link to this definition")

Computes the TMEM column offset given a TMEM tensor.

Parameters:

**tmem\_tensor** (_Tensor_) – The TMEM tensor to use to compute the columns offset

Returns:

The columns offset

Return type:

Int

cutlass.cute.nvgpu.tcgen05.make\_tmem\_copy(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_tmem\_tensor: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.make_tmem_copy "Link to this definition")

Makes a Tiled Copy instance from a TMEM Copy Atom and a TMEM tensor.

cutlass.cute.nvgpu.tcgen05.make\_s2t\_copy(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_tmem\_tensor: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [TiledCopy](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.TiledCopy "cutlass.cute.atom.TiledCopy")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.make_s2t_copy "Link to this definition")

Makes a Tiled Copy instance from a TMEM Copy Atom and a TMEM tensor.

cutlass.cute.nvgpu.tcgen05.get\_s2t\_smem\_desc\_tensor(

_atom: [CopyAtom](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute.html#cutlass.cute.CopyAtom "cutlass.cute.atom.CopyAtom")_,

_smem\_tensor: cutlass.cute.typing.Tensor_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Tensor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.get_s2t_smem_desc_tensor "Link to this definition")

Returns the SMEM descriptor tensor from a S2T copy atom and a SMEM tensor.

cutlass.cute.nvgpu.tcgen05.make\_umma\_smem\_desc(

_src: cutlass.cute.typing.Pointer_,

_layout: cutlass.cute.typing.Layout_,

_major: str_,

_next\_src: cutlass.cute.typing.Pointer | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.make_umma_smem_desc "Link to this definition")

Construct shared memory descriptor for UMMA.

The make\_umma\_smem\_desc operation accepts an input cute.ptr (optionally a nextSrc pointer for the second buffer in a circular buffer scheme), alongside a cute.layout and a major attr, then constructs the shared memory descriptor and returns it. The layout must be describing the buffer pointed to by the input pointer and the iterator must carry valid swizzle information.

There are 5 supported swizzle variants: - S<0, 4, 3> | SWIZZLE\_NONE - S<1, 4, 3> | SWIZZLE\_32B - S<2, 4, 3> | SWIZZLE\_64B - S<3, 4, 3> | SWIZZLE\_128B - S<2, 5, 2> | SWIZZLE\_128B\_BASE32B

The cute.ptr must carry shared address space and must be aligned to 16B.

Parameters:

-   **src** (_Pointer_) – The source pointer to shared memory
-   **layout** (_Layout_) – The layout describing the buffer
-   **major** (_str_) – The major mode attribute
-   **next\_src** (_Optional__\[__Pointer__\]_) – Optional next source pointer for circular buffer scheme

Returns:

The shared memory descriptor

Return type:

SmemDescType