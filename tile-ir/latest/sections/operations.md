# 8\. Operations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#operations "Link to this heading")

This section describes a complete and categorized list of all **Tile IR** instructions names, signatures, and semantics.

## 8.1. Meta Types[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#meta-types "Link to this heading")

Operations have arguments which are **Tile IR** values with **Tile IR** types but many operations have immediate or static arguments which correspond to attributes in the MLIR dialect. These **meta types** are not representable in the **Tile IR** type system but are used to construct **Tile IR** programs and only present at compile time. Operations in the specification are described abstractly in both the **Tile IR** IR and bytecode independent of the MLIR or bytecode encoding. For each of these types we provide a definition of them below and link to them from each operation.

Note

The convention is that the meta types are capitalized and **Tile IR** types are snake cased.

The convention is that the meta types are capitalized and the native **Tile IR** types are camel cased are snake cased.

### 8.1.1. Symbol[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#symbol "Link to this heading")

`Symbol` a symbol in the program, begins with `@` and uniquely identifies a symbol in the program.

### 8.1.2. Flag[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#flag "Link to this heading")

`Flag` a boolean value that can be used to control the behavior of an operation.

### 8.1.3. Token[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#token "Link to this heading")

Token represents a memory ordering token that can be used to control the ordering of memory operations.

### 8.1.4. Variadic[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#variadic "Link to this heading")

`Variadic` represents an argument which can accept a statically sized, but variable, number of arguments.

### 8.1.5. Any[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#any "Link to this heading")

`Any` represents a value of any valid **Tile IR** type.

### 8.1.6. Name[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#name "Link to this heading")

`Name` represents a name in the program, begins with `#` and uniquely identifies a name in the program.

### 8.1.7. Type[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type "Link to this heading")

`Type` represents a **Tile IR** type and are attached as attributes to operations which define IR items.

### 8.1.8. Array[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#array "Link to this heading")

`Array` represents a statically sized array of values that can be passed to attributes.

### 8.1.9. String[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#string "Link to this heading")

`String` represents a string value that can be passed to attributes.

### 8.1.10. bool[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#bool "Link to this heading")

`bool` represents a boolean value that can be passed to attributes.

### 8.1.11. DenseConstant[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#denseconstant "Link to this heading")

`DenseConstant` represents a dense constant value that can be passed to attributes.

## 8.2. Operation Design Considerations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#operation-design-considerations "Link to this heading")

The design of **Tile IR** has a set of design considerations that apply to all operations in the dialect this section introduces some of the common design considerations that apply to all operations, or to classes of operations generically.

### 8.2.1. Explicit Broadcast[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#explicit-broadcast "Link to this heading")

There are no implicit broadcast performed by operations in the **Tile IR** dialect all operations that require operands of the same shape must be explicitly broadcasted. For example to use the [cuda\_tile.offset](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-offset) operation to add an offset tile to a pointer, the pointer and offset must be reshaped or broadcasted to have the same shape using the [cuda\_tile.reshape](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-reshape) or [cuda\_tile.broadcast](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-broadcast) operations.

### 8.2.2. Distinct Floating-Point and Integer Operations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#distinct-floating-point-and-integer-operations "Link to this heading")

Numeric ooerations are split across integer and floating-point types due to differences in flags such as rounding modes, `NaN` handling, and fast math.

For example, the [cuda\_tile.addf](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-addf) operation supports a rounding attribute, but the addi operation does not.

### 8.2.3. Explicit Overflow Annotations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#explicit-overflow-annotations "Link to this heading")

Some operations such as [cuda\_tile.addi](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-addi) support an explicit overflow annotation that expresses the expected overflow behavior of the operation.

These attributes serve as assumptions that an implementation may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

We recommend that generators of **Tile IR** programs utilize these annotations to help the implementation reason about the overflow behavior of the operation, enabling extra optimization opportunities.

## 8.3. Core[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#core "Link to this heading")

### 8.3.1. cuda\_tile.broadcast[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-broadcast "Link to this heading")

_Broadcast tile to new shape_

cuda\_tile.broadcast %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#parameters "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The tile to broadcast. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#results "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The broadcasted tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#description "Link to this heading")

The `broadcast` operation expands each unary (`1`) dimension in the input tile by duplicating the data along that dimension.

Expansion happens only for dimensions of size one that are stretched or “copied” to match the size of the dimension implied by the result type of the operation. The operation does not change the rank of the source tile. Any change to the rank of the source tile must be made using reshape-like operations before broadcasting.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#constraints "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same element type (tile).
-   `source` and `result` must have the same rank.

### 8.3.2. cuda\_tile.cat[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-cat "Link to this heading")

_Concatenate tiles along specified dimension_

cuda\_tile.cat %lhs %rhs %dim

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id1 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The right hand side operand. 13.1
-   **dim** ([i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)) - The dimension along which to concatenate. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id2 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The concatenated result tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id3 "Link to this heading")

The `cat` operation concatenates the two input tiles. The input tiles must have the same shape in all but the concatenating dimension. Concatenation happens along the dimension specified by the the attribute `dim` the resulting dimension is the sum of the the two input tiles concatenating dimension.

cat(x,y,dimcat)\[i→\]\={x\[...,icat,...,in\]if icat<dcaty\[...,icat−dcat,...,in\]if icat≥dcat

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id4 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same rank.
-   `lhs`, `rhs` and `result` must have the same element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)).

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#examples "Link to this heading")

// A valid invocation of cat.
%0 \= cat %arg0, %arg1 dim \= 1
  : tile<2x4xf32\>, tile<2x4xf32\> \-> tile<2x8xf32\>

// >>> %arg0 = tile(\[\[ A, B, C \],
//                   \[ D, E, F \]\])
// >>> %arg1 = tile(\[\[ 1, 2, 3 \],
//                   \[ 4, 5, 6 \]\])
// >>> %0 = tile(\[\[ A, B, C, 1, 2, 3 \],
//                \[ D, E, F, 4, 5, 6 \]\])

// A valid invocation of cat.
%1 \= cat %arg0, %arg1 dim \= 0
  : tile<2x4xf32\>, tile<2x4xf32\> \-> tile<4x4xf32\>

// >>> %arg0 = tile(\[\[ A, B, C \],
//                   \[ D, E, F \]\])
//
// >>> %arg1 = tile(\[\[ 1, 2, 3 \],
//                   \[ 4, 5, 6 \]\])
//
// >>> %1 = tile(\[\[ A, B, C \],
//                \[ D, E, F \],
//                \[ 1, 2, 3 \],
//                \[ 4, 5, 6 \]\])

Copy to clipboard

See [cuda\_tile.cat\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-cat-0) for the full example listing.

### 8.3.3. cuda\_tile.constant[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-constant "Link to this heading")

_Construct a constant tile_

cuda\_tile.constant %value

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id5 "Link to this heading")

-   **value** ([DenseConstant](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-denseconstant)) - The constant value to create. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id6 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The constant tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id7 "Link to this heading")

The `constant` operation creates a tile initialized by `$value`.

There are two main forms of using the operation:

-   One where the value is a single constant specified by `<D: c>` and the tile is filled with identical values for all elements with element type `D`.
-   One where the value is a list of constants specified by `dense<D: [c0, c1, c2, ...]>` and the constant value’s shape must match the tile’s shape with the element type `D`.

The annotated type of the tile constrains its rank, shape, and element type.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id8 "Link to this heading")

-   Operation must have zero operands and be foldable at compile time.
-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `value` and `result` must have the same shape and element type ([DenseConstant](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-denseconstant)).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id9 "Link to this heading")

%c0 \= constant <i32: 0\> : tile<i32\>
%c1 \= constant <i64: 1\> : tile<i64\>
%c2 \= constant <i32: \[0, 1, 2, 3\]\> : tile<4xi32\>
%c3 \= constant <f32: 0.0\> : tile<2x4xf32\>
%c4 \= constant <f64: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf64\>

Copy to clipboard

See [cuda\_tile.constant\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-constant-0) for the full example listing.

### 8.3.4. cuda\_tile.entry[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-entry "Link to this heading")

_Define a tile kernel_

cuda\_tile.entry %sym\_name %function\_type %arg\_attrs %res\_attrs %optimization\_hints

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id10 "Link to this heading")

-   **sym\_name** ([Symbol](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-symbol)) - The name of the function. 13.1
-   **function\_type** ([Type](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-type)) - The type of the function. 13.1
-   **arg\_attrs** ([Attributes](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-attributes)) - The argument attributes of the function: none of these are supported by CUDA Tile IR at the moment. 13.1
-   **res\_attrs** ([Attributes](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-attributes)) - The result attributes of the function: none of these are supported by CUDA Tile IR at the moment. 13.1
-   **optimization\_hints** ([OptimizationHints](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-entry-optimizationhints-attr)) - Compiler architecture-specific optimization hints 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id11 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id12 "Link to this heading")

The `entry` operation defines a tile kernel; a kernel is a function that can serve as the program entry point. It has a unique name per-module. A kernel can not return any value. It must be launched from the host side using `cuLaunchKernel` or similar CUDA runtime API functions.

Tile kernels require that the user specifies the 3-d grid dimensions at launch which defines the number of tile blocks (or kernel instances) that will execute the kernel in parallel.

