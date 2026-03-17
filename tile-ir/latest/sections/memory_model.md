# 7\. Memory Model[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#memory-model "Link to this heading")

The memory model defines the legal values that loads can return from memory. This is not as straightforward as one might expect at first glance, to enable compiler and hardware optimizations, we allow the apparent re-ordering of instructions.

This memory model is derived from the PTX memory model, and synchronization primitives are deliberately similar.

## 7.1. Memory model operations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#memory-model-operations "Link to this heading")

The memory model is built of relations between individual element accesses of tile operations, and restrictions on cycles of those relations. Therefore, a **Tile IR** memory instruction generates one or more memory model operations. In particular, tile loads, stores, and atomic updates generate one memory operation per element in the tile. When expanding a tile operation into many memory model operations, one might ask what order the memory model operations happen in. That is deliberately left unspecified for implementation flexibility.

To generalize the memory model over **Tile IR** operations, we use the terminology of _memory model operations_ throughout the specification of the memory consistency model. We enumerate which **Tile IR** operations expand into which memory model operations in the table below.

## 7.2. Scopes[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#scopes "Link to this heading")

Memory operations in **Tile IR** may have a scope. Operations without a scope are called `weak`. All memory operations specify a scope or `weak`. Any scope other than weak requires a memory ordering to be set.

| Scope | Description |
| --- | --- |
| `tile_block` | Tile block scope, for communication within a single tile block. |
| `device` | Device scope, for communication within the same GPU. |
| `sys` | System scope, for communication anywhere in the system. |

Weak operations cannot be used to communicate through memory between threads, or between fragments of the same tile block which are not ordered by token order. The compiler may assume that tiles accessed with `weak` are not concurrently accessed by any other thread.

Note

Tile Block scope is needed when building communicating algorithms where there is communication within a single tile block. This is necessary when communicating memory through memory between operations which are not ordered by token order, or when storing to a tile with internal aliasing.

## 7.3. Memory ordering[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#memory-ordering "Link to this heading")

Memory operations have a memory ordering parameter which controls how that operation can be used for synchronization. Synchronization through memory is a two-party process, which requires a releaser and an acquirer observing the same location. When a pair of memory accesses synchronize through memory it establishes a _happens before_ relationship. See the happens before definition below.

Any ordering other than `weak` requires a scope to be set.

| Memory ordering | Description |
| --- | --- |
| `weak` | No concurrent accesses to the source/destination location. |
| `relaxed` | There may be concurrent access to the location, but this access does not establish a happens-before relationship. |
| `release` | There may be concurrent access to the location. If this release is observed with an acquire operation, then happens before is established. |
| `acquire` | There may be concurrent accesses to the location. If this acquire observes a release operation, then happens before is established. |
| `acq_rel` | There may be concurrent accesses to the location. This has the effect of both a release and acquire operation. |

## 7.4. Moral Strength[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#moral-strength "Link to this heading")

Two accesses to the same location are morally strong if the operations are related in _restricted program order_, or each operation specifies a scope which includes the tile block executing the other operation.

## 7.5. Tokens and token order[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#tokens-and-token-order "Link to this heading")

In **Tile IR** we have explicit annotation of dependencies between loads and stores for the token-ordered operations. **Tile IR** produces wide loads and stores of whole tiles of data, making efficient use of various resources of the GPU in parallel. We provide token ordered operations to explicitly inform the **Tile IR** toolchain that two operations may happen in parallel, and will not interfere with each other. There is a family of memory operations called token ordered operations which produce and consume tokens. Tokens are abstract values in the **Tile IR** language for building dependencies between memory operations within the same tile block thread. They have no concrete representation at runtime, cannot be compared, computed upon, or stored/loaded to/from memory.

Program dependencies (i.e. dependencies apparent from control flow, data dependency, or address dependency) **do not** provide ordering between two memory operations. Tokens must be used, even where the token ordering appears redundant with program dependencies. Program dependencies may be optimized away by the **Tile IR** toolchain, whereas token dependencies are not.

