# Core Abstractions[#](https://docs.nvidia.com/nsight-python/collection/core.html#module-nsight.collection.core "Link to this heading")

_class_ nsight.collection.core.NsightCollector[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightCollector "Link to this definition")

Bases: [`ABC`](https://docs.python.org/3/library/abc.html#abc.ABC "(in Python v3.14)")

_abstract_ collect(

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]_,

_configs: [Iterable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]_,

_settings: [ProfileSettings](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "nsight.collection.core.ProfileSettings")_,

)[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightCollector.collect "Link to this definition")

Collects profiling data for the given function and configurations.

Parameters:

-   **func** ([`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]) – The function to be profiled.
-   **configs** ([`Iterable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]) – iterable of configurations for profiling.
-   **settings** ([`ProfileSettings`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "nsight.collection.core.ProfileSettings")) – Settings for profiling.

Return type:

`DataFrame` | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")

Returns:

Collected profiling data.

_class_ nsight.collection.core.NsightProfiler(

_settings: [ProfileSettings](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "nsight.collection.core.ProfileSettings")_,

_collector: [NsightCollector](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightCollector "nsight.collection.core.NsightCollector")_,

)[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightProfiler "Link to this definition")

Bases: [`object`](https://docs.python.org/3/library/functions.html#object "(in Python v3.14)")

A decorator class for profiling functions using Nsight Python’s profiling tools.

This class allows you to wrap a function with profiling capabilities, collecting performance data and saving the results to CSV files. It uses a collector to gather raw profiling data and processes it according to the provided settings.

Parameters:

-   **settings** ([_ProfileSettings_](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "nsight.collection.core.ProfileSettings"))
-   **collector** ([_NsightCollector_](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightCollector "nsight.collection.core.NsightCollector"))

settings[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightProfiler.settings "Link to this definition")

Configuration settings for profiling, including normalization, and other options.

collector[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightProfiler.collector "Link to this definition")

The collector responsible for gathering raw profiling data.

\_\_call\_\_(_func_)[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightProfiler.__call__ "Link to this definition")

Wraps the given function with profiling logic. Collects raw profiling data, processes it, and saves the results to CSV files. Returns the processed data.

_class_ nsight.collection.core.ProfileResults(_results: DataFrame_)[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults "Link to this definition")

Bases: [`object`](https://docs.python.org/3/library/functions.html#object "(in Python v3.14)")

Class to hold profile results for Nsight Python

Parameters:

**results** (_DataFrame_)

to\_dataframe()[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileResults.to_dataframe "Link to this definition")

Returns the processed profiling data as a pandas DataFrame.

This DataFrame contains aggregated statistics across multiple runs for each configuration and annotation combination. The data is equivalent to what is written to the `processed_data-<function_name>-<run_id>.csv` file when `output_csv=True`.

Returns:

-   `Annotation`: Name of the annotated region being profiled
-   `<param_name>`: One column for each parameter of the decorated function
-   `AvgValue`: Average metric values across all runs
-   `StdDev`: Standard deviation of the metrics across runs
-   `MinValue`: Minimum metric values observed
-   `MaxValue`: Maximum metric values observed
-   `NumRuns`: Number of runs used for aggregation
-   `CI95_Lower`: Lower bound of the 95% confidence interval
-   `CI95_Upper`: Upper bound of the 95% confidence interval
-   `RelativeStdDevPct`: Standard deviation as a percentage of the mean
-   `StableMeasurement`: Boolean indicating if the measurement is stable (low variance). The measurement is stable if `RelativeStdDevPct` < 2 % .
-   `Metric`: The metrics being collected and the metrics being derived
-   `Kernel`: Name of the GPU kernel(s) launched
-   `GPU`: GPU device name
-   `Host`: Host machine name
-   `ComputeClock`: GPU compute clock frequency
-   `MemoryClock`: GPU memory clock frequency

Return type:

Processed profiling data with the following columns

_class_ nsight.collection.core.ProfileSettings(

_configs: [Iterable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_runs: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")_,

_output\_progress: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

_output\_detailed: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

_derive\_metric: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)") | [dict](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)"), [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_normalize\_against: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_thermal\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['auto', 'manual', 'off'\]_,

_thermal\_wait: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_thermal\_cont: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_thermal\_timeout: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_output\_prefix: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_output\_csv: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

)[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "Link to this definition")

Bases: [`object`](https://docs.python.org/3/library/functions.html#object "(in Python v3.14)")

Class to hold profile settings for Nsight Python.

Parameters:

-   **configs** ([_Iterable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")_\[_[_Any_](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")_\]_ _|_ _None_)
-   **runs** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)"))
-   **output\_progress** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))
-   **output\_detailed** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))
-   **derive\_metric** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[__...__\]__,_ [_float_](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)") _|_ [_dict_](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.14)")_\[_[_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")_,_ [_float_](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")_\]__\]_ _|_ _None_)
-   **normalize\_against** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") _|_ _None_)
-   **thermal\_mode** ([_Literal_](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")_\[__'auto'__,_ _'manual'__,_ _'off'__\]_)
-   **thermal\_wait** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_cont** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_timeout** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **output\_prefix** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") _|_ _None_)
-   **output\_csv** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))

