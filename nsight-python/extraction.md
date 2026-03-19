# Extraction[#](https://docs.nvidia.com/nsight-python/extraction.html#module-nsight.extraction "Link to this heading")

Extraction utilities for analyzing NVIDIA Nsight Compute profiling data.

This module provides functionality to load .ncu-rep reports, extract performance data, and transform it into structured pandas DataFrames for further analysis.

Functions:

extract\_ncu\_action\_data(action, metrics):

Extracts performance data for a specific kernel action from an NVIDIA Nsight Compute report.

extract\_df\_from\_report(report\_path, metrics, configs, iterations, func, derive\_metric, ignore\_kernel\_list, output\_progress, combine\_kernel\_metrics=None):

Processes the full NVIDIA Nsight Compute report and returns a pandas DataFrame containing performance metrics.

nsight.extraction.extract\_df\_from\_report(

_report\_path: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")_,

_metrics: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]_,

_configs: [List](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple "(in Python v3.14)")\[[Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)"), ...\]\]_,

_iterations: [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")_,

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]_,

_derive\_metric: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_ignore\_kernel\_list: [List](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_output\_progress: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

_combine\_kernel\_metrics: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)"), [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\], [float](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\] | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)") \= None_,

)[#](https://docs.nvidia.com/nsight-python/extraction.html#nsight.extraction.extract_df_from_report "Link to this definition")

Extracts and aggregates profiling results from an NVIDIA Nsight Compute report.

Parameters:

-   **report\_path** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")) – Path to the report file.
-   **metrics** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – The NVIDIA Nsight Compute metrics to extract.
-   **configs** ([`List`](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple "(in Python v3.14)")\[[`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)"), [`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)")\]\]) – Configuration settings used during profiling runs.
-   **iterations** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.14)")) – Number of times each configuration was run.
-   **func** ([`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]) – Function representing the kernel launch with parameter signature.
-   **derive\_metric** ([`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\] | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")) – Function to transform the raw metric values with config values.
-   **ignore\_kernel\_list** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`List`](https://docs.python.org/3/library/typing.html#typing.List "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]\]) – Kernel names to ignore in the analysis.
-   **combine\_kernel\_metrics** ([`Optional`](https://docs.python.org/3/library/typing.html#typing.Optional "(in Python v3.14)")\[[`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\], [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.14)")\]\]) – Function to merge multiple kernel metrics.
-   **verbose** – Toggles the printing of extraction progress.
-   **output\_progress** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)"))

Return type:

`DataFrame`

Returns:

A DataFrame containing the extracted and transformed performance data.

Raises:

-   [**RuntimeError**](https://docs.python.org/3/library/exceptions.html#RuntimeError "(in Python v3.14)") – If multiple kernels are detected per config without a combining function.
-   **exceptions.ProfilerException** – If profiling results are missing or incomplete.

nsight.extraction.extract\_ncu\_action\_data(

_action: [Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")_,

_metrics: [Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]_,

)[#](https://docs.nvidia.com/nsight-python/extraction.html#nsight.extraction.extract_ncu_action_data "Link to this definition")

Extracts performance data from an NVIDIA Nsight Compute kernel action.

Parameters:

-   **action** ([`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")) – The NVIDIA Nsight Compute action object.
-   **metrics** ([`Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "(in Python v3.14)")\[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]) – The metric names to extract from the action.

Return type:

[`NCUActionData`](https://docs.nvidia.com/nsight-python/utils.html#nsight.utils.NCUActionData "nsight.utils.NCUActionData")

Returns:

A data container with extracted metrics, clock rates, and GPU name.

# Transformation[#](https://docs.nvidia.com/nsight-python/transformation.html#module-nsight.transformation "Link to this heading")

Data transformation utilities for Nsight Python profiling output.

This module contains functions that process raw profiling results, aggregate metrics, normalize them, and prepare the data for visualization or further statistical analysis.

nsight.transformation.aggregate\_data(

_df: DataFrame_,

_func: [Callable](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[\[...\], [Any](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]_,

_normalize\_against: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [None](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")_,

_output\_progress: [bool](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")_,

)[#](https://docs.nvidia.com/nsight-python/transformation.html#nsight.transformation.aggregate_data "Link to this definition")

Groups and aggregates profiling data by configuration and annotation.

Parameters:

-   **df** (`DataFrame`) – The raw profiling results.
-   **func** ([`Callable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Callable "(in Python v3.14)")\[[`...`](https://docs.python.org/3/library/constants.html#Ellipsis "(in Python v3.14)"), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any "(in Python v3.14)")\]) – Function representing kernel configuration parameters.
-   **normalize\_against** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)") | [`None`](https://docs.python.org/3/library/constants.html#None "(in Python v3.14)")) – Name of the annotation to normalize against.
-   **output\_progress** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.14)")) – Toggles the display of data processing logs

Return type:

`DataFrame`

Returns:

Aggregated DataFrame and the (possibly normalized) metric name.