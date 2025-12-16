# cuda.tile.assert_



### `cuda.tile.assert_(cond, /, message=None)`

Assert that all elements of the given tile are True.

Parameters:

cond (Tile) – Boolean tile.
message (str) – Message to print if condition is false.

Notes
This operation has significant overhead, and should only be used
for debugging purpose.
Examples
>>> tile = ct.arange(4, dtype=ct.int32)
>>> ct.assert_(tile > 2)
>>> ct.assert_(tile > 2, "Not all elements in tile are greater than 2")