For detailed semantics of tile kernels see [Tile Kernel](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/semantics.html#sub-sec-tile-kernel).

The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.

The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.

-   `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda\_tile.entry](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-entry).
-   `allow_tma` - suggest whether to use TMA for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).
-   `latency` - latency hint for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).

For example they can be annotated as:

optimization\_hints\=<
  sm\_100 \= {num\_cta\_in\_cga \= 8},
  sm\_120 \= {num\_cta\_in\_cga \= 16}
\>

Copy to clipboard

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id13 "Link to this heading")

-   Operation must be a symbol in the global symbol table.
-   Operation must implement callable target interface.
-   Operation must implement function-like behavior interface.
-   Region must not capture SSA values defined above the operation.
-   Operation must provide custom parsing and printing methods.
-   Each region must contain exactly one block.

### 8.3.5. cuda\_tile.extract[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-extract "Link to this heading")

_Extract a subtile from a tile_

cuda\_tile.extract %source %indices

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id14 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The source tile to extract from. 13.1
-   **indices** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>\>) - The indices of the slice to extract. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id15 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The extracted subtile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id16 "Link to this heading")

The `extract` operation extracts a subtile from the given source tile.

The shape of the result tile must divide the shape of the source tile evenly e.g., `tile<4xf32>` is a valid extraction from `tile<8xf32>`, but `tile<3xf32>` is not.

The `$indices` indicate the number of the slice to extract, but _importantly_ not the offsets used to construct the subtile for extraction. The semantics of extract means that only full size slices can be extracted.

Slices of a source tile with the same shape are non-overlapping by definition for unique indices.

The `indices` operands are interpreted as unsigned integers.

Warning

If the `indices` specify a non-existent (i.e., out-of-bounds) slice, the behavior of the operation is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id17 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same rank.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id18 "Link to this heading")

// Extract a subtile from %t at dim\_0 = \[4;8) and dim\_1 = \[4;6).
%c1 \= constant <i32: 1\> : tile<i32\>
%c2 \= constant <i32: 2\> : tile<i32\>
%t \= constant <f32: 0.0\> : tile<32x8xf32\>
// Valid indices are: \[ {0, 1, 2, 3, 4, 5, 6, 7}, {0, 1, 2, 3} \]
%0 \= extract %t\[%c1, %c2\]
    : tile<32x8xf32\> \-> tile<4x2xf32\>

Copy to clipboard

See [cuda\_tile.extract\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-extract-0) for the full example listing.

### 8.3.6. cuda\_tile.get\_global[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-get-global "Link to this heading")

_Get a pointer to a global variable_

cuda\_tile.get\_global %name

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id19 "Link to this heading")

-   **name** ([Symbol](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-symbol)) - The name of the global variable. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id20 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)\>) - The result of the get\_global operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id21 "Link to this heading")

The `get_global` operation returns a pointer to the specified `global` variable. A global variable is a form of static global memory allocation that can be declared using the [cuda\_tile.global](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-global) operation.

The element type of the returned pointer will be of the same type as the element type of the declared global variable.

For detailed semantics of global variables see [Global Variable](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/semantics.html#sub-sec-tile-global).

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id22 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id23 "Link to this heading")

global @val <f32: \[0.1, 0.2, 0.3, 0.4\]\> : tile<4xf32\>

entry @example() {
  %ptr \= get\_global @val : tile<ptr<f32\>>
  return
}

Copy to clipboard

See [cuda\_tile.get\_global\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-get-global-0) for the full example listing.

### 8.3.7. cuda\_tile.get\_num\_tile\_blocks[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-get-num-tile-blocks "Link to this heading")

_Get total number of tile blocks_

cuda\_tile.get\_num\_tile\_blocks

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id24 "Link to this heading")

No parameters.

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id25 "Link to this heading")

-   **gridSize\_x** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The number of tile blocks in dimension `x`. 13.1
-   **gridSize\_y** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The number of tile blocks in dimension `y`. 13.1
-   **gridSize\_z** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The number of tile blocks in dimension `z`. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id26 "Link to this heading")

The `get_num_tile_blocks` operation queries the total number of tile blocks in the form of a 3-tuple specifying the extent of each grid dimension.

A tile `id` is a coordinate in 3-space and therefore the must also be a 3-tuple containing the extent of each dimension: `x`, `y` and `z`.

When launching 1- or 2-dimensional grids, the unspecified dimensions will have a cardinality of 1.

For example if the grid used to launch the kernel is `(1024, 1024)` then the result of this operation will be `(1024, 1024, 1)`.

Note

**Grid Dimension Limitation**: Grid dimensions are limited to 2^24-1 (16,777,215) per axis. Larger dimensions may result in incorrect tile block ID calculations. Use multiple kernel launches for larger workloads.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id27 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id28 "Link to this heading")

entry @example() {
  %x, %y, %z \= get\_num\_tile\_blocks : tile<i32\>
  // print "x: %, y: %, z: %\\n", %x, %y, %z : tile<i32>, tile<i32>, tile<i32>
}

Copy to clipboard

See [cuda\_tile.get\_num\_tile\_blocks\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-get-num-tile-blocks-0) for the full example listing.

### 8.3.8. cuda\_tile.get\_tile\_block\_id[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-get-tile-block-id "Link to this heading")

_Get the currently executing tile block coordinates_

cuda\_tile.get\_tile\_block\_id

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id29 "Link to this heading")

No parameters.

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id30 "Link to this heading")

-   **blockId\_x** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The tile block ID for dimension `x`. 13.1
-   **blockId\_y** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The tile block ID for dimension `y`. 13.1
-   **blockId\_z** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The tile block ID for dimension `z`. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id31 "Link to this heading")

`get_tile_block_id` returns a 3-d tile block coordinates (or ID) of the currently executing tile block.

A tile ID has three dimensions: `x`, `y`, and `z`. This operation returns all three of them simultaneously. The value of each dimension returned by this operation is between `0` (including) and the value returned by `get_num_tile_blocks` for the respective axis (excluding), represented by the inclusive interval `[0, get_num_tile_blocks(dim) - 1]` . Grid dimensions unspecified at kernel launch (i.e., a 1-d or 2-d grid) will always be `0` for all tile blocks.

Note

**Grid Dimension Limitation**: Grid dimensions are limited to 2^24-1 (16,777,215) per axis. Larger dimensions may result in incorrect tile block ID calculations. Use multiple kernel launches for larger workloads.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id32 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   Operation must infer result types from operands and attributes.

### 8.3.9. cuda\_tile.global[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-global "Link to this heading")

_Allocate static global memory_

cuda\_tile.global %sym\_name %value %alignment

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id33 "Link to this heading")

-   **sym\_name** ([Symbol](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-symbol)) - The name of the global variable. 13.1
-   **value** ([DenseConstant](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-denseconstant)) - The value to initialize the allocation with. 13.1
-   **alignment** ([i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)) - The alignment of the buffer. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id34 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id35 "Link to this heading")

The `global` operation statically allocates a mutable 1-dimensional location in global memory and initializes it using `value`. The initialization of the allocation is performed at [CUDA module](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g9e4ef4dcfba4662b2299acb8d049a1ef) load time. The lifetime of the allocation is the same as the lifetime of the module.

The allocation may be read or written to by first using [cuda\_tile.get\_global](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-global) to obtain a pointer to the the memory and then read using [cuda\_tile.load\_ptr\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-ptr-tko) or written to using [cuda\_tile.store\_ptr\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-ptr-tko).

The initial values are stored in memory in linear order, so the pointer returned by [cuda\_tile.get\_global](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-get-global) points to the first element, and offsetting the pointer by x would allow to load element at position x.

`global` operations must be directly nested within the **Tile IR** module. They cannot be defined inside functions. As globals are defined at the module scope their names are globally unique symbols and must not collide with any other symbol in the module.

For more detailed semantics of global variables see [Global Variable](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/semantics.html#sub-sec-tile-global).

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id36 "Link to this heading")

-   Operation must be a symbol in the global symbol table.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id37 "Link to this heading")

global @val alignment \= 128 <f32: \[0.1, 0.2, 0.3, 0.4\]\> : tile<4xf32\>
entry @example() {}

Copy to clipboard

See [cuda\_tile.global\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-global-0) for the full example listing.

### 8.3.10. cuda\_tile.iota[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-iota "Link to this heading")

_Generate a 1-d tile range from 0 to n-1_

cuda\_tile.iota

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id38 "Link to this heading")

No parameters.

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id39 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the iota operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id40 "Link to this heading")

The `iota` operation generates a 1-d tile with a sequence of integer values. The starting value is `0` and the stride is `1`. If the shape of the result tile is `(n)`, then the generated values are `[0, n - 1]`.

iota(n)i\=ifor i∈\[0,n−1\]

The result values should be interpreted as unsigned integers.

Note

The number of elements in the result tile must not exceed the maximum value that the element type can express.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id41 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.3.11. cuda\_tile.module[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-module "Link to this heading")

_Top-level module containing a series of defined items._

cuda\_tile.module %sym\_name

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id42 "Link to this heading")

-   **sym\_name** ([Symbol](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-symbol)) - The name of the module. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id43 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id44 "Link to this heading")

A `module` operation represents a single compilation unit and contains zero or more items (global variables, functions, or kernels).

For detailed description of the semantics of modules, and the full definition of each item type see [Modules](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/semantics.html#sub-sec-modules).

The `module` operation is the top-level operation in a **Tile IR** module and must contain only **Tile IR** operations and no other dialects.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id45 "Link to this heading")

-   Region must not capture SSA values defined above the operation.
-   Operation must provide custom parsing and printing methods.
-   All regions must have zero arguments.
-   Each region must contain exactly one block.
-   Operation must define a symbol scope.
-   Regions must not require explicit terminator operations.
-   Operation must specify whether regions are SSACFG or Graph kind.
-   Operation must contain only dataflow Graph regions.

### 8.3.12. cuda\_tile.offset[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-offset "Link to this heading")

_Offsets a tile of pointers_

cuda\_tile.offset %ptr %offset

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id46 "Link to this heading")

-   **ptr** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The base pointer tile to advance. 13.1
-   **offset** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The offset tile to add to the pointer. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id47 "Link to this heading")

-   **result** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The resulting pointer tile after advancement. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id48 "Link to this heading")

`offset` advances a tile of pointers. It takes `ptr` as base and `offset` as increment, and performs element-wise addition of `ptr` by `offset`:

offset(ptr,offset)i\=ptri+offseti×bitwidth

result\[i,j\] \= ptr\[i,j\] + offset\[i,j\] \* bitwidth

Copy to clipboard

`ptr` is interpreted as an unsigned integer. `offset` is interpreted as a signed integer. `bitwidth` is the storage bitwidth of the pointee type. The multiplication must not overflow (wrap-around) in a signed sense. The addition must not overflow (wrap-around) in an unsigned sense. In case of an overflow, the result is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id49 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   Operation must apply element-wise to its operands.
-   `ptr`, `offset` and `result` must have the same shape.
-   `result` and `ptr` must have the same shape and element type ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)).
-   Operation must infer result types from operands and attributes.

### 8.3.13. cuda\_tile.permute[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-permute "Link to this heading")

_Permute tile dimensions_

cuda\_tile.permute %source %permutation

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id50 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The input tile. 13.1
-   **permutation** ([Array](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-array)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The permutation of the dimensions. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id51 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The permuted tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id52 "Link to this heading")

Permute the dimensions of the input tile `source` according to the `permutation` array. The `permutation` array is a list of integers that specify the new order of the dimensions.

For example, if the input tile has shape `[2, 4, 8]`, and the permutation is `[2, 0, 1]`, the output tile will have shape `[8, 2, 4]`.

This operation logically is a change in the indexing of the tile.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id53 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)).
-   `source` and `result` must have the same rank.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id54 "Link to this heading")

%arg0 \= constant <f16: 0.0\> : tile<2x4x8xf16\>
%0 \= permute %arg0 \[2, 0, 1\] : tile<2x4x8xf16\> \-> tile<8x2x4xf16\>

Copy to clipboard

See [cuda\_tile.permute\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-permute-0) for the full example listing.

### 8.3.14. cuda\_tile.reduce[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-reduce "Link to this heading")

_Variadic tile reduction across dimensions_

cuda\_tile.reduce %operands %dim %identities

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id55 "Link to this heading")

-   **operands** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)\>) - The set of tiles to reduce. 13.1
-   **dim** ([i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)) - The index of the dimension to perform reduction on. 13.1
-   **identities** ([Array](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-array)) - The reduction identities for each operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id56 "Link to this heading")

-   **results** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)\>) - The set of reduced tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id57 "Link to this heading")

The `reduce` operation applies a custom reduction function along a specified dimension of one or more input tiles, producing the same number of output tiles.

The reduction function must be an associative operation defined within the `reduce` operation’s region. A single reduction operation can reduce over any number of input tiles in parallel, producing a reduced output tile for each.

Note

Only pure operations are allowed in the body of `reduce`.

All input tiles must have the same shape. The output tiles will have a matching shape in every dimension except the one being reduced, which is removed.

For each input tile, a constant identity value must be provided that matches the element type of the input tile. Identity `i` of `identities` corresponds to input tile `i` of `operands`. The correct identity value is a property of the reduction function in the `body`. (For example, if the reduction function performs `min`, the identity is `+inf`, while if the reduction function performs a `sum`, the identity is `0`.)

The reduction function must expect `2N` arguments, where `N` is the number of input tiles. Each pair of reduction arguments `2i` and `2i+1` will correspond to the `i`\-th input tile. The first argument of each pair is an element of the input tile; the second is the accumulator from all prior reductions along the specified dimension. This second value might be input element, the identity value, or the result of a previous reduction iteration. The reduction function should yield the new accumulator value for each input tile.

Note

There are no guarantees on the order of element reduction along the specified dimension. However, the result is deterministic across different runs of the same kernel on the same device.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id58 "Link to this heading")

-   Operation must provide custom parsing and printing methods.
-   Operation effects must include all nested operations’ effects.
-   All operands must have identical shapes.
-   Each region must contain exactly one block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id59 "Link to this heading")

%input \= constant <f32: 0.0\> : tile<8xf32\>
%0 \= reduce %input dim\=0 identities\=\[0.000000e+0 : f32\] : tile<8xf32\> \-> tile<f32\>
  (%input\_arg: tile<f32\>, %input\_accum: tile<f32\>) {
    %add\_result \= addf %input\_arg, %input\_accum : tile<f32\>
    yield %add\_result : tile<f32\>
  }

Copy to clipboard

See [cuda\_tile.reduce\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-reduce-0) for the full example listing.

%input \= constant <f32: 0.0\> : tile<8x64xf32\>
%0 \= reduce %input dim\=1 identities\=\[0.000000e+0 : f32\] : tile<8x64xf32\> \-> tile<8xf32\>
  (%input\_arg: tile<f32\>, %input\_accum: tile<f32\>) {
    %add\_result \= addf %input\_arg, %input\_accum : tile<f32\>
    yield %add\_result : tile<f32\>
  }

Copy to clipboard

See [cuda\_tile.reduce\_1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-reduce-1) for the full example listing.

### 8.3.15. cuda\_tile.reshape[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-reshape "Link to this heading")

_Reshape tile dimensions_

cuda\_tile.reshape %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id60 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The source tile to reshape. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id61 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The reshaped tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id62 "Link to this heading")

The `reshape` operation changes the shape of the `source` operand. `reshape` is only a change in the indexing of the tile. The number of elements and element type must remain unchanged.

0-d tiles (i.e., scalars) contain precisely one element and thus are the one exception where a 0-d tile can be reshaped to shape where the `size(shape) == 1`.

Conceptually reshaping a tile is equivalent to first creating a 1-d tile from the data of the source assuming a row-major layout and then converting the 1-d tile into the new shape in a row-major layout.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id63 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same element type (tile).

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id64 "Link to this heading")

%cst \= constant <i8: 0\> : tile<i8\>
%0 \= reshape %cst
    : tile<i8\> \-> tile<1x1x1xi8\>

%t \= constant <f32: 0.0\> : tile<8x2xf32\>
%1 \= reshape %t
    : tile<8x2xf32\> \-> tile<2x2x4x1xf32\>

Copy to clipboard

See [cuda\_tile.reshape\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-reshape-0) for the full example listing.

  %cst \= constant <i32: \[\[0, 1, 2, 3\], \[4, 5, 6, 7\]\]\>
      : tile<2x4xi32\>
  %r0 \= reshape %cst
: tile<2x4xi32\> \-> tile<2x2x2xi32\>

// Step 1: Turn source into 1D tile. Use row-major by convention.
// %tmp: \[0, 1, 2, 3, 4, 5, 6, 7\]
%tmp \= reshape %cst
    : tile<2x4xi32\> \-> tile<8xi32\>

// Step 2: Turn 1D tile into result tile. Use row-major by convention.
// %r: \[\[\[0, 1\], \[2, 3\]\], \[\[4, 5\], \[6, 7\]\]\]
%r1 \=  reshape %tmp
        : tile<8xi32\> \-> tile<2x2x2xi32\>

Copy to clipboard

See [cuda\_tile.reshape\_1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-reshape-1) for the full example listing.

### 8.3.16. cuda\_tile.scan[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-scan "Link to this heading")

_A parallel prefix sum operation_

cuda\_tile.scan %operands %dim %reverse %identities

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id65 "Link to this heading")

-   **operands** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)\>) - The a set of tiles to scan. 13.1
-   **dim** ([i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)) - The index of the dimension along which to scan. 13.1
-   **reverse** ([bool](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-bool)) - Whether to scan in reverse order. 13.1
-   **identities** ([Array](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-array)) - The identities of the scan operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id66 "Link to this heading")

-   **results** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)\>) - The resulting tiles from the scan operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id67 "Link to this heading")

The `scan` operation computes an inclusive parallel prefix along a given dimension of the input tiles using a binary associative function and an identity.

The `scan` operation applies a scan function defined over a tile of elements for a given type, utilizing an associative operation and an identity value. It operates on `operands` and `identities` across the specified `dim`, producing new `results` tile values. The exact evaluation order within each prefix is implementation-defined but the result remains deterministic across different runs of the same kernel on the same device.

Note

Only pure operations are allowed in the body of `scan`.

scan(X,dim,identity,f)i1,…,id\[j\]\=fold(f,identity,(Xi1,…,idim−1,0,idim+1,…,id,…,Xi1,…,idim−1,j,idim+1,…,id))

The scan preserves all intermediate accumulator values:

result\[0\]\=f(identity,X\[…,0,…\])result\[1\]\=f(result\[0\],X\[…,1,…\])⋮result\[j\]\=f(result\[j−1\],X\[…,j,…\])

When `reverse` is `true`, the prefix is taken in decreasing index order. Let N be the size of the scanned dimension; then:

scanrev(X)\[j\]\= fold(f,identity,(X\[…,N−1,…\],…,X\[…,j,…\]))

The `identities` attribute is a list of identity elements for each input tile; the identity at position `i` binds with the operand tile at the same position. The correct identity is a property of the scan function in the `body` (e.g., `sum` uses 0, `prod` uses 1, `min` uses +inf, `max` uses -inf).

The `body` region represents the binary associative operation. The region must contain **Tile IR** operations with 0-rank tile types. Region arguments are bound in operand order as `[op_0_current_iter, op_0_prev_iter, op_1_current_iter, op_1_prev_iter, ...]`, where `op_i_current_iter` is the current element along `dim` and `op_i_prev_iter` is the running accumulator for operand `i`. On the first step, the accumulator is the corresponding identity element.

Note

Associativity of the binary operation permits the compiler to reorganize the applications of the operation to achieve efficient parallel prefix scans on the GPU.

Warning

The scan operation is restricted to only support single tile input.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id68 "Link to this heading")

-   Operation must provide custom parsing and printing methods.
-   Operation effects must include all nested operations’ effects.
-   All operands must have identical shapes.
-   Each region must contain exactly one block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id69 "Link to this heading")

%input \= constant <f32: 0.0\> : tile<8x16xf32\>
%result \= scan %input dim\=1 reverse\=false identities\=\[1.0 : f32\] : tile<8x16xf32\> \-> tile<8x16xf32\>
(%acc: tile<f32\>, %elem: tile<f32\>) {
  %prod \= mulf %acc, %elem rounding<nearest\_even\>: tile<f32\>
  yield %prod : tile<f32\>
}

Copy to clipboard

See [cuda\_tile.scan\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-scan-0) for the full example listing.

### 8.3.17. cuda\_tile.select[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-select "Link to this heading")

_Select values based on condition_

cuda\_tile.select %cond %val\_if\_true %val\_if\_false

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id70 "Link to this heading")

-   **cond** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The condition tile. 13.1
-   **val\_if\_true** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The value if true tile. 13.1
-   **val\_if\_false** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The value if false tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id71 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The tile of selected values. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id72 "Link to this heading")

The `select` op chooses values based on the binary conditions supplied as the `cond` operand. The `val_if_true` operand contains the value(s) to use if the condition is 1. The `val_if_false` operand contains the value(s) to use if the condition is 0. The choice is made element-wise according to the values in the condition tile.

select(cond,x,y)i\={xiif condi\=1yiif condi\=0

All tiles must have the same shape. The tiles `val_if_true`, `val_if_false`, and the result must have the same element type. The `cond` tile must be a tile of `i1` values.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id73 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `val_if_true`, `val_if_false` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)).
-   Operation must infer result types from operands and attributes.

## 8.4. Conversions[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#conversions "Link to this heading")

There are no implicit type conversions in **Tile IR** thus we expose a set of explicit conversion operations for interconverting between types which have compatible representations or rules for conversion.

[cuda\_tile.bitcast](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-bitcast) preserves the contents of the input but allows for changing of element types, [cuda\_tile.exti](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-exti) and [cuda\_tile.trunci](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-trunci) change the width of integer tiles, [cuda\_tile.ftoi](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-ftoi) and [cuda\_tile.itof](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-itof) convert floating-point tiles to integer tiles and vice versa, and [cuda\_tile.ftof](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-ftof) converts between different floating-point types.

For more details on conversions and their rules see the individual operation’s documentation.

### 8.4.1. cuda\_tile.bitcast[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-bitcast "Link to this heading")

_Bitcast a tile from one element type to another_

cuda\_tile.bitcast %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id74 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The source tile to cast. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id75 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The casted tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id76 "Link to this heading")

The `bitcast` operation casts the input tile from one element type to another without modifying the underlying bits.

Only non-pointer types of the same bit width are allowed (e.g., `i32` to `f32`). Pointer types must use [cuda\_tile.ptr\_to\_int](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-ptr-to-int) or [cuda\_tile.int\_to\_ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-int-to-ptr) instead.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id77 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.2. cuda\_tile.exti[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-exti "Link to this heading")

_Extend the width of an integer tile_

cuda\_tile.exti %from %signedness

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id78 "Link to this heading")

-   **from** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input integer tile to extend. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-exti-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id79 "Link to this heading")

-   **to** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The extended integer tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id80 "Link to this heading")

The `exti` operation converts a tile of integers of a given width to a strictly larger width. Zero-extension is used for `unsigned` integers and sign-extension is used for `signed` integers.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id81 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.3. cuda\_tile.ftof[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-ftof "Link to this heading")

_Convert between floating-point types_

cuda\_tile.ftof %from %rounding\_mode

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id82 "Link to this heading")

-   **from** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-ftof-roundingmode-attr)) - The rounding mode for the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id83 "Link to this heading")

-   **to** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result floating-point tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id84 "Link to this heading")

The `ftof` operation converts a tile of a given floating-point element type into one of a different floating-point element type (for example, from `f32` to `f64`).

The source type and the result type must be different.

The `rounding_mode` attribute specifies the rounding behavior for the operation. Only `NEAREST_EVEN` rounding mode is supported.

Warning

Different floating-point types have different conversion behaviors for out-of-finite-range values and special values. See [Floating-Point Conversion: Special Value and Saturation Behavior](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#table-float-conversion-semantics) for more details.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id85 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.4. cuda\_tile.ftoi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-ftoi "Link to this heading")

_Convert a tile from floating-point values to integer values_

cuda\_tile.ftoi %from %signedness %rounding\_mode

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id86 "Link to this heading")

-   **from** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-ftoi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-ftoi-roundingmode-attr)) - The rounding mode for the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id87 "Link to this heading")

-   **to** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result integer tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id88 "Link to this heading")

The `ftoi` operation converts a floating-point tile into an integer tile.

In contrast to a [cuda\_tile.bitcast](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-bitcast) which is bits preserving, this preserves the numerical value of the tile, rounded towards zero to the nearest integer of the provided type.

The `rounding_mode` attribute specifies the rounding behavior for the operation. Only `NEAREST_INT_TO_ZERO` rounding mode is supported.

Warning

If the input floating-point value, after being rounded, is outside the (signed or unsigned) range of the target integer type, the closest representable value is used instead. `NaN` values are converted to 0. Input `Inf` values are undefined behavior.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id89 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.5. cuda\_tile.itof[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-itof "Link to this heading")

_Convert integer to floating-point_

cuda\_tile.itof %from %signedness %rounding\_mode

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id90 "Link to this heading")

-   **from** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input integer tile. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-itof-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-itof-roundingmode-attr)) - The rounding mode for the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id91 "Link to this heading")

-   **to** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The converted floating-point tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id92 "Link to this heading")

The `itof` operation converts an integer tile into a float tile. In contrast to [cuda\_tile.bitcast](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-bitcast), this preserves the numerical value of the tile, rounded to the nearest floating-point number of the provided type.

Warning

Different floating-point types have different conversion behaviors for out-of-finite-range values and special values. See [Floating-Point Conversion: Special Value and Saturation Behavior](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#table-float-conversion-semantics) for more details.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id93 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.6. cuda\_tile.int\_to\_ptr[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-int-to-ptr "Link to this heading")

_Convert a tile of integers to a tile of pointers_

cuda\_tile.int\_to\_ptr %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id94 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input tile of integers. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id95 "Link to this heading")

-   **result** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The output tile of pointers. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id96 "Link to this heading")

The `int_to_ptr` operation converts a tile of integers to a tile of pointers.

The `source` operand is interpreted as an unsigned integer.

The inverse of this operation is [cuda\_tile.ptr\_to\_int](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-ptr-to-int).

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id97 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.7. cuda\_tile.ptr\_to\_int[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-ptr-to-int "Link to this heading")

_Convert a tile of pointers to a tile of integers_

cuda\_tile.ptr\_to\_int %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id98 "Link to this heading")

-   **source** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The input tile of pointers. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id99 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The output tile of integers. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id100 "Link to this heading")

The `ptr_to_int` operation converts a tile of pointer-type elements to a tile of `i64` elements.

The result values should be interpreted as unsigned integers.

The inverse of this operation is [cuda\_tile.int\_to\_ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-int-to-ptr).

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id101 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.8. cuda\_tile.ptr\_to\_ptr[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-ptr-to-ptr "Link to this heading")

_Reinterpret a tile of one pointer type as another_

cuda\_tile.ptr\_to\_ptr %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id102 "Link to this heading")

-   **source** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - Tile with source pointer element type. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id103 "Link to this heading")

-   **result** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - Tile with target pointer element type. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id104 "Link to this heading")

The `ptr_to_ptr` operation casts a tile of pointers from a pointer of one element type to another element. Casts between pointer and non-pointer types are disallowed.

In order to perform those conversions, use [cuda\_tile.ptr\_to\_int](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-ptr-to-int) or [cuda\_tile.int\_to\_ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-int-to-ptr). These operations are distinct to enable future compiler reasoning about pointer provenance.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id105 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

### 8.4.9. cuda\_tile.trunci[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-trunci "Link to this heading")

_Truncates the width of an integer tile_

cuda\_tile.trunci %from %overflow

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id106 "Link to this heading")

-   **from** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input integer tile to truncate. 13.1
-   **overflow** ([IntegerOverflow](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-trunci-integeroverflow-attr)) - The overflow behavior of the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id107 "Link to this heading")

-   **to** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The truncated integer tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id108 "Link to this heading")

The `trunci` operation converts a tile of integers of a given element type to one with a strictly smaller width.

The optional overflow attribute specifies whether an overflow can occur when interpreting the operand as a signed and/or unsigned integer. In case of “no signed wrap”, all truncated bits must have the same value as the most significant bit of the truncated result. In case of “no unsigned wrap”, the truncated bits must be zero.

The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.

These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

-   `none` - The compiler makes no assumptions regarding overflow behavior.
-   `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
-   `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
-   `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.

If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id109 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

## 8.5. Control Flow[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#control-flow "Link to this heading")

**Tile IR** contains a standard set of control flow operations that enable conditionals, and loops.

The operations are designed in the style of the [MLIR Control Flow dialect](https://mlir.llvm.org/docs/Dialects/ControlFlow/).

A notable difference is that we allow the nesting of control flow operations for example a [cuda\_tile.if](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-if) may appear inside a [cuda\_tile.loop](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-loop) or [cuda\_tile.for](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-for).

The main control structures are:

-   [cuda\_tile.if](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-if) which implements conditional branching.
-   [cuda\_tile.loop](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-loop) which implements a loop with arbitrary exit conditions.
-   [cuda\_tile.for](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-for) which implements a range-based loop with a fixed number of iterations.

These operations and their supporting operations are described in the following section.

### 8.5.1. cuda\_tile.assert[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-assert "Link to this heading")

_Terminate kernel execution with an error message if condition is false-y_

cuda\_tile.assert %condition %message

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id110 "Link to this heading")

-   **condition** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The condition tile to check. 13.1
-   **message** ([String](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-string)) - The error message to display if assertion fails. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id111 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id112 "Link to this heading")