configs_: [`Iterable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.configs "Link to this definition")

An iterable of configurations to run the function with. Each configuration can either be a sequence of arguments or if the decorated function takes only one argument, can also be a scalar value. If the configs are not provided at decoration time, they must be provided when calling the decorated function.

derive\_metric_: [`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)") | [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\] | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.derive_metric "Link to this definition")

A function to transform the collected metrics. This can be used to compute derived metrics like TFLOPs that cannot be captured by ncu directly. The function takes the metric values and the arguments of the profile-decorated function and returns the new metrics. See the examples for concrete use cases.

normalize\_against_: [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.normalize_against "Link to this definition")

Annotation name to normalize metrics against. This is useful to compute relative metrics like speedup.

output\_csv_: [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.output_csv "Link to this definition")

Controls whether to output raw and processed profiling data to CSV files

output\_detailed_: [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.output_detailed "Link to this definition")

Will display a progress bar, detailed output for each config along with the profiler logs

output\_prefix_: [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.output_prefix "Link to this definition")

All intermediate profiler files are created with this prefix

output\_progress_: [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.output_progress "Link to this definition")

Will display a progress bar on stdout during profiling

runs_: [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.runs "Link to this definition")

Number of times each configuration should be executed.

thermal\_cont_: [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.thermal_cont "Link to this definition")

Thermal headroom threshold (T.Limit in °C) to resume profiling after cooling.

After a cooling pause, profiling resumes once GPU thermal headroom reaches this value. Higher values mean the GPU cools more before resuming (safer, fewer cooling cycles, but slower overall profiling time).

If None, uses default value (20°C). In “auto” mode, this value adapts based on workload characteristics. In “manual” mode, it remains fixed.

**Requirement:** Must be greater than thermal\_wait.

thermal\_mode_: [`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'auto'`, `'manual'`, `'off'`\]_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.thermal_mode "Link to this definition")

Controls GPU thermal management mode.

Monitors GPU thermal headroom (T.Limit) and pauses profiling when GPU gets too hot, resuming after cooling. Prevents thermal throttling from affecting profiling accuracy.

**T.Limit (Thermal Limit)** T.Limit is the temperature margin before the GPU starts throttling performance to protect itself. It represents: Max\_Safe\_Temperature - Current\_Temperature. - High T.Limit (e.g., 40°C): GPU is cool, plenty of headroom - Low T.Limit (e.g., 5°C): GPU is hot, approaching thermal throttling

**Modes:** - “auto”: Adaptive mode - automatically adjusts thermal\_cont threshold based on GPU heating behavior - “manual”: Fixed mode - uses specified thermal\_wait and thermal\_cont thresholds without adaptation - “off”: Thermal control disabled.

thermal\_timeout_: [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.thermal_timeout "Link to this definition")

Maximum wait time in seconds for GPU to cool down. If None, uses default value (180 seconds).

thermal\_wait_: [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings.thermal_wait "Link to this definition")

Thermal headroom threshold (T.Limit in °C) that triggers cooling pause.

When GPU thermal headroom drops to this value, profiling pauses and waits for the GPU to cool down. Lower values allow the GPU to run hotter before pausing (more aggressive, faster profiling, higher throttling risk).

If None, uses default value (10°C). Applied in both “auto” and “manual” modes.

nsight.collection.core.run\_profile\_session(

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\]_,

_configs: [List](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]_,

_runs: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")_,

_output\_progress: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

_output\_detailed: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

_thermal\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['auto', 'manual', 'off'\]_,

