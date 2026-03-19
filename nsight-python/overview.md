# Introduction[#](https://docs.nvidia.com/nsight-python/overview/introduction.html#introduction "Link to this heading")

**Nsight Python** is a Python kernel profiling interface that automates performance analysis across multiple kernel configurations using NVIDIA Nsight Tools.

With just a decorator and a context manager, you can benchmark kernel variants, collect detailed architectural metrics, prevent GPU throttling, and generate publication-quality visualizations—all from a single script. No boilerplate. No manual report parsing.

Built for researchers, engineers, and performance enthusiasts who want **real metrics** (not just wall-clock time), **at scale**, with **minimal code overhead**.

![Example Nsight Python visualization](https://docs.nvidia.com/nsight-python/_images/intro.png)

## Key Features[#](https://docs.nvidia.com/nsight-python/overview/introduction.html#key-features "Link to this heading")

-   Works with **any Python framework** (PyTorch, Triton, etc.)
-   Profiles **multiple kernel configurations** with one decorator
-   Collects **detailed GPU kernel metrics**, not just timings
-   Annotates kernel regions using a simple with nsight.annotate(…) context
-   **Prevents GPU throttling** using real-time NVML temperature monitoring
-   Automatically **aggregates and visualizes** performance results
-   Outputs structured data (CSV, plots) for publication or analysis

# Introduction[#](https://docs.nvidia.com/nsight-python/overview/introduction.html#introduction "Link to this heading")

**Nsight Python** is a Python kernel profiling interface that automates performance analysis across multiple kernel configurations using NVIDIA Nsight Tools.

With just a decorator and a context manager, you can benchmark kernel variants, collect detailed architectural metrics, prevent GPU throttling, and generate publication-quality visualizations—all from a single script. No boilerplate. No manual report parsing.

Built for researchers, engineers, and performance enthusiasts who want **real metrics** (not just wall-clock time), **at scale**, with **minimal code overhead**.

![Example Nsight Python visualization](https://docs.nvidia.com/nsight-python/_images/intro.png)

## Key Features[#](https://docs.nvidia.com/nsight-python/overview/introduction.html#key-features "Link to this heading")

-   Works with **any Python framework** (PyTorch, Triton, etc.)
-   Profiles **multiple kernel configurations** with one decorator
-   Collects **detailed GPU kernel metrics**, not just timings
-   Annotates kernel regions using a simple with nsight.annotate(…) context
-   **Prevents GPU throttling** using real-time NVML temperature monitoring
-   Automatically **aggregates and visualizes** performance results
-   Outputs structured data (CSV, plots) for publication or analysis

# Core Concepts[#](https://docs.nvidia.com/nsight-python/overview/core_concepts.html#core-concepts "Link to this heading")

Nsight Python requires two components working together to profile your GPU code:

-   [`@nsight.analyze.kernel`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel") - A decorator on your benchmark function that runs the profiler and collects metrics
-   [`nsight.annotate`](https://docs.nvidia.com/nsight-python/annotation.html#nsight.annotate "nsight.annotate") - A context manager (or decorator) used _inside_ your benchmark function to mark which kernel(s) to measure

**Both are required.** The `@nsight.analyze.kernel` decorator controls the profiling session, while `nsight.annotate` tells the profiler which specific code regions to measure.

@nsight.analyze.kernel  \# Controls profiling session
def benchmark(n):
    a \= torch.randn(n, n, device\="cuda")
    b \= torch.randn(n, n, device\="cuda")

    with nsight.annotate("matmul"):  \# Marks the kernel to measure
        c \= a @ b

Nsight Python operates through three key primitives:

**1\. Annotations** An [`annotation`](https://docs.nvidia.com/nsight-python/annotation.html#nsight.annotate "nsight.annotate") wraps a region of code that launches a GPU kernel and tags it for profiling. By default, each annotation should contain exactly one kernel launch. Annotations can be used as decorators or context managers:

@nsight.annotate("torch")
def torch\_kernel():
    ...

\# or
with nsight.annotate("cutlass4"):
    cutlass\_kernel()

If your annotated region launches multiple kernels, you have two options:

-   Use `replay_mode="range"` to profile the entire annotated range as a unit, with metrics associated with the range rather than individual kernels
-   Use `combine_kernel_metrics` to specify how to aggregate metrics across individual kernels (e.g., sum the runtimes)

See the [`@nsight.analyze.kernel`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel") documentation for details on these parameters.

**2\. Kernel Analysis Decorator** Use [`nsight.analyze.kernel()`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel") to annotate a benchmark function. Nsight Python will rerun this function one configuration at a time. You can provide configurations in two ways:

-   **At decoration time** using the configs parameter.
-   **At function call time** by passing configs directly as an argument when invoking the decorated function.

@nsight.analyze.kernel
def benchmark(s):
    ...

benchmark(configs\=\[(1024,), (2048,)\])

**3\. Plot Decorator** Add [`nsight.analyze.plot()`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.plot "nsight.analyze.plot") to automatically generate plots from your profiling runs.

@nsight.analyze.plot(filename\="plot.png", ylabel\="Runtime (ns)")
@nsight.analyze.kernel(configs\=\[(1024,), (2048,)\])
def benchmark(s):
    ...

# Architecture[#](https://docs.nvidia.com/nsight-python/overview/architecture.html#architecture "Link to this heading")

Nsight Python’s architecture consists of:

1.  **Collection**: Runs your benchmark under NVIDIA Nsight Compute. See [Collection](https://docs.nvidia.com/nsight-python/collection/index.html).
2.  **Extraction**: Parses Nsight reports using ncu-report and associates metrics with annotations/configs. See [Extraction](https://docs.nvidia.com/nsight-python/extraction.html).
3.  **Visualization**: Converts data to a pandas DataFrame and optionally plots results via matplotlib. See [Visualization](https://docs.nvidia.com/nsight-python/visualization.html).

Internally, Nsight Python:

-   Inserts NVTX ranges for each annotation
-   Profiles each configuration for multiple runs
-   Associates collected metrics with annotations
-   Supports TFLOPs, speedup, and other derived metrics

## Advanced Options[#](https://docs.nvidia.com/nsight-python/overview/architecture.html#advanced-options "Link to this heading")

**Metric Selection** Nsight Python collects gpu\_\_time\_duration.sum by default. To collect other NVIDIA Nsight Compute metrics:

@nsight.analyze.kernel(metrics\=\["sm\_\_throughput.avg.pct\_of\_peak\_sustained\_elapsed"\])
def benchmark1(...):
    ...

\# or
@nsight.analyze.kernel(
    metrics\=\[
        "smsp\_\_sass\_inst\_executed\_op\_shared\_ld.sum",
        "smsp\_\_sass\_inst\_executed\_op\_shared\_st.sum",
        "launch\_\_sm\_count",
    \],
)
def benchmark2(...):
    ...

**Derived Metrics** Define a Python function that computes custom metrics like TFLOPS based on runtime and input configuration:

def tflops\_scalar(t, m, n, k):
    return 2 \* m \* n \* k / (t / 1e9) / 1e12

@nsight.analyze.kernel(configs\=\[(1024, 1024, 64)\], derive\_metric\=tflops\_scalar)
def benchmark1(m, n, k):
    ...

\# or
def tflops\_dict(t, m, n, k):
    return {"TFLOPS": 2 \* m \* n \* k / (t / 1e9) / 1e12}

@nsight.analyze.kernel(configs\=\[(1024, 1024, 64)\], derive\_metric\=tflops\_dict)
def benchmark2(m, n, k):
    ...

\# or
def tflops\_and\_arith\_intensity(t, m, n, k):
    tflops \= 2 \* m \* n \* k / (t / 1e9) / 1e12
    memory\_bytes \= (m \* k + k \* n + m \* n) \* 4
    return {
        "TFLOPS": tflops,
        "ArithIntensity": tflops / memory\_bytes,
    }

@nsight.analyze.kernel(configs\=\[(1024, 1024, 64)\], derive\_metric\=tflops\_and\_arith\_intensity)
def benchmark3(m, n, k):
    ...

**Relative Metrics** Compare performance against a baseline annotation:

@nsight.analyze.kernel(normalize\_against\="torch.einsum")
def benchmark(...):
    ...

**Multiple Annotations** Profile multiple implementations side-by-side:

with nsight.annotate("torch"):
    torch\_impl(...)

with nsight.annotate("cutlass4"):
    cutlass\_impl(...)

**Multiple Config Parameters**

Nsight Python supports multi-dimensional config tuples which can contain arbitrary Python objects:

import itertools
configs \= list(itertools.product(\[512, 1024\], \[64, 128\]))  \# (seqlen, head\_dim)

@nsight.analyze.kernel(configs\=configs)
def benchmark(seqlen, head\_dim):
    ...

