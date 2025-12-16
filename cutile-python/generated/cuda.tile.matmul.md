# cuda.tile.matmul



### `cuda.tile.matmul(x, y, /)`

Performs matrix multiply on the given tiles.

Parameters:

x (Tile) – LHS of the matmul, 1D, 2D, or 3D.
y (Tile) – RHS of the matmul, 1D, 2D, or 3D.

Supported input datatypes: [f16, bf16, f32, f64, tf32, f8e4m3fn, f8e5m2, i8, u8]
If x and y have different dtype, they will first be promoted to common
dtype. The result dtype is the same as the promoted input types.
Shape of x and y will be broadcasted to up until the last two axes.

Return type:
Tile

Example
>>> tx = ct.full((2, 4), 3, dtype=ct.float32)
>>> ty = ct.full((4, 8), 4, dtype=ct.float32)
# default
>>> tz = ct.matmul(tx, ty)
# use builtin `@`
>>> tz = tx @ ty