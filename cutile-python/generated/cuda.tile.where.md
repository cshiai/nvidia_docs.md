# cuda.tile.where



### `cuda.tile.where(cond, x, y, /)`

Returns elements chosen from x or y depending on condition.

Parameters:

cond (Tile) – Boolean tile of shape S.
x (Tile) – Tile of shape S and dtype T, selected if cond is True.
y (Tile) – Tile of shape S and dtype T, selected if cond is False.

Return type:
Tile

Examples
>>> cond = ct.arange(4, dtype=ct.int32)
>>> cond = cond > 2
>>> x_true = ct.full((4,), 1.0, dtype=ct.float32)
>>> x_false = ct.full((4,), -1.0, dtype=ct.float32)
>>> y = ct.where(cond, x_true, x_false)
>>> y
[1., 1., -1., -1.]
>>> z = ct.where(cond, 1.0, -1.0)
>>> z
[1., 1., -1., -1.]