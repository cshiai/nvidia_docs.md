# cuda.tile.Tile



### `class cuda.tile.Tile`

A tile array (or tile) is an immutable multidimensional collection of values that is
local to a block.
The contents of a tile do not necessarily have a representation in memory.
Tiles can be created by loading from global arrays or with factory functions.
Tiles can also be stored into global arrays.
Tiles shall not be used in host code; they can only be used in tile code.
Tiles shall not be kernel parameters.
Each dimension of a tile shall be a power of 2.

property dtype
The data type of the tile’s elements.

Return type:
DType (constant)

property shape
The number of elements in each of the tile’s dimensions.

Return type:
tuple[const int,…]

property ndim
The number of dimensions in the tile.

Return type:
int (constant)

item()
Extract scalar (0D Tile) from a single element tile.
Tile must contain only 1 element.

Returns:
A 0D Tile usable as a scalar.

Return type:
Tile

Examples
>>> tx = ct.full((1,), 0, dtype=ct.int32)
>>> x = tx.item()
>>> ty = ct.load(array, (0, x), shape=(4, 4))

extract(index, shape)
See extract().

reshape(shape)
See reshape().

permute(axes)
See permute().

transpose(axis0=None, axis1=None)
See transpose().

astype(dtype)
See astype().

__index__()
0D Tile can be used as index in range

__getitem__(index)
Syntax sugar for expand_dim

__add__(other)

__sub__(other)

__mul__(other)

__truediv__(other)

__floordiv__(other)

__mod__(other)

__pow__(other)

__and__(other)

__or__(other)
Return self|value.

__xor__(other)

__radd__(other)

__rsub__(other)

__rmul__(other)

__rtruediv__(other)

__rfloordiv__(other)

__rmod__(other)

__rpow__(other)

__rand__(other)

__ror__(other)
Return value|self.

__rxor__(other)

__ge__(other)
Return self>=value.

__gt__(other)
Return self>value.

__le__(other)
Return self<=value.

__lt__(other)
Return self<value.

__eq__(other)
Return self==value.

__ne__(other)
Return self!=value.

__hash__ = None