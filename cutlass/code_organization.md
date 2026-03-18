# Code Organization[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#code-organization "Link to this heading")

This document describes the layout of the CUTLASS repository. The main components are:

-   **CUTLASS Template Library** - CUDA Templates for Linear Algebra Subroutines and Solvers (header only)
-   **CuTe Template Library** - CUTLASS’s core vocabulary layout type and associated algebra (header only)
-   **CUTLASS Utilities** - Additional templates
-   **CUTLASS Instance Library** - instantiations of CUTLASS templates covering the design space
-   **CUTLASS Profiler** - CUTLASS Library, Profiler, and Utilities
-   **Examples** - SDK examples of CUTLASS Template Library and components
-   **Media** - supporting documentation and media content
-   **Tests** - test components for CUTLASS Template Library and tools

## CUTLASS Template Library[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#cutlass-template-library "Link to this heading")

CUDA Templates for Linear Algebra Subroutines and Solvers is a library of CUDA C++ template classes for performing efficient matrix computations on NVIDIA GPUs.

Like NVIDIA CUB, the components of CUTLASS are organized hierarchically based on the scope of cooperative elements. For example, warp-level GEMM components perform a matrix multiply collectively by the set of threads within a warp. The following figure illustrates each layer.

Components are designed to be usable by client applications accessing functionailty at each scope.

CUTLASS Templates are implemented by header files in the following directory structure:

include/                     # Top-level include directory. Client applications should target this path.
  cutlass/                   # CUDA Templates for Linear Algebra Subroutines and Solvers - headers only

    arch/                    # direct exposure of architecture features (including instruction-level GEMMs)
      \*
    gemm/                    # code specialized for general matrix product computations
      thread/                #   thread-level operators
      warp/                  #   warp-level operators
      collective/            #   3.x API operators for all threads a tiled mma/copy are built over
      threadblock/           #   CTA-level operators
      kernel/                #   CUDA kernel entry points
      device/                #   launches kernel(s) over a full device
      \*                      # scope-agnostic components and basic vocabulary type definitions for GEMM

    layout/                  # layout definitions for matrices, tensors, and other mathematical objects in memory
      \*

    reduction/               # bandwidth-limited reduction kernels that do not fit the "gemm" models
      thread/                #   thread-level operators
      warp/                  #   warp-level operators
      threadblock/           #   CTA-level operators
      kernel/                #   CUDA kernel entry points
      device/                #   launches kernel(s) over a full device
      \*                      # scope-agnostic components and basic vocabulary type definitions

    transform/               # code specialized for layout, type, and domain transformations
      thread/                #   thread-level operators
      warp/                  #   warp-level operators
      threadblock/           #   CTA-level operators
      kernel/                #   CUDA kernel entry points
      device/                #   launches kernel(s) over a full device
      \*                      # scope-agnostic components and basic vocabulary type definitions

    util/                    # miscellaneous CUTLASS components
      \*
    \*                        # core vocabulary types and fundamental arithmetic operators

  cute /                     # CuTe Layout, layout algebra, MMA/Copy atoms, tiled MMA/Copy
    algorithm/               # Definitions of core operations such as copy, gemm, and operations on cute::tuples
    arch/                    # Bare bones PTX wrapper structs for copy and math instructions
    atom/                    # Meta-information either link to or built from arch/ operators
      mma\_atom.hpp           # cute::Mma\_Atom and cute::TiledMma
      copy\_atom.hpp          # cute::Copy\_Atom and cute::TiledCopy
      \*sm\*.hpp               # Arch specific meta-information for copy and math operations
    container/               # Core container types used across CuTe, namely, cute::tuple
    numeric/                 # CuTe's internal numerics implementation
    \*                        # Core library types such as Shape, Stride, Layout, Tensor, and associated operations

Copy to clipboard

See [Programming Guidelines](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html) for further details about conventions and design patterns used throughout CUTLASS.

## CuTe[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#cute "Link to this heading")

CuTe is a collection of C++ CUDA template abstractions for defining and operating on hierarchically multidimensional layouts of threads and data. CuTe provides `Layout` and `Tensor` objects that compactly packages the type, shape, memory space, and layout of data, while performing the complicated indexing for the user. This lets programmers focus on the logical descriptions of their algorithms while CuTe does the mechanical bookkeeping for them. With these tools, we can quickly design, implement, and modify all dense linear algebra operations. More documentation for CuTe can be found in [`cute/`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/index.html).

## Tools[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#tools "Link to this heading")

The `tools/` directory contains clients of the CUTLASS Template library and includes the following.

## CUTLASS Instance Library[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#cutlass-instance-library "Link to this heading")

