# cuda.tile.transpose



### `cuda.tile.transpose(x, /, axis0=None, axis1=None)`

Transposes two axes of the input tile with at least 2 dimensions.
For a 2-dimensional tile, the two axes are transposed if axis0 and axis1 are not specified.
For tiles with more than 2 dimensions, axis0 and axis1 must be explicitly specified.

Parameters:

x (Tile) – input tile.
axis0 (const int) – the first axis to transpose.
axis1 (const int) – the second axis to transpose.

Return type:
Tile

Examples
>>> tx = ct.full((2, 4, 8), 0., dtype=ct.float32)
>>> ty = ct.transpose(tx, axis0=0, axis1=1)
>>> ty.shape
(4, 2, 8)
>>> tx = ct.full((2, 4), 0., dtype=ct.float32)
>>> ty = ct.transpose(tx)
>>> ty.shape
(4, 2)