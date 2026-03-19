# Visualization[#](https://docs.nvidia.com/nsight-python/visualization.html#module-nsight.visualization "Link to this heading")

Visualization utilities for Nsight Python profiling and tensor difference analysis.

This module provides:

-   Plotting functions for profiling results with configurable layout and annotation.

nsight.visualization.visualize(

_agg\_df: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | DataFrame_,

_metric: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_row\_panels: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_col\_panels: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_x\_keys: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_print\_data: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_,

_title: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= ''_,

_filename: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= 'plot.png'_,

_ylabel: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= ''_,

_annotate\_points: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= True_,

_show\_avg: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= True_,

_plot\_type: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") \= 'line'_,

_plot\_width: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") \= 6_,

_plot\_height: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") \= 4_,

_show\_geomean: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= True_,

_show\_grid: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= True_,

_variant\_fields: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_variant\_annotations: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_plot\_callback: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[Figure](https://matplotlib.org/stable/api/_as_gen/matplotlib.figure.Figure.html#matplotlib.figure.Figure "(in Matplotlib v3.10.8)")\], [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

)[#](https://docs.nvidia.com/nsight-python/visualization.html#nsight.visualization.visualize "Link to this definition")

Plots profiling results using line or bar plots in a subplot grid.

Parameters:

-   **agg\_df** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | `DataFrame`) – Aggregated profiling data or path to CSV file.
-   **metric** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")) – The specific metric to plot (e.g., `gpu__time_duration.sum`). If None (default), the function will plot the single metric found in the `ProfileResults` object containing profiling data, if only one exists, otherwise it will raise an error if multiple metrics are present. Default: `None`
-   **row\_panels** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")) – List of fields for whose unique values to create a new subplot along the vertical axis.
-   **col\_panels** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")) – List of fields for whose unique values to create a new subplot along the horizontal axis.
-   **x\_keys** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – List of fields to use for the x-axis. By default, we use all parameters of the decorated function except those specified in row\_panels and col\_panels.
-   **print\_data** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Whether to print aggregated profiling data to stdout.
-   **title** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Main plot title.
-   **filename** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Output filename for the saved plot.
-   **ylabel** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Label for the y-axis (typically the metric name).
-   **annotate\_points** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Whether to annotate data points with values.
-   **show\_avg** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Whether to add an “Avg” column with average metric values.
-   **plot\_type** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Type of plot: “line” or “bar”.
-   **show\_geomean** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Whether to show geometric mean values.
-   **show\_grid** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Whether to display grid lines on the plot.
-   **variant\_fields** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]) – List of config fields to use as variant fields (lines).
-   **variant\_annotations** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]\]) – List of annotated range names for which to apply variant splitting. The provided strings must each match one of the names defined using nsight.annotate.
-   **plot\_width** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)"))
-   **plot\_height** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)"))
-   **plot\_callback** ([_Callable_](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")_\[__\[_[_Figure_](https://matplotlib.org/stable/api/_as_gen/matplotlib.figure.Figure.html#matplotlib.figure.Figure "(in Matplotlib v3.10.8)")_\]__,_ _None__\]_ _|_ _None_)

Return type:

`DataFrame`

# Thermovision[#](https://docs.nvidia.com/nsight-python/thermovision.html#module-nsight.thermovision "Link to this heading")

_class_ nsight.thermovision.ThermalController(

_thermal\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['auto', 'manual', 'off'\] \= 'auto'_,

_thermal\_wait: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_cont: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_timeout: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_verbose: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_,

)[#](https://docs.nvidia.com/nsight-python/thermovision.html#nsight.thermovision.ThermalController "Link to this definition")

Bases: [`object`](https://docs.python.org/3/library/functions.html#object "(in Python v3.14)")

GPU thermal monitoring and throttling prevention.

Manages GPU temperature and prevents thermal throttling by pausing profiling when the GPU gets too hot and resuming after cooling.

Parameters:

-   **thermal\_mode** ([_Literal_](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")_\[__'auto'__,_ _'manual'__,_ _'off'__\]_)
-   **thermal\_wait** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_cont** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_timeout** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **verbose** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))

init()[#](https://docs.nvidia.com/nsight-python/thermovision.html#nsight.thermovision.ThermalController.init "Link to this definition")

Initialize NVML and get GPU handle.

Return type:

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")

Returns:

True if temperature retrieval is supported, False otherwise.

throttle\_guard()[#](https://docs.nvidia.com/nsight-python/thermovision.html#nsight.thermovision.ThermalController.throttle_guard "Link to this definition")

Check thermal state and pause if GPU is too hot.

Thermal headroom = temperature margin before GPU starts throttling.

Operates in two modes: - Auto mode: Automatically adjusts thermal\_cont based on workload - Manual mode: Uses user-provided thresholds without adaptation

Adaptive Algorithm (in auto mode): 1. When thermal headroom reaches thermal\_cont after cooling, start counting iterations :rtype: [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")

2.  Run kernel as headroom drops from thermal\_cont toward thermal\_wait
3.  When headroom drops below thermal\_wait, analyze iteration count: - Few iterations (<TARGET\_MIN\_ITERATIONS): GPU heats quickly → increase thermal\_cont (cool more) - Many iterations (>TARGET\_MAX\_ITERATIONS): GPU heats slowly → decrease thermal\_cont (cool less)
4.  Wait until GPU cools back to thermal\_cont, then repeat

Return type:

None

# Thermovision[#](https://docs.nvidia.com/nsight-python/thermovision.html#module-nsight.thermovision "Link to this heading")

_class_ nsight.thermovision.ThermalController(

_thermal\_mode: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")\['auto', 'manual', 'off'\] \= 'auto'_,

_thermal\_wait: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_cont: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_thermal\_timeout: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

_verbose: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)") \= False_,

)[#](https://docs.nvidia.com/nsight-python/thermovision.html#nsight.thermovision.ThermalController "Link to this definition")

Bases: [`object`](https://docs.python.org/3/library/functions.html#object "(in Python v3.14)")

GPU thermal monitoring and throttling prevention.

Manages GPU temperature and prevents thermal throttling by pausing profiling when the GPU gets too hot and resuming after cooling.

Parameters:

-   **thermal\_mode** ([_Literal_](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.14)")_\[__'auto'__,_ _'manual'__,_ _'off'__\]_)
-   **thermal\_wait** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_cont** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **thermal\_timeout** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)") _|_ _None_)
-   **verbose** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))

init()[#](https://docs.nvidia.com/nsight-python/thermovision.html#nsight.thermovision.ThermalController.init "Link to this definition")

Initialize NVML and get GPU handle.

Return type:

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")

Returns:

True if temperature retrieval is supported, False otherwise.

throttle\_guard()[#](https://docs.nvidia.com/nsight-python/thermovision.html#nsight.thermovision.ThermalController.throttle_guard "Link to this definition")

Check thermal state and pause if GPU is too hot.

Thermal headroom = temperature margin before GPU starts throttling.

Operates in two modes: - Auto mode: Automatically adjusts thermal\_cont based on workload - Manual mode: Uses user-provided thresholds without adaptation

Adaptive Algorithm (in auto mode): 1. When thermal headroom reaches thermal\_cont after cooling, start counting iterations :rtype: [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")

2.  Run kernel as headroom drops from thermal\_cont toward thermal\_wait
3.  When headroom drops below thermal\_wait, analyze iteration count: - Few iterations (<TARGET\_MIN\_ITERATIONS): GPU heats quickly → increase thermal\_cont (cool more) - Many iterations (>TARGET\_MAX\_ITERATIONS): GPU heats slowly → decrease thermal\_cont (cool less)
4.  Wait until GPU cools back to thermal\_cont, then repeat

Return type:

None