The `assert` operation takes as `condition` a tile of `i1` values. For each value that is `0`, it prints the given error message, along with the index of the value within the tile.

If at least one value is `0`, an error is signalled to the host side. The kernel, including the tile block that failed the assertion, may keep running.

Assertions are for debugging purposes. They can affect performance and it is therefore recommended to remove them in production code.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id113 "Link to this heading")

No constraints.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id114 "Link to this heading")

assert %arg0, "assertion failed" : tile<i1\>

Copy to clipboard

See [cuda\_tile.assert\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-assert-0) for the full example listing.

### 8.5.2. cuda\_tile.break[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-break "Link to this heading")

_Break from loop_

cuda\_tile.break %operands

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id115 "Link to this heading")

-   **operands** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The operands to yield to the parent loop upon termination. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id116 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id117 "Link to this heading")

The `break` operation is a terminator operation of a [cuda\_tile.loop](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-loop).

It may yield any number of `$operands` to the parent loop upon termination. The number of values yielded and the execution semantics of how they are yielded are determined by the parent loop.

The `break` operation always returns control to the innermost enclosing loop operation, even when it is nested within other control constructs such as `if` or additional loops.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id118 "Link to this heading")

-   Operation must terminate its parent basic block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id119 "Link to this heading")

// Break from the body of a loop.
loop {
    break
}

// Break from an if nested within the loop.
loop  {
    %condition \= constant <i1: 1\> : tile<i1\>
    if %condition  {
        break
    }
    // ...
}

%initValue0 \= constant <f32: 0.0\> : tile<f32\>
// Break from an if nested within the loop, while yielding values.
%results \= loop iter\_values(%var0 \= %initValue0): tile<f32\> \-> tile<f32\> {
    %condition \= constant <i1: 1\> : tile<i1\>
    if %condition  {
        // ...
        yield
    } else {
        // %if.loopValue0 = ...
        %loopValue0 \= constant <f32: 1.0\> : tile<f32\>
        break %loopValue0 : tile<f32\>
    }
    %loopValue1 \= constant <f32: 1.0\> : tile<f32\>
    continue %loopValue1 : tile<f32\>
}

Copy to clipboard

See [cuda\_tile.break\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-break-0) for the full example listing.

### 8.5.3. cuda\_tile.continue[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-continue "Link to this heading")

_Continue to next loop iteration_

cuda\_tile.continue %operands

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id120 "Link to this heading")

-   **operands** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The values to yield to the parent loop. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id121 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id122 "Link to this heading")

The `continue` operation represents a block terminator that returns control to a loop operation, such as [cuda\_tile.for](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-for) and [cuda\_tile.loop](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-loop). The operation may yield any number of `$operands` to the parent loop upon termination.

The requirements and semantics of the `continue` operation are defined by the parent loop operation, see the loop operation’s description for particular semantics.

The `continue` operation always returns control to the innermost enclosing loop operation, even when it is nested within other control constructs such as `if` or additional loops.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id123 "Link to this heading")

-   Operation must terminate its parent basic block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id124 "Link to this heading")

  %lowerBound \= constant <i32: 0\> : tile<i32\>
  %upperBound \= constant <i32: 10\> : tile<i32\>
  %step \= constant <i32: 1\> : tile<i32\>
  %condition \= constant <i1: 1\> : tile<i1\>
  // Continue from the body of a loop.
  for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\> {
      continue
  }

  // Continue from an if nested within the loop.
  for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\> {
      if %condition  {
          continue
      }
      // ...
  }

// Continue from an if nested within the loop, while yielding values.
%initVar0 \= constant <f32: 0.0\> : tile<f32\>
%results \= for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\>
          iter\_values(%var0 \= %initVar0) \-> (tile<f32\>)
  {
      if %condition {
          // ...
          yield
      } else {
          %loopValue0 \= constant <f32: 1.0\> : tile<f32\>
          continue %loopValue0 : tile<f32\>
      }
      %loopValue1 \= constant <f32: 1.0\> : tile<f32\>
      continue %loopValue1 : tile<f32\>
  }

Copy to clipboard

See [cuda\_tile.continue\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-continue-0) for the full example listing.

### 8.5.4. cuda\_tile.for[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-for "Link to this heading")

_For loop over integer range_

cuda\_tile.for %lowerBound %upperBound %step %initValues %unsignedCmp

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id125 "Link to this heading")

-   **lowerBound** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The lower bound of the loop. 13.1
-   **upperBound** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The upper bound of the loop. 13.1
-   **step** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The step of the loop. 13.1
-   **initValues** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The initial values of the loop-carried values. 13.1
-   **unsignedCmp** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If present, use unsigned integer comparison for loop termination. 13.2

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id126 "Link to this heading")

-   **resultValues** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The values of the loop-carried variables after loop termination. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id127 "Link to this heading")

The `for` operation is a structured range-based sequential loop.

The loop operation consists of (1) a range formed by `lowerBound`, `upperBound`, and `step`, (2) a set of loop-carried values which are initialized by `initValues` and updated by each iteration of the loop, and (3) a region which represents the loop body.

The iteration space is defined by the interval \[lowerBound,upperBound) with each value separated by `step`.

range(Lb,Ub,S)\={Lb+i⋅S∣i∈Z,Lb+i⋅S<Ub}

`lowerBound`, `upperBound`, and `step` must be of the same type. `lowerBound` and `upperBound` specify a half-open (or exclusive) range: the range includes the `lowerBound` but does not include the `upperBound`. `step` must be positive but the bounds may be negative or zero.

The `lowerBound`, `upperBound`, and `step` operands are interpreted as signed integers.

The first iteration of the loop receives the induction variable initialized to the value of `lowerBound` and the loop-carried values initialized to the values of `initValues`.

The loop body is executed for each value in the range, receiving an integer induction variable incremented by `step` on each iteration and the loop-carried values which correspond to the loop-carried values yielded by the previous loop iteration.

The loop terminates when the induction variable is greater than or equal to `upperBound`. By default, signed comparison is used between the upperBound and the induction variable. To use unsigned comparison instead, specify the optional `unsigned` unit attribute.

The body of the loop must be terminated by a [cuda\_tile.continue](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-continue) that yields the next iteration’s value for each loop carried variable.

The for operation produces one return value for each loop carried variable. The type of the i\-th return value is that of the i\-th loop carried variable and its value is the final value of the i\-th loop carried variable.

Warning

-   Loop carried variables can not be a [tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) or view type.
-   `for` operations cannot terminate early and must end in a [cuda\_tile.continue](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-continue).

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id128 "Link to this heading")

-   Operation must define scope where stack allocations are automatically freed.
-   `lowerBound`, `upperBound` and `step` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>).
-   `initValues` and `resultValues` must have the same shape and element type ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>).
-   Operation must provide custom parsing and printing methods.
-   Operation effects must include all nested operations’ effects.
-   Each region must contain exactly one block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id129 "Link to this heading")

%lowerBound \= constant <i32: 0\> : tile<i32\>
%upperBound \= constant <i32: 10\> : tile<i32\>
%step \= constant <i32: 1\> : tile<i32\>

// A simple loop iterating over an i32 range.
for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\> {
    continue
}

%initVal0 \= constant <f32: 0.0\> : tile<f32\>
// A similar loop to the above, but with a loop carried value, val0.
%results \= for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\>
                    iter\_values(%val00 \= %initVal0) \-> (tile<f32\>) {
  %loopVal0 \= constant <f32: 1.0\> : tile<f32\>
  continue %loopVal0 : tile<f32\>
}

Copy to clipboard

See [cuda\_tile.for\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-for-0) for the full example listing.

### 8.5.5. cuda\_tile.if[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-if "Link to this heading")

_Conditional execution_

cuda\_tile.if %condition

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id130 "Link to this heading")

-   **condition** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The condition of the if operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id131 "Link to this heading")

-   **results** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The results of the if operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id132 "Link to this heading")

The `if` operation represents an if-then-else construct.

The if operation consists of (1) a control operand which is a `tile<i1>` value, (2) a true branch `thenRegion` and (3) an optional false branch `elseRegion`.

The `if` operation may produce results by yielding values in each branch using [cuda\_tile.yield](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-yield).

If yielding value(s) the types of yielded values must match and the result result type of the `if` operation will be the same as the yielded values.

If yielding values the else branch is required and must also yield a value.

The values returned will be dependent on which branch is taken.

Warning

The `if` operation has a set of additional restrictions today:

-   Results of `if` must not be a [tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) or view type.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id133 "Link to this heading")

-   All regions must have zero arguments.
-   Operation must provide custom parsing and printing methods.
-   Operation effects must include all nested operations’ effects.
-   Each region must contain exactly one block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id134 "Link to this heading")

%condition \= constant <i1: 1\> : tile<i1\>

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
%x, %y \= if %condition \-> (tile<f32\>, tile<i32\>) {
  %x\_then \= constant <f32: 1.0\> : tile<f32\>
  %y\_then \= constant <i32: 2\> : tile<i32\>
  yield %x\_then, %y\_then : tile<f32\>, tile<i32\>
} else {
  %x\_then \= constant <f32: 1.0\> : tile<f32\>
  %y\_then \= constant <i32: 42\> : tile<i32\>
  yield %x\_then, %y\_then : tile<f32\>, tile<i32\>
}

Copy to clipboard

See [cuda\_tile.if\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-if-0) for the full example listing.

### 8.5.6. cuda\_tile.loop[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-loop "Link to this heading")

_Loop until a break operation_

cuda\_tile.loop %initValues

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id135 "Link to this heading")

-   **initValues** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The initial values of the loop. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id136 "Link to this heading")

-   **resultValues** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The result values of the loop. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id137 "Link to this heading")

The `loop` operation represents an, unstructured, infinite loop that executes until a [cuda\_tile.break](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-break) is reached.

The loop consists of a (1) a set of loop-carried values which are initialized by `initValues` and updated by each iteration of the loop, and (2) a region which represents the loop body.

The loop will execute the body of the loop until a [cuda\_tile.break](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-break) is dynamically executed.

Each control path of the loop must be terminated by:

-   a [cuda\_tile.continue](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-continue) that yields the next iteration’s value for each loop carried variable.
-   a [cuda\_tile.break](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-break) that terminates the loop and yields the final loop carried values.

As long as each loop iteration is terminated by one of these operations they may be combined with other control flow operations to express different control flow patterns.

The loop operation produces one return value for each loop carried variable. The type of the ith return value is that of the ith loop carried variable and its value is the final value of the ith loop carried variable.

Warning

Loop operations have a set of additional restrictions today:

-   Early returns from inside loops are not supported, a code generator must first terminate the loop and then return if they wish to end the function execution entirely.
-   Loop carried variables can not be a [tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) or view type.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id138 "Link to this heading")

-   Operation must define scope where stack allocations are automatically freed.
-   Operation must provide custom parsing and printing methods.
-   Operation effects must include all nested operations’ effects.
-   Each region must contain exactly one block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id139 "Link to this heading")

// A simple "while-do" loop.
loop {
    %cond \= constant <i1: 1\> : tile<i1\>
    if %cond {
        continue
    }
    break
}

Copy to clipboard

See [cuda\_tile.loop\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-loop-0) for the full example listing.

// A simple "do-while" loop.
loop {
    //... body of the loop.

    %cond \= constant <i1: 1\> : tile<i1\>
    if %cond {
        continue
    }
    break
}

Copy to clipboard

See [cuda\_tile.loop\_1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-loop-1) for the full example listing.

%initValue0 \= constant <f32: 0.0\> : tile<f32\>
// A loop that yields carried-iteration values, returning the final values.
%results \= loop iter\_values(%value0 \= %initValue0) : tile<f32\> \-> tile<f32\> {
    %cond \= constant <i1: 1\> : tile<i1\>
    if %cond {
        %loopValue0 \= constant <f32: 0.0\> : tile<f32\>
        continue %loopValue0 : tile<f32\>
    }
    break %value0 : tile<f32\>
}

Copy to clipboard

See [cuda\_tile.loop\_2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-loop-2) for the full example listing.

%initValue0 \= constant <i32: 0\> : tile<i32\>
// A loop that uses loop-carried values and returns a different type.
%results \= loop iter\_values(%value0 \= %initValue0) : tile<i32\> \-> tile<f32\> {
    %cond \= constant <i1: 1\> : tile<i1\>

    if %cond {
        %newLoopValue \= constant <i32: 0\> : tile<i32\>
        continue %newLoopValue : tile<i32\>
    }

    %finalReturnValue \= constant <f32: 0.0\> : tile<f32\>
    break %finalReturnValue : tile<f32\>
}

Copy to clipboard

See [cuda\_tile.loop\_3](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-loop-3) for the full example listing.

### 8.5.7. cuda\_tile.return[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-return "Link to this heading")

_Return value(s) from a function_

cuda\_tile.return %operands

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id140 "Link to this heading")

-   **operands** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The values to return. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id141 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id142 "Link to this heading")

The `return` operation returns control to the caller of a function.

Warning

Currently `return` implements restricted return semantics, notably:

-   [cuda\_tile.entry](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-entry) operations do not produce return value(s) and thus `return` may be used to terminate the execution of the kernel by invoking the operation with no operands
-   `return` can not be directly used inside of loop bodies to terminate the the execution of the kernel

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id143 "Link to this heading")

-   Operation must terminate its parent basic block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id144 "Link to this heading")

entry @foo() {
  %0 \= constant <i32: 0\> : tile<i32\>
  %1 \= constant <f16: 0.0\> : tile<f16\>
  // ...
  return
}

Copy to clipboard

See [cuda\_tile.return\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-return-0) for the full example listing.

### 8.5.8. cuda\_tile.yield[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-yield "Link to this heading")

_Yield a value from the block_

cuda\_tile.yield %operands

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id145 "Link to this heading")

-   **operands** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>) - The operands to yield to the parent operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id146 "Link to this heading")

No results.

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id147 "Link to this heading")

The `yield` operation terminates a block that must yield control back to the parent operation such as `if`, `scan`, `reduce`.

The operation may yield any number of `$operands` to the parent upon termination. The number of values yielded and the execution semantics of how they are yielded are determined by the parent operation.

Note

Unlike standard MLIR control flow dialects `yield` is not used for loop control flow, see [cuda\_tile.break](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-break) and [cuda\_tile.continue](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-continue) for loop control flow.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id148 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   Operation must terminate its parent basic block.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id149 "Link to this heading")

%condition \= constant <i1: true\> : tile<i1\>
// Yield from the body of an if conditional.
if %condition  {
    yield
}

// Yield values from within an if conditional.
%x, %y \= if %condition \-> (tile<f32\>, tile<f32\>) {
    %x\_then \= constant <f32: 0.0\> : tile<f32\>
    %y\_then \= constant <f32: 1.0\> : tile<f32\>
    yield %x\_then, %y\_then : tile<f32\>, tile<f32\>
} else {
    %x\_else \= constant <f32: 2.0\> : tile<f32\>
    %y\_else \= constant <f32: 3.0\> : tile<f32\>
    yield %x\_else, %y\_else : tile<f32\>, tile<f32\>
}

Copy to clipboard

See [cuda\_tile.yield\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-yield-0) for the full example listing.

## 8.6. Memory[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#memory "Link to this heading")

**Tile IR** contains a set of memory operations which enable loading, storing, and manipulating memory.

There are a few families of memory operations in **Tile IR**:

-   Tile of pointer based memory operations such as [cuda\_tile.load\_ptr\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-ptr-tko) and [cuda\_tile.store\_ptr\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-ptr-tko) which load and store tiles from and to global memory.
-   View based memory operations such as [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko) which load and store tiles from and to views.
-   Atomic memory operations such as [cuda\_tile.atomic\_rmw\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-atomic-rmw-tko) and [cuda\_tile.atomic\_cas\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-atomic-cas-tko) which perform atomic operations on global memory.

Currently all memory operations are token-ordered; the ordering between any pair of memory operations is undefined unless connected by tokens. For more discussion on token-ordered operations see [Memory Model](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model).

Warning

Reading or writing of bound of any allocation is undefined behavior. Examples of out of bounds access are: \* Pointer memory operations to tiles containing elements outside the allocation, for example offseting passed the end of the allocation. \* Associating an invalid layout with a base pointer, that describes a striding or shape that over runs the allocation and then indexing into the view. \* Indexing into a view with indices that are out of bounds.

Note

