# cuda.tile.bitwise_or



### `cuda.tile.bitwise_or(x, y, /)`

Elementwise bitwise_or on two tiles.
Can also use builtin operation x | y.

Parameters:

x (Tile) – LHS tile.
y (Tile) – RHS tile.

The shape of x and y will be broadcasted and
dtype promoted to common dtype.

Return type:
Tile

Examples
>>> # tile and tile
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int32)
>>> tz = ct.bitwise_or(tx, ty)

>>> # Can also use the builtin op
>>> tz = tx | ty

>>> # shape broadcast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2,), 3, dtype=ct.int32)
>>> tz = tx | ty

>>> # dtype cast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int64)
>>> tz = tx | ty

>>> # tile and scalar
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> y = 2
>>> tz = tx | y

>>> # scalar and scalar
>>> z = 7 | 2