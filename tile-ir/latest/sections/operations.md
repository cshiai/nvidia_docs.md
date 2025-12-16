# 8. Operations


This section describes a complete and categorized list of all Tile IR instructions names, signatures, and semantics.


## 8.1. Meta Types


Operations have arguments which are Tile IR values with Tile IR types but many operations have immediate or static arguments which correspond to attributes in the MLIR dialect. These meta types are not representable in the Tile IR type system but are used to construct Tile IR programs and only present at compile time. Operations in the specification are described abstractly in both the Tile IR IR and bytecode independent of the MLIR or bytecode encoding. For each of these types we provide a definition of them below and link to them from each operation.


Note


The convention is that the meta types are capitalized and Tile IR types are snake cased.


The convention is that the meta types are capitalized and the native Tile IR types are camel cased are snake cased.


### 8.1.1. Symbol


`Symbol` a symbol in the program, begins with `@` and uniquely identifies a symbol in the program.


### 8.1.2. Flag


`Flag` a boolean value that can be used to control the behavior of an operation.


### 8.1.3. Token


Token represents a memory ordering token that can be used to control the ordering of memory operations.


### 8.1.4. Variadic


`Variadic` represents an argument which can accept a statically sized, but variable, number of arguments.


### 8.1.5. Any


`Any` represents a value of any valid Tile IR type.


### 8.1.6. Name


`Name` represents a name in the program, begins with `#` and uniquely identifies a name in the program.


### 8.1.7. Type


`Type` represents a Tile IR type and are attached as attributes to operations which define IR items.


### 8.1.8. Array


`Array` represents a statically sized array of values that can be passed to attributes.


### 8.1.9. String


`String` represents a string value that can be passed to attributes.


### 8.1.10. bool


`bool` represents a boolean value that can be passed to attributes.


### 8.1.11. DenseConstant


`DenseConstant` represents a dense constant value that can be passed to attributes.


### 8.1.12. view_type


`view_type` represents a type which implements the view interface, currently this is only implemented by partition_view but will have new implementers in future releases.


## 8.2. Operation Design Considerations


The design of Tile IR has a set of design considerations that apply to all operations in the dialect this section introduces some of the common design considerations that apply to all operations, or to classes of operations generically.


### 8.2.1. Explicit Broadcast


