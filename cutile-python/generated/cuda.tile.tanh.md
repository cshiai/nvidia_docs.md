# cuda.tile.tanh



### `cuda.tile.tanh(x, /)`

Perform tanh on a tile.

Parameters:
x (Tile)

Return type:
Tile

Examples
>>> tx = ct.full((32, 32), 3.0, dtype=ct.float32)
>>> tx = ct.tanh(tx)