# cuda.tile.load



### `cuda.tile.load(

array,
/,
index,
shape,
*,
order='C',
padding_mode=PaddingMode.UNDETERMINED,
latency=None,
allow_tma=None,

)`

Loads a tile from the array which is partitioned into a tile space.
The tile space is the result of partitioning the array into a grid of equally
sized tiles specified by shape.
For example, partitoning a 2D array of shape (M, N) using tile shape
(tm, tn) results in a 2D tile space of size (cdiv(M, tm), cdiv(N, tn)).
An index into this tile space using index (i, j) produces a tile of size (tm, tn):
>>> t = ct.load(array, (i, j), (tm, tn))  # `t` has shape (tm, tn)

The result tile t will be computed according to
t[x, y] = array[i * tm + x, j * tn + y]  (for all 0<=x<tm, 0<=y<tn)

For access that is out of bound, the value will be determined by padding_mode.
order is used to map the tile axis to the array axis. The transposed example of the above call
to load would be:
>>> ct.load(array, (j, i), shape=(tn, tm), order=(1, 0))

The result tile t will be computed according to
t[y, x] = array[i * tm + x, j * tn + y]

Parameters:

array (Array) – The array to load from.
index (tuple[int,...]) – An index in the tile space of shape from array.
shape (tuple[const int,...]) – A tuple of const integers definining the shape of the tile.
order ("C" or "F", or tuple[const int,...]) – Permutation applied to array axes before the
logical tile space is constructed. Can be specified either as a tuple of constants,
or as one of the two special string literal values:

”C” is an alias for (0, 1, 2, ...), i.e. no permutation applied;
”F” is an alias for (..., 2, 1, 0), i.e. axis order is reversed.

padding_mode (PaddingMode) – The value used to pad the tile when it extends beyond the array
boundaries. By default, the padding value is undetermined.
latency (const int) – A hint indicating how heavy DRAM traffic will be. It shall be an
integer between 1 (low) and 10 (high). By default, the compiler will infer the latency.
allow_tma (const bool) – If False, the load will not use TMA. By default, TMA is allowed.

Return type:
Tile

Examples
>>> # Regular load.
>>> tile = ct.load(array2d, (0, 0), shape=(2, 4))
>>> # Load with a transpose.
>>> tile = ct.load(array2d, (0, 0), shape=(4, 2), order='F')
>>> # Load transposing the last two axes.
>>> tile = ct.load(array3d, (0, 0, 0), shape=(8, 4, 2), order=(0, 2, 1))
>>> # Load a single element as 0d tile
>>> tile = ct.load(array3d, (0, 0, 0), shape=())

See also

store()
gather()
Tile space