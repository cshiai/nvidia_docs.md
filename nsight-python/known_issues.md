# Updates in Nsight Python 0.9.6[#](https://docs.nvidia.com/nsight-python/release_notes/topics/updates-in-nsight-python-0.9.6.html#updates-in-nsight-python-0-9-6 "Link to this heading")

## Enhancements[#](https://docs.nvidia.com/nsight-python/release_notes/topics/updates-in-nsight-python-0.9.6.html#enhancements "Link to this heading")

-   [Github Issue #11](https://github.com/NVIDIA/nsight-python/issues/11): Added support for **multiple derived metrics** in [`nsight.analyze.kernel()`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel") using `derive_metric` parameter. The `derive_metric` function can now return either a single value or a dictionary of multiple metrics.
-   Added **metric parameter** to [`nsight.analyze.plot()`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.plot "nsight.analyze.plot") decorator to specify which metric to visualize when multiple metrics are collected.
-   **Normalization improvements** in [`nsight.analyze.kernel()`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel"):
    
    -   Changed `normalize_against` to use standard normalization (current/baseline) instead of appending normalization info to metric names.
    -   Added **Normalized** column to the output dataframe to indicate which annotation is used for normalization.
-   **Adaptive Thermovision** in [`nsight.analyze.kernel()`](https://docs.nvidia.com/nsight-python/analyze.html#nsight.analyze.kernel "nsight.analyze.kernel"):
    
    -   Replaced `thermal_control` boolean parameter with `thermal_mode` parameter that accepts `"auto"`, `"manual"`, or `"off"` values for more flexible thermal throttling control.
    -   Added `thermal_wait` parameter to specify the thermal headroom threshold (T.Limit in °C) that triggers cooling pause.
    -   Added `thermal_cont` parameter to specify the thermal headroom threshold (T.Limit in °C) to resume profiling after cooling.
    -   Added `thermal_timeout` parameter to specify the maximum wait time in seconds for GPU to cool down.

## Fixes[#](https://docs.nvidia.com/nsight-python/release_notes/topics/updates-in-nsight-python-0.9.6.html#fixes "Link to this heading")

-   [Github Issue #13](https://github.com/NVIDIA/nsight-python/issues/13): Fixed incorrect profiling results when making multiple function calls of the same decorated function.
-   [Github Issue #17](https://github.com/NVIDIA/nsight-python/issues/17): Fixed `ZeroDivisionError` when handling zero-valued metrics (e.g., `sm__idc_divergent_instructions.avg`). Added test coverage for zero-valued metrics to ensure proper handling.

# Known Issues[#](https://docs.nvidia.com/nsight-python/release_notes/known_issues.html#known-issues "Link to this heading")

-   Nsight Python launches the application python script again with NVIDIA Nsight Compute CLI (ncu) for each `@nsight.analyze.kernel` decorator.
    
    -   Due to this issue, using `nsight-python` in interactive notebook environments (e.g., Jupyter Notebook or Google Colab) is not supported. Refer to [GitHub issue #3](https://github.com/NVIDIA/nsight-python/issues/3) for more information..
    
    In the meantime, you can use the following workaround by placing your benchmark into a standalone Python script and executing it outside the interactive cell environment:
    
    %%writefile quickstart.py
    import torch
    import nsight
    
    @nsight.analyze.kernel
    def benchmark\_matmul(n):
        """
        The simplest possible benchmark.
        We create two matrices and multiply them.
        """
        \# Create two NxN matrices on GPU
        a \= torch.randn(n, n, device\="cuda")
        b \= torch.randn(n, n, device\="cuda")
    
        \# Mark the kernel we want to profile
        with nsight.annotate("matmul"):
            c \= a @ b
    
        return c
    
    result \= benchmark\_matmul(1024)
    
    Then run the script with:
    
    %run quickstart.py
    
-   Kernels launched from a subprocess which is created within the annotated region will not be profiled.
-   For the `nsight.analyze.kernel`’s `replay_mode="range"` option, only a subset of CUDA APIs are supported within the annotated range. If an unsupported API call is detected, an error will be reported. For details on supported APIs, refer to the [NVIDIA Nsight Compute Profiling Guide](https://docs.nvidia.com/nsight-compute/ProfilingGuide/index.html#supported-apis). In such cases, you can either switch to `replay_mode="kernel"` or modify the code to exclude the unsupported API from the annotated range.
-   Nested annotations (using `nsight.annotate` within another `nsight.annotate` context) are not supported. nsight-python errors out when nested annotations are used.