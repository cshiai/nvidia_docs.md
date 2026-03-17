# 9\. Debug Info[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#debug-info "Link to this heading")

Debug info is essential for understanding and diagnosing the behavior of a **Tile IR** program. Debug info is metadata that maps generated code back to the original source code, creating a more informative and intuitive debugging experience for the **Tile IR** user and allowing the user to quickly identify and fix issues in a **Tile IR** program. This section explains how to include and use debug info in a **Tile IR** program when using the MLIR dialect. For a description of how to produce this information in the bytecode directly, see the [bytecode section](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/bytecode.html#section-bytecode).

**Tile IR** supports control flow based debugging of unoptimized code with features such as breakpoints, stepping through code and inspecting stack frames. **Tile IR** debug info exposes scope metadata describing the files, functions and blocks that comprise a **Tile IR** program along with information on how that program was compiled. This scope metadata is included in the **Tile IR** program by fusing it to location information. Details and examples below. **Tile IR** does not support value inspection of user variables, only control flow based debugging as described above is supported at this time.

## 9.1. Location Information[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#location-information "Link to this heading")

**Tile IR** requires that scope metadata is attached to all operations within a **Tile IR** module to generate debug info of any kind. Scope metadata is required in addition to simple file, line, column location information. Providing simple file, line, column location information alone without scope metadata results in a very poor user experience. Scoped metadata is required to generate DWARF information and DWARF information is required by all developer tools including debuggers and profilers.

Example of a simple file, line, column location: `loc("/tmp/foo.py":1:4)`

Example of a location fused with scope metadata: `#cuda_tile.di_loc<loc("/tmp/foo.py":1:4) in #subprogram`

### 9.1.1. Location Types[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#location-types "Link to this heading")

Two location types are supported by **Tile IR**:

1.  A **Tile IR** location represented by a `#cuda_tile.di_loc` attribute which combines file, line, column information with scope metadata as shown in the example above. This is the preferred method for generating location information fused with scope metadata.
2.  A `CallSiteLoc` where both the callee and caller are supported location types. This respresents a function call e.g. in the case where the **Tile IR** producer supports inlining.

All **Tile IR** global variables will have `UnknownLoc` given that `#cuda_tile.di_loc` supports local scope only and there is no support for `FileLineColLoc`.

| Location Type | Support |
| --- | --- |
| CudaTile DILocAttr | Supported |
| CallSiteLoc | Supported if BOTH callee and caller are supported. |
| FusedLoc | Unsupported |
| NameLoc | Unsupported |
| OpaqueLoc | Unsupported |
| FileLineColLoc | Supported only as part of DILocAttr, else converted to UnknownLoc. |
| UnknownLoc | Supported |

### 9.1.2. Generating Scope Metadata[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#generating-scope-metadata "Link to this heading")

Below are the options, trade-offs and mechanisms for generating scope metadata in **Tile IR** programs.

### 9.1.3. Options[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#options "Link to this heading")

**Tile IR** producers have two options for generating location information fused with scope metadata:

1.  The **Tile IR** producer can generate location information fused with scope metadata directly using `#cuda_tile.di_loc` as shown in the example above.
2.  The **Tile IR** producer can generate a `loc` with file, line, column location information and then use a **Tile IR** pass (via `--synthesize-debug-info-scopes`) to synthesize scope metadata from that file, line, column location information.

Note

File, line, column location information must be converted to a **Tile IR** location prior to bytecode generation as all `FileLineColLoc` attributes are encoded as `UnknownLoc` attributes in the bytecode.

### 9.1.4. Trade-offs[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#trade-offs "Link to this heading")

When deciding between the two options above, the **Tile IR** producer should consider the following trade-offs:

1.  Providing location information with scope metadata may be harder for the **Tile IR** producer to implement, however, the **Tile IR** producer retains full control to describe its source code to the compiler which may result in a smoother debugging experience for the end user.
2.  Providing simple file line, location information is very simple for the **Tile IR** producer to implement but cedes control to the pass which may not be able to accurately synthesize debug info for all cases possibly resulting in a degraded debugging experience for the end user. E.g. the pass may be able to synthesize function name, guess at linkage name, but not do a very good job of getting the line or column number of the function.

### 9.1.5. Mechanism[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#mechanism "Link to this heading")

To synthesize scope metadata, the SynthesizeDebugInfoScopes pass can be added to any **Tile IR** pass pipeline or invoked via Python as follows:

pm \= passmanager.PassManager(context\=module.context)
full\_pass\_string \= f"cuda\_tile.module({"synthesize-debug-info-scopes"})"
pm \= pm.parse(full\_pass\_string, context\=module.context)
pm.run(module.operation.regions\[0\].blocks\[0\].operations\[0\])

Copy to clipboard

## 9.2. Scope Metadata[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#scope-metadata "Link to this heading")

**Tile IR** debug info is comprised of the following scope metadata expressed as attributes and fields:

### 9.2.1. Compile Unit[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#compile-unit "Link to this heading")

A compile unit represents the root scope of all objects declared within a specific compilation unit. It specifies the source file associated with the compilation unit and encompasses all the other debug information elements such as files, lexical blocks, and subprograms. This scope is fundamental for organizing and correlating debug information with the original source code, facilitating efficient debugging.

Fields:

-   **File**: The source file associated with the compilation unit.

The following fields are set by the **Tile IR** compiler and listed for reference:

-   **Is Optimized?**: Set to `false` if compiler option `--opt-level` is `0` else `true`.
-   **Emission Kind**: Set based on compiler options: `--line-info` to generate line tables only or `--device-debug` alias `-g` for generating full debug info.

### 9.2.2. File[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#file "Link to this heading")

A file represents a source file used in the compilation process. It specifies the file name and directory of the source file. This information is used to map the generated code back to the original source, allowing developers to trace and debug code effectively.

Fields:

-   **Name**: The name of the file.
-   **Directory**: The directory containing the file.

### 9.2.3. Lexical Block[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#lexical-block "Link to this heading")

A lexical block represents a nested scope within a subprogram, specifying the scope, file, line number, and optional column number of the block. Lexical blocks are used to represent various nested scopes in the source code, such as conditional statements, loops, and other code blocks. This detailed scope information helps in understanding the program’s structure and control flow during debugging.

Fields:

-   **Scope**: The scope in which the lexical block is defined.
-   **File**: The source file containing the lexical block.
-   **Line**: The line number where the lexical block starts.
-   **Column**: The column number where the lexical block starts.

### 9.2.4. Subprogram[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#subprogram "Link to this heading")

A subprogram represents a function within the source language. It specifies the scope, file, line number, name, and linkage name of the subprogram. Optionally, it can include the line number within the scope. Subprogram information is used for function level debugging, allowing developers to set breakpoints, step through code, and inspect stack frames within specific functions.

Fields:

-   **File**: The source file containing the subprogram.
-   **Line**: The line number where the subprogram starts.
-   **Name**: The name of the subprogram.
-   **Linkage Name**: The linkage name of the subprogram.
-   **Compile Unit**: The compilation unit containing the subprogram.
-   **Scope Line**: The line number where the scope of the subprogram starts. \[Optional\]

The following fields are set by the **Tile IR** compiler and listed for reference:

-   **Subroutine Type**: Set to `() -> ()` meaning that all functions appear to have no arguments and no return value.

## 9.3. Example Usage[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/debug_info.html#example-usage "Link to this heading")

Below is an example showing how to use **Tile IR** debug info:

#file\= #cuda\_tile.di\_file<"foo.py" in "/tmp/"\>

#compile\_unit\= #cuda\_tile.di\_compile\_unit<
  file \= #file
\>

#subprogram\= #cuda\_tile.di\_subprogram<
  file \= #file,
  line \= 1,
  name \= "test\_kernel",
  linkageName \= "kernel",
  compileUnit \= #compile\_unit,
  scopeLine \= 1
\>

#block\= #cuda\_tile.di\_lexical\_block<
  scope \= #subprogram,
  file \= #file,
  line \= 1,
  column \= 4
\>

#loc\_fn\= #cuda\_tile.di\_loc<loc("/tmp/foo.py":1:4) in #subprogram\>
#loc\_return\= #cuda\_tile.di\_loc<loc("/tmp/foo.py":5:4) in #block\>

cuda\_tile.module @kernels attributes { } {
  entry @kernel() {
    return loc(#loc\_return)
  } loc(#loc\_fn)
}
