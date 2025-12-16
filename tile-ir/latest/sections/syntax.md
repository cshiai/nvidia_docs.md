# 3. Syntax


Tile IR is intended to be constructed using the Tile IR MLIR dialect and stored as bytecode.


To enable humans to comprehend Tile IR bytecode programs, we provide an unstable textual representation based on the MLIR dialect. This textual representation has no stability guarantees and it is not intended to be used for writing Tile IR programs.


## 3.1. Module


A Tile IR program consists of a Tile IR module which contains a series of items.


```
symbol_name := `@` identifier

cuda_tile.module @symbol_name {
    <items>*
}
```


## 3.2. Items


An item is a kernel definition or a global variable definition.


```
<items> ::= <kernel_definition> | <global_variable_definition>
```


## 3.3. Globals


A global variable definition is a variable that is defined outside of a kernel.


```
global_variable_definition ::= `global` <symbol_name> `:` <type> `=` <value>
```


## 3.4. Kernels


A kernel definition is a function that is defined inside a Tile IR module.


```
ssa_name := `%` identifier

function_signature ::= <function_parameter>*

function_parameter ::= <ssa_name> `:` <type>

<kernel_definition> ::= `func` @kernel_name `(` <function_signature> `)` `->` <function_type> {
    <kernel_body>
}
```


A kernel definition’s body is a sequence of operations.


```
kernel_body ::= <operation>*

operation ::= (ssa_name `,`?)* `=` <operation_name> <ssa_name>* attribute=attribute_value : type ...
```


## 3.5. Types


A type in Tile IR is a fixed pre-defined set of types.


```
element_type ::= `f32` | `f64` | `i8` | `i16` | `i32` | `i64` | `b8` | `b16` | `b32` | `b64`

type ::= `tile` `<` shape `x` element_type `>`

shape ::= `[` integer_literal (`x` integer_literal)* `]`
```