# cutlass.pipeline[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#module-cutlass.pipeline "Link to this heading")

_class_ cutlass.pipeline.Agent(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent "Link to this definition")

Bases: `Enum`

Agent indicates what is participating in the pipeline synchronization.

Thread _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent.Thread "Link to this definition")

ThreadBlock _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent.ThreadBlock "Link to this definition")

ThreadBlockCluster _\= 3_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent.ThreadBlockCluster "Link to this definition")

_class_ cutlass.pipeline.CooperativeGroup(

_agent: [Agent](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent "cutlass.pipeline.helpers.Agent")_,

_size: int \= 1_,

_alignment\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "Link to this definition")

Bases: `object`

CooperativeGroup contains size and alignment restrictions for an Agent.

\_\_init\_\_(

_agent: [Agent](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent "cutlass.pipeline.helpers.Agent")_,

_size: int \= 1_,

_alignment\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineOp(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp "Link to this definition")

Bases: `Enum`

PipelineOp assigns an operation to an agent corresponding to a specific hardware feature.

AsyncThread _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.AsyncThread "Link to this definition")

TCGen05Mma _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.TCGen05Mma "Link to this definition")

TmaLoad _\= 3_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.TmaLoad "Link to this definition")

ClcLoad _\= 4_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.ClcLoad "Link to this definition")

TmaStore _\= 5_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.TmaStore "Link to this definition")

Composite _\= 6_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.Composite "Link to this definition")

AsyncLoad _\= 7_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp.AsyncLoad "Link to this definition")

_class_ cutlass.pipeline.SyncObject[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "Link to this definition")

Bases: `ABC`

Abstract base class for hardware synchronization primitives.

This class defines the interface for different types of hardware synchronization mechanisms including shared memory barriers, named barriers, and fences.

_abstract_ arrive() → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject.arrive "Link to this definition")

_abstract_ wait() → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject.wait "Link to this definition")

_abstract_ arrive\_and\_wait() → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject.arrive_and_wait "Link to this definition")

_abstract_ arrive\_and\_drop() → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject.arrive_and_drop "Link to this definition")

_abstract_ get\_barrier() → cutlass.cute.typing.Pointer | int | None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject.get_barrier "Link to this definition")

_abstract_ max() → int | None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject.max "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject._abc_impl "Link to this definition")

_class_ cutlass.pipeline.MbarrierArray[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray "Link to this definition")

Bases: [`SyncObject`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")

MbarrierArray implements an abstraction for an array of smem barriers.

\_\_init\_\_(

_barrier\_storage: cutlass.cute.typing.Pointer_,

_num\_stages: int_,

_agent: tuple\[[PipelineOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp "cutlass.pipeline.helpers.PipelineOp"), [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")\]_,

_tx\_count: int \= 0_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.__init__ "Link to this definition")

recast\_to\_new\_op\_type(

_new\_op\_type: [PipelineOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp "cutlass.pipeline.helpers.PipelineOp")_,

) → [MbarrierArray](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray "cutlass.pipeline.helpers.MbarrierArray")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.recast_to_new_op_type "Link to this definition")

Creates a copy of MbarrierArray with a different op\_type without re-initializing barriers

mbarrier\_init(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.mbarrier_init "Link to this definition")

Initializes an array of mbarriers using warp 0.

arrive(

_index: int_,

_dst: int_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup") | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive "Link to this definition")

Select the arrive corresponding to this MbarrierArray’s PipelineOp.

Parameters:

-   **index** (_int_) – Index of the mbarrier in the array to arrive on
-   **dst** (_int_ _|_ _None_) – Destination parameter for selective arrival, which can be either a mask or destination cta rank. When None, both `TCGen05Mma` and `AsyncThread` will arrive on their local mbarrier. - For `TCGen05Mma`, `dst` serves as a multicast mask (e.g., 0b1011 allows arrive signal to be multicast to CTAs in the cluster with rank = 0, 1, and 3). - For `AsyncThread`, `dst` serves as a destination cta rank (e.g., 3 means threads will arrive on the mbarrier with rank = 3 in the cluster).
-   **cta\_group** (`cute.nvgpu.tcgen05.CtaGroup`, optional) – CTA group for `TCGen05Mma`, defaults to None for other op types

arrive\_mbarrier(

_index: int_,

_dst\_rank: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_mbarrier "Link to this definition")

arrive\_cp\_async\_mbarrier(

_index: int_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_cp_async_mbarrier "Link to this definition")

arrive\_tcgen05mma(

_index: int_,

_mask: int | None_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_tcgen05mma "Link to this definition")

arrive\_and\_expect\_tx(

_index: int_,

_tx\_count: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_and_expect_tx "Link to this definition")

arrive\_and\_expect\_tx\_with\_dst(

_index: int_,

_tx\_count: int_,

_dst: int | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_and_expect_tx_with_dst "Link to this definition")

try\_wait(

_index: int_,

_phase: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cutlass\_dsl.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.try_wait "Link to this definition")

wait(

_index: int_,

_phase: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.wait "Link to this definition")

arrive\_and\_wait(

_index: int_,

_phase: int_,

_dst: int_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup") | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_and_wait "Link to this definition")

arrive\_and\_drop(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.arrive_and_drop "Link to this definition")

get\_barrier(

_index: int_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.get_barrier "Link to this definition")

max() → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray.max "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.MbarrierArray._abc_impl "Link to this definition")

_class_ cutlass.pipeline.NamedBarrier(_barrier\_id: int_, _num\_threads: int_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier "Link to this definition")

Bases: [`SyncObject`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")

NamedBarrier is an abstraction for named barriers managed by hardware. There are 16 named barriers available, with barrier\_ids 0-15.

See the [PTX documentation](https://https//docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-bar).

barrier\_id_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.barrier_id "Link to this definition")

num\_threads_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.num_threads "Link to this definition")

arrive(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.arrive "Link to this definition")

The aligned flavor of arrive is used when all threads in the CTA will execute the same instruction. See PTX documentation.

arrive\_unaligned(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.arrive_unaligned "Link to this definition")

The unaligned flavor of arrive can be used with an arbitrary number of threads in the CTA.

wait(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.wait "Link to this definition")

NamedBarriers do not have a standalone wait like mbarriers, only an arrive\_and\_wait. If synchronizing two warps in a producer/consumer pairing, the arrive count would be 32 using mbarriers but 64 using NamedBarriers. Only threads from either the producer or consumer are counted for mbarriers, while all threads participating in the sync are counted for NamedBarriers.

wait\_unaligned(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.wait_unaligned "Link to this definition")

arrive\_and\_wait(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.arrive_and_wait "Link to this definition")

arrive\_and\_drop(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.arrive_and_drop "Link to this definition")

sync(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.sync "Link to this definition")

get\_barrier(_\*_, _loc\=None_, _ip\=None_) → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.get_barrier "Link to this definition")

max() → int[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.max "Link to this definition")

\_\_init\_\_(_barrier\_id: int_, _num\_threads: int_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier.__init__ "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.NamedBarrier._abc_impl "Link to this definition")

_class_ cutlass.pipeline.PipelineOrder(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_depth: int_,

_length: int_,

_group\_id: int_,

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder "Link to this definition")

Bases: `object`

PipelineOrder is used for managing ordered pipeline execution with multiple groups.

This class implements a pipeline ordering mechanism where work is divided into groups and stages, allowing for controlled progression through pipeline stages with proper synchronization between different groups.

The pipeline ordering works as follows: - The pipeline is divided into ‘length’ number of groups - Each group has ‘depth’ number of stages - Groups execute in a specific order with synchronization barriers - Each group waits for the previous group to complete before proceeding

**Example:**

\# Create pipeline order with 3 groups, each with 2 stages
pipeline\_order \= PipelineOrder.create(
    barrier\_storage\=smem\_ptr,      \# shared memory pointer for barriers
    depth\=2,                       \# 2 stages per group
    length\=3,                      \# 3 groups total
    group\_id\=0,                    \# current group ID (0, 1, or 2)
    producer\_group\=producer\_warp   \# cooperative group for producers
)

\# In the pipeline loop
for stage in range(num\_stages):
    pipeline\_order.wait()          \# Wait for previous group to complete
    \# Process current stage
    pipeline\_order.arrive()        \# Signal completion to next group

Copy to clipboard

sync\_object\_full_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.sync_object_full "Link to this definition")

depth_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.depth "Link to this definition")

length_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.length "Link to this definition")

group\_id_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.group_id "Link to this definition")

