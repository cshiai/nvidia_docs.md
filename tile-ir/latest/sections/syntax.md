# 3\. Syntax[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/syntax.html#syntax "Link to this heading")

**Tile IR** is intended to be constructed using the **Tile IR** MLIR dialect and stored as bytecode.

To enable humans to comprehend **Tile IR** bytecode programs, we provide an **unstable** textual representation based on the MLIR dialect. This textual representation has no stability guarantees and it is not intended to be used for writing **Tile IR** programs.

## 3.1. Module[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/syntax.html#module "Link to this heading")

A **Tile IR** program consists of a **Tile IR** module which contains a series of items.

symbol\_name := \`@\` identifier

cuda\_tile.module @symbol\_name {
    <items>\*
}

Copy to clipboard

## 3.2. Items[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/syntax.html#items "Link to this heading")

An item is a kernel definition or a global variable definition.

<items\> ::= <kernel\_definition\> | <global\_variable\_definition\>

Copy to clipboard

## 3.3. Globals[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/syntax.html#globals "Link to this heading")

A global variable definition is a variable that is defined outside of a kernel.

global\_variable\_definition ::= \`global\` <symbol\_name> \`:\` <type> \`=\` <value>

Copy to clipboard

## 3.4. Kernels[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/syntax.html#kernels "Link to this heading")

A kernel definition is a function that is defined inside a **Tile IR** module.

ssa\_name := \`%\` identifier

function\_signature ::= <function\_parameter>\*

function\_parameter ::= <ssa\_name> \`:\` <type>

<kernel\_definition> ::= \`func\` @kernel\_name \`(\` <function\_signature> \`)\` \`->\` <function\_type> {
    <kernel\_body>
}

Copy to clipboard

A kernel definition’s body is a sequence of operations.

kernel\_body ::= <operation>\*

operation ::= (ssa\_name \`,\`?)\* \`=\` <operation\_name> <ssa\_name>\* attribute=attribute\_value : type ...

Copy to clipboard

## 3.5. Types[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/syntax.html#types "Link to this heading")

A type in **Tile IR** is a fixed pre-defined set of types.

element\_type ::= \`f32\` | \`f64\` | \`i8\` | \`i16\` | \`i32\` | \`i64\` | \`b8\` | \`b16\` | \`b32\` | \`b64\`

type ::= \`tile\` \`<\` shape \`x\` element\_type \`>\`

shape ::= \`\[\` integer\_literal (\`x\` integer\_literal