There are no implicit broadcast performed by operations in the Tile IR dialect all operations that require operands of the same shape must be explicitly broadcasted. For example to use the [cuda_tile.offset](operations.html#op-cuda-tile-offset) operation to add an offset tile to a pointer, the pointer and offset must be reshaped or broadcasted to have the same shape using the [cuda_tile.reshape](operations.html#op-cuda-tile-reshape) or [cuda_tile.broadcast](operations.html#op-cuda-tile-broadcast) operations.


### 8.2.2. Distinct Floating-Point and Integer Operations


Numeric ooerations are split across integer and floating-point types due to differences in flags such as rounding modes, `NaN` handling, and fast math.


For example, the [cuda_tile.addf](operations.html#op-cuda-tile-addf) operation supports a rounding attribute, but the addi operation does not.


### 8.2.3. Explicit Overflow Annotations


Some operations such as [cuda_tile.addi](operations.html#op-cuda-tile-addi) support an explicit overflow annotation that expresses the expected overflow behavior of the operation.


These attributes serve as assumptions that an implementation may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


We recommend that generators of Tile IR programs utilize these annotations to help the implementation reason about the overflow behavior of the operation, enabling extra optimization opportunities.


## 8.3. Core


### 8.3.1. cuda_tile.broadcast


*Broadcast tile to new shape*


```
cuda_tile.broadcast %source
```


#### Parameters


 - source ([tile](types.html#type-tile)) - The tile to broadcast. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The broadcasted tile. 13.1


#### Description


The `broadcast` operation expands each unary (`1`) dimension in the input tile by duplicating the data along that dimension.


Expansion happens only for dimensions of size one that are stretched or “copied” to match the size of the dimension implied by the result type of the operation. The operation does not change the rank of the source tile. Any change to the rank of the source tile must be made using reshape-like operations before broadcasting.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same element type (tile).
 - `source` and `result` must have the same rank.


### 8.3.2. cuda_tile.cat


*Concatenate tiles along specified dimension*


```
cuda_tile.cat %lhs %rhs %dim
```


#### Parameters


 - lhs ([tile](types.html#type-tile)) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)) - The right hand side operand. 13.1
 - dim ([i64](types.html#subsection-element-types)) - The dimension along which to concatenate. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The concatenated result tile. 13.1


#### Description


The `cat` operation concatenates the two input tiles. The input tiles must have the same shape in all but the concatenating dimension. Concatenation happens along the dimension specified by the the attribute `dim` the resulting dimension is the sum of the the two input tiles concatenating dimension.

  \[\begin{split}\text{cat}(x, y, dim_{cat})[ \vec{i} ] = \begin{cases} x[..., i_{cat}, ..., i_n] & \text{if } i_{cat} < d_{cat} \\ y[..., i_{cat} - d_{cat}, ..., i_n] & \text{if } i_{cat} \geq d_{cat} \end{cases}\end{split}\]
#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same rank.
 - `lhs`, `rhs` and `result` must have the same element type ([tile](types.html#type-tile)).


#### Examples


```
// A valid invocation of cat.
%0 = cat %arg0, %arg1 dim = 1
  : tile<2x4xf32>, tile<2x4xf32> -> tile<2x8xf32>

// >>> %arg0 = tile([[ A, B, C ],
//                   [ D, E, F ]])
// >>> %arg1 = tile([[ 1, 2, 3 ],
//                   [ 4, 5, 6 ]])
// >>> %0 = tile([[ A, B, C, 1, 2, 3 ],
//                [ D, E, F, 4, 5, 6 ]])

// A valid invocation of cat.
%1 = cat %arg0, %arg1 dim = 0
  : tile<2x4xf32>, tile<2x4xf32> -> tile<4x4xf32>

// >>> %arg0 = tile([[ A, B, C ],
//                   [ D, E, F ]])
//
// >>> %arg1 = tile([[ 1, 2, 3 ],
//                   [ 4, 5, 6 ]])
//
// >>> %1 = tile([[ A, B, C ],
//                [ D, E, F ],
//                [ 1, 2, 3 ],
//                [ 4, 5, 6 ]])
```


See [cuda_tile.cat_0](appendix.html#example-cuda-tile-cat-0) for the full example listing.


### 8.3.3. cuda_tile.cmpf


*Element-wise floating-point comparison*


```
cuda_tile.cmpf %comparison_predicate %comparison_ordering %lhs %rhs
```


#### Parameters


 - comparison_predicate ([ComparisonPredicate](operations.html#op-attribute-cuda-tile-cmpf-comparisonpredicate-attr)) - The comparison predicate. 13.1
 - comparison_ordering ([ComparisonOrdering](operations.html#op-attribute-cuda-tile-cmpf-comparisonordering-attr)) - The comparison ordering. 13.1
 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The result of the comparison. 13.1


#### Description


The `cmpf` operation is a generic comparison for float-like types. The operands must have the same shape and type, and this type must be a float type.


The result is `1` if the comparison is true and `0` otherwise. The comparison is performed element-wise and the element of the result indicates whether the comparison is true for the operand elements with the same indices as those of the result.

  \[\begin{split}\text{cmpf}(x, y, \text{pred})_i = \begin{cases} 1 & \text{if } x_i \text{ pred } y_i \\ 0 & \text{otherwise} \end{cases}\end{split}\]
The `comparison_predicate` attribute specifies the kind of comparison to be performed.


 - `equal` - Equal comparison.
 - `not_equal` - Not equal comparison.
 - `less_than` - Less than comparison.
 - `less_than_or_equal` - Less than or equal comparison.
 - `greater_than` - Greater than comparison.
 - `greater_than_or_equal` - Greater than or equal comparison.


The `comparison_ordering` attribute specifies the kind of ordering to be performed in the comparison operation.


 - `unordered` - Unordered comparison.
 - `ordered` - Ordered comparison.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs` and `rhs` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - Result type has i1 element type and same shape as operands
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%lhs0 = constant <f16: 0.0> : tile<f16>
%rhs0 = constant <f16: 0.0> : tile<f16>

// Custom form of scalar "ordered equal" comparison.
%x0 = cmpf equal ordered %lhs0, %rhs0 : tile<f16> -> tile<i1>

%lhs1 = constant <f16: 0.0> : tile<2x2xf16>
%rhs1 = constant <f16: 0.0> : tile<2x2xf16>

// Custom form of scalar "unordered less than" comparison.
%x2 = cmpf less_than unordered %lhs1, %rhs1 : tile<2x2xf16> -> tile<2x2xi1>

%lhs2 = constant <f64: 0.0> : tile<2x2xf64>
%rhs2 = constant <f64: 0.0> : tile<2x2xf64>
```


See [cuda_tile.cmpf_0](appendix.html#example-cuda-tile-cmpf-0) for the full example listing.


### 8.3.4. cuda_tile.cmpi


*Element-wise integer comparison*


```
cuda_tile.cmpi %comparison_predicate %lhs %rhs %signedness
```


#### Parameters


 - comparison_predicate ([ComparisonPredicate](operations.html#op-attribute-cuda-tile-cmpi-comparisonpredicate-attr)) - The comparison predicate. 13.1
 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-cmpi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The result of the comparison. 13.1


#### Description


The `cmpi` operation is a generic comparison for integer-like types. The operands must have the same shape and type, and this type must be an integer type. The result type has i1 element type and the same shape as the operands.


The result is `1` if the comparison is true and `0` otherwise. The comparison is performed element-wise and the element of the result indicates whether the comparison is true for the operand elements with the same indices as those of the result.

  \[\begin{split}\text{cmpi}(x, y, \text{pred})_i = \begin{cases} 1 & \text{if } x_i \text{ pred } y_i \\ 0 & \text{otherwise} \end{cases}\end{split}\]
The `comparison_predicate` attribute specifies the kind of comparison to be performed.


 - `equal` - Equal comparison.
 - `not_equal` - Not equal comparison.
 - `less_than` - Less than comparison.
 - `less_than_or_equal` - Less than or equal comparison.
 - `greater_than` - Greater than comparison.
 - `greater_than_or_equal` - Greater than or equal comparison.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs` and `rhs` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - Result type has i1 element type and same shape as operands
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%lhs0 = constant <i16: 0> : tile<i16>
%rhs0 = constant <i16: 0> : tile<i16>

// Scalar "signed less than" comparison.
%x0 = cmpi less_than %lhs0, %rhs0, signed : tile<i16> -> tile<i1>

%lhs1 = constant <i64: 0> : tile<2x2xi64>
%rhs1 = constant <i64: 0> : tile<2x2xi64>

// Tile equality comparison.
// There is no difference between "signed" and "unsigned" when performing equality and inequality comparison.
%x1 = cmpi equal %lhs1, %rhs1, signed : tile<2x2xi64> -> tile<2x2xi1>
```


See [cuda_tile.cmpi_0](appendix.html#example-cuda-tile-cmpi-0) for the full example listing.


### 8.3.5. cuda_tile.constant


*Construct a constant tile*


```
cuda_tile.constant %value
```


#### Parameters


 - value ([DenseConstant](operations.html#type-denseconstant)) - The constant value to create. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types) | [f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The constant tile. 13.1


#### Description


The `constant` operation creates a tile initialized by `$value`.


There are two main forms of using the operation:


 - One where the value is a single constant specified by `<D: c>` and the tile is filled with identical values for all elements with element type `D`.
 - One where the value is a list of constants specified by `dense<D: [c0, c1, c2, ...]>` and the constant value’s shape must match the tile’s shape with the element type `D`.


The annotated type of the tile constrains its rank, shape, and element type.


#### Constraints


 - The operation has no operands and may be constant folded.
 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `value` and `result` must have the same shape and element type ([DenseConstant](operations.html#type-denseconstant)).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%c0 = constant <i32: 0> : tile<i32>
%c1 = constant <i64: 1> : tile<i64>
%c2 = constant <i32: [0, 1, 2, 3]> : tile<4xi32>
%c3 = constant <f32: 0.0> : tile<2x4xf32>
%c4 = constant <f64: [0.0, 1.0, 2.0, 3.0]> : tile<4xf64>
```


See [cuda_tile.constant_0](appendix.html#example-cuda-tile-constant-0) for the full example listing.


### 8.3.6. cuda_tile.entry


*Define a tile kernel*


```
cuda_tile.entry %sym_name %function_type %arg_attrs %res_attrs %optimization_hints
```


#### Parameters


 - sym_name ([Symbol](operations.html#type-symbol)) - The name of the function. 13.1
 - function_type ([Type](operations.html#type-type)) - The type of the function. 13.1
 - arg_attrs ([Attributes](operations.html#type-attributes)) - The argument attributes of the function: none of these are supported by TileIR at the moment. 13.1
 - res_attrs ([Attributes](operations.html#type-attributes)) - The result attributes of the function: none of these are supported by TileIR at the moment. 13.1
 - optimization_hints ([OptimizationHints](operations.html#op-attribute-cuda-tile-entry-optimizationhints-attr)) - Compiler architecture-specific optimization hints 13.1


#### Results


No results.


#### Description


The `entry` operation defines a tile kernel; a kernel is a function that can serve as the program entry point. It has a unique name per-module. A kernel can not return any value. It must be launched from the host side using `cuLaunchKernel` or similar CUDA runtime API functions.


Tile kernels require that the user specifies the 3-d grid dimensions at launch which defines the number of tile blocks (or kernel instances) that will execute the kernel in parallel.


For detailed semantics of tile kernels see [Tile Kernel](semantics.html#sub-sec-tile-kernel).


The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.


The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.


 - `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda_tile.entry](operations.html#op-cuda-tile-entry).
 - `allow_tma` - suggest whether to use TMA for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).
 - `latency` - latency hint for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).


For example they can be annotated as:


```
optimization_hints=<
  sm_100 = {num_cta_in_cga = 8},
  sm_120 = {num_cta_in_cga = 16}
>
```


#### Constraints


 - The operation must be a symbol in the global symbol table.
 - The operation must implement callable target interface.
 - The operation must implement function-like behavior interface.
 - The region must not capture SSA values defined above the operation.
 - The operation must provide custom parsing and printing methods.
 - Each provided region must contain exactly one block.


### 8.3.7. cuda_tile.extract


*Extract a subtile from a tile*


```
cuda_tile.extract %source %indices
```


#### Parameters


 - source ([tile](types.html#type-tile)) - The source tile to extract from. 13.1
 - indices ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>>) - The indices of the slice to extract. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The extracted subtile. 13.1


#### Description


The `extract` operation extracts a subtile from the given source tile.


The shape of the result tile must divide the shape of the source tile evenly e.g., `tile<4xf32>` is a valid extraction from `tile<8xf32>`, but `tile<3xf32>` is not.


The `$indices` indicate the number of the slice to extract, but *importantly* not the offsets used to construct the subtile for extraction. The semantics of extract means that only full size slices can be extracted.


Slices of a source tile with the same shape are non-overlapping by definition for unique indices.


The `indices` operands are interpreted as unsigned integers.


Warning


If the `indices` specify a non-existent (i.e., out-of-bounds) slice, the behavior of the operation is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same rank.


#### Examples


```
// Extract a subtile from %t at dim_0 = [4;8) and dim_1 = [4;6).
%c1 = constant <i32: 1> : tile<i32>
%c2 = constant <i32: 2> : tile<i32>
%t = constant <f32: 0.0> : tile<32x8xf32>
// Valid indices are: [ {0, 1, 2, 3, 4, 5, 6, 7}, {0, 1, 2, 3} ]
%0 = extract %t[%c1, %c2]
    : tile<32x8xf32> -> tile<4x2xf32>
```


See [cuda_tile.extract_0](appendix.html#example-cuda-tile-extract-0) for the full example listing.


### 8.3.8. cuda_tile.get_global


*Get a pointer to a global variable*


```
cuda_tile.get_global %name
```


#### Parameters


 - name ([Symbol](operations.html#type-symbol)) - The name of the global variable. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[ptr](types.html#type-ptr)>) - The result of the get_global operation. 13.1


#### Description


The `get_global` operation returns a pointer to the specified `global` variable. A global variable is a form of static global memory allocation that can be declared using the [cuda_tile.global](operations.html#op-cuda-tile-global) operation.


The element type of the returned pointer will be of the same type as the element type of the declared global variable.


For detailed semantics of global variables see [Global Variable](semantics.html#sub-sec-tile-global).


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


#### Examples


```
global @val <f32: [0.1, 0.2, 0.3, 0.4]> : tile<4xf32>

entry @example() {
  %ptr = get_global @val : tile<ptr<f32>>
  return
}
```


See [cuda_tile.get_global_0](appendix.html#example-cuda-tile-get-global-0) for the full example listing.


### 8.3.9. cuda_tile.get_num_tile_blocks


*Get total number of tile blocks*


```
cuda_tile.get_num_tile_blocks
```


#### Parameters


No parameters.


#### Results


 - gridSize_x ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The number of tile blocks in dimension `x`. 13.1
 - gridSize_y ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The number of tile blocks in dimension `y`. 13.1
 - gridSize_z ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The number of tile blocks in dimension `z`. 13.1


#### Description


The `get_num_tile_blocks` operation queries the total number of tile blocks in the form of a 3-tuple specifying the extent of each grid dimension.


A tile `id` is a coordinate in 3-space and therefore the must also be a 3-tuple containing the extent of each dimension: `x`, `y` and `z`.


When launching 1- or 2-dimensional grids, the unspecified dimensions will have a cardinality of 1.


For example if the grid used to launch the kernel is `(1024, 1024)` then the result of this operation will be `(1024, 1024, 1)`.


Note


Grid Dimension Limitation: Grid dimensions are limited to 2^24-1 (16,777,215) per axis. Larger dimensions may result in incorrect tile block ID calculations. Use multiple kernel launches for larger workloads.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
entry @example() {
  %x, %y, %z = get_num_tile_blocks : tile<i32>
  // print "x: %, y: %, z: %\n", %x, %y, %z : tile<i32>, tile<i32>, tile<i32>
}
```


See [cuda_tile.get_num_tile_blocks_0](appendix.html#example-cuda-tile-get-num-tile-blocks-0) for the full example listing.


### 8.3.10. cuda_tile.get_tile_block_id


*Get the currently executing tile block coordinates*


```
cuda_tile.get_tile_block_id
```


#### Parameters


No parameters.


#### Results


 - blockId_x ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The tile block ID for dimension `x`. 13.1
 - blockId_y ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The tile block ID for dimension `y`. 13.1
 - blockId_z ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The tile block ID for dimension `z`. 13.1


#### Description


`get_tile_block_id` returns a 3-d tile block coordinates (or ID) of the currently executing tile block.


A tile ID has three dimensions: `x`, `y`, and `z`. This operation returns all three of them simultaneously. The value of each dimension returned by this operation is between `0` (including) and the value returned by `get_num_tile_blocks` for the respective axis (excluding), represented by the inclusive interval `[0, get_num_tile_blocks(dim) - 1]` . Grid dimensions unspecified at kernel launch (i.e., a 1-d or 2-d grid) will always be `0` for all tile blocks.


Note


Grid Dimension Limitation: Grid dimensions are limited to 2^24-1 (16,777,215) per axis. Larger dimensions may result in incorrect tile block ID calculations. Use multiple kernel launches for larger workloads.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - The operation’s result type may be inferred from its operands and attributes.


### 8.3.11. cuda_tile.global


*Allocate static global memory*


```
cuda_tile.global %sym_name %value %alignment
```


#### Parameters


 - sym_name ([Symbol](operations.html#type-symbol)) - The name of the global variable. 13.1
 - value ([DenseConstant](operations.html#type-denseconstant)) - The value to initialize the allocation with. 13.1
 - alignment ([i64](types.html#subsection-element-types)) - The alignment of the buffer. 13.1


#### Results


No results.


#### Description


The `global` operation statically allocates a mutable 1-dimensional location in global memory and initializes it using `value`. The initialization of the allocation is performed at [CUDA module](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g9e4ef4dcfba4662b2299acb8d049a1ef) load time. The lifetime of the allocation is the same as the lifetime of the module.


The allocation may be read or written to by first using [cuda_tile.get_global](operations.html#op-cuda-tile-get-global) to obtain a pointer to the the memory and then read using [cuda_tile.load_ptr_tko](operations.html#op-cuda-tile-load-ptr-tko) or written to using [cuda_tile.store_ptr_tko](operations.html#op-cuda-tile-store-ptr-tko).


The initial values are stored in memory in linear order, so the pointer returned by [cuda_tile.get_global](operations.html#op-cuda-tile-get-global) points to the first element, and offsetting the pointer by x would allow to load element at position x.


`global` operations must be directly nested within the Tile IR module. They cannot be defined inside functions. As globals are defined at the module scope their names are globally unique symbols and must not collide with any other symbol in the module.


For more detailed semantics of global variables see [Global Variable](semantics.html#sub-sec-tile-global).


#### Constraints


 - The operation must be a symbol in the global symbol table.


#### Examples


```
global @val alignment = 128 <f32: [0.1, 0.2, 0.3, 0.4]> : tile<4xf32>
entry @example() {}
```


See [cuda_tile.global_0](appendix.html#example-cuda-tile-global-0) for the full example listing.


### 8.3.12. cuda_tile.iota


*Generate a 1-d tile range from 0 to n-1*


```
cuda_tile.iota
```


#### Parameters


No parameters.


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result of the iota operation. 13.1


#### Description


The `iota` operation generates a 1-d tile with a sequence of integer values. The starting value is `0` and the stride is `1`. If the shape of the result tile is `(n)`, then the generated values are `[0, n - 1]`.

  \[\text{iota}(n)_i = i \quad \text{for } i \in [0, n-1]\]
The result values should be interpreted as unsigned integers.


Note


The number of elements in the result tile must not exceed the maximum value that the element type can express.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.3.13. cuda_tile.mmaf


*Floating-point matrix-multiply-accumulate*


```
cuda_tile.mmaf %lhs %rhs %acc
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [tile](types.html#type-tile)<[tf32](types.html#subsection-element-types)>>) - The left hand side matrix operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [tile](types.html#type-tile)<[tf32](types.html#subsection-element-types)>>) - The right hand side matrix operand. 13.1
 - acc ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The accumulator matrix operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result matrix after multiplication and accumulation. 13.1


#### Description


The `mmaf` operation implements an MMA (matrix-multiply-accumulate) operation for floating-point tiles. It performs matrix multiplication on the floating-point tiles `lhs` and `rhs`, then adds the tile `acc` to the result. `lhs`, `rhs`, and `acc` must be 2D tiles or 3D tiles. The latter case indicates a batched matrix multiplication.

  \[\text{mmaf}(A, B, C)_{ij} = \sum_{k=0}^{K-1} A_{ik} \times B_{kj} + C_{ij}\]
The types of all operands must be a supported combination (see [mmaf Supported Data Types](operations.html#table-cuda-tile-mmaf-0)).


Shapes must be a valid matrix multiplication configuration. Unbatched (2D) MMA expects the operands `lhs`, `rhs`, and `acc` to have shapes `M x K`, `K x N`, and `M x N` (respectively). Batched (3D) MMA expects the operands to have shapes `B x M x K`, `B x K x N`, and `B x M x N` (respectively).


The table below shows the supported output types for each possible `mmaf` input type. Input operands must be of the same element type.


| Input Type | Supported Output Types |
| --- | --- |
| f8E4M3FN | f16 or f32 |
| f8E5M2 | f16 or f32 |
| f16 | f16 or f32 |
| bf16 | f32 |
| tf32 | f32 |
| f32 | f32 |
| f64 | f64 |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `acc` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - `lhs` and `rhs` must have the same element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [tile](types.html#type-tile)<[tf32](types.html#subsection-element-types)>>).
 - `lhs`, `rhs` and `acc` must have the same rank.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%lhs0 = constant <f16: 0.0> : tile<4x8xf16>
%rhs0 = constant <f16: 0.0> : tile<8x2xf16>
%acc0 = constant <f32: 0.0> : tile<4x2xf32>

%0 = mmaf %lhs0, %rhs0, %acc0
    : tile<4x8xf16>, tile<8x2xf16>,
      tile<4x2xf32>

%lhs1 = constant <f16: 0.0> : tile<2x4x8xf16>
%rhs1 = constant <f16: 0.0> : tile<2x8x2xf16>
%acc1 = constant <f32: 0.0> : tile<2x4x2xf32>

%1 = mmaf %lhs1, %rhs1, %acc1
    : tile<2x4x8xf16>, tile<2x8x2xf16>,
      tile<2x4x2xf32>
```


See [cuda_tile.mmaf_0](appendix.html#example-cuda-tile-mmaf-0) for the full example listing.


### 8.3.14. cuda_tile.mmai


*Integer matrix-multiply-accumulate*


```
cuda_tile.mmai %lhs %rhs %acc %signedness_lhs %signedness_rhs
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i8](types.html#subsection-element-types)>) - The left hand side matrix operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i8](types.html#subsection-element-types)>) - The right hand side matrix operand. 13.1
 - acc ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The accumulator matrix operand. 13.1
 - signedness_lhs ([Signedness](operations.html#op-attribute-cuda-tile-mmai-signedness-attr)) - The signedness of the `lhs` operand. 13.1
 - signedness_rhs ([Signedness](operations.html#op-attribute-cuda-tile-mmai-signedness-attr)) - The signedness of the `rhs` operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>) - The result matrix after multiplication and accumulation. 13.1


#### Description


The `mmai` operation implements an MMA (matrix-multiply-accumulate) operation for integer tiles. It performs matrix multiplication on the integer tiles `lhs` and `rhs`, then adds the tile `acc` to the result. `lhs`, `rhs`, and `acc` must be 2D tiles or 3D tiles. The latter case indicates a batched matrix multiplication.

  \[\text{mmai}(A, B, C)_{ij} = \sum_{k=0}^{K-1} A_{ik} \times B_{kj} + C_{ij}\]
Input tiles `lhs` and `rhs` must be of integer type `i8`. The signedness of `lhs` and `rhs` are specified separately by the `signedness_lhs` and `signedness_rhs` attributes, respectively. The accumulator tile `acc` must be of type `i32` and is always interpreted as signed. The output tile `result` is of type `i32` and is always interpreted as signed.


Shapes must be a valid matrix multiplication configuration. Unbatched (2D) MMA expects the operands `lhs`, `rhs`, and `acc` to have shapes `M x K`, `K x N`, and `M x N` (respectively). Batched (3D) MMA expects the operands to have shapes `B x M x K`, `B x K x N`, and `B x M x N` (respectively).


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `acc` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i32](types.html#subsection-element-types)>).
 - `lhs` and `rhs` must have the same element type ([tile](types.html#type-tile)<[i8](types.html#subsection-element-types)>).
 - `lhs`, `rhs` and `acc` must have the same rank.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%lhs0 = cuda_tile.constant <i8: 0> : tile<4x8xi8>
%rhs0 = cuda_tile.constant <i8: 0> : tile<8x2xi8>
%acc0 = cuda_tile.constant <i32: 0> : tile<4x2xi32>

%0 = mmai %lhs0, %rhs0, %acc0 signed signed
    : tile<4x8xi8>, tile<8x2xi8>,
      tile<4x2xi32>

%lhs1 = cuda_tile.constant <i8: 0> : tile<2x4x8xi8>
%rhs1 = cuda_tile.constant <i8: 0> : tile<2x8x2xi8>
%acc1 = cuda_tile.constant <i32: 0> : tile<2x4x2xi32>

%1 = mmai %lhs1, %rhs1, %acc1 unsigned unsigned
    : tile<2x4x8xi8>, tile<2x8x2xi8>,
      tile<2x4x2xi32>
```


See [cuda_tile.mmai_0](appendix.html#example-cuda-tile-mmai-0) for the full example listing.


### 8.3.15. cuda_tile.module


*Top-level module containing a series of defined items.*


```
cuda_tile.module %sym_name
```


#### Parameters


 - sym_name ([Symbol](operations.html#type-symbol)) - The name of the module. 13.1


#### Results


No results.


#### Description


A `module` operation represents a single compilation unit and contains zero or more items (global variables, functions, or kernels).


For detailed description of the semantics of modules, and the full definition of each item type see [Modules](semantics.html#sub-sec-modules).


The `module` operation is the top-level operation in a Tile IR module and must contain only Tile IR operations and no other dialects.


#### Constraints


 - The region must not capture SSA values defined above the operation.
 - The operation must provide custom parsing and printing methods.
 - All regions must have zero arguments.
 - Each provided region must contain exactly one block.
 - The operation must define a symbol scope.
 - The region must not require explicit terminator operations.
 - The operation must specify whether regions are SSACFG or Graph kind.
 - The operation must contain only dataflow graph regions.


### 8.3.16. cuda_tile.offset


*Offsets a tile of pointers*


```
cuda_tile.offset %ptr %offset
```


#### Parameters


 - ptr ([ptr](types.html#type-ptr)) - The base pointer tile to advance. 13.1
 - offset ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The offset tile to add to the pointer. 13.1


#### Results


 - result ([ptr](types.html#type-ptr)) - The resulting pointer tile after advancement. 13.1


#### Description


`offset` advances a tile of pointers. It takes `ptr` as base and `offset` as increment, and performs element-wise addition of `ptr` by `offset`:

  \[\text{offset}(\text{ptr}, \text{offset})_i = \text{ptr}_i + \text{offset}_i \times \text{bitwidth}\]
```
result[i,j] = ptr[i,j] + offset[i,j] * bitwidth
```


`ptr` is interpreted as an unsigned integer. `offset` is interpreted as a signed integer. `bitwidth` is the storage bitwidth of the pointee type. The multiplication must not overflow (wrap-around) in a signed sense. The addition must not overflow (wrap-around) in an unsigned sense. In case of an overflow, the result is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - The operation must apply element-wise to its operands.
 - `ptr`, `offset` and `result` must have the same shape.
 - `result` and `ptr` must have the same shape and element type ([ptr](types.html#type-ptr)).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.3.17. cuda_tile.pack


*Pack a tile into a byte array*


```
cuda_tile.pack %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types) | [f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The input tile. 13.2


#### Results


 - result ([tile](types.html#type-tile)<[i8](types.html#subsection-element-types)>) - The packed tile. 13.2


#### Description


The `pack` operation takes a rank-1 numeric tile and produces a rank-1 `tile<i8>`.


Similar to `bitcast`, underlying bit-values are not changed. However, `pack` does not operate elementwise, instead reinterpreting the entire tile as a byte array.


Input and output tiles must be rank-1 to eliminate packing ambiguity. The size of the output tile must match the number of bytes in the input tile.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same rank.


#### Examples


```
%arg0 = constant <f16: 0.0> : tile<64xf16>
%0 = pack %arg0 : tile<64xf16> -> tile<128xi8>
```


See [cuda_tile.pack_0](appendix.html#example-cuda-tile-pack-0) for the full example listing.


```
%arg0 = constant <f4E2M1FN: 0.0> : tile<64xf4E2M1FN>
%0 = pack %arg0 : tile<64xf4E2M1FN> -> tile<32xi8>
```


See [cuda_tile.pack_1](appendix.html#example-cuda-tile-pack-1) for the full example listing.


### 8.3.18. cuda_tile.permute


*Permute tile dimensions*


```
cuda_tile.permute %source %permutation
```


#### Parameters


 - source ([tile](types.html#type-tile)) - The input tile. 13.1
 - permutation ([Array](operations.html#type-array)<[i32](types.html#subsection-element-types)>) - The permutation of the dimensions. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The permuted tile. 13.1


#### Description


Permute the dimensions of the input tile `source` according to the `permutation` array. The `permutation` array is a list of integers that specify the new order of the dimensions.


For example, if the input tile has shape `[2, 4, 8]`, and the permutation is `[2, 0, 1]`, the output tile will have shape `[8, 2, 4]`.


This operation logically is a change in the indexing of the tile.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same element type ([tile](types.html#type-tile)).
 - `source` and `result` must have the same rank.


#### Examples


```
%arg0 = constant <f16: 0.0> : tile<2x4x8xf16>
%0 = permute %arg0 [2, 0, 1] : tile<2x4x8xf16> -> tile<8x2x4xf16>
```


See [cuda_tile.permute_0](appendix.html#example-cuda-tile-permute-0) for the full example listing.


### 8.3.19. cuda_tile.reduce


*Variadic tile reduction across dimensions*


```
cuda_tile.reduce %operands %dim %identities
```


#### Parameters


 - operands ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)>) - The set of tiles to reduce. 13.1
 - dim ([i32](types.html#subsection-element-types)) - The index of the dimension to perform reduction on. 13.1
 - identities ([Array](operations.html#type-array)) - The reduction identities for each operand. 13.1


#### Results


 - results ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)>) - The set of reduced tiles. 13.1


#### Description


The `reduce` operation applies a custom reduction function along a specified dimension of one or more input tiles, producing the same number of output tiles.


The reduction function must be an associative operation defined within the `reduce` operation’s region. A single reduction operation can reduce over any number of input tiles in parallel, producing a reduced output tile for each.


All input tiles must have the same shape. The output tiles will have a matching shape in every dimension except the one being reduced, which is removed.


For each input tile, a constant identity value must be provided that matches the element type of the input tile. Identity `i` of `identities` corresponds to input tile `i` of `operands`. The correct identity value is a property of the reduction function in the `body`. (For example, if the reduction function performs `min`, the identity is `+inf`, while if the reduction function performs a `sum`, the identity is `0`.)


The reduction function must expect `2N` arguments, where `N` is the number of input tiles. Each pair of reduction arguments `2i` and `2i+1` will correspond to the `i`-th input tile. The first argument of each pair is an element of the input tile; the second is the accumulator from all prior reductions along the specified dimension. This second value might be input element, the identity value, or the result of a previous reduction iteration. The reduction function should yield the new accumulator value for each input tile.


Note


There are no guarantees on the order of element reduction along the specified dimension. However, the result is deterministic across different runs of the same kernel on the same device.


#### Constraints


 - The operation must provide custom parsing and printing methods.
 - The operation only has an effect if and only if it the region’s operation have an effect.
 - All operands must have identical shapes.
 - Each provided region must contain exactly one block.


#### Examples


```
%input = constant <f32: 0.0> : tile<8xf32>
%0 = reduce %input dim=0 identities=[0.000000e+0 : f32] : tile<8xf32> -> tile<f32>
  (%input_arg: tile<2xf32>, %input_accum: tile<f32>) {
    %add_result = addf %input_arg, %input_accum : tile<f32>
    yield %add_result : tile<f32>
  }
```


See [cuda_tile.reduce_0](appendix.html#example-cuda-tile-reduce-0) for the full example listing.


```
%input = constant <f32: 0.0> : tile<8x64xf32>
%0 = reduce %input dim=0 identities=[0.000000e+0 : f32] : tile<8x64xf32> -> tile<8xf32>
  (%input_arg: tile<f32>, %input_accum: tile<f32>) {
    %add_result = addf %input_arg, %input_accum : tile<f32>
    yield %add_result : tile<f32>
  }
```


See [cuda_tile.reduce_1](appendix.html#example-cuda-tile-reduce-1) for the full example listing.


### 8.3.20. cuda_tile.reshape


*Reshape tile dimensions*


```
cuda_tile.reshape %source
```


#### Parameters


 - source ([tile](types.html#type-tile)) - The source tile to reshape. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The reshaped tile. 13.1


#### Description


The `reshape` operation changes the shape of the `source` operand. `reshape` is only a change in the indexing of the tile. The number of elements and element type must remain unchanged.


0-d tiles (i.e., scalars) contain precisely one element and thus are the one exception where a 0-d tile can be reshaped to shape where the `size(shape) == 1`.


Conceptually reshaping a tile is equivalent to first creating a 1-d tile from the data of the source assuming a row-major layout and then converting the 1-d tile into the new shape in a row-major layout.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same element type (tile).


#### Examples


```
%cst = constant <i8: 0> : tile<i8>
%0 = reshape %cst
    : tile<i8> -> tile<1x1x1xi8>

%t = constant <f32: 0.0> : tile<8x2xf32>
%1 = reshape %t
    : tile<8x2xf32> -> tile<2x2x4x1xf32>
```


See [cuda_tile.reshape_0](appendix.html#example-cuda-tile-reshape-0) for the full example listing.


```
%cst = constant <i32: [[0, 1, 2, 3], [4, 5, 6, 7]]>
      : tile<2x4xi32>
  %r0 = reshape %cst
: tile<2x4xi32> -> tile<2x2x2xi32>

// Step 1: Turn source into 1D tile. Use row-major by convention.
// %tmp: [0, 1, 2, 3, 4, 5, 6, 7]
%tmp = reshape %cst
    : tile<2x4xi32> -> tile<8xi32>

// Step 2: Turn 1D tile into result tile. Use row-major by convention.
// %r: [[[0, 1], [2, 3]], [[4, 5], [6, 7]]]
%r1 =  reshape %tmp
        : tile<8xi32> -> tile<2x2x2xi32>
```


See [cuda_tile.reshape_1](appendix.html#example-cuda-tile-reshape-1) for the full example listing.


### 8.3.21. cuda_tile.scan


*A parallel prefix sum operation*


```
cuda_tile.scan %operands %dim %reverse %identities
```


#### Parameters


 - operands ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)>) - The a set of tiles to scan. 13.1
 - dim ([i32](types.html#subsection-element-types)) - The index of the dimension along which to scan. 13.1
 - reverse ([bool](operations.html#type-bool)) - Whether to scan in reverse order. 13.1
 - identities ([Array](operations.html#type-array)) - The identities of the scan operation. 13.1


#### Results


 - results ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)>) - The resulting tiles from the scan operation. 13.1


#### Description


The `scan` operation computes an inclusive parallel prefix along a given dimension of the input tiles using a binary associative function and an identity.


The `scan` operation applies a scan function defined over a tile of elements for a given type, utilizing an associative operation and an identity value. It operates on `operands` and `identities` across the specified `dim`, producing new `results` tile values. The exact evaluation order within each prefix is implementation-defined but the result remains deterministic across different runs of the same kernel on the same device.

  \[\text{scan}(X, \text{dim}, \text{identity}, f)_{i_1,\ldots,i_d}[j] \;=\; \text{fold}\!\left(f, \text{identity}, \left(X_{i_1,\ldots,i_{\text{dim}-1}, 0, i_{\text{dim}+1},\ldots,i_d}, \ldots, X_{i_1,\ldots,i_{\text{dim}-1}, j, i_{\text{dim}+1},\ldots,i_d}\right)\right)\]
The scan preserves all intermediate accumulator values:

  \[\begin{split}\text{result}[0] \;=\; f(\text{identity}, X[\ldots, 0, \ldots]) \\ \text{result}[1] \;=\; f(\text{result}[0], X[\ldots, 1, \ldots]) \\ \vdots \\ \text{result}[j] \;=\; f(\text{result}[j-1], X[\ldots, j, \ldots])\end{split}\]
When `reverse` is `true`, the prefix is taken in decreasing index order. Let \(N\) be the size of the scanned dimension; then:

  \[\text{scan}_{\text{rev}}(X)[j] \;=\;\ \text{fold}\!\left(f, \text{identity}, \left(X[\ldots, N\!-\!1,\ldots], \ldots, X[\ldots, j,\ldots]\right)\right)\]
The `identities` attribute is a list of identity elements for each input tile; the identity at position `i` binds with the operand tile at the same position. The correct identity is a property of the scan function in the `body` (e.g., `sum` uses 0, `prod` uses 1, `min` uses +inf, `max` uses -inf).


The `body` region represents the binary associative operation. The region must contain Tile IR operations with 0-rank tile types. Region arguments are bound in operand order as `[op_0_current_iter, op_0_prev_iter, op_1_current_iter, op_1_prev_iter, ...]`, where `op_i_current_iter` is the current element along `dim` and `op_i_prev_iter` is the running accumulator for operand `i`. On the first step, the accumulator is the corresponding identity element.


Note


Associativity of the binary operation permits the compiler to reorganize the applications of the operation to achieve efficient parallel prefix scans on the GPU.


Warning


The scan operation is restricted to only support single tile input.


#### Constraints


 - The operation must provide custom parsing and printing methods.
 - The operation only has an effect if and only if it the region’s operation have an effect.
 - All operands must have identical shapes.
 - Each provided region must contain exactly one block.


#### Examples


```
%input = constant <f32: 0.0> : tile<8x16xf32>
%result = scan %input dim=1 reverse=false identities=[1.0 : f32] : tile<8x16xf32> -> tile<8x16xf32>
(%acc: tile<f32>, %elem: tile<f32>) {
  %prod = mulf %acc, %elem rounding<nearest_even>: tile<f32>
  yield %prod : tile<f32>
}
```


See [cuda_tile.scan_0](appendix.html#example-cuda-tile-scan-0) for the full example listing.


### 8.3.22. cuda_tile.select


*Select values based on condition*


```
cuda_tile.select %cond %val_if_true %val_if_false
```


#### Parameters


 - cond ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The condition tile. 13.1
 - val_if_true ([tile](types.html#type-tile)) - The value if true tile. 13.1
 - val_if_false ([tile](types.html#type-tile)) - The value if false tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The tile of selected values. 13.1


#### Description


The `select` op chooses values based on the binary conditions supplied as the `cond` operand. The `val_if_true` operand contains the value(s) to use if the condition is 1. The `val_if_false` operand contains the value(s) to use if the condition is 0. The choice is made element-wise according to the values in the condition tile.

  \[\begin{split}\text{select}(\text{cond}, x, y)_i = \begin{cases} x_i & \text{if } \text{cond}_i = 1 \\ y_i & \text{if } \text{cond}_i = 0 \end{cases}\end{split}\]
All tiles must have the same shape. The tiles `val_if_true`, `val_if_false`, and the result must have the same element type. The `cond` tile must be a tile of `i1` values.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `val_if_true`, `val_if_false` and `result` must have the same shape and element type ([tile](types.html#type-tile)).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.3.23. cuda_tile.unpack


*Unpack a byte array into a tile*


```
cuda_tile.unpack %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[i8](types.html#subsection-element-types)>) - The input i8 tile. 13.2


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types) | [f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The output unpacked tile. 13.2


#### Description


The `unpack` operation takes a rank-1 `tile<i8>` and produces a rank-1 numeric tile.


Similar to `bitcast`, underlying bit-values are not changed. However, `unpack` does not operate elementwise, instead reinterpreting the entire tile as a numeric tile of different element type.


Input and output tiles must be rank-1 to eliminate unpacking ambiguity. The size of the input tile must match the number of bytes in the output tile.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same rank.


#### Examples


```
%arg0 = constant <i8: 0> : tile<64xi8>
%0 = unpack %arg0 : tile<64xi8> -> tile<32xf16>
```


See [cuda_tile.unpack_0](appendix.html#example-cuda-tile-unpack-0) for the full example listing.


```
%arg0 = constant <i8: 0> : tile<64xi8>
%0 = unpack %arg0 : tile<64xi8> -> tile<128xF4E2M1FN>
```


See [cuda_tile.unpack_1](appendix.html#example-cuda-tile-unpack-1) for the full example listing.


## 8.4. Conversions


There are no implicit type conversions in Tile IR thus we expose a set of explicit conversion operations for interconverting between types which have compatible representations or rules for conversion.


[cuda_tile.bitcast](operations.html#op-cuda-tile-bitcast) preserves the contents of the input but allows for changing of element types, [cuda_tile.exti](operations.html#op-cuda-tile-exti) and [cuda_tile.trunci](operations.html#op-cuda-tile-trunci) change the width of integer tiles, [cuda_tile.ftoi](operations.html#op-cuda-tile-ftoi) and [cuda_tile.itof](operations.html#op-cuda-tile-itof) convert floating-point tiles to integer tiles and vice versa, and [cuda_tile.ftof](operations.html#op-cuda-tile-ftof) converts between different floating-point types.


For more details on conversions and their rules see the individual operation’s documentation.


### 8.4.1. cuda_tile.bitcast


*Bitcast a tile from one element type to another*


```
cuda_tile.bitcast %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types) | [f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The source tile to cast. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types) | [f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The casted tile. 13.1


#### Description


The `bitcast` operation casts the input tile from one element type to another without modifying the underlying bits.


Only non-pointer types of the same bit width are allowed (e.g., `i32` to `f32`). Pointer types must use [cuda_tile.ptr_to_int](operations.html#op-cuda-tile-ptr-to-int) or [cuda_tile.int_to_ptr](operations.html#op-cuda-tile-int-to-ptr) instead.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.2. cuda_tile.exti


*Extend the width of an integer tile*


```
cuda_tile.exti %from %signedness
```


#### Parameters


 - from ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The input integer tile to extend. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-exti-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1


#### Results


 - to ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The extended integer tile. 13.1


#### Description


The `exti` operation converts a tile of integers of a given width to a strictly larger width. Zero-extension is used for `unsigned` integers and sign-extension is used for `signed` integers.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.3. cuda_tile.ftof


*Convert between floating-point types*


```
cuda_tile.ftof %from %rounding_mode
```


#### Parameters


 - from ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The input floating-point tile. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-ftof-roundingmode-attr)) - The rounding mode for the operation. 13.1


#### Results


 - to ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The result floating-point tile. 13.1


#### Description


The `ftof` operation converts a tile of a given floating-point element type into one of a different floating-point element type (for example, from `f32` to `f64`).


The source type and the result type must be different.


The `rounding_mode` attribute specifies the rounding behavior for the operation. Only `NEAREST_EVEN` rounding mode is supported.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.4. cuda_tile.ftoi


*Convert a tile from floating-point values to integer values*


```
cuda_tile.ftoi %from %signedness %rounding_mode
```


#### Parameters


 - from ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The input floating-point tile. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-ftoi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-ftoi-roundingmode-attr)) - The rounding mode for the operation. 13.1


#### Results


 - to ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result integer tile. 13.1


#### Description


The `ftoi` operation converts a floating-point tile into an integer tile.


In contrast to a [cuda_tile.bitcast](operations.html#op-cuda-tile-bitcast) which is bits preserving, this preserves the numerical value of the tile, rounded towards zero to the nearest integer of the provided type.


The `rounding_mode` attribute specifies the rounding behavior for the operation. Only `NEAREST_INT_TO_ZERO` rounding mode is supported.


Warning


If the input floating-point value, after being rounded, is outside the (signed or unsigned) range of the target integer type, the closest representable value is used instead. `NaN` values are converted to 0. Input `Inf` values are undefined behavior.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.5. cuda_tile.itof


*Convert integer to floating-point*


```
cuda_tile.itof %from %signedness %rounding_mode
```


#### Parameters


 - from ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The input integer tile. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-itof-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-itof-roundingmode-attr)) - The rounding mode for the operation. 13.1


#### Results


 - to ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The converted floating-point tile. 13.1


#### Description


The `itof` operation converts an integer tile into a float tile. In contrast to [cuda_tile.bitcast](operations.html#op-cuda-tile-bitcast), this preserves the numerical value of the tile, rounded to the nearest floating-point number of the provided type.


Warning


If the input integer value, after being rounded, is outside the range of the target floating-point type, it is converted to `Inf` for types that support that value, and `NaN` otherwise.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.6. cuda_tile.int_to_ptr


*Convert a tile of integers to a tile of pointers*


```
cuda_tile.int_to_ptr %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[i64](types.html#subsection-element-types)>) - The input tile of integers. 13.1


#### Results


 - result ([ptr](types.html#type-ptr)) - The output tile of pointers. 13.1


#### Description


The `int_to_ptr` operation converts a tile of integers to a tile of pointers.


The `source` operand is interpreted as an unsigned integer.


The inverse of this operation is [cuda_tile.ptr_to_int](operations.html#op-cuda-tile-ptr-to-int).


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.7. cuda_tile.ptr_to_int


*Convert a tile of pointers to a tile of integers*


```
cuda_tile.ptr_to_int %source
```


#### Parameters


 - source ([ptr](types.html#type-ptr)) - The input tile of pointers. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i64](types.html#subsection-element-types)>) - The output tile of integers. 13.1


#### Description


The `ptr_to_int` operation converts a tile of pointer-type elements to a tile of `i64` elements.


The result values should be interpreted as unsigned integers.


The inverse of this operation is [cuda_tile.int_to_ptr](operations.html#op-cuda-tile-int-to-ptr).


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.8. cuda_tile.ptr_to_ptr


*Reinterpret a tile of one pointer type as another*


```
cuda_tile.ptr_to_ptr %source
```


#### Parameters


 - source ([ptr](types.html#type-ptr)) - Tile with source pointer element type. 13.1


#### Results


 - result ([ptr](types.html#type-ptr)) - Tile with target pointer element type. 13.1


#### Description


The `ptr_to_ptr` operation casts a tile of pointers from a pointer of one element type to another element. Casts between pointer and non-pointer types are disallowed.


In order to perform those conversions, use [cuda_tile.ptr_to_int](operations.html#op-cuda-tile-ptr-to-int) or [cuda_tile.int_to_ptr](operations.html#op-cuda-tile-int-to-ptr). These operations are distinct to enable future compiler reasoning about pointer provenance.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


### 8.4.9. cuda_tile.trunci


*Truncates the width of an integer tile*


```
cuda_tile.trunci %from %overflow
```


#### Parameters


 - from ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The input integer tile to truncate. 13.1
 - overflow ([IntegerOverflow](operations.html#op-attribute-cuda-tile-trunci-integeroverflow-attr)) - The overflow behavior of the operation. 13.1


#### Results


 - to ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The truncated integer tile. 13.1


#### Description


The `trunci` operation converts a tile of integers of a given element type to one with a strictly smaller width.


The optional overflow attribute specifies whether an overflow can occur when interpreting the operand as a signed and/or unsigned integer. In case of “no signed wrap”, all truncated bits must have the same value as the most significant bit of the truncated result. In case of “no unsigned wrap”, the truncated bits must be zero.


The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.


These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


 - `none` - The compiler makes no assumptions regarding overflow behavior.
 - `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
 - `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
 - `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.


If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


## 8.5. Control Flow


Tile IR contains a standard set of control flow operations that enable conditionals, and loops.


The operations are designed in the style of the [MLIR Control Flow dialect](https://mlir.llvm.org/docs/Dialects/ControlFlow/).


A notable difference is that we allow the nesting of control flow operations for example a [cuda_tile.if](operations.html#op-cuda-tile-if) may appear inside a [cuda_tile.loop](operations.html#op-cuda-tile-loop) or [cuda_tile.for](operations.html#op-cuda-tile-for).


The main control structures are:


 - [cuda_tile.if](operations.html#op-cuda-tile-if) which implements conditional branching.
 - [cuda_tile.loop](operations.html#op-cuda-tile-loop) which implements a loop with arbitrary exit conditions.
 - [cuda_tile.for](operations.html#op-cuda-tile-for) which implements a range-based loop with a fixed number of iterations.


These operations and their supporting operations are described in the following section.


### 8.5.1. cuda_tile.assert


*Terminate kernel execution with an error message if condition is false-y*


```
cuda_tile.assert %condition %message
```


#### Parameters


 - condition ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The condition tile to check. 13.1
 - message ([String](operations.html#type-string)) - The error message to display if assertion fails. 13.1


#### Results


No results.


#### Description


The `assert` operation takes as `condition` a tile of `i1` values. For each value that is `0`, it prints the given error message, along with the index of the value within the tile.


If at least one value is `0`, an error is signalled to the host side. The kernel, including the tile block that failed the assertion, may keep running.


Assertions are for debugging purposes. They can affect performance and it is therefore recommended to remove them in production code.


#### Constraints


No constraints.


#### Examples


```
assert %arg0, "assertion failed" : tile<i1>
```


See [cuda_tile.assert_0](appendix.html#example-cuda-tile-assert-0) for the full example listing.


### 8.5.2. cuda_tile.break


*Break from loop*


```
cuda_tile.break %operands
```


#### Parameters


 - operands ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The operands to yield to the parent loop upon termination. 13.1


#### Results


No results.


#### Description


The `break` operation is a terminator operation of a [cuda_tile.loop](operations.html#op-cuda-tile-loop).


It may yield any number of `$operands` to the parent loop upon termination. The number of values yielded and the execution semantics of how they are yielded are determined by the parent loop.


The `break` operation always returns control to the innermost enclosing loop operation, even when it is nested within other control constructs such as `if` or additional loops.


#### Constraints


 - The operation must terminate its parent basic block.


#### Examples


```
// Break from the body of a loop.
loop {
    break
}

// Break from an if nested within the loop.
loop  {
    %condition = constant <i1: 1> : tile<i1>
    if %condition  {
        break
    }
    // ...
}

%initValue0 = constant <f32: 0.0> : tile<f32>
// Break from an if nested within the loop, while yielding values.
%results = loop iter_values(%var0 = %initValue0): tile<f32> -> tile<f32> {
    %condition = constant <i1: 1> : tile<i1>
    if %condition  {
        // ...
        yield
    } else {
        // %if.loopValue0 = ...
        %loopValue0 = constant <f32: 1.0> : tile<f32>
        break %loopValue0 : tile<f32>
    }
    %loopValue1 = constant <f32: 1.0> : tile<f32>
    continue %loopValue1 : tile<f32>
}
```


See [cuda_tile.break_0](appendix.html#example-cuda-tile-break-0) for the full example listing.


### 8.5.3. cuda_tile.continue


*Continue to next loop iteration*


```
cuda_tile.continue %operands
```


#### Parameters


 - operands ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The values to yield to the parent loop. 13.1


#### Results


No results.


#### Description


The `continue` operation represents a block terminator that returns control to a loop operation, such as [cuda_tile.for](operations.html#op-cuda-tile-for) and [cuda_tile.loop](operations.html#op-cuda-tile-loop). The operation may yield any number of `$operands` to the parent loop upon termination.


The requirements and semantics of the `continue` operation are defined by the parent loop operation, see the loop operation’s description for particular semantics.


The `continue` operation always returns control to the innermost enclosing loop operation, even when it is nested within other control constructs such as `if` or additional loops.


#### Constraints


 - The operation must terminate its parent basic block.


#### Examples


```
%lowerBound = constant <i32: 0> : tile<i32>
  %upperBound = constant <i32: 10> : tile<i32>
  %step = constant <i32: 1> : tile<i32>
  %condition = constant <i1: 1> : tile<i1>
  // Continue from the body of a loop.
  for %iv in (%lowerBound to %upperBound, step %step) : tile<i32> {
      continue
  }

  // Continue from an if nested within the loop.
  for %iv in (%lowerBound to %upperBound, step %step) : tile<i32> {
      if %condition  {
          continue
      }
      // ...
  }

// Continue from an if nested within the loop, while yielding values.
%initVar0 = constant <f32: 0.0> : tile<f32>
%results = for %iv in (%lowerBound to %upperBound, step %step) : tile<i32>
          iter_values(%var0 = %initVar0) -> (tile<f32>)
  {
      if %condition {
          // ...
          yield
      } else {
          %loopValue0 = constant <f32: 1.0> : tile<f32>
          continue %loopValue0 : tile<f32>
      }
      %loopValue1 = constant <f32: 1.0> : tile<f32>
      continue %loopValue1 : tile<f32>
  }
```


See [cuda_tile.continue_0](appendix.html#example-cuda-tile-continue-0) for the full example listing.


### 8.5.4. cuda_tile.for


*For loop over integer range*


```
cuda_tile.for %lowerBound %upperBound %step %initValues %unsignedCmp
```


#### Parameters


 - lowerBound ([tile](types.html#type-tile)<[any](operations.html#type-any)>) - The lower bound of the loop. 13.1
 - upperBound ([tile](types.html#type-tile)<[any](operations.html#type-any)>) - The upper bound of the loop. 13.1
 - step ([tile](types.html#type-tile)<[any](operations.html#type-any)>) - The step of the loop. 13.1
 - initValues ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The initial values of the loop-carried values. 13.1
 - unsignedCmp ([Flag](operations.html#type-flag)) - If present, use unsigned integer comparison for loop termination. 13.2


#### Results


 - resultValues ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The values of the loop-carried variables after loop termination. 13.1


#### Description


The `for` operation is a structured range-based sequential loop.


The loop operation consists of (1) a range formed by `lowerBound`, `upperBound`, and `step`, (2) a set of loop-carried values which are initialized by `initValues` and updated by each iteration of the loop, and (3) a region which represents the loop body.


The iteration space is defined by the interval \([lowerBound, upperBound)\) with each value separated by `step`.

  \[range(L_b, U_b, S) = \{ L_b + i \cdot S \mid i \in \mathbb{Z}, L_b + i \cdot S < U_b \}\]
`lowerBound`, `upperBound`, and `step` must be of the same type. `lowerBound` and `upperBound` specify a half-open (or exclusive) range: the range includes the `lowerBound` but does not include the `upperBound`. `step` must be positive but the bounds may be negative or zero.


The `lowerBound`, `upperBound`, and `step` operands are interpreted as signed integers.


The first iteration of the loop receives the induction variable initialized to the value of `lowerBound` and the loop-carried values initialized to the values of `initValues`.


The loop body is executed for each value in the range, receiving an integer induction variable incremented by `step` on each iteration and the loop-carried values which correspond to the loop-carried values yielded by the previous loop iteration.


The loop terminates when the induction variable is greater than or equal to `upperBound`. By default, signed comparison is used between the upperBound and the induction variable. To use unsigned comparison instead, specify the optional `unsigned` unit attribute.


The body of the loop must be terminated by a [cuda_tile.continue](operations.html#op-cuda-tile-continue) that yields the next iteration’s value for each loop carried variable.


The for operation produces one return value for each loop carried variable. The type of the \(i\)-th return value is that of the \(i\)-th loop carried variable and its value is the final value of the \(i\)-th loop carried variable.


Warning


 - Loop carried variables can not be a [tensor_view](types.html#type-tensor-view) or view type.
 - `for` operations cannot terminate early and must end in a [cuda_tile.continue](operations.html#op-cuda-tile-continue).


#### Constraints


 - The operation must define scope when stack allocations are freed automatically.
 - `lowerBound`, `upperBound` and `step` must have the same shape and element type ([tile](types.html#type-tile)<[any](operations.html#type-any)>).
 - `initValues` and `resultValues` must have the same shape and element type ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>).
 - The operation must provide custom parsing and printing methods.
 - The operation only has an effect if and only if it the region’s operation have an effect.
 - Each provided region must contain exactly one block.


#### Examples


```
%lowerBound = constant <i32: 0> : tile<i32>
%upperBound = constant <i32: 10> : tile<i32>
%step = constant <i32: 1> : tile<i32>

// A simple loop iterating over an i32 range.
for %iv in (%lowerBound to %upperBound, step %step) : tile<i32> {
    continue
}

%initVal0 = constant <f32: 0.0> : tile<f32>
// A similar loop to the above, but with a loop carried value, val0.
%results = for %iv in (%lowerBound to %upperBound, step %step) : tile<i32>
                    iter_values(%val00 = %initVal0) -> (tile<f32>) {
  %loopVal0 = constant <f32: 1.0> : tile<f32>
  continue %loopVal0 : tile<f32>
}
```


See [cuda_tile.for_0](appendix.html#example-cuda-tile-for-0) for the full example listing.


### 8.5.5. cuda_tile.if


*Conditional execution*


```
cuda_tile.if %condition
```


#### Parameters


 - condition ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The condition of the if operation. 13.1


#### Results


 - results ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The results of the if operation. 13.1


#### Description


The `if` operation represents an if-then-else construct.


The if operation consists of (1) a control operand which is a `tile<i1>` value, (2) a true branch `thenRegion` and (3) an optional false branch `elseRegion`.


The `if` operation may produce results by yielding values in each branch using [cuda_tile.yield](operations.html#op-cuda-tile-yield).


If yielding value(s) the types of yielded values must match and the result result type of the `if` operation will be the same as the yielded values.


If yielding values the else branch is required and must also yield a value.


The values returned will be dependent on which branch is taken.


Warning


The `if` operation has a set of additional restrictions today:


 - Results of `if` must not be a [tensor_view](types.html#type-tensor-view) or view type.


#### Constraints


 - All regions must have zero arguments.
 - The operation must provide custom parsing and printing methods.
 - The operation only has an effect if and only if it the region’s operation have an effect.
 - Each provided region must contain exactly one block.


#### Examples


```
%condition = constant <i1: 1> : tile<i1>

// A simple if operation that conditionally executes a region.
if %condition  {
  // ...
}

// An if operation with an "else" branch.
if %condition  {
  // ...
} else {
  // ...
}

// An if operation that returns mixed types (f32,i32)
%x, %y = if %condition -> (tile<f32>, tile<i32>) {
  %x_then = constant <f32: 1.0> : tile<f32>
  %y_then = constant <i32: 2> : tile<i32>
  yield %x_then, %y_then : tile<f32>, tile<i32>
} else {
  %x_then = constant <f32: 1.0> : tile<f32>
  %y_then = constant <i32: 42> : tile<i32>
  yield %x_then, %y_then : tile<f32>, tile<i32>
}
```


See [cuda_tile.if_0](appendix.html#example-cuda-tile-if-0) for the full example listing.


### 8.5.6. cuda_tile.loop


*Loop until a break operation*


```
cuda_tile.loop %initValues
```


#### Parameters


 - initValues ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The initial values of the loop. 13.1


#### Results


 - resultValues ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The result values of the loop. 13.1


#### Description


The `loop` operation represents an, unstructured, infinite loop that executes until a [cuda_tile.break](operations.html#op-cuda-tile-break) is reached.


The loop consists of a (1) a set of loop-carried values which are initialized by `initValues` and updated by each iteration of the loop, and (2) a region which represents the loop body.


The loop will execute the body of the loop until a [cuda_tile.break](operations.html#op-cuda-tile-break) is dynamically executed.


Each control path of the loop must be terminated by:


 - a [cuda_tile.continue](operations.html#op-cuda-tile-continue) that yields the next iteration’s value for each loop carried variable.
 - a [cuda_tile.break](operations.html#op-cuda-tile-break) that terminates the loop and yields the final loop carried values.


As long as each loop iteration is terminated by one of these operations they may be combined with other control flow operations to express different control flow patterns.


The loop operation produces one return value for each loop carried variable. The type of the \(i\)th return value is that of the \(i\)th loop carried variable and its value is the final value of the \(i\)th loop carried variable.


Warning


Loop operations have a set of additional restrictions today:


 - Early returns from inside loops are not supported, a code generator must first terminate the loop and then return if they wish to end the function execution entirely.
 - Loop carried variables can not be a [tensor_view](types.html#type-tensor-view) or view type.


#### Constraints


 - The operation must define scope when stack allocations are freed automatically.
 - The operation must provide custom parsing and printing methods.
 - The operation only has an effect if and only if it the region’s operation have an effect.
 - Each provided region must contain exactly one block.


#### Examples


```
// A simple "while-do" loop.
loop {
    %cond = constant <i1: 1> : tile<i1>
    if %cond {
        continue
    }
    break
}
```


See [cuda_tile.loop_0](appendix.html#example-cuda-tile-loop-0) for the full example listing.


```
// A simple "do-while" loop.
loop {
    //... body of the loop.

    %cond = constant <i1: 1> : tile<i1>
    if %cond {
        continue
    }
    break
}
```


See [cuda_tile.loop_1](appendix.html#example-cuda-tile-loop-1) for the full example listing.


```
%initValue0 = constant <f32: 0.0> : tile<f32>
// A loop that yields carried-iteration values, returning the final values.
%results = loop iter_values(%value0 = %initValue0) : tile<f32> -> tile<f32> {
    %cond = constant <i1: 1> : tile<i1>
    if %cond {
        %loopValue0 = constant <f32: 0.0> : tile<f32>
        continue %loopValue0 : tile<f32>
    }
    break %value0 : tile<f32>
}
```


See [cuda_tile.loop_2](appendix.html#example-cuda-tile-loop-2) for the full example listing.


```
%initValue0 = constant <i32: 0> : tile<i32>
// A loop that uses loop-carried values and returns a different type.
%results = loop iter_values(%value0 = %initValue0) : tile<i32> -> tile<f32> {
    %cond = constant <i1: 1> : tile<i1>

    if %cond {
        %newLoopValue = constant <i32: 0> : tile<i32>
        continue %newLoopValue : tile<i32>
    }

    %finalReturnValue = constant <f32: 0.0> : tile<f32>
    break %finalReturnValue : tile<f32>
}
```


See [cuda_tile.loop_3](appendix.html#example-cuda-tile-loop-3) for the full example listing.


### 8.5.7. cuda_tile.return


*Return value(s) from a function*


```
cuda_tile.return %operands
```


#### Parameters


 - operands ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The values to return. 13.1


#### Results


No results.


#### Description


The `return` operation returns control to the caller of a function.


Warning


Currently `return` implements restricted return semantics, notably:


 - [cuda_tile.entry](operations.html#op-cuda-tile-entry) operations do not produce return value(s) and thus `return` may be used to terminate the execution of the kernel by invoking the operation with no operands
 - `return` can not be directly used inside of loop bodies to terminate the the execution of the kernel


#### Constraints


 - The operation must terminate its parent basic block.


#### Examples


```
experimental$func @foo() -> (tile<i32>, tile<f16>) {
  %0 = constant <i32: 0> : tile<i32>
  %1 = constant <f16: 0.0> : tile<f16>
  // ...
  return %0, %1 : tile<i32>, tile<f16>
}
```


See [cuda_tile.return_0](appendix.html#example-cuda-tile-return-0) for the full example listing.


```
entry @foo() {
  %0 = constant <i32: 0> : tile<i32>
  %1 = constant <f16: 0.0> : tile<f16>
  // ...
  return
}
```


See [cuda_tile.return_1](appendix.html#example-cuda-tile-return-1) for the full example listing.


### 8.5.8. cuda_tile.yield


*Yield a value from the block*


```
cuda_tile.yield %operands
```


#### Parameters


 - operands ([Variadic](operations.html#type-variadic)<[Any](operations.html#type-any)>) - The operands to yield to the parent operation. 13.1


#### Results


No results.


#### Description


The `yield` operation terminates a block that must yield control back to the parent operation such as `if`, `scan`, `reduce`.


The operation may yield any number of `$operands` to the parent upon termination. The number of values yielded and the execution semantics of how they are yielded are determined by the parent operation.


Note


Unlike standard MLIR control flow dialects `yield` is not used for loop control flow, see [cuda_tile.break](operations.html#op-cuda-tile-break) and [cuda_tile.continue](operations.html#op-cuda-tile-continue) for loop control flow.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - The operation must terminate its parent basic block.


#### Examples


```
%condition = constant <i1: true> : tile<i1>
// Yield from the body of an if conditional.
if %condition  {
    yield
}

// Yield values from within an if conditional.
%x, %y = if %condition -> (tile<f32>, tile<f32>) {
    %x_then = constant <f32: 0.0> : tile<f32>
    %y_then = constant <f32: 1.0> : tile<f32>
    yield %x_then, %y_then : tile<f32>, tile<f32>
} else {
    %x_else = constant <f32: 2.0> : tile<f32>
    %y_else = constant <f32: 3.0> : tile<f32>
    yield %x_else, %y_else : tile<f32>, tile<f32>
}
```


See [cuda_tile.yield_0](appendix.html#example-cuda-tile-yield-0) for the full example listing.


## 8.6. Memory


Tile IR contains a set of memory operations which enable loading, storing, and manipulating memory.


There are a few families of memory operations in Tile IR:


 - Tile of pointer based memory operations such as [cuda_tile.load_ptr_tko](operations.html#op-cuda-tile-load-ptr-tko) and [cuda_tile.store_ptr_tko](operations.html#op-cuda-tile-store-ptr-tko) which load and store tiles from and to global memory.
 - View based memory operations such as [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko) which load and store tiles from and to views.
 - Atomic memory operations such as [cuda_tile.atomic_rmw_tko](operations.html#op-cuda-tile-atomic-rmw-tko) and [cuda_tile.atomic_cas_tko](operations.html#op-cuda-tile-atomic-cas-tko) which perform atomic operations on global memory.


Currently all memory operations are token-ordered; the ordering between any pair of memory operations is undefined unless connected by tokens. For more discussion on token-ordered operations see [Memory Model](memory_model.html#section-memory-model).


Warning


Reading or writing of bound of any allocation is undefined behavior. Examples of out of bounds access are: * Pointer memory operations to tiles containing elements outside the allocation, for example offseting passed the end of the allocation. * Associating an invalid layout with a base pointer, that describes a striding or shape that over runs the allocation and then indexing into the view. * Indexing into a view with indices that are out of bounds.


Note


The rules of what consititues out of bounds is modified when using padded views or masking, see [Type System](types.html#section-types) for more details on specific types.


### 8.6.1. cuda_tile.join_tokens


*Product a new token which depends on the input tokens*


```
cuda_tile.join_tokens %tokens
```


#### Parameters


 - tokens ([Variadic](operations.html#type-variadic)<[token](operations.html#type-token)>) - The input tokens to join. 13.1


#### Results


 - result ([token](operations.html#type-token)) - The joined token. 13.1


#### Description


The `join_tokens` operation produces a fresh token which depends on all input tokens. Token-ordered operations which consume the new token will then be ordered with respect to all joined tokens.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - The operation’s result type may be inferred from its operands and attributes.


### 8.6.2. cuda_tile.load_ptr_tko


*Load and gather data from global memory using a pointer tile without ordering guarantees*


```
cuda_tile.load_ptr_tko %memory_ordering_semantics %memory_scope %source %mask %paddingValue %token %optimization_hints
```


#### Parameters


 - memory_ordering_semantics ([MemoryOrderingSemantics](operations.html#op-attribute-cuda-tile-load-ptr-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the load operation. 13.1
 - memory_scope ([MemoryScope](operations.html#op-attribute-cuda-tile-load-ptr-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
 - source ([ptr](types.html#type-ptr)) - The source tile of pointers. 13.1
 - mask ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The mask for the load operation. 13.1
 - paddingValue ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types) | [f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types) | [fp8e4m3fn](types.html#subsection-element-types) | [fp8e5m2](types.html#subsection-element-types) | [tf32](types.html#subsection-element-types)>) - The padding value for the load operation. 13.1
 - token ([token](operations.html#type-token)) - The token for the load operation. 13.1
 - optimization_hints ([OptimizationHints](operations.html#op-attribute-cuda-tile-load-ptr-tko-optimizationhints-attr)) - Optimization hints for operation 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The result of the load operation. 13.1
 - result_token ([token](operations.html#type-token)) - The result token of the load operation. 13.1


#### Description


This `load` OP performs a gather operation by loading a tile of data from global memory into a result tile based on a tile of pointers provided by the `source` operand.


The `source` operand is a tile of pointers, which specifies the memory locations from which the data is gathered. The operation loads this data and returns it as the `result` tile. When loading i1 values, each value is loaded from a full byte in memory. Any nonzero byte is canonicalized to 0x01, and zero bytes become 0x00.


Optionally, a `mask` operand can be provided to control the gathering of elements. If present, only the elements specified by the `mask` are loaded. The shape of the `mask` must match the shape of the `result`.


When `mask` is present one `paddingValue` can be optionally present as well. The `paddingValue` must have the same shape of the `source` tile. If it is not present, the value of masked elements are undefined.


Token-ordered operations are not constrained by program order. The compiler may reorder them (i.e. place them earlier or later in program order) unless further constrained by tokens.


The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](memory_model.html#section-memory-model) of the specification.


 - `weak` - No concurrent accesses to the source/destination location.
 - `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
 - `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then *happens before* is established.


Note: The following variants are not supported by this operation: `release`, `acq_rel`.


The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.


 - `tl_blk` - There may be concurrent accesses from within the same tile block.
 - `device` - There may be concurrent accesses from within the same device (i.e., GPU).
 - `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).


The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.


The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.


 - `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda_tile.entry](operations.html#op-cuda-tile-entry).
 - `allow_tma` - suggest whether to use TMA for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).
 - `latency` - latency hint for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).


For example they can be annotated as:


```
optimization_hints=<
  sm_100 = {num_cta_in_cga = 8},
  sm_120 = {num_cta_in_cga = 16}
>
```


#### Constraints


 - The operation must encode variadic operand segment sizes in attributes.
 - source type is expected a pointer type of result type
 - shape of ‘mask’ must match the shape of ‘source’
 - type of ‘paddingValue’ must match the type of ‘result’


#### Examples


```
%mask = constant <i1: 1> : tile<i1>
%padding = constant <f32: 0.0> : tile<f32>

  // Load without token.
  %result0, %res_token0 = load_ptr_tko weak %ptr, %mask, %padding
      : tile<ptr<f32>>, tile<i1>, tile<f32> -> tile<f32>, token

  // Load with token.
  %token0 = make_token : token
  %result1, %res_token1 = load_ptr_tko weak %ptr, %mask, %padding token=%token0
      : tile<ptr<f32>>, tile<i1>, tile<f32> -> tile<f32>, token

  return
```


See [cuda_tile.load_ptr_tko_0](appendix.html#example-cuda-tile-load-ptr-tko-0) for the full example listing.


### 8.6.3. cuda_tile.make_token


*Create a fresh token with no prior dependencies*


```
cuda_tile.make_token
```


#### Parameters


No parameters.


#### Results


 - result ([token](operations.html#type-token)) - A fresh token with no prior dependencies. 13.1


#### Description


The `make_token` operation creates a fresh token with no prior dependencies.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - The operation’s result type may be inferred from its operands and attributes.


### 8.6.4. cuda_tile.store_ptr_tko


*Store and scatter data from pointer of tile to global memory without ordering guarantees*


```
cuda_tile.store_ptr_tko %memory_ordering_semantics %memory_scope %destination %value %mask %token %optimization_hints
```


#### Parameters


 - memory_ordering_semantics ([MemoryOrderingSemantics](operations.html#op-attribute-cuda-tile-store-ptr-tko-memoryorderingsemantics-attr)) - The memory ordering semantics. 13.1
 - memory_scope ([MemoryScope](operations.html#op-attribute-cuda-tile-store-ptr-tko-memoryscope-attr)) - The optional memory scope. 13.1
 - destination ([ptr](types.html#type-ptr)) - The destination pointer tile. 13.1
 - value ([tile](types.html#type-tile)) - The value tile to store. 13.1
 - mask ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The optional mask for selective storage. 13.1
 - token ([token](operations.html#type-token)) - The optional token for operation ordering. 13.1
 - optimization_hints ([OptimizationHints](operations.html#op-attribute-cuda-tile-store-ptr-tko-optimizationhints-attr)) - Optimization hints for operation 13.1


#### Results


 - result_token ([token](operations.html#type-token)) - The result token for synchronization. 13.1


#### Description


The `store` operation performs a scatter by storing a tile of data from a tile into global memory.


The `destination` operand is a tile of pointers indicating the global memory locations where data from the `value` tile will be stored. When storing i1 values, each value occupies a full byte in memory. Any nonzero byte is canonicalized to 0x01, and zero bytes become 0x00.


Additionally, the operation supports an optional `mask` operand, which allows selective scattering of elements. If provided, only the elements specified by the `mask` are stored. The shape of the `mask` must align with the shape of the `value` tile.


The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](memory_model.html#section-memory-model) of the specification.


 - `weak` - No concurrent accesses to the source/destination location.
 - `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
 - `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then *happens before* is established.


Note: The following variants are not supported by this operation: `acquire`, `acq_rel`.


The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.


 - `tl_blk` - There may be concurrent accesses from within the same tile block.
 - `device` - There may be concurrent accesses from within the same device (i.e., GPU).
 - `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).


The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.


The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.


 - `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda_tile.entry](operations.html#op-cuda-tile-entry).
 - `allow_tma` - suggest whether to use TMA for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).
 - `latency` - latency hint for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).


For example they can be annotated as:


```
optimization_hints=<
  sm_100 = {num_cta_in_cga = 8},
  sm_120 = {num_cta_in_cga = 16}
>
```


#### Constraints


 - The operation must encode variadic operand segment sizes in attributes.
 - destination type is expected a pointer type of value type
 - shape of ‘destination’ must match the shape of ‘mask’
 - The operation’s result type may be inferred from its operands and attributes.


## 8.7. Floating Point


Tile IR contains a set of typed arithmetic operations which implement familiar arithmetic operations on floating-point types for integer operations see [Integer](operations.html#op-group-integer).


All operations are implemented in a manner that is efficient for the target architecture and device family. In most common cases this means utilizing the underlying hardware’s native floating-point operations. Due to Tile IR’s stability guarantees and higher-level programming model some types on some hardware may be emulated, see [Stability](stability.html#section-stability) for more information about the stability guarantees and information about per device behavior.


### 8.7.1. Floating-Point Arithmetic


Standard floating-point types implement the IEEE-754 standard for floating-point arithmetic. On NVIDIA hardware, certain types are non-standard and *do not* implement the IEEE-754 standard, see [Element Types](types.html#subsection-element-types) for more details about the different floating-point types, their precision, storage, and formats.


Supports 16-bit, 32-bit, and 64-bit floating-point data types.


### 8.7.2. Floating-Point Math


Tile IR contains a set of standard math library operations which implement familiar mathematical functions over tensors supporting 16-bit, 32-bit, and 64-bit floating-point data types.


Note


32-bit and 64-bit operations typically leverage efficient hardware-specific instructions. Some 16-bit operations are emulated using wider intermediate computations, and may not offer the same performance.


Warning


There are some restrictions based on data type support which are detailed in the [Type System](types.html#section-types) section.


### 8.7.3. cuda_tile.absf


*Element-wise floating-point absolute value*


```
cuda_tile.absf %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input float tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The absolute value of the input tile. 13.1


#### Description


The `absf` operation computes the element-wise absolute value of the input float tile.

  \[\text{absf}(x)_i = |x|_i\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.4. cuda_tile.addf


*Element-wise floating-point addition*


```
cuda_tile.addf %lhs %rhs %rounding_mode %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-addf-roundingmode-attr)) - The rounding mode for the operation. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The sum of the input tiles. 13.1


#### Description


The `addf` operation computes the element-wise addition of two tiles with floating-point element type.

  \[\text{addf}(x, y)_i = x_i + y_i\]
The addition of individual elements is performed by the target architecture’s native floating-point addition for the given element type unless otherwise specified.


Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |
| rounding<nearest_even> | yes | yes | yes | yes |
| rounding<zero> | yes | yes | yes* | yes* |
| rounding<negative_inf> | yes | yes | yes* | yes* |
| rounding<positive_inf> | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.5. cuda_tile.atan2


*Element-wise atan2*


```
cuda_tile.atan2 %x %y
```


#### Parameters


 - x ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input x float tile. 13.2
 - y ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input y float tile. 13.2


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The element-wise result tile. 13.2


#### Description


The `atan2` operation calculates the principal value of the arc tangent of the ratio of first and second input arguments x / y. The quadrant of the result is determined by the signs of inputs x and y.

  \[(\operatorname{atan2}(x, y))_i = \mathrm{atan2}(x_i, y_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `x`, `y` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%x = constant <f32: [1.0, -1.0, 0.0, 2.0]> : tile<4xf32>
%y = constant <f32: [1.0,  1.0, 1.0, 0.0]> : tile<4xf32>
%res = atan2 %x, %y : tile<4xf32>
```


See [cuda_tile.atan2_0](appendix.html#example-cuda-tile-atan2-0) for the full example listing.


### 8.7.6. cuda_tile.ceil


*Element-wise ceiling*


```
cuda_tile.ceil %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input float tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The ceiling of the input tile. 13.1


#### Description


The `ceil` operation computes the element-wise ceiling on the input floating-point tile. The ceiling operation rounds each element up to the largest integer value that is greater than or equal to the input value.

  \[\text{ceil}(x)_i = \min\{n \in \mathbb{Z} \mid n \geq x_i\}\]
#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%result = ceil %source : tile<f32>
```


See [cuda_tile.ceil_0](appendix.html#example-cuda-tile-ceil-0) for the full example listing.


### 8.7.7. cuda_tile.cosh


*Element-wise hyperbolic cosine*


```
cuda_tile.cosh %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input floating-point tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The hyperbolic cosine of the input tile. 13.1


#### Description


The `cosh` operation computes the element-wise hyperbolic cosine of the input tile with floating-point element type.

  \[\text{cosh}(x)_i = {\cosh x}_i\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.8. cuda_tile.cos


*Element-wise cosine*


```
cuda_tile.cos %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input float tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The cosine of the input tile. 13.1


#### Description


The `cos` operation computes the element-wise cosine of the input floating-point tile.

  \[\text{cos}(x)_i = \cos(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res = cos %in : tile<4xf32>
```


See [cuda_tile.cos_0](appendix.html#example-cuda-tile-cos-0) for the full example listing.


### 8.7.9. cuda_tile.divf


*Element-wise floating-point division*


```
cuda_tile.divf %lhs %rhs %rounding_mode %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The dividend input floating-point tile. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The divisor input floating-point tile. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-divf-roundingmode-attr)) - The rounding mode for the operation. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the `divf` operation. 13.1


#### Description


The `divf` operation computes the element-wise division of two input tiles with floating-point element types.


The `approx` rounding mode implements a fast approximation of divide, computed as a multiplication by reciprocal. For `|rhs|` in normalized range `[2^(-126), 2^(126)]` the maximum ULP (Unit in the Last Place) error is `2`. For `2^(126) < |rhs| < 2^(128)`, if `lhs` is infinity the operation returns `NaN`, otherwise `0`.


The `full` rounding mode implements a relatively fast, full-range approximation that scales operands to achieve better accuracy, but is not fully IEEE 754 compliant. The maximum ulp error is 2 across the full range of inputs.

  \[\text{div(lhs, rhs)}_i = \text{lhs}_i / \text{rhs}_i\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |
| approx | yes | no | no | no |
| full | yes | no | no | no |
| rounding<nearest_even> | yes | yes | yes* | yes* |
| rounding<zero> | yes | yes | yes* | yes* |
| rounding<negative_inf> | yes | yes | yes* | yes* |
| rounding<positive_inf> | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.10. cuda_tile.exp2


*Element-wise power of two*


```
cuda_tile.exp2 %source %flush_to_zero
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input floating-point tile. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of raising 2 to the power of the input tile. 13.1


#### Description


The `exp2` operation computes the element-wise power of two of the input floating-point tile.

  \[\text{exp2}(x)_i = 2^{x_i}\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


The below table shows the supported modifiers for each data type.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res = exp2 %in : tile<4xf32>
```


See [cuda_tile.exp2_0](appendix.html#example-cuda-tile-exp2-0) for the full example listing.


### 8.7.11. cuda_tile.exp


*Element-wise exponential*


```
cuda_tile.exp %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input float tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The exponential of the input tile. 13.1


#### Description


The `exp` operation computes the element-wise exponential of the input floating-point tile.

  \[\text{exp}(x)_i = e^{x_i}\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res = exp %in : tile<4xf32>
```


See [cuda_tile.exp_0](appendix.html#example-cuda-tile-exp-0) for the full example listing.


### 8.7.12. cuda_tile.floor


*Element-wise floor rounding*


```
cuda_tile.floor %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input tile to the floor operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the floor operation. 13.1


#### Description


The `floor` operation computes the element-wise floor on the input floating-point tile rounding each element down to the largest integer that is less than or equal to the element.

  \[\text{floor}_i(x_i) = \max\{n \in \mathbb{Z} \mid n \leq x_i\}\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%source = constant <f32: 1.5> : tile<f32>
%result = floor %source : tile<f32>
```


See [cuda_tile.floor_0](appendix.html#example-cuda-tile-floor-0) for the full example listing.


### 8.7.13. cuda_tile.fma


*Floating point fused multipy-add*


```
cuda_tile.fma %lhs %rhs %acc %rounding_mode %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - acc ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The accumulator operand. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-fma-roundingmode-attr)) - The rounding mode for the operation. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The fused multiply-add of the input tiles. 13.1


#### Description


Takes three operands `lhs`, `rhs` and `acc`, returns `result = lhs * rhs + acc`.

  \[\text{fma}(x, y, z)_i = x_i \times y_i + z_i\]
The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |
| rounding<nearest_even> | yes | yes | yes | yes |
| rounding<zero> | yes | yes | yes* | yes* |
| rounding<negative_inf> | yes | yes | yes* | yes* |
| rounding<positive_inf> | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs`, `acc` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.14. cuda_tile.log2


*Element-wise base-2 logarithm*


```
cuda_tile.log2 %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input floating-point tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the log2 operation. 13.1


#### Description


The `log2` operation computes the element-wise base-2 logarithm of a floating-point tile.

  \[\text{log2}(x)_i = \log_2(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res = log2 %in : tile<4xf32>
```


See [cuda_tile.log2_0](appendix.html#example-cuda-tile-log2-0) for the full example listing.


### 8.7.15. cuda_tile.log


*Element-wise natural logarithm*


```
cuda_tile.log %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input floating-point tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the log operation. 13.1


#### Description


The `log` operation computes the element-wise natural logarithm of a floating-point tile.

  \[\text{log}(x)_i = \ln(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.16. cuda_tile.maxf


*Element-wise floating-point maximum*


```
cuda_tile.maxf %lhs %rhs %propagate_nan %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - propagate_nan ([Flag](operations.html#type-flag)) - When set, `maxf` (or `minf`) returns a `NaN` if either of the two compared elements is `NaN`. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the `maxf` operation. 13.1


#### Description


The `maxf` operation computes the element-wise maximum of two input tiles with floating-point element types.


The `propagate_nan` controls how `maxf` will interpret `NaN`. If the `propagate_nan` modifier is set, `maxf` returns a canonical `NaN` if either of the compared elements is `NaN` (IEEE 754-2019’s maximum). While if the `propagate_nan` modifier is not set, `maxf` returns a canonical `NaN` only if both elements are `NaN`; otherwise, it returns the non-`NaN` element (IEEE 754-2019’s maximumNumber).


If neither element is `NaN`, `maxf` will return the greater of the inputs. `+0.0` is considered greater than `-0.0`.


If the `flush_to_zero` modifier is specified, denormal numbers are flushed to sign-preserving zero. The `flush_to_zero` modifier applies only to the f32 data type.

  \[\begin{split}\text{maxi}(x, y)_i = \begin{cases} x_i & \text{if } x_i \geq y_i \\ y_i & \text{if } x_i < y_i \end{cases}\end{split}\]
#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// Create tensor view from a pointer to global memory
%0 = make_tensor_view %arg0, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xf32, strides=[4,1]>
%1 = make_tensor_view %arg1, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xf32, strides=[4,1]>
// Convert tensor views to partition views and load tiles from partition views.
%p0 = make_partition_view %0 : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>
%p1 = make_partition_view %1 : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>
%c0 = constant <i32: 0> : tile<i32>
%2, %token0 = load_view_tko weak %p0[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>, tile<i32> -> tile<2x4xf32>, token
%3, %token1 = load_view_tko weak %p1[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>, tile<i32> -> tile<2x4xf32>, token
// IEEE 754-2019's maximum
%4 = maxf %2, %3 propagate_nan : tile<2x4xf32>
// IEEE 754-2019's maximumNumber
%5 = maxf %2, %3 : tile<2x4xf32>
// flush denormal to positive zero
%6 = maxf %2, %3 flush_to_zero : tile<2x4xf32>
```


See [cuda_tile.maxf_0](appendix.html#example-cuda-tile-maxf-0) for the full example listing.


### 8.7.17. cuda_tile.minf


*Element-wise floating-point minimum*


```
cuda_tile.minf %lhs %rhs %propagate_nan %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - propagate_nan ([Flag](operations.html#type-flag)) - When set, `maxf` (or `minf`) returns a `NaN` if either of the two compared elements is `NaN`. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The minimum of the input tiles. 13.1


#### Description


The `minf` operation computes the element-wise minimum of two input tiles with floating-point element types.


The `propagate_nan` controls how `minf` will interpret `NaN`. If the `propagate_nan` modifier is set, `minf` returns a canonical `NaN` if either of the compared elements is `NaN` (IEEE 754-2019’s minimum). While if the `propagate_nan` modifier is not set, `minf` returns a canonical `NaN` only if both elements are `NaN`; otherwise, it returns the non-`NaN` element (IEEE 754-2019’s minimumNumber).


If neither element is `NaN`, `minf` will return the lowest of the inputs. `-0.0` is considered less than `+0.0`.


If the `flush_to_zero` modifier is specified, denormal numbers are flushed to sign-preserving zero. The `flush_to_zero` modifier applies only to the f32 data type.

  \[\begin{split}\text{minf}(x, y)_i = \begin{cases} x_i & \text{if } x_i \leq y_i \\ y_i & \text{if } x_i > y_i \end{cases}\end{split}\]
#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// Create tensor view from a pointer to global memory
%0 = make_tensor_view %arg0, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xf32, strides=[4,1]>
%1 = make_tensor_view %arg1, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xf32, strides=[4,1]>
// Convert tensor views to partition views and load tiles from partition views.
%p0 = make_partition_view %0 : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>
%p1 = make_partition_view %1 : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>
%c0 = constant <i32: 0> : tile<i32>
%2, %token0 = load_view_tko weak %p0[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>, tile<i32> -> tile<2x4xf32>, token
%3, %token1 = load_view_tko weak %p1[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xf32, strides=[4,1]>>, tile<i32> -> tile<2x4xf32>, token
// IEEE 754-2019's minimum
%4 = minf %2, %3 propagate_nan : tile<2x4xf32>
// IEEE 754-2019's minimumNumber
%5 = minf %2, %3 : tile<2x4xf32>
// flush denormal to positive zero
%6 = minf %2, %3 flush_to_zero : tile<2x4xf32>
```


See [cuda_tile.minf_0](appendix.html#example-cuda-tile-minf-0) for the full example listing.


### 8.7.18. cuda_tile.mulf


*Element-wise floating-point multiplication*


```
cuda_tile.mulf %lhs %rhs %rounding_mode %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-mulf-roundingmode-attr)) - The rounding mode for the operation. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The product of the input tiles. 13.1


#### Description


The `mulf` operation computes the element-wise product between the two input tiles with with floating-point element types.


If the `flush_to_zero` modifier is specified, denormal numbers are flushed to positive zero.


If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result.

  \[\text{mulf}(x, y)_i = x_i \times y_i\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |
| rounding<nearest_even> | yes | yes | yes | yes |
| rounding<zero> | yes | yes | yes* | yes* |
| rounding<negative_inf> | yes | yes | yes* | yes* |
| rounding<positive_inf> | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.19. cuda_tile.negf


*Element-wise floating-point negation*


```
cuda_tile.negf %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The negated floating-point tile. 13.1


#### Description


`negf` is an element-wise operation that negates the sign of `source`.

  \[\text{negf}(x)_i = -x_i\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%source = constant <f32: 0.0> : tile<4xf32>
%result = negf %source : tile<4xf32>
```


See [cuda_tile.negf_0](appendix.html#example-cuda-tile-negf-0) for the full example listing.


### 8.7.20. cuda_tile.pow


*Element-wise floating-point exponentiation*


```
cuda_tile.pow %source %exponent
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The base tile. 13.1
 - exponent ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The exponent tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the pow operation. 13.1


#### Description


The `pow` operation computes the element-wise exponentiation of the source floating-point tile raised to the power of the exponent floating-point tile.

  \[\text{pow}(x, y)_i = x_i^{y_i}\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `result`, `source` and `exponent` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - `source`, `exponent` and `result` must have the same rank.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%source = constant <f32: 0.0> : tile<4xf32>
%exponent = constant <f32: 2.0> : tile<4xf32>
%result = pow %source, %exponent : tile<4xf32>
```


See [cuda_tile.pow_0](appendix.html#example-cuda-tile-pow-0) for the full example listing.


### 8.7.21. cuda_tile.remf


*Element-wise floating-point remainder*


```
cuda_tile.remf %lhs %rhs
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The remainder after division. 13.1


#### Description


The `remf` operation computes the element-wise floating-point remainder using truncated division (rounding towards zero).

  \[\text{remf}(x, y)_i = x_i - \text{trunc}(x_i / y_i) \times y_i\]
The result has the same sign as the dividend (`lhs`) and its magnitude is less than the magnitude of divisor (`rhs`).


Special cases:


 - If `y` is zero, returns `NaN`
 - If `x` is infinite and `y` is finite, returns `NaN`
 - If `x` is finite and `y` is infinite, returns `x`
 - If either argument is `NaN`, returns `NaN`


Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.22. cuda_tile.rsqrt


*Element-wise reciprocal square root*


```
cuda_tile.rsqrt %source %flush_to_zero
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input tile to compute the reciprocal square root of. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The reciprocal square root of the input tile. 13.1


#### Description


The `rsqrt` operation computes the element-wise reciprocal square root of the input floating-point tile.


This operation supports: `flush_to_zero`: if set by the user, will flush subnormal inputs and results to sign-preserving zero.

  \[\text{rsqrt}(x)_i = \frac{1}{\sqrt{x_i}}\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


The below table shows the supported modifiers for each data type.


| Modifier | Float32 | Float64 |
| --- | --- | --- |
| flush_to_zero | yes | no |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res = rsqrt %in : tile<4xf32>

// Rsqrt op with flush to zero modifier
%ftz_res = rsqrt %in flush_to_zero : tile<4xf32>
```


See [cuda_tile.rsqrt_0](appendix.html#example-cuda-tile-rsqrt-0) for the full example listing.


### 8.7.23. cuda_tile.sinh


*Element-wise hyperbolic sine*


```
cuda_tile.sinh %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input float tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The hyperbolic sine of the input tile. 13.1


#### Description


The `sinh` operation computes the element-wise hyperbolic sine of the input floating-point tile.

  \[\text{sinh}(x)_i = \sinh(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.24. cuda_tile.sin


*Element-wise sine*


```
cuda_tile.sin %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input float tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The sine of the input tile. 13.1


#### Description


The `sin` operation computes the element-wise sine of the input floating-point tile.

  \[\text{sin}(x)_i = \sin(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res = sin %in : tile<4xf32>
```


See [cuda_tile.sin_0](appendix.html#example-cuda-tile-sin-0) for the full example listing.


### 8.7.25. cuda_tile.sqrt


*Element-wise square root*


```
cuda_tile.sqrt %source %rounding_mode %flush_to_zero
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input tile to compute the square root of. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-sqrt-roundingmode-attr)) - The rounding mode for the operation. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The square root of the input tile. 13.1


#### Description


The `sqrt` operation computes the element-wise square root of a floating-point tile.

  \[\text{sqrt}(x)_i = \sqrt{x_i}\]
The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |
| approx | yes | no | no | no |
| rounding<nearest_even> | yes | yes | yes | yes |
| rounding<zero> | yes | yes | yes* | yes* |
| rounding<negative_inf> | yes | yes | yes* | yes* |
| rounding<positive_inf> | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.26. cuda_tile.subf


*Element-wise floating-point subtraction*


```
cuda_tile.subf %lhs %rhs %rounding_mode %flush_to_zero
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-subf-roundingmode-attr)) - The rounding mode for the operation. 13.1
 - flush_to_zero ([Flag](operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The result of the subtraction. 13.1


#### Description


The `subf` operation computes the element-wise subtraction of the input floating-point tiles.

  \[\text{subf}(x, y)_i = x_i - y_i\]
Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating Point](operations.html#op-group-floating-point) for more details.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| flush_to_zero | yes | no | no | no |
| rounding<nearest_even> | yes | yes | yes | yes |
| rounding<zero> | yes | yes | yes* | yes* |
| rounding<negative_inf> | yes | yes | yes* | yes* |
| rounding<positive_inf> | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.7.27. cuda_tile.tanh


*Element-wise hyperbolic tangent*


```
cuda_tile.tanh %source %rounding_mode
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input floating-point tile. 13.1
 - rounding_mode ([RoundingMode](operations.html#op-attribute-cuda-tile-tanh-roundingmode-attr)) - The rounding mode for the operation. 13.2


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The hyperbolic tangent of the input floating-point tile. 13.1


#### Description


The `tanh` operation computes the element-wise hyperbolic tangent of the input floating-point tile. Default rounding mode is full.


The `approx` rounding mode implements a fast approximation to hyperbolic tangent. Subnormal results of this fast approximation are not flushed to zero.


The `full` rounding mode implements a relatively fast full-range approximation. The maximum ulp error is 2 across the full range of inputs in FP32 and 1 in FP64.

  \[\text{tanh}(x)_i = \tanh(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


The below table shows the supported modifiers for each data type. Entries with ‘*’ are emulated in f32.


| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| approx | yes | no | no | no |
| full | yes | yes | yes* | yes* |


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%in = constant <f32: [0.0, 1.0, 2.0, 3.0]> : tile<4xf32>
%res0 = tanh %in : tile<4xf32>

// tanh with approx modifier
%res1 = tanh %in rounding<approx> : tile<4xf32>
```


See [cuda_tile.tanh_0](appendix.html#example-cuda-tile-tanh-0) for the full example listing.


### 8.7.28. cuda_tile.tan


*Element-wise tangent*


```
cuda_tile.tan %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The input floating-point tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>) - The tangent of the input floating-point tile. 13.1


#### Description


The `tan` operation computes the element-wise tangent of the input floating-point tile.

  \[\text{tan}(x)_i = \tan(x_i)\]
This operation is emulated in `:code:`f32`` when executed on half-precision inputs (`:code:`f16`` and `:code:`bf16``). See [Floating Point](operations.html#op-group-floating-point) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[f16](types.html#subsection-element-types) | [bf16](types.html#subsection-element-types) | [f32](types.html#subsection-element-types) | [f64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


## 8.8. Integer


Tile IR contains a set of typed arithmetic operations which implement familiar arithmetic operations on tiles of integers, for floating-point operations see [Floating Point](operations.html#op-group-floating-point).


All operations are implemented in a manner that is efficient for the target architecture and device family. In most common cases this means utilizing the underlying hardware’s native floating-point operations. Due to Tile IR’s stability guarantees and higher-level programming model some types on some hardware may be emulated, see [Stability](stability.html#section-stability) for more information about the stability guarantees and information about per device behavior.


### 8.8.1. Integer Arithmetic


Integer types in Tile IR are signless, which is importantly not the same as unsigned. We store all integers in a two’s complement representation and with required operations supporting a signed or unsigned flag as needed. This design allows us to not have to differentiate between signed and unsigned integer types at the IR level and keeps sign information local to the operation.


For the `i1` type, unsigned operations see values 0/1, while signed operations see values 0/-1, with all i1 values canonicalized to 0x00 (false) or 0x01 (true) for consistent LSB-only semantics.


### 8.8.2. cuda_tile.absi


*Element-wise integer absolute value*


```
cuda_tile.absi %source
```


#### Parameters


 - source ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The input integer tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The absolute value of the input tile. 13.1


#### Description


The `absi` operation computes the absolute value of the input integer tile.


The input tile is always interpreted as a signed integer. The output tile is always interpreted as an unsigned integer.

  \[\text{absi}(x) = |x|\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.3. cuda_tile.addi


*Element-wise integer addition*


```
cuda_tile.addi %lhs %rhs %overflow
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - overflow ([IntegerOverflow](operations.html#op-attribute-cuda-tile-addi-integeroverflow-attr)) - The overflow behavior of the operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The sum of the input tiles. 13.1


#### Description


The `addi` operation computes the element-wise addition of two tiles with integer element types.

  \[\text{addi}(x, y)_i = x_i + y_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.


These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


 - `none` - The compiler makes no assumptions regarding overflow behavior.
 - `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
 - `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
 - `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.


If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.4. cuda_tile.divi


*Element-wise integer division*


```
cuda_tile.divi %lhs %rhs %signedness %rounding
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-divi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1
 - rounding ([RoundingMode](operations.html#op-attribute-cuda-tile-divi-roundingmode-attr)) - Set the rounding direction (implementing floordiv/ceildiv). 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result of the division. 13.1


#### Description


The `divi` operation computes the element-wise division of two tile values with integer element type.


The default rounding is towards zero. The rounding mode can be set to positive_inf (“ceiling division”), or negative_inf (“floor division”), other values are illegal.


The use of the rounding flag negative_inf with unsigned is not a valid combination.


If the unsigned flag is provided, the operands are treated as unsigned integers, otherwise they are treated as signed integers.


The behavior is undefined if the right hand side is zero. A signed division overflow (minimum value divided by -1) is undefined behavior.

  \[\text{div(lhs, rhs)}_i = \text{lhs}_i / \text{rhs}_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


The `rounding` attribute specifies the rounding mode to use for the operation.


 - `nearest_even` - Round to nearest (ties to even).
 - `zero` - Round towards zero (truncate).
 - `negative_inf` - Round towards negative infinity.
 - `positive_inf` - Round towards positive infinity.
 - `approx` - Approximate rounding mode.
 - `full` - Full precision rounding mode.
 - `nearest_int_to_zero` - Round towards zero to the nearest integer.


#### Constraints


 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.5. cuda_tile.maxi


*Element-wise integer maximum*


```
cuda_tile.maxi %lhs %rhs %signedness
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-maxi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result of the maxi operation. 13.1


#### Description


The `maxi` operation computes the element-wise maximum between two input integer tiles.

  \[\begin{split}\text{maxi}(x, y)_i = \begin{cases} x_i & \text{if } x_i \geq y_i \\ y_i & \text{if } x_i < y_i \end{cases}\end{split}\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// Create tensor view from a pointer to global memory
%0 = make_tensor_view %arg0, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xi32, strides=[4,1]>
%1 = make_tensor_view %arg1, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xi32, strides=[4,1]>
// Convert tensor views to partition views and load tiles from them.
%p0 = make_partition_view %0 : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>
%p1 = make_partition_view %1 : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>
%c0 = constant <i32: 0> : tile<i32>
%2, %token0 = load_view_tko weak %p0[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>, tile<i32> -> tile<2x4xi32>, token
%3, %token1 = load_view_tko weak %p1[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>, tile<i32> -> tile<2x4xi32>, token
// Signless i32 treated as unsigned
%4 = maxi %2, %3 unsigned : tile<2x4xi32>
// Signless i32 treated as signed
%5 = maxi %2, %3 signed : tile<2x4xi32>
```


See [cuda_tile.maxi_0](appendix.html#example-cuda-tile-maxi-0) for the full example listing.


### 8.8.6. cuda_tile.mini


*Element-wise integer minimum*


```
cuda_tile.mini %lhs %rhs %signedness
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-mini-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The minimum of the input tiles. 13.1


#### Description


The `mini` operation computes the element-wise minimum between the two input tiles with integer element types.

  \[\begin{split}\text{mini}(x, y)_i = \begin{cases} x_i & \text{if } x_i \leq y_i \\ y_i & \text{if } x_i > y_i \end{cases}\end{split}\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// Create tensor view from a pointer to global memory
%0 = make_tensor_view %arg0, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xi32, strides=[4,1]>
%1 = make_tensor_view %arg1, shape = [2, 4], strides = [4, 1] : tensor_view<2x4xi32, strides=[4,1]>
// Convert tensor views to partition views and load tiles from partition views.
%p0 = make_partition_view %0 : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>
%p1 = make_partition_view %1 : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>
%c0 = constant <i32: 0> : tile<i32>
%2, %token0 = load_view_tko weak %p0[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>, tile<i32> -> tile<2x4xi32>, token
%3, %token1 = load_view_tko weak %p1[%c0, %c0] : partition_view<tile=(2x4), tensor_view<2x4xi32, strides=[4,1]>>, tile<i32> -> tile<2x4xi32>, token
// Signless i32 treated as unsigned
%4 = mini %2, %3 unsigned : tile<2x4xi32>
// Signless i32 treated as signed
%5 = mini %2, %3 signed : tile<2x4xi32>
```


See [cuda_tile.mini_0](appendix.html#example-cuda-tile-mini-0) for the full example listing.


### 8.8.7. cuda_tile.muli


*Element-wise integer multiplication*


```
cuda_tile.muli %lhs %rhs %overflow
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side input integer tile. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side input integer tile. 13.1
 - overflow ([IntegerOverflow](operations.html#op-attribute-cuda-tile-muli-integeroverflow-attr)) - The overflow behavior of the operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The product of the input tiles. 13.1


#### Description


The `muli` operation computes the element-wise product between the two input tiles with integer element types.

  \[\text{muli}(x, y)_i = x_i \times y_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.


These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


 - `none` - The compiler makes no assumptions regarding overflow behavior.
 - `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
 - `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
 - `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.


If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.8. cuda_tile.mulhii


*Element-wise high bits of integer multiplication*


```
cuda_tile.mulhii %x %y
```


#### Parameters


 - x ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side input integer tile. 13.1
 - y ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side input integer tile. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The most significant bits of the product of the input tiles. 13.1


#### Description


The `mulhii` operation produces the most significant N bits of the 2N-bit product of two N-bit integer tiles. For `i64`, this is the most significant 64 bits of the full 128-bit product; for `i8`, it is the most significant 8 bits of the full 16-bit product; etc.


This is in contrast to `muli`, which produces the lower N bits of the 2N-bit product.


The `mulhii` operation is only defined for unsigned integers.

  \[\text{mulhii}(x_i, y_i) = x_i \times y_i >> \text{bitwidth}(\text{type}(x_i))\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `x`, `y` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// 2^31 * 2 = 2^32, or 0x100000000.
// The most significant 32 bits of the product are 0x00000001.
// The lower 32 bits of the product are 0x00000000.
%a = constant <i32: 2147483648> : tile<i32>  // %a = 2^31
%b = constant <i32: 2> : tile<i32>           // %b = 2
%res_hi = mulhii %a, %b : tile<i32>          // %res_hi = 1
%res_lo = muli %a, %b : tile<i32>            // %res_lo = 0
```


See [cuda_tile.mulhii_0](appendix.html#example-cuda-tile-mulhii-0) for the full example listing.


### 8.8.9. cuda_tile.negi


*Element-wise integer negation*


```
cuda_tile.negi %source %overflow
```


#### Parameters


 - source ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The input integer tile. 13.1
 - overflow ([IntegerOverflow](operations.html#op-attribute-cuda-tile-negi-integeroverflow-attr)) - The overflow behavior of the operation. 13.2


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The negated integer tile. 13.1


#### Description


The `negi` operation computes the element-wise negation of the input integer tile. The input and output tiles are always interpreted as signed integers.

  \[\text{negi}(x_i) = -x_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.


These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


 - `none` - The compiler makes no assumptions regarding overflow behavior.
 - `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
 - `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
 - `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.


If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `source` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%source = constant <i16: [0, 1, 2, 3]> : tile<4xi16>
%result = negi %source : tile<4xi16>
// %result = [0, -1, -2, -3]
```


See [cuda_tile.negi_0](appendix.html#example-cuda-tile-negi-0) for the full example listing.


### 8.8.10. cuda_tile.ori


*Element-wise bitwise OR*


```
cuda_tile.ori %lhs %rhs
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The bitwise OR of the input tiles. 13.1


#### Description


The `ori` operation computes the element-wise bitwise OR of two tiles with integer element types.

  \[\text{ori}(x, y)_i = x_i | y_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.11. cuda_tile.remi


*Element-wise integer remainder*


```
cuda_tile.remi %lhs %rhs %signedness
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-remi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The remainder after division. 13.1


#### Description


The `remi` operation computes the element-wise remainder of the input tiles with integer element types using truncated division (rounding towards zero). Division by zero is undefined behavior.

  \[\text{remi}(x, y)_i = x_i - \text{trunc}(x_i / y_i) \times y_i\]
If the operation is signed, the sign of the result matches the sign of the dividend (`lhs`). For example:


 - `remi(7, 3) = 1`
 - `remi(7, -3) = 1`
 - `remi(-7, 3) = -1`
 - `remi(-7, -3) = -1`


Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `result`, `lhs` and `rhs` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.12. cuda_tile.shli


*Element-wise shift-left*


```
cuda_tile.shli %lhs %rhs %overflow
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand (shift amount). 13.1
 - overflow ([IntegerOverflow](operations.html#op-attribute-cuda-tile-shli-integeroverflow-attr)) - The overflow behavior of the operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result of the left shift operation. 13.1


#### Description


The `shli` operation computes the element-wise left shift of the `lhs` integer operand by the `rhs` operand. The lower-order bits on the right are filled with zeros.

  \[\text{shli}(x, y)_i = x_i \ll y_i\]
The `rhs` operand is interpreted as an unsigned integer.


Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.


These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


 - `none` - The compiler makes no assumptions regarding overflow behavior.
 - `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
 - `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
 - `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.


If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.13. cuda_tile.shri


*Element-wise shift-right*


```
cuda_tile.shri %lhs %rhs %signedness
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand (shift amount). 13.1
 - signedness ([Signedness](operations.html#op-attribute-cuda-tile-shri-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result of the right shift operation. 13.1


#### Description


The `shri` operation computes the element-wise right shift of the `lhs` integer operand by the value of the `rhs` operand for tiles with integer element types.

  \[\text{shri}(x, y)_i = x_i \gg y_i\]
When `unsigned`, higher-order bits are zero-filled; when `signed`, the higher-order bits are filled with the sign bit.


The `rhs` operand is always interpreted as an unsigned integer.


Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `signedness` attribute specifies the signedness of operand(s).


 - `unsigned` - Treat the operands as unsigned integers.
 - `signed` - Treat the operands as signed integers.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.14. cuda_tile.subi


*Element-wise integer subtraction*


```
cuda_tile.subi %lhs %rhs %overflow
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1
 - overflow ([IntegerOverflow](operations.html#op-attribute-cuda-tile-subi-integeroverflow-attr)) - The overflow behavior of the operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The result of the subtraction. 13.1


#### Description


The `subi` operation computes the element-wise subtraction of two input integer tiles.

  \[\text{subi}(x, y)_i = x_i - y_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.


These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.


 - `none` - The compiler makes no assumptions regarding overflow behavior.
 - `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
 - `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
 - `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.


If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


### 8.8.15. cuda_tile.xori


*Element-wise bitwise XOR*


```
cuda_tile.xori %lhs %rhs
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The bitwise XOR of the input tiles. 13.1


#### Description


The `xori` operation computes the element-wise bitwise exclusive or (XOR) of two tile values with integer element types.

  \[\text{xori}(x, y)_i = x_i \oplus y_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%lhs = constant <i32: [0, 1, 2, 3]> : tile<4xi32>
%rhs = constant <i32: [4, 5, 6, 7]> : tile<4xi32>
// This computes the bitwise XOR of each element in `%lhs` and `%rhs`, which
// are tiles of shape `4xi32`, and returns the result as `%result`.
%result = xori %lhs, %rhs : tile<4xi32>
```


See [cuda_tile.xori_0](appendix.html#example-cuda-tile-xori-0) for the full example listing.


## 8.9. Bitwise


### 8.9.1. cuda_tile.andi


*Element-wise bitwise logical AND*


```
cuda_tile.andi %lhs %rhs
```


#### Parameters


 - lhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The left hand side operand. 13.1
 - rhs ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The right hand side operand. 13.1


#### Results


 - result ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>) - The bitwise AND of the input tiles. 13.1


#### Description


The `andi` operation produces a value that is the result of an element-wise, bitwise “and” of two tiles with integer element type.

  \[\text{andi}(x, y)_i = x_i \land y_i\]
Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer](operations.html#op-group-integer) for more details.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.
 - `lhs`, `rhs` and `result` must have the same shape and element type ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types) | [i8](types.html#subsection-element-types) | [i16](types.html#subsection-element-types) | [i32](types.html#subsection-element-types) | [i64](types.html#subsection-element-types)>).
 - The operation’s result type may be inferred from its operands and attributes.


## 8.10. Atomics


Warning


Atomic operations are limited in Tile IR as of early-access and will be updated in coming releases in accordance with the incoming memory model and memory operation updates.


### 8.10.1. cuda_tile.atomic_cas_tko


*Atomic compare-and-swap on global memory*


```
cuda_tile.atomic_cas_tko %memory_ordering_semantics %memory_scope %pointers %cmp %val %mask %token
```


#### Parameters


 - memory_ordering_semantics ([MemoryOrderingSemantics](operations.html#op-attribute-cuda-tile-atomic-cas-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the atomic operation. 13.1
 - memory_scope ([MemoryScope](operations.html#op-attribute-cuda-tile-atomic-cas-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
 - pointers ([ptr](types.html#type-ptr)) - The pointers to the memory locations to perform the atomic compare-and-swap operation on. 13.1
 - cmp ([tile](types.html#type-tile)) - The values to compare against. 13.1
 - val ([tile](types.html#type-tile)) - The values to swap in. 13.1
 - mask ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The mask for the atomic operation. 13.1
 - token ([token](operations.html#type-token)) - The token for the atomic operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The result of the atomic operation. 13.1
 - result_token ([token](operations.html#type-token)) - The result token of the atomic operation. 13.1


#### Description


The `atomic_cas` operation performs element-wise, atomic compare-and-swaps at the specified global memory `pointers`. The data in memory is compared to `cmp` and the data written to memory is specified by `val`. The operation returns the original value that was stored in memory before the atomic operation was performed.


The shape (and the element type) of `pointers`, `cmp`, `val` and `result` must match. The `atomic_cas` operation performs the following steps for every `(pointer, cmp, val)` tuple in one atomic transaction. (One atomic transaction per tuple.)


```
atomic() {
    x = *pointer
    if x == cmp {
    *pointer = val
  }
  return x
}
```


An optional parameter, `mask`, allows specifying which elements participate in the atomic operation. A false value at position i masks out the corresponding element in `pointers`, excluding it from the operation. The returned value for a masked element at position i is `cmp[i]`. If no mask is provided, all elements are included in the computation by default. The shape of mask must match that of `pointers`, `cmp`, and `val`.


A token-ordered atomic compare-and-swap is not constrained by program order. The compiler may reorder it (i.e. place them earlier or later in program order) unless constrained by tokens.


Supported data types:
i32, i64: integer values
f32, f64: floating-point values


For floating-point types, the comparison uses bitwise equality rather than IEEE-754 semantics. This means different `NaN` bit patterns are treated as distinct values, and `+0.0` and `-0.0` are considered different if their bit representations differ.


The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](memory_model.html#section-memory-model) of the specification.


 - `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
 - `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then *happens before* is established.
 - `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then *happens before* is established.
 - `acq_rel` - There may be concurrent accesses to the location. This has the effect of both a release and acquire operation.


Note: The following variants are not supported by this operation: `weak`.


The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.


 - `tl_blk` - There may be concurrent accesses from within the same tile block.
 - `device` - There may be concurrent accesses from within the same device (i.e., GPU).
 - `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).


#### Constraints


 - `cmp`, `val` and `result` must have the same shape and element type ([tile](types.html#type-tile)).
 - The operation must encode variadic operand segment sizes in attributes.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%ptr_1x = reshape %ptr : tile<ptr<i32>> -> tile<1xptr<i32>>
%ptr_vec = broadcast %ptr_1x : tile<1xptr<i32>> -> tile<8xptr<i32>>
%offsets = iota : tile<8xi32>
%ptrs = offset %ptr_vec, %offsets : tile<8xptr<i32>>, tile<8xi32> -> tile<8xptr<i32>>
%cmp = constant <i32: [0, 1, 2, 3, 4, 5, 6, 7]> : tile<8xi32>
%val = constant <i32: [7, 6, 5, 4, 3, 2, 1, 0]> : tile<8xi32>
%mask = constant <i1: [0, 1, 0, 1, 0, 1, 0, 1]> : tile<8xi1>

// Atomic CAS without input token.
%0, %token = atomic_cas_tko relaxed device %ptrs, %cmp, %val :
  tile<8xptr<i32>>, tile<8xi32> -> tile<8xi32>, token

// Atomic CAS without input token.
%1, %token1 = atomic_cas_tko relaxed device %ptrs, %cmp, %val, %mask :
  tile<8xptr<i32>>, tile<8xi32>, tile<8xi1> -> tile<8xi32>, token

// Atomic CAS with input token.
%token2 = make_token : token
%2, %token3 = atomic_cas_tko relaxed device %ptrs, %cmp, %val token=%token2 :
  tile<8xptr<i32>>, tile<8xi32> -> tile<8xi32>, token

return
```


See [cuda_tile.atomic_cas_tko_0](appendix.html#example-cuda-tile-atomic-cas-tko-0) for the full example listing.


### 8.10.2. cuda_tile.atomic_rmw_tko


*Atomic read-modify-write on global memory*


```
cuda_tile.atomic_rmw_tko %memory_ordering_semantics %memory_scope %pointers %mode %arg %mask %token
```


#### Parameters


 - memory_ordering_semantics ([MemoryOrderingSemantics](operations.html#op-attribute-cuda-tile-atomic-rmw-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the load operation. 13.1
 - memory_scope ([MemoryScope](operations.html#op-attribute-cuda-tile-atomic-rmw-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
 - pointers ([ptr](types.html#type-ptr)) - The pointer tile to perform atomic operation on. 13.1
 - mode ([AtomicRMWMode](operations.html#op-attribute-cuda-tile-atomic-rmw-tko-atomicrmwmode-attr)) - The atomic operation mode (e.g., add, max, min, etc.). 13.1
 - arg ([tile](types.html#type-tile)) - The value tile to use in the atomic operation. 13.1
 - mask ([tile](types.html#type-tile)<[i1](types.html#subsection-element-types)>) - The mask for the load operation. 13.1
 - token ([token](operations.html#type-token)) - The token for the atomic operation. 13.1


#### Results


 - result ([tile](types.html#type-tile)) - The result of the atomic operation. 13.1
 - result_token ([token](operations.html#type-token)) - The result token of the load operation. 13.1


#### Description


The `atomic_rmw_tko` operation performs element-wise, atomic read-modify-write operations at the global memory locations specified by `pointers`. The values written to memory are determined by `mode` and `arg`. The operation returns the original value stored at each location before the atomic update.


The shapes of `pointers`, `arg`, and `result` must match. The element type of the pointer type must match the element types of both `arg` and `result`. Each (`pointer`, `arg`) pair is processed in a single atomic transaction.


```
atomic {
  x = *pointer
  y = mode(x, arg)
  *pointer = y
  return x
}
```


An optional parameter, `mask`, specifies which elements participate in the atomic operation. A False value at position `i` excludes the corresponding element in `pointers` from the operation. The value returned for a masked-out element is implementation-defined. The shape of `mask` must match the shape of `pointers`.


The `atomic_addf` operation is defined to round to the nearest even value. .. note:: The current implementation of the compiler flushes denormals to zero. This behavior will be fixed in a future version of the compiler and users should not rely on it.


Token-ordered atomic read-modify-write operations are not constrained by program order. The compiler may reorder them (i.e., move them earlier or later in the program) unless further constrained by tokens.


Supported data types by `mode`:


> - ADD, AND, MAX, MIN, OR, UMAX, UMIN, XOR: i32, i64
>  - ADDF: f16, f32, f64
>  - XCHF: i32, i64, f32, f64


The `U` prefix in UMAX and UMIN distinguishes these from their signed counterparts (MAX and MIN) by interpreting the comparison as unsigned.


The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](memory_model.html#section-memory-model) of the specification.


 - `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
 - `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then *happens before* is established.
 - `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then *happens before* is established.
 - `acq_rel` - There may be concurrent accesses to the location. This has the effect of both a release and acquire operation.


Note: The following variants are not supported by this operation: `weak`.


The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.


 - `tl_blk` - There may be concurrent accesses from within the same tile block.
 - `device` - There may be concurrent accesses from within the same device (i.e., GPU).
 - `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).


The `mode` attribute specifies the mode of the atomic read-modify-write operation.


 - `and` - Perform bitwise AND as the modification operation.
 - `or` - Perform bitwise OR as the modification operation.
 - `xor` - Perform bitwise XOR as the modification operation.
 - `add` - Perform integer addition as the modification operation.
 - `addf` - Perform floating-point addition as the modification operation.
 - `max` - Perform maximum as the modification operation.
 - `min` - Perform minimum as the modification operation.
 - `umax` - Perform unsigned maximum as the modification operation.
 - `umin` - Perform unsigned minimum as the modification operation.
 - `xchg` - Perform exchange as the modification operation.


The `mode` attribute has a default value of `add`.


#### Constraints


 - `arg` and `result` must have the same shape and element type ([tile](types.html#type-tile)).
 - The operation must encode variadic operand segment sizes in attributes.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// Reshape the input pointer tile to have a 1d shape
%ptr_1x = reshape %ptr : tile<ptr<f32>> -> tile<1xptr<f32>>
// Broadcast the reshaped tile to a tile with 8 rows, effectively replicating the pointer 8 times
%ptr_vec = broadcast %ptr_1x : tile<1xptr<f32>> -> tile<8xptr<f32>>
// Create a tile of offsets [0, 1, 2, ..., 7] to index into memory
%offsets = iota : tile<8xi32>
// Add the offsets to each pointer in the vector to create 8 unique pointers
%ptrs = offset %ptr_vec, %offsets : tile<8xptr<f32>>, tile<8xi32> -> tile<8xptr<f32>>
%vals = constant <f32: [7.0, 6.0, 5.0, 4.0, 3.0, 2.0, 1.0, 0.0]> : tile<8xf32>

// Perform atomic addf operations on the memory locations pointed by %ptrs
// without requiring an input token. Returns the original values and a result token
%0, %res_token0 = atomic_rmw_tko relaxed device %ptrs, addf, %vals :
    tile<8xptr<f32>>, tile<8xf32> -> tile<8xf32>, token

// Perform atomic add operations again, this time using the explicit input token
%token = make_token : token
%1, %res_token1 = atomic_rmw_tko relaxed device %ptrs, addf, %vals, token = %token :
    tile<8xptr<f32>>, tile<8xf32> -> tile<8xf32>, token
```


See [cuda_tile.atomic_rmw_tko_0](appendix.html#example-cuda-tile-atomic-rmw-tko-0) for the full example listing.


## 8.11. Views


Views are a structured way to interact with tensors in memory. They are described in both the types section [Tensor View](types.html#sub-sec-view-types) and the semantics section [Views](semantics.html#section-semantics-sub-section-views).


Views are the primary way to interact with global memory in Tile IR. A common pattern is to construct a [Tensor View](types.html#type-tensor-view) from a pointer with [cuda_tile.make_tensor_view](operations.html#op-cuda-tile-make-tensor-view) and then use the [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko) operations to read and write to them. For larger tensors, loading the entire tensor is not efficient and therefore we have a sub-view [Partition View](types.html#type-partition-view) which allows a user to tile a `tensor_view`.


### 8.11.1. cuda_tile.get_index_space_shape


*Query the index space dimension size*


```
cuda_tile.get_index_space_shape %src
```


#### Parameters


 - src ([view_type](operations.html#type-view-type)) - The source view type. 13.1


#### Results


 - result (Variadic<tile<any>>) - The shape of the index space, each value representing the size of the
corresponding dimension. 13.1


#### Description


The `get_index_space_shape` operation returns the shape of the index space of `src`.


The result tile has the same rank as the view’s index space with the elements representing the size of the corresponding dimension.


The result values should be interpreted as unsigned integers.


Warning


If the individual index space dimension do not fit in the result tile’s element type the behavior is undefined.


#### Constraints


 - The operation is pure and does not perform any memory side effects.


#### Examples


```
%tensor_view = make_tensor_view %base,
    shape = [2, 2, 4], strides = [2, 2, 1]
    : tensor_view<2x2x4xf32, strides=[2,2,1]>
%partition_view = make_partition_view %tensor_view :
  partition_view<tile=(2x2x4), tensor_view<2x2x4xf32, strides=[2,2,1]>>
%dim0, %dim1, %dim2 = get_index_space_shape %partition_view :
  partition_view<tile=(2x2x4), tensor_view<2x2x4xf32, strides=[2,2,1]>> -> tile<i64>
```


See [cuda_tile.get_index_space_shape_0](appendix.html#example-cuda-tile-get-index-space-shape-0) for the full example listing.


### 8.11.2. cuda_tile.get_tensor_shape


*Query the shape of a tensor view*


```
cuda_tile.get_tensor_shape %src
```


#### Parameters


 - src ([tensor_view](types.html#type-tensor-view)) - The source tensor view. 13.1


#### Results


 - result ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)<[any](operations.html#type-any)>>) - The shape of the tensor, each value representing the size of the corresponding dimension. 13.1


#### Description


The `get_tensor_shape` operation returns the shape of the tensor backing the provided tensor view.


The result values should be interpreted as unsigned integers.


Warning


If the tensor dimensions do not fit in the result tile’s element type the behavior is undefined.


#### Constraints


 - The operation is pure and does not perform any memory side effects.


#### Examples


```
%dim0, %dim1 = get_tensor_shape %tensor_view : tensor_view<32x32xf32, strides=[32,1]> -> tile<i64>
```


See [cuda_tile.get_tensor_shape_0](appendix.html#example-cuda-tile-get-tensor-shape-0) for the full example listing.


### 8.11.3. cuda_tile.load_view_tko


*Load a tile from a tile view*


```
cuda_tile.load_view_tko %memory_ordering_semantics %memory_scope %view %index %token %optimization_hints
```


#### Parameters


 - memory_ordering_semantics ([MemoryOrderingSemantics](operations.html#op-attribute-cuda-tile-load-view-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the load operation. 13.1
 - memory_scope ([MemoryScope](operations.html#op-attribute-cuda-tile-load-view-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
 - view ([view_type](operations.html#type-view-type)) - The view from which the tile will be loaded. 13.1
 - index ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)<[any](operations.html#type-any)>>) - The n-dimensional index of the desired element to load from the view. 13.1
 - token ([token](operations.html#type-token)) - The optional token for the load operation. 13.1
 - optimization_hints ([OptimizationHints](operations.html#op-attribute-cuda-tile-load-view-tko-optimizationhints-attr)) - Optimization hints for operation 13.1


#### Results


 - tile ([tile](types.html#type-tile)) - The loaded tile. 13.1
 - result_token ([token](operations.html#type-token)) - The result token. 13.1


#### Description


The `load_view_tko` operation loads a tile from a tile view.


A view is mapping from view-space indices to a particular element in the view, each view type has a defined mapping from view-space indices to tiles produced from elements of the view.


For example, the [Partition View](types.html#type-partition-view) partitions a [Tensor View](types.html#type-tensor-view) into a grid of equally sized tiles. The view indexes one of the partitioned tiles in the grid.


For a given view the rank of the indices must match the rank of the view’s index space. The space of valid indices depends on which view is passed to the operation. For example the index space of a [Partition View](types.html#type-partition-view) is equal to the rank of the partitioned tiles.


The `index` operands are interpreted as unsigned integers.


Out of bounds accesses are handled according to the semantics of [Partition View](types.html#type-partition-view).


The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](memory_model.html#section-memory-model) of the specification.


 - `weak` - No concurrent accesses to the source/destination location.
 - `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
 - `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then *happens before* is established.


Note: The following variants are not supported by this operation: `release`, `acq_rel`.


The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.


 - `tl_blk` - There may be concurrent accesses from within the same tile block.
 - `device` - There may be concurrent accesses from within the same device (i.e., GPU).
 - `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).


The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.


The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.


 - `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda_tile.entry](operations.html#op-cuda-tile-entry).
 - `allow_tma` - suggest whether to use TMA for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).
 - `latency` - latency hint for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).


For example they can be annotated as:


```
optimization_hints=<
  sm_100 = {num_cta_in_cga = 8},
  sm_120 = {num_cta_in_cga = 16}
>
```


#### Constraints


 - The operation must encode variadic operand segment sizes in attributes.


#### Examples


```
%tensor_view = make_tensor_view %ptr, shape=[8192, 128], strides=[128, 1]
  : tensor_view<8192x128xf32, strides=[128,1]>

// This example uses the PartitionView on a 8192x128xf32 tensor_view,
// dividing the tensor_view in tiles of 64x64.

%view = make_partition_view %tensor_view : partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>

%c0 = constant <i32: 0> : tile<i32>
%c1 = constant <i32: 1> : tile<i32>

// Load a tile at index (0, 0) in the view's index space.
// For this PartitionView, this is the rectangular tile such that
// X=[0,64) and Y=[0,64), in the coordinates of tiles.
%tile0, %res_token0 = load_view_tko weak %view[%c0, %c0]
  : partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> tile<64x64xf32>, token

// Load a tile at index (0, 1) in the view's index space.
// For this PartitionView, this is the rectangular tile such that
// X=[0,64) and Y=[64,128), in the coordinates of tiles.
%tile1, %res_token1 = load_view_tko weak %view[%c0, %c1]
  : partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> tile<64x64xf32>, token

// Same example as above but with memory token as input.
%token = make_token : token
%tile2, %res_token2 = load_view_tko weak %view[%c0, %c1] token = %token
  : partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> tile<64x64xf32>, token

// Loads a tile at the dynamic index (%index, %index) in the view's index space.
%tile3, %res_token3 = load_view_tko weak %view[%index, %index]
  : partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> tile<64x64xf32>, token
```


See [cuda_tile.load_view_tko_0](appendix.html#example-cuda-tile-load-view-tko-0) for the full example listing.


### 8.11.4. cuda_tile.make_partition_view


*Create a partition view from a tensor view*


```
cuda_tile.make_partition_view %tensor_view
```


#### Parameters


 - tensor_view ([tensor_view](types.html#type-tensor-view)) - The source tensor view to create a partition view from. 13.1


#### Results


 - result ([partition_view](types.html#type-partition-view)) - The created partition view. 13.1


#### Description


The `make_partition_view` operation creates a [partition_view](types.html#type-partition-view) from a [tensor_view](types.html#type-tensor-view). For more details about partition views see [Partition View](types.html#type-partition-view).


The operation uses the type constraints of the input tensor view and the annotated return type to perform the partitioning. The tensor view’s type contains its physical layout in the form of shapes and strides and the partition view contains the logical size of a single tile.


The resulting partition view can be loaded from using [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and stored to using [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).


The view memory options act on the computed index space of the partition view see [Tensor View](types.html#type-tensor-view) and [Partition View](types.html#type-partition-view) for detailed semantics.


#### Constraints


 - The operation is conditionally speculatablebased on the specific operands and attributes.
 - The operation may be speculatively executed without side effects.
 - The operation is pure and does not perform any memory side effects.


#### Examples


```
%tensor_view0 = make_tensor_view %ptr, shape=[8192, 8192, 64], strides=[524288,64,1]
  : tensor_view<8192x8192x64xf32, strides=[524288,64,1]>

// Creates a partition with 32-bit-indexed tiles of size (1024x1x32) over
// the provided tensor_view.
make_partition_view %tensor_view0 :
  partition_view<
    tile=(1024x1x32),
    tensor_view<8192x8192x64xf32, strides=[524288,64,1]>
  >

%s0 = constant <i32: 8192> : tile<i32>
%str0 = constant <i32: 524288> : tile<i32>

// These seems very wrong.
%tensor_view1 = make_tensor_view %ptr, shape=[%s0, 8192, 64], strides=[%str0, 64, 1]
  : tile<i32> -> tensor_view<?x8192x64xf32, strides=[?,64,1]>

// Creates a partition with 32-bit-indexed tiles of size (1024x1x32) over
// the provided tensor_view, with masking. The provided tensor_view has a
// dynamically-sized dimension.
make_partition_view %tensor_view1 :
  partition_view<tile=(1024x1x32), tensor_view<?x8192x64xf32, strides=[?,64,1]>>
```


See [cuda_tile.make_partition_view_0](appendix.html#example-cuda-tile-make-partition-view-0) for the full example listing.


### 8.11.5. cuda_tile.make_tensor_view


*Create :code:`tensor_view` from a pointer to global memory*


```
cuda_tile.make_tensor_view %base %dynamicShape %dynamicStrides
```


#### Parameters


 - base ([tile](types.html#type-tile)<[ptr](types.html#type-ptr)>) - The scalar base pointer to a portion of global memory. 13.1
 - dynamicShape ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)<[any](operations.html#type-any)>>) - The array of values representing the shape of the view, may be fully dynamic. 13.1
 - dynamicStrides ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)<[any](operations.html#type-any)>>) - The array of values representing the strides of the view, may be fully dynamic. 13.1


#### Results


 - result ([tensor_view](types.html#type-tensor-view)) - The constructed tensor_view. 13.1


#### Description


The `make_tensor_view` operation constructs a `tensor_view` from a global memory pointer, a dynamic shape and dynamic strides. See [Tensor View](types.html#type-tensor-view) for more details.


The constructor supports taking dynamic arrays for shapes and strides as part of the constructor enabling workloads to take global memory tensors of dynamic shape and strides. If these arguments are static they will be statically reflected in the type of the resulting `tensor_view`, if they are dynamic they will appear as `?` in the type. See below for concrete examples.


The `dynamicShape` and `dynamicStrides` operands are interpreted as unsigned integers.


#### Constraints


 - The operation must encode variadic operand segment sizes in attributes.
 - The operation is pure and does not perform any memory side effects.


#### Examples


```
// tensor_view to a scalar tile of f32
  %a0 = make_tensor_view %base,
      shape = [], strides = [] : tensor_view<f32>

  // tensor_view to a tile of static shape and strides
  %a1 = make_tensor_view %base,
      shape = [32, 32], strides = [32, 1]
      : tensor_view<32x32xf32, strides=[32,1]>

%sh0 = constant <i32: 32> : tile<i32>
%sh1 = constant <i32: 32> : tile<i32>
%st0 = constant <i32: 32> : tile<i32>
%st1 = constant <i32: 1> : tile<i32>

  // tensor_view to a tile with partially dynamic shape and strides
  // all dynamic values must be of the same type, here tile<i32>
  %a2 = make_tensor_view %base,
          shape = [%sh0, %sh1], strides = [%st0, %st1]
          : tile<i32> -> tensor_view<?x?xf32, strides=[?,?]>
```


See [cuda_tile.make_tensor_view_0](appendix.html#example-cuda-tile-make-tensor-view-0) for the full example listing.


### 8.11.6. cuda_tile.store_view_tko


*Stores a tile into a tile view*


```
cuda_tile.store_view_tko %memory_ordering_semantics %memory_scope %tile %view %index %token %optimization_hints
```


#### Parameters


 - memory_ordering_semantics ([MemoryOrderingSemantics](operations.html#op-attribute-cuda-tile-store-view-tko-memoryorderingsemantics-attr)) - The memory scope for the store operation. 13.1
 - memory_scope ([MemoryScope](operations.html#op-attribute-cuda-tile-store-view-tko-memoryscope-attr)) - The memory scope for the store operation. 13.1
 - tile ([tile](types.html#type-tile)) - The tile to store. 13.1
 - view ([view_type](operations.html#type-view-type)) - The view to store the tile to. 13.1
 - index ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)<[any](operations.html#type-any)>>) - The indices of the desired target tile within the view. 13.1
 - token ([token](operations.html#type-token)) - The optional token for operation ordering. 13.1
 - optimization_hints ([OptimizationHints](operations.html#op-attribute-cuda-tile-store-view-tko-optimizationhints-attr)) - Optimization hints for operation 13.1


#### Results


 - result_token ([token](operations.html#type-token)) - The result token for synchronization. 13.1


#### Description


The `store_view_tko` operation stores a tile to a view indexing into a tile view.


A view is mapping from view-space indices to a particular element in the view, each view type has a defined mapping from view-space indices to tiles produced from elements of the view.


For example, the [Partition View](types.html#type-partition-view) partitions a [Tensor View](types.html#type-tensor-view) into a grid of equally sized tiles. The view indexes one of the partitioned tiles in the grid.


For a given view the rank of the indices must match the rank of the view’s index space. The space of valid indices depends on which view is passed to the operation. For example the index space of a [Partition View](types.html#type-partition-view) is equal to the rank of the partitioned tiles.


The index space of the view is computed a function of the requested tile size and the shape of the view.


The `index` operands are interpreted as unsigned integers.


Out of bounds accesses are handled according to the semantics of [Partition View](types.html#type-partition-view).


The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](memory_model.html#section-memory-model) of the specification.


 - `weak` - No concurrent accesses to the source/destination location.
 - `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
 - `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then *happens before* is established.


Note: The following variants are not supported by this operation: `acquire`, `acq_rel`.


The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.


 - `tl_blk` - There may be concurrent accesses from within the same tile block.
 - `device` - There may be concurrent accesses from within the same device (i.e., GPU).
 - `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).


The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.


The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.


 - `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda_tile.entry](operations.html#op-cuda-tile-entry).
 - `allow_tma` - suggest whether to use TMA for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).
 - `latency` - latency hint for [cuda_tile.load_view_tko](operations.html#op-cuda-tile-load-view-tko) and [cuda_tile.store_view_tko](operations.html#op-cuda-tile-store-view-tko).


For example they can be annotated as:


```
optimization_hints=<
  sm_100 = {num_cta_in_cga = 8},
  sm_120 = {num_cta_in_cga = 16}
>
```


#### Constraints


 - The operation must encode variadic operand segment sizes in attributes.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
%tensor_view = make_tensor_view %ptr, shape=[8192, 128], strides=[128,1] :
  tensor_view<8192x128xf32, strides=[128,1]>

// This example uses the PartitionView on a 8192x128xf32 tensor_view,
// dividing the tensor_view in tiles of 64x64.
%view = make_partition_view %tensor_view :
  partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>

%c0 = constant <i32: 0> : tile<i32>
%c1 = constant <i32: 1> : tile<i32>

%tile = constant <f32: 0.0> : tile<64x64xf32>

// Store a tile at index (0, 0) in the view's index space.
// For this TilePartitionView, this is the rectangular tile such that
// X=[0,64) and Y=[0,64), in the coordinates of tiles.
%res_token0 = store_view_tko weak %tile, %view[%c0, %c0]
  : tile<64x64xf32>, partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> token

// Store a tile at index (0, 1) in the view's index space.
// For this PartitionView, this is the rectangular tile such that
// X=[0,64) and Y=[64,128), in the coordinates of tiles.
%res_token1 = store_view_tko weak %tile, %view[%c0, %c1]
  : tile<64x64xf32>, partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> token

// Same example as above but with input token.
%token = make_token : token
%res_token2 = store_view_tko weak %tile, %view[%c0, %c1] token = %token
  : tile<64x64xf32>, partition_view<tile=(64x64), tensor_view<8192x128xf32, strides=[128,1]>>, tile<i32> -> token
```


See [cuda_tile.store_view_tko_0](appendix.html#example-cuda-tile-store-view-tko-0) for the full example listing.


## 8.12. Miscellaneous


The set of miscellaneous operations in Tile IR are operations which do not have a specific category.


### 8.12.1. cuda_tile.assume


*Attach static information to an SSA value*


```
cuda_tile.assume %value %predicate
```


#### Parameters


 - value ([Any](operations.html#type-any)) - The value to attach the predicate to. 13.1
 - predicate ([AssumePredicate](operations.html#op-attribute-cuda-tile-assume-assumepredicate-attr)) - The predicate to attach to the value. 13.1


#### Results


 - result ([Any](operations.html#type-any)) - The value with the attached predicate. 13.1


#### Description


The `assume` operation passes through `value` as the result and attaches a predicate to it. The assumed predicate is a property of `result`.


This operation can be used to inject static information into the compiler, potentially resulting in more efficient code generation.


`predicate` must implement the `AssumePredicateAttrInterface`.


Note


`assume` does not check the correctness of the predicate. Incorrect predicates may inject incorrect static information and cause miscompilation. If an incorrect predicate is attached to an SSA value, the behavior of the program is undefined.


#### AssumePredicate Implementers


#### Bounded


```
#bounded<(lb|?), (ub|?)>
```


The `bounded` attribute must be used as a predicate for `cuda_tile.assume`. The predicated value must be a tile of integers.


`bounded` specifies a lower and upper bound for all elements of the predicated tile when interpreted as signed integers. Bounds are optional: it is possible to leave a bound unspecified, as indicated by “?” in the assembly format. E.g., `#bounded<0, ?>`. Both lower bound and upper bound are inclusive.


The lower bounds must be less than or equal to the upper bound. A lower/ upper bound that exceeds the range of valid values of the predicated value is invalid.


```
%1 = cuda_tile.assume #cuda_tile.bounded<0, ?>, %0
    : !cuda_tile.tile<4x8xi16>
```


See [cuda_tile.assume_example_Bounded_0](appendix.html#example-cuda-tile-assume-example-bounded-0) for the full example listing.


#### DivBy


```
div_by< $divisor (, every $every^ along $along)?>
```


The `div_by` attribute must be used as a predicate for `cuda_tile.assume` ops. The predicated value must be a `tile` of integers or pointers, or a `tensor_view`.


If the predicated value is a `tile`, the attribute indicates that some elements of the `tile` are divisible by `divisor`. If the predicated value is a `tensor_view` the attribute indicates that the base address of the `tensor_view` is divisible by `divisor`. `divisor` must be a positive power of `2`.


The `every` and `along` attributes control which elements are assumed to satisfy the divisibility property. When splitting the tensor in groups of size `every` along dimension `along`, the first element of each group is assumed to satisfy the divisibility property. The other elements are assumed to be monotonically increasing by `1` within the group. In case of a `tile` of pointers, the elements are assumed to be monotonically increasing by the byte width of the pointee type. The size of the last group may be smaller than `every`.


The `every` and `along` attributes are optional. When missing, they are assumed to have a default value of `1` and `0` in case of a `tile`. I.e., all elements of the `tile` are assumed to satisfy the divisibility property. (The value of `along` does not matter in that case.) If the predicated value is a `tensor_view` or a 0D `tile`, `every` and `along` cannot be used.


`every`, and `along` must be used together. If one is specified, so must be the other.


Note


If the predicated value is a tile of integers, `every` is a property of the signed interpretation of the integer values. Otherwise, it is a property of the unsigned integer interpretation. E.g., `every = 4` is incorrect for the following sequence of “i8” values (written in binary form) because they wrap around when interpreted as signed integers: `[01111110, 01111111, 10000000, 10000001]`. `every = 2` would be correct.


The examples below demonstrate tensors that satisfy the assumed properties.


```
// Example 1: Each pointer is divisible by 16.
// [ 0x10, 0x20, 0x80, 0x10, 0x0, 0x120, ... ]
%0 = cuda_tile.assume #cuda_tile.div_by<16>, %ptrs
    : !cuda_tile.tile<128x!cuda_tile.ptr<f32>>
// Note: Equivalent to #cuda_tile.div_by<16, every 1 along 0>.
```


See [cuda_tile.assume_example_DivBy_0](appendix.html#example-cuda-tile-assume-example-divby-0) for the full example listing.


```
// Example 2: Each integer is divisible by 4.
// [ 16, 24, 8, 4, 12, 12, 0, 16, ... ]
%0 = cuda_tile.assume #cuda_tile.div_by<4>, %t
    : !cuda_tile.tile<128xi32>
```


See [cuda_tile.assume_example_DivBy_1](appendix.html#example-cuda-tile-assume-example-divby-1) for the full example listing.


```
// Example 3: Group size [4].
// [7, 8, 9, 10, 23, 24, 25, 26, 0, 1, 2, 3, ...]
%0 = cuda_tile.assume #cuda_tile.div_by<1, every 4 along 0>, %t
    : !cuda_tile.tile<128xi32>
```


See [cuda_tile.assume_example_DivBy_2](appendix.html#example-cuda-tile-assume-example-divby-2) for the full example listing.


```
// Example 4: 2-d Group size [1, 4] with divisibility 4.
// [ [  4,  5,  6,  7, 12, 13, 14, 15 ],
//   [  8,  9, 10, 11, 24, 25, 26, 27 ],
//   [ 24, 25, 26, 27, 64, 65, 66, 67 ],
//   [  0,  1,  2,  3,  4,  5,  6,  7 ] ]
%0 = cuda_tile.assume #cuda_tile.div_by<4, every 4 along 1>, %t
    : !cuda_tile.tile<4x8xi32>
```


See [cuda_tile.assume_example_DivBy_3](appendix.html#example-cuda-tile-assume-example-divby-3) for the full example listing.


```
// Example 5: 2-d Group size [4, 1] with divisibility 32.
// Note that the elements within each column are monotonically increasing
// by the byte width of the pointee type f32, e.g., 0x20, 0x24, 0x28, 0x2c.
// [ [  0x20, 0x100,  0x40,  0x60,  0x40, 0x200, 0x340,  0x40 ],
//   [  0x24, 0x104,  0x44,  0x64,  0x44, 0x204, 0x344,  0x44 ],
//   [  0x28, 0x108,  0x48,  0x68,  0x48, 0x208, 0x348,  0x48 ],
//   [  0x2c, 0x10c,  0x4c,  0x6c,  0x4c, 0x20c, 0x34c,  0x4c ] ]
%0 = cuda_tile.assume #cuda_tile.div_by<32, every 4 along 0>, %ptrs
    : !cuda_tile.tile<4x8x!cuda_tile.ptr<f32>>
```


See [cuda_tile.assume_example_DivBy_4](appendix.html#example-cuda-tile-assume-example-divby-4) for the full example listing.


#### SameElements


```
#same_elements< $values >
```


The `same_elements` attribute must be used as a predicate for `cuda_tile.assume`. The predicated value must be a tensor of integers or pointers.


`same_elements` is specified for each dimension. A value of C for a dimension of size N indicates that, after dividing the respective dimension into N/C groups of size C, each group consists of the same elements. As N/C may not divide evenly, the last group may have fewer than C elements.


If the “same elements” property does not hold along a dimension, the respective value should be set to 1. `#cuda_tile.same_elements<[1, 1, ..., 1]>` is a correct predicate for any tensor of integers or pointers, where the number of ones matches the rank of the tensor. (Size-1 groups always have the same elements.)


```
// Integer tensor with same elements.
%0 = cuda_tile.constant <i16: [[0, 0, 0, 0, 10, 10, 10, 10],
                               [0, 0, 0, 0, 10, 10, 10, 10],
                               [5, 5, 5, 5, 93, 93, 93, 93],
                               [5, 5, 5, 5, 93, 93, 93, 93]]>
    : tile<4x8xi16>
%1 = cuda_tile.assume #cuda_tile.same_elements<[2, 4]>, %0
    : !cuda_tile.tile<4x8xi16>

// Pointer tensor with same elements.
%2 = cuda_tile.constant <i64: [[ 0,  0,  0,  0,  8,  8,  8,  8],
                               [ 0,  0,  0,  0,  8,  8,  8,  8],
                               [64, 64, 64, 64, 32, 32, 32, 32],
                               [64, 64, 64, 64, 32, 32, 32, 32]]>
    : tile<4x8xi64>
%3 = cuda_tile.bitcast %2
    : !cuda_tile.tile<4x8xi64>
      -> !cuda_tile.tile<!cuda_tile.ptr<f32>>
%4 = cuda_tile.assume #cuda_tile.same_elements<[2, 4]>, %3
    : !cuda_tile.tile<!cuda_tile.ptr<f32>>
```


See [cuda_tile.assume_example_SameElements_0](appendix.html#example-cuda-tile-assume-example-sameelements-0) for the full example listing.


#### Constraints


 - `value` and `result` must have the same shape and element type ([Any](operations.html#type-any)).
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
// Assume that all integers are divisible by 32.
%int_tile = constant <i16: [32, 64, 0, 0, 32, -32, 1024, 0]> : tile<8xi16>
%div_by_1 = assume div_by<32>, %int_tile : tile<8xi16>

// Assume that every 4th element (starting with element 0) along
// dimension 0 is divisible by 32 that and all integers are
// montonically increasing by 1 within each group of 4.
%int_tile_2 = constant <i16: [96, 97, 98, 99, 64, 65, 66, 67]> : tile<8xi16>
%div_by_2 = assume div_by<32, every 4 along 0>, %int_tile_2 : tile<8xi16>

// Assume that every rectangular chunk of size [1, 4, 2] has the same
// values.
%same_elem = assume same_elements<[1, 4, 2]>, %ptr_3d : tile<1x8x8xptr<f32>>

// Assume that every value is greater or equal to 5.
%int_tile_3 = constant <i16: [5, 9, 10, 11, 6, 5, 5, 7]> : tile<8xi16>
%bounded = assume bounded<5, ?>, %int_tile_3 : tile<8xi16>
```


See [cuda_tile.assume_0](appendix.html#example-cuda-tile-assume-0) for the full example listing.


### 8.12.2. cuda_tile.print_tko


*Print a formatted string (token-ordered)*


```
cuda_tile.print_tko %str %args %token
```


#### Parameters


 - str ([String](operations.html#type-string)) - The format string. 13.1
 - args ([Variadic](operations.html#type-variadic)<[tile](types.html#type-tile)>) - The arguments to format and print. 13.1
 - token ([token](operations.html#type-token)) - The optional token for operation ordering. 13.2


#### Results


 - result_token ([token](operations.html#type-token)) - The result token for synchronization. 13.2


#### Description


The `print_tko` operation prints a C-printf-style format string, interleaved with the given operands. The number of format expressions (starting with the `%` character) must match the number of operands. If a format expression is not applicable to its respective operand, then the output is undefined.


Token-ordered print operations are not constrained by program order. The compiler may reorder them (i.e., move them earlier or later in the program) unless further constrained by tokens.


This operation is meant for debugging. Its implementation is not optimized for performance, so it should not be used in production mode. Prints are not guaranteed to be atomic. I.e., the output of prints that execute simultaneously may be interleaved.


Note


This op was renamed from `print` to `print_tko` in 13.2. The op code did not change.


#### Constraints


 - The operation must encode variadic operand segment sizes in attributes.
 - The operation’s result type may be inferred from its operands and attributes.


#### Examples


```
print_tko "Hello world: %f\n", %arg : tile<4xf32> -> token
print_tko "%+08.3f", %arg : tile<4xf32> -> token
```


See [cuda_tile.print_tko_0](appendix.html#example-cuda-tile-print-tko-0) for the full example listing.