# cuda.tile.argmin



### `cuda.tile.argmin(x, /, axis=None, *, keepdims=False)`

Performs argmin reduction on tile along the axis.

Parameters:

x (Tile) – input tile.
axis (None | const int | tuple[const int,...]) – the axis for reduction.
The default, axis=None, will reduce all of the elements.
keep_dims (const bool) – If true, preserves the number of dimension
from the input tile.

Return type:
Tile

Examples
>>> tx = ct.full((2, 4), 3, dtype=ct.float32)
>>> ty = ct.argmin(tx, 1)
>>> ty.shape
(2,)
>>> ty = ct.argmin(tx, 1, keepdims=True)
>>> ty.shape
(2, 1)