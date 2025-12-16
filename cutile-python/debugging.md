# Debugging


## Exception Types



### `class cuda.tile.TileSyntaxError`

Exception when a python syntax not supported by cuTile is encountered.



### `class cuda.tile.TileTypeError`

Exception when an unexpected type or data type is encountered.



### `class cuda.tile.TileValueError`

Exception when an unexpected python value is encountered.



### `class cuda.tile.TileCompilerExecutionError`

Exception when tileiras compiler throws an error.



### `class cuda.tile.TileCompilerTimeoutError`

Exception when tileiras compiler timeout limit is exceeded.


## Environment Variables


The following environment variables are useful when the above exceptions are encountered during kernel development.


Set `CUDA_TILE_ENABLE_CRASH_DUMP=1` to enable dumping an archive including the TileIR bytecode for submitting a bug report on [`TileCompilerExecutionError`](debugging.html#cuda.tile.TileCompilerExecutionError) or [`TileCompilerTimeoutError`](debugging.html#cuda.tile.TileCompilerTimeoutError).


Set `CUDA_TILE_COMPILER_TIMEOUT_SEC` to limit the time the TileIR compiler tileiras can take.


Set `CUDA_TILE_LOGS=CUTILEIR` to print cuTile Python IR during compilation to stderr. This is useful when debugging [`TileTypeError`](debugging.html#cuda.tile.TileTypeError).


Set `CUDA_TILE_TEMP_DIR` to configure the directory for storing temporary files.