The CUTLASS Instance Library contains instantiations of the above CUTLASS templates covering supported configurations, data types, block structure, and tile sizes. These instantiations are procedurally generated using a set of scripts to span the design space.

tools/
  library/                   # static/dynamic library containing all kernel instantiations of interest
                             # (with some build-level filter switches to compile specific subsets)

    include/
      cutlass/
        library/             # header files for CUTLASS Deliverables Library (in cutlass::library:: namespace)

          handle.h           # implements a host-side API for launching kernels, similar to cuBLAS
          library.h          # defines enums and structs to describe the tiled structure of operator instances          
          manifest.h         # collection of all instances

    src/

python/
    cutlass\_library/       # scripts to procedurally generate CUTLASS template instances

      gemm\_operations.py
      library.py
      generator.py            # entry point of procedural generation scripts - invoked by cmake
      manifest.py

Copy to clipboard

When CMake is executed, the CUTLASS Instance Library generator scripts are executed to construct a set of instantiations in `build/tools/library/generated/`.

### CUTLASS Profiler[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#cutlass-profiler "Link to this heading")

The CUTLASS Profiler is designed to load the CUTLASS Instance Library and execute all operations contained therein. This command-line driven application constructs an execution environment for evaluating functionality and performance. It is implemented in

tools/
  profiler/

Copy to clipboard

and may be built as follows.

$ make cutlass\_profiler \-j

Copy to clipboard

[Further details about the CUTLASS Profiler are described here.](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/profiler.html)

### CUTLASS Utilities[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#cutlass-utilities "Link to this heading")

`tools/util/` defines a companion library of headers and sources that support the CUTLASS test programs, examples, and other client applications. Its structure is as follows:

tools/
  util/
    include/
      cutlass/
        util/                   # CUTLASS Utility companion library

          reference/            #  functional reference implementation of CUTLASS operators
                                #    (minimal consideration for performance)
            
            detail/
              \*

            device/             #  device-side reference implementations of CUTLASS operators
              thread/
              kernel/
                \*
            host/               #  host-side reference implementations of CUTLASS operators
              \*
          \*

Copy to clipboard

[More details about CUTLASS Utilities may be found here.](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/utilities.html)

## Examples[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#examples "Link to this heading")

To demonstrate CUTLASS components, several SDK examples are implemented in `examples/`.

CUTLASS SDK examples apply CUTLASS templates to implement basic computations.

examples/
  00\_basic\_gemm/             # launches a basic GEMM with single precision inputs and outputs

  01\_cutlass\_utilities/      # demonstrates CUTLASS Utilities for allocating and initializing tensors
  
  02\_dump\_reg\_smem/          # debugging utilities for printing register and shared memory contents
  
  03\_visualize\_layout/       # utility for visualizing all layout functions in CUTLASS

  04\_tile\_iterator/          # example demonstrating an iterator over tiles in memory

  05\_batched\_gemm/           # example demonstrating CUTLASS's batched strided GEMM operation

  06\_splitK\_gemm/            # exmaple demonstrating CUTLASS's Split-K parallel reduction kernel

  07\_volta\_tensorop\_gemm/    # example demonstrating mixed precision GEMM using Volta Tensor Cores

  08\_turing\_tensorop\_gemm/   # example demonstrating integer GEMM using Turing Tensor Cores

  10\_planar\_complex/         # example demonstrating planar complex GEMM kernels

  11\_planar\_complex\_array/   # example demonstrating planar complex kernels with batch-specific problem sizes

  12\_gemm\_bias\_relu/         # example demonstrating GEMM fused with bias and relu activation function

  13\_fused\_two\_gemms/        # example demonstrating two GEMMs fused into one kernel

Copy to clipboard

## Media[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#media "Link to this heading")

This directory contains documentation, images, and performance result data which accompanies the CUTLASS library and components.

## Tests[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/code_organization.html#tests "Link to this heading")

Test programs for CUTLASS. Tests are organized hierarchically, mirroring the organization of source files.

test/                        # unit tests for CUTLASS Template Library
  unit/
    arch/
    core/
    gemm/
      device/
      kernel/
      thread/
      threadblock/
      warp/
    reduction/
      kernel/
      thread/
    transform/
      threadblock/
      \*

Copy to clipboard

Tests can be built and run at the top level scope by invoking `make test_unit` or by building and explicitly executing each individual target, e.g. `cutlass_test_unit_gemm_device`.

Tests are configured to specify appropriate GTest filter strings to avoid running except on architectures where they are expected to pass. Thus, no tests should fail. The actual number of tests run may vary over time as more are added.