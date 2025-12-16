# cuda.tile.astype



### `cuda.tile.astype(x, dtype, /)`

Converts a tile to the specified data type.

Parameters:

x (Tile) – input tile.
dtype (DType) – target data type.

Return type:
Tile

Examples
>>> tx = ct.arange(8, dtype=ct.float32)
>>> ty = ct.astype(tx, ct.float16)
>>> ty.dtype
float16