The rules of what consititues out of bounds is modified when using padded views or masking, see [Type System](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#section-types) for more details on specific types.

### 8.6.1. cuda\_tile.join\_tokens[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-join-tokens "Link to this heading")

_Product a new token which depends on the input tokens_

cuda\_tile.join\_tokens %tokens

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id150 "Link to this heading")

-   **tokens** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)\>) - The input tokens to join. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id151 "Link to this heading")

-   **result** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The joined token. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id152 "Link to this heading")

The `join_tokens` operation produces a fresh token which depends on all input tokens. Token-ordered operations which consume the new token will then be ordered with respect to all joined tokens.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id153 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   Operation must infer result types from operands and attributes.

### 8.6.2. cuda\_tile.load\_ptr\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-load-ptr-tko "Link to this heading")

_Load and gather data from global memory using a pointer tile without ordering guarantees_

cuda\_tile.load\_ptr\_tko %memory\_ordering\_semantics %memory\_scope %source %mask %paddingValue %token %optimization\_hints

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id154 "Link to this heading")

-   **memory\_ordering\_semantics** ([MemoryOrderingSemantics](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-load-ptr-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the load operation. 13.1
-   **memory\_scope** ([MemoryScope](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-load-ptr-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
-   **source** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The source tile of pointers. 13.1
-   **mask** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The mask for the load operation. 13.1
-   **paddingValue** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e4m3fn](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [fp8e5m2](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The padding value for the load operation. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The token for the load operation. 13.1
-   **optimization\_hints** ([OptimizationHints](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-load-ptr-tko-optimizationhints-attr)) - Optimization hints for operation 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id155 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The result of the load operation. 13.1
-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token of the load operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id156 "Link to this heading")

This `load` OP performs a gather operation by loading a tile of data from global memory into a result tile based on a tile of pointers provided by the `source` operand.

The `source` operand is a tile of pointers, which specifies the memory locations from which the data is gathered. The operation loads this data and returns it as the `result` tile. When loading i1 values, each value is loaded from a full byte in memory. Any nonzero byte is canonicalized to 0x01, and zero bytes become 0x00.

Optionally, a `mask` operand can be provided to control the gathering of elements. If present, only the elements specified by the `mask` are loaded. The shape of the `mask` must match the shape of the `result`.

When `mask` is present one `paddingValue` can be optionally present as well. The `paddingValue` must have the same shape of the `source` tile. If it is not present, the value of masked elements are undefined.

Token-ordered operations are not constrained by program order. The compiler may reorder them (i.e. place them earlier or later in program order) unless further constrained by tokens.

The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model) of the specification.

-   `weak` - No concurrent accesses to the source/destination location.
-   `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
-   `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then _happens before_ is established.

Note: The following variants are not supported by this operation: `release`, `acq_rel`.

The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.

-   `tl_blk` - There may be concurrent accesses from within the same tile block.
-   `device` - There may be concurrent accesses from within the same device (i.e., GPU).
-   `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).

The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.

The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.

-   `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda\_tile.entry](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-entry).
-   `allow_tma` - suggest whether to use TMA for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).
-   `latency` - latency hint for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).

For example they can be annotated as:

optimization\_hints\=<
  sm\_100 \= {num\_cta\_in\_cga \= 8},
  sm\_120 \= {num\_cta\_in\_cga \= 16}
\>

Copy to clipboard

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id157 "Link to this heading")

-   Operation must encode variadic operand segment sizes in attributes.
-   source type is expected a pointer type of result type
-   shape of ‘mask’ must match the shape of ‘source’
-   type of ‘paddingValue’ must match the type of ‘result’

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id158 "Link to this heading")

%mask \= constant <i1: 1\> : tile<i1\>
%padding \= constant <f32: 0.0\> : tile<f32\>

  // Load without token.
  %result0, %res\_token0 \= load\_ptr\_tko weak %ptr, %mask, %padding
      : tile<ptr<f32\>>, tile<i1\>, tile<f32\> \-> tile<f32\>, token

  // Load with token.
  %token0 \= make\_token : token
  %result1, %res\_token1 \= load\_ptr\_tko weak %ptr, %mask, %padding token\=%token0
      : tile<ptr<f32\>>, tile<i1\>, tile<f32\> \-> tile<f32\>, token

  return

Copy to clipboard

See [cuda\_tile.load\_ptr\_tko\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-load-ptr-tko-0) for the full example listing.

### 8.6.3. cuda\_tile.make\_token[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-make-token "Link to this heading")

_Create a fresh token with no prior dependencies_

cuda\_tile.make\_token

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id159 "Link to this heading")

No parameters.

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id160 "Link to this heading")

-   **result** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - A fresh token with no prior dependencies. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id161 "Link to this heading")

The `make_token` operation creates a fresh token with no prior dependencies.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id162 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   Operation must infer result types from operands and attributes.

### 8.6.4. cuda\_tile.store\_ptr\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-store-ptr-tko "Link to this heading")

_Store and scatter data from pointer of tile to global memory without ordering guarantees_

cuda\_tile.store\_ptr\_tko %memory\_ordering\_semantics %memory\_scope %destination %value %mask %token %optimization\_hints

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id163 "Link to this heading")

-   **memory\_ordering\_semantics** ([MemoryOrderingSemantics](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-store-ptr-tko-memoryorderingsemantics-attr)) - The memory ordering semantics. 13.1
-   **memory\_scope** ([MemoryScope](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-store-ptr-tko-memoryscope-attr)) - The optional memory scope. 13.1
-   **destination** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The destination pointer tile. 13.1
-   **value** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The value tile to store. 13.1
-   **mask** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The optional mask for selective storage. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The optional token for operation ordering. 13.1
-   **optimization\_hints** ([OptimizationHints](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-store-ptr-tko-optimizationhints-attr)) - Optimization hints for operation 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id164 "Link to this heading")

-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token for synchronization. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id165 "Link to this heading")

The `store` operation performs a scatter by storing a tile of data from a tile into global memory.

The `destination` operand is a tile of pointers indicating the global memory locations where data from the `value` tile will be stored. When storing i1 values, each value occupies a full byte in memory. Any nonzero byte is canonicalized to 0x01, and zero bytes become 0x00.

Additionally, the operation supports an optional `mask` operand, which allows selective scattering of elements. If provided, only the elements specified by the `mask` are stored. The shape of the `mask` must align with the shape of the `value` tile.

The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model) of the specification.

-   `weak` - No concurrent accesses to the source/destination location.
-   `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
-   `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then _happens before_ is established.

Note: The following variants are not supported by this operation: `acquire`, `acq_rel`.

The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.

-   `tl_blk` - There may be concurrent accesses from within the same tile block.
-   `device` - There may be concurrent accesses from within the same device (i.e., GPU).
-   `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).

The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.

The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.

-   `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda\_tile.entry](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-entry).
-   `allow_tma` - suggest whether to use TMA for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).
-   `latency` - latency hint for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).

For example they can be annotated as:

optimization\_hints\=<
  sm\_100 \= {num\_cta\_in\_cga \= 8},
  sm\_120 \= {num\_cta\_in\_cga \= 16}
\>

Copy to clipboard

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id166 "Link to this heading")

-   Operation must encode variadic operand segment sizes in attributes.
-   destination type is expected a pointer type of value type
-   shape of ‘destination’ must match the shape of ‘mask’
-   Operation must infer result types from operands and attributes.

## 8.7. Floating Point[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#floating-point "Link to this heading")

**Tile IR** contains a set of typed arithmetic operations which implement familiar arithmetic operations on floating-point types for integer operations see [Integer](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-group-integer).

All operations are implemented in a manner that is efficient for the target architecture and device family. In most common cases this means utilizing the underlying hardware’s native floating-point operations. Due to **Tile IR**’s stability guarantees and higher-level programming model some types on some hardware may be emulated, see [Stability](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/stability.html#section-stability) for more information about the stability guarantees and information about per device behavior.

### 8.7.1. Floating-Point Arithmetic[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#floating-point-arithmetic "Link to this heading")

Standard floating-point types implement the IEEE-754 standard for floating-point arithmetic. On NVIDIA hardware, certain types are non-standard and _do not_ implement the IEEE-754 standard, see [Element Types](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) for more details about the different floating-point types, their precision, storage, and formats.

Supports 16-bit, 32-bit, and 64-bit floating-point data types.

### 8.7.2. Floating-Point Math[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#floating-point-math "Link to this heading")

**Tile IR** contains a set of standard math library operations which implement familiar mathematical functions over tensors supporting 16-bit, 32-bit, and 64-bit floating-point data types.

Note

32-bit and 64-bit operations typically leverage efficient hardware-specific instructions. Some 16-bit operations are emulated using wider intermediate computations, and may not offer the same performance.

Warning

There are some restrictions based on data type support which are detailed in the [Type System](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#section-types) section.

### 8.7.3. cuda\_tile.absf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-absf "Link to this heading")

_Element-wise floating-point absolute value_

cuda\_tile.absf %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id167 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input float tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id168 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The absolute value of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id169 "Link to this heading")

The `absf` operation computes the element-wise absolute value of the input float tile.

absf(x)i\=|x|i

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id170 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.4. cuda\_tile.addf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-addf "Link to this heading")

_Element-wise floating-point addition_

cuda\_tile.addf %lhs %rhs %rounding\_mode %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id171 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-addf-roundingmode-attr)) - The rounding mode for the operation. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id172 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The sum of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id173 "Link to this heading")

The `addf` operation computes the element-wise addition of two tiles with floating-point element type.

addf(x,y)i\=xi+yi

The addition of individual elements is performed by the target architecture’s native floating-point addition for the given element type unless otherwise specified.

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |
| `rounding<nearest_even>` | yes | yes | yes | yes |
| `rounding<zero>` | yes | yes | yes\\* | yes\\* |
| `rounding<negative_inf>` | yes | yes | yes\\* | yes\\* |
| `rounding<positive_inf>` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id174 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.5. cuda\_tile.atan2[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-atan2 "Link to this heading")

_Element-wise atan2_

cuda\_tile.atan2 %x %y

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id175 "Link to this heading")

-   **x** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input x float tile. 13.2
-   **y** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input y float tile. 13.2

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id176 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The element-wise result tile. 13.2

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id177 "Link to this heading")

The `atan2` operation calculates the principal value of the arc tangent of the ratio of first and second input arguments x / y. The quadrant of the result is determined by the signs of inputs x and y.

(atan2(x,y))i\=atan2(xi,yi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id178 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `x`, `y` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id179 "Link to this heading")

%x \= constant <f32: \[1.0, \-1.0, 0.0, 2.0\]\> : tile<4xf32\>
%y \= constant <f32: \[1.0,  1.0, 1.0, 0.0\]\> : tile<4xf32\>
%res \= atan2 %x, %y : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.atan2\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-atan2-0) for the full example listing.

### 8.7.6. cuda\_tile.ceil[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-ceil "Link to this heading")

_Element-wise ceiling_

cuda\_tile.ceil %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id180 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input float tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id181 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The ceiling of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id182 "Link to this heading")

The `ceil` operation computes the element-wise ceiling on the input floating-point tile. The ceiling operation rounds each element up to the largest integer value that is greater than or equal to the input value.

ceil(x)i\=min{n∈Z∣n≥xi}

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id183 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id184 "Link to this heading")

%result \= ceil %source : tile<f32\>

Copy to clipboard

See [cuda\_tile.ceil\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-ceil-0) for the full example listing.

### 8.7.7. cuda\_tile.cmpf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-cmpf "Link to this heading")

_Element-wise floating-point comparison_

cuda\_tile.cmpf %comparison\_predicate %comparison\_ordering %lhs %rhs

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id185 "Link to this heading")

-   **comparison\_predicate** ([ComparisonPredicate](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-cmpf-comparisonpredicate-attr)) - The comparison predicate. 13.1
-   **comparison\_ordering** ([ComparisonOrdering](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-cmpf-comparisonordering-attr)) - The comparison ordering. 13.1
-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id186 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the comparison. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id187 "Link to this heading")

The `cmpf` operation is a generic comparison for float-like types. The operands must have the same shape and type, and this type must be a float type.

The result is `1` if the comparison is true and `0` otherwise. The comparison is performed element-wise and the element of the result indicates whether the comparison is true for the operand elements with the same indices as those of the result.

cmpf(x,y,pred)i\={1if xi pred yi0otherwise

The `comparison_predicate` attribute specifies the kind of comparison to be performed.

-   `equal` - Equal comparison.
-   `not_equal` - Not equal comparison.
-   `less_than` - Less than comparison.
-   `less_than_or_equal` - Less than or equal comparison.
-   `greater_than` - Greater than comparison.
-   `greater_than_or_equal` - Greater than or equal comparison.

The `comparison_ordering` attribute specifies the kind of ordering to be performed in the comparison operation.

-   `unordered` - Unordered comparison.
-   `ordered` - Ordered comparison.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id188 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs` and `rhs` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Result type has i1 element type and same shape as operands
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id189 "Link to this heading")

%lhs0 \= constant <f16: 0.0\> : tile<f16\>
%rhs0 \= constant <f16: 0.0\> : tile<f16\>

// Custom form of scalar "ordered equal" comparison.
%x0 \= cmpf equal ordered %lhs0, %rhs0 : tile<f16\> \-> tile<i1\>

%lhs1 \= constant <f16: 0.0\> : tile<2x2xf16\>
%rhs1 \= constant <f16: 0.0\> : tile<2x2xf16\>

// Custom form of scalar "unordered less than" comparison.
%x2 \= cmpf less\_than unordered %lhs1, %rhs1 : tile<2x2xf16\> \-> tile<2x2xi1\>

%lhs2 \= constant <f64: 0.0\> : tile<2x2xf64\>
%rhs2 \= constant <f64: 0.0\> : tile<2x2xf64\>

Copy to clipboard

See [cuda\_tile.cmpf\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-cmpf-0) for the full example listing.

### 8.7.8. cuda\_tile.cosh[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-cosh "Link to this heading")

_Element-wise hyperbolic cosine_

cuda\_tile.cosh %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id190 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id191 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The hyperbolic cosine of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id192 "Link to this heading")

The `cosh` operation computes the element-wise hyperbolic cosine of the input tile with floating-point element type.

cosh(x)i\=cosh⁡xi

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id193 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.9. cuda\_tile.cos[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-cos "Link to this heading")

_Element-wise cosine_

cuda\_tile.cos %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id194 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input float tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id195 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The cosine of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id196 "Link to this heading")

The `cos` operation computes the element-wise cosine of the input floating-point tile.

cos(x)i\=cos⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id197 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id198 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res \= cos %in : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.cos\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-cos-0) for the full example listing.

### 8.7.10. cuda\_tile.divf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-divf "Link to this heading")

_Element-wise floating-point division_

cuda\_tile.divf %lhs %rhs %rounding\_mode %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id199 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The dividend input floating-point tile. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The divisor input floating-point tile. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-divf-roundingmode-attr)) - The rounding mode for the operation. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id200 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the `divf` operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id201 "Link to this heading")

The `divf` operation computes the element-wise division of two input tiles with floating-point element types.

The `approx` rounding mode implements a fast approximation of divide, computed as a multiplication by reciprocal. For `|rhs|` in normalized range `[2^(-126), 2^(126)]` the maximum ULP (Unit in the Last Place) error is `2`. For `2^(126) < |rhs| < 2^(128)`, if `lhs` is infinity the operation returns `NaN`, otherwise `0`.

The `full` rounding mode implements a relatively fast, full-range approximation that scales operands to achieve better accuracy, but is not fully IEEE 754 compliant. The maximum ulp error is 2 across the full range of inputs.

div(lhs, rhs)i\=lhsi/rhsi

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |
| `approx` | yes | no  | no  | no  |
| `full` | yes | no  | no  | no  |
| `rounding<nearest_even>` | yes | yes | yes\\* | yes\\* |
| `rounding<zero>` | yes | yes | yes\\* | yes\\* |
| `rounding<negative_inf>` | yes | yes | yes\\* | yes\\* |
| `rounding<positive_inf>` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id202 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.11. cuda\_tile.exp2[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-exp2 "Link to this heading")

_Element-wise power of two_

cuda\_tile.exp2 %source %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id203 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id204 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of raising 2 to the power of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id205 "Link to this heading")

The `exp2` operation computes the element-wise power of two of the input floating-point tile.

exp2(x)i\=2xi

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

The below table shows the supported modifiers for each data type.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id206 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id207 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res \= exp2 %in : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.exp2\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-exp2-0) for the full example listing.

### 8.7.12. cuda\_tile.exp[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-exp "Link to this heading")

_Element-wise exponential_

cuda\_tile.exp %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id208 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input float tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id209 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The exponential of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id210 "Link to this heading")

The `exp` operation computes the element-wise exponential of the input floating-point tile.

exp(x)i\=exi

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id211 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id212 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res \= exp %in : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.exp\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-exp-0) for the full example listing.

### 8.7.13. cuda\_tile.floor[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-floor "Link to this heading")

_Element-wise floor rounding_

cuda\_tile.floor %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id213 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input tile to the floor operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id214 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the floor operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id215 "Link to this heading")

The `floor` operation computes the element-wise floor on the input floating-point tile rounding each element down to the largest integer that is less than or equal to the element.

floori(xi)\=max{n∈Z∣n≤xi}

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id216 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id217 "Link to this heading")

%source \= constant <f32: 1.5\> : tile<f32\>
%result \= floor %source : tile<f32\>

Copy to clipboard

See [cuda\_tile.floor\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-floor-0) for the full example listing.

### 8.7.14. cuda\_tile.fma[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-fma "Link to this heading")

_Floating point fused multipy-add_

cuda\_tile.fma %lhs %rhs %acc %rounding\_mode %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id218 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **acc** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The accumulator operand. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-fma-roundingmode-attr)) - The rounding mode for the operation. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id219 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The fused multiply-add of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id220 "Link to this heading")

Takes three operands `lhs`, `rhs` and `acc`, returns `result = lhs * rhs + acc`.

fma(x,y,z)i\=xi×yi+zi

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |
| `rounding<nearest_even>` | yes | yes | yes | yes |
| `rounding<zero>` | yes | yes | yes\\* | yes\\* |
| `rounding<negative_inf>` | yes | yes | yes\\* | yes\\* |
| `rounding<positive_inf>` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id221 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs`, `acc` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.15. cuda\_tile.log2[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-log2 "Link to this heading")

_Element-wise base-2 logarithm_

cuda\_tile.log2 %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id222 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id223 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the log2 operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id224 "Link to this heading")

