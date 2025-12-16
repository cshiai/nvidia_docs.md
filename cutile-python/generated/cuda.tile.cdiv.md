# cuda.tile.cdiv



### `cuda.tile.cdiv(x, y, /)`

Computes ceil(x / y). Can be used on the host.

Parameters:

x (Tile) – int tile.
y (Tile) – int tile.

Return type:
Tile

Examples
>>> tile = ct.full((2, 2), 7, dtype=ct.int32)
>>> ct.cdiv(tile, 4)
Tile((2,2), dtype=int32)

>>> ct.cdiv(7, 4)
2