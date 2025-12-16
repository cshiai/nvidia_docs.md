# cuda.tile.reshape



### `cuda.tile.reshape(x, /, shape)`

Reshapes a tile to the specified shape.
One of the shape elements may be specified as -1 to indicate that the
corresponding dimension is to be inferred automatically.
For example, reshaping a (16, 2) tile to (8, -1) will
produce a tile of shape (8, 4): as there are 32 elements in total,
the second dimension will be computed as 32 divided by 8.

Parameters:

x (Tile) – input tile.
shape (tuple[const int,...]) – target shape.

Return type:
Tile

Examples
>>> tx = ct.arange(8, dtype=ct.float32)
>>> tx.shape
(8,)
>>> ty = ct.reshape(tx, (2, 4))
>>> ty.shape
(2, 4)
>>> tz = ct.reshape(tx, (2, -1))
>>> tz.shape
(2, 4)