The `log2` operation computes the element-wise base-2 logarithm of a floating-point tile.

log2(x)i\=log2⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id225 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id226 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res \= log2 %in : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.log2\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-log2-0) for the full example listing.

### 8.7.16. cuda\_tile.log[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-log "Link to this heading")

_Element-wise natural logarithm_

cuda\_tile.log %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id227 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id228 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the log operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id229 "Link to this heading")

The `log` operation computes the element-wise natural logarithm of a floating-point tile.

log(x)i\=ln⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id230 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.17. cuda\_tile.maxf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-maxf "Link to this heading")

_Element-wise floating-point maximum_

cuda\_tile.maxf %lhs %rhs %propagate\_nan %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id231 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **propagate\_nan** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - When set, `maxf` (or `minf`) returns a `NaN` if either of the two compared elements is `NaN`. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id232 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the `maxf` operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id233 "Link to this heading")

The `maxf` operation computes the element-wise maximum of two input tiles with floating-point element types.

The `propagate_nan` controls how `maxf` will interpret `NaN`. If the `propagate_nan` modifier is set, `maxf` returns a canonical `NaN` if either of the compared elements is `NaN` (IEEE 754-2019’s maximum). While if the `propagate_nan` modifier is not set, `maxf` returns a canonical `NaN` only if both elements are `NaN`; otherwise, it returns the non-`NaN` element (IEEE 754-2019’s maximumNumber).

If neither element is `NaN`, `maxf` will return the greater of the inputs. `+0.0` is considered greater than `-0.0`.

If the `flush_to_zero` modifier is specified, denormal numbers are flushed to sign-preserving zero. The `flush_to_zero` modifier applies only to the f32 data type.

maxi(x,y)i\={xiif xi≥yiyiif xi<yi

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id234 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id235 "Link to this heading")

// Create tensor view from a pointer to global memory
%0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
%1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
// Convert tensor views to partition views and load tiles from partition views.
%p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
%p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
%c0 \= constant <i32: 0\> : tile<i32\>
%2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
%3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
// IEEE 754-2019's maximum
%4 \= maxf %2, %3 propagate\_nan : tile<2x4xf32\>
// IEEE 754-2019's maximumNumber
%5 \= maxf %2, %3 : tile<2x4xf32\>
// flush denormal to positive zero
%6 \= maxf %2, %3 flush\_to\_zero : tile<2x4xf32\>

Copy to clipboard

See [cuda\_tile.maxf\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-maxf-0) for the full example listing.

### 8.7.18. cuda\_tile.minf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-minf "Link to this heading")

_Element-wise floating-point minimum_

cuda\_tile.minf %lhs %rhs %propagate\_nan %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id236 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **propagate\_nan** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - When set, `maxf` (or `minf`) returns a `NaN` if either of the two compared elements is `NaN`. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id237 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The minimum of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id238 "Link to this heading")

The `minf` operation computes the element-wise minimum of two input tiles with floating-point element types.

The `propagate_nan` controls how `minf` will interpret `NaN`. If the `propagate_nan` modifier is set, `minf` returns a canonical `NaN` if either of the compared elements is `NaN` (IEEE 754-2019’s minimum). While if the `propagate_nan` modifier is not set, `minf` returns a canonical `NaN` only if both elements are `NaN`; otherwise, it returns the non-`NaN` element (IEEE 754-2019’s minimumNumber).

If neither element is `NaN`, `minf` will return the lowest of the inputs. `-0.0` is considered less than `+0.0`.

If the `flush_to_zero` modifier is specified, denormal numbers are flushed to sign-preserving zero. The `flush_to_zero` modifier applies only to the f32 data type.

minf(x,y)i\={xiif xi≤yiyiif xi\>yi

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id239 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id240 "Link to this heading")

// Create tensor view from a pointer to global memory
%0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
%1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
// Convert tensor views to partition views and load tiles from partition views.
%p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
%p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
%c0 \= constant <i32: 0\> : tile<i32\>
%2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
%3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
// IEEE 754-2019's minimum
%4 \= minf %2, %3 propagate\_nan : tile<2x4xf32\>
// IEEE 754-2019's minimumNumber
%5 \= minf %2, %3 : tile<2x4xf32\>
// flush denormal to positive zero
%6 \= minf %2, %3 flush\_to\_zero : tile<2x4xf32\>

Copy to clipboard

See [cuda\_tile.minf\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-minf-0) for the full example listing.

### 8.7.19. cuda\_tile.mmaf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-mmaf "Link to this heading")

_Floating-point matrix-multiply-accumulate_

cuda\_tile.mmaf %lhs %rhs %acc

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id241 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>\>) - The left hand side matrix operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>\>) - The right hand side matrix operand. 13.1
-   **acc** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The accumulator matrix operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id242 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result matrix after multiplication and accumulation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id243 "Link to this heading")

The `mmaf` operation implements an MMA (matrix-multiply-accumulate) operation for floating-point tiles. It performs matrix multiplication on the floating-point tiles `lhs` and `rhs`, then adds the tile `acc` to the result. `lhs`, `rhs`, and `acc` must be 2D tiles or 3D tiles. The latter case indicates a batched matrix multiplication.

mmaf(A,B,C)ij\=∑k\=0K−1Aik×Bkj+Cij

The types of all operands must be a supported combination (see [mmaf Supported Data Types](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#table-cuda-tile-mmaf-0)).

Shapes must be a valid matrix multiplication configuration. Unbatched (2D) MMA expects the operands `lhs`, `rhs`, and `acc` to have shapes `M x K`, `K x N`, and `M x N` (respectively). Batched (3D) MMA expects the operands to have shapes `B x M x K`, `B x K x N`, and `B x M x N` (respectively).

The table below shows the supported output types for each possible `mmaf` input type. Input operands must be of the same element type.

| Input Type | Supported Output Types |
| --- | --- |
| `f8E4M3FN` | `f16` or `f32` |
| `f8E5M2` | `f16` or `f32` |
| `f16` | `f16` or `f32` |
| `bf16` | `f32` |
| `tf32` | `f32` |
| `f32` | `f32` |
| `f64` | `f64` |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id244 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `acc` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   `lhs` and `rhs` must have the same element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[tf32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>\>).
-   `lhs`, `rhs` and `acc` must have the same rank.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id245 "Link to this heading")

%lhs0 \= constant <f16: 0.0\> : tile<4x8xf16\>
%rhs0 \= constant <f16: 0.0\> : tile<8x2xf16\>
%acc0 \= constant <f32: 0.0\> : tile<4x2xf32\>

%0 \= mmaf %lhs0, %rhs0, %acc0
    : tile<4x8xf16\>, tile<8x2xf16\>,
      tile<4x2xf32\>

%lhs1 \= constant <f16: 0.0\> : tile<2x4x8xf16\>
%rhs1 \= constant <f16: 0.0\> : tile<2x8x2xf16\>
%acc1 \= constant <f32: 0.0\> : tile<2x4x2xf32\>

%1 \= mmaf %lhs1, %rhs1, %acc1
    : tile<2x4x8xf16\>, tile<2x8x2xf16\>,
      tile<2x4x2xf32\>

Copy to clipboard

See [cuda\_tile.mmaf\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-mmaf-0) for the full example listing.

### 8.7.20. cuda\_tile.mulf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-mulf "Link to this heading")

_Element-wise floating-point multiplication_

cuda\_tile.mulf %lhs %rhs %rounding\_mode %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id246 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-mulf-roundingmode-attr)) - The rounding mode for the operation. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id247 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The product of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id248 "Link to this heading")

The `mulf` operation computes the element-wise product between the two input tiles with with floating-point element types.

If the `flush_to_zero` modifier is specified, denormal numbers are flushed to positive zero.

If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result.

mulf(x,y)i\=xi×yi

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |
| `rounding<nearest_even>` | yes | yes | yes | yes |
| `rounding<zero>` | yes | yes | yes\\* | yes\\* |
| `rounding<negative_inf>` | yes | yes | yes\\* | yes\\* |
| `rounding<positive_inf>` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id249 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.21. cuda\_tile.negf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-negf "Link to this heading")

_Element-wise floating-point negation_

cuda\_tile.negf %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id250 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id251 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The negated floating-point tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id252 "Link to this heading")

`negf` is an element-wise operation that negates the sign of `source`.

negf(x)i\=−xi

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id253 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id254 "Link to this heading")

%source \= constant <f32: 0.0\> : tile<4xf32\>
%result \= negf %source : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.negf\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-negf-0) for the full example listing.

### 8.7.22. cuda\_tile.pow[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-pow "Link to this heading")

_Element-wise floating-point exponentiation_

cuda\_tile.pow %source %exponent

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id255 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The base tile. 13.1
-   **exponent** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The exponent tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id256 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the pow operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id257 "Link to this heading")

The `pow` operation computes the element-wise exponentiation of the source floating-point tile raised to the power of the exponent floating-point tile.

pow(x,y)i\=xiyi

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id258 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `result`, `source` and `exponent` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   `source`, `exponent` and `result` must have the same rank.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id259 "Link to this heading")

%source \= constant <f32: 0.0\> : tile<4xf32\>
%exponent \= constant <f32: 2.0\> : tile<4xf32\>
%result \= pow %source, %exponent : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.pow\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-pow-0) for the full example listing.

### 8.7.23. cuda\_tile.remf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-remf "Link to this heading")

_Element-wise floating-point remainder_

cuda\_tile.remf %lhs %rhs

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id260 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id261 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The remainder after division. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id262 "Link to this heading")

The `remf` operation computes the element-wise floating-point remainder using truncated division (rounding towards zero).

remf(x,y)i\=xi−trunc(xi/yi)×yi

The result has the same sign as the dividend (`lhs`) and its magnitude is less than the magnitude of divisor (`rhs`).

**Special cases:**

-   If `y` is zero, returns `NaN`
-   If `x` is infinite and `y` is finite, returns `NaN`
-   If `x` is finite and `y` is infinite, returns `x`
-   If either argument is `NaN`, returns `NaN`

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id263 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.24. cuda\_tile.rsqrt[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-rsqrt "Link to this heading")

_Element-wise reciprocal square root_

cuda\_tile.rsqrt %source %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id264 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input tile to compute the reciprocal square root of. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id265 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The reciprocal square root of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id266 "Link to this heading")

The `rsqrt` operation computes the element-wise reciprocal square root of the input floating-point tile.

This operation supports: `flush_to_zero`: if set by the user, will flush subnormal inputs and results to sign-preserving zero.

rsqrt(x)i\=1xi

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

The below table shows the supported modifiers for each data type.

| Modifier | Float32 | Float64 |
| --- | --- | --- |
| `flush_to_zero` | yes | no  |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id267 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id268 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res \= rsqrt %in : tile<4xf32\>

// Rsqrt op with flush to zero modifier
%ftz\_res \= rsqrt %in flush\_to\_zero : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.rsqrt\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-rsqrt-0) for the full example listing.

### 8.7.25. cuda\_tile.sinh[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-sinh "Link to this heading")

_Element-wise hyperbolic sine_

cuda\_tile.sinh %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id269 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input float tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id270 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The hyperbolic sine of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id271 "Link to this heading")

The `sinh` operation computes the element-wise hyperbolic sine of the input floating-point tile.

sinh(x)i\=sinh⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id272 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.26. cuda\_tile.sin[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-sin "Link to this heading")

_Element-wise sine_

cuda\_tile.sin %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id273 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input float tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id274 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The sine of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id275 "Link to this heading")

The `sin` operation computes the element-wise sine of the input floating-point tile.

sin(x)i\=sin⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id276 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id277 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res \= sin %in : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.sin\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-sin-0) for the full example listing.

### 8.7.27. cuda\_tile.sqrt[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-sqrt "Link to this heading")

_Element-wise square root_

cuda\_tile.sqrt %source %rounding\_mode %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id278 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input tile to compute the square root of. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-sqrt-roundingmode-attr)) - The rounding mode for the operation. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id279 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The square root of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id280 "Link to this heading")

The `sqrt` operation computes the element-wise square root of a floating-point tile.

sqrt(x)i\=xi

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |
| `approx` | yes | no  | no  | no  |
| `rounding<nearest_even>` | yes | yes | yes | yes |
| `rounding<zero>` | yes | yes | yes\\* | yes\\* |
| `rounding<negative_inf>` | yes | yes | yes\\* | yes\\* |
| `rounding<positive_inf>` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id281 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.28. cuda\_tile.subf[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-subf "Link to this heading")

_Element-wise floating-point subtraction_

cuda\_tile.subf %lhs %rhs %rounding\_mode %flush\_to\_zero

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id282 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-subf-roundingmode-attr)) - The rounding mode for the operation. 13.1
-   **flush\_to\_zero** ([Flag](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-flag)) - If set, flushes subnormal inputs and results to sign-preserving zero. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id283 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the subtraction. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id284 "Link to this heading")

The `subf` operation computes the element-wise subtraction of the input floating-point tiles.

subf(x,y)i\=xi−yi

Element-wise floating-point arithmetic operations are performed by the target architecture’s native floating-point instructions. If the `rounding` modifier is specified, the particular rounding mode will be applied to each element of the result. See [Floating-Point Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-arithmetic) for more details.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers and rounding modes for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `flush_to_zero` | yes | no  | no  | no  |
| `rounding<nearest_even>` | yes | yes | yes | yes |
| `rounding<zero>` | yes | yes | yes\\* | yes\\* |
| `rounding<negative_inf>` | yes | yes | yes\\* | yes\\* |
| `rounding<positive_inf>` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id285 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.7.29. cuda\_tile.tanh[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-tanh "Link to this heading")

_Element-wise hyperbolic tangent_

cuda\_tile.tanh %source %rounding\_mode

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id286 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1
-   **rounding\_mode** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-tanh-roundingmode-attr)) - The rounding mode for the operation. 13.2

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id287 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The hyperbolic tangent of the input floating-point tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id288 "Link to this heading")

The `tanh` operation computes the element-wise hyperbolic tangent of the input floating-point tile. Default rounding mode is full.

The `approx` rounding mode implements a fast approximation to hyperbolic tangent. Subnormal results of this fast approximation are not flushed to zero.

The `full` rounding mode implements a relatively fast full-range approximation. The maximum ulp error is 2 across the full range of inputs in FP32 and 1 in FP64.

tanh(x)i\=tanh⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

The below table shows the supported modifiers for each data type. Entries with ‘\*’ are emulated in f32.

| Modifier | Float32 | Float64 | BFloat16 | Float16 |
| --- | --- | --- | --- | --- |
| `approx` | yes | no  | no  | no  |
| `full` | yes | yes | yes\\* | yes\\* |

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id289 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id290 "Link to this heading")

%in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
%res0 \= tanh %in : tile<4xf32\>

// tanh with approx modifier
%res1 \= tanh %in rounding<approx\> : tile<4xf32\>

Copy to clipboard

See [cuda\_tile.tanh\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-tanh-0) for the full example listing.

### 8.7.30. cuda\_tile.tan[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-tan "Link to this heading")

_Element-wise tangent_

cuda\_tile.tan %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id291 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input floating-point tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id292 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The tangent of the input floating-point tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id293 "Link to this heading")

The `tan` operation computes the element-wise tangent of the input floating-point tile.

tan(x)i\=tan⁡(xi)

This operation is emulated in `f32` when executed on half-precision inputs (`f16` and `bf16`). See [Floating-Point Math](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-floating-point-math) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id294 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[f16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [bf16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [f64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

## 8.8. Integer[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#integer "Link to this heading")

**Tile IR** contains a set of typed arithmetic operations which implement familiar arithmetic operations on tiles of integers, for floating-point operations see [Floating Point](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-group-floating-point).

All operations are implemented in a manner that is efficient for the target architecture and device family. In most common cases this means utilizing the underlying hardware’s native floating-point operations. Due to **Tile IR**’s stability guarantees and higher-level programming model some types on some hardware may be emulated, see [Stability](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/stability.html#section-stability) for more information about the stability guarantees and information about per device behavior.

### 8.8.1. Integer Arithmetic[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#integer-arithmetic "Link to this heading")

Integer types in **Tile IR** are signless, which is importantly not the same as unsigned. We store all integers in a two’s complement representation and with required operations supporting a signed or unsigned flag as needed. This design allows us to not have to differentiate between signed and unsigned integer types at the IR level and keeps sign information local to the operation.

For the `i1` type, unsigned operations see values 0/1, while signed operations see values 0/-1, with all i1 values canonicalized to 0x00 (false) or 0x01 (true) for consistent LSB-only semantics.

### 8.8.2. cuda\_tile.absi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-absi "Link to this heading")

_Element-wise integer absolute value_

cuda\_tile.absi %source

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id295 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input integer tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id296 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The absolute value of the input tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id297 "Link to this heading")

The `absi` operation computes the absolute value of the input integer tile.

The input tile is always interpreted as a signed integer. The output tile is always interpreted as an unsigned integer.

absi(x)\=|x|

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id298 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.3. cuda\_tile.addi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-addi "Link to this heading")

_Element-wise integer addition_

cuda\_tile.addi %lhs %rhs %overflow

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id299 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **overflow** ([IntegerOverflow](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-addi-integeroverflow-attr)) - The overflow behavior of the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id300 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The sum of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id301 "Link to this heading")

The `addi` operation computes the element-wise addition of two tiles with integer element types.

addi(x,y)i\=xi+yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.

These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

-   `none` - The compiler makes no assumptions regarding overflow behavior.
-   `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
-   `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
-   `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.

If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id302 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.4. cuda\_tile.cmpi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-cmpi "Link to this heading")

_Element-wise integer comparison_

cuda\_tile.cmpi %comparison\_predicate %lhs %rhs %signedness

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id303 "Link to this heading")

-   **comparison\_predicate** ([ComparisonPredicate](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-cmpi-comparisonpredicate-attr)) - The comparison predicate. 13.1
-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-cmpi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id304 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the comparison. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id305 "Link to this heading")

The `cmpi` operation is a generic comparison for integer-like types. The operands must have the same shape and type, and this type must be an integer type. The result type has i1 element type and the same shape as the operands.

The result is `1` if the comparison is true and `0` otherwise. The comparison is performed element-wise and the element of the result indicates whether the comparison is true for the operand elements with the same indices as those of the result.

cmpi(x,y,pred)i\={1if xi pred yi0otherwise

The `comparison_predicate` attribute specifies the kind of comparison to be performed.

-   `equal` - Equal comparison.
-   `not_equal` - Not equal comparison.
-   `less_than` - Less than comparison.
-   `less_than_or_equal` - Less than or equal comparison.
-   `greater_than` - Greater than comparison.
-   `greater_than_or_equal` - Greater than or equal comparison.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id306 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs` and `rhs` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Result type has i1 element type and same shape as operands
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id307 "Link to this heading")

