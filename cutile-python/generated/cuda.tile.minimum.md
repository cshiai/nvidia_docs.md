# cuda.tile.minimum



### `cuda.tile.minimum(x, y, /, *, flush_to_zero=False)`

Elementwise minimum on two tiles.
Can also use builtin operation min(x, y).

Parameters:

x (Tile) – LHS tile.
y (Tile) – RHS tile.
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

The shape of x and y will be broadcasted and
dtype promoted to common dtype.

Return type:
Tile

Examples
>>> # tile and tile
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int32)
>>> tz = ct.minimum(tx, ty)

>>> # Can also use the builtin op
>>> tz = min(tx, ty)

>>> # shape broadcast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2,), 3, dtype=ct.int32)
>>> tz = min(tx, ty)

>>> # dtype cast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int64)
>>> tz = min(tx, ty)

>>> # tile and scalar
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> y = 2
>>> tz = min(tx, y)

>>> # scalar and scalar
>>> z = min(7, 2)