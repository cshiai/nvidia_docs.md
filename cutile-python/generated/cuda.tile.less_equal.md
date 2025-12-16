# cuda.tile.less_equal



### `cuda.tile.less_equal(x, y, /)`

Compare two tiles elementwise with <=.
Can also use builtin operation x <= y.

Parameters:

x (Tile) – LHS tile.
y (Tile) – RHS tile.

The shape of x and y will be broadcasted and
dtype promoted to common dtype.

Return type:
Tile

Examples
>>> # tile and tile
>>> tx = ct.arange(8, dtype=ct.int32) - 4
>>> ty = ct.arange(8, dtype=ct.int32)
>>> tz = ct.less_equal(tx, ty)

>>> # Can also use the builtin op
>>> tz = tx <= ty

>>> # shape broadcast
>>> tx = ct.arange(8, dtype=ct.int32)
>>> ty = ct.full((1,), 0, dtype=ct.int32)
>>> tz = tx <= ty

>>> # dtype broadcast
>>> tx = ct.arange(8, dtype=ct.int32) - 4
>>> ty = ct.arange(8, dtype=ct.int64)
>>> tz = tx <= ty

>>> # tile and scalar
>>> tx = ct.arange(8, dtype=ct.int32) - 4
>>> tz = tx <= 0

>>> # scalar and scala
>>> z = 5 <= 3