%lhs0 \= constant <i16: 0\> : tile<i16\>
%rhs0 \= constant <i16: 0\> : tile<i16\>

// Scalar "signed less than" comparison.
%x0 \= cmpi less\_than %lhs0, %rhs0, signed : tile<i16\> \-> tile<i1\>

%lhs1 \= constant <i64: 0\> : tile<2x2xi64\>
%rhs1 \= constant <i64: 0\> : tile<2x2xi64\>

// Tile equality comparison.
// There is no difference between "signed" and "unsigned" when performing equality and inequality comparison.
%x1 \= cmpi equal %lhs1, %rhs1, signed : tile<2x2xi64\> \-> tile<2x2xi1\>

Copy to clipboard

See [cuda\_tile.cmpi\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-cmpi-0) for the full example listing.

### 8.8.5. cuda\_tile.divi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-divi "Link to this heading")

_Element-wise integer division_

cuda\_tile.divi %lhs %rhs %signedness %rounding

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id308 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-divi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1
-   **rounding** ([RoundingMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-divi-roundingmode-attr)) - Set the rounding direction (implementing floordiv/ceildiv). 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id309 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the division. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id310 "Link to this heading")

The `divi` operation computes the element-wise division of two tile values with integer element type.

The default rounding is towards zero. The rounding mode can be set to positive\_inf (“ceiling division”), or negative\_inf (“floor division”), other values are illegal.

The use of the rounding flag negative\_inf with unsigned is not a valid combination.

If the unsigned flag is provided, the operands are treated as unsigned integers, otherwise they are treated as signed integers.

The behavior is undefined if the right hand side is zero. A signed division overflow (minimum value divided by -1) is undefined behavior.

div(lhs, rhs)i\=lhsi/rhsi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

The `rounding` attribute specifies the rounding mode to use for the operation.

-   `nearest_even` - Round to nearest (ties to even).
-   `zero` - Round towards zero (truncate).
-   `negative_inf` - Round towards negative infinity.
-   `positive_inf` - Round towards positive infinity.
-   `approx` - Approximate rounding mode.
-   `full` - Full precision rounding mode.
-   `nearest_int_to_zero` - Round towards zero to the nearest integer.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id311 "Link to this heading")

-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.6. cuda\_tile.maxi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-maxi "Link to this heading")

_Element-wise integer maximum_

cuda\_tile.maxi %lhs %rhs %signedness

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id312 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-maxi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id313 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the maxi operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id314 "Link to this heading")

The `maxi` operation computes the element-wise maximum between two input integer tiles.

maxi(x,y)i\={xiif xi≥yiyiif xi<yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id315 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id316 "Link to this heading")

// Create tensor view from a pointer to global memory
%0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
%1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
// Convert tensor views to partition views and load tiles from them.
%p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
%p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
%c0 \= constant <i32: 0\> : tile<i32\>
%2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
%3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
// Signless i32 treated as unsigned
%4 \= maxi %2, %3 unsigned : tile<2x4xi32\>
// Signless i32 treated as signed
%5 \= maxi %2, %3 signed : tile<2x4xi32\>

Copy to clipboard

See [cuda\_tile.maxi\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-maxi-0) for the full example listing.

### 8.8.7. cuda\_tile.mini[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-mini "Link to this heading")

_Element-wise integer minimum_

cuda\_tile.mini %lhs %rhs %signedness

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id317 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-mini-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id318 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The minimum of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id319 "Link to this heading")

The `mini` operation computes the element-wise minimum between the two input tiles with integer element types.

mini(x,y)i\={xiif xi≤yiyiif xi\>yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id320 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id321 "Link to this heading")

// Create tensor view from a pointer to global memory
%0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
%1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
// Convert tensor views to partition views and load tiles from partition views.
%p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
%p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
%c0 \= constant <i32: 0\> : tile<i32\>
%2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
%3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
// Signless i32 treated as unsigned
%4 \= mini %2, %3 unsigned : tile<2x4xi32\>
// Signless i32 treated as signed
%5 \= mini %2, %3 signed : tile<2x4xi32\>

Copy to clipboard

See [cuda\_tile.mini\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-mini-0) for the full example listing.

### 8.8.8. cuda\_tile.mmai[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-mmai "Link to this heading")

_Integer matrix-multiply-accumulate_

cuda\_tile.mmai %lhs %rhs %acc %signedness\_lhs %signedness\_rhs

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id322 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side matrix operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side matrix operand. 13.1
-   **acc** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The accumulator matrix operand. 13.1
-   **signedness\_lhs** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-mmai-signedness-attr)) - The signedness of the `lhs` operand. 13.1
-   **signedness\_rhs** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-mmai-signedness-attr)) - The signedness of the `rhs` operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id323 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result matrix after multiplication and accumulation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id324 "Link to this heading")

The `mmai` operation implements an MMA (matrix-multiply-accumulate) operation for integer tiles. It performs matrix multiplication on the integer tiles `lhs` and `rhs`, then adds the tile `acc` to the result. `lhs`, `rhs`, and `acc` must be 2D tiles or 3D tiles. The latter case indicates a batched matrix multiplication.

mmai(A,B,C)ij\=∑k\=0K−1Aik×Bkj+Cij

Input tiles `lhs` and `rhs` must be of integer type `i8`. The signedness of `lhs` and `rhs` are specified separately by the `signedness_lhs` and `signedness_rhs` attributes, respectively. The accumulator tile `acc` must be of type `i32` and is always interpreted as signed. The output tile `result` is of type `i32` and is always interpreted as signed.

Shapes must be a valid matrix multiplication configuration. Unbatched (2D) MMA expects the operands `lhs`, `rhs`, and `acc` to have shapes `M x K`, `K x N`, and `M x N` (respectively). Batched (3D) MMA expects the operands to have shapes `B x M x K`, `B x K x N`, and `B x M x N` (respectively).

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id325 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `acc` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   `lhs` and `rhs` must have the same element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   `lhs`, `rhs` and `acc` must have the same rank.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id326 "Link to this heading")

%lhs0 \= cuda\_tile.constant <i8: 0\> : tile<4x8xi8\>
%rhs0 \= cuda\_tile.constant <i8: 0\> : tile<8x2xi8\>
%acc0 \= cuda\_tile.constant <i32: 0\> : tile<4x2xi32\>

%0 \= mmai %lhs0, %rhs0, %acc0 signed signed
    : tile<4x8xi8\>, tile<8x2xi8\>,
      tile<4x2xi32\>

%lhs1 \= cuda\_tile.constant <i8: 0\> : tile<2x4x8xi8\>
%rhs1 \= cuda\_tile.constant <i8: 0\> : tile<2x8x2xi8\>
%acc1 \= cuda\_tile.constant <i32: 0\> : tile<2x4x2xi32\>

%1 \= mmai %lhs1, %rhs1, %acc1 unsigned unsigned
    : tile<2x4x8xi8\>, tile<2x8x2xi8\>,
      tile<2x4x2xi32\>

Copy to clipboard

See [cuda\_tile.mmai\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-mmai-0) for the full example listing.

### 8.8.9. cuda\_tile.muli[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-muli "Link to this heading")

_Element-wise integer multiplication_

cuda\_tile.muli %lhs %rhs %overflow

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id327 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side input integer tile. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side input integer tile. 13.1
-   **overflow** ([IntegerOverflow](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-muli-integeroverflow-attr)) - The overflow behavior of the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id328 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The product of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id329 "Link to this heading")

The `muli` operation computes the element-wise product between the two input tiles with integer element types.

muli(x,y)i\=xi×yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.

These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

-   `none` - The compiler makes no assumptions regarding overflow behavior.
-   `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
-   `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
-   `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.

If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id330 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.10. cuda\_tile.mulhii[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-mulhii "Link to this heading")

_Element-wise high bits of integer multiplication_

cuda\_tile.mulhii %x %y

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id331 "Link to this heading")

-   **x** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side input integer tile. 13.1
-   **y** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side input integer tile. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id332 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The most significant bits of the product of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id333 "Link to this heading")

The `mulhii` operation produces the most significant N bits of the 2N-bit product of two N-bit integer tiles. For `i64`, this is the most significant 64 bits of the full 128-bit product; for `i8`, it is the most significant 8 bits of the full 16-bit product; etc.

This is in contrast to `muli`, which produces the lower N bits of the 2N-bit product.

The `mulhii` operation is only defined for unsigned integers.

mulhii(xi,yi)\=xi×yi\>>bitwidth(type(xi))

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id334 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `x`, `y` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id335 "Link to this heading")

// 2^31 \* 2 = 2^32, or 0x100000000.
// The most significant 32 bits of the product are 0x00000001.
// The lower 32 bits of the product are 0x00000000.
%a \= constant <i32: 2147483648\> : tile<i32\>  // %a = 2^31
%b \= constant <i32: 2\> : tile<i32\>           // %b = 2
%res\_hi \= mulhii %a, %b : tile<i32\>          // %res\_hi = 1
%res\_lo \= muli %a, %b : tile<i32\>            // %res\_lo = 0

Copy to clipboard

See [cuda\_tile.mulhii\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-mulhii-0) for the full example listing.

### 8.8.11. cuda\_tile.negi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-negi "Link to this heading")

_Element-wise integer negation_

cuda\_tile.negi %source %overflow

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id336 "Link to this heading")

-   **source** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The input integer tile. 13.1
-   **overflow** ([IntegerOverflow](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-negi-integeroverflow-attr)) - The overflow behavior of the operation. 13.2

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id337 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The negated integer tile. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id338 "Link to this heading")

The `negi` operation computes the element-wise negation of the input integer tile. The input and output tiles are always interpreted as signed integers.

negi(xi)\=−xi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.

These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

-   `none` - The compiler makes no assumptions regarding overflow behavior.
-   `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
-   `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
-   `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.

If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id339 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `source` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id340 "Link to this heading")

%source \= constant <i16: \[0, 1, 2, 3\]\> : tile<4xi16\>
%result \= negi %source : tile<4xi16\>
// %result = \[0, -1, -2, -3\]

Copy to clipboard

See [cuda\_tile.negi\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-negi-0) for the full example listing.

### 8.8.12. cuda\_tile.ori[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-ori "Link to this heading")

_Element-wise bitwise OR_

cuda\_tile.ori %lhs %rhs

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id341 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id342 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The bitwise OR of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id343 "Link to this heading")

The `ori` operation computes the element-wise bitwise OR of two tiles with integer element types.

ori(x,y)i\=xi|yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id344 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.13. cuda\_tile.remi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-remi "Link to this heading")

_Element-wise integer remainder_

cuda\_tile.remi %lhs %rhs %signedness

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id345 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-remi-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id346 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The remainder after division. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id347 "Link to this heading")

The `remi` operation computes the element-wise remainder of the input tiles with integer element types using truncated division (rounding towards zero). Division by zero is undefined behavior.

remi(x,y)i\=xi−trunc(xi/yi)×yi

If the operation is signed, the sign of the result matches the sign of the dividend (`lhs`). For example:

-   `remi(7, 3) = 1`
-   `remi(7, -3) = 1`
-   `remi(-7, 3) = -1`
-   `remi(-7, -3) = -1`

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id348 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `result`, `lhs` and `rhs` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.14. cuda\_tile.shli[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-shli "Link to this heading")

_Element-wise shift-left_

cuda\_tile.shli %lhs %rhs %overflow

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id349 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand (shift amount). 13.1
-   **overflow** ([IntegerOverflow](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-shli-integeroverflow-attr)) - The overflow behavior of the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id350 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the left shift operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id351 "Link to this heading")

The `shli` operation computes the element-wise left shift of the `lhs` integer operand by the `rhs` operand. The lower-order bits on the right are filled with zeros.

shli(x,y)i\=xi≪yi

The `rhs` operand is interpreted as an unsigned integer.

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.

These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

-   `none` - The compiler makes no assumptions regarding overflow behavior.
-   `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
-   `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
-   `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.

If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id352 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.15. cuda\_tile.shri[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-shri "Link to this heading")

_Element-wise shift-right_

cuda\_tile.shri %lhs %rhs %signedness

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id353 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand (shift amount). 13.1
-   **signedness** ([Signedness](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-shri-signedness-attr)) - Interpret integer(s) as `signed` or `unsigned` 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id354 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the right shift operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id355 "Link to this heading")

The `shri` operation computes the element-wise right shift of the `lhs` integer operand by the value of the `rhs` operand for tiles with integer element types.

shri(x,y)i\=xi≫yi

When `unsigned`, higher-order bits are zero-filled; when `signed`, the higher-order bits are filled with the sign bit.

The `rhs` operand is always interpreted as an unsigned integer.

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `signedness` attribute specifies the signedness of operand(s).

-   `unsigned` - Treat the operands as unsigned integers.
-   `signed` - Treat the operands as signed integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id356 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.16. cuda\_tile.subi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-subi "Link to this heading")

_Element-wise integer subtraction_

cuda\_tile.subi %lhs %rhs %overflow

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id357 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1
-   **overflow** ([IntegerOverflow](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-subi-integeroverflow-attr)) - The overflow behavior of the operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id358 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The result of the subtraction. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id359 "Link to this heading")

The `subi` operation computes the element-wise subtraction of two input integer tiles.

subi(x,y)i\=xi−yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

The `overflow` attribute is used to instruct the compiler on how to reason about the overflow behavior of the specific operation.

These attributes serve as assumptions that the compiler may use to reason about the operation. It is the responsibility of the code generator to ensure that the operation respects these assumptions dynamically during execution.

-   `none` - The compiler makes no assumptions regarding overflow behavior.
-   `no_signed_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands signed integers.
-   `no_unsigned_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands unsigned integers.
-   `no_wrap` - The compiler assumes that overflow (wrap-around) will not occur when interpreting the operands as signed or unsigned integers.

If an overflow occurs at runtime despite the value of overflow stating otherwise, the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id360 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

### 8.8.17. cuda\_tile.xori[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-xori "Link to this heading")

_Element-wise bitwise XOR_

cuda\_tile.xori %lhs %rhs

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id361 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id362 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The bitwise XOR of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id363 "Link to this heading")

The `xori` operation computes the element-wise bitwise exclusive or (XOR) of two tile values with integer element types.

xori(x,y)i\=xi⊕yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id364 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id365 "Link to this heading")

%lhs \= constant <i32: \[0, 1, 2, 3\]\> : tile<4xi32\>
%rhs \= constant <i32: \[4, 5, 6, 7\]\> : tile<4xi32\>
// This computes the bitwise XOR of each element in \`%lhs\` and \`%rhs\`, which
// are tiles of shape \`4xi32\`, and returns the result as \`%result\`.
%result \= xori %lhs, %rhs : tile<4xi32\>

Copy to clipboard

See [cuda\_tile.xori\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-xori-0) for the full example listing.

## 8.9. Bitwise[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#bitwise "Link to this heading")

### 8.9.1. cuda\_tile.andi[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-andi "Link to this heading")

_Element-wise bitwise logical AND_

cuda\_tile.andi %lhs %rhs

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id366 "Link to this heading")

-   **lhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The left hand side operand. 13.1
-   **rhs** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The right hand side operand. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id367 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The bitwise AND of the input tiles. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id368 "Link to this heading")

The `andi` operation produces a value that is the result of an element-wise, bitwise “and” of two tiles with integer element type.

andi(x,y)i\=xi∧yi

Element-wise integer arithmetic operations are performed by the target architecture’s native integer instructions. The default semantics are wrap-around semantics on overflow or underflow. See [Integer Arithmetic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sub-section-integer-arithmetic) for more details.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id369 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.
-   `lhs`, `rhs` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i8](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i16](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i32](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types) | [i64](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>).
-   Operation must infer result types from operands and attributes.

## 8.10. Atomics[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#atomics "Link to this heading")

Warning

Atomic operations are limited in **Tile IR** as of early-access and will be updated in coming releases in accordance with the incoming memory model and memory operation updates.

### 8.10.1. cuda\_tile.atomic\_cas\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-atomic-cas-tko "Link to this heading")

_Atomic compare-and-swap on global memory_

cuda\_tile.atomic\_cas\_tko %memory\_ordering\_semantics %memory\_scope %pointers %cmp %val %mask %token

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id370 "Link to this heading")

-   **memory\_ordering\_semantics** ([MemoryOrderingSemantics](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-atomic-cas-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the atomic operation. 13.1
-   **memory\_scope** ([MemoryScope](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-atomic-cas-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
-   **pointers** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The pointers to the memory locations to perform the atomic compare-and-swap operation on. 13.1
-   **cmp** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The values to compare against. 13.1
-   **val** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The values to swap in. 13.1
-   **mask** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The mask for the atomic operation. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The token for the atomic operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id371 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The result of the atomic operation. 13.1
-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token of the atomic operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id372 "Link to this heading")

The `atomic_cas` operation performs element-wise, atomic compare-and-swaps at the specified global memory `pointers`. The data in memory is compared to `cmp` and the data written to memory is specified by `val`. The operation returns the original value that was stored in memory before the atomic operation was performed.

The shape (and the element type) of `pointers`, `cmp`, `val` and `result` must match. The `atomic_cas` operation performs the following steps for every `(pointer, cmp, val)` tuple in one atomic transaction. (One atomic transaction per tuple.)

  atomic() {
    x \= \*pointer
    if x \== cmp {
    \*pointer \= val
  }
  return x
}

Copy to clipboard

An optional parameter, `mask`, allows specifying which elements participate in the atomic operation. A false value at position i masks out the corresponding element in `pointers`, excluding it from the operation. The returned value for a masked element at position i is `cmp[i]`. If no mask is provided, all elements are included in the computation by default. The shape of mask must match that of `pointers`, `cmp`, and `val`.

A token-ordered atomic compare-and-swap is not constrained by program order. The compiler may reorder it (i.e. place them earlier or later in program order) unless constrained by tokens.

Supported data types:

-   i32, i64: integer values
-   f32, f64: floating-point values

For floating-point types, the comparison uses bitwise equality rather than IEEE-754 semantics. This means different `NaN` bit patterns are treated as distinct values, and `+0.0` and `-0.0` are considered different if their bit representations differ.

The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model) of the specification.

-   `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
-   `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then _happens before_ is established.
-   `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then _happens before_ is established.
-   `acq_rel` - There may be concurrent accesses to the location. This has the effect of both a release and acquire operation.

