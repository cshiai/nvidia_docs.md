# cuda.tile.Array



### `class cuda.tile.Array`

A global array (or array) is a container of objects stored in a logical
multidimensional space.
Global arrays are always stored in memory.
Copying an array does not copy the underlying data.
Global arrays can be used in host code and tile code.
They can be kernel parameters.
Any object that implements the DLPack format or the CUDA Array Interface can be used
as a global array. Example: CuPy arrays and PyTorch tensors.

property dtype
The data type of the array’s elements.

Return type:
DType (constant)

property shape
The number of elements in each of the array’s dimensions.

Return type:
tuple[int32,…]

property strides
The number of elements to step in each dimension while traversing the array.

Return type:
tuple[int32,…]

property ndim
The number of dimensions in the array.

Return type:
int (constant)