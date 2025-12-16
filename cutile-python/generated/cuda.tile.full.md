# cuda.tile.full



### `cuda.tile.full(shape, fill_value, dtype)`

Creates a tile filled with given value.

Parameters:

shape (tuple[const int,...]) – The shape of the tile.
fill_value (int | float | bool]) – Value for the tile.
dtype (DType) – The Data type of the tile.

Return type:
Tile

Examples
>>> tile = ct.full((4, 4), 3.14, dtype=ct.float32)