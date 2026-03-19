# nsight.analyze[#](https://docs.nvidia.com/nsight-python/analyze.html#nsight-analyze "Link to this heading")

Note

`@nsight.analyze.kernel` runs the profiling session, but you must use [`nsight.annotate`](https://docs.nvidia.com/nsight-python/annotation.html#nsight.annotate "nsight.annotate") inside your decorated function to mark which kernel(s) to measure. See [Core Concepts](https://docs.nvidia.com/nsight-python/overview/core_concepts.html) for details.

The decorator returns a [`ProfileResults`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults "nsight.collection.core.ProfileResults") object containing the collected metrics. See [Core Abstractions](https://docs.nvidia.com/nsight-python/collection/core.html) for full API documentation.

_class_ nsight.analyze.kernel(

_\_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_\*_,

_configs: [Iterable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_runs: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") \= 1_,

_derive\_metric: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)") | [dict](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)"), [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_normalize\_against: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_output: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['quiet', 'progress', 'verbose'\] \= 'progress'_,

_metrics: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] \= \['gpu\_\_time\_duration.sum'\]_,

_ignore\_kernel\_list: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_clock\_control: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['base', 'none'\] \= 'none'_,

_cache\_control: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['all', 'none'\] \= 'all'_,

_replay\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['kernel', 'range'\] \= 'kernel'_,

_thermal\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['auto', 'manual', 'off'\] \= 'auto'_,

_thermal\_wait: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_cont: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_timeout: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_combine\_kernel\_metrics: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)"), [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\], [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_output\_prefix: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_output\_csv: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_,

)[#](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "Link to this definition")

Bases:

A decorator that collects profiling data using NVIDIA Nsight Compute.

Can be used with or without parentheses:

-   `@nsight.analyze.kernel` (no parentheses)
-   `@nsight.analyze.kernel()` (empty parentheses)
-   `@nsight.analyze.kernel(configs=..., runs=10)` (with arguments)

The decorator returns a wrapped version of your function with the following signature:

def wrapped\_function(\*args, configs\=None, \*\*kwargs) \-> ProfileResults

Where:

-   `*args`: Original function arguments (when providing a single config)
-   `configs`: Optional iterable of configurations (overrides decorator-time configs)
-   `**kwargs`: Original function keyword arguments
-   Returns `ProfileResults` object containing profiling data

Parameters:

-   **configs** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Iterable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]) –
    
    An iterable of configurations to run the function with. Each configuration can be either:
    
    -   A sequence of arguments to pass to the decorated function:
        
        > configs = \[ \[1, 2\], \[3, 4\], \]
        
    -   If the decorated function takes only one argument, it can be a scalar value:
        
        > configs = \[1, 2, 3, 4\]
        
    
    If the configs are not provided at decoration time, they must be provided when calling the decorated function.
    
-   **runs** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")) – Number of times each configuration should be executed.
-   **derive\_metric** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)") | [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\]\]) –
    
    A function to transform the collected metrics. This can be used to compute derived metrics like TFLOPs that cannot be captured by ncu directly. The function takes the metric values and the arguments of the profile-decorated function and returns the new metrics. Return value can be either:
    
    -   A single value (float/int): Will be added as a new metric with the function name as the metric name. For lambda functions, the metric name will be `"<lambda>"`.
    -   A dictionary: Keys will be used as metric names, values as metric values.
    
    The parameter order requirements for the custom function:
    
    -   First several arguments: Must exactly match the order of metrics declared in the @kernel decorator. These arguments will receive the actual measured values of those metrics.
    -   Remaining arguments: Must exactly match the signature of the decorated function. In other words, the original function’s parameters are passed in order.
    
    See the examples for concrete use cases.
    
