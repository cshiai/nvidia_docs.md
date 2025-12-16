# cuda.tile.expand_dims



### `cuda.tile.expand_dims(x, /, axis)`

Reshapes the tile by inserting a new axis of size 1 at given position.
This can also be done via the NumPy-style syntax: x[:, None] or x[np.newaxis, :]

Parameters:

x (Tile) – input tile.
axis (const int) – axis to expand the tile dimension.

Return type:
Tile

Examples
>>> tx = ct.arange(16, dtype=ct.float32)
>>> tx.shape
(16,)
>>> ty = ct.expand_dims(x, 1)
>>> ty.shape
(16,1)
>>> ty = x[None, ..., None, None]
>>> ty.shape
(1, 16, 1, 1)