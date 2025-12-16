# cuda.tile.arange



### `cuda.tile.arange(size, /, *, dtype)`

Creates a tile with value starting from 0 to size - 1.

Parameters:

size (const int) – Size of the tile.
dtype (DType) – Datatype of the tile.

Return type:
Tile

Examples
>>> tile = ct.arange(16, dtype=ct.int32)