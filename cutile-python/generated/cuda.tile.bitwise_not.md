# cuda.tile.bitwise_not



### `cuda.tile.bitwise_not(x, /)`

Elementwise bitwise not on a tile.
Can also use builtin operator ~x.

Parameters:
x (Tile) – input tile.

Return type:
Tile

Examples
>>> tx = ct.full((4, 4), 0, dtype=ct.int32)
>>> ty = ct.bitwise_not(x)
>>> ty = ~tx