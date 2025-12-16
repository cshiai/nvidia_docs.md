# cuda.tile.exp2



### `cuda.tile.exp2(x, /, *, flush_to_zero=False)`

Perform exp2 on a tile.

Parameters:

x (Tile)
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

Return type:
Tile

Examples
>>> tx = ct.full((32, 32), 3.0, dtype=ct.float32)
>>> tx = ct.exp2(tx)