## 7.6. Base relations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#base-relations "Link to this heading")

**Coherence order**

There exists a partial transitive order that relates overlapping write operations, determined at runtime, called _coherence order_. Two overlapping write operations are related in _coherence order_ if they are _morally strong_ or if they are related in _happens before_ order.

**Program order**

A memory operation A is program order before a memory operation B if the instruction that gave rise to A is before the instruction that gave rise to B in the program source.

**Waits-for order**

An operation A _waits-for_ an operation B if: - an instruction IA gave rise to A, IA produced a token t, an instruction IB gave rise to B and IB depends upon the token t; or - there is some operation C such that A _waits-for_ C and C _waits-for_ B.

**Reads from**

An read operation R _reads-from_ a write operation W when R and W access the same location and R reads the value written by W.

**Read-modify-write order**

Read-modify-write atomics generate a pair of memory operations for each element location within a tile. Each pair of memory operations is related by _read-modify-write order_.

**Atomicity**

When an atomic operation A and a write W overlap and are _morally strong_, then the following two communications cannot both exist in the same execution:

-   A reads from a write W′ that precedes W in _coherence order_.
-   A follows W in _coherence order_.

## 7.9. No-thin-air[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#no-thin-air "Link to this heading")

It is not practical to specify a “no thin air” axiom without preventing useful compiler optimizations. We therefore say informally that the implementation will not provide values out of thin air to satisfy program executions.

## 7.10. Data Races[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#data-races "Link to this heading")

Two accesses are said to _conflict_ when they access the same location and at least one of them is a write.

Two conflicting memory accesses are said to be in a _data race_ if they are not related in happens before and are they are not morally strong.

Programs with data races have **undefined behaviour**.

## 7.11. PTX interoperability[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#ptx-interoperability "Link to this heading")

The axioms and relations of the **Tile IR** memory model are intended to be a strict weakening of the PTX memory model.

The **Tile IR** memory model is designed to allow communication with PTX threads. Release and acquire patterns in **Tile IR** will match up with acquire and release patterns in PTX to build PTX _causality_ and **Tile IR** _happens before_.

The same is true for data races, data races between accesses in a **Tile IR** program and a PTX program will result in undefined behavior as if the data race were all in **Tile IR**.

## 7.12. Hazards and intuition in the **Tile IR** Memory Model[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#hazards-and-intuition-in-the-cuda-tile-memory-model "Link to this heading")

### 7.12.1. Token ordered operations reading from the future[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#token-ordered-operations-reading-from-the-future "Link to this heading")

Store buffering and load buffering behavior are visible when using token ordered operations without token constraints.

### 7.12.2. Race hazards within a single tile block thread[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#race-hazards-within-a-single-tile-block-thread "Link to this heading")

The definition of data race relies on two operations being in happens before order. In many programming languages this is always true within a single thread, but this is not the case in **Tile IR**. In **Tile IR** you can construct a data race when there are two accesses to the same location within a single tile block store (because of internal overlap in the destination tile), or with two accesses within a tile block thread to the same location which are not ordered by token order. This motivates the need for a `tile_block` scope, and is a hazard to be aware of in the language.

### 7.12.3. Some intuition on how to use token ordering[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#some-intuition-on-how-to-use-token-ordering "Link to this heading")

When you have memory accesses to tiles with no overlap between them, it is generally safe to not order these with respect to each other in token order. When you use a release operation, you need to token-order all memory events that must stay before the release to the release itself. Similarly, when an acquire operation is used, all memory events which must remain after the acquire need to be token ordered after the acquire operation itself.

To reiterate: a user of **Tile IR** cannot rely on program dependencies of any form other than token dependencies to enforce ordering within a Tile Block Thread. The **Tile IR** toolchain can remove dependencies through any possible complex reasoning, breaking dependencies which appear to be in the program syntax.
