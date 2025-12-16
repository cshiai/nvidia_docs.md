# cuda.tile.argmax



### `cuda.tile.argmax(x, /, axis=None, *, keepdims=False)`

Performs argmax reduction on tile along the axis.

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
>>> ty = ct.argmax(tx, 1)
>>> ty.shape
(2,)
>>> ty = ct.argmax(tx, 1, keepdims=True)
>>> ty.shape
(2, 1)