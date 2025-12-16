# cuda.tile.ones



### `cuda.tile.ones(shape, dtype)`

Creates a tile filled with ones.

Parameters:

shape (tuple[const int,...]) – The shape of the tile.
dtype (DType) – The Data type of the tile.

Return type:
Tile

Examples
>>> tile = ct.ones((4, 4), dtype=ct.float32)