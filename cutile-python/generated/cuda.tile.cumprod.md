# cuda.tile.cumprod



### `cuda.tile.cumprod(

x,
/,
axis=0,
*,
reverse=False,
rounding_mode=None,
flush_to_zero=False,

)`

Performs cumprod on tile along the axis.

Parameters:

x (Tile) – input tile
axis (const int) – the axis for scan, default 0.
reverse (const bool) – if True, the scan is performed in the reverse direction.
rounding_mode (RoundingMode) – The rounding mode for the operation, only supported for float types, default is RoundingMode.RN when applicable.
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

Return type:
Tile

Examples
>>> tx = ct.full((2, 4), 3, dtype=ct.float32)
>>> ty = ct.cumprod(tx, 1)
>>> ty.shape
(2, 4)
>>> ty = ct.cumprod(tx, 1, reverse=True)
>>> ty.shape
(2, 4)