# cuda.tile.permute



### `cuda.tile.permute(x, /, axes)`

Permutes the axes of the input tile.

Parameters:

x (Tile) – input tile.
axes (tuple[const int,...]) – the desired axes order.

Return type:
Tile

Examples
>>> tx = ct.full((2, 4, 8), 0., dtype=ct.float32)
>>> ty = ct.permute(tx, (0, 2, 1))
>>> ty.shape
(2, 8, 4)