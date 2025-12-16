# cuda.tile.atomic_max



### `cuda.tile.atomic_max(

array,
indices,
update,
/,
*,
check_bounds=True,
memory_order=MemoryOrder.ACQ_REL,
memory_scope=MemoryScope.DEVICE,

)`

Bulk atomic maximum value assignment on array elements at given indices.
For each specified index, atomic_max() reads the corresponding array element,
computes the maximum between its value and the corresponding value of update,
and writes the modified value back to the same location.
The original value of the element before the update is returned.
For each individual element, the operation is performed atomically,
but the operation as a whole is not atomic, and the order of individual writes is unspecified.
atomic_max() follows the same convention as gather() and scatter():
indices must be a tuple whose length equals the array rank.
All elements of this tuple must be integer tiles or scalars of the same shape,
or different shapes that are broadcastable to a common shape.
If the array is 1-dimensional, indices can be passed as a single tile
rather than a tuple of length 1.
update must be a scalar or a tile whose shape is broadcastable to the
common shape of indices.
By default, atomic_max() checks that indices are within the bounds of the array.
For indices that are out of bounds, no operation is performed, and an implementation-defined
value is returned. To disable bounds checking, set check_bounds to False.
In this mode, the caller is responsible for ensuring that all indices are within
the bounds of the array, and any out-of-bounds access will result in undefined behavior.
Examples
>>> indices = ct.arange(32, dtype=ct.int32)
>>> update = ct.arange(32, dtype=ct.int32)
>>> old_value = ct.atomic_max(array, indices, update)