state_: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.state "Link to this definition")

_static_ create(

_barrier\_storage: cutlass.cute.typing.Pointer_,

_depth: int_,

_length: int_,

_group\_id: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_defer\_sync: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.create "Link to this definition")

get\_barrier\_for\_current\_stage\_idx(_group\_id_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.get_barrier_for_current_stage_idx "Link to this definition")

arrive(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.arrive "Link to this definition")

wait(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.wait "Link to this definition")

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_depth: int_,

_length: int_,

_group\_id: int_,

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOrder.__init__ "Link to this definition")

_class_ cutlass.pipeline.TmaStoreFence(_num\_stages: int \= 0_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence "Link to this definition")

Bases: [`SyncObject`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")

TmaStoreFence is used for a multi-stage epilogue buffer.

\_\_init\_\_(_num\_stages: int \= 0_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.__init__ "Link to this definition")

arrive(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.arrive "Link to this definition")

wait(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.wait "Link to this definition")

arrive\_and\_wait(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.arrive_and_wait "Link to this definition")

arrive\_and\_drop(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.arrive_and_drop "Link to this definition")

get\_barrier(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.get_barrier "Link to this definition")

max() → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.max "Link to this definition")

tail(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence.tail "Link to this definition")

\_abc\_impl _\= <\_abc.\_abc\_data object>_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.TmaStoreFence._abc_impl "Link to this definition")

_class_ cutlass.pipeline.PipelineUserType(_value_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUserType "Link to this definition")

Bases: `Enum`

An enumeration.

Producer _\= 1_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUserType.Producer "Link to this definition")

Consumer _\= 2_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUserType.Consumer "Link to this definition")

ProducerConsumer _\= 3_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUserType.ProducerConsumer "Link to this definition")

_class_ cutlass.pipeline.PipelineState(_stages: int_, _count_, _index_, _phase_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "Link to this definition")

Bases: `object`

Pipeline state contains an index and phase bit corresponding to the current position in the circular buffer.

\_\_init\_\_(_stages: int_, _count_, _index_, _phase_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.__init__ "Link to this definition")

clone() → [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.clone "Link to this definition")

_property_ index_: cutlass.cutlass\_dsl.Int32_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.index "Link to this definition")

_property_ count_: cutlass.cutlass\_dsl.Int32_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.count "Link to this definition")

_property_ stages_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.stages "Link to this definition")

_property_ phase_: cutlass.cutlass\_dsl.Int32_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.phase "Link to this definition")

reset\_count(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.reset_count "Link to this definition")

advance(_\*_, _loc\=None_, _ip\=None_) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.advance "Link to this definition")

reverse(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState.reverse "Link to this definition")

_class_ cutlass.pipeline.PipelineAsync(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "Link to this definition")

Bases: `object`

PipelineAsync is a generic pipeline class where both the producer and consumer are AsyncThreads. It also serves as a base class for specialized pipeline classes.

This class implements a producer-consumer pipeline pattern where both sides operate asynchronously. The pipeline maintains synchronization state using barrier objects to coordinate between producer and consumer threads.

The pipeline state transitions of one pipeline entry(mbarrier) can be represented as:

| Barrier | State | p.acquire | p.commit | c.wait | c.release |
| --- | --- | --- | --- | --- | --- |
| empty\\_bar | empty | <Return> | n/a | n/a |     |
| empty\\_bar | wait | <Block> | n/a | n/a | \\-> empty |
| full\\_bar | wait | n/a | \\-> full | <Block > | n/a |
| full\\_bar | full | n/a |     | <Return> | n/a |

