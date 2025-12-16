# cuda.tile.num_tiles



### `cuda.tile.num_tiles(array, /, axis, shape, order='C')`

Gets the number of tiles in the tile space of the array along the axis.

Parameters:

array (Array) – An array object on a cuda device.
axis (const int) – The axis of the tile partition space to get the dim size.
shape (const int...) – A sequence of const integers definining the shape of the tile.
order ("C" or "F", or tuple[const int,...]) – Order of axis mapping. See load().

Returns:
int32

Examples
Suppose array size is (32, 16), tile shape (4, 8),
the partition space will be (cdiv(32, 4), cdiv(16, 8)) == (8, 2)
>>> ct.num_tiles(array, 0, shape=(4, 8))
8
>>> ct.num_tiles(array, 1, shape=(4, 8))
2