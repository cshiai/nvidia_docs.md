# 10. Stability


Tile IR provides a set of guarantees regarding portability, stability, and compatibility to ensure predictable behavior across different platforms, toolchains, and hardware targets. These guarantees are documented below.


Definitions:


 - Stability: An unchanging property of a program or interface.
 - Portability: A property of a program to be transfered to a different hardware or toolchain version with the same behavior.
 - Compatibility: A property of a program to be executed on a different platform or toolchain with the same behavior.
 - Toolchain: Either the compiler and CTK version used to perform ahead of time compilation or, the driver and CTK version used to perfomr JIT compilation of a Tile IR program.


## 10.1. Platform & Compatibility Guarantees


Bytecode Stability The Tile IR bytecode format ensures that programs can be interpreted and loaded by all conforming drivers (see [Binary Format](bytecode.html#section-bytecode)).


Program Portability A program conforming to Tile IR vX.Y is syntactically portable to any platform that advertises support for vX.Y or newer.


Portability does not imply availability of target-specific features on all targets: if a program uses a feature that the selected hardware target does not support, the compiler will either:


> - diagnose the incompatibility
>  - or apply a lowering that preserves the semantics defined by the specification


CUDA CompatibilityTile IR respects the CUDA platform’s forward and backward minor-version compatibility rules for toolchain and driver integration (see [CUDA Minor Version Compatibility Rules](https://docs.nvidia.com/deploy/cuda-compatibility/minor-version-compatibility.html)).


## 10.2. Feature Availability & Emulation


Target-specific FeaturesTile IR may introduce new target-specific features (e.g., new datatypes, new operations) over time.


 - Availability: A feature introduced in vX.Y becomes usable on a hardware target starting with the first platform release that declares support for it.
 - Fallback: If a program uses a feature unsupported by the selected hardware target, the compiler will either diagnose the incompatibility or apply a lowering (emulation) that preserves semantics as defined by the specification.


Warning


During the 13.x release cycle, we are bringing up existing hardware targets which may introduce new features on old targets. This “cold start” period is an exception; normally, new features will only appear in new targets.


Note


Today the only target-specific features are specific datatypes.


| Data Type | Ampere | Ada | Hopper | Blackwell |
| --- | --- | --- | --- | --- |
| i1, i8, i16, i32, i64 | n/a | n/a | n/a | Supported |
| f16, f32, f64 | n/a | n/a | n/a | Supported |
| bf16 | n/a | n/a | n/a | Supported |
| e3m4 | n/a | n/a | n/a | Supported |
| e5m2 | n/a | n/a | n/a | Supported |


Emulation


To maintain portability, Tile IR may emulate operations on hardware targets that lack native support. For example, 16-bit floating-point operations may be emulated using 32-bit instructions if the target does not support them natively.


## 10.3. Execution & Numerical Guarantees


Execution Determinism For a fixed toolchain, configuration, and hardware target, compilation and execution are deterministic within a single tile-block thread.


 - Version Changes: Using a different toolchain version may produce a different program and thus different results; this is expected behavior, this is expected and not non-determinism.


Numerical StabilityTile IR does not guarantee bit‑identical numerical results across different toolchain versions, configurations, or targets, except where explicitly documented.


 - Scope: Stability guarantees are scoped to specific versions and targets.
 - Updates: Changes are not retroactive; compiling/executing with an earlier toolchain retains the guarantees published for that version.


Floating-point Semantics Floating‑point operations follow applicable IEEE semantics for the order in which they are actually evaluated.


 - Transformations: Compiler transformations (e.g., reordering) can change numeric results across versions.
 - Precision: Operations like MMA may have weaker or no guarantees of bit-identical numerical results unless explicitly documented.