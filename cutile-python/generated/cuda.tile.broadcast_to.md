# cuda.tile.broadcast_to



### `cuda.tile.broadcast_to(x, /, shape)`

Broadcasts a tile to the specified shape
following Numpy broadcasting rule.

Parameters:

x (Tile) – input tile.
shape (tuple[const int,...]) – target shape.

Return type:
Tile

Examples
>>> tx = ct.arange(4, dtype=ct.float32)
>>> tx.shape
(4,)
>>> ty = ct.broadcast_to(tx, (2, 4))
>>> ty.shape
(2, 4)