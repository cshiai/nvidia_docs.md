# cuda.tile.sqrt



### `cuda.tile.sqrt(x, /, *, rounding_mode=None, flush_to_zero=False)`

Perform sqrt on a tile.

Parameters:

x (Tile)
rounding_mode (RoundingMode) – The rounding mode for the operation, only supported for float types, default is RoundingMode.RN when applicable.
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

Return type:
Tile

Examples
>>> tx = ct.full((32, 32), 3.0, dtype=ct.float32)
>>> tx = ct.sqrt(tx)