Note: The following variants are not supported by this operation: `weak`.

The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.

-   `tl_blk` - There may be concurrent accesses from within the same tile block.
-   `device` - There may be concurrent accesses from within the same device (i.e., GPU).
-   `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id373 "Link to this heading")

-   `cmp`, `val` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)).
-   Operation must encode variadic operand segment sizes in attributes.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id374 "Link to this heading")

%ptr\_1x \= reshape %ptr : tile<ptr<i32\>> \-> tile<1xptr<i32\>>
%ptr\_vec \= broadcast %ptr\_1x : tile<1xptr<i32\>> \-> tile<8xptr<i32\>>
%offsets \= iota : tile<8xi32\>
%ptrs \= offset %ptr\_vec, %offsets : tile<8xptr<i32\>>, tile<8xi32\> \-> tile<8xptr<i32\>>
%cmp \= constant <i32: \[0, 1, 2, 3, 4, 5, 6, 7\]\> : tile<8xi32\>
%val \= constant <i32: \[7, 6, 5, 4, 3, 2, 1, 0\]\> : tile<8xi32\>
%mask \= constant <i1: \[0, 1, 0, 1, 0, 1, 0, 1\]\> : tile<8xi1\>

// Atomic CAS without input token.
%0, %token \= atomic\_cas\_tko relaxed device %ptrs, %cmp, %val :
  tile<8xptr<i32\>>, tile<8xi32\> \-> tile<8xi32\>, token

// Atomic CAS without input token.
%1, %token1 \= atomic\_cas\_tko relaxed device %ptrs, %cmp, %val, %mask :
  tile<8xptr<i32\>>, tile<8xi32\>, tile<8xi1\> \-> tile<8xi32\>, token

// Atomic CAS with input token.
%token2 \= make\_token : token
%2, %token3 \= atomic\_cas\_tko relaxed device %ptrs, %cmp, %val token\=%token2 :
  tile<8xptr<i32\>>, tile<8xi32\> \-> tile<8xi32\>, token

return

Copy to clipboard

See [cuda\_tile.atomic\_cas\_tko\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-atomic-cas-tko-0) for the full example listing.

### 8.10.2. cuda\_tile.atomic\_rmw\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-atomic-rmw-tko "Link to this heading")

_Atomic read-modify-write on global memory_

cuda\_tile.atomic\_rmw\_tko %memory\_ordering\_semantics %memory\_scope %pointers %mode %arg %mask %token

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id375 "Link to this heading")

-   **memory\_ordering\_semantics** ([MemoryOrderingSemantics](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-atomic-rmw-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the load operation. 13.1
-   **memory\_scope** ([MemoryScope](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-atomic-rmw-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
-   **pointers** ([ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)) - The pointer tile to perform atomic operation on. 13.1
-   **mode** ([AtomicRMWMode](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-atomic-rmw-tko-atomicrmwmode-attr)) - The atomic operation mode (e.g., add, max, min, etc.). 13.1
-   **arg** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The value tile to use in the atomic operation. 13.1
-   **mask** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[i1](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#subsection-element-types)\>) - The mask for the load operation. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The token for the atomic operation. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id376 "Link to this heading")

-   **result** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The result of the atomic operation. 13.1
-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token of the load operation. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id377 "Link to this heading")

The `atomic_rmw_tko` operation performs element-wise, atomic read-modify-write operations at the global memory locations specified by `pointers`. The values written to memory are determined by `mode` and `arg`. The operation returns the original value stored at each location before the atomic update.

The shapes of `pointers`, `arg`, and `result` must match. The element type of the pointer type must match the element types of both `arg` and `result`. Each (`pointer`, `arg`) pair is processed in a single atomic transaction.

atomic {
  x \= \*pointer
  y \= mode(x, arg)
  \*pointer \= y
  return x
}

Copy to clipboard

An optional parameter, `mask`, specifies which elements participate in the atomic operation. A False value at position `i` excludes the corresponding element in `pointers` from the operation. The value returned for a masked-out element is implementation-defined. The shape of `mask` must match the shape of `pointers`.

The `atomic_addf` operation is defined to round to the nearest even value. .. note:: The current implementation of the compiler flushes denormals to zero. This behavior will be fixed in a future version of the compiler and users should not rely on it.

Token-ordered atomic read-modify-write operations are not constrained by program order. The compiler may reorder them (i.e., move them earlier or later in the program) unless further constrained by tokens.

Supported data types by `mode`:

> -   ADD, AND, MAX, MIN, OR, UMAX, UMIN, XOR: i32, i64
> -   ADDF: f16, f32, f64
> -   XCHF: i32, i64, f32, f64

The `U` prefix in UMAX and UMIN distinguishes these from their signed counterparts (MAX and MIN) by interpreting the comparison as unsigned.

The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model) of the specification.

-   `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
-   `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then _happens before_ is established.
-   `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then _happens before_ is established.
-   `acq_rel` - There may be concurrent accesses to the location. This has the effect of both a release and acquire operation.

Note: The following variants are not supported by this operation: `weak`.

The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.

-   `tl_blk` - There may be concurrent accesses from within the same tile block.
-   `device` - There may be concurrent accesses from within the same device (i.e., GPU).
-   `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).

The `mode` attribute specifies the mode of the atomic read-modify-write operation.

-   `and` - Perform bitwise AND as the modification operation.
-   `or` - Perform bitwise OR as the modification operation.
-   `xor` - Perform bitwise XOR as the modification operation.
-   `add` - Perform integer addition as the modification operation.
-   `addf` - Perform floating-point addition as the modification operation.
-   `max` - Perform maximum as the modification operation.
-   `min` - Perform minimum as the modification operation.
-   `umax` - Perform unsigned maximum as the modification operation.
-   `umin` - Perform unsigned minimum as the modification operation.
-   `xchg` - Perform exchange as the modification operation.

The `mode` attribute has a default value of `add`.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id378 "Link to this heading")

-   `arg` and `result` must have the same shape and element type ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)).
-   Operation must encode variadic operand segment sizes in attributes.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id379 "Link to this heading")

// Reshape the input pointer tile to have a 1d shape
%ptr\_1x \= reshape %ptr : tile<ptr<f32\>> \-> tile<1xptr<f32\>>
// Broadcast the reshaped tile to a tile with 8 rows, effectively replicating the pointer 8 times
%ptr\_vec \= broadcast %ptr\_1x : tile<1xptr<f32\>> \-> tile<8xptr<f32\>>
// Create a tile of offsets \[0, 1, 2, ..., 7\] to index into memory
%offsets \= iota : tile<8xi32\>
// Add the offsets to each pointer in the vector to create 8 unique pointers
%ptrs \= offset %ptr\_vec, %offsets : tile<8xptr<f32\>>, tile<8xi32\> \-> tile<8xptr<f32\>>
%vals \= constant <f32: \[7.0, 6.0, 5.0, 4.0, 3.0, 2.0, 1.0, 0.0\]\> : tile<8xf32\>

// Perform atomic addf operations on the memory locations pointed by %ptrs
// without requiring an input token. Returns the original values and a result token
%0, %res\_token0 \= atomic\_rmw\_tko relaxed device %ptrs, addf, %vals :
    tile<8xptr<f32\>>, tile<8xf32\> \-> tile<8xf32\>, token

// Perform atomic add operations again, this time using the explicit input token
%token \= make\_token : token
%1, %res\_token1 \= atomic\_rmw\_tko relaxed device %ptrs, addf, %vals, token \= %token :
    tile<8xptr<f32\>>, tile<8xf32\> \-> tile<8xf32\>, token

Copy to clipboard

See [cuda\_tile.atomic\_rmw\_tko\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-atomic-rmw-tko-0) for the full example listing.

## 8.11. Views[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#views "Link to this heading")

Views are a structured way to interact with tensors in memory. They are described in both the types section [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#sub-sec-view-types) and the semantics section [Views](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/semantics.html#section-semantics-sub-section-views).

Views are the primary way to interact with global memory in **Tile IR**. A common pattern is to construct a [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) from a pointer with [cuda\_tile.make\_tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-make-tensor-view) and then use the [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko) operations to read and write to them. For larger tensors, loading the entire tensor is not efficient and therefore we have a sub-view [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) which allows a user to tile a `tensor_view`.

### 8.11.1. cuda\_tile.get\_index\_space\_shape[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-get-index-space-shape "Link to this heading")

_Query the index space dimension size_

cuda\_tile.get\_index\_space\_shape %src

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id380 "Link to this heading")

-   **src** ([view\_type](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-views)) - The source view type. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id381 "Link to this heading")

-   **result** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>\>) - The shape of the index space, each value representing the size of the
    
    corresponding dimension. 13.1
    

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id382 "Link to this heading")

The `get_index_space_shape` operation returns the shape of the index space of `src`.

The result tile has the same rank as the view’s index space with the elements representing the size of the corresponding dimension.

The result values should be interpreted as unsigned integers.

Warning

If the individual index space dimension do not fit in the result tile’s element type the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id383 "Link to this heading")

-   Operation must not perform any memory side effects.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id384 "Link to this heading")

%tensor\_view \= make\_tensor\_view %base,
    shape \= \[2, 2, 4\], strides \= \[2, 2, 1\]
    : tensor\_view<2x2x4xf32, strides\=\[2,2,1\]\>
%partition\_view \= make\_partition\_view %tensor\_view :
  partition\_view<tile\=(2x2x4), tensor\_view<2x2x4xf32, strides\=\[2,2,1\]\>>
%dim0, %dim1, %dim2 \= get\_index\_space\_shape %partition\_view :
  partition\_view<tile\=(2x2x4), tensor\_view<2x2x4xf32, strides\=\[2,2,1\]\>> \-> tile<i64\>

Copy to clipboard

See [cuda\_tile.get\_index\_space\_shape\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-get-index-space-shape-0) for the full example listing.

### 8.11.2. cuda\_tile.get\_tensor\_shape[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-get-tensor-shape "Link to this heading")

_Query the shape of a tensor view_

cuda\_tile.get\_tensor\_shape %src

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id385 "Link to this heading")

-   **src** ([tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view)) - The source tensor view. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id386 "Link to this heading")

-   **result** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>\>) - The shape of the tensor, each value representing the size of the corresponding dimension. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id387 "Link to this heading")

The `get_tensor_shape` operation returns the shape of the tensor backing the provided tensor view.

The result values should be interpreted as unsigned integers.

Warning

If the tensor dimensions do not fit in the result tile’s element type the behavior is undefined.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id388 "Link to this heading")

-   Operation must not perform any memory side effects.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id389 "Link to this heading")

%dim0, %dim1 \= get\_tensor\_shape %tensor\_view : tensor\_view<32x32xf32, strides\=\[32,1\]\> \-> tile<i64\>

Copy to clipboard

See [cuda\_tile.get\_tensor\_shape\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-get-tensor-shape-0) for the full example listing.

### 8.11.3. cuda\_tile.load\_view\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-load-view-tko "Link to this heading")

_Load a tile from a tile view_

cuda\_tile.load\_view\_tko %memory\_ordering\_semantics %memory\_scope %view %index %token %optimization\_hints

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id390 "Link to this heading")

-   **memory\_ordering\_semantics** ([MemoryOrderingSemantics](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-load-view-tko-memoryorderingsemantics-attr)) - The memory ordering semantics for the load operation. 13.1
-   **memory\_scope** ([MemoryScope](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-load-view-tko-memoryscope-attr)) - The memory scope for the atomic operation. 13.1
-   **view** ([view\_type](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-views)) - The view from which the tile will be loaded. 13.1
-   **index** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>\>) - The n-dimensional index of the desired element to load from the view. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The optional token for the load operation. 13.1
-   **optimization\_hints** ([OptimizationHints](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-load-view-tko-optimizationhints-attr)) - Optimization hints for operation 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id391 "Link to this heading")

-   **tile** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The loaded tile. 13.1
-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id392 "Link to this heading")

The `load_view_tko` operation loads a tile from a tile view.

A view is mapping from view-space indices to a particular element in the view, each view type has a defined mapping from view-space indices to tiles produced from elements of the view.

For example, the [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) partitions a [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) into a grid of equally sized tiles. The view indexes one of the partitioned tiles in the grid.

For a given view the rank of the indices must match the rank of the view’s index space. The space of valid indices depends on which view is passed to the operation. For example the index space of a [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) is equal to the rank of the partitioned tiles.

The `index` operands are interpreted as unsigned integers.

Out of bounds accesses are handled according to the semantics of [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view).

The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model) of the specification.

-   `weak` - No concurrent accesses to the source/destination location.
-   `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
-   `acquire` - There may be concurrent accesses to the location. If this acquire observes a release operation, then _happens before_ is established.

Note: The following variants are not supported by this operation: `release`, `acq_rel`.

The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.

-   `tl_blk` - There may be concurrent accesses from within the same tile block.
-   `device` - There may be concurrent accesses from within the same device (i.e., GPU).
-   `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).

The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.

The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.

-   `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda\_tile.entry](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-entry).
-   `allow_tma` - suggest whether to use TMA for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).
-   `latency` - latency hint for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).

For example they can be annotated as:

optimization\_hints\=<
  sm\_100 \= {num\_cta\_in\_cga \= 8},
  sm\_120 \= {num\_cta\_in\_cga \= 16}
\>

Copy to clipboard

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id393 "Link to this heading")

-   Operation must encode variadic operand segment sizes in attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id394 "Link to this heading")

%tensor\_view \= make\_tensor\_view %ptr, shape\=\[8192, 128\], strides\=\[128, 1\]
  : tensor\_view<8192x128xf32, strides\=\[128,1\]\>

// This example uses the PartitionView on a 8192x128xf32 tensor\_view,
// dividing the tensor\_view in tiles of 64x64.

%view \= make\_partition\_view %tensor\_view : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>

%c0 \= constant <i32: 0\> : tile<i32\>
%c1 \= constant <i32: 1\> : tile<i32\>

// Load a tile at index (0, 0) in the view's index space.
// For this PartitionView, this is the rectangular tile such that
// X=\[0,64) and Y=\[0,64), in the coordinates of tiles.
%tile0, %res\_token0 \= load\_view\_tko weak %view\[%c0, %c0\]
  : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

// Load a tile at index (0, 1) in the view's index space.
// For this PartitionView, this is the rectangular tile such that
// X=\[0,64) and Y=\[64,128), in the coordinates of tiles.
%tile1, %res\_token1 \= load\_view\_tko weak %view\[%c0, %c1\]
  : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

// Same example as above but with memory token as input.
%token \= make\_token : token
%tile2, %res\_token2 \= load\_view\_tko weak %view\[%c0, %c1\] token \= %token
  : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

// Loads a tile at the dynamic index (%index, %index) in the view's index space.
%tile3, %res\_token3 \= load\_view\_tko weak %view\[%index, %index\]
  : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

Copy to clipboard

See [cuda\_tile.load\_view\_tko\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-load-view-tko-0) for the full example listing.

### 8.11.4. cuda\_tile.make\_partition\_view[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-make-partition-view "Link to this heading")

_Create a partition view from a tensor view_

cuda\_tile.make\_partition\_view %tensor\_view

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id395 "Link to this heading")

-   **tensor\_view** ([tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view)) - The source tensor view to create a partition view from. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id396 "Link to this heading")

-   **result** ([partition\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view)) - The created partition view. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id397 "Link to this heading")

The `make_partition_view` operation creates a [partition\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) from a [tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view). For more details about partition views see [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view).

The operation uses the type constraints of the input tensor view and the annotated return type to perform the partitioning. The tensor view’s type contains its physical layout in the form of shapes and strides and the partition view contains the logical size of a single tile.

The resulting partition view can be loaded from using [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and stored to using [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).

The view memory options act on the computed index space of the partition view, see [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) and [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) for detailed semantics.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id398 "Link to this heading")

-   Operation speculation safety must be determined by operands and attributes.
-   Operation must be safe to execute speculatively without side effects.
-   Operation must not perform any memory side effects.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id399 "Link to this heading")

%tensor\_view0 \= make\_tensor\_view %ptr, shape\=\[8192, 8192, 64\], strides\=\[524288,64,1\]
  : tensor\_view<8192x8192x64xf32, strides\=\[524288,64,1\]\>

// Creates a partition with 32-bit-indexed tiles of size (1024x1x32) over
// the provided tensor\_view.
make\_partition\_view %tensor\_view0 :
  partition\_view<
    tile\=(1024x1x32),
    tensor\_view<8192x8192x64xf32, strides\=\[524288,64,1\]\>
  \>

%s0 \= constant <i32: 8192\> : tile<i32\>
%str0 \= constant <i32: 524288\> : tile<i32\>

%tensor\_view1 \= make\_tensor\_view %ptr, shape\=\[%s0, 8192, 64\], strides\=\[%str0, 64, 1\]
  : tile<i32\> \-> tensor\_view<?x8192x64xf32, strides\=\[?,64,1\]\>

// Creates a partition with 32-bit-indexed tiles of size (1024x1x32) over
// the provided tensor\_view. The provided tensor\_view has a
// dynamically-sized dimension.
make\_partition\_view %tensor\_view1 :
  partition\_view<tile\=(1024x1x32), tensor\_view<?x8192x64xf32, strides\=\[?,64,1\]\>>

Copy to clipboard

See [cuda\_tile.make\_partition\_view\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-make-partition-view-0) for the full example listing.

### 8.11.5. cuda\_tile.make\_tensor\_view[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-make-tensor-view "Link to this heading")

