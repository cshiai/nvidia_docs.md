# cuda.tile.num_blocks



### `cuda.tile.num_blocks(axis)`

Gets the number of blocks along the axis.

Parameters:
axis (const int) – The axis of the block index space. Possible values are 0, 1, 2.

Return type:
int32

Examples
>>> num_blocks_x = ct.num_blocks(0)
>>> num_blocks_y = ct.num_blocks(1)
>>> num_blocks_z = ct.num_blocks(2)