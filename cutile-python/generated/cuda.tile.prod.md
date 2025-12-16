# cuda.tile.prod



### `cuda.tile.prod(

x,
/,
axis=None,
*,
keepdims=False,
rounding_mode=None,
flush_to_zero=False,

)`

Performs prod reduction on tile along the axis.

Parameters:

x (Tile) – input tile.
axis (None | const int | tuple[const int,...]) – the axis for reduction.
The default, axis=None, will reduce all of the elements.
keep_dims (const bool) – If true, preserves the number of dimension
from the input tile.
rounding_mode (RoundingMode) – The rounding mode for the operation, only supported for float types, default is RoundingMode.RN when applicable.
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

Return type:
Tile

Examples
>>> tx = ct.full((2, 4), 3, dtype=ct.float32)
>>> ty = ct.prod(tx, 1)
>>> ty.shape
(2,)
>>> ty = ct.prod(tx, 1, keepdims=True)
>>> ty.shape
(2, 1)