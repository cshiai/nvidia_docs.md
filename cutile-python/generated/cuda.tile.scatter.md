# cuda.tile.scatter



### `cuda.tile.scatter(array, indices, value, /, *, check_bounds=True, latency=None)`

Stores a tile value into the array elements specified by indices.
indices must be a tuple whose length equals the array rank.
All elements of this tuple must be integer tiles or scalars of the same shape,
or different shapes that are broadcastable to a common shape.
value must be a scalar or a tile whose shape is broadcastable to the
common shape of indices.
For example, consider a 2-dimensional array. In this case, indices must be a tuple
of length 2. Suppose that ind0 and ind1 are integer tiles
of shapes (M, N, 1) and (M, 1, K), and value is a tile of shape of (N, K):
>>> # ind0: (M, N, 1),  ind1: (M, 1, K),  value: (N, K)
>>> ct.scatter(array, (ind0, ind1), value)

The above call to scatter will store elements according to
array[ind0[i, j, 0], ind1[i, 0, k]] = value[j, k]

If the array is 1-dimensional, indices can be passed as a tile rather than a tuple.
This is a convenience notation that is strictly equivalent to passing a tuple of length 1:
>>> ct.scatter(array, ind0, value)   # equivalent to ct.scatter(array, (ind0,), value)

scatter() checks that indices are within the bounds of the array. For indices
that are out of bounds, nothing is stored. To disable bounds checking,
set check_bounds to False. In this mode, the caller is responsible for ensuring that
all indices are within the bounds of the array, and any out-of-bounds access
will result in undefined behavior.