_Create :code:\`tensor\_view\` from a pointer to global memory_

cuda\_tile.make\_tensor\_view %base %dynamicShape %dynamicStrides

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id400 "Link to this heading")

-   **base** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[ptr](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-ptr)\>) - The scalar base pointer to a portion of global memory. 13.1
-   **dynamicShape** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>\>) - The array of values representing the shape of the view, may be fully dynamic. 13.1
-   **dynamicStrides** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>\>) - The array of values representing the strides of the view, may be fully dynamic. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id401 "Link to this heading")

-   **result** ([tensor\_view](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view)) - The constructed tensor\_view. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id402 "Link to this heading")

The `make_tensor_view` operation constructs a `tensor_view` from a global memory pointer, a dynamic shape and dynamic strides. See [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) for more details.

The constructor supports taking dynamic arrays for shapes and strides as part of the constructor enabling workloads to take global memory tensors of dynamic shape and strides. If these arguments are static they will be statically reflected in the type of the resulting `tensor_view`, if they are dynamic they will appear as `?` in the type. See below for concrete examples.

The `dynamicShape` and `dynamicStrides` operands are interpreted as unsigned integers.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id403 "Link to this heading")

-   Operation must encode variadic operand segment sizes in attributes.
-   Operation must not perform any memory side effects.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id404 "Link to this heading")

  // tensor\_view to a scalar tile of f32
  %a0 \= make\_tensor\_view %base,
      shape \= \[\], strides \= \[\] : tensor\_view<f32\>

  // tensor\_view to a tile of static shape and strides
  %a1 \= make\_tensor\_view %base,
      shape \= \[32, 32\], strides \= \[32, 1\]
      : tensor\_view<32x32xf32, strides\=\[32,1\]\>

%sh0 \= constant <i32: 32\> : tile<i32\>
%sh1 \= constant <i32: 32\> : tile<i32\>
%st0 \= constant <i32: 32\> : tile<i32\>
%st1 \= constant <i32: 1\> : tile<i32\>

  // tensor\_view to a tile with partially dynamic shape and strides
  // all dynamic values must be of the same type, here tile<i32>
  %a2 \= make\_tensor\_view %base,
          shape \= \[%sh0, %sh1\], strides \= \[%st0, %st1\]
          : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,?\]\>

Copy to clipboard

See [cuda\_tile.make\_tensor\_view\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-make-tensor-view-0) for the full example listing.

### 8.11.6. cuda\_tile.store\_view\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-store-view-tko "Link to this heading")

_Stores a tile into a tile view_

cuda\_tile.store\_view\_tko %memory\_ordering\_semantics %memory\_scope %tile %view %index %token %optimization\_hints

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id405 "Link to this heading")

-   **memory\_ordering\_semantics** ([MemoryOrderingSemantics](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-store-view-tko-memoryorderingsemantics-attr)) - The memory scope for the store operation. 13.1
-   **memory\_scope** ([MemoryScope](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-store-view-tko-memoryscope-attr)) - The memory scope for the store operation. 13.1
-   **tile** ([tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)) - The tile to store. 13.1
-   **view** ([view\_type](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-views)) - The view to store the tile to. 13.1
-   **index** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)<[any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)\>\>) - The indices of the desired target tile within the view. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The optional token for operation ordering. 13.1
-   **optimization\_hints** ([OptimizationHints](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-store-view-tko-optimizationhints-attr)) - Optimization hints for operation 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id406 "Link to this heading")

-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token for synchronization. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id407 "Link to this heading")

The `store_view_tko` operation stores a tile to a view indexing into a tile view.

A view is mapping from view-space indices to a particular element in the view, each view type has a defined mapping from view-space indices to tiles produced from elements of the view.

For example, the [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) partitions a [Tensor View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tensor-view) into a grid of equally sized tiles. The view indexes one of the partitioned tiles in the grid.

For a given view the rank of the indices must match the rank of the view’s index space. The space of valid indices depends on which view is passed to the operation. For example the index space of a [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view) is equal to the rank of the partitioned tiles.

The index space of the view is computed a function of the requested tile size and the shape of the view.

The `index` operands are interpreted as unsigned integers.

Out of bounds accesses are handled according to the semantics of [Partition View](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-partition-view).

The `memory_ordering_semantics` attribute specifies the concurrency assumption between memory accesses in different threads, which controls the synchronization required. For example, `weak` ordering allows the compiler to assume that there are no concurrent accesses to any accessed location. For more information, refer to the [memory model section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/memory_model.html#section-memory-model) of the specification.

-   `weak` - No concurrent accesses to the source/destination location.
-   `relaxed` - There may be concurrent access to the location, but this access does not establish a happens-before relationship.
-   `release` - There may be concurrent access to the location. If this release is observed with an acquire operation, then _happens before_ is established.

Note: The following variants are not supported by this operation: `acquire`, `acq_rel`.

The `memory_scope` attribute specifies a communication scope for memory operations. When communicating with other concurrent threads in the system, the scope must be broad enough to encompass all other threads which are participating in the communication, or data races may occur.

-   `tl_blk` - There may be concurrent accesses from within the same tile block.
-   `device` - There may be concurrent accesses from within the same device (i.e., GPU).
-   `sys` - There may be concurrent accesses from anywhere within the system (i.e., all devices).

The `optimization_hints` attribute provides architecture-specific compiler hints in the form of nested dictionaries.

The hints are specified for each architecture (e.g., `sm_100`, `sm_120`) and for each architecture the user can specify specific hints for each operation.

-   `num_cta_in_cga` - suggest the number of CTAs in a CGA (which must be the power of 2 less than or equal to 16) for [cuda\_tile.entry](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-entry).
-   `allow_tma` - suggest whether to use TMA for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).
-   `latency` - latency hint for [cuda\_tile.load\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-load-view-tko) and [cuda\_tile.store\_view\_tko](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-cuda-tile-store-view-tko).

For example they can be annotated as:

optimization\_hints\=<
  sm\_100 \= {num\_cta\_in\_cga \= 8},
  sm\_120 \= {num\_cta\_in\_cga \= 16}
\>

Copy to clipboard

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id408 "Link to this heading")

-   Operation must encode variadic operand segment sizes in attributes.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id409 "Link to this heading")

%tensor\_view \= make\_tensor\_view %ptr, shape\=\[8192, 128\], strides\=\[128,1\] :
  tensor\_view<8192x128xf32, strides\=\[128,1\]\>

// This example uses the PartitionView on a 8192x128xf32 tensor\_view,
// dividing the tensor\_view in tiles of 64x64.
%view \= make\_partition\_view %tensor\_view :
  partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>

%c0 \= constant <i32: 0\> : tile<i32\>
%c1 \= constant <i32: 1\> : tile<i32\>

%tile \= constant <f32: 0.0\> : tile<64x64xf32\>

// Store a tile at index (0, 0) in the view's index space.
// For this TilePartitionView, this is the rectangular tile such that
// X=\[0,64) and Y=\[0,64), in the coordinates of tiles.
%res\_token0 \= store\_view\_tko weak %tile, %view\[%c0, %c0\]
  : tile<64x64xf32\>, partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> token

// Store a tile at index (0, 1) in the view's index space.
// For this PartitionView, this is the rectangular tile such that
// X=\[0,64) and Y=\[64,128), in the coordinates of tiles.
%res\_token1 \= store\_view\_tko weak %tile, %view\[%c0, %c1\]
  : tile<64x64xf32\>, partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> token

// Same example as above but with input token.
%token \= make\_token : token
%res\_token2 \= store\_view\_tko weak %tile, %view\[%c0, %c1\] token \= %token
  : tile<64x64xf32\>, partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> token

Copy to clipboard

See [cuda\_tile.store\_view\_tko\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-store-view-tko-0) for the full example listing.

## 8.12. Miscellaneous[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#miscellaneous "Link to this heading")

The set of miscellaneous operations in **Tile IR** are operations which do not have a specific category.

### 8.12.1. cuda\_tile.assume[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-assume "Link to this heading")

_Attach static information to an SSA value_

cuda\_tile.assume %value %predicate

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id410 "Link to this heading")

-   **value** ([Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)) - The value to attach the predicate to. 13.1
-   **predicate** ([AssumePredicate](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#op-attribute-cuda-tile-assume-assumepredicate-attr)) - The predicate to attach to the value. 13.1

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id411 "Link to this heading")

-   **result** ([Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)) - The value with the attached predicate. 13.1

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id412 "Link to this heading")

The `assume` operation passes through `value` as the result and attaches a predicate to it. The assumed predicate is a property of `result`.

This operation can be used to inject static information into the compiler, potentially resulting in more efficient code generation.

`predicate` must implement the `AssumePredicateAttrInterface`.

Note

`assume` does not check the correctness of the predicate. Incorrect predicates may inject incorrect static information and cause miscompilation. If an incorrect predicate is attached to an SSA value, the behavior of the program is undefined.

#### AssumePredicate Implementers[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#assumepredicate-implementers "Link to this heading")

#### Bounded[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#bounded "Link to this heading")

#bounded<(lb|?), (ub|?)\>

Copy to clipboard

The `bounded` attribute must be used as a predicate for `cuda_tile.assume`. The predicated value must be a tile of integers.

`bounded` specifies a lower and upper bound for all elements of the predicated tile when interpreted as signed integers. Bounds are optional: it is possible to leave a bound unspecified, as indicated by “?” in the assembly format. E.g., `#bounded<0, ?>`. Both lower bound and upper bound are inclusive.

The lower bounds must be less than or equal to the upper bound. A lower/ upper bound that exceeds the range of valid values of the predicated value is invalid.

%1 \= cuda\_tile.assume #cuda\_tile.bounded<0, ?\>, %0
    : !cuda\_tile.tile<4x8xi16\>

Copy to clipboard

#### DivBy[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#divby "Link to this heading")

div\_by< $divisor (, every $every^ along $along)?\>

Copy to clipboard

The `div_by` attribute must be used as a predicate for `cuda_tile.assume` ops. The predicated value must be a `tile` of integers or pointers, or a `tensor_view`.

If the predicated value is a `tile`, the attribute indicates that some elements of the `tile` are divisible by `divisor`. If the predicated value is a `tensor_view` the attribute indicates that the base address of the `tensor_view` is divisible by `divisor`. `divisor` must be a positive power of `2`.

The `every` and `along` attributes control which elements are assumed to satisfy the divisibility property. When splitting the tensor in groups of size `every` along dimension `along`, the first element of each group is assumed to satisfy the divisibility property. The other elements are assumed to be monotonically increasing by `1` within the group. In case of a `tile` of pointers, the elements are assumed to be monotonically increasing by the byte width of the pointee type. The size of the last group may be smaller than `every`.

The `every` and `along` attributes are optional. When missing, they are assumed to have a default value of `1` and `0` in case of a `tile`. I.e., all elements of the `tile` are assumed to satisfy the divisibility property. (The value of `along` does not matter in that case.) If the predicated value is a `tensor_view` or a 0D `tile`, `every` and `along` cannot be used.

`every`, and `along` must be used together. If one is specified, so must be the other.

Note

If the predicated value is a tile of integers, `every` is a property of the signed interpretation of the integer values. Otherwise, it is a property of the unsigned integer interpretation. E.g., `every = 4` is incorrect for the following sequence of “i8” values (written in binary form) because they wrap around when interpreted as signed integers: `[01111110, 01111111, 10000000, 10000001]`. `every = 2` would be correct.

The examples below demonstrate tensors that satisfy the assumed properties.

// Example 1: Each pointer is divisible by 16.
// \[ 0x10, 0x20, 0x80, 0x10, 0x0, 0x120, ... \]
%0 \= cuda\_tile.assume #cuda\_tile.div\_by<16\>, %ptrs
    : !cuda\_tile.tile<128x!cuda\_tile.ptr<f32\>>
// Note: Equivalent to #cuda\_tile.div\_by<16, every 1 along 0>.

Copy to clipboard

// Example 2: Each integer is divisible by 4.
// \[ 16, 24, 8, 4, 12, 12, 0, 16, ... \]
%0 \= cuda\_tile.assume #cuda\_tile.div\_by<4\>, %t
    : !cuda\_tile.tile<128xi32\>

Copy to clipboard

// Example 3: Group size \[4\].
// \[7, 8, 9, 10, 23, 24, 25, 26, 0, 1, 2, 3, ...\]
%0 \= cuda\_tile.assume #cuda\_tile.div\_by<1, every 4 along 0\>, %t
    : !cuda\_tile.tile<128xi32\>

Copy to clipboard

// Example 4: 2-d Group size \[1, 4\] with divisibility 4.
// \[ \[  4,  5,  6,  7, 12, 13, 14, 15 \],
//   \[  8,  9, 10, 11, 24, 25, 26, 27 \],
//   \[ 24, 25, 26, 27, 64, 65, 66, 67 \],
//   \[  0,  1,  2,  3,  4,  5,  6,  7 \] \]
%0 \= cuda\_tile.assume #cuda\_tile.div\_by<4, every 4 along 1\>, %t
    : !cuda\_tile.tile<4x8xi32\>

Copy to clipboard

// Example 5: 2-d Group size \[4, 1\] with divisibility 32.
// Note that the elements within each column are monotonically increasing
// by the byte width of the pointee type f32, e.g., 0x20, 0x24, 0x28, 0x2c.
// \[ \[  0x20, 0x100,  0x40,  0x60,  0x40, 0x200, 0x340,  0x40 \],
//   \[  0x24, 0x104,  0x44,  0x64,  0x44, 0x204, 0x344,  0x44 \],
//   \[  0x28, 0x108,  0x48,  0x68,  0x48, 0x208, 0x348,  0x48 \],
//   \[  0x2c, 0x10c,  0x4c,  0x6c,  0x4c, 0x20c, 0x34c,  0x4c \] \]
%0 \= cuda\_tile.assume #cuda\_tile.div\_by<32, every 4 along 0\>, %ptrs
    : !cuda\_tile.tile<4x8x!cuda\_tile.ptr<f32\>>

Copy to clipboard

#### SameElements[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#sameelements "Link to this heading")

#same\_elements< $values \>

Copy to clipboard

The `same_elements` attribute must be used as a predicate for `cuda_tile.assume`. The predicated value must be a tensor of integers or pointers.

`same_elements` is specified for each dimension. A value of C for a dimension of size N indicates that, after dividing the respective dimension into N/C groups of size C, each group consists of the same elements. As N/C may not divide evenly, the last group may have fewer than C elements.

If the “same elements” property does not hold along a dimension, the respective value should be set to 1. `#cuda_tile.same_elements<[1, 1, ..., 1]>` is a correct predicate for any tensor of integers or pointers, where the number of ones matches the rank of the tensor. (Size-1 groups always have the same elements.)

// Integer tensor with same elements.
%0 \= cuda\_tile.constant <i16: \[\[0, 0, 0, 0, 10, 10, 10, 10\],
                               \[0, 0, 0, 0, 10, 10, 10, 10\],
                               \[5, 5, 5, 5, 93, 93, 93, 93\],
                               \[5, 5, 5, 5, 93, 93, 93, 93\]\]\>
    : tile<4x8xi16\>
%1 \= cuda\_tile.assume #cuda\_tile.same\_elements<\[2, 4\]\>, %0
    : !cuda\_tile.tile<4x8xi16\>

// Pointer tensor with same elements.
%2 \= cuda\_tile.constant <i64: \[\[ 0,  0,  0,  0,  8,  8,  8,  8\],
                               \[ 0,  0,  0,  0,  8,  8,  8,  8\],
                               \[64, 64, 64, 64, 32, 32, 32, 32\],
                               \[64, 64, 64, 64, 32, 32, 32, 32\]\]\>
    : tile<4x8xi64\>
%3 \= cuda\_tile.bitcast %2
    : !cuda\_tile.tile<4x8xi64\>
      \-> !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>
%4 \= cuda\_tile.assume #cuda\_tile.same\_elements<\[2, 4\]\>, %3
    : !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>

Copy to clipboard

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id413 "Link to this heading")

-   `value` and `result` must have the same shape and element type ([Any](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-any)).
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id414 "Link to this heading")

// Assume that all integers are divisible by 32.
%int\_tile \= constant <i16: \[32, 64, 0, 0, 32, \-32, 1024, 0\]\> : tile<8xi16\>
%div\_by\_1 \= assume div\_by<32\>, %int\_tile : tile<8xi16\>

// Assume that every 4th element (starting with element 0) along
// dimension 0 is divisible by 32 that and all integers are
// montonically increasing by 1 within each group of 4.
%int\_tile\_2 \= constant <i16: \[96, 97, 98, 99, 64, 65, 66, 67\]\> : tile<8xi16\>
%div\_by\_2 \= assume div\_by<32, every 4 along 0\>, %int\_tile\_2 : tile<8xi16\>

// Assume that every rectangular chunk of size \[1, 4, 2\] has the same
// values.
%same\_elem \= assume same\_elements<\[1, 4, 2\]\>, %ptr\_3d : tile<1x8x8xptr<f32\>>

// Assume that every value is greater or equal to 5.
%int\_tile\_3 \= constant <i16: \[5, 9, 10, 11, 6, 5, 5, 7\]\> : tile<8xi16\>
%bounded \= assume bounded<5, ?\>, %int\_tile\_3 : tile<8xi16\>

Copy to clipboard

See [cuda\_tile.assume\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-assume-0) for the full example listing.

### 8.12.2. cuda\_tile.print\_tko[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#cuda-tile-print-tko "Link to this heading")

_Print a formatted string (token-ordered)_

cuda\_tile.print\_tko %str %args %token

Copy to clipboard

#### Parameters[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id415 "Link to this heading")

-   **str** ([String](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-string)) - The format string. 13.1
-   **args** ([Variadic](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-variadic)<[tile](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/types.html#type-tile)\>) - The arguments to format and print. 13.1
-   **token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The optional token for operation ordering. 13.2

#### Results[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id416 "Link to this heading")

-   **result\_token** ([token](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#type-token)) - The result token for synchronization. 13.2

#### Description[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id417 "Link to this heading")

The `print_tko` operation prints a C-printf-style format string, interleaved with the given operands. The number of format expressions (starting with the `%` character) must match the number of operands. If a format expression is not applicable to its respective operand, then the output is undefined.

Token-ordered print operations are not constrained by program order. The compiler may reorder them (i.e., move them earlier or later in the program) unless further constrained by tokens.

This operation is meant for debugging. Its implementation is not optimized for performance, so it should not be used in production mode. Prints are not guaranteed to be atomic. I.e., the output of prints that execute simultaneously may be interleaved.

Note

This op was renamed from `print` to `print_tko` in 13.2. The op code did not change.

#### Constraints[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id418 "Link to this heading")

-   Operation must encode variadic operand segment sizes in attributes.
-   Operation must infer result types from operands and attributes.

#### Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/operations.html#id419 "Link to this heading")

print\_tko "Hello world: %f\\n", %arg : tile<4xf32\> \-> token
print\_tko "%+08.3f", %arg : tile<4xf32\> \-> token

Copy to clipboard

See [cuda\_tile.print\_tko\_0](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#example-cuda-tile-print-tko-0) for the full example listing.
