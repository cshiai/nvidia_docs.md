# 12\. Release Notes[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#release-notes "Link to this heading")

## 12.1. Known Issues[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#known-issues "Link to this heading")

-   The programming model is missing a section on a cross-tile block kernel such as split-k.
-   The bytecode section does not provide exact encoding of each operation, expect this to be introduced in a future release.
-   The semi-formal memory model section is written but does not provide detailed examples of how to to utilize it.
-   Atomics are currently limited in **Tile IR** and will be expanded in a future release.

## 12.2. Changelog[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#changelog "Link to this heading")

### 12.2.1. Spec 13.2 (2026-03-11)[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#spec-13-2-2026-03-11 "Link to this heading")

#### Supported Architectures[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#supported-architectures "Link to this heading")

-   Added support for Ampere (sm\_80, sm\_86, sm\_87, sm\_88) and Ada (sm\_89) architectures.

#### New Operations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#new-operations "Link to this heading")

-   Added `cuda_tile.atan2` operation for element-wise two-argument arctangent.

#### Updated Operations[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/release_notes.html#updated-operations "Link to this heading")

-   Added `overflow` attribute to `cuda_tile.negi` to control integer overflow behavior.
-   Added `rounding_mode` attribute to `cuda_tile.tanh` to control floating-point rounding behavior.
-   Added `token` result to `cuda_tile.print_tko` for memory ordering support.
-   Added `unsignedCmp` flag to `cuda_tile.for` to support unsigned integer comparison for loop termination.
-   Renamed `cuda_tile.print` to `cuda_tile.print_tko` in the textual format. Bytecode encoding is unchanged and remains backward compatible.
