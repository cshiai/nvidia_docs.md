# cuda.tile.store



### `cuda.tile.store(

array,
/,
index,
tile,
*,
order='C',
latency=None,
allow_tma=None,

)`

Stores a tile value into the array at the index of its tile space.
The tile space is the result of partitioning the array into a grid of tiles
with equal size defined by the shape of the tile.
For example, given a tile t of shape (tm, tn) and array of shape (M, N):
>>> # tile `t` has shape (tm, tn)
>>> ct.store(array, (i, j), t)

The above call to store will store elements according to:
array[i * tm + x, i * tn + y] = t[x, y]  (for 0<=x<tm, 0<=y<tn)

Access which falls out of the boundary of the array will be ignored.

Parameters:

array (Array) – The array to store to.
index (tuple[int,...]) – An index in the tile space of array.
shape is inferred from the tile argument.
tile (Tile) – The tile to store. The rank of the tile must match rank of the array,
unless it is a scalar or 0d tile.
order ("C" or "F", or tuple[const int,...]) – Order of axis mapping. See load().
latency (int, optional) – A hint indicating how heavy DRAM traffic will be. It shall be an
integer between 1 (low) and 10 (high). By default, the compiler will infer the latency.
allow_tma (bool, optional) – If False, the load will not use TMA. By default, TMA is allowed.

Examples
>>> tile = ct.load(array_in, bid_x, shape=4)
>>> tile = tile * 2
>>> ct.store(array_out, (bid_x,), tile=tile)
# store a scalar
>>> ct.store(array_out, (0,), tile=0)

See also

load()
scatter()
Tile space