-   **normalize\_against** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – Annotation name to normalize metrics against (computes current / baseline). Combine with `derive_metric` to compute speedup (reciprocal of normalized value).
-   **metrics** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – The metrics to collect. By default, kernel runtimes in nanoseconds are collected. Default: `["gpu__time_duration.sum"]`. To see the available metrics on your system, use the command: `ncu --query-metrics`.
-   **ignore\_kernel\_list** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – List of kernel names to ignore. If you call a library within an annotated range context, you might not have precise control over which and how many kernels are being launched. If some of these kernels should be ignored in the profile, their names can be provided in this parameter. Default: `None`
-   **combine\_kernel\_metrics** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\], [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\]) – By default, Nsight Python expects one kernel launch per annotation. In case an annotated region launches multiple kernels, instead of failing the profiling run, you can specify how to summarize the collected metrics into a single number. For example, if we profile runtime and want to sum the times of all kernels we can specify `combine_kernel_metrics = lambda x, y: x + y`. The function should take two arguments and return a single value. Default: `None`.
-   **clock\_control** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'base'`, `'none'`\]) –
    
    Control the behavior of the GPU clocks during profiling. Allowed values:
    
    -   `"base"`: GPC and memory clocks are locked to their respective base frequency during profiling. This has no impact on thermal throttling. Note that actual clocks might still vary, depending on the level of driver support for this feature. As an alternative, use nvidia-smi to lock the clocks externally and set this option to `"none"`.
    -   `"none"`: No GPC or memory frequencies are changed during profiling.
    
    Default: `"none"`
    
-   **cache\_control** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'all'`, `'none'`\]) –
    
    Control the behavior of the GPU caches during profiling. Allowed values:
    
    -   `"all"`: All GPU caches are flushed before each kernel replay iteration during profiling. While metric values in the execution environment of the application might be slightly different without invalidating the caches, this mode offers the most reproducible metric results across the replay passes and also across multiple runs of the target application.
    -   `"none"`: No GPU caches are flushed during profiling. This can improve performance and better replicates the application behavior if only a single kernel replay pass is necessary for metric collection. However, some metric results will vary depending on prior GPU work, and between replay iterations. This can lead to inconsistent and out-of-bounds metric values.
    
    Default: `"all"`
    
-   **replay\_mode** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'kernel'`, `'range'`\]) –
    
    Mechanism used for replaying a kernel launch multiple times to collect selected metrics. Allowed values:
    
    -   `"kernel"`: Replay individual kernel launches during the execution of the application.
    -   `"range"`: Replay range of kernel launches during the execution of the application. Ranges are defined using nsight.annotate.
    
    Default: `"kernel"`
    
-   **thermal\_mode** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'auto'`, `'manual'`, `'off'`\]) –
    
    Controls GPU thermal management mode. Default: `"auto"`
    
    Monitors GPU thermal headroom (T.Limit) and pauses profiling when GPU gets too hot, resuming after cooling. Prevents thermal throttling from affecting profiling accuracy.
    
    **Modes:**
    
    -   `"auto"`: Adaptive mode - automatically adjusts thermal\_cont threshold based on GPU heating behavior.
    -   `"manual"`: Fixed mode - uses specified thermal\_wait and thermal\_cont thresholds without adaptation.
    -   `"off"`: Thermal control disabled - no monitoring or pausing.
    
-   **thermal\_wait** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")\]) –
    
    Thermal headroom threshold (T.Limit in °C) that triggers cooling pause.
    
    When GPU thermal headroom drops to this value, profiling pauses and waits for the GPU to cool down. Lower values allow the GPU to run hotter before pausing (more aggressive, faster profiling, higher throttling risk).
    
    If `None`, uses default value (10°C). Applied in both “auto” and “manual” modes.
    
-   **thermal\_cont** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")\]) –
    
    Thermal headroom threshold (T.Limit in °C) to resume profiling after cooling.
    
    After a cooling pause, profiling resumes once GPU thermal headroom reaches this value. Higher values mean the GPU cools more before resuming (safer, fewer cooling cycles, but slower overall profiling time).
    
    If `None`, uses default value (20°C). In “auto” mode, this value adapts based on workload characteristics. In “manual” mode, it remains fixed.
    
    **Requirement:** Must be greater than thermal\_wait.
    
