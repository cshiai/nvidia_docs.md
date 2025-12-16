# cuda.tile.negative



### `cuda.tile.negative(x, /)`

Same as -x.

Parameters:
x (Tile) – input tile.

Return type:
Tile

Examples
>>> Negate a tile
>>> tx = ct.arange(8, dtype=ct.int32)
>>> ty = ct.negative(tx)
>>> ty = -tx

>>> Negate a scalar
>>> x = 3
>>> y = -x