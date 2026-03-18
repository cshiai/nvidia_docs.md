# Debugging[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#debugging "Link to this heading")

## Exception Types[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#exception-types "Link to this heading")

_class_ cuda.tile.TileSyntaxError[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileSyntaxError "Link to this definition")

Exception when a python syntax not supported by cuTile is encountered.

_class_ cuda.tile.TileTypeError[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileTypeError "Link to this definition")

Exception when an unexpected type or [data type](https://docs.nvidia.com/cuda/cutile-python/data.html#data-data-types) is encountered.

_class_ cuda.tile.TileValueError[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileValueError "Link to this definition")

Exception when an unexpected python value is encountered.

_class_ cuda.tile.TileUnsupportedFeatureError[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileUnsupportedFeatureError "Link to this definition")

Exception when a feature is not supported by the underlying compiler or the GPU architecture.

_class_ cuda.tile.TileCompilerExecutionError[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileCompilerExecutionError "Link to this definition")

Exception when `tileiras` compiler throws an error.

_class_ cuda.tile.TileCompilerTimeoutError[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileCompilerTimeoutError "Link to this definition")

Exception when `tileiras` compiler timeout limit is exceeded.

## Environment Variables[#](https://docs.nvidia.com/cuda/cutile-python/debugging.html#environment-variables "Link to this heading")

The following environment variables are useful when the above exceptions are encountered during kernel development.

Set `CUDA_TILE_ENABLE_CRASH_DUMP=1` to enable dumping an archive including the TileIR bytecode for submitting a bug report on [`TileCompilerExecutionError`](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileCompilerExecutionError "cuda.tile.TileCompilerExecutionError") or [`TileCompilerTimeoutError`](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileCompilerTimeoutError "cuda.tile.TileCompilerTimeoutError").

Set `CUDA_TILE_COMPILER_TIMEOUT_SEC` to limit the time the TileIR compiler tileiras can take.

Set `CUDA_TILE_LOGS=CUTILEIR` to print cuTile Python IR during compilation to stderr. This is useful when debugging [`TileTypeError`](https://docs.nvidia.com/cuda/cutile-python/debugging.html#cuda.tile.TileTypeError "cuda.tile.TileTypeError").

Set `CUDA_TILE_TEMP_DIR` to configure the directory for storing temporary files.

Set `CUDA_TILE_CACHE_DIR` to configure the directory for the bytecode-to-cubin disk cache. Compiled cubins are cached here to avoid recompilation of unchanged kernels. Set to `0`, `off`, `none`, or an empty string to disable caching. Defaults to `~/.cache/cutile-python`.

Set `CUDA_TILE_CACHE_SIZE` to configure the maximum disk cache size in bytes. Oldest entries are evicted when the cache exceeds this limit. Defaults to 2 GB (2147483648).

[

](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.static_iter.html "previous page")
