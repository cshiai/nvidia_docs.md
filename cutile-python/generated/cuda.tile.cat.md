# cuda.tile.cat



### `cuda.tile.cat(tiles, /, axis)`

Concatenates two tiles along the axis.

Parameters:

tiles (tuple) – a pair of tiles to concatenate.
axis (const int) – axis to concatenate the tiles.

Return type:
Tile

Notes
Due to power-of-two assumption on all tile shapes,
the two input tiles must have the same shape.
Examples
>>> tx = ct.full((2, 4), 3., dtype=ct.float32)
>>> ty = ct.full((2, 4), 4., dtype=ct.float32)
>>> tz = ct.cat((tx, ty), 0)
>>> tz.shape
(4,4)
>>> tz = ct.cat((tx, ty), 1)
>>> tz.shape
(2,8)