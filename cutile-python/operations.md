# Operations[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#operations "Link to this heading")

## Load/Store[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#load-store "Link to this heading")

| [`bid`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bid.html#cuda.tile.bid "cuda.tile.bid") | Gets the index of current block. |
| --- | --- |
| [`num_blocks`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.num_blocks.html#cuda.tile.num_blocks "cuda.tile.num_blocks") | Gets the number of blocks along the axis. |
| [`num_tiles`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.num_tiles.html#cuda.tile.num_tiles "cuda.tile.num_tiles") | Gets the number of tiles in the [tile space](https://docs.nvidia.com/cuda/cutile-python/data.html#data-element-tile-space) of the array along the axis. |
| [`load`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.load.html#cuda.tile.load "cuda.tile.load") | Loads a tile from the array which is partitioned into a [tile space](https://docs.nvidia.com/cuda/cutile-python/data.html#data-element-tile-space). |
| [`store`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.store.html#cuda.tile.store "cuda.tile.store") | Stores a tile value into the array at the index of its [tile space](https://docs.nvidia.com/cuda/cutile-python/data.html#data-element-tile-space). |
| [`gather`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.gather.html#cuda.tile.gather "cuda.tile.gather") | Loads a tile from the array elements specified by indices. |
| [`scatter`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.scatter.html#cuda.tile.scatter "cuda.tile.scatter") | Stores a tile value into the array elements specified by indices. |

## Factory[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#factory "Link to this heading")

| [`arange`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.arange.html#cuda.tile.arange "cuda.tile.arange") | Creates a tile with value starting from 0 to size - 1. |
| --- | --- |
| [`full`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.full.html#cuda.tile.full "cuda.tile.full") | Creates a tile filled with given value. |
| [`ones`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.ones.html#cuda.tile.ones "cuda.tile.ones") | Creates a tile filled with ones. |
| [`zeros`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.zeros.html#cuda.tile.zeros "cuda.tile.zeros") | Creates a tile filled with zeros. |

## Shape & DType[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#shape-dtype "Link to this heading")

| [`cat`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.cat.html#cuda.tile.cat "cuda.tile.cat") | Concatenates two tiles along the axis. |
| --- | --- |
| [`broadcast_to`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.broadcast_to.html#cuda.tile.broadcast_to "cuda.tile.broadcast_to") | Broadcasts a tile to the specified shape following [Numpy broadcasting rule](https://numpy.org/devdocs/user/basics.broadcasting.html). |
| [`expand_dims`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.expand_dims.html#cuda.tile.expand_dims "cuda.tile.expand_dims") | Reshapes the tile by inserting a new axis of size 1 at given position. |
| [`reshape`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.reshape.html#cuda.tile.reshape "cuda.tile.reshape") | Reshapes a tile to the specified shape. |
| [`permute`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.permute.html#cuda.tile.permute "cuda.tile.permute") | Permutes the axes of the input tile. |
| [`transpose`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.transpose.html#cuda.tile.transpose "cuda.tile.transpose") | Transposes two axes of the input tile with at least 2 dimensions. |
| [`astype`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.astype.html#cuda.tile.astype "cuda.tile.astype") | Converts a tile to the specified data type. |
| [`bitcast`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitcast.html#cuda.tile.bitcast "cuda.tile.bitcast") | Reinterpets tile as being of specified data type. |

## Reduction[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#reduction "Link to this heading")

| [`sum`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.sum.html#cuda.tile.sum "cuda.tile.sum") | Performs sum reduction on tile along the axis. |
| --- | --- |
| [`max`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.max.html#cuda.tile.max "cuda.tile.max") | Performs max reduction on tile along the axis. |
| [`min`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.min.html#cuda.tile.min "cuda.tile.min") | Performs min reduction on tile along the axis. |
| [`prod`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.prod.html#cuda.tile.prod "cuda.tile.prod") | Performs prod reduction on tile along the axis. |
| [`argmax`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.argmax.html#cuda.tile.argmax "cuda.tile.argmax") | Performs argmax reduction on tile along the axis. |
| [`argmin`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.argmin.html#cuda.tile.argmin "cuda.tile.argmin") | Performs argmin reduction on tile along the axis. |
| [`reduce`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.reduce.html#cuda.tile.reduce "cuda.tile.reduce") | Apply custom reduction function along axis. |

## Scan[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#scan "Link to this heading")

| [`cumsum`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.cumsum.html#cuda.tile.cumsum "cuda.tile.cumsum") | Performs cumsum on tile along the axis. |
| --- | --- |
| [`cumprod`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.cumprod.html#cuda.tile.cumprod "cuda.tile.cumprod") | Performs cumprod on tile along the axis. |
| [`scan`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.scan.html#cuda.tile.scan "cuda.tile.scan") | Apply custom scan (inclusive prefix) function along axis. |

## Matmul[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#matmul "Link to this heading")

| [`mma`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.mma.html#cuda.tile.mma "cuda.tile.mma") | Matrix multiply-accumulate. |
| --- | --- |
| [`matmul`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.matmul.html#cuda.tile.matmul "cuda.tile.matmul") | Performs matrix multiply on the given tiles. |

## Selection[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#selection "Link to this heading")

| [`where`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.where.html#cuda.tile.where "cuda.tile.where") | Returns elements chosen from x or y depending on condition. |
| --- | --- |
| [`extract`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.extract.html#cuda.tile.extract "cuda.tile.extract") | Extracts a smaller tile from input tile. |

## Math[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#math "Link to this heading")

| [`add`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.add.html#cuda.tile.add "cuda.tile.add") | Elementwise add on two tiles. |
| --- | --- |
| [`sub`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.sub.html#cuda.tile.sub "cuda.tile.sub") | Elementwise sub on two tiles. |
| [`mul`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.mul.html#cuda.tile.mul "cuda.tile.mul") | Elementwise mul on two tiles. |
| [`truediv`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.truediv.html#cuda.tile.truediv "cuda.tile.truediv") | Elementwise truediv on two tiles. |
| [`floordiv`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.floordiv.html#cuda.tile.floordiv "cuda.tile.floordiv") | Elementwise floordiv on two tiles. |
| [`cdiv`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.cdiv.html#cuda.tile.cdiv "cuda.tile.cdiv") | Computes ceil(x / y). |
| [`pow`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.pow.html#cuda.tile.pow "cuda.tile.pow") | Elementwise pow on two tiles. |
| [`mod`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.mod.html#cuda.tile.mod "cuda.tile.mod") | Elementwise mod on two tiles. |
| [`minimum`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.minimum.html#cuda.tile.minimum "cuda.tile.minimum") | Elementwise minimum on two tiles. |
| [`maximum`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.maximum.html#cuda.tile.maximum "cuda.tile.maximum") | Elementwise maximum on two tiles. |
| [`negative`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.negative.html#cuda.tile.negative "cuda.tile.negative") | Same as \\-x. |
| [`abs`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.abs.html#cuda.tile.abs "cuda.tile.abs") | Perform abs on a tile. |
| [`isnan`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.isnan.html#cuda.tile.isnan "cuda.tile.isnan") | Perform isnan on a tile. |
| [`exp`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.exp.html#cuda.tile.exp "cuda.tile.exp") | Perform exp on a tile. |
| [`exp2`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.exp2.html#cuda.tile.exp2 "cuda.tile.exp2") | Perform exp2 on a tile. |
| [`log`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.log.html#cuda.tile.log "cuda.tile.log") | Perform log on a tile. |
| [`log2`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.log2.html#cuda.tile.log2 "cuda.tile.log2") | Perform log2 on a tile. |
| [`sqrt`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.sqrt.html#cuda.tile.sqrt "cuda.tile.sqrt") | Perform sqrt on a tile. |
| [`rsqrt`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.rsqrt.html#cuda.tile.rsqrt "cuda.tile.rsqrt") | Perform rsqrt on a tile. |
| [`sin`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.sin.html#cuda.tile.sin "cuda.tile.sin") | Perform sin on a tile. |
| [`cos`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.cos.html#cuda.tile.cos "cuda.tile.cos") | Perform cos on a tile. |
| [`tan`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.tan.html#cuda.tile.tan "cuda.tile.tan") | Perform tan on a tile. |
| [`sinh`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.sinh.html#cuda.tile.sinh "cuda.tile.sinh") | Perform sinh on a tile. |
| [`cosh`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.cosh.html#cuda.tile.cosh "cuda.tile.cosh") | Perform cosh on a tile. |
| [`tanh`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.tanh.html#cuda.tile.tanh "cuda.tile.tanh") | Perform tanh on a tile. |
| [`floor`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.floor.html#cuda.tile.floor "cuda.tile.floor") | Perform floor on a tile. |
| [`ceil`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.ceil.html#cuda.tile.ceil "cuda.tile.ceil") | Perform ceil on a tile. |

## Bitwise[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#bitwise "Link to this heading")

| [`bitwise_and`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitwise_and.html#cuda.tile.bitwise_and "cuda.tile.bitwise_and") | Elementwise bitwise\\_and on two tiles. |
| --- | --- |
| [`bitwise_or`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitwise_or.html#cuda.tile.bitwise_or "cuda.tile.bitwise_or") | Elementwise bitwise\\_or on two tiles. |
| [`bitwise_xor`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitwise_xor.html#cuda.tile.bitwise_xor "cuda.tile.bitwise_xor") | Elementwise bitwise\\_xor on two tiles. |
| [`bitwise_lshift`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitwise_lshift.html#cuda.tile.bitwise_lshift "cuda.tile.bitwise_lshift") | Elementwise bitwise\\_lshift on two tiles. |
| [`bitwise_rshift`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitwise_rshift.html#cuda.tile.bitwise_rshift "cuda.tile.bitwise_rshift") | Elementwise bitwise\\_rshift on two tiles. |
| [`bitwise_not`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.bitwise_not.html#cuda.tile.bitwise_not "cuda.tile.bitwise_not") | Elementwise bitwise not on a tile. |

## Comparison[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#comparison "Link to this heading")

| [`greater`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.greater.html#cuda.tile.greater "cuda.tile.greater") | Compare two tiles elementwise with \\>. |
| --- | --- |
| [`greater_equal`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.greater_equal.html#cuda.tile.greater_equal "cuda.tile.greater_equal") | Compare two tiles elementwise with \\>=. |
| [`less`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.less.html#cuda.tile.less "cuda.tile.less") | Compare two tiles elementwise with <. |
| [`less_equal`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.less_equal.html#cuda.tile.less_equal "cuda.tile.less_equal") | Compare two tiles elementwise with <=. |
| [`equal`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.equal.html#cuda.tile.equal "cuda.tile.equal") | Compare two tiles elementwise with \\==. |
| [`not_equal`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.not_equal.html#cuda.tile.not_equal "cuda.tile.not_equal") | Compare two tiles elementwise with !=. |

## Atomic[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#atomic "Link to this heading")

| [`atomic_cas`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_cas.html#cuda.tile.atomic_cas "cuda.tile.atomic_cas") | Bulk atomic compare-and-swap on array elements with given indices. |
| --- | --- |
| [`atomic_xchg`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_xchg.html#cuda.tile.atomic_xchg "cuda.tile.atomic_xchg") | Bulk atomic exchange of array elements at given indices. |
| [`atomic_add`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_add.html#cuda.tile.atomic_add "cuda.tile.atomic_add") | Bulk atomic post-increment of array elements at given indices. |
| [`atomic_max`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_max.html#cuda.tile.atomic_max "cuda.tile.atomic_max") | Bulk atomic maximum value assignment on array elements at given indices. |
| [`atomic_min`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_min.html#cuda.tile.atomic_min "cuda.tile.atomic_min") | Bulk atomic minimum value assignment on array elements at given indices. |
| [`atomic_and`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_and.html#cuda.tile.atomic_and "cuda.tile.atomic_and") | Bulk atomic AND operation on array elements at given indices. |
| [`atomic_or`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_or.html#cuda.tile.atomic_or "cuda.tile.atomic_or") | Bulk atomic OR operation on array elements at given indices. |
| [`atomic_xor`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.atomic_xor.html#cuda.tile.atomic_xor "cuda.tile.atomic_xor") | Bulk atomic XOR operation on array elements at given indices. |

## Utility[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#utility "Link to this heading")

| [`printf`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.printf.html#cuda.tile.printf "cuda.tile.printf") | Print the values at runtime from the device |
| --- | --- |
| [`print`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.print.html#cuda.tile.print "cuda.tile.print") | Print values at runtime from the device using Python-style syntax. |
| [`assert_`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.assert_.html#cuda.tile.assert_ "cuda.tile.assert_") | Assert that all elements of the given tile are True. |

## Metaprogramming Support[#](https://docs.nvidia.com/cuda/cutile-python/operations.html#metaprogramming-support "Link to this heading")

| [`static_assert`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.static_assert.html#cuda.tile.static_assert "cuda.tile.static_assert") | Asserts that a condition is true at compile time. |
| --- | --- |
| [`static_eval`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.static_eval.html#cuda.tile.static_eval "cuda.tile.static_eval") | Evaluates the given Python expression at compile time. |
| [`static_iter`](https://docs.nvidia.com/cuda/cutile-python/generated/cuda.tile.static_iter.html#cuda.tile.static_iter "cuda.tile.static_iter") | Iterates at compile time. |