-   **thermal\_timeout** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")\]) – Maximum wait time in seconds for GPU to cool down. Default: 180 seconds
-   **output** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'quiet'`, `'progress'`, `'verbose'`\]) –
    
    Controls the verbosity level of the output.
    
    -   `"quiet"`: Suppresses all output.
    -   `"progress"`: Shows a progress bar along with details about profiling and data extraction progress.
    -   `"verbose"`: Displays the progress bar, configuration-specific logs, and profiler logs.
    
-   **output\_prefix** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) –
    
    When specified, all intermediate profiler files are created with this prefix. For example, if output\_prefix=”/home/user/run1\_”, the profiler will generate:
    
    -   /home/user/run1\_ncu-output-<name\_of\_decorated\_function>-<run\_id>.log
    -   /home/user/run1\_ncu-output-<name\_of\_decorated\_function>-<run\_id>.ncu-rep
    -   /home/user/run1\_processed\_data-<name\_of\_decorated\_function>-<run\_id>.csv
    -   /home/user/run1\_profiled\_data-<name\_of\_decorated\_function>-<run\_id>.csv
    
    Where `<run_id>` is a counter that increments each time the decorated function is called within the same Python process (0, 1, 2, …). This allows calling the same decorated function multiple times without overwriting previous results.
    
    if `None`, the intermediate profiler files are created in a directory under <TEMP\_DIR> prefixed with nspy. <TEMP\_DIR> is the system’s temporary directory ($TMPDIR or /tmp on Linux, %TEMP% on Windows).
    
-   **output\_csv** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) –
    
    Controls whether to dump raw and processed profiling data to CSV files. Default: `False`. When enabled, two CSV files are generated:
    
    **Raw Data CSV** (`profiled_data-<function_name>-<run_id>.csv`): Contains unprocessed profiling data with one row per run per configuration. Columns include:
    
    > -   `Annotation`: Name of the annotated region being profiled
    > -   `Value`: Raw metric values collected by the profiler
    > -   `Metric`: The metrics being collected (e.g., `gpu__time_duration.sum`) and the metrics being derived
    > -   `Kernel`: Name of the GPU kernel(s) launched
    > -   `GPU`: GPU device name
    > -   `Host`: Host machine name
    > -   `ComputeClock`: GPU compute clock frequency during profiling
    > -   `MemoryClock`: GPU memory clock frequency during profiling
    > -   `<param_name>`: One column for each parameter of the decorated function
    
    **Processed Data CSV** (`processed_data-<function_name>-<run_id>.csv`): Contains aggregated statistics across multiple runs. Columns include:
    
    > -   `Annotation`: Name of the annotated region being profiled
    > -   `<param_name>`: One column for each parameter of the decorated function
    > -   `AvgValue`: Average metric values across all runs
    > -   `StdDev`: Standard deviation of the metrics across runs
    > -   `MinValue`: Minimum metric values observed
    > -   `MaxValue`: Maximum metric values observed
    > -   `NumRuns`: Number of runs used for aggregation
    > -   `CI95_Lower`: Lower bound of the 95% confidence interval
    > -   `CI95_Upper`: Upper bound of the 95% confidence interval
    > -   `RelativeStdDevPct`: Standard deviation as a percentage of the mean
    > -   `StableMeasurement`: Boolean indicating if the measurement is stable (low variance). The measurement is stable if `RelativeStdDevPct` < 2 % .
    > -   `Metric`: The metrics being collected and the metrics being derived
    > -   `Kernel`: Name of the GPU kernel(s) launched
    > -   `GPU`: GPU device name
    > -   `Host`: Host machine name
    > -   `ComputeClock`: GPU compute clock frequency
    > -   `MemoryClock`: GPU memory clock frequency
    
-   **\_func** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[__...__\]__,_ _None__\]_ _|_ _None_)

Return type:

[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`ProfileResults`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults "nsight.collection.core.ProfileResults")\] | [`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\]\], [`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`ProfileResults`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults "nsight.collection.core.ProfileResults")\]\]

_class_ nsight.analyze.plot(

_filename: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= 'plot.png'_,

_metric: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_\*_,

_title: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= 'Nsight Analyze Kernel Plot Results'_,

_ylabel: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_annotate\_points: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_,

_show\_aggregate: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_plot\_type: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= 'line'_,

_plot\_width: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") \= 6_,

_plot\_height: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") \= 4_,

_row\_panels: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_col\_panels: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_x\_keys: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_print\_data: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_,

_variant\_fields: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_variant\_annotations: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_plot\_callback: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[Figure](https://matplotlib.org/stable/api/_as_gen/matplotlib.figure.Figure.html#matplotlib.figure.Figure "(in Matplotlib v3.10.8)")\], [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

)[#](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.plot "Link to this definition")

Bases:

A decorator that plots the result of a profile-decorated function. This decorator is intended to be only used on functions that have been decorated with @nsight.analyze.kernel.

The decorator returns a wrapped version of your function that maintains the same signature as the underlying `@nsight.analyze.kernel` decorated function:

def wrapped\_function(\*args, configs\=None, \*\*kwargs) \-> ProfileResults

The function returns `ProfileResults` and generates a plot as a side effect.

Example usage:

@nsight.analyze.plot(title\="My Plot")
@nsight.analyze.kernel
def my\_func(...):

Parameters:

-   **metric** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – The specific metric to plot (e.g., `gpu__time_duration.sum`). If None (default), the function will plot the single metric found in the `ProfileResults` object containing profiling data, if only one exists, otherwise it will raise an error if multiple metrics are present. Default: `None`
-   **filename** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Filename to save the plot. Default: `'plot'`
-   **title** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Title for the plot. Default: `'Nsight Analyze Kernel Plot Results'`
-   **ylabel** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – Label for the y-axis in the generated plot. Default: `f'{metric} (avg: {runs} runs)'`
-   **annotate\_points** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – If True, annotate the points with their numeric value in the plot. Default: `False`
-   **show\_aggregate** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – If “avg”, show the average value in the plot. If “geomean”, show the geometric mean value in the plot. Default: None
-   **plot\_type** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Type of plot to generate. Options are ‘line’ or ‘bar’. Default: `'line'`
-   **plot\_width** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")) – Width of the plot in inches. Default: `6`
-   **plot\_height** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")) – Height of the plot in inches. Default: `4`
-   **row\_panels** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – Enables generating subplots along the horizontal axis for each unique values of the listed function parameters. The provided strings must each match one argument of the nsight.analyze.kernel-decorated function. Default: `None`
-   **col\_panels** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – Enables generating subplots along the vertical axis for each unique values of the listed function parameters. The provided strings must each match one argument of the nsight.analyze.kernel-decorated function. Default: `None`
-   **x\_keys** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – List of fields to use for the x-axis. By default, we use all parameters of the decorated function except those specified in row\_panels and col\_panels.
-   **print\_data** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – If True, print the data used for plotting. Default: `False`
-   **variant\_fields** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – List of config fields to use as variant fields (lines).
-   **variant\_annotations** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – List of annotated range names for which to apply variant splitting. The provided strings must each match one of the names defined using nsight.annotate.
-   **plot\_callback** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[_[_Figure_](https://matplotlib.org/stable/api/_as_gen/matplotlib.figure.Figure.html#matplotlib.figure.Figure "(in Matplotlib v3.10.8)")_\]__,_ _None__\]_ _|_ _None_)

Return type:

[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`ProfileResults`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults "nsight.collection.core.ProfileResults")\]\], [`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`ProfileResults`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults "nsight.collection.core.ProfileResults")\]\]

