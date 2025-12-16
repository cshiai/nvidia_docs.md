# cuda.tile.zeros



### `cuda.tile.zeros(shape, dtype)`

Creates a tile filled with zeros.

Parameters:

shape (tuple[const int,...]) – The shape of the tile.
dtype (DType) – The Data type of the tile.

Return type:
Tile

Examples
>>> tile = ct.zeros((4, 4), dtype=ct.float32)