_thermal\_wait: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_cont: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_timeout: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

)[#](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.run_profile_session "Link to this definition")

Return type:

[`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")

Parameters:

-   **func** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[__...__\]__,_ _None__\]_)
-   **configs** ([_List_](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")_\[_[_Sequence_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")_\[_[_Any_](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")_\]__\]_)
-   **runs** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)"))
-   **output\_progress** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))
-   **output\_detailed** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))
-   **thermal\_mode** ([_Literal_](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")_\[__'auto'__,_ _'manual'__,_ _'off'__\]_)
-   **thermal\_wait** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_cont** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_timeout** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)


# NVIDIA Nsight Compute Collector[#](https://docs.nvidia.com/nsight-python/collection/ncu.html#module-nsight.collection.ncu "Link to this heading")

Collection utilities for profiling Nsight Python runs using NVIDIA Nsight Compute (ncu).

This module contains logic for launching NVIDIA Nsight Compute with appropriate settings. NCU is instructed to profile specific code sections marked by NVTX ranges - the Nsight Python annotations.

_class_ nsight.collection.ncu.NCUCollector(

_metrics: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] \= \['gpu\_\_time\_duration.sum'\]_,

_ignore\_kernel\_list: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_combine\_kernel\_metrics: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)"), [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\], [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_clock\_control: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['base', 'none'\] \= 'none'_,

_cache\_control: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['all', 'none'\] \= 'all'_,

_replay\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['kernel', 'range'\] \= 'kernel'_,

)[#](https://docs.nvidia.com/nsight-python/collection/ncu.html#nsight.collection.ncu.NCUCollector "Link to this definition")

Bases: [`NsightCollector`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.NsightCollector "nsight.collection.core.NsightCollector")

NCU collector for Nsight Python.

Parameters:

-   **metrics** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – Metrics to collect from NVIDIA Nsight Compute. By default we collect kernel runtimes in nanoseconds. A list of supported metrics can be found with `ncu --list-metrics`.
-   **ignore\_kernel\_list** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – List of kernel names to ignore. If you call a library within a `annotation` context, you might not have precise control over which and how many kernels are being launched. If some of these kernels should be ignored in the Nsight Python profile, their their names can be blacklisted. Default: `None`
-   **combine\_kernel\_metrics** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\], [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\]) – By default, Nsight Python expects one kernel launch per annotation. In case an annotated region launches multiple kernels, instead of failing the profiling run, you can specify how to summarize the collected metrics into a single number. For example, if we profile runtime and want to sum the times of all kernels we can specify `combine_kernel_metrics = lambda x, y: x + y`. The function should take two arguments and return a single value. Default: `None`.
-   **clock\_control** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'base'`, `'none'`\]) – Select clock\_control option control in NVIDIA Nsight Compute. If `None`, we launch `ncu --clock-control none ...`. For more details, see the NVIDIA Nsight Compute Profiling Guide: [https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#clock-control](https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#clock-control) Default: `None`
-   **cache\_control** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'all'`, `'none'`\]) – Select cache\_control option control in NVIDIA Nsight Compute. If `None`, we launch `ncu --cache-control none ...`. For more details, see the NVIDIA Nsight Compute Profiling Guide: [https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#cache-control](https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#cache-control) Default: `all`
-   **replay\_mode** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'kernel'`, `'range'`\]) – Select replay mode option control in NVIDIA Nsight Compute. If `None`, we launch `ncu --replay-mode kernel ...`. For more details, see the NVIDIA Nsight Compute Profiling Guide: [https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#replay](https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#replay) Default: `kernel`

collect(

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\]_,

_configs: [Iterable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]_,

_settings: [ProfileSettings](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "nsight.collection.core.ProfileSettings")_,

)[#](https://docs.nvidia.com/nsight-python/collection/ncu.html#nsight.collection.ncu.NCUCollector.collect "Link to this definition")

Collects profiling data using NVIDIA Nsight Compute.

Parameters:

-   **func** ([`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\]) – The function to profile.
-   **configs** ([`Iterable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Iterable "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]) – iterable of configurations to run the function with.
-   **settings** ([`ProfileSettings`](https://docs.nvidia.com/nsight-python/collection/core.html#nsight.collection.core.ProfileSettings "nsight.collection.core.ProfileSettings")) – Profiling settings.

Return type:

`DataFrame` | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")

Returns:

Collected profiling data.

nsight.collection.ncu.get\_signature(

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]_,

_configs: [List](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]_,

)[#](https://docs.nvidia.com/nsight-python/collection/ncu.html#nsight.collection.ncu.get_signature "Link to this definition")

Return type:

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")

Parameters:

-   **func** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[__...__\]__,_ [_Any_](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")_\]_)
-   **configs** ([_List_](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")_\[_[_Sequence_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")_\[_[_Any_](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")_\]__\]_)

nsight.collection.ncu.launch\_ncu(

_report\_path: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")_,

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\]_,

_configs: [List](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]_,

_metrics: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]_,

_cache\_control: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['none', 'all'\]_,

_clock\_control: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['none', 'base'\]_,

_replay\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['kernel', 'range'\]_,

_verbose: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

)[#](https://docs.nvidia.com/nsight-python/collection/ncu.html#nsight.collection.ncu.launch_ncu "Link to this definition")

Launch NVIDIA Nsight Compute to profile the current script with specified options.

Parameters:

-   **report\_path** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Path to write report file to.
-   **metrics** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – Specific metrics to collect.
-   **cache\_control** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'none'`, `'all'`\]) – Select cache control option
-   **clock\_control** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'none'`, `'base'`\]) – Select clock control option
-   **replay\_mode** ([`Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\[`'kernel'`, `'range'`\]) – Select replay mode option
-   **verbose** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – If False, log is written to a file (ncu\_log.txt)
-   **func** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[__...__\]__,_ _None__\]_)
-   **configs** ([_List_](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")_\[_[_Sequence_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")_\[_[_Any_](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")_\]__\]_)

Raises:

-   **NCUNotAvailableError** – If NCU is not available on the system.
-   **ProfilerException** – If profiling fails due to an error from NVIDIA Nsight Compute.
-   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.14)") – If invalid values are provided for cache\_control, clock\_control, or replay\_mode.

Return type:

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")

Returns:

path to the NVIDIA Nsight Compute log file Produces NVIDIA Nsight Compute report file with profiling data.