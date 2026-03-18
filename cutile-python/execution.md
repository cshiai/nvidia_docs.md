# Execution Model[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-model "Link to this heading")

## Abstract Machine[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#abstract-machine "Link to this heading")

A _tile kernel_ is executed by logical thread [blocks](https://docs.nvidia.com/cuda/cutile-python/execution.html#block) that are organized in a 1D, 2D, or 3D _grid_.

Each _block_ is executed by a subset of a GPU, which is decided by the implementation, not the programmer. Each [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block) executes the body of the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels). Scalar operations are executed serially by a single thread of the [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block), and array operations are collectively executed in parallel by all threads of the [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block).

Tile programs explicitly describe [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block)\-level parallelism, but not thread-level parallelism. Threads cannot be explicitly identified or manipulated in tile programs.

Explicit synchronization or communication within a [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block) is not permitted, but it is allowed between different [blocks](https://docs.nvidia.com/cuda/cutile-python/execution.html#block).

It is important to not confuse [blocks](https://docs.nvidia.com/cuda/cutile-python/execution.html#block) (units of execution) with [tiles](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) (units of data). A block may work with multiple different [tiles](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) with differing shapes originating from differing [global arrays](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array).

## Execution Spaces[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-spaces "Link to this heading")

cuTile code is executed on one or more _targets_, which are distinct execution environments that are distinguished by different hardware resources or programming models.

A function is _usable_ if it can be called. A type or object is _usable_ if its attributes are accessible (can be read and written) and its methods are callable.

Some functions, types, and objects are only usable on certain _targets_. The set of _targets_ that such a construct is usable on is called its _execution space_.

-   _Host code_ is the execution space that includes all CPU targets.
-   _SIMT code_ is the execution space that includes all CUDA SIMT targets. Note: This has historically been called device code, but we avoid this term to prevent ambiguity.
-   _Tile code_ is the execution space that includes all CUDA tile targets.

Functions can have decorators that explicitly specify their execution space. These are called _annotated functions_.

## Tile Functions[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-functions "Link to this heading")

_class_ cuda.tile.function(_func\=None_, _/_, _\*_, _host\=False_, _tile\=True_)[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#cuda.tile.function "Link to this definition")

_Tile functions_ are functions that are usable in [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code).

This decorator indicates what [execution spaces](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-execution-spaces) a function can be called from. With no arguments, it denotes a tile-only function.

When an unannotated function is called by a [tile function](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-functions), tile shall be added to the unannotated function’s execution space. This process is recursive. No explicit annotation is required.

The types usable as parameters to a [tile function](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-functions) are described in the [data model](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-model).

Parameters:

-   **host** (_bool__,_ _optional_) – Whether the function can be called from [host code](https://docs.nvidia.com/cuda/cutile-python/execution.html#host-code). Default is False.
-   **tile** (_bool__,_ _optional_) – Whether the function can be called from [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code). Default is True.

## Tile Kernels[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels "Link to this heading")

_class_ cuda.tile.kernel(_function\=None_, _/_, _\*\*kwargs_)[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#cuda.tile.kernel "Link to this definition")

A _tile kernel_ is a function executed by each [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block) in a [grid](https://docs.nvidia.com/cuda/cutile-python/execution.html#grid).

Functions with this decorator are [kernels](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels).

[Kernels](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) are the entry points of [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code). Their [execution space](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-execution-spaces) shall be only [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code); they cannot be called from [host code](https://docs.nvidia.com/cuda/cutile-python/execution.html#host-code).

Kernels cannot be called directly. Instead, use [`launch()`](https://docs.nvidia.com/cuda/cutile-python/execution.html#cuda.tile.launch "cuda.tile.launch") to queue a kernel for execution over a grid.

The types usable as parameters to a [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) are described in the [data model](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-model).

Parameters:

-   **num\_ctas** – Number of CTAs in a CGA. Must be a power of 2 between 1 and 16, inclusive. Default: None (auto).
-   **occupancy** – Expected number of active CTAs per SM, \[1, 32\]. Default: None (auto).
-   **opt\_level** – Optimization level \[0, 3\], default 3.

Target-specific values for the compiler options above can be provided using a [`ByTarget`](https://docs.nvidia.com/cuda/cutile-python/performance.html#cuda.tile.ByTarget "cuda.tile.ByTarget") object.

Examples:

@ct.kernel
def f(a, b, c):
    pass

grid \= (8, 8)
ct.launch(stream, grid, f, (A, B, C))

cuda.tile.launch(_stream_, _grid_, _kernel_, _kernel\_args_, _/_)[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#cuda.tile.launch "Link to this definition")

Launch a cuTile kernel.

Parameters:

-   **stream** – The CUDA stream to execute the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) on.
-   **grid** – Tuple of up to 3 grid dimensions to execute the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) over.
-   **kernel** – The [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) to execute.
-   **kernel\_args** – Positional arguments to pass to the kernel.

## Python Subset[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#python-subset "Link to this heading")

[Tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code) supports a subset of the Python language. Within [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code), there is no Python runtime.

Only Python features explicitly enumerated in this document are supported. Many features, such as lambdas, exceptions, and coroutines are not supported today.

### Object Model & Lifetimes[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#object-model-lifetimes "Link to this heading")

All objects created within [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code) are immutable. Any operation that conceptually modifies an object or its attributes creates and returns a new object. Attributes cannot be dynamically added to objects.

The only mutable objects that can be used in [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code) are [arrays](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array), which must be passed in as [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) parameters.

The caller of a [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) must ensure that:

-   No [arrays](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array) passed to the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) alias one another.
-   All passed [arrays](https://docs.nvidia.com/cuda/cutile-python/data/array.html#data-array-cuda-tile-array) remain valid until the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) has finished execution.

### Control Flow[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#control-flow "Link to this heading")

Python control flow statements (`if`, `for`, `while`, etc.) shall be usable in [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code). They can be arbitrarily nested.

#### Current limitations[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#current-limitations "Link to this heading")

The Python subset used in [tile code](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-code) imposes additional restrictions on control flow:

-   `step` must be strictly positive.
    
    Negative-step ranges such as `range(10, 0, -1)` are not supported today. Passing a negative step indirectly via a variable may lead to undefined behavior.
    

## Tile Parallelism[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#tile-parallelism "Link to this heading")

When a [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block) executes a function that takes [tiles](https://docs.nvidia.com/cuda/cutile-python/data.html#data-tiles-and-scalars) as parameters, it may parallelize the evaluation of the function across the [block](https://docs.nvidia.com/cuda/cutile-python/execution.html#block)’s execution resources. Unless otherwise specified, the execution shall complete before the function returns.

## Constantness[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#constantness "Link to this heading")

### Constant Expressions & Objects[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#constant-expressions-objects "Link to this heading")

Some facilities require certain parameters to be an object that is known statically at compilation time. _Constant expressions_ produce _constant objects_ suitable for such parameters. Constant expressions are:

-   A literal object.
-   Integer arithmetic expressions where all the operands are literal objects.
-   A local object or parameter that is assigned from a literal object or constant expression.
-   A global object that is defined at the time of compilation or launch.

By default, numeric constants are _loosely typed_: until used in a context that requires a type of a specific width, integer constants have infinite precision, and floating-point constants are stored in the IEEE 754 double precision format.

A _strictly typed_ constant can be created by calling a dtype object as a constructor, e.g. `ct.int16(5)` creates a strictly typed `int16` constant. When a strictly typed constant is combined with a loosely typed constant, the result is a strictly typed constant. For example `ct.int16(5) + 2` will create a strictly typed `int16` constant 7.

Combining two strictly typed constants creates a new strictly typed constant. In this case, the regular [type promotion](https://docs.nvidia.com/cuda/cutile-python/data.html#data-arithmetic-promotion) rules apply. For example, `ct.int16(5) + ct.int32(7)` will create a strictly typed `int32` constant 12.

### Constant Embedding[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#constant-embedding "Link to this heading")

If a parameter to a [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) is _constant embedded_, then:

-   All uses of the parameter shall act as if they were replaced by the literal value of the parameter.
-   There shall be a distinct machine representation of the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) for each different value of the parameter that the [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) is invoked with. Note: The [kernel](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-tile-kernels) shall be compiled once for each different value of the parameter, even if JIT caching is enabled.
-   The [machine representation](https://docs.nvidia.com/cuda/cutile-python/interoperability.html#interoperability-machine-representation) of the parameter shall be 0 bytes.

### Constant Type Hints[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#constant-type-hints "Link to this heading")

import cuda.tile as ct

def needs\_constant(x: ct.Constant):
    pass

def needs\_constant\_int(x: ct.Constant\[int\]):
    pass

_class_ cuda.tile.ConstantAnnotation[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#cuda.tile.ConstantAnnotation "Link to this definition")

A `typing.Annotated` metadata class indicating that an object shall be [constant embedded](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-embedding).

If an object of this class is passed as a metadata argument to a `typing.Annotated` type hint on a parameter, then the parameter shall be a constant embedded.

cuda.tile.Constant[#](https://docs.nvidia.com/cuda/cutile-python/execution.html#cuda.tile.Constant "Link to this definition")

A type hint indicating that a value shall be [constant embedded](https://docs.nvidia.com/cuda/cutile-python/execution.html#execution-constant-embedding). It can be used either with (`Constant[int]`) or without (`Constant`, meaning a constant of any type) an underlying type hint.

alias of `Annotated`\[`T`, ConstantAnnotation()\]