Where:

-   p: producer
-   c: consumer
-   <Block>: This action is blocked until transition to a state allow it to proceed by other side - e.g. `p.acquire()` is blocked until `empty_bar` transition to `empty` state by `c.release()`

Array of mbarriers as circular buffer:

     Advance Direction
   <-------------------

    Producer   Consumer
        |         ^
        V         |
   +-----------------+
 --|X|X|W|D|D|D|D|R|X|<-.
/  +-----------------+   \\
|                        |
\`------------------------'

Copy to clipboard

Where:

-   X: Empty buffer (initial state)
-   W: Producer writing (producer is waiting for buffer to be empty)
-   D: Data ready (producer has written data to buffer)
-   R: Consumer reading (consumer is consuming data from buffer)

**Example:**

\# Create pipeline with 5 stages
pipeline \= PipelineAsync.create(
    num\_stages\=5,                   \# number of pipeline stages
    producer\_group\=producer\_warp,
    consumer\_group\=consumer\_warp
    barrier\_storage\=smem\_ptr,       \# smem pointer for array of mbarriers in shared memory
)

producer, consumer \= pipeline.make\_participants()
\# Producer side
for i in range(num\_iterations):
    handle \= producer.acquire\_and\_advance()  \# Wait for buffer to be empty & Move index to next stage
    \# Write data to pipeline buffer
    handle.commit()   \# Signal buffer is full

\# Consumer side
for i in range(num\_iterations):
    handle \= consumer.wait\_and\_advance()     \# Wait for buffer to be full & Move index to next stage
    \# Read data from pipeline buffer
    handle.release()  \# Signal buffer is empty

Copy to clipboard

sync\_object\_full_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.sync_object_full "Link to this definition")

sync\_object\_empty_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.sync_object_empty "Link to this definition")

num\_stages_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.num_stages "Link to this definition")

producer\_mask_: cutlass.cutlass\_dsl.Int32 | None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.producer_mask "Link to this definition")

consumer\_mask_: cutlass.cutlass\_dsl.Int32 | None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.consumer_mask "Link to this definition")

_static_ \_make\_sync\_object(

_barrier\_storage: cutlass.cute.typing.Pointer_,

_num\_stages: int_,

_agent: tuple\[[PipelineOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp "cutlass.pipeline.helpers.PipelineOp"), [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")\]_,

_tx\_count: int \= 0_,

) → [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync._make_sync_object "Link to this definition")

Returns a SyncObject corresponding to an agent’s PipelineOp.

_static_ create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_barrier\_storage: cutlass.cute.typing.Pointer | None \= None_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None \= None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None \= None_,

_defer\_sync: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.create "Link to this definition")

Creates and initializes a new PipelineAsync instance.

This helper function computes necessary attributes and returns an instance of PipelineAsync with the specified configuration for producer and consumer synchronization.

Parameters:

-   **barrier\_storage** (_cute.Pointer_) – Pointer to the shared memory address for this pipeline’s mbarriers
-   **num\_stages** (_int_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the producer agent
-   **consumer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the consumer agent
-   **producer\_mask** (_Int32__,_ _optional_) – Mask for signaling arrives for the producer agent
-   **consumer\_mask** (_Int32__,_ _optional_) – Mask for signaling arrives for the consumer agent

Raises:

**ValueError** – If barrier\_storage is not a cute.Pointer instance

Returns:

A new `PipelineAsync` instance

Return type:

[PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.PipelineAsync")

producer\_acquire(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.producer_acquire "Link to this definition")

producer\_try\_acquire(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.producer_try_acquire "Link to this definition")

producer\_commit(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.producer_commit "Link to this definition")

consumer\_wait(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_wait\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.consumer_wait "Link to this definition")

consumer\_try\_wait(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.consumer_try_wait "Link to this definition")

consumer\_release(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.consumer_release "Link to this definition")

producer\_get\_barrier(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.producer_get_barrier "Link to this definition")

producer\_tail(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.producer_tail "Link to this definition")

Make sure the last used buffer empty signal is visible to producer. Producer tail is usually executed by producer before exit, to avoid dangling mbarrier arrive signals after kernel exit.

Parameters:

**state** ([_PipelineState_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.PipelineState")) – The pipeline state that points to next useful buffer

make\_producer(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.make_producer "Link to this definition")

make\_consumer(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.make_consumer "Link to this definition")

make\_participants(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.make_participants "Link to this definition")

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineCpAsync(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineCpAsync "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineCpAsync is used for CpAsync producers and AsyncThread consumers

_static_ create(

_barrier\_storage: cutlass.cute.typing.Pointer_,

_num\_stages: cutlass.cutlass\_dsl.Int32_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None \= None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None \= None_,

_defer\_sync: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineCpAsync.create "Link to this definition")

Helper function that computes necessary attributes and returns a `PipelineCpAsync` instance.

Parameters:

-   **barrier\_storage** (_cute.Pointer_) – Pointer to the shared memory address for this pipeline’s mbarriers
-   **num\_stages** (_Int32_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the producer agent
-   **consumer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the consumer agent
-   **producer\_mask** (_Int32__,_ _optional_) – Mask for signaling arrives for the producer agent, defaults to None
-   **consumer\_mask** (_Int32__,_ _optional_) – Mask for signaling arrives for the consumer agent, defaults to None

Returns:

A new `PipelineCpAsync` instance configured with the provided parameters

Return type:

[PipelineCpAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineCpAsync "cutlass.pipeline.PipelineCpAsync")

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineCpAsync.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineTmaAsync(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_signalling\_thread: cutlass.cutlass\_dsl.Boolean_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineTmaAsync is used for TMA producers and AsyncThread consumers (e.g. Hopper mainloops).

is\_signalling\_thread_: cutlass.cutlass\_dsl.Boolean_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.is_signalling_thread "Link to this definition")

_static_ init\_empty\_barrier\_arrive\_signal(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_tidx: cutlass.cutlass\_dsl.Int32_,

_mcast\_mode\_mn: tuple\[int, int\] \= (1, 1)_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.init_empty_barrier_arrive_signal "Link to this definition")

Initialize the empty barrier arrive signal.

This function determines which threads should signal empty barrier arrives based on the cluster layout and multicast modes. It returns the destination CTA rank and whether the current thread should signal.

Parameters:

-   **cta\_layout\_vmnk** (_cute.Layout_) – Layout describing the cluster shape and CTA arrangement
-   **tidx** (_Int32_) – Thread index within the warp
-   **mcast\_mode\_mn** (_tuple__\[__int__,_ _int__\]_) – Tuple specifying multicast modes for m and n dimensions (each 0 or 1), defaults to (1,1)

Raises:

**AssertionError** – If both multicast modes are disabled (0,0)

Returns:

Tuple containing destination CTA rank and boolean indicating if current thread signals

Return type:

tuple\[Int32, Boolean\]

_static_ create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_tx\_count: int_,

_barrier\_storage: cutlass.cute.typing.Pointer | None \= None_,

_cta\_layout\_vmnk: cutlass.cute.typing.Layout | None \= None_,

_tidx: cutlass.cutlass\_dsl.Int32 | None \= None_,

_mcast\_mode\_mn: tuple\[int, int\] \= (1, 1)_,

_defer\_sync: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.create "Link to this definition")

Create a new `PipelineTmaAsync` instance.

Parameters:

-   **num\_stages** (_int_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the producer agent
-   **consumer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the consumer agent
-   **tx\_count** (_int_) – Number of bytes expected to be written to the transaction barrier for one stage
-   **barrier\_storage** (_cute.Pointer__,_ _optional_) – Pointer to the shared memory address for this pipeline’s mbarriers, defaults to None
-   **cta\_layout\_vmnk** (_cute.Layout__,_ _optional_) – Layout of the cluster shape, defaults to None
-   **tidx** (_Int32__,_ _optional_) – Thread index to consumer async threads, defaults to None
-   **mcast\_mode\_mn** (_tuple__\[__int__,_ _int__\]__,_ _optional_) – Tuple specifying multicast modes for m and n dimensions (each 0 or 1), defaults to (1,1)

Raises:

**ValueError** – If barrier\_storage is not a cute.Pointer instance

Returns:

New `PipelineTmaAsync` instance

Return type:

[PipelineTmaAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync "cutlass.pipeline.PipelineTmaAsync")

producer\_acquire(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.producer_acquire "Link to this definition")

TMA producer commit conditionally waits on buffer empty and sets the transaction barrier.

producer\_commit(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.producer_commit "Link to this definition")

TMA producer commit is a noop since TMA instruction itself updates the transaction count.

consumer\_release(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.consumer_release "Link to this definition")

TMA consumer release conditionally signals the empty buffer to the producer.

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_signalling\_thread: cutlass.cutlass\_dsl.Boolean_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaAsync.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineTmaUmma(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_leader\_cta: bool_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineTmaUmma is used for TMA producers and UMMA consumers (e.g. Blackwell mainloops).

is\_leader\_cta_: bool_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.is_leader_cta "Link to this definition")

cta\_group_: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.cta_group "Link to this definition")

\_make\_sync\_object(

_barrier\_storage: cutlass.cute.typing.Pointer_,

_num\_stages: int_,

_agent: tuple\[[PipelineOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp "cutlass.pipeline.helpers.PipelineOp"), [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")\]_,

_tx\_count: int \= 0_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma._make_sync_object "Link to this definition")

Returns a SyncObject corresponding to an agent’s PipelineOp.

\_compute\_mcast\_arrival\_mask(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_mcast\_mode\_mn: tuple\[int, int\]_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma._compute_mcast_arrival_mask "Link to this definition")

Computes a mask for signaling arrivals to multicasting threadblocks.

\_compute\_is\_leader\_cta(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma._compute_is_leader_cta "Link to this definition")

Computes leader threadblocks for 2CTA kernels. For 1CTA, all threadblocks are leaders.

create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_tx\_count: int_,

_barrier\_storage: cutlass.cute.typing.Pointer \= None_,

_cta\_layout\_vmnk: cutlass.cute.typing.Layout | None \= None_,

_mcast\_mode\_mn: tuple\[int, int\] \= (1, 1)_,

_defer\_sync: bool \= False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.create "Link to this definition")

Creates and initializes a new PipelineTmaUmma instance.

Parameters:

-   **num\_stages** (_int_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – CooperativeGroup for the producer agent
-   **consumer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – CooperativeGroup for the consumer agent
-   **tx\_count** (_int_) – Number of bytes expected to be written to the transaction barrier for one stage
-   **barrier\_storage** (_cute.Pointer__,_ _optional_) – Pointer to the shared memory address for this pipeline’s mbarriers
-   **cta\_layout\_vmnk** (_cute.Layout__,_ _optional_) – Layout of the cluster shape
-   **mcast\_mode\_mn** (_tuple__\[__int__,_ _int__\]__,_ _optional_) – Tuple specifying multicast modes for m and n dimensions (each 0 or 1)

Raises:

**ValueError** – If barrier\_storage is not a cute.Pointer instance

Returns:

A new PipelineTmaUmma instance configured with the provided parameters

Return type:

[PipelineTmaUmma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma "cutlass.pipeline.PipelineTmaUmma")

consumer\_release(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.consumer_release "Link to this definition")

UMMA consumer release buffer empty, cta\_group needs to be provided.

producer\_acquire(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.producer_acquire "Link to this definition")

TMA producer commit conditionally waits on buffer empty and sets the transaction barrier for leader threadblocks.

producer\_commit(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.producer_commit "Link to this definition")

TMA producer commit is a noop since TMA instruction itself updates the transaction count.

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_leader\_cta: bool_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaUmma.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineAsyncUmma(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineAsyncUmma is used for AsyncThread producers and UMMA consumers (e.g. Blackwell input fusion pipelines).

cta\_group_: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma.cta_group "Link to this definition")

\_compute\_leading\_cta\_rank(

_cta\_v\_size_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma._compute_leading_cta_rank "Link to this definition")

Computes the leading CTA rank.

\_compute\_is\_leader\_cta(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma._compute_is_leader_cta "Link to this definition")

Computes leader threadblocks for 2CTA kernels. For 1CTA, all threadblocks are leaders.

\_compute\_peer\_cta\_mask(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma._compute_peer_cta_mask "Link to this definition")

Computes a mask for signaling arrivals to multicasting threadblocks.

create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_barrier\_storage: cutlass.cute.typing.Pointer \= None_,

_cta\_layout\_vmnk: cutlass.cute.typing.Layout | None \= None_,

_defer\_sync: bool \= False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma.create "Link to this definition")

Creates and initializes a new PipelineAsyncUmma instance.

Parameters:

-   **num\_stages** (_int_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – CooperativeGroup for the producer agent
-   **consumer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – CooperativeGroup for the consumer agent
-   **barrier\_storage** (_cute.Pointer__,_ _optional_) – Pointer to the shared memory address for this pipeline’s mbarriers
-   **cta\_layout\_vmnk** (_cute.Layout__,_ _optional_) – Layout of the cluster shape

Raises:

**ValueError** – If barrier\_storage is not a cute.Pointer instance

Returns:

A new PipelineAsyncUmma instance configured with the provided parameters

Return type:

[PipelineAsyncUmma](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma "cutlass.pipeline.PipelineAsyncUmma")

consumer\_release(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma.consumer_release "Link to this definition")

UMMA consumer release buffer empty, cta\_group needs to be provided.

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsyncUmma.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineUmmaAsync(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineUmmaAsync is used for UMMA producers and AsyncThread consumers (e.g. Blackwell accumulator pipelines).

cta\_group_: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync.cta_group "Link to this definition")

\_compute\_tmem\_sync\_mask(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync._compute_tmem_sync_mask "Link to this definition")

Computes a mask to signal completion of tmem buffers for 2CTA kernels.

\_compute\_peer\_cta\_rank(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync._compute_peer_cta_rank "Link to this definition")

Computes a mask to signal release of tmem buffers for 2CTA kernels.

create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_barrier\_storage: cutlass.cute.typing.Pointer \= None_,

_cta\_layout\_vmnk: cutlass.cute.typing.Layout | None \= None_,

_defer\_sync: bool \= False_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync.create "Link to this definition")

Creates an instance of PipelineUmmaAsync with computed attributes.

Parameters:

-   **num\_stages** (_int_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the producer agent
-   **consumer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the consumer agent
-   **barrier\_storage** (_cute.Pointer__,_ _optional_) – Pointer to the shared memory address for this pipeline’s mbarriers
-   **cta\_layout\_vmnk** (_cute.Layout__,_ _optional_) – Layout of the cluster shape

Raises:

**ValueError** – If barrier\_storage is not a cute.Pointer instance

Returns:

New instance of `PipelineUmmaAsync`

Return type:

[PipelineUmmaAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync "cutlass.pipeline.PipelineUmmaAsync")

producer\_commit(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync.producer_commit "Link to this definition")

UMMA producer commit buffer full, cta\_group needs to be provided.

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUmmaAsync.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineClcFetchAsync(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_signalling\_thread: cutlass.cutlass\_dsl.Boolean_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync "Link to this definition")

Bases: `object`

PipelineClcFetchAsync implements a producer-consumer pipeline for Cluster Launch Control based dynamic scheduling. Both producer and consumer operate asynchronously using barrier synchronization to coordinate across pipeline stages and cluster CTAs.

-   Producer: waits for empty buffer, signals full barrier with transection bytes across all CTAs in cluster, hardware autosignals each CTA’s mbarrier when transaction bytes are written, then the satte advance to next buffer slot.
-   Consumer: waits for full barrier, then load respinse from local SMEM, then sigals CTA 0’s empty barrier to allow buffer reuse.

sync\_object\_full_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.sync_object_full "Link to this definition")

sync\_object\_empty_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.sync_object_empty "Link to this definition")

num\_stages_: int_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.num_stages "Link to this definition")

producer\_mask_: cutlass.cutlass\_dsl.Int32 | None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.producer_mask "Link to this definition")

consumer\_mask_: cutlass.cutlass\_dsl.Int32 | None_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.consumer_mask "Link to this definition")

is\_signalling\_thread_: cutlass.cutlass\_dsl.Boolean_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.is_signalling_thread "Link to this definition")

_static_ \_init\_full\_barrier\_arrive\_signal(

_cta\_layout\_vmnk: cutlass.cute.typing.Layout_,

_tidx: cutlass.cutlass\_dsl.Int32_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync._init_full_barrier_arrive_signal "Link to this definition")

Computes producer barrier signaling parameters, returns destination CTA rank (0 to cluster\_size-1) based on thread ID, and a boolean flag indicating if this thread participates in signaling.

Parameters:

-   **cta\_layout\_vmnk** – Cluster layout defining CTA count
-   **tidx** – Thread ID within the CTA

_static_ create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_tx\_count: int_,

_barrier\_storage: cutlass.cute.typing.Pointer | None \= None_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None \= None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None \= None_,

_cta\_layout\_vmnk: cutlass.cute.typing.Layout | None \= None_,

_defer\_sync: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.create "Link to this definition")

This helper function computes any necessary attributes and returns an instance of PipelineClcFetchAsync. :param barrier\_storage: Pointer to the shared memory address for this pipeline’s mbarriers :type barrier\_storage: cute.Pointer :param num\_stages: Number of buffer stages for this pipeline :type num\_stages: int :param producer\_group: CooperativeGroup for the producer agent :type producer\_group: CooperativeGroup :param consumer\_group: CooperativeGroup for the consumer agent :type consumer\_group: CooperativeGroup :param tx\_count: Number of bytes expected to be written to the transaction barrier for one stage :type tx\_count: int :param producer\_mask: Mask for signaling arrives for the producer agent, defaults to `None` :type producer\_mask: Int32, optional :param consumer\_mask: Mask for signaling arrives for the consumer agent, defaults to `None` :type consumer\_mask: Int32, optional

producer\_acquire(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.producer_acquire "Link to this definition")

Producer acquire waits for empty buffer and sets transaction expectation on full barrier.

Parameters:

-   **state** – Pipeline state pointing to the current buffer stage
-   **try\_acquire\_token** – Optional token to skip the empty barrier wait

consumer\_wait(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_wait\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.consumer_wait "Link to this definition")

Consumer waits for full barrier to be signaled by hardware multicast.

Parameters:

-   **state** – Pipeline state pointing to the current buffer stage
-   **try\_wait\_token** – Optional token to skip the full barrier wait

consumer\_release(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.consumer_release "Link to this definition")

producer\_get\_barrier(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cute.typing.Pointer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.producer_get_barrier "Link to this definition")

producer\_tail(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.producer_tail "Link to this definition")

Ensures all in-flight buffers are released before producer exits.

Parameters:

-   **state** – Pipeline state with current position in the buffer
-   **try\_acquire\_token** – Optional token to skip the empty barrier waits

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_signalling\_thread: cutlass.cutlass\_dsl.Boolean_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineClcFetchAsync.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineTmaMultiConsumersAsync(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_leader\_cta: bool_,

_sync\_object\_empty\_umma: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty\_async: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineTmaMultiConsumersAsync is used for TMA producers and UMMA+Async consumers.

is\_leader\_cta_: bool_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.is_leader_cta "Link to this definition")

sync\_object\_empty\_umma_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.sync_object_empty_umma "Link to this definition")

sync\_object\_empty\_async_: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.sync_object_empty_async "Link to this definition")

cta\_group_: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.cta_group "Link to this definition")

_static_ create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group\_umma: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_consumer\_group\_async: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

_tx\_count: int_,

_barrier\_storage: cutlass.cute.typing.Pointer | None \= None_,

_cta\_layout\_vmnk: cutlass.cute.typing.Layout | None \= None_,

_defer\_sync: bool \= False_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.create "Link to this definition")

This helper function computes any necessary attributes and returns an instance of PipelineTmaMultiConsumersAsync. :param barrier\_storage: Pointer to the smem address for this pipeline’s mbarriers :type barrier\_storage: cute.Pointer :param num\_stages: Number of buffer stages for this pipeline :type num\_stages: Int32 :param producer\_group: CooperativeGroup for the producer agent :type producer\_group: CooperativeGroup :param consumer\_group\_umma: CooperativeGroup for the UMMA consumer agent :type consumer\_group\_umma: CooperativeGroup :param consumer\_group\_async: CooperativeGroup for the AsyncThread consumer agent :type consumer\_group\_async: CooperativeGroup :param tx\_count: Number of bytes expected to be written to the transaction barrier for one stage :type tx\_count: int :param cta\_layout\_vmnk: Layout of the cluster shape :type cta\_layout\_vmnk: cute.Layout | None

producer\_acquire(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.producer_acquire "Link to this definition")

TMA producer acquire waits on buffer empty and sets the transaction barrier for leader threadblocks.

producer\_commit(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.producer_commit "Link to this definition")

TMA producer commit is a noop since TMA instruction itself updates the transaction count.

consumer\_release(

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_op\_type: [PipelineOp](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineOp "cutlass.pipeline.helpers.PipelineOp")_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.consumer_release "Link to this definition")

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_is\_leader\_cta: bool_,

_sync\_object\_empty\_umma: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty\_async: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_cta\_group: [CtaGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/cute_nvgpu_tcgen05.html#cutlass.cute.nvgpu.tcgen05.CtaGroup "cutlass.cute.nvgpu.tcgen05.mma.CtaGroup")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaMultiConsumersAsync.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineTmaStore(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore "Link to this definition")

Bases: [`PipelineAsync`](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")

PipelineTmaStore is used for synchronizing TMA stores in the epilogue. It does not use mbarriers.

_static_ create(

_\*_,

_num\_stages: int_,

_producer\_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.create "Link to this definition")

This helper function computes any necessary attributes and returns an instance of `PipelineTmaStore`.

Parameters:

-   **num\_stages** (_int_) – Number of buffer stages for this pipeline
-   **producer\_group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – `CooperativeGroup` for the producer agent

Returns:

A new `PipelineTmaStore` instance

Return type:

[PipelineTmaStore](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore "cutlass.pipeline.PipelineTmaStore")

producer\_acquire(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.producer_acquire "Link to this definition")

producer\_commit(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.producer_commit "Link to this definition")

consumer\_wait(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.consumer_wait "Link to this definition")

consumer\_release(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.consumer_release "Link to this definition")

producer\_tail(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.producer_tail "Link to this definition")

\_\_init\_\_(

_sync\_object\_full: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_sync\_object\_empty: [SyncObject](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.SyncObject "cutlass.pipeline.helpers.SyncObject")_,

_num\_stages: int_,

_producer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

_consumer\_mask: cutlass.cutlass\_dsl.Int32 | None_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineTmaStore.__init__ "Link to this definition")

_class_ cutlass.pipeline.PipelineProducer(

_pipeline_,

_state_,

_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer "Link to this definition")

Bases: `object`

A class representing a producer in an asynchronous pipeline.

This class manages the producer side of an asynchronous pipeline, handling synchronization and state management for producing data. It provides methods for acquiring, committing, and advancing through pipeline stages.

Variables:

-   **\_\_pipeline** – The asynchronous pipeline this producer belongs to
-   **\_\_state** – The current state of the producer in the pipeline
-   **\_\_group** – The cooperative group this producer operates in

**Examples:**

pipeline \= PipelineAsync.create(...)
producer, consumer \= pipeline.make\_participants()
for i in range(iterations):
    \# Try to acquire the current buffer without blocking
    try\_acquire\_token \= producer.try\_acquire()

    \# Do something else independently
    ...

    \# Wait for current buffer to be empty & Move index to next stage
    \# If try\_acquire\_token is True, return immediately
    \# If try\_acquire\_token is False, block until buffer is empty
    handle \= producer.acquire\_and\_advance(try\_acquire\_token)

    \# Produce data
    handle.commit()

Copy to clipboard

_class_ ImmutableResourceHandle(

_\_ImmutableResourceHandle\_\_origin: [cutlass.pipeline.sm90.PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")_,

_\_ImmutableResourceHandle\_\_immutable\_state: [cutlass.pipeline.helpers.PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "Link to this definition")

Bases: `ImmutableResourceHandle`

_property_ barrier[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle.barrier "Link to this definition")

Get the barrier pointer for the current pipeline stage.

Returns:

Pointer to the barrier for the current stage

Return type:

cute.Pointer

commit(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle.commit "Link to this definition")

Signal that data production is complete for the current stage.

This allows consumers to start processing the data.

\_\_init\_\_(

_\_ImmutableResourceHandle\_\_origin: [PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")_,

_\_ImmutableResourceHandle\_\_immutable\_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle.__init__ "Link to this definition")

\_\_init\_\_(

_pipeline_,

_state_,

_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.__init__ "Link to this definition")

Initialize a new Producer instance.

Parameters:

-   **pipeline** ([_PipelineAsync_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.PipelineAsync")) – The pipeline this producer belongs to
-   **state** ([_PipelineState_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.PipelineState")) – Initial pipeline state
-   **group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – The cooperative group for synchronization

\_\_pipeline_: [PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.__pipeline "Link to this definition")

\_\_state_: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.__state "Link to this definition")

\_\_group_: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.__group "Link to this definition")

clone()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.clone "Link to this definition")

Create a new Producer instance with the same state.

reset(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.reset "Link to this definition")

Reset the count of how many handles this producer has committed.

acquire(

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "cutlass.pipeline.sm90.PipelineProducer.ImmutableResourceHandle")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.acquire "Link to this definition")

Wait for the current buffer to be empty before producing data. This is a blocking operation.

Parameters:

**try\_acquire\_token** (_Optional__\[__Boolean__\]_) – Optional token to try to acquire the buffer

Returns:

A handle to the producer for committing the data

Return type:

[ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "cutlass.pipeline.PipelineProducer.ImmutableResourceHandle")

advance(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.advance "Link to this definition")

Move to the next pipeline stage.

acquire\_and\_advance(

_try\_acquire\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "cutlass.pipeline.sm90.PipelineProducer.ImmutableResourceHandle")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.acquire_and_advance "Link to this definition")

Acquire the current buffer and advance to the next pipeline stage.

This method combines the acquire() and advance() operations into a single call. It first waits for the current buffer to be empty before producing data, then advances the pipeline to the next stage.

Parameters:

**try\_acquire\_token** (_Optional__\[__Boolean__\]_) – Token indicating whether to try non-blocking acquire. If True, returns immediately without waiting. If False or None, blocks until buffer is empty.

Returns:

A handle to the producer that can be used to commit data to the acquired buffer stage

Return type:

[ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "cutlass.pipeline.PipelineProducer.ImmutableResourceHandle")

try\_acquire(

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cutlass\_dsl.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.try_acquire "Link to this definition")

Attempt to acquire the current buffer without blocking.

This method tries to acquire the current buffer stage for producing data without waiting. It can be used to check buffer availability before committing to a blocking acquire operation.

Returns:

A boolean token indicating whether the buffer was successfully acquired

Return type:

Boolean

commit(

_handle: [ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "cutlass.pipeline.sm90.PipelineProducer.ImmutableResourceHandle") | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.commit "Link to this definition")

Signal that data production is complete for the current stage.

This allows consumers to start processing the data.

Parameters:

**handle** (_Optional__\[_[_ImmutableResourceHandle_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.ImmutableResourceHandle "cutlass.pipeline.PipelineProducer.ImmutableResourceHandle")_\]_) – Optional handle to commit, defaults to None

Raises:

**AssertionError** – If provided handle does not belong to this producer

tail(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineProducer.tail "Link to this definition")

Ensure all used buffers are properly synchronized before producer exit.

This should be called before the producer finishes to avoid dangling signals.

_class_ cutlass.pipeline.PipelineConsumer(

_pipeline_,

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer "Link to this definition")

Bases: `object`

A class representing a consumer in an asynchronous pipeline.

The Consumer class manages the consumer side of an asynchronous pipeline, handling synchronization and state management for consuming data. It provides methods for waiting, releasing, and advancing through pipeline stages.

Variables:

-   **\_\_pipeline** – The asynchronous pipeline this consumer belongs to
-   **\_\_state** – The current state of the consumer in the pipeline
-   **\_\_group** – The cooperative group this consumer operates in

**Examples:**

pipeline \= PipelineAsync.create(...)
producer, consumer \= pipeline.make\_participants()
for i in range(iterations):
    \# Try to wait for buffer to be full
    try\_wait\_token \= consumer.try\_wait()

    \# Do something else independently
    ...

    \# Wait for buffer to be full & Move index to next stage
    \# If try\_wait\_token is True, return immediately
    \# If try\_wait\_token is False, block until buffer is full
    handle \= consumer.wait\_and\_advance(try\_wait\_token)

    \# Consume data
    handle.release(  )  \# Signal buffer is empty

    \# Alternative way to do this is:
    \# handle.release()  # Signal buffer is empty

Copy to clipboard

_class_ ImmutableResourceHandle(

_\_ImmutableResourceHandle\_\_origin: [cutlass.pipeline.sm90.PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")_,

_\_ImmutableResourceHandle\_\_immutable\_state: [cutlass.pipeline.helpers.PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle "Link to this definition")

Bases: `ImmutableResourceHandle`

release(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle.release "Link to this definition")

Signal that data production is complete for the current stage. This allows consumers to start processing the data.

\_\_init\_\_(

_\_ImmutableResourceHandle\_\_origin: [PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")_,

_\_ImmutableResourceHandle\_\_immutable\_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

) → None[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle.__init__ "Link to this definition")

\_\_init\_\_(

_pipeline_,

_state: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_,

_group: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.__init__ "Link to this definition")

Initialize a new Consumer instance.

Parameters:

-   **pipeline** ([_PipelineAsync_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.PipelineAsync")) – The pipeline this consumer belongs to
-   **state** ([_PipelineState_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.PipelineState")) – Initial pipeline state
-   **group** ([_CooperativeGroup_](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.CooperativeGroup")) – The cooperative group for synchronization

\_\_pipeline_: [PipelineAsync](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineAsync "cutlass.pipeline.sm90.PipelineAsync")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.__pipeline "Link to this definition")

\_\_group_: [CooperativeGroup](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.CooperativeGroup "cutlass.pipeline.helpers.CooperativeGroup")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.__group "Link to this definition")

\_\_state_: [PipelineState](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineState "cutlass.pipeline.helpers.PipelineState")_[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.__state "Link to this definition")

clone()[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.clone "Link to this definition")

Create a new Consumer instance with the same state.

reset(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.reset "Link to this definition")

Reset the count of how many handles this consumer has consumed.

wait(

_try\_wait\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle "cutlass.pipeline.sm90.PipelineConsumer.ImmutableResourceHandle")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.wait "Link to this definition")

Wait for data to be ready in the current buffer. This is a blocking operation that will not return until data is available.

Parameters:

**try\_wait\_token** (_Optional__\[__Boolean__\]_) – Token used to attempt a non-blocking wait for the buffer. If provided and True, returns immediately if buffer is not ready.

Returns:

An immutable handle to the consumer that can be used to release the buffer once data consumption is complete

Return type:

[ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle "cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle")

advance(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.advance "Link to this definition")

Advance the consumer to the next pipeline stage.

This updates the internal state to point to the next buffer in the pipeline. Should be called after consuming data from the current buffer.

wait\_and\_advance(

_try\_wait\_token: cutlass.cutlass\_dsl.Boolean | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

) → [ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle "cutlass.pipeline.sm90.PipelineConsumer.ImmutableResourceHandle")[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.wait_and_advance "Link to this definition")

Atomically wait for data and advance to next pipeline stage.

This is a convenience method that combines wait() and advance() into a single atomic operation. It will block until data is available in the current buffer, then automatically advance to the next stage.

Parameters:

**try\_wait\_token** (_Optional__\[__Boolean__\]_) – Token used to attempt a non-blocking wait for the buffer. If provided and True, returns immediately if buffer is not ready.

Returns:

An immutable handle to the consumer that can be used to release the buffer once data consumption is complete

Return type:

[ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle "cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle")

try\_wait(

_\*_,

_loc\=None_,

_ip\=None_,

) → cutlass.cutlass\_dsl.Boolean[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.try_wait "Link to this definition")

Non-blocking check if data is ready in the current buffer.

This method provides a way to test if data is available without blocking. Unlike wait(), this will return immediately regardless of buffer state.

Returns:

True if data is ready to be consumed, False if the buffer is not yet ready

Return type:

Boolean

release(

_handle: [ImmutableResourceHandle](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.ImmutableResourceHandle "cutlass.pipeline.sm90.PipelineConsumer.ImmutableResourceHandle") | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineConsumer.release "Link to this definition")

Signal that data consumption is complete for the current stage. This allows producers to start producing new data.

cutlass.pipeline.make\_pipeline\_state(

_type: [PipelineUserType](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.PipelineUserType "cutlass.pipeline.helpers.PipelineUserType")_,

_stages: int_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.make_pipeline_state "Link to this definition")

Creates a pipeline state. Producers are assumed to start with an empty buffer and have a flipped phase bit of 1.

cutlass.pipeline.pipeline\_init\_arrive(

_cluster\_shape\_mn: cutlass.cute.typing.Layout | None \= None_,

_is\_relaxed: bool \= False_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.pipeline_init_arrive "Link to this definition")

Fences the mbarrier\_init and sends an arrive if using clusters.

cutlass.pipeline.pipeline\_init\_wait(

_cluster\_shape\_mn: cutlass.cute.typing.Layout | None \= None_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.pipeline_init_wait "Link to this definition")

Syncs the threadblock or cluster

cutlass.pipeline.agent\_sync(

_group: [Agent](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.Agent "cutlass.pipeline.helpers.Agent")_,

_is\_relaxed: bool \= False_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.agent_sync "Link to this definition")

Syncs all threads within an agent.

cutlass.pipeline.arrive(_barrier\_id: int_, _num\_threads: int_, _\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.arrive "Link to this definition")

The aligned flavor of arrive is used when all threads in the CTA will execute the same instruction. See PTX documentation.

cutlass.pipeline.arrive\_unaligned(

_barrier\_id: int_,

_num\_threads: int_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.arrive_unaligned "Link to this definition")

The unaligned flavor of arrive can be used with an arbitrary number of threads in the CTA.

cutlass.pipeline.wait(_\*_, _loc\=None_, _ip\=None_)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.wait "Link to this definition")

NamedBarriers do not have a standalone wait like mbarriers, only an arrive\_and\_wait. If synchronizing two warps in a producer/consumer pairing, the arrive count would be 32 using mbarriers but 64 using NamedBarriers. Only threads from either the producer or consumer are counted for mbarriers, while all threads participating in the sync are counted for NamedBarriers.

cutlass.pipeline.wait\_unaligned(

_barrier\_id: int_,

_num\_threads: int_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.wait_unaligned "Link to this definition")

cutlass.pipeline.arrive\_and\_wait(

_barrier\_id: int_,

_num\_threads: int_,

_\*_,

_loc\=None_,

_ip\=None_,

)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_api/pipeline.html#cutlass.pipeline.arrive_and_wait "Link to this definition")

cutlass.pipeline.sync(_barrier\_id: int \= 0_, _\*_, _loc\=None_, _ip\=None_)

