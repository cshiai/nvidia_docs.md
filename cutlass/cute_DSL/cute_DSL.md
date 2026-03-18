# Introduction[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_introduction.html#introduction "Link to this heading")

## Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_introduction.html#overview "Link to this heading")

CuTe DSL is a Python-based domain-specific language (DSL) designed for dynamic compilation of high-performance GPU kernels. It evolved from the C++ CUTLASS library and is now available as a decorator-based DSL.

Its primary goals are:

-   **Zero-cost abstraction**, DSL is a zero-cost abstraction thanks to Hybrid DSL approach.
-   **Consistent with CuTe C++**, allowing users to express GPU kernels with full control of the hardware.
-   **JIT compilation** for both host and GPU execution.
-   [DLPack](https://github.com/dmlc/dlpack) **integration**, enabling seamless interop with frameworks (e.g., PyTorch, JAX).
-   **JIT caching**, so that repeated calls to the same function benefit from cached IR modules.
-   **Native types and type inference** to reduce boilerplate and improve performance.
-   **Optional lower-level control**, offering direct access to GPU backends or specialized IR dialects.

## Decorators[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_introduction.html#decorators "Link to this heading")

CuTe DSL provides two main Python decorators for generating optimized code via dynamic compilation:

1.  `@jit` — Host-side JIT-compiled functions
2.  `@kernel` — GPU kernel functions

Both decorators can optionally use a **preprocessor** that automatically expands Python control flow (loops, conditionals) into operations consumable by the underlying IR.

### `@jit`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_introduction.html#jit "Link to this heading")

Declares JIT-compiled functions that can be invoked from Python or from other CuTe DSL functions.

**Decorator Parameters**:

-   `preprocessor`:
    
    -   `True` (default) — Automatically translate Python flow control (e.g., loops, if-statements) into IR operations.
    -   `False` — No automatic expansion; Python flow control must be handled manually or avoided.

**Call-site Parameters**:

-   `no_cache`:
    
    -   `True` — Disables JIT caching, forcing a fresh compilation each call.
    -   `False` (default) — Enables caching for faster subsequent calls.

### `@kernel`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_introduction.html#kernel "Link to this heading")

Defines GPU kernel functions, compiled as specialized GPU symbols through dynamic compilation.

**Decorator Parameters**:

-   `preprocessor`:
    
    -   `True` (default) — Automatically expands Python loops/ifs into GPU-compatible IR operations.
    -   `False` — Expects manual or simplified kernel implementations.

**Kernel Launch Parameters**:

-   `grid` Specifies the grid size as a list of integers.
-   `block` Specifies the block size as a list of integers.
-   `cluster` Specifies the cluster size as a list of integers.
-   `smem` Specifies the size of shared memory in bytes (integer).

## Calling Conventions[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_introduction.html#calling-conventions "Link to this heading")

| **Caller** | **Callee** | **Allowed** | **Compilation/Runtime** |
| --- | --- | --- | --- |
| Python function | `@jit` | ✅   | DSL runtime |
| Python function | `@kernel` | ❌   | N/A (error raised) |
| `@jit` | `@jit` | ✅   | Compile-time call, inlined |
| `@jit` | Python function | ✅   | Compile-time call, inlined |
| `@jit` | `@kernel` | ✅   | Dynamic call via GPU driver or runtime |
| `@kernel` | `@jit` | ✅   | Compile-time call, inlined |
| `@kernel` | Python function | ✅   | Compile-time call, inlined |
| `@kernel` | `@kernel` | ❌   | N/A (error raised) |

# End-to-End Code Generation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#end-to-end-code-generation "Link to this heading")

## 1\. Hybrid DSL: Python Metaprogramming, Structured GPU Code[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#hybrid-dsl-python-metaprogramming-structured-gpu-code "Link to this heading")

CuTe DSL is a **hybrid DSL** that combines two compilation techniques: _AST rewrite_ and _tracing_. This combination gives you the best of both worlds:

-   **Program structure is preserved** — control flow (loops, branches) is captured via AST rewrite, compiling to proper structured code instead of flattened traces.
-   **Python stays Python** — arithmetic and tensor operations are captured via tracing, so dynamic shapes, metaprogramming, and Python’s rich expression language work naturally.

To understand why this matters, let’s look at each technique.

### 1.1 AST Rewrite[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#ast-rewrite "Link to this heading")

The function’s abstract-syntax tree is analysed **before** execution. Python control-flow (`for`/`while`, `if`/`else`) and built-ins are converted to structured intermediate representation (IR) constructs. Computation inside each region is left untouched at this stage.

_Advantages_

-   Sees the entire program, so every branch and loop is preserved.
-   Keeps loop structure intact for optimization such as tiling, vectorisation or GPU thread mapping.

_Disadvantages_

-   Requires a well-defined Python subset that the rewriter understands.

### 1.2 Tracing[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#tracing "Link to this heading")

The decorated function is executed once with _proxy_ arguments; overloaded operators record every tensor operation that actually runs and produce a flat trace that is lowered to intermediate representation (IR).

_Advantages_

-   Near-zero compile latency, ideal for straight-line arithmetic.
-   No need to parse Python source, so it supports many dynamic Python features, and Python has many features.

_Disadvantages_

-   Untaken branches vanish, so the generated kernel may be wrong for other inputs.
-   Loops are flattened to the iteration count observed during tracing.
-   Data-dependent control-flow freezes to a single execution path.

### 1.3 The Hybrid Solution[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#the-hybrid-solution "Link to this heading")

As shown above, neither technique alone is sufficient—but together they complement each other perfectly.

**Why this works: GPU kernels are simple at runtime**

High-performance GPU kernels are structurally simple at runtime: they avoid deep call hierarchies, complex branching, and dynamic dispatch. However, _authoring_ such kernels benefits greatly from Python’s abstractions—classes, metaprogramming, and polymorphic patterns improve readability and maintainability.

The hybrid approach resolves this tension by evaluating Python abstractions at compile time while emitting simple, optimized code for runtime execution.

**How |DSL| divides the work:**

1.  **AST rewrite handles structure** — loops (`for`, `while`) and branches (`if`/`else`) are converted to structured intermediate representation (IR) _before_ execution. This solves tracing’s control-flow problem.
2.  **Tracing handles arithmetic** — inside each structured region, the tracer records tensor operations exactly as they execute. No need to model Python’s complex semantics—just run Python and record what happens. This solves AST rewriting’s complexity problem.

The result:

-   Loops compile to real loops, not unrolled traces.
-   All branches are preserved, even if not taken during tracing.
-   Dynamic shapes, metaprogramming, and Python idioms work naturally.
-   The rewriter only needs to understand control flow, not all of Python.

## 2\. CuTe DSL Compilation Flow: Meta-Stage to Object-Stage[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#dsl-compilation-flow-meta-stage-to-object-stage "Link to this heading")

CuTe DSL bridges Python and GPU hardware through a three-stage pipeline.

[![../../../../_images/dsl_modes.png](https://docs.nvidia.com/cutlass/latest/_images/dsl_modes.png)](https://docs.nvidia.com/cutlass/latest/_images/dsl_modes.png)

Figure 1 _Left_: tracing mode records only the path that executed. _Right_: preprocessor mode emits structured intermediate representation (IR) for every branch and loop before tracing the arithmetic.[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#id1 "Link to this image")

The default CuTe DSL compilation pipeline (mode 2): Python source flows through AST preprocessing and interpreter-driven tracing to produce intermediate representation (IR), which is then lowered and compiled to device code.

**Stage 1: Pre-Staging (Python AST)**

Before any code executes, the AST preprocessor rewrites the decorated function. It inserts _callbacks_ around control-flow constructs—loops, branches, and function boundaries—so that program structure is captured explicitly rather than lost during execution.

**Stage 2: Meta-Stage (Python Interpreter)**

The rewritten function runs in the Python interpreter with proxy tensor arguments. As execution proceeds:

-   Callbacks fire at control-flow boundaries, emitting structured intermediate representation (IR) (loops, branches, etc.).
-   Tensor operations are traced: each operator invocation records the corresponding operation.
-   Compile-time constants are _partially evaluated_—values known at JIT time fold directly into the intermediate representation (IR), enabling aggressive specialization.

The result is a complete representation of the kernel, with both high-level structure and low-level arithmetic intact.

**Stage 3: Object-Stage (Compiler Backend)**

The internal representation passes through a lowering pipeline:

1.  High-level operations are progressively lowered toward hardware-specific representations.
2.  Optimization passes (tiling, vectorization, memory promotion) reshape the code for the target architecture.
3.  The final code is translated to PTX/SASS (for NVIDIA GPUs) and assembled into a device binary.

At runtime, the compiled kernel is loaded and launched on the accelerator.

## 3\. Meta-Programming vs Runtime: Two Worlds in One Function[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#meta-programming-vs-runtime-two-worlds-in-one-function "Link to this heading")

A key insight for understanding CuTe DSL is that **your Python code runs twice**, in two very different contexts:

1.  **Meta-programming time (compilation)** — Python executes to _build_ the kernel. This happens on the host CPU when you call a `@jit` function.
2.  **Runtime (execution)** — The compiled kernel runs on the GPU with actual tensor data.

This distinction determines what you can observe and when.

### `print()` vs `cute.printf()`: Meta-Stage vs Object-Stage Output[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#print-vs-cute-printf-meta-stage-vs-object-stage-output "Link to this heading")

CuTe DSL provides two ways to print values, each operating at a different stage:

-   **Python’s** `print()` — executes during the **meta-stage** (compilation). Use it to inspect what the compiler sees.
-   `cute.printf()` — compiles into the kernel and executes at **runtime** on the GPU. Use it to observe actual tensor values during execution.

The following examples demonstrate how the same `result` variable appears differently depending on when and how you print it.

**Example 1: Dynamic variables (both** `a` **and** `b` **are runtime values)**

@cute.jit
def add\_dynamicexpr(b: cutlass.Float32):
    a \= cutlass.Float32(2.0)
    result \= a + b
    print("\[meta-stage\] result =", result)          \# runs at compile time
    cute.printf("\[object-stage\] result = %f\\n", result)  \# runs on GPU

add\_dynamicexpr(5.0)

Copy to clipboard

$> python myprogram.py
\[meta-stage\] result = <Float32 proxy>
\[object-stage\] result = 7.000000

Copy to clipboard

At meta-stage, `result` is a proxy—its value is unknown until the kernel runs. At runtime, `cute.printf()` prints the actual GPU-computed value.

**Example 2: Compile-time constants (both** `a` **and** `b` **are Constexpr)**

@cute.jit
def add\_constexpr(b: cutlass.Constexpr):
    a \= 2.0
    result \= a + b
    print("\[meta-stage\] result =", result)          \# runs at compile time
    cute.printf("\[object-stage\] result = %f\\n", result)  \# runs on GPU

add\_constexpr(5.0)

Copy to clipboard

$> python myprogram.py
\[meta-stage\] result = 7.0
\[object-stage\] result = 7.000000

Copy to clipboard

Both values are known at compile time, so Python evaluates `2.0 + 5.0 = 7.0` during tracing. The constant is baked into the compiled kernel.

**Example 3: Hybrid (** `a` **is dynamic,** `b` **is Constexpr)**

@cute.jit
def add\_hybrid(b: cutlass.Constexpr):
    a \= cutlass.Float32(2.0)
    result \= a + b
    print("\[meta-stage\] result =", result)          \# runs at compile time
    cute.printf("\[object-stage\] result = %f\\n", result)  \# runs on GPU

add\_hybrid(5.0)

Copy to clipboard

$> python myprogram.py
\[meta-stage\] result = <Float32 proxy>
\[object-stage\] result = 7.000000

Copy to clipboard

The constant `b = 5.0` is folded in, but since `a` is dynamic, the result remains a proxy at meta-stage. The GPU computes the final answer at runtime.

### Practical Implications[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#practical-implications "Link to this heading")

-   **Use** `print()` **to debug your meta-program** — inspect shapes, strides, tile sizes, and compile-time decisions.
-   **Constexpr parameters enable specialization** — the compiler can generate tighter code when values are known at JIT time.
-   **Dynamic parameters preserve generality** — a single compiled kernel can handle varying input sizes without recompilation.

## 4\. CuTe DSL Code-Generation Modes[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#dsl-code-generation-modes "Link to this heading")

CuTe’s Python front-end combines the techniques above into **two mutually exclusive modes** (see [Left: tracing mode records only the path that executed. Right: preprocessor mode emits structured intermediate representation (IR) for every branch and loop before tracing the arithmetic.](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html#fig-dsl-modes)), selectable with the `preprocessor` flag of the `@jit` decorator:

1\. Tracing mode `@jit(preprocess=False)` – tracing only. This results in the fastest compilation path and is recommended only for kernels that are guaranteed to be straight-line arithmetic. It suffers from all tracing limitations listed in the previous section.

2\. Preprocessor mode (**default**) `@jit(preprocess=True)` – **AST rewrite + tracing**. The AST pass captures every loop and branch, eliminating the correctness and optimisation problems of pure tracing; tracing then fills in the arithmetic. This hybrid “preprocessor” pipeline is unique to CuTe DSL and was designed specifically to overcome the disadvantages identified above.

# Control Flow[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#control-flow "Link to this heading")

## Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#overview "Link to this heading")

CuTe DSL walks Python’s AST and converts each control-flow construct it finds into structured intermediate representation (IR). You can therefore write ordinary Python loops and branches while the compiler decides—statement by statement—whether to

-   **evaluate at compile time** if it’s a native Python control flow, or
-   **emit intermediate representation (IR)** when the control flow is marked as dynamic.

Passing intermediate representation (IR) values to a native Python control flow will result in an error.

For a high-level discussion of the overall pipeline, see [the code-generation overview](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_code_generation.html).

## For Loops[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#for-loops "Link to this heading")

CuTe DSL recognises three kinds of ranges for `for` loops:

-   `range` – the Python built-in, always lowered to intermediate representation (IR)
-   `cutlass.range` - Same as Python built-in `range`, but supports advanced unrolling and pipelining control
-   `cutlass.range_constexpr` – unrolled at compile time

### range(…)/cutlass.range(…)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#range-cutlass-range "Link to this heading")

Use when you _always_ want a loop in the generated intermediate representation (IR), even if the inputs are Python values.

### cutlass.range\_constexpr(…)[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#cutlass-range-constexpr "Link to this heading")

Runs in the Python interpreter and is fully unrolled before code generation. All loop indices must be **Constexpr** (compile-time Python value).

**Example:**

@cute.jit
def control\_flow\_examples(bound: cutlass.Int32):
    n \= 10

    \# ✅ This loop is Python loop, evaluated at compile time.
    for i in cutlass.range\_constexpr(n):
        cute.printf("%d\\\\n", i)

    \# ✅ This loop is dynamic, even when bound is Python value.
    for i in range(n):
        cute.printf("%d\\\\n", i)

    \# ❌ This loop bound is a dynamic value, not allowed in Python loop.
    \# Should use \`range\` instead.
    for i in cutlass.range\_constexpr(bound):
        cute.printf("%d\\\\n", i)

    \# ✅ This loop is dynamic, emitted IR loop.
    for i in range(bound):
        cute.printf("%d\\\\n", i)

    \# ✅ This loop is dynamic, emitted IR loop with unrolling
    for i in cutlass.range(bound, unroll\=2):
        cute.printf("%d\\\\n", i)

Copy to clipboard

### Software Pipelining[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#software-pipelining "Link to this heading")

Software pipelining is a technique used to optimize loops. Typically, this involves writing a prefetch loop and a main loop.

@cute.jit
def example():
    ...
    \# build a circular buffer
    buffer \= ...

    \# prefetch loop
    for i in range(prefetch\_stages):
        cute.copy(atom, gmem\[i\], buffer\[i\], ...)

    \# main loop
    for i in range(bound):
        if i + prefetch\_stages < bound:
            cute.copy(atom, gmem\[i + prefetch\_stages\], buffer\[(i + prefetch\_stages) % total\_stages\], ...)

        use(buffer\[i % total\_stages\])

    ...

Copy to clipboard

This can be tedious to write and tune. CuTe DSL provides a loop attribute to ask the compiler to do this.

@cute.jit
def example():
    ...
    \# build a circular buffer
    buffer \= ...

    for i in cutlass.range(bound, prefetch\_stages\=prefetch\_stages):
        \# Compiler automatically handles the pipelining:
        \# - Generates prefetch loop for initial stages
        \# - In main loop, prefetches future data while using current data
        cute.copy(atom, gmem\[i\], buffer\[i % total\_stages\], ...)
        use(buffer\[i % total\_stages\])  \# Uses data from previous iterations

    ...

Copy to clipboard

Compiler will automatically generate the prefetch loop with prefetch\_stages iterations and a corresponding main loop.

This feature is experimental and only supported on sm90 and above.

## If-Else Statements[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#if-else-statements "Link to this heading")

Standard Python `if`/`elif`/`else` is supported.

-   **Predicate without annotation** → lowered to intermediate representation (IR).
-   **Predicate annotated with \`cutlass.const\_expr\`** → evaluated at compile time.

**Example:**

@cute.jit
def main(const\_var: cutlass.Constexpr, dynamic\_var: cutlass.Int32):
    \# ✅ This branch is Python branch, evaluated at compile time.
    if cutlass.const\_expr(const\_var):
        cute.printf("Const branch\\\\n")
    else:
        cute.printf("Const else\\\\n")

    \# ✅ This branch is dynamic branch, emitted IR branch.
    if dynamic\_var \== 10:
        cute.printf("Dynamic True\\\\n")
    else:
        cute.printf("Dynamic False\\\\n")

    \# ❌ Using a dynamic value with \`cutlass.const\_expr\` is not allowed.
    if cutlass.const\_expr(dynamic\_var \== 10):
        cute.printf("Bound is 10\\\\n")

Copy to clipboard

## While Loops[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#while-loops "Link to this heading")

Standard Python `while` is supported.

-   **Condition without annotation** → lowered to intermediate representation (IR).
-   **Condition annotated with \`cutlass.const\_expr\`** → evaluated at compile time.

**Example:**

@cute.jit
def main(dynamic\_var: cutlass.Int32):
    n \= 0

    \# ✅ This is Python while loop, evaluated at compile time.
    while cutlass.const\_expr(n < 10):
        cute.printf("Const branch\\\\n")
        n += 1

    \# ✅ This is dynamic while loop, emitted IR while loop.
    while dynamic\_var \== 10:
        cute.printf("Dynamic True\\\\n")
        n += 1

    \# ❌ Using a dynamic value with \`cutlass.const\_expr\` is not allowed.
    while cutlass.const\_expr(n < dynamic\_var):
        n += 1

Copy to clipboard

## Summary of Control Flow behavior[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#summary-of-control-flow-behavior "Link to this heading")

| **Control Flow** | **Run time evaluation** | **Compile time evaluation** |
| --- | --- | --- |
| if cutlass.const\\_expr() | ❌   | ✅   |
| if pred | ✅   | ❌   |
| while cutlass.const\\_expr() | ❌   | ✅   |
| while pred | ✅   | ❌   |
| for i in cutlass.range\\_constexpr() | ❌   | ✅   |
| for i in range() | ✅   | ❌   |
| for i in cutlass.range() (support advanced unrolling and pipelining) | ✅   | ❌   |

## Compile-Time Metaprogramming[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#compile-time-metaprogramming "Link to this heading")

Mix compile-time constructs with normal CuTe DSL code to generate specialised kernels without runtime overhead. A compile-time flag can, for example, toggle an optional **ReLU** epilogue:

@cute.kernel
def gemm(..., do\_relu: cutlass.Constexpr):
    \# main GEMM work
    ...
    if cutlass.const\_expr(do\_relu):    \# compile-time guard
        \# ReLU code is emitted only when do\_relu is True
        ...

Copy to clipboard

gemm(..., False)   # ReLU is omitted from the generated |IR|
gemm(..., True)    # ReLU is included

Copy to clipboard

### Limitations of Dynamic Control Flow[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html#limitations-of-dynamic-control-flow "Link to this heading")

-   Early-exit `break`, `continue`, `pass` or raising exception from control flow body are not yet supported.
-   Operations in the control flow body are traced only when tracing is active in that region.
-   Values originating in control flow body are not available outside the control flow.
-   Changing type of a variable in control flow body is not allowed.

**Example:**

@cute.jit
def control\_flow\_negative\_examples(predicate: cutlass.Boolean):
    n \= 10

    \# ❌ This loop is dynamic, early-exit isn't allowed.
    for i in range(n):
        if i \== 5:
            break         \# Early-exit

    if predicate:
        val \= 10
        \# ❌ return from control flow body is not allowed.
        return
        \# ❌ Raising exception from control flow body is not allowed.
        raise ValueError("This is not allowed")
        \# ❌ Using pass in control flow body is not allowed.
        pass

    \# ❌ val is not available outside the dynamic if
    cute.printf("%d\\\\n", val)

    if predicate:
        \# ❌ Changing type of a variable in control flow body is not allowed.
        n \= 10.0

# JIT Function Argument Generation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#jit-function-argument-generation "Link to this heading")

## In a nutshell[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#in-a-nutshell "Link to this heading")

When using the `@jit` or `@kernel` decorators to define a JIT-compiled function, the arguments to the function are traced to determine the JIT function’s signature. CuTe DSL provides a Pythonic way to write the arguments for JIT function as one normally would in Python, and the CuTe DSL will take care of the rest for you.

Specifically, CuTe DSL honors following when generating the JIT function’s arguments:

-   JIT function arguments are assumed to be **dynamic arguments** by default.
-   If an argument is explicitly type annotated with `cutlass.Constexpr`, it is treated as a **compile-time constant**.
-   If type annotation is provided, CuTe DSL validates the argument type at compile time for **type safety**.
-   CuTe DSL provides **runtime checkable protocols** (`JitArgument` and `DynamicExpression`) for generating JIT function arguments for customized types.

More details below for each of the above.

## Static argument vs. Dynamic argument[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#static-argument-vs-dynamic-argument "Link to this heading")

CuTe DSL supports both static and dynamic arguments for JIT functions.

1.  **Static arguments** hold values that are known at compile time. It is not included in the generated JIT function signature.
2.  **Dynamic arguments** hold values that are only known at runtime.

By default, CuTe DSL assumes dynamic arguments and tries to infer the argument types from the call-site argument types. An explicit type annotation `cutlass.Constexpr` can be used to specify a static argument.

import cutlass
import cutlass.cute as cute

@cute.jit
def foo(x: cutlass.Int32, y: cutlass.Constexpr):
    print("x = ", x)        \# Prints x = ?
    print("y = ", y)        \# Prints y = 2
    cute.printf("x: {}", x) \# Prints x: 2
    cute.printf("y: {}", y) \# Prints y: 2

foo(2, 2)

Copy to clipboard

In the example above, `x` is a dynamic argument with type cutlass.Int32 and `y` is a static argument.

With the `cutlass.Constexpr` annotation, a more sophisticated uses case of static argument in the JIT functions can be something like:

import cutlass
import cutlass.cute as cute

@cute.kernel
def kernel(
    self,
    tiled\_mma: cute.TiledMma,
    tma\_atom\_a: cute.CopyAtom,
    mA\_mkl: cute.Tensor,
    tma\_atom\_b: cute.CopyAtom,
    mB\_nkl: cute.Tensor,
    tma\_atom\_c: Optional\[cute.CopyAtom\],
    mC\_mnl: cute.Tensor,
    cluster\_layout\_vmnk: cute.Layout,
    a\_smem\_layout\_staged: cute.ComposedLayout,
    b\_smem\_layout\_staged: cute.ComposedLayout,
    c\_smem\_layout\_staged: Union\[cute.Layout, cute.ComposedLayout, None\],
    epi\_tile: cute.Tile,
    epilogue\_op: cutlass.Constexpr,
):
    ...

    \# Perform epilogue op on accumulator and convert to C type
    acc\_vec \= tTR\_rAcc.load()
    acc\_vec \= epilogue\_op(acc\_vec.to(self.c\_dtype))
    tTR\_rC.store(acc\_vec)

Copy to clipboard

In this example, `epilogue_op` is a static argument in the JIT kernel where the argument is used for the epilogue fusion. Upon calling the kernel, an elementwise lambda function can be passed in as the `epilogue_op` argument. For example, a ReLU can be applied for epilogue fusion by simply setting the `epilogue_op` to `lambda x: cute.where(x > 0, x, cute.full_like(x, 0))`

Refer to the [Blackwell dense GEMM example](https://github.com/NVIDIA/cutlass/tree/main/examples/python/CuTeDSL/blackwell/dense_gemm_persistent.py) for a complete example.

## Type safety[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#type-safety "Link to this heading")

CuTe DSL makes good use of type annotation in JIT function signature and validates the JIT function argument types at compile time for **type safety**.

import cutlass
import cutlass.cute as cute
import numpy as np

@cute.jit
def foo(x: cute.Tensor, y: cutlass.Float16):
    ...

a \= np.random.randn(10, 10).astype(np.float16)
b \= 32

foo(a, b)
foo(b, a)  \# This will fail at compile time due to type mismatch

Copy to clipboard

The type safety check helps catch the type mismatch issue early at the compile time with clear error message to avoid tricky runtime errors which is usually more expensive to debug. In the example above, the second call to `foo` will fail at compile time due to the type mismatch with a clear error message:

cutlass.base\_dsl.common.DSLRuntimeError: DSLRuntimeError: expects argument #1 (a) to be <class 'cutlass.cute.typing.Tensor'>, but got <class 'int'>

Copy to clipboard

## JIT function arguments with customized types[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#jit-function-arguments-with-custom-types "Link to this heading")

CuTe DSL supports customized types for JIT function arguments by providing two runtime checkable protocols:

-   `JitArgument` which is used for host JIT functions to be called from Python.
    
    -   `__c_pointers__`: Generate a list of ctypes pointers for the current object.
    -   `__get_mlir_types__`: Generate a list of MLIR types for the current object.
    -   `__new_from_mlir_values__`: Create a new object from MLIR values.
    
-   `DynamicExpression` which is used for device JIT functions to be called from the host JIT functions.
    
    -   `__extract_mlir_values__`: Generate a dynamic expression for the current object.
    -   `__new_from_mlir_values__`: Create a new object from MLIR values.
    

Refer to [typing.py](https://github.com/NVIDIA/cutlass/tree/main/python/CuTeDSL/base_dsl/typing.py) for more details on these protocol APIs.

Depending on different cases of the customized types, CuTe DSL provides easy ways to adopt customized types for JIT function arguments.

### 1\. Direct protocol implementation in customized types[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#direct-protocol-implementation-in-custom-types "Link to this heading")

One way is to implement the protocol methods directly in the customized types to enable the protocol based JIT function argument generation.

import cutlass
import cutlass.cute as cute

\# Customized type that implements the DynamicExpression protocol
class MyDynamicExpression:
    def \_\_init\_\_(self, tensor, offset):
        self.\_tensor \= tensor \# Dynamic argument
        self.\_offset \= offset \# Dynamic argument

    def \_\_extract\_mlir\_values\_\_(self):
        return \[self.\_tensor.\_\_extract\_mlir\_values\_\_(), self.\_offset.\_\_extract\_mlir\_values\_\_()\]

    def \_\_new\_from\_mlir\_values\_\_(self, values):
        return MyDynamicExpression(values\[0\], values\[1\])

@cute.kernel
def my\_kernel(x: MyDynamicExpression):
    ...

Copy to clipboard

In the example above, the `MyDynamicExpression` implements the `DynamicExpression` protocol and CuTe DSL will generate the JIT function arguments for the JIT kernel `my_kernel` based on the protocol methods.

### 2\. Adaptor based protocol implementation for customized types[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html#adaptor-based-protocol-implementation-for-custom-types "Link to this heading")

For the case where directly changing the customized types to implement the protocol is not feasible, CuTe DSL provides adaptor based approach to adapt the customized types for JIT function argument generation.

The JIT function argument adaptor is a callable object that implements the desired protocol methods for the registered customized types. This way, CuTe DSL automatically queries the JIT argument adaptor registry to generate the JIT function arguments for the given customized types.

@cutlass.register\_jit\_arg\_adapter(MyFrameworkObject)
class MyFrameworkObjectAdapter:
    """
    Convert a 3rd party framework object to a JIT function argument with JitArgument protocol
    """

    def \_\_init\_\_(self, arg):
        self.\_arg \= arg

    def \_\_c\_pointers\_\_(self):
        \# Convert the framework object to a C-ABI compatible object
        \# thru its C-ABI interface
        return \[self.\_arg.get\_cabi\_pointer()\]

    def \_\_get\_mlir\_types\_\_(self):
        \# Return the list of MLIR types the framework object represents
        return \[self.\_arg.get\_data().mlir\_type\]

    def \_\_new\_from\_mlir\_values\_\_(self, values):
        \# Convert the MLIR values back to the framework object
        return MyFrameworkObject(values\[0\])

Copy to clipboard

In this example, the `MyFrameworkObjectAdapter` implements an adaptor class which bridges the CuTe DSL and the 3rd party framework type `MyFrameworkObject`. The registration is done by just decorating the adaptor with `cutlass.register_jit_arg_adapter` for the customized type. With the registered adaptor, CuTe DSL will automatically use the adaptor to generate the JIT function arguments for `MyFrameworkObject` typed arguments.

# Static vs Dynamic layouts[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_dynamic_layout.html#static-vs-dynamic-layouts "Link to this heading")

## Static Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_dynamic_layout.html#static-layout "Link to this heading")

When integrating with popular deep learning frameworks, one question is how to deal with the layout of the converted `cute.Tensor`. For example, when converting a `torch.Tensor` to a `cute.Tensor`, the shape of the `torch.Tensor` is honored for the layout of `cute.Tensor`.

import torch
import cutlass
from cutlass.cute.runtime import from\_dlpack

@cute.jit
def foo(tensor):
    print(f"tensor.layout: {tensor.layout}")  \# Prints tensor layout at compile time
    cute.printf("tensor: {}", tensor)         \# Prints tensor values at runtime

Copy to clipboard

In this example, we define a JIT function `foo` that takes a `cute.Tensor` as input and prints its layout. Note that Python print is used to print the layout at compile time. This works fine for static layout whose value is known at compile time.

Now let’s try to run the JIT function `foo` with different shapes of the input `torch.Tensor`.

a \= torch.tensor(\[1, 2, 3\], dtype\=torch.uint16)
a\_pack \= from\_dlpack(a)
compiled\_func \= cute.compile(foo, a\_pack)
compiled\_func(a\_pack)

Copy to clipboard

Here we first convert a 1D `torch.Tensor` with 3 elements to a `cute.Tensor` using `from_dlpack`. Then we compile the JIT function `foo` with the converted `cute.Tensor` and call the compiled function.

  tensor.layout: (3):(1)
  tensor: raw\_ptr(0x00000000079e5100: i16, generic, align<2>) o (3):(1) =
( 1, 2, 3 )

Copy to clipboard

It prints `(3):(1)` for the layout because the converted `cute.Tensor` has a static layout with shape `(3)` which is the shape of the `a`.

Now if we call the compiled function with a different shape of the input `torch.Tensor`, it would result in an unexpected result at runtime due to the mismatch of the type since `compiled_func` expects a `cute.Tensor` with layout `(3):(1)` while `b` has shape `(5)`.

b \= torch.tensor(\[11, 12, 13, 14, 15\], dtype\=torch.uint16)
b\_pack \= from\_dlpack(b)
compiled\_func(b\_pack)  \# ❌ This results in an unexpected result at runtime due to type mismatch

Copy to clipboard

Following is the output which is unexpected due to the type mismatch.

  tensor: raw\_ptr(0x00000000344804c0: i16, generic, align<2>) o (3):(1) =
( 11, 12, 13 )

Copy to clipboard

To fix that, we would have to trigger another code generation and compilation for the new shape for `b`.

compiled\_func\_2 \= cute.compile(foo, b\_pack)  \# This would trigger another compilation
compiled\_func\_2(b\_pack)                      \# ✅ Now this works fine

Copy to clipboard

As shown in the example above, with the newly compiled `compiled_func_2`, we can pass in `b_pack` to the compiled JIT function `compiled_func_2`.

  tensor.layout: (5):(1)
  tensor: raw\_ptr(0x0000000034bb2840:: i16, generic, align<2>) o (5):(1) =
( 11, 12, 13, 14, 15 )

Copy to clipboard

Now it recompiles and prints the values of `b` correctly.

It’s obvoius that we need distinct codes generated and compiled for different static layout. In this case, one for layout `(3):(1)` and the other for layout `(5):(1)`.

## Dynamic Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_dynamic_layout.html#dynamic-layout "Link to this heading")

In order to avoid generating and compiling multiple times for different shapes of the input `torch.Tensor`, CuTe DSL provides a way to generate and compile JIT function with dynamic layout.

To get dyanmic layout of the `cute.Tensor`, a `torch.Tensor` object can be passed into the JIT function directly which instructs CuTe DSL to call `cute.mark_layout_dynamic` automatically on the converted `cute.Tensor` per the leading dimension of the layout.

import torch
import cutlass
from cutlass.cute.runtime import from\_dlpack

@cute.jit
def foo(tensor):
    print(tensor.layout)  \# Prints (?,?):(?,1) for dynamic layout

a \= torch.tensor(\[\[1, 2\], \[3, 4\]\], dtype\=torch.uint16)
compiled\_func \= cute.compile(foo, a)
compiled\_func(a)

b \= torch.tensor(\[\[11, 12\], \[13, 14\], \[15, 16\]\], dtype\=torch.uint16)
compiled\_func(b)  \# Reuse the same compiled function for different shape

Copy to clipboard

In the example above, a single compilation of the JIT function `foo` is reused for different shapes of the input `torch.Tensor`. This is possible because the converted `cute.Tensor` has a dynamic layout `(?,?):(?,1)` which is compatible with the shape of the input `torch.Tensor` of both calls.

Alternatively, for compact layout, `cute.mark_compact_shape_dynamic` can be called for a finer-grained control to specify the mode of the layout for dynamic and the divisibility constraint for the dynamic dimension.

Refer to [Integration with Frameworks](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html) for more details on `from_dlpack`, `mark_layout_dynamic`, and `mark_compact_shape_dynamic`.

## Static Layout vs. Dynamic Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_dynamic_layout.html#static-layout-vs-dynamic-layout "Link to this heading")

Per the previous sections, we have seen that static layout leads to distinct JIT code generations while dynamic layout leads to a single compilation for different shapes.

That said, creating JIT function with static layout is useful when the use cases targeting input data with fixed shapes. Since more information is available at compile time, the compiler would be able to kick in optimizations that otherwise would not be possible for the code generated for dynamic layout.

On the other hand, dynamic layout would be more flexible for the cases where the input data has varying shapes. This provides more scalability of the generated code to deal with varying input data of different shapes.

## Programming with Static and Dynamic Layout[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_dynamic_layout.html#programming-with-static-and-dynamic-layout "Link to this heading")

CuTe DSL provides intuitive way to program with static and dynamic layout in the codes.

import torch
import cutlass
from cutlass.cute.runtime import from\_dlpack

@cute.jit
def foo(tensor, x: cutlass.Constexpr\[int\]):
    print(cute.size(tensor))  \# Prints 3 for the 1st call
                              \# Prints ? for the 2nd call
    if cute.size(tensor) \> x:
        cute.printf("tensor\[2\]: {}", tensor\[2\])
    else:
        cute.printf("tensor size <= {}", x)

a \= torch.tensor(\[1, 2, 3\], dtype\=torch.uint16)
foo(from\_dlpack(a), 3)   \# First call with static layout

b \= torch.tensor(\[1, 2, 3, 4, 5\], dtype\=torch.uint16)
foo(b, 3)                \# Second call with dynamic layout

Copy to clipboard

In this example, the JIT function `foo` is compiled with a static layout `(3):(1)` for the first call, which means the size of the tensor is known at compile time. CuTe DSL makes good use of this and automatically handles the if condition at the compile time. Hence the generated codes are efficient without the if condition at all.

For the second call, the JIT function `foo` is compiled with a dynamic layout `(?):(1)` hence the tensor size is only evaluated at runtime. CuTe DSL automatically generates the code to handle the dynamic layout and the if condition at runtime.

The same applies to loop as well:

@cute.jit
def foo(tensor, x: cutlass.Constexpr\[int\]):
    for i in range(cute.size(tensor)):
        cute.printf("tensor\[{}\]: {}", i, tensor\[i\])

a \= torch.tensor(\[1, 2, 3\], dtype\=torch.uint16)
foo(from\_dlpack(a), 3)   \# First call with static layout

b \= torch.tensor(\[1, 2, 3, 4, 5\], dtype\=torch.uint16)
foo(b, 3)                \# Second call with dynamic layout

Copy to clipboard

With the static layout in the first call, CuTe DSL is able to fully unroll the loop at compile time. While in the second call, the generated codes will have the loop executed at runtime based on the dynamic layout.

With the single JIT function implementation, CuTe DSL is able to handle control-flow constructs and automatically generate the optimized codes for different cases. This is all possible because CuTe DSL is able to walk the Python AST and convert each control-flow construct it finds accordingly.

Please refer to [Control Flow](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_control_flow.html) for more details.

[

](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_arg_generation.html "previous page")

# JIT Caching[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_caching.html#jit-caching "Link to this heading")

## Zero Compile and JIT Executor[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_caching.html#zero-compile-and-jit-executor "Link to this heading")

Zero Compile is a feature that enables explicit kernel compilation on demand through `cute.compile`. When `cute.compile` is called, it compiles the kernel and returns a JIT Executor instance. This JIT Executor instance can be cached and reused directly for subsequent executions without compiling the kernel again.

The JIT Executor is a component that independently executes compiled code. It can be created either through `cute.compile` or implicit compilation. The JIT Executor instance behaves like a callable object to execute the compiled code. Each JIT Executor instance maintains a single compiled host function.

It encompasses all necessary execution components:

-   Host function pointer and its MLIR execution engine
-   CUDA modules (optional)
-   Argument specifications defining how Python arguments are converted to C ABI-compatible types. Note that arguments with the `cutlass.Constexpr` hint are excluded from argument specifications since they are evaluated at compile time rather than runtime.

For example, in the following code, `print_result` is a `cutlass.Constexpr` value that is **NOT** evaluated at runtime:

import cutlass.cute as cute

@cute.jit
def add(a, b, print\_result: cutlass.Constexpr):
   if print\_result:
      cute.printf("Result: %d\\n", a + b)
   return a + b

jit\_executor \= cute.compile(add, 1, 2, True)

jit\_executor(1, 2) \# output: \`\`Result: 3\`\`

Copy to clipboard

The JIT Executor ensures all components are properly initialized and loaded after compilation.

For example, all CUDA modules are loaded (via `cuModuleLoad`) and kernel function pointers are extracted (via `cuModuleGetFunction`).

When calling a JIT Executor instance, it:

-   Parses Python runtime arguments and converts them to C ABI-compatible types according to argument specifications
-   Invokes the host function with the converted arguments

### Custom Caching with `cute.compile`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_caching.html#custom-caching-with-cute-compile "Link to this heading")

`cute.compile` bypasses caching in CuTe DSL and always performs compilation, returning a fixed JIT Executor instance. This allows implementing custom caching strategies as shown below:

@cute.jit
def add(b):
   return a + b

\# Define a custom cache
custom\_cache \= {}

a \= 1
compiled\_add\_1 \= cute.compile(add, 2)
custom\_cache\[1\] \= compiled\_add\_1
compiled\_add\_1(2) \# result = 3

a \= 2
compiled\_add\_2 \= cute.compile(add, 2)
custom\_cache\[2\] \= compiled\_add\_2
compiled\_add\_2(2) \# result = 4

\# Use the custom cache
custom\_cache\[1\](2) \# result = 3
custom\_cache\[2\](2) \# result = 4

Copy to clipboard

## Cache in CuTe DSL[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_caching.html#cache-in-dsl "Link to this heading")

By default, cache in CuTe DSL is implicitly enabled to avoid recompilation when kernels are called repeatedly without changes.

The cache is implemented as a map storing compiled JIT Executor instances within CuTe DSL.

The cache key combines hashes of:

-   MLIR bytecode of the MLIR program generated by CuTe DSL
-   All CuTe DSL Python source files
-   All CuTe DSL shared libraries
-   All CuTe DSL environment variables

The cache value is a compiled JIT Executor instance.

On a cache hit, compilation is skipped and the cached JIT Executor instance is reused.

On a cache miss, the kernel is compiled and the new JIT Executor instance is stored in the cache.

Here is an example demonstrating automatic caching of the `add` kernel:

\# Global variable
a \= 1

@cute.jit
def add(b):
   return a + b

\# Cache is empty at beginning

\# First call: cache miss triggers compilation
result \= add(2) \# result = 3
\# Cache now has one instance

\# Second call: cache hit reuses cached JIT Executor
result \= add(2) \# result = 3

a \= 2
\# Third call: cache miss due to changed IR code triggers recompilation
result \= add(2) \# result = 4
\# Cache now has two instances

Copy to clipboard

The cache can be serialized to files for subsequent runs. After serialization, compiled MLIR bytecode is stored in file. The cache directory is `/tmp/{current_user}/cutlass_python_cache`. During compilation, the cache loads the corresponding kernel from file (if it exists) into memory as needed, and after compilation, it saves any newly compiled executables back to file.

Note that for efficiency, the default cache directory is located in a temporary folder. However, this location is not persistent, it may be cleared by the system (for example, during a reboot or disk space cleanup). If you wish to preserve the cache across sessions, set the `CUTE_DSL_CACHE_DIR` environment variable to point to a persistent directory.

The following environment variables control file caching:

\# Disable file caching while keeping in-memory cache available, defaults to False.
export CUTE\_DSL\_DISABLE\_FILE\_CACHING\=True

\# Cache directory, defaults to /tmp/{current\_user}/cutlass\_python\_cache.
export CUTE\_DSL\_CACHE\_DIR\=/home/user/local\_cutlass\_python\_cache/dense\_gemm\_cache/

Copy to clipboard

### Limitations[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_caching.html#limitations "Link to this heading")

The intention of caching is to reduce the host launch overhead before each execution. As above example shows, the consistency between the original Python code and the MLIR program is hard to maintain because of the impact of dynamic factors such as global variables. Therefore, the MLIR program **MUST** always be generated to verify that the kernel content matches what was previously built.

For optimal host launch latency, we recommend using above custom caching method with `cute.compile`.

# JIT Compilation Options[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_compilation_options.html#jit-compilation-options "Link to this heading")

## JIT Compilation Options Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_compilation_options.html#jit-compilation-options-overview "Link to this heading")

When compiling a JIT function using CuTe DSL, you may want to control various aspects of the compilation process, such as optimization level, or debugging flags. CuTe DSL provides a flexible interface for specifying these compilation options when invoking `cute.compile`.

Compilation options allow you to customize how your JIT-compiled functions are built and executed. This can be useful for:

-   Enabling or disabling specific compiler optimizations
-   Generating debug information for troubleshooting

These options can be passed as keyword arguments to `cute.compile` or set globally for all JIT compilations. The available options and their effects are described in the following sections, along with usage examples to help you get started.

The CuTe DSL provides multiple ways to specify compilation options - either by specifying additional arguments to `cute.compile` or by using a more Pythonic approach with separate Python types for `cute.compile`.

## `cute.compile` Compilation Options as strings[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_compilation_options.html#cute-compile-compilation-options-as-strings "Link to this heading")

You can provide additional compilation options as a string when calling `cute.compile`. The CuTe DSL uses `argparse` to parse these options and will raise an error if any invalid options are specified.

| **Option** | **Description** | **Default** | **Type** |
| --- | --- | --- | --- |
| `opt-level` | Optimization level of compilation. The higher the level, the more optimizations are applied. The valid value range is \\[0, 3\\]. | 3 (highest level of optimization) | int |
| `enable-assertions` | Enable host and device code assertions. | False | bool |
| `keep-cubin` | Keep the generated CUBIN file. | False | bool |
| `keep-ptx` | Keep the generated PTX file. | False | bool |
| `ptxas-options` | The options to pass to the PTX Compiler library. | “”  | str |
| `generate-line-info` | Generate line information for debugging. | False | bool |
| `gpu-arch` | The GPU architecture to compile for. | “”  | str |
| `enable-tvm-ffi` | Enable Apache TVM FFI. | False | bool |

You can use the following code to specify compilation options:

jit\_executor\_with\_opt\_level\_2 \= cute.compile(add, 1, 2, options\="--opt-level 2")
jit\_executor\_with\_opt\_level\_1 \= cute.compile(add, 1, 2, options\="--opt-level 1")
jit\_executor\_with\_enable\_assertions \= cute.compile(add, 1, 2, options\="--enable-assertions")
jit\_executor\_with\_keep\_cubin \= cute.compile(add, 1, 2, options\="--keep-cubin")
jit\_executor\_with\_keep\_ptx \= cute.compile(add, 1, 2, options\="--keep-ptx")
jit\_executor\_with\_ptxas\_options \= cute.compile(add, 1, 2, options\="--ptxas-options '--opt-level=2'")

Copy to clipboard

## `cute.compile` Compilation Options as separate Python types[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_compilation_options.html#cute-compile-compilation-options-as-separate-python-types "Link to this heading")

Alternatively, you can also use a more Pythonic way to specify compilation options with separate Python types. Compilation options can be programmatically composed using tuple and passed to `cute.compile` separately.

from cutlass.cute import OptLevel, EnableAssertions, GenerateLineInfo, KeepCUBIN, KeepPTX

my\_debugging\_options \= (OptLevel(1), EnableAssertions, GenerateLineInfo, KeepCUBIN, KeepPTX)
compiled\_kernel\_1 \= cute.compile\[my\_debugging\_options\](my\_kernel\_1, ...)
compiled\_kernel\_2 \= cute.compile\[my\_debugging\_options\](my\_kernel\_2, ...)

Copy to clipboard

This approach causes invalid options to raise errors immediately, making it much easier to detect typos when specifying multiple options. Notebly, boolean options are automatically converted to True instances of the option type for convenience.

jit\_executor\_with\_opt\_level\_2 \= cute.compile\[OptLevel(2)\](add, 1, 2)
jit\_executor\_with\_opt\_level\_1 \= cute.compile\[OptLevel(1)\](add, 1, 2)
jit\_executor\_with\_enable\_assertions \= cute.compile\[EnableAssertions\](add, 1, 2)
jit\_executor\_with\_keep\_cubin \= cute.compile\[KeepCUBIN\](add, 1, 2)
jit\_executor\_with\_keep\_ptx \= cute.compile\[KeepPTX\](add, 1, 2)
jit\_executor\_with\_ptxas\_options \= cute.compile\[PtxasOptions("--opt-level=2")\](add, 1, 2)


# Integration with Frameworks[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#integration-with-frameworks "Link to this heading")

In order to facilitate the integration of CUTLASS Python with popular frameworks, we leverage the [DLPack protocol](https://github.com/dmlc/dlpack) and transform tensors originating from these frameworks to CuTe tensors. The present page documents the conventions, the API available to the user, and provide example code snippets for common usage patterns. We also provide a section on how to bypass the DLPack protocol and directly call the JIT function.

## Implicit Conversion[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#implicit-conversion "Link to this heading")

Tensors originating from frameworks supporting the DLPack protocol can be directly provided to a JIT function as a regular parameter. CuTe DSL’s runtime implicitly converts the original tensor to a CuTe tensor with a fully dynamic layout except for the stride element corresponding to the leading dimension. The example below demonstrates this use case.

import torch
import cutlass.cute as cute

@cute.jit
def foo(src):
    """
    The following lines print

    ptr<f32, generic> o (?,?,?):(?,?,1)
    <class 'cutlass.cute.core.\_Tensor'>
    """
    print(src)
    print(type(src))

a \= torch.randn(30, 20, 32, device\="cpu")
foo(a)

Copy to clipboard

## Explicit conversion using `from_dlpack`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#explicit-conversion-using-from-dlpack "Link to this heading")

CuTe DSL’s runtime provides an interface for converting DLPack-compatible tensors to CuTe tensors,

b \= cute.runtime.from\_dlpack(a)

Copy to clipboard

where `a` is a tensor supporting the DLPack protocol with the `__dlpack__` and `__dlpack_device__` methods. The resulting CuTe tensor `b` has a fully static layout. This conversion is performed without copying any tensor data, enabling seamless integration with major frameworks. Users can create tensors using NumPy, PyTorch, etc. and directly feed them into JIT functions writtnen using CuTe DSL.

The resulting CuTe tensor shares the same underlying memory buffer as the original tensor. This zero-copy approach maximizes performance by eliminating unnecessary data duplication. However, it is important to note that the CuTe tensor’s validity is tied to the lifetime of the original tensor. If the source tensor is destroyed or goes out of scope, the corresponding CuTe tensor becomes invalid since it references the original memory location.

The full signature of from\_dlpack is as follows:

def from\_dlpack(tensor, assumed\_align\=None, use\_32bit\_stride\=False):

Copy to clipboard

The `assumed_align` integer parameter specifies the alignment of the tensor in unit of bytes. The tensor’s base address must be divisible by `assumed_align`. When not provided explicitly, the alignment is set to the natural alignment of the tensor’s element type. Note that the alignment information is part of the pointer type in the generated IR. Therefore, programs with different alignments have a different IR and identical IRs are required for hitting the kernel caching mechanism of CuTe DSL.

The `use_32bit_stride` parameter determines whether to use 32-bit stride for the tensor’s dynamic stride values. By default, it is set to False (64bit) to ensure that address calculations do not risk overflow. For smaller problem sizes (where `cosize(layout_of_tensor) <= Int32_MAX`), users may set it to True (32bit) to improve performance by reducing register usage and the number of address calculation instructions. When `use_32bit_stride` is set to True, a runtime check is performed to ensure that the layout does not overflow. Please note that this parameter only has an effect when the tensor’s layout is marked as dynamic.

### Code Example[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#code-example "Link to this heading")

The following code demonstrates how to convert a PyTorch tensor to a CuTe tensor using the `from_dlpack` function with default parameters.

import torch
import cutlass
from cutlass.cute.runtime import from\_dlpack

x \= torch.randn(30, 20, device\="cpu")
y \= from\_dlpack(x)

Copy to clipboard

Once converted, we can access the tensor’s information through various attributes. The following list shows the attributes of the converted tensor:

-   `tensor.shape`: the tensor’s shape
-   `tensor.stride`: the tensor’s stride
-   `tensor.memspace`: the tensor’s memory space
-   `tensor.element_type`: the tensor’s element data type

import torch
import cutlass
from cutlass.cute.runtime import from\_dlpack

x \= torch.randn(30, 20, device\="cpu")
y \= from\_dlpack(x)

print(y.shape)        \# (30, 20)
print(y.stride)       \# (20, 1)
print(y.memspace)     \# generic (if torch tensor in on device memory, memspace will be gmem)
print(y.element\_type) \# Float32
print(y)              \# Tensor<0x000000000875f580@generic o (30, 20):(20, 1)>

Copy to clipboard

The string format of the resulting CuTe tensor is

Tensor<0x{tensor.data\_ptr:016x}@{tensor.memspace} o {tensor.shape}:{tensor.stride}>

Copy to clipboard

As can be seen in the example above, `from_dlpack` first results in a tensor with a static layout. To obtain dynamic or mixed static/dynamic layouts after calling `from_dlpack`, the `mark_layout_dynamic` and `mark_compact_shape_dynamic` functions are used and described in the following sections.

### When to Use Explicit Conversion?[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#when-to-use-explicit-conversion "Link to this heading")

The DLPack protocol is a widely used protocol for interoperability between different frameworks. However, there is some associated overhead. Based on our benchmark, it usually takes between 2 to 3 us per call to `from_dlpack`.

Explicit conversion allows for caching the converted CuTe tensors in order to avoid the overhead of repeated calls to `from_dlpack`.

x \= torch.randn(30, 20, device\="cpu")
if key not in cached\_tensors:
    \# Do the conversion only for cache misses
    cached\_tensors\[key\] \= cute.runtime.from\_dlpack(x)
foo(cached\_tensors\[key\])

Copy to clipboard

Another use case for explicit conversion is to gain fine-grain control over which modes of a tensor are considered dynamic from the perspective of the generated program.

## Mark the Tensor’s Layout as Dynamic with `mark_layout_dynamic`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#mark-the-tensor-s-layout-as-dynamic-with-mark-layout-dynamic "Link to this heading")

After calling this function, all shape modes become dynamic. The stride modes also become dynamic with the following two exceptions:

1.  the leading dimension’s stride remains fixed at 1;
2.  stride elements equal to 0 (which indicates broadcasting) are retained.

The full signature of `mark_layout_dynamic` is as follows:

def mark\_layout\_dynamic(self, leading\_dim: int|None \= None):

Copy to clipboard

The `leading_dim` parameter specifies the leading dimension of the tensor. The leading dimension’s stride is set to 1 unless inconsistent with the layout of the DLPack tensor. For example,

-   For a tensor with layout `(2,2,3,4):(2,1,4,12)`, if `leading_dim` is specified to be 1, the layout will be marked as `(?,?,?,?):(?,1,?,?)`.
-   If `leading_dim` is specified to be 0, a deduction failure error is raised because the stride of dimension 0 is 2 (not 1).

The default value for `leading_dim` is `None`. In such case, the system automatically deduces it from the tensor’s layout using the following logic:

1.  If exactly one dimension has stride 1, that dimension is the leading dimension.
2.  If multiple dimensions have stride 1, deduction succeeds only when exactly one of them has size > 1 (that dimension is used). If none or more than one has size > 1, an error is raised. Note that after converting a **PyTorch** tensor to the DLPack format, the stride for dimensions with size 1 are canonicalized to 1, which can produce multiple stride-1 dimensions.
3.  If no dimension has stride 1, all strides remain dynamic.

For example:

-   For a tensor with layout `(2,2,3,4):(2,1,4,12)`, the leading dimension is 1. The layout will be marked as `(?,?,?,?):(?,1,?,?)`.
-   For a tensor with layout `(1,5,1):(1,1,1)`, multiple dimensions have stride 1 but exactly one has size > 1 (dim 1). The leading dimension is deduced to be 1: `(?,?,?):(?,1,?)`.
-   For a tensor with layout `(2,2):(8,2)`, no dimension has stride 1, so all strides remain dynamic: `(?,?):(?,?)`.

The leading dimension accepts negative index which means the dimension is counted from the last dimension. For example,

-   For a tensor with layout `(2,2,3,4):(2,1,4,12)`, if `leading_dim` is specified to be -1, the layout will be marked as `(?,?,?,?):(?,?,?,1)`.

### Code Example[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#id1 "Link to this heading")

The following example demonstrates how to use `mark_layout_dynamic` to specify dynamic tensor layouts.

-   `t0` shows the usage of `mark_layout_dynamic` with unspecified `leading_dim` and the automatic deduction of leading dimension.
-   `t1` & `t2` shows the usage of `mark_layout_dynamic` with specified `leading_dim`.
-   `t3` shows the usage of `mark_layout_dynamic` with no leading dimension.
-   `t4` shows the usage of `mark_layout_dynamic` with broadcasted dimensions.
-   `t5` shows automatic deduction for tensor `b` (multiple stride-1, exactly one has size > 1 → dim 1).
-   `t5_fail` demonstrates the deduction failure when multiple dimensions have stride 1 but none has size > 1.
-   `t6` & `t7` demonstrate incorrect settings for `leading_dim` and expected errors.

import torch
from cutlass.cute.runtime import from\_dlpack

\# (8,4,16,2):(2,16,64,1)
a \= torch.empty(16, 4, 8, 2).permute(2, 1, 0, 3)
\# (1,4,1,32,1):(4,1,4,4,4) => torch tensor when dimension has shape 1, its stride is degenerated to 1,
\# resulting in (1,4,1,32,1):(1,1,1,4,1)
b \= torch.empty(32, 1, 1, 1, 4).permute(3, 4, 1, 0, 2)
\# (2,2):(8,2)
c \= torch.empty(3, 4)\[::2, ::2\]
\# (3,1,1,5):(5,0,0,1)
d \= torch.empty(3, 1, 1, 5).expand(3, 4, 2, 5)

\# auto deduce the leading dimension to be 3
t0 \= from\_dlpack(a).mark\_layout\_dynamic()
print(t0)
\# (?,?,?,?):(?,?,?,1)

t1 \= from\_dlpack(b).mark\_layout\_dynamic(leading\_dim\=0)
print(t2)
\# (?,?,?,?,?):(1,?,?,?,?)

t2 \= from\_dlpack(b).mark\_layout\_dynamic(leading\_dim\=2)
print(t3)
\# (?,?,?,?,?):(?,?,1,?,?)

t3 \= from\_dlpack(c).mark\_layout\_dynamic()
print(t3)
\# (?,?):(?,?)

t4 \= from\_dlpack(d).mark\_layout\_dynamic()
print(t4)
\# (?,?,?,?):(?,0,0,1)

\# b has layout (1,4,1,32,1):(1,1,1,4,1); dim 1 has size > 1, so deduction succeeds to dim 1.
t5 \= from\_dlpack(b).mark\_layout\_dynamic()
print(t5)
\# (?,?,?,?,?):(?{i64},1,?{i64},?{i64},?{i64})

\# Rejected: multiple stride-1, none with size > 1 (e.g. torch.ones(1,1,1)).
t5\_fail \= from\_dlpack(torch.ones(1, 1, 1)).mark\_layout\_dynamic()
\# Can't deduce the leading dimension from layout (multiple dimensions have stride 1 but none has size > 1)...

t6 \= from\_dlpack(a).mark\_layout\_dynamic(leading\_dim\=1)
\# Expected strides\[leading\_dim\] == 1, but got 16

t7 \= from\_dlpack(b).mark\_layout\_dynamic(leading\_dim\=3)
\# Expected strides\[leading\_dim\] == 1, but got 4

c \= torch.empty(1000000000, 1000000000)
t8 \= from\_dlpack(c, use\_32bit\_stride\=True).mark\_layout\_dynamic()
\# Layout in DLTensorWrapper has int32 overflow risk. Please set use\_32bit\_stride to False.

Copy to clipboard

## Mark the Tensor’s Layout as Dynamic with `mark_compact_shape_dynamic`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#mark-the-tensor-s-layout-as-dynamic-with-mark-compact-shape-dynamic "Link to this heading")

The `mark_compact_shape_dynamic` function provides fine-grain control over dynamic shapes for compact layouts. The full signature of `mark_compact_shape_dynamic` is as follows:

def mark\_compact\_shape\_dynamic(self, mode: int, stride\_order: tuple\[int, ...\]|None \= None, divisibility: int \= 1):

Copy to clipboard

The `mode` parameter determines which shape dimension becomes dynamic. After calling this function, the specific shape dimension given by `mode` is marked as dynamic immediately. The stride will be updated accordingly. For modes that have a shape of size 1, their stride are canonicalized to 0.

The `stride_order` parameter specifies the ordering of strides in the tensor. It is consistent with `torch.Tensor.dim_order()` and defaults to `None`. The parameter indicates the order of modes (dimensions) if the current layout were to be converted to row-major order. It starts from the outermost to the innermost dimension when reading it from left to right. This parameter must be explicitly set when the stride order cannot be automatically deduced from the tensor’s layout, such as when multiple dimensions have a stride of 1.

For example:

-   Layout `(4,2):(1,4)` has a `stride_order` of `(1,0)` indicates the innermost dimension is 0 (`4:1`), the outermost dimension is 1 (`2:4`).
-   Layout `(5,3,2,4):(3,1,15,30)` has a `stride_order` of `(3,2,0,1)` indicates the innermost dimension is 1 (`3:1`), the outermost dimension is 3 (`4:30`).

If `stride_order` is not specified, the system automatically deduces it from the tensor’s layout using the following logic:

1.  Sort the strides in descending order.
2.  If multiple dimensions have a stride of 1, a deduction failure error is raised.

For example:

-   For a tensor with layout `(2,2,3,4):(2,1,4,12)`, the deduced `stride_order` is `[3,2,0,1]`.
-   For a tensor with layout `(1,5,1):(1,1,1)`, `stride_order`’s deduction fails because all dimensions have an identical stride of 1, making it impossible to determine the correct ordering.

If `stride_order` is specified, the system validates that the order is consistent with the tensor’s layout.

The `divisibility` parameter specifies the divisibility of the dynamic shape. It could be used to represent the assumption alignment of the input. Defaults to 1.

Note that this API is only available for compact tensors. For non-compact tensors, we can use `cute.assume` to attach divisibility information to a specific shape mode in a host JIT function, as demonstrated in the following example:

@cute.jit
def foo(a: cute.Tensor):
    new\_shape \= a.shape
    \# use cute.assume to set shape of mode=0 with divisibility=16
    new\_shape\[0\] \= cute.assume(new\_shape\[0\], 16)
    new\_layout \= cute.make\_layout(new\_shape, stride\=a.stride)
    new\_a \= cute.make\_tensor(a.iterator, new\_layout)

Copy to clipboard

### Code Example[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#id2 "Link to this heading")

The following example demonstrates how to use `mark_compact_shape_dynamic` to specify dynamic tensor layouts.

-   `t0` & `t1` show the usage of `mark_compact_shape_dynamic` with unspecified `stride_order` and different `mode` and `divisibility`.
-   `t2` shows the usage of consecutive `mark_compact_shape_dynamic` with unspecified `stride_order` and different `mode` and `divisibility`.
-   `t3` & `t4` show the usage of `mark_compact_shape_dynamic` with different specified `stride_order`.
-   `t5`, `t6`, `t7`, `t8`, `t9`, `t10`, `t11`, and `t12` demonstrate incorrect settings for parameters and expected errors.

import torch
from cutlass.cute.runtime import from\_dlpack

\# (8,4,16,2):(2,16,64,1)
a \= torch.empty(16, 4, 8, 2).permute(2, 1, 0, 3)
\# (1,4,1,32,1):(4,1,4,4,4) => torch tensor when dimension has shape 1, its stride is degenerated to 1,
\# resulting in (1,4,1,32,1):(1,1,1,4,1)
\# b.dim\_order() is (3,2,4,0,1)
b \= torch.empty(32, 1, 1, 1, 4).permute(3, 4, 1, 0, 2)

\# auto deduce the stride order to be \[2,1,0,3\]
t0 \= from\_dlpack(a).mark\_compact\_shape\_dynamic(
    mode\=0, divisibility\=2
)
\# (?{div=2},4,16,2):(2,?{div=4},?{div=16},1)
print(t0)

t1 \= from\_dlpack(a).mark\_compact\_shape\_dynamic(
    mode\=1, divisibility\=2
)
\# (8,?{div=2},16,2):(2,16,?{div=32},1)
print(t1)

t2 \= from\_dlpack(a).mark\_compact\_shape\_dynamic(
    mode\=1, divisibility\=2
).mark\_compact\_shape\_dynamic(
    mode\=3, divisibility\=2
)
\# (8,?{div=2},16,?{div=2}):(?{div=2},?{div=16},?{div=32},1)
print(t2)

t3 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=2, divisibility\=1, stride\_order\=(3, 0, 2, 4, 1)
)
\# (1,4,?,32,1):(0,1,4,?{div=4},0)
print(t3)

t4 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=2, divisibility\=1, stride\_order\=(2, 3, 4, 0, 1)
)
\# (1,4,?,32,1):(0,1,128,4,0)
print(t4)

t5 \= t2.mark\_compact\_shape\_dynamic(
    mode\=3, divisibility\=5, stride\_order\=(0, 1, 2, 3)
)
\# The stride\_order is not consistent with the last stride\_order

t6 \= from\_dlpack(a).mark\_compact\_shape\_dynamic(
    mode\=3, divisibility\=5, stride\_order\=(0, 1, 2, 3)
)
\# The stride\_order is not consistent with the deduced stride\_order

t7 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=0, divisibility\=4
)
\# The layout could not be deduced, please specify the stride\_order explicitly

t8 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=30, divisibility\=5, stride\_order\=(3, 0, 2, 4, 1)
)
\# Expected mode value to be in range \[0, 5), but got 30

t9 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=3, divisibility\=5, stride\_order\=(2, 1, 2, 3, 4)
)
\# Expected stride\_order to contain all the dimensions of the tensor, but it doesn't contain 0.

t10 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=3, divisibility\=5, stride\_order\=(0, 1, 2, 3, 4, 5)
)
\# Expected stride\_order to have 5 elements, but got 6.

t11 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=0, divisibility\=4, stride\_order\=b.dim\_order()
)
\# The shape(1) of mode(0) is not divisible by the divisibility(4)

t12 \= from\_dlpack(b).mark\_compact\_shape\_dynamic(
    mode\=0, divisibility\=1, stride\_order\=(2, 1, 3, 0, 4)
)
\# The stride\_order is not consistent with the layout

c \= torch.empty(1000000000, 1000000000)
t13 \= from\_dlpack(c, use\_32bit\_stride\=True).mark\_compact\_shape\_dynamic(
    mode\=0, divisibility\=1
)
\# Layout in DLTensorWrapper has int32 overflow risk. Please set use\_32bit\_stride to False.

Copy to clipboard

## Leveraging TVM FFI for Faster PyTorch Interop[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#leveraging-tvm-ffi-for-faster-pytorch-interop "Link to this heading")

The latest version of CuTe DSL supports TVM FFI to improve interoperability with PyTorch and other machine learning frameworks. Using TVM FFI provides the following features:

-   Faster JIT function invocation.
-   Direct acceptance of `torch.Tensor` objects as function arguments.
-   Enhanced error handling and kernel validation.
-   Seamless integration with multiple programming languages.

For more details, see [Compile with TVM FFI](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html).

## Bypass the DLPack Protocol[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/framework_integration.html#bypass-the-dlpack-protocol "Link to this heading")

In certain scenarios, users may wish to bypass the DLPack protocol and invoke the JIT function directly. This can be accomplished by creating a lightweight JIT wrapper around the existing JIT function, utilizing `cute.ptr` and `cute.make_tensor` to pass pointers and construct tensors directly.

Typical use cases for bypassing DLPack include: 1. Users want to call the JIT function directly to avoid the overhead introduced by the DLPack protocol. 2. DLPack canonicalizes the stride of shape-1 dimensions to 1, which may result in incorrect alignment propagation and affect memory access or performance. 3. DLPack may lack support for some narrow data types.

The following example illustrates how to bypass the DLPack protocol when invoking a JIT function. Assume we have a pre-defined `TensorOpGemm` kernel whose JIT interface expects three arguments of type `cute.Tensor`. To enable direct invocation without DLPack, we first define a JIT wrapper function that accepts `cute.Pointer` types as parameters. Within this wrapper, we use `cute.make_tensor` to construct tensors from the provided pointers, and then call the `TensorOpGemm` kernel as usual.

@cute.jit
def tensor\_op\_gemm\_wrapper(
    a\_ptr: cute.Pointer,
    b\_ptr: cute.Pointer,
    c\_ptr: cute.Pointer,
    m: cutlass.Int32,
    n: cutlass.Int32,
    k: cutlass.Int32,
    l: cutlass.Int32,
):

    \# Assume alignment of shape to call tensorop\_gemm example
    m \= cute.assume(m, divby\=8)
    n \= cute.assume(n, divby\=8)

    \# Torch is row major
    a\_layout \= cute.make\_ordered\_layout((m, k, l), order\=(0, 1, 2))
    b\_layout \= cute.make\_ordered\_layout((n, k, l), order\=(0, 1, 2))
    c\_layout \= cute.make\_ordered\_layout((m, n, l), order\=(1, 0, 2))
    mA \= cute.make\_tensor(a\_ptr, layout\=a\_layout)
    mB \= cute.make\_tensor(b\_ptr, layout\=b\_layout)
    mC \= cute.make\_tensor(c\_ptr, layout\=c\_layout)

    \# TensorOpGemm is a pre-defined kernel from our example
    tensor\_op\_gemm \= TensorOpGemm(
        a\_ptr.value\_type, c\_ptr.value\_type, cutlass.Float32, (2, 2, 1)
    )

    tensor\_op\_gemm(mA, mB, mC)

Copy to clipboard

To pass a PyTorch tensor to this new JIT wrapper, we retrieve the raw pointer from the PyTorch tensor and create a `cute.Pointer` instance using `cute.make_ptr`. This approach allows us to bypass the DLPack protocol entirely, avoiding its overhead and potential issues with shape-1 dimension handling.

a \= torch.randn(
    m, k, l, dtype\=torch.float16, device\="cuda"
).permute(2, 1, 0)
b \= torch.randn(
    n, k, l, dtype\=torch.float16, device\="cuda"
).permute(2, 1, 0)
c \= torch.randn(
    n, m, l, dtype\=torch.float16, device\="cuda"
).permute(1, 2, 0)

\# from cutlass.cute.runtime import make\_ptr
a\_ptr \= make\_ptr(
    cutlass.Float16, a.data\_ptr(), cute.AddressSpace.gmem, assumed\_align\=32
)
b\_ptr \= make\_ptr(
    cutlass.Float16, b.data\_ptr(), cute.AddressSpace.gmem, assumed\_align\=32
)
c\_ptr \= make\_ptr(
    cutlass.Float16, c.data\_ptr(), cute.AddressSpace.gmem, assumed\_align\=32
)
tensor\_op\_gemm\_wrapper(a\_ptr, b\_ptr, c\_ptr, m, n, k, l)

# Debugging[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#debugging "Link to this heading")

This page provides an overview of debugging techniques and tools for CuTe DSL programs.

## Getting Familiar with the Limitations[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#getting-familiar-with-the-limitations "Link to this heading")

Before diving into comprehensive debugging capabilities, it’s important to understand the limitations of CuTe DSL. Understanding these limitations will help you avoid potential pitfalls from the start.

Please refer to [Limitations](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/limitations.html) for more details.

## Source Code Correlation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#source-code-correlation "Link to this heading")

CuTe DSL provides Python code to PTX/SASS correlation to enable the profiling/debugging of generated kernels with debug symbols by generating line info when compiling the kernel.

You can enable that globally via the environment variable CUTE\_DSL\_LINEINFO=1. Alternative, you can use compilation options to enable that per kernel. Please refer to [JIT Compilation Options](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_compilation_options.html) for more details.

## DSL Debugging[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#dsl-debugging "Link to this heading")

CuTe DSL provides built-in logging mechanisms to help you understand the code execution flow and some of the internal state.

### Enabling Logging[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#enabling-logging "Link to this heading")

CuTe DSL provides environment variables to control logging level:

\# Enable console logging (default: False)
export CUTE\_DSL\_LOG\_TO\_CONSOLE\=1

\# Log to file instead of console (default: False)
export CUTE\_DSL\_LOG\_TO\_FILE\=my\_log.txt

\# Control log verbosity (0, 10, 20, 30, 40, 50, default: 10)
export CUTE\_DSL\_LOG\_LEVEL\=20

Copy to clipboard

### Log Categories and Levels[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#log-categories-and-levels "Link to this heading")

Similar to standard Python logging, different log levels provide varying degrees of detail:

| Level | Description |
| --- | --- |
| 0   | Disabled |
| 10  | Debug |
| 20  | Info |
| 30  | Warning |
| 40  | Error |
| 50  | Critical |

### Dump the generated IR[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#dump-the-generated-ir "Link to this heading")

For users familiar with MLIR and compilers, CuTe DSL supports dumping the Intermediate Representation (IR). This helps you verify whether the IR is generated as expected.

\# Dump Generated CuTe IR (default: False)
export CUTE\_DSL\_PRINT\_IR\=1

\# Keep Generated CuTe IR in a file (default: False)
export CUTE\_DSL\_KEEP\_IR\=1

Copy to clipboard

### Dump the generated PTX & CUBIN[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#dump-the-generated-ptx-cubin "Link to this heading")

For users familiar with PTX and SASS, CuTe DSL supports dumping the generated PTX and CUBIN.

\# Dump generated PTX in a .ptx file (default: False)
export CUTE\_DSL\_KEEP\_PTX\=1

\# Dump generated cubin in a .cubin file (default: False)
export CUTE\_DSL\_KEEP\_CUBIN\=1

Copy to clipboard

To further get SASS from cubin, users can use `nvdisasm` (usually installed with CUDA toolkit) to disassemble the cubin.

nvdisasm your\_dsl\_code.cubin \> your\_dsl\_code.sass

Copy to clipboard

### Access the dumped contents programmatically[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#access-the-dumped-contents-programmatically "Link to this heading")

For compiled kernels, the generated PTX/CUBIN/IR can be accessed programmatically as well through following attributes:

-   `__ptx__`: The generated PTX code of the compiled kernel.
-   `__cubin__`: The generated CUBIN data of the compiled kernel.
-   `__mlir__`: The generated IR code of the compiled kernel.

compiled\_foo \= cute.compile(foo, ...)
print(f"PTX: {compiled\_foo.\_\_ptx\_\_}")
with open("foo.cubin", "wb") as f:
    f.write(compiled\_foo.\_\_cubin\_\_)

Copy to clipboard

### Change the dump directory[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#change-the-dump-directory "Link to this heading")

By default, all dumped files are saved in the current working directory. To specify a different directory for the dumped files, please set the environment variable CUTE\_DSL\_DUMP\_DIR accordingly.

## Kernel Functional Debugging[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#kernel-functional-debugging "Link to this heading")

### Using Python’s `print` and CuTe’s `cute.printf`[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#using-python-s-print-and-cute-s-cute-printf "Link to this heading")

CuTe DSL programs can use both Python’s native `print()` as well as our own `cute.printf()` to print debug information during kernel generation and execution. They differ in a few key ways:

-   Python’s `print()` executes during compile-time only (no effect on the generated kernel) and is typically used for printing static values (e.g. a fully static layouts).
-   `cute.printf()` executes at runtime on the GPU itself and changes the PTX being generated. This can be used for printing values of tensors at runtime for diagnostics, but comes at a performance overhead similar to that of printf() in CUDA C.

For detailed examples of using these functions for debugging, please refer to the associated notebook referenced in [Educational Notebooks](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/notebooks.html).

### Handling Unresponsive/Hung Kernels[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#handling-unresponsive-hung-kernels "Link to this heading")

When a kernel becomes unresponsive and `SIGINT` (`CTRL+C`) fails to terminate it, you can follow these steps to forcefully terminate the process:

1.  Use `CTRL+Z` to suspend the unresponsive kernel
2.  Execute the following command to terminate the suspended process:

\# Terminate the most recently suspended process
kill \-9 $(jobs \-p | tail \-1)

Copy to clipboard

CuTe DSL can also be debugged using standard NVIDIA CUDA tools.

### Using Compute-Sanitizer[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#using-compute-sanitizer "Link to this heading")

For detecting memory errors and race conditions:

compute-sanitizer \--some\_options python your\_dsl\_code.py

Copy to clipboard

Please refer to the [compute-sanitizer documentation](https://developer.nvidia.com/compute-sanitizer) for more details.

### Set function name prefix[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#set-function-name-prefix "Link to this heading")

By default, the function name (host function or kernel function) is automatically generated based on the function name and its parameters. Sometimes you may want to attach some runtime information to the function name to make performance profiling and debugging easier, e.g., the kernel configs or the rank ids. You can assign a name prefix to the name by calling the `set_name_prefix` method on the host function or kernel function.

@cute.kernel
def kernel(arg1, arg2, ...):
    ...
@cute.jit
def launch\_kernel():
    kernel.set\_name\_prefix("your\_custom\_name\_prefix")
    kernel(arg1, arg2, ...).launch(grid\=\[1, 1, 1\], block\=\[1, 1, 1\], ...)

Copy to clipboard

For above example, the generated kernel name will be “your\_custom\_name\_prefix\_xxx”.

## Conclusion[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/debugging.html#conclusion "Link to this heading")

This page covered several key methods for debugging CuTe DSL programs. Effective debugging typically requires a combination of these approaches. If you encounter issues with DSL, you can enable logging and share the logs with the CUTLASS team as a GitHub issue to report a bug.

# Guidance for Auto-Tuning[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/autotuning_gemm.html#guidance-for-auto-tuning "Link to this heading")

Numerous GEMM kernel code examples are offered within our codebase. When integrating these kernels into frameworks, auto-tuning becomes essential for achieving optimal performance. This involves selecting the appropriate kernel parameters based on the inputs of real applications. Next, we’ll briefly introduce some tips on how to perform auto-tuning.

The auto-tuning process typically involves the following steps:

1.  Define search space
2.  Benchmark each configuration and select the kernel with the best performance
3.  Enable caching to reduce the tuning cost

The search space defines the valid combinations of kernel parameters that can be used to run the kernels. Different inputs (shapes, data types, etc.) typically require different kernel parameters to achieve optimal performance. The search space is related to the kernel. We take the Blackwell GEMM persistent kernel as an example. The search space is as follows:

-   `mma_tiler_mn`: Defines the dimensions of the matrix tile that each Matrix Multiply-Accumulate (MMA) instruction processes in a single operation.
-   `cluster_shape_mn`: Specifies the number of CTAs along each dimension within a cluster. Refer [Parallel Thread Execution ISA documentation](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#tensorcore-5th-generation-family-instructions) for the possible mma tiler size and cluster shape for different tensor data types.
-   `use_2cta_instrs`: Whether to utilize Blackwell’s 2 CTA instructions for MMA/Copy.
-   `use_tma_store`: Whether to use Tensor Memory Access (TMA) instructions to store the result back to global memory.

After defining the search space, we could traverse all parameter combinations to find the optimal kernel. The `autotune_gemm` function below demonstrates a simple exhaustive search approach - it iterates through configurations, compiles and benchmarks each kernel, and returns the best performing one. Since kernel compilation incurs overhead, it’s important to cache and reuse compiled kernels to minimize host launch latency. CuTe DSL facilitates this through its separate compilation and execution workflow. More details can be found in [JIT Caching](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_jit_caching.html#jit-caching). As demonstrated in the `autotune_gemm` function (between the `begin of cache the compiled GEMM kernel` and `end of cache the compiled GEMM kernel` comments), we can use `cute.compile()` to compile a kernel once, cache the compiled result, and reuse the cached JIT executor for multiple kernel executions. We could maintain a global configuration-to-kernel dictionary (`config_kernel_dict`) to cache the compiled GEMM kernels, where each key (`kernel_cache_key`) uniquely identifies a kernel based on its characteristics. Usually we could use the {dtype + kernel configs} as the cached key for GEMM compilation. For example,

kernel\_cache\_key \= f"{ab\_dtype}x{c\_dtype}x{acc\_dtype}x{use\_2cta\_instrs}x{mma\_tiler}x{cluster\_shape\_mn}x{use\_tma\_store}"

Copy to clipboard

If the input tensor’s layout is static, we should add the shape in the cached key too. Users can customize the `benchmark` function to measure kernel execution time. For stable and reliable performance measurements:

1.  Run a few warmup iterations (e.g., 5-10) to stabilize GPU temperature
2.  Execute multiple timed iterations (e.g., 100-1000) for statistical significance
3.  Use CUDA events and synchronization for precise timing
4.  Lock GPU frequencies (SM and memory frequencies) with nvidia-smi
5.  Process results by removing outliers and using min/avg statistics as measurements.

This ensures reliable kernel selection through proper benchmarking.

\# get the best GEMM kernel for given input tensors
def autotune\_gemm(
    a: cute.Tensor,
    b: cute.Tensor,
    c: cute.Tensor,
    stream: cuda.CUstream,
    use\_2cta\_instrs\_list: List\[bool\] \= \[True\],
    use\_tma\_store\_list: List\[bool\] \= \[True\],
    mma\_tiler\_m\_list: List\[int\] \= \[256\],
    mma\_tiler\_n\_list: List\[int\] \= \[256\],
    cluster\_shape\_m\_list: List\[int\] \= \[2\],
    cluster\_shape\_n\_list: List\[int\] \= \[1\],
):
    best\_kernel \= None
    min\_time \= float("inf")
    \# traverse the search space
    for use\_2cta\_instrs in use\_2cta\_instrs\_list:
        for use\_tma\_store in use\_tma\_store\_list:
            for mma\_tiler\_mn in product(mma\_tiler\_m\_list, mma\_tiler\_n\_list):
                for cluster\_shape\_mn in product(cluster\_shape\_m\_list, cluster\_shape\_n\_list):
                    acc\_dtype \= cutlass.Float32
                    hardware\_info \= cutlass.utils.HardwareInfo()
                    max\_active\_clusters \= hardware\_info.get\_max\_active\_clusters(
                        cluster\_shape\_mn\[0\] \* cluster\_shape\_mn\[1\]
                    )
                    \# instance a GEMM kernel
                    gemm \= PersistentDenseGemmKernel(
                        acc\_dtype,
                        use\_2cta\_instrs,
                        mma\_tiler\_mn,
                        cluster\_shape\_mn,
                        use\_tma\_store,
                    )
                    \# begin of cache the compiled GEMM kernel
                    if kernel\_cache\_key not in config\_kernel\_dict:
                        \# compile gemm kernel
                        compiled\_gemm \= cute.compile(
                            gemm,
                            a,
                            b,
                            c,
                            max\_active\_clusters,
                            stream,
                        )
                        config\_kernel\_dict\[kernel\_cache\_key\] \= compiled\_gemm
                    else:
                        compiled\_gemm \= config\_kernel\_dict\[kernel\_cache\_key\]
                    \# end of cache the compiled GEMM kernel
                    try:
                        \# define a benchmark function to measure the execution time of the compiled GEMM kernel
                        cur\_time \= benchmark(
                            partial(compiled\_gemm, a, b, c, stream),
                        )
                    except Exception as e:
                        print(f"Execution error: {e}")
                        cur\_time \= float("inf")
                    if cur\_time < min\_time:
                        min\_time \= cur\_time
                        best\_kernel \= compiled\_gemm
    if best\_kernel is None:
        raise ValueError("No best kernel found")
    return best\_kernel

Copy to clipboard

This brute-force approach ensures we could find the optimal parameters, though at the cost of trying every possibilities. For more advanced use cases, users can explore sophisticated optimization techniques like search space pruning and genetic algorithms to reduce tuning overhead and discover better configurations more efficiently.

To further optimize tuning performance, we can utilize caching mechanisms to avoid redundant computations. We could cache the tuning results in a input-to-kernel dictionary (e.g., `input_kernel_dict`). When processing inputs with matching `config_key` values, the cached kernel can be reused directly without re-tuning. The `config_key` is related with the input tensor’s characteristics, such as the shape, data type, etc. The setup of `config_key` is very flexible, users can customize it based on their own application. For instance, if the data type is fixed in users’ application, we could use the input tensor’s shape as the key, i.e., `(m, n, k)`. To further reduce tuning overhead, we could consider using a simplified key like `config_key = (power_of_2(m), power_of_2(n), power_of_2(k))`, where `m`, `n`, and `k` are rounded up to the nearest power of 2. This simplification can significantly reduce the number of unique keys while still maintaining good performance in most cases. However, it’s important to validate that this approximation doesn’t negatively impact performance for your specific use case.

config\_key \= (m, n, k)
if config\_key in input\_kernel\_dict:
    compiled\_gemm \= input\_kernel\_dict\[config\_key\]
else:
    compiled\_gemm \= autotune\_gemm(...)
    input\_kernel\_dict\[config\_key\] \= compiled\_gemm
\# launch gemm kernel
compiled\_gemm(a\_tensor, b\_tensor, c\_tensor, stream)

Copy to clipboard

By following the methods above, you can customize your own auto-tuner to find the optimal GEMM kernel configuration for specific matrix dimensions and data types, significantly improving computational performance for models.

# Compile with TVM FFI[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#id1 "Link to this heading")

Apache TVM FFI is an open ABI and FFI for machine learning systems. More information can be found in the [official documentation](https://tvm.apache.org/ffi/).

To install TVM FFI, you can run the following command:

pip install apache-tvm-ffi
\# optional package for improved torch tensor calling performance
pip install torch-c-dlpack-ext

Copy to clipboard

In CuTe DSL, TVM FFI can be enabled as an option for JIT-compiled functions. Using TVM FFI can lead to faster JIT function invocation and provides better interoperability with machine learning frameworks (e.g., directly take `torch.Tensor` as arguments).

## Enable Apache TVM FFI in CuTe DSL[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#enable-apache-tvm-ffi-in-dsl "Link to this heading")

First, install the `tvm-ffi` package by following its [installation guide](https://tvm.apache.org/ffi/#installation).

There are two ways to enable TVM FFI in CuTe DSL:

1.  Use the `options` argument in `cute.compile` to specify the TVM FFI option. For example:

\# Assuming you have defined a function \`add\` decorated with @cute.jit
def example\_compile():
   a\_torch \= torch.randn(10, 20, 30).to(torch.float16)
   b\_torch \= torch.randn(10, 20, 30).to(torch.float16)
   a\_cute \= cute.runtime.from\_dlpack(a\_torch, enable\_tvm\_ffi\=True).mark\_layout\_dynamic()
   b\_cute \= cute.runtime.from\_dlpack(b\_torch, enable\_tvm\_ffi\=True).mark\_layout\_dynamic()

   compiled\_add \= cute.compile(add, a\_torch, b\_torch, options\="--enable-tvm-ffi")

Copy to clipboard

Note that the object returned by `cute.compile` is a Python function specific to TVM FFI.

2.  Alternatively, you can enable TVM FFI globally by setting the environment variable `CUTE_DSL_ENABLE_TVM_FFI=1`. Please note that this setting will apply to all JIT compilations within the environment.

## Minimizing Host Overhead[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#minimizing-host-overhead "Link to this heading")

Eager kernel invocation overhead on the CPU host can sometimes become a bottleneck for latency-sensitive applications. TVM FFI can help greatly reduce this overhead. To maximize performance benefits, we recommend setting up your workflow as follows (detailed instructions are provided in subsequent sections):

-   **Compile the kernel with TVM FFI enabled.**
-   **Declare shape constraints using fake tensors** and reuse the compiled function throughout your execution.
-   **Pass PyTorch tensors directly** to the compiled function to avoid explicit DLPack conversion.
-   **Use the environment stream flag** to implicitly pass the current PyTorch stream.
-   **Rely on compiled argument validation** instead of Python-side attribute validation, as TVM FFI functions perform fast compiled checks.

Following these steps can significantly reduce the host-side overhead of eager kernel execution. The sections below provide detailed examples and explanations for each step. You may find it helpful to refer back to this summary after you review the implementation details.

## Fake tensor for compilation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#fake-tensor-for-compilation "Link to this heading")

The TVM FFI function accepts DLPack-compatible tensors as arguments, such as those from torch or jax. However, during compilation, it is necessary to specify the tensors’ dynamic properties in CuTe DSL. To clearly distinguish between the compilation phase and runtime, CuTe DSL provides a “fake tensor” that can be used for compilation. For example:

import cutlass.cute as cute
import torch

@cute.kernel
def device\_add\_one(a: cute.Tensor, b: cute.Tensor):
   threads\_per\_block \= 128
   cta\_x\_, \_, \_ \= cute.arch.block\_idx()
   tid\_x, \_, \_ \= cute.arch.thread\_idx()
   tid \= cta\_x\_ \* threads\_per\_block + tid\_x
   if tid < a.shape\[0\]:
      b\[tid\] \= a\[tid\] + 1.0

@cute.jit
def add\_one(a: cute.Tensor, b: cute.Tensor):
   n \= a.shape\[0\]
   threads\_per\_block \= 128
   blocks \= (n + threads\_per\_block \- 1) // threads\_per\_block
   device\_add\_one(a, b).launch(
      grid\=(blocks, 1, 1),
      block\=(threads\_per\_block, 1, 1),
   )

def example\_add\_one():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   \# compile the kernel with "--enable-tvm-ffi" option and example input tensors
   compiled\_add\_one \= cute.compile(add\_one, a\_cute, b\_cute, options\="--enable-tvm-ffi")
   \# now compiled\_add\_one is a TVM-FFI function that can be called with torch.Tensor as input
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   compiled\_add\_one(a\_torch, b\_torch)
   print("result of b\_torch after compiled\_add\_one(a\_torch, b\_torch)")
   print(b\_torch)

Copy to clipboard

The fake tensor is a placeholder that mimics the interface of a real tensor but does not hold real data or allow indexing. It is used in compilation or testing scenarios where only shape/type/layout information is needed. All attempts to access or mutate data will raise errors.

### Note on Stride Order[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#note-on-stride-order "Link to this heading")

Note that CuTe’s convention is to write the stride order for dimensions from left to right, where a lower order number means higher priority. In the context of the `make_fake_compact_tensor` API, for shape `(2, 3, 4)` and stride order `(0, 1, 2)`, the stride is `(1, 2, 6)`. This is commonly known as column-major order. If you want to create a fake tensor with compact row-major order, you should explicitly pass in `stride_order=tuple(reversed(range(len(shape))))` to `make_fake_compact_tensor`. Alternatively, you can always precisely control the stride via the `stride` argument in the `make_fake_tensor` API.

## `cute.Tensor` adapter for TVM FFI[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#cute-tensor-adapter-for-tvm-ffi "Link to this heading")

To adapt the `cute.Tensor` to the TVM FFI function, you can use the `cute.runtime.from_dlpack` function with the `enable_tvm_ffi=True` option or the environment variable `CUTE_DSL_ENABLE_TVM_FFI=1`. For example:

def example\_from\_dlpack():
   a\_cute \= cute.runtime.from\_dlpack(a\_torch, enable\_tvm\_ffi\=True).mark\_layout\_dynamic()
   b\_cute \= cute.runtime.from\_dlpack(b\_torch, enable\_tvm\_ffi\=True).mark\_layout\_dynamic()

   compiled\_add\_one(a\_cute, b\_cute)

Copy to clipboard

Note that because the `cute.runtime.from_dlpack` function performs an explicit DLPack conversion, it is less efficient than passing the `torch.Tensor` directly. You can also use `cute.Tensor` as an argument hint for `cute.compile`.

compiled\_add\_one \= cute.compile(add\_one, a\_cute, b\_cute, options\="--enable-tvm-ffi")

Copy to clipboard

## Working with torch Tensors[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#working-with-torch-tensors "Link to this heading")

As you may have noticed in the examples above, TVM FFI-compiled functions can directly accept `torch.Tensor` objects (and other DLPack-compatible tensors) as inputs. The resulting functions add minimal overhead, enabling faster eager invocations thanks to the optimized calling path.

## Working with Streams[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#working-with-streams "Link to this heading")

In many cases, a CuTe kernel needs to run on a specific CUDA stream. CuTe DSL provides two ways to work with streams through TVM FFI. The first is to pass the stream explicitly as an argument. The following example demonstrates this approach; the function accepts `torch.cuda.Stream`, `CUstream` or any stream class that implements the CUDA stream protocol.

import cutlass.cute as cute
import torch
from cuda.bindings.driver import CUstream

@cute.kernel
def device\_add\_one(a: cute.Tensor, b: cute.Tensor):
   threads\_per\_block \= 128
   cta\_x\_, \_, \_ \= cute.arch.block\_idx()
   tid\_x, \_, \_ \= cute.arch.thread\_idx()
   tid \= cta\_x\_ \* threads\_per\_block + tid\_x
   if tid < a.shape\[0\]:
      b\[tid\] \= a\[tid\] + 1.0

@cute.jit
def add\_one\_with\_stream(a: cute.Tensor, b: cute.Tensor, stream: CUstream):
   n \= a.shape\[0\]
   threads\_per\_block \= 128
   blocks \= (n + threads\_per\_block \- 1) // threads\_per\_block
   device\_add\_one(a, b).launch(
      grid\=(blocks, 1, 1),
      block\=(threads\_per\_block, 1, 1),
      stream\=stream,
   )

def example\_add\_one\_with\_stream():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   \# Fake stream is a placeholder for stream argument
   stream \= cute.runtime.make\_fake\_stream()
   compiled\_add\_one \= cute.compile(
      add\_one\_with\_stream, a\_cute, b\_cute, stream, options\="--enable-tvm-ffi"
   )
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   torch\_stream \= torch.cuda.current\_stream()
   compiled\_add\_one(a\_torch, b\_torch, torch\_stream)
   torch\_stream.synchronize()
   print("result of b\_torch after compiled\_add\_one(a\_torch, b\_torch, torch\_stream)")
   print(b\_torch)

Copy to clipboard

### Using Environment Stream[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#using-environment-stream "Link to this heading")

The second option is to rely on the environment stream flag. Pass `use_tvm_ffi_env_stream=True` to `make_fake_stream` to mark the stream argument as an environment stream, which means it no longer needs to be provided explicitly. TVM FFI will automatically use its environment stream (i.e., the current PyTorch stream) as the stream argument. The example below demonstrates this flow:

def example\_add\_one\_with\_env\_stream():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   \# Fake stream is a placeholder for stream argument
   \# we will use TVM FFI environment stream
   stream \= cute.runtime.make\_fake\_stream(use\_tvm\_ffi\_env\_stream\=True)
   compiled\_add\_one \= cute.compile(
      add\_one\_with\_stream, a\_cute, b\_cute, stream, options\="--enable-tvm-ffi"
   )
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   torch\_stream \= torch.cuda.current\_stream()
   with torch.cuda.stream(torch\_stream):
      \# no need to pass in the stream explicitly, env stream will be synced
      \# to torch.cuda.current\_stream() before the function call.
      compiled\_add\_one(a\_torch, b\_torch)
   torch\_stream.synchronize()
   print("result of b\_torch after compiled\_add\_one(a\_torch, b\_torch)")
   print(b\_torch)

Copy to clipboard

Using the environment stream flag both speeds up calls and simplifies integration with frameworks such as PyTorch, since no explicit stream parameter is required. We recommend using the environment stream flag to both simplify framework integration and minimize host-side calling overhead.

## Working with Tuples[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#working-with-tuples "Link to this heading")

TVM FFI functions can also accept tuples as arguments. Tuples can be recursively composed of the types that are supported by TVM FFI. The example below shows how to use tuples as arguments:

import torch
from cutlass import cute

@cute.kernel
def device\_add\_one(a: cute.Tensor, b: cute.Tensor, c: cute.Float32):
   threads\_per\_block \= 128
   cta\_x\_, \_, \_ \= cute.arch.block\_idx()
   tid\_x, \_, \_ \= cute.arch.thread\_idx()
   tid \= cta\_x\_ \* threads\_per\_block + tid\_x
   if tid < a.shape\[0\]:
      b\[tid\] \= a\[tid\] + c

@cute.jit
def add\_one\_with\_tuple(a: Tuple\[cute.Tensor, cute.Tensor, cute.Float32\]):
   n \= a\[0\].shape\[0\]
   threads\_per\_block \= 128
   blocks \= (n + threads\_per\_block \- 1) // threads\_per\_block
   device\_add\_one(a\[0\], a\[1\], a\[2\]).launch(grid\=(blocks, 1, 1), block\=(threads\_per\_block, 1, 1))

def example\_add\_one\_with\_tuple():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   compiled\_add\_one \= cute.compile(
      add\_one\_with\_tuple, (a\_cute, b\_cute, cute.Float32(4)),
      options\="--enable-tvm-ffi"
   )
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   compiled\_add\_one((a\_torch, b\_torch, 5))
   print("result of b\_torch after compiled\_add\_one((a\_torch, b\_torch, 5))")
   print(b\_torch)

example\_add\_one\_with\_tuple()

Copy to clipboard

## Working with Variadic Tuples[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#working-with-variadic-tuples "Link to this heading")

Sometimes it is helpful to annotate a tuple with no explicit element types. This can be useful to build up a generic template for a function that accepts a variable number of elements. The compiled function’s signature will be determined by the tuple argument passed to the `cute.compile` function. The following example shows how to use a variadic tuple to build such a generic template.

import cutlass
import torch
from cutlass import cute

@cute.kernel
def device\_add\_one(a: cute.Tensor, b: cute.Tensor, extra\_value: tuple):
   threads\_per\_block \= 128
   cta\_x\_, \_, \_ \= cute.arch.block\_idx()
   tid\_x, \_, \_ \= cute.arch.thread\_idx()
   tid \= cta\_x\_ \* threads\_per\_block + tid\_x
   if tid < a.shape\[0\]:
      if cutlass.const\_expr(len(extra\_value) != 0):
            b\[tid\] \= a\[tid\] + 1 + extra\_value\[0\]
      else:
            b\[tid\] \= a\[tid\] + 1

@cute.jit
def add\_one\_with\_extra\_value(a: cute.Tensor, b: cute.Tensor, extra\_value: tuple):
   n \= a.shape\[0\]
   threads\_per\_block \= 128
   blocks \= (n + threads\_per\_block \- 1) // threads\_per\_block
   device\_add\_one(a, b, extra\_value).launch(grid\=(blocks, 1, 1), block\=(threads\_per\_block, 1, 1))

def example\_add\_one\_with\_variadic\_tuple():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   compiled\_add\_one\_no\_extra \= cute.compile(
      add\_one\_with\_extra\_value, a\_cute, b\_cute, (),
      options\="--enable-tvm-ffi"
   )
   compiled\_add\_one\_with\_extra \= cute.compile(
      add\_one\_with\_extra\_value, a\_cute, b\_cute, (cute.Float32(4),),
      options\="--enable-tvm-ffi"
   )
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   compiled\_add\_one\_no\_extra(a\_torch, b\_torch, ())
   print("result of b\_torch after compiled\_add\_one\_no\_extra(a\_torch, b\_torch, ())")
   print(b\_torch)
   compiled\_add\_one\_with\_extra(a\_torch, b\_torch, (4,))
   print("result of b\_torch after compiled\_add\_one\_with\_extra(a\_torch, b\_torch, (4,))")
   print(b\_torch)

example\_add\_one\_with\_variadic\_tuple()

Copy to clipboard

### Working with Named Tuples[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#working-with-named-tuples "Link to this heading")

Named tuples are also supported and help logically group related arguments together. The example below shows how to use named tuples as arguments. Under the hood, named tuples are passed as unnamed tuples at the ABI level. When errors occur, the function signature in error messages will display unnamed tuple arguments. Ensure that the compile-time CuTe named tuple type definition has the same fields as the runtime PyTorch named tuple. Currently, users need to explicitly unpack the named tuple outside of conditionals and then use the unpacked variables inside the conditionals.

from typing import NamedTuple
from cutlass import cute
import torch

class CuteNamedTuple(NamedTuple):
   a: cute.Tensor
   b: cute.Tensor
   c: cute.Float32 \= cute.Float32(1)

   def \_\_new\_from\_mlir\_values\_\_(self, values):
      return CuteNamedTuple(\*values)

class TorchNamedTuple(NamedTuple):
   a: torch.Tensor
   b: torch.Tensor
   c: float \= 1

@cute.kernel
def device\_add\_one\_named\_tuple(value: CuteNamedTuple):
   tid \= cute.arch.block\_idx()\[0\] \* 128 + cute.arch.thread\_idx()\[0\]
   \# need to unpack namedtuple outside conditionals
   a \= value.a
   b \= value.b
   c \= value.c
   if tid < a.shape\[0\]:
      b\[tid\] \= a\[tid\] + c

@cute.jit
def add\_one\_with\_named\_tuple(value: CuteNamedTuple):
   n \= value.a.shape\[0\]
   threads\_per\_block \= 128
   blocks \= (n + threads\_per\_block \- 1) // threads\_per\_block
   device\_add\_one\_named\_tuple(value).launch(grid\=(blocks, 1, 1), block\=(threads\_per\_block, 1, 1))

def example\_add\_one\_with\_named\_tuple():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))

   compiled\_add\_one \= cute.compile(
      add\_one\_with\_named\_tuple, CuteNamedTuple(a\=a\_cute, b\=b\_cute),
      options\="--enable-tvm-ffi"
   )
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   compiled\_add\_one(TorchNamedTuple(a\=a\_torch, b\=b\_torch))
   print("result of b\_torch")
   print(b\_torch)

example\_add\_one\_with\_named\_tuple()

Copy to clipboard

## Supported types[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#supported-types "Link to this heading")

The TVM FFI function supports the following CuTe DSL-specific types as arguments:

-   `cute.Tensor`
-   `cutlass.Boolean`, `cutlass.Int8`, `cutlass.Int16`, `cutlass.Int32`, `cutlass.Int64`, `cutlass.Uint8`, `cutlass.Uint16`, `cutlass.Uint32`, `cutlass.Uint64`, `cutlass.Float32`, `cutlass.Float64`
-   `cute.Shape`, `cute.Stride`, `cute.Coord`, `cute.Tile`, `cute.IntTuple`

| Compile-time type | Call-time type |
| --- | --- |
| `cute.Pointer` | `ctypes.c_void_p` or a class that implements `__tvm_ffi_opaque_ptr__` protocol. |
| `cute.runtime.FakeTensor` | `torch.Tensor` and other DLPack-compatible tensors. |
| Scalar types (e.g. `cutlass.Boolean`, `cutlass.Int32`) | Python scalars (e.g. True, 123). |
| CuTe algebra types (e.g. `cute.Shape`, `cute.Stride`) | `tvm_ffi.Shape` or python tuple of ints. |
| CUDA stream `cuda.CUstream` | A stream class that implements the CUDA stream protocol (e.g. `torch.cuda.Stream`, `cuda.CUstream`). |
| Tuple of types (e.g. `Tuple[cute.Tensor, cute.Tensor, cutlass.Int32]`) | Python tuple of corresponding call-time types. |

## Error handling[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#error-handling "Link to this heading")

TVM FFI functions will enable validation of arguments to make sure they match the expected type and value constraints declared by the user. These checks are compiled into the function, run very fast, and have no observable overhead during function invocation. Each of those errors will translate into a proper Python exception that can be caught and handled. The example below shows some example error cases that can be checked:

def example\_constraint\_checks():
   n \= cute.sym\_int(divisibility\=16)
   \# assume align to 16 bytes (4 int32), both should share same shape variable n
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,), assumed\_align\=16)
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,), assumed\_align\=16)
   compiled\_add\_one \= cute.compile(add\_one, a\_cute, b\_cute, options\="--enable-tvm-ffi")
   a \= torch.zeros(128, dtype\=torch.float32, device\="cuda")
   b \= torch.zeros(128, dtype\=torch.float32, device\="cuda")

   try:
      \# raises type mismatch error because we expect a and b to be float32
      compiled\_add\_one(a, 1)
   except TypeError as e:
      \# Mismatched type on argument #1 when calling:
      \# \`add\_one(a: Tensor(\[n0\], float32), b: Tensor(\[n0\], float32))\`,
      \# expected Tensor
      print(f"TypeError: {e}")

   try:
      \# raises shape mismatch error because we expect both a and b have shap \[n\]
      compiled\_add\_one(a, b\[:126\])
   except ValueError as e:
      \# Mismatched b.shape\[0\] on argument #1 when calling:
      \# \`add\_one(a: Tensor(\[n0\], float32), b: Tensor(\[n0\], float32))\`,
      \# expected to match a.shape\[0\]
      print(f"ValueError: {e}")

   try:
      \# triggers divisibility mismatch error because 126 is not divisible by 16
      compiled\_add\_one(a\[:126\], b\[:126\])
   except ValueError as e:
      \# Invalid a.shape\[0\] on argument #0 when calling:
      \# \`add\_one(a: Tensor(\[n0\], float32), b: Tensor(\[n0\], float32)\`,
      \# expected to be divisible by 16
      print(f"ValueError: {e}")

   try:
      a \= torch.zeros(129, dtype\=torch.float32, device\="cuda")
      b \= torch.zeros(129, dtype\=torch.float32, device\="cuda")
      \# triggers data alignment mismatch error because x and y are not aligned to 16 bytes
      compiled\_add\_one(a\[1:\], b\[1:\])
   except ValueError as e:
      \# raises: Misaligned Tensor data on argument #0 when calling:
      \# \`add\_one(a: Tensor(\[n0\], float32), b: Tensor(\[n0\], float32)\`,
      \# expected data alignment=16 bytes
      print(f"ValueError: {e}")

Copy to clipboard

Any CUDA errors encountered will also be automatically converted into Python exceptions by the TVM FFI function.

@cute.jit
def add\_one\_invalid\_launch(a: cute.Tensor, b: cute.Tensor):
   \# Intentionally exceed the maximum block dimension (1024 threads) so the
   \# CUDA runtime reports an invalid configuration error.
   device\_add\_one(a, b).launch(grid\=(1, 1, 1), block\=(4096, 1, 1))

def example\_error\_cuda\_error():
   a\_torch \= torch.zeros((10,), dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.zeros((10,), dtype\=torch.float32, device\="cuda")

   a\_cute \= cute.runtime.from\_dlpack(a\_torch, enable\_tvm\_ffi\=True)
   b\_cute \= cute.runtime.from\_dlpack(b\_torch, enable\_tvm\_ffi\=True)
   compiled\_add\_one\_invalid\_launch \= cute.compile(
      add\_one\_invalid\_launch, a\_cute, b\_cute, options\="--enable-tvm-ffi"
   )

   try:
      compiled\_add\_one\_invalid\_launch(a\_torch, b\_torch)
   except RuntimeError as e:
      \# raises RuntimeError: CUDA Error: cudaErrorInvalidValue
      print(f"RuntimeError: {e}")

Copy to clipboard

## Working with Devices[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#working-with-devices "Link to this heading")

TVM FFI-compiled functions naturally work across GPU devices. The device index of the first input GPU tensor determines the kernel’s device context. The TVM FFI function calls `cudaSetDevice` to set the correct device before launching the kernel based on that tensor’s device index. For advanced scenarios that pass raw pointers instead of tensors, you should call `cudaSetDevice` explicitly through the CUDA Python API.

## Exporting Compiled Module[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#exporting-compiled-module "Link to this heading")

The TVM FFI function supports exporting the compiled module to an object file for further use. For example:

import subprocess
import cutlass.cute as cute

def example\_add\_one\_export():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   \# compile the kernel with "--enable-tvm-ffi" option and example input tensors
   compiled\_add\_one \= cute.compile(add\_one, a\_cute, b\_cute, options\="--enable-tvm-ffi")
   \# export the compiled module to object file
   compiled\_add\_one.export\_to\_c("./add\_one.o", function\_name\="add\_one")
   \# obtain necessary runtime libs for loading the shared library
   runtime\_libs \= cute.runtime.find\_runtime\_libraries(enable\_tvm\_ffi\=True)
   \# compile the object file to a shared library
   cmd \= \["gcc", "-shared", "-o", "./add\_one.so", "./add\_one.o", \*runtime\_libs\]
   print(cmd)
   subprocess.run(cmd, check\=True)
   print(f"Successfully created shared library: ./add\_one.so")

Copy to clipboard

Then you can load back the exported module and use it in different ways:

import torch
from cutlass import cute

def example\_load\_module\_add\_one():
   mod \= cute.runtime.load\_module("./add\_one.so", enable\_tvm\_ffi\=True)
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   mod.add\_one(a\_torch, b\_torch)
   print("result of b\_torch after mod.add\_one(a\_torch, b\_torch)")
   print(b\_torch)

Copy to clipboard

The exported object file exposes the function symbol `__tvm_ffi_add_one` that is compatible with TVM FFI and can be used in various frameworks and programming languages. You can either build a shared library and load it back, or link the object file directly into your application and invoke the function via the `InvokeExternC` mechanism in TVM FFI. For more information, see the [quick start guide](https://tvm.apache.org/ffi/get_started/quickstart) in the official documentation.

When you build your own libraries, make sure you link against the necessary runtime libraries. You can use `cute.runtime.find_runtime_libraries(enable_tvm_ffi=True)` to get the path to these libraries. `cute.runtime.load_module(path, enable_tvm_ffi=True)` will load these libraries automatically before loading an exported module. You can also manually load these libraries in advanced use cases.

For low-level cute ABI AOT compilation support without TVM FFI, you can refer to [Ahead-of-Time (AOT) Compilation](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html).

### Keyword Arguments and Defaults[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#keyword-arguments-and-defaults "Link to this heading")

The function returned by `cute.compile` supports keyword arguments and defaults. The example below shows how to use keyword arguments and defaults:

import torch
from cutlass import cute

@cute.kernel
def device\_add\_scalar(a: cute.Tensor, b: cute.Tensor, offset: cutlass.Float32):
   threads\_per\_block \= 128
   cta\_x\_, \_, \_ \= cute.arch.block\_idx()
   tid\_x, \_, \_ \= cute.arch.thread\_idx()
   tid \= cta\_x\_ \* threads\_per\_block + tid\_x
   if tid < a.shape\[0\]:
      b\[tid\] \= a\[tid\] + offset

@cute.jit
def add\_constant(a: cute.Tensor, b: cute.Tensor, offset: cutlass.Float32\=cutlass.Float32(1)):
   n \= a.shape\[0\]
   threads\_per\_block \= 128
   blocks \= (n + threads\_per\_block \- 1) // threads\_per\_block
   device\_add\_scalar(a, b, offset).launch(grid\=(blocks, 1, 1), block\=(threads\_per\_block, 1, 1))

def example\_kwargs\_and\_defaults():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   compiled\_add\_constant \= cute.compile(add\_constant, a\_cute, b\_cute, options\="--enable-tvm-ffi")
   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")
   compiled\_add\_constant(a\_torch, b\_torch)
   print("result of b\_torch after compiled\_add\_constant(a\_torch, b\_torch)")
   print(b\_torch)
   compiled\_add\_constant(a\_torch, b\_torch, offset\=4)
   print("result of b\_torch after compiled\_add\_constant(a\_torch, b\_torch, offset=4)")
   print(b\_torch)

Copy to clipboard

For efficiency and portability reasons, TVM FFI ABI supports functions with positional-only arguments. If you export the compiled module to an object file and then load it back, the function will only accept positional arguments in the order of the arguments in the function signature. You can rewrap the function or use the TVM FFI wrapper generator to generate a kwargs wrapper. The code block below shows how to do this:

def example\_kwargs\_and\_defaults():
   n \= cute.sym\_int()
   a\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   b\_cute \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))
   compiled\_add\_constant \= cute.compile(add\_constant, a\_cute, b\_cute, options\="--enable-tvm-ffi")
   \# export the compiled module to object file
   compiled\_add\_constant.export\_to\_c("./add\_constant.o", function\_name\="add\_constant")
   \# obtain necessary runtime libs for loading the shared library
   runtime\_libs \= cute.runtime.find\_runtime\_libraries(enable\_tvm\_ffi\=True)
   \# compile the object file to a shared library
   cmd \= \["gcc", "-shared", "-o", "./add\_constant.so", "./add\_constant.o", \*runtime\_libs\]
   subprocess.run(cmd, check\=True)

   a\_torch \= torch.arange(10, dtype\=torch.float32, device\="cuda")
   b\_torch \= torch.empty(10, dtype\=torch.float32, device\="cuda")

   mod \= cute.runtime.load\_module("./add\_constant.so")
   try:
      mod.add\_constant(a\_torch, b\_torch)
   except Exception as e:
      \# Raises a missing arguments error because kwargs and default information are lost
      print(e)
   \# We rewrap the function to regain argument and kwargs support.
   \# Alternatively, use the TVM FFI wrapper generator to generate a kwargs wrapper function.
   from tvm\_ffi.utils import kwargs\_wrapper
   \# arg\_defaults are aligned to the end of the argument list
   wrapped\_func \= kwargs\_wrapper.make\_kwargs\_wrapper(
      mod.add\_constant, arg\_names\=\["a", "b", "offset"\], arg\_defaults\=(1,)
   )
   wrapped\_func(a\_torch, b\_torch)
   print("result of b\_torch after wrapped\_func(a\_torch, b\_torch)")
   print(b\_torch)
   \# You can also use the signature of the original function
   \# to generate a kwargs wrapper function. Make sure to exclude
   \# arguments that are not included in the runtime,
   \# such as 'self', constexpr, and env stream arguments.
   wrapped\_func \= kwargs\_wrapper.make\_kwargs\_wrapper\_from\_signature(
      mod.add\_constant, signature\=inspect.signature(add\_constant),
      exclude\_arg\_names\=\["self"\]
   )
   wrapped\_func(a\_torch, b\_torch, offset\=4)
   print("result of b\_torch after wrapped\_func(a\_torch, b\_torch, offset=4)")
   print(b\_torch)

Copy to clipboard

## Limitations[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html#limitations "Link to this heading")

The Fake Tensor flow is ONLY compatible with TVM FFI because TVM FFI supports more flexible constraints on Tensor arguments. For instance, fake tensor can specify per-mode static shape or constraints on shape and strides which are not supported by existing `from_dlpack` flow. It’s expected that JIT function compiled with fake tensor will have different ABI compared to tensor converted by `from_dlpack`.

import cutlass.cute as cute
import torch

n \= cute.sym\_int()
\# Dynamic Shape
fake\_a \= cute.runtime.make\_fake\_compact\_tensor(cute.Float32, (n,))

\# Compile without tvm-ffi
compiled\_fn \= cute.compile(foo, fake\_a)

\# Wrong, in compatible ABI
compiled\_fn(from\_dlpack(a))

Copy to clipboard

In order to avoid such issue, it’s recommended to use fake tensor only with TVM FFI backend. Practically speaking, as we only want to call `from_dlpack` once and reuse for both compilation and runtime, the benefit of using fake tensor is limited in this case.

# Ahead-of-Time (AOT) Compilation[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#ahead-of-time-aot-compilation "Link to this heading")

This guide demonstrates how to use CuTe DSL’s Ahead-of-Time (AOT) compilation features to export compiled kernels for use in production environments.

## Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#overview "Link to this heading")

CuTe DSL Ahead-of-Time (hereinafter referred to as AOT) compilation allows you to:

-   **Compile once, enable cross-compilation**: Write kernels in Python and cross-compile them for multiple GPU architectures.
-   **Remove JIT overhead**: Eliminate compilation delays in production by pre-compiling kernels.
-   **Flexible integration**: Easily integrate compiled kernels into both Python and C/C++ codebases using flexible deployment options.

We provide 2 levels of AOT ABI:

1.  **Low-Level CuTe ABI**: This ABI is expressed using CuTe DSL types and tensors, mirroring the original Python function.
2.  **High-Level Apache TVM FFI ABI**: For interop with various frameworks (e.g., PyTorch, JAX), and offer high-level stable ABI access.

This guide will focus on the CuTe ABI AOT. For the Apache TVM FFI AOT, please refer to the section “Exporting Compiled Module” in [Compile with TVM FFI](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html).

## CuTe ABI AOT Workflow[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#cute-abi-aot-workflow "Link to this heading")

### Export Interface[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#export-interface "Link to this heading")

The `export_to_c` interface is provided by the `JitCompiledFunction` class. It accepts the following parameters:

-   `file_path`: The path to the directory where the header and object files will be saved.
-   `file_name`: The base name for the header and object files. The same file name will always overwrite existing files.
-   `function_prefix`: The prefix of the function symbol in the generated object file. This should be a unique identifier to avoid symbol conflicts. Users should ensure the function prefix is unique for each exported function. Defaults to the `file_name`.

It generates the following files:

-   `{file_path}/{file_name}.h`: A C header file containing API function declarations. This header specifies the runtime function signatures in C, mirroring the original Python function interfaces.
-   `{file_path}/{file_name}.o`: A standard object file containing the compiled kernel code. You can link this object file into either a static or shared library. It includes the host entry function, fatbin data, and helper functions such as `cuda_init` and `cuda_load_to_device`. Additionally, it embeds metadata for runtime loading and version verification.

Example:

import cutlass.cute as cute
import cutlass.cute.cuda as cuda

@cute.kernel
def print\_tensor\_kernel(a: cute.Tensor):
    cute.printf("a: {}", a)

@cute.jit
def print\_tensor(a: cute.Tensor, stream: cuda.CUstream):
    print\_tensor\_kernel(a).launch(grid\=(1, 1, 1), block\=(1, 1, 1), stream\=stream)

compiled\_func \= cute.compile(print\_tensor)
\# Export compiled functions to object files and headers
compiled\_func.export\_to\_c(file\_path\="./artifacts", file\_name\="print\_tensor\_example", function\_prefix\="print\_tensor")

Copy to clipboard

### Loading in Python[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#loading-in-python "Link to this heading")

Load pre-compiled object files or shared libraries into Python for execution.

import cutlass.cute as cute
import torch
from cutlass.cute import from\_dlpack
import cutlass.cute.cuda as cuda

\# Load module from object file
module \= cute.runtime.load\_module("./artifacts/print\_tensor\_example.o")
\# or
module \= cute.runtime.load\_module("./artifacts/libprint\_tensor\_example.so")

\# Prepare data
a \= torch.arange(160, dtype\=torch.float32, device\="cuda").reshape(16, 10)
a\_cute \= from\_dlpack(a).mark\_layout\_dynamic()
stream \= cuda.CUstream(0)

\# Call the function (no JIT compilation needed!)
module.print\_tensor(a\_cute, stream\=stream)

\# This will fail because 'non\_existing\_api' was not exported:
\# module.non\_existing\_api()

Copy to clipboard

### C++ Integration with Static Linking[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#c-integration-with-static-linking "Link to this heading")

Integrate compiled kernels directly into your C++ executable during the build process. The generated header file supplies the necessary API for loading the module and invoking the function.

Example:

#include "print\_tensor\_example.h"
#include <cuda\_runtime.h>

void run\_print\_tensor() {
    // Prepare tensor, the tensor declaration is in the header file
    print\_tensor\_Tensor\_a\_t tensor\_a;
    tensor\_a.data \= nullptr; // GPU memory is set to nullptr.
    // Set dynamic shapes and strides
    tensor\_a.dynamic\_shapes\[0\] \= 32;
    tensor\_a.dynamic\_shapes\[1\] \= 16;
    tensor\_a.dynamic\_strides\[0\] \= 16;

    // Create stream
    cudaStream\_t stream;
    cudaStreamCreate(&stream);

    // Load module before calling the kernel
    print\_tensor\_Kernel\_Module\_t module;
    print\_tensor\_Kernel\_Module\_Load(&module);

    // Call the kernel; the kernel wrapper function is defined in the header file
    cute\_dsl\_print\_tensor\_wrapper(&module, &tensor\_a, stream);

    // Cleanup
    print\_tensor\_Kernel\_Module\_Unload(&module);
    cudaStreamDestroy(stream);
}

Copy to clipboard

The `print_tensor_example.h` header file is generated by the `export_to_c` interface. It includes:

-   The `print_tensor_Kernel_Module_t` type: Represents the kernel module.
-   The `print_tensor_Tensor_a_t` type: A tensor-specific type that defines the ABI for a particular CuTe tensor.
-   The `cute_dsl_print_tensor_wrapper` function: The user-facing entry point to invoke the kernel.

The compilation of the C++ executable requires the `libcuda_dialect_runtime.so` or `libcuda_dialect_runtime_static.a` library which is involved in `<wheel_install_path>/lib`, along with the CUDA driver and runtime libraries, to function properly.

### C++ Integration with Dynamic Loading[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#c-integration-with-dynamic-loading "Link to this heading")

Dynamically load pre-compiled object files or shared libraries at runtime. By including the `CuteDSLRuntime.h` header, you can load the module, look up exported functions, and invoke them.

#include "CuteDSLRuntime.h"
#include <cuda\_runtime.h>

void run\_print\_tensor() {
    // Load module from shared library
    CuteDSLRT\_Module\_t \*module \= nullptr;
    CuteDSLRT\_Error\_t err \= CuteDSLRT\_Module\_Load(
        &module,
        "./artifacts/libprint\_tensor\_example.so"
    );
    // or
    CuteDSLRT\_Error\_t err \= CuteDSLRT\_Module\_Load(
        &module,
        "./artifacts/print\_tensor\_example.o"
    );
    check\_error(err);

    // Lookup function
    CuteDSLRT\_Function\_t \*func \= nullptr;
    err \= CuteDSLRT\_Module\_Get\_Function(&func, module, "print\_tensor");
    check\_error(err);

    // Prepare arguments, matching the argument type defined in the header file
    typedef struct {
        void \*data;
        int32\_t dynamic\_shapes\[2\];
        int64\_t dynamic\_strides\[1\];
    } print\_tensor\_Tensor\_a\_t;

    print\_tensor\_Tensor\_a\_t tensor\_a;
    tensor\_a.data \= nullptr;
    tensor\_a.dynamic\_shapes\[0\] \= 32;
    tensor\_a.dynamic\_shapes\[1\] \= 16;
    tensor\_a.dynamic\_strides\[0\] \= 16;

    // Create stream
    cudaStream\_t stream;
    cudaStreamCreate(&stream);

    // Call the function; the runtime function accepts packed arguments, refer to the wrapper in the header file
    int ret;
    void\* args\[\] \= {&tensor\_a, &stream, &ret};
    err \= CuteDSLRT\_Function\_Run(func, args, 3);
    check\_error(err);
    cudaStreamSynchronize(stream);

    // Cleanup
    CuteDSLRT\_Module\_Destroy(module);
    cudaStreamDestroy(stream);
}

Copy to clipboard

The `CuteDSLRuntime.h` header file can be found in `<wheel_install_path>/include`. It includes:

-   The `CuteDSLRT_Error_t` type: Indicates error status.
-   The `CuteDSLRT_Module_Load` function: Loads the module.
-   The `CuteDSLRT_Module_Get_Function` function: Gets a function from the loaded module. The runtime API will load the CUDA module for kernel execution.
-   The `CuteDSLRT_Function_Run` function: Runs the function.
-   The `CuteDSLRT_Module_Destroy` function: Destroys the module.

The compilation of the C++ executable requires the `libcute_dsl_runtime.so` library which is involved in `<wheel_install_path>/lib`, along with the CUDA driver and runtime libraries, to function properly.

## Supported Argument Types[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#supported-argument-types "Link to this heading")

CuTe DSL supports the following argument types:

-   `cute.Tensor`
-   `cute.Shape` / `cute.Coord` / `cute.Tile` / `cute.IntTuple` / `cute.Stride`
-   `cuda.CUstream`
-   `cutlass.Int8` / `cutlass.Int16` / `cutlass.Int32` / `cutlass.Int64` / `cutlass.Boolean`
-   `cutlass.Uint8` / `cutlass.Uint16` / `cutlass.Uint32` / `cutlass.Uint64`
-   `cutlass.Float32` / `cutlass.TFloat32` / `cutlass.Float64` / `cutlass.Float16`

Note that:

1.  `cute.Tensor` is a dynamic tensor type that only contains dynamic shapes and strides in its ABI representation. As a result, different compilations may produce different tensor ABIs. This is why declarations for each tensor type are included in the generated header file.
2.  `strides` in `cute.Tensor` are determined by the `use_32bit_strides` compile argument. When `use_32bit_strides` is set to `True`, the strides are 32-bit; when set to `False`, they are 64-bit.
3.  Currently, custom types are not supported for AOT compilation.

## Object File Compatibility Issues[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#object-file-compatibility-issues "Link to this heading")

The object file generated by CuTe DSL depends on the CUDA runtime library. Therefore, ensure that the version of the CUDA runtime/toolkit library matches the version used by CuTe DSL. Otherwise, ABI compatibility with the CUDA runtime cannot be guaranteed.

When using C++ static linking integration, compatibility is assured because the header and object files are generated together and guaranteed to match.

For C++ dynamic loading integration and Python loading, the binary file is loaded at runtime. To ensure compatibility, version information is embedded in the metadata of the generated binary file. At runtime, this version information is checked, and if it does not match the expected version, the binary file will be rejected.

## Relation to Apache TVM FFI AOT[#](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/dsl_ahead_of_time_compilation.html#relation-to-apache-tvm-ffi-aot "Link to this heading")

Apache TVM FFI AOT offers a comparable capability, enabling TVM functions to be compiled into binary files that can be loaded and executed at runtime. For more information, see the section “Exporting Compiled Module” in [Compile with TVM FFI](https://docs.nvidia.com/cutlass/latest/media/docs/pythonDSL/cute_dsl_general/compile_with_tvm_ffi.html).

The primary distinction is that, when TVM FFI is enabled, CuTe DSL generates a dedicated wrapper function on top of the underlying CuTe ABI. This wrapper adheres to the calling conventions defined by TVM FFI. In contrast, the CuTe ABI entry function is specified directly in the generated header file, which affects how arguments must be provided.

For instance, with the TVM FFI wrapper function, users are able to pass in arguments such as `torch.Tensor` directly. However, when calling the CuTe ABI entry function, arguments should be provided as `cute.Tensor` types.

