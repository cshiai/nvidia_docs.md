# Memory Model[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#memory-model "Link to this heading")

cuTile employs a memory model that permits the compiler and hardware to reorder operations for performance. As a result, without explicit synchronization, there is no guaranteed ordering of memory accesses across threads.

To coordinate memory accesses among threads, cuTile provides two attributes for atomic operations:

-   **Memory Order**: Defines the memory ordering semantics of an atomic operation.
-   **Memory Scope**: Defines the scope of threads that participate in memory ordering.

Synchronization occurs at a per-element granularity. Each element in the array participates independently in the memory model.

For a more detailed explanation, see the Memory Model section in the [Tile IR documentation](https://docs.nvidia.com/cuda/tile-ir/).

## Memory Order[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#memory-order "Link to this heading")

_class_ cuda.tile.MemoryOrder[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryOrder "Link to this definition")

Memory ordering semantics of an atomic operation.

RELAXED _\= 'relaxed'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryOrder.RELAXED "Link to this definition")

No ordering guarantees. Cannot be used to synchronize between threads.

ACQUIRE _\= 'acquire'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryOrder.ACQUIRE "Link to this definition")

Acquire semantics. When this reads a value written by a release, the releasing thread’s prior writes become visible. Subsequent reads/writes within the same block cannot be reordered before this operation.

RELEASE _\= 'release'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryOrder.RELEASE "Link to this definition")

Release semantics. When an acquire reads the value written by this, this thread’s prior writes become visible to the acquiring thread. Prior reads/writes within the same block cannot be reordered after this operation.

ACQ\_REL _\= 'acq\_rel'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryOrder.ACQ_REL "Link to this definition")

Combined acquire and release semantics.

## Memory Scope[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#memory-scope "Link to this heading")

_class_ cuda.tile.MemoryScope[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryScope "Link to this definition")

The scope of threads that participate in memory ordering.

BLOCK _\= 'block'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryScope.BLOCK "Link to this definition")

Ordering guarantees apply to threads within the same block.

DEVICE _\= 'device'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryScope.DEVICE "Link to this definition")

Ordering guarantees apply to all threads on the same GPU.

SYS _\= 'sys'_[#](https://docs.nvidia.com/cuda/cutile-python/memory_model.html#cuda.tile.MemoryScope.SYS "Link to this definition")

Ordering guarantees apply to all threads across the entire system, including multiple GPUs and the host.

[

](https://docs.nvidia.com/cuda/cutile-python/data/tile.html "previous page")
