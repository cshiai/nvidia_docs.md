# cuda.tile.add



### `cuda.tile.add(x, y, /, *, rounding_mode=None, flush_to_zero=False)`

Elementwise add on two tiles.
Can also use builtin operation x + y.

Parameters:

x (Tile) – LHS tile.
y (Tile) – RHS tile.
rounding_mode (RoundingMode) – The rounding mode for the operation, only supported for float types, default is RoundingMode.RN when applicable.
flush_to_zero (const bool) – If True, flushes subnormal inputs and results to sign-preserving zero, default is False.

The shape of x and y will be broadcasted and
dtype promoted to common dtype.

Return type:
Tile

Examples
>>> # tile and tile
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int32)
>>> tz = ct.add(tx, ty)

>>> # Can also use the builtin op
>>> tz = tx + ty

>>> # shape broadcast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2,), 3, dtype=ct.int32)
>>> tz = tx + ty

>>> # dtype cast
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> ty = ct.full((2, 4), 3, dtype=ct.int64)
>>> tz = tx + ty

>>> # tile and scalar
>>> tx = ct.full((2, 4), 7, dtype=ct.int32)
>>> y = 2
>>> tz = tx + y

>>> # scalar and scalar
>>> z = 7 + 2