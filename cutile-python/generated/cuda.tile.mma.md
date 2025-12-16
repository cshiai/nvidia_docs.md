# cuda.tile.mma



### `cuda.tile.mma(x, y, /, acc)`

Matrix multiply-accumulate.
Computes (x @ y) + acc as a single operation
(where @ denotes matrix multiplication).
Preserves the dtype of acc.

Parameters:

x (Tile) – LHS of the mma, 2D or 3D.
y (Tile) – RHS of the mma, 2D or 3D.
acc (Tile) – Accumulator of mma.

Supported datatypes:

Input
Acc/Ouput

f16
f16 or f32

bf16
f32

f32
f32

f64
f64

tf32
f32

f8e4m3fn
f16 or f32

f8e5m2
f16 or f32

[u|i]8
i32

If x and y have different dtype, they will NOT be promoted to common dtype.
Shape of x and y will be broadcasted to up until the last two axes.

Return type:
Tile

Example
>>> tx = ct.full((2, 4), 3, dtype=ct.float32)
>>> ty = ct.full((4, 8), 4, dtype=ct.float32)
>>> acc = ct.full((2, 8), 0, dtype=ct.float32)
# default
>>> tz = ct.mma(tx, ty, acc)