# cuda.tile.atomic_cas



### `cuda.tile.atomic_cas(

array,
indices,
expected,
desired,
/,
*,
check_bounds=True,
memory_order=MemoryOrder.ACQ_REL,
memory_scope=MemoryScope.DEVICE,

)`

Bulk atomic compare-and-swap on array elements with given indices.
For each specified index, atomic_cas() compares the corresponding array element
to the expected value. If it matches, it is then overwritten with the desired value;
otherwise, no update is performed. In either case, the old value of the element is returned.
For each individual element, the described compare-and-swap operation is performed atomically,
but the operation as a whole is not atomic, and the order of individual updates is unspecified.
atomic_cas() follows the same convention as gather() and scatter():
indices must be a tuple whose length equals the array rank.
All elements of this tuple must be integer tiles or scalars of the same shape,
or different shapes that are broadcastable to a common shape.
If the array is 1-dimensional, indices can be passed as a single tile
rather than a tuple of length 1.
expected and desired must be scalars or tiles whose shapes are broadcastable
to the common shape of indices.
By default, atomic_cas() checks that indices are within the bounds of the array.
For indices that are out of bounds, no operation is performed, and a corresponding expected
value is returned. To disable bounds checking, set check_bounds to False.
In this mode, the caller is responsible for ensuring that all indices are within
the bounds of the array, and any out-of-bounds access will result in undefined behavior.
As an example, consider a 2-dimensional array. In this case, indices must be a tuple
of length 2. Suppose that ind0 and ind1 are integer tiles
of shapes (M, N, 1) and (M, 1, K), and both expected and desrired
are tiles of shape of (N, K):
>>> # ind0: (M, N, 1),  ind1: (M, 1, K),  expected: (N, K),  desired: (N, K)
>>> ct.atomic_cas(array, (ind0, ind1), expected, desired)

The above call to atomic_cas will behave similarly to the following pseudocode:
in parallel, for all (i, j, k) such that 0<=i<M, 0<=j<N, i<=k<K:
    if not check_bounds or (0 <= ind0[i, j, 0] < array.shape[0]
                            and 0 <= ind1[i, 0, k] < array.shape[1]):
        do atomically:
            actual = array[ind0[i, j, 0], ind1[i, 0, k]]
            if actual == expected[j, k]:
                array[ind0[i, j, 0], ind1[i, 0, k]] = desired[j, k]
        result[i, j, k] = actual
    else:
        result[i, j, k] = expected[j, k]

Examples
>>> indices = ct.arange(32, dtype=ct.int32)
>>> expected = ct.full((32,), 1, dtype=ct.int32)
>>> desired = ct.arange(32, dtype=ct.int32)
>>> old_value = ct.atomic_cas(array, indices, expected, desired)