# Operations


## Load/Store


| bid | Gets the index of current block. |
| --- | --- |
| num_blocks | Gets the number of blocks along the axis. |
| num_tiles | Gets the number of tiles in the tile space of the array along the axis. |
| load | Loads a tile from the array which is partitioned into a tile space. |
| store | Stores a tile value into the array at the index of its tile space. |
| gather | Loads a tile from the array elements specified by indices. |
| scatter | Stores a tile value into the array elements specified by indices. |


## Factory


| arange | Creates a tile with value starting from 0 to size - 1. |
| --- | --- |
| full | Creates a tile filled with given value. |
| ones | Creates a tile filled with ones. |
| zeros | Creates a tile filled with zeros. |


## Shape & DType


| cat | Concatenates two tiles along the axis. |
| --- | --- |
| broadcast_to | Broadcasts a tile to the specified shape following Numpy broadcasting rule. |
| expand_dims | Reshapes the tile by inserting a new axis of size 1 at given position. |
| reshape | Reshapes a tile to the specified shape. |
| permute | Permutes the axes of the input tile. |
| transpose | Transposes two axes of the input tile with at least 2 dimensions. |
| astype | Converts a tile to the specified data type. |


## Reduction


| sum | Performs sum reduction on tile along the axis. |
| --- | --- |
| max | Performs max reduction on tile along the axis. |
| min | Performs min reduction on tile along the axis. |
| prod | Performs prod reduction on tile along the axis. |
| argmax | Performs argmax reduction on tile along the axis. |
| argmin | Performs argmin reduction on tile along the axis. |


## Scan


| cumsum | Performs cumsum on tile along the axis. |
| --- | --- |
| cumprod | Performs cumprod on tile along the axis. |


## Matmul


| mma | Matrix multiply-accumulate. |
| --- | --- |
| matmul | Performs matrix multiply on the given tiles. |


## Selection


| where | Returns elements chosen from x or y depending on condition. |
| --- | --- |
| extract | Extracts a smaller tile from input tile. |


## Math


| add | Elementwise add on two tiles. |
| --- | --- |
| sub | Elementwise sub on two tiles. |
| mul | Elementwise mul on two tiles. |
| truediv | Elementwise truediv on two tiles. |
| floordiv | Elementwise floordiv on two tiles. |
| cdiv | Computes ceil(x / y). |
| pow | Elementwise pow on two tiles. |
| mod | Elementwise mod on two tiles. |
| minimum | Elementwise minimum on two tiles. |
| maximum | Elementwise maximum on two tiles. |
| negative | Same as -x. |
| exp | Perform exp on a tile. |
| exp2 | Perform exp2 on a tile. |
| log | Perform log on a tile. |
| log2 | Perform log2 on a tile. |
| sqrt | Perform sqrt on a tile. |
| rsqrt | Perform rsqrt on a tile. |
| sin | Perform sin on a tile. |
| cos | Perform cos on a tile. |
| tan | Perform tan on a tile. |
| sinh | Perform sinh on a tile. |
| cosh | Perform cosh on a tile. |
| tanh | Perform tanh on a tile. |
| floor | Perform floor on a tile. |
| ceil | Perform ceil on a tile. |


## Bitwise


| bitwise_and | Elementwise bitwise_and on two tiles. |
| --- | --- |
| bitwise_or | Elementwise bitwise_or on two tiles. |
| bitwise_xor | Elementwise bitwise_xor on two tiles. |
| bitwise_lshift | Elementwise bitwise_lshift on two tiles. |
| bitwise_rshift | Elementwise bitwise_rshift on two tiles. |
| bitwise_not | Elementwise bitwise not on a tile. |


## Comparison


| greater | Compare two tiles elementwise with >. |
| --- | --- |
| greater_equal | Compare two tiles elementwise with >=. |
| less | Compare two tiles elementwise with <. |
| less_equal | Compare two tiles elementwise with <=. |
| equal | Compare two tiles elementwise with ==. |
| not_equal | Compare two tiles elementwise with !=. |


## Atomic


| atomic_cas | Bulk atomic compare-and-swap on array elements with given indices. |
| --- | --- |
| atomic_xchg | Bulk atomic exchange of array elements at given indices. |
| atomic_add | Bulk atomic post-increment of array elements at given indices. |
| atomic_max | Bulk atomic maximum value assignment on array elements at given indices. |
| atomic_min | Bulk atomic minimum value assignment on array elements at given indices. |
| atomic_and | Bulk atomic AND operation on array elements at given indices. |
| atomic_or | Bulk atomic OR operation on array elements at given indices. |
| atomic_xor | Bulk atomic XOR operation on array elements at given indices. |


## Utility


| printf | Print the values at runtime from the device |
| --- | --- |
| assert_ | Assert that all elements of the given tile are True. |