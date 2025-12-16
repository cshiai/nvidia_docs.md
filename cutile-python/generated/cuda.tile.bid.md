# cuda.tile.bid



### `cuda.tile.bid(axis)`

Gets the index of current block.

Parameters:
axis (const int) – The axis of the block index space. Possible values are 0, 1, 2.

Return type:
int32

Examples
>>> bid_x = ct.bid(0)
>>> bid_y = ct.bid(1)
>>> bid_z = ct.bid(2)