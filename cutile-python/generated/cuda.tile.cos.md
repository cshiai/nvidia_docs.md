# cuda.tile.cos



### `cuda.tile.cos(x, /)`

Perform cos on a tile.

Parameters:
x (Tile)

Return type:
Tile

Examples
>>> tx = ct.full((32, 32), 3.0, dtype=ct.float32)
>>> tx = ct.cos(tx)