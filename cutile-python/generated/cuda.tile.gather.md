# cuda.tile.gather



### `cuda.tile.gather(

array,
indices,
/,
*,
padding_value=0,
check_bounds=True,
latency=None,

)`

Loads a tile from the array elements specified by indices.
indices must be a tuple whose length equals the array rank.
All elements of this tuple must be integer tiles or scalars of the same shape,
or different shapes that are broadcastable to a common shape.
The result shape will be the same as the broadcasted shape of indices.
For example, consider a 2-dimensional array. In this case, indices must be a tuple
of length 2. Suppose that ind0 and ind1 are integer tiles
of shapes (M, N, 1) and (M, 1, K).
Then the result tile will have the broadcasted shape (M, N, K):
>>> t = ct.gather(array, (ind0, ind1))   # `t` has shape (M, N, K)

The result tile t will be computed according to
t[i, j, k] = array[ind0[i, j, 0], ind1[i, 0, k]]   (for all 0<=i<M, 0<=j<N, 0<=k<K)

If the array is 1-dimensional, indices can be passed as a tile rather than a tuple.
This is a convenience notation that is strictly equivalent to passing a tuple of length 1:
>>> ct.gather(array, ind0)   # equivalent to ct.gather(array, (ind0,))

gather() checks that indices are within the bounds of the array. For indices
that are out of bounds, padding_value will be returned (zero by default).
It must be a scalar or a tile whose shape is broadcastable to the common shape of indices.
To disable bounds checking, set check_bounds to False.
In this mode, the caller is responsible for ensuring that all indices are within the bounds
of the array, and any out-of-bounds access will result in undefined behavior.
Negative indices are interpreted as out of bounds, i.e. they don’t follow the Python’s
negative index convention.