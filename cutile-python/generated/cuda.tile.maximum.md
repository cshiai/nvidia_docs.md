# cuda.tile.maximum



### `cuda.tile.maximum(x, y, /, *, flush_to_zero=False)`

Elementwise maximum on two tiles.
Can also use builtin operation max(x, y).

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
>>> tz = ct.maximum(tx, ty)

>>> # Can also use the builtin op
>>> tz = max(tx, ty)

>>> # shape broadcast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2,), 3, dtype=ct.int32)
>>> tz = max(tx, ty)

>>> # dtype cast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int64)
>>> tz = max(tx, ty)

>>> # tile and scalar
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> y = 2
>>> tz = max(tx, y)

>>> # scalar and scalar
>>> z = max(7, 2)