_class_ nsight.analyze.ignore\_failures[#](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.ignore_failures "Link to this definition")

Bases:

Context manager that ignores errors in a code block.

Useful when you want failures in the block to be suppressed so they do not propagate and cause the decorated function to fail.

Return type:

[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")


# nsight.annotate[#](https://docs.nvidia.com/nsight-python/annotation.html#nsight-annotate "Link to this heading")

Note

`nsight.annotate` is used to mark which code regions to profile, but it does not run the profiler by itself. You must use it inside a function decorated with [`@nsight.analyze.kernel`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel") to actually collect metrics. See [Core Concepts](https://docs.nvidia.com/nsight-python/overview/core_concepts.html) for details.

_class_ nsight.annotate(_name: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")_, _ignore\_failures: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_)[#](https://docs.nvidia.com/nsight-python/annotation.html#nsight.annotate "Link to this definition")

Bases: `annotate`

A decorator/context-manager hybrid for marking profiling regions. The encapsulated code will be profiled and associated with an NVTX range of the given annotate name.

Example usage:

\# as context manager
with nsight.annotate("name"):
    \# your kernel launch here

\# as decorator
@nsight.annotate("name")
def your\_kernel\_launcher(...):
    ...

Parameters:

-   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Name of the annotation to be used for profiling. Annotation names must be unique within a single profiling run to ensure unambiguous results.
-   **ignore\_failures** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Flag indicating whether to ignore failures in the annotate context. If set to `True`, any exceptions raised within the context will be ignored, and the profiling will continue. The measured metric for this run will be set to NaN. Default: `False`

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.14)") – If attempting to enter a nested annotation context, or if an annotation with the same name has already been used in this profiling run. Nested annotations are not supported and annotation names must be unique within a profiling run to avoid incorrect profiling results.

Note

All annotations are created under the NVTX domain `"nsight-python"`. This domain is used internally to filter and identify Nsight Python annotations in profiling tools.

Note

Nested annotations are currently not supported. However, since each annotation is expected to contain a single kernel launch by default, nested annotations should not be necessary in typical usage scenarios.