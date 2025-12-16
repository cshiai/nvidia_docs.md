# cuda.tile.min



### `cuda.tile.min(x, /, axis=None, *, keepdims=False, flush_to_zero=False)`

Performs min reduction on tile along the axis.

Parameters:

x (Tile) – input tile.
axis (None | const int | tuple[const int,...]) – the axis for reduction.
The default, axis=None, will reduce all of the elements.
keep_dims (const bool) – If true, preserves the number of dimension
from the input tile.
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

Return type:
Tile

Examples
>>> tx = ct.full((2, 4), 3, dtype=ct.float32)
>>> ty = ct.min(tx, 1)
>>> ty.shape
(2,)
>>> ty = ct.min(tx, 1, keepdims=True)
>>> ty.shape
(2, 1)