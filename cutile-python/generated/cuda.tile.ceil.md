# cuda.tile.ceil



### `cuda.tile.ceil(x, /)`

Perform ceil on a tile.

Parameters:
x (Tile)

Return type:
Tile

Examples
>>> tx = ct.full((32, 32), 3.0, dtype=ct.float32)
>>> tx = ct.ceil(tx)