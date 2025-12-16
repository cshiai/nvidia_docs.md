# cuda.tile.log2



### `cuda.tile.log2(x, /)`

Perform log2 on a tile.

Parameters:
x (Tile)

Return type:
Tile

Examples
>>> tx = ct.full((32, 32), 3.0, dtype=ct.float32)
>>> tx = ct.log2(tx)