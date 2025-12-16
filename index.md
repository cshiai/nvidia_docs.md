# CUDA Toolkit Documentation 13.1


Develop, Optimize and Deploy GPU-Accelerated Apps


The NVIDIA® CUDA® Toolkit provides a development environment for creating high performance GPU-accelerated applications. With the CUDA Toolkit, you can develop, optimize, and deploy your applications on GPU-accelerated embedded systems, desktop workstations, enterprise data centers, cloud-based platforms and HPC supercomputers. The toolkit includes GPU-accelerated libraries, debugging and optimization tools, a C/C++ compiler, and a runtime library to deploy your application.


Using built-in capabilities for distributing computations across multi-GPU configurations, scientists and researchers can develop applications that scale from single GPU workstations to cloud installations with thousands of GPUs.


---


Release Notes
The Release Notes for the CUDA Toolkit.


---


## CUDA Installation Guides


Quick Start Guide
This guide provides the minimal first-steps instructions for installation and verifying CUDA on a standard system.

Installation Guide Linux
This guide discusses how to install and check for correct operation of the CUDA Development Tools on GNU/Linux systems.

Installation Guide Windows
This guide discusses how to install and check for correct operation of the CUDA Development Tools on Microsoft Windows systems.


---


## CUDA Programming Guides


CUDA Programming Guide
This guide provides a detailed discussion of the CUDA programming model and programming interface.
      It also describes the hardware implementation and provides guidance on achieving maximum performance.

Best Practices Guide
This guide presents established parallelization and optimization techniques and explains coding idioms
      that simplify programming for CUDA-capable GPUs. It provides guidelines for obtaining the best performance
      from NVIDIA GPUs using the CUDA Toolkit.

cuTile Python
This guide provides documentation of cuTile Python, the DSL for tile programming in Python.

PTX ISA
This guide provides detailed instructions on the use of PTX, a low-level parallel thread execution virtual
      machine and instruction set architecture (ISA). PTX exposes the GPU as a data-parallel computing device.

CUDA Tile IR
This guide provides documentation of CUDA Tile IR, a portable, low-level tile virtual machine and instruction set that models the GPU as a tile-based processor.


---


## CUDA Architecture Guides


Ada Compatibility Guide
This application note is intended to help developers ensure that their NVIDIA CUDA applications will run properly on the Ada GPUs. This document provides guidance to ensure that your software applications are compatible with Ada architecture.

Ada Tuning Guide
The NVIDIA® Ada GPU architecture is NVIDIA’s 10th-generation architecture for CUDA® compute applications. The NVIDIA Ada GPU architecture retains and extends the same CUDA programming model provided by previous NVIDIA GPU architectures such as NVIDIA Ampere and Turing architectures, and applications that follow the best practices for those architectures should typically see speedups on the NVIDIA Ada architecture without any code changes. This guide summarizes the ways that an application can be fine-tuned to gain additional speedups by leveraging the NVIDIA Ada GPU architecture’s features.

Blackwell Compatibility Guide
This application note is intended to help developers ensure that their NVIDIA CUDA applications will run properly on the Blackwell GPUs. This document provides guidance to ensure that your software applications are compatible with Blackwell architecture.

Blackwell Tuning Guide
The NVIDIA® Blackwell GPU architecture is NVIDIA’s latest architecture for CUDA® compute applications. The NVIDIA Blackwell GPU architecture retains and extends the same CUDA programming model provided by previous NVIDIA GPU architectures such as NVIDIA Ampere and Turing srchitectures, and applications that follow the best practices for those architectures should typically see speedups on the NVIDIA Blackwell architecture without any code changes. This guide summarizes the ways that an application can be fine-tuned to gain additional speedups by leveraging the NVIDIA Blackwell GPU architecture’s features.

Hopper Compatibility Guide
This application note is intended to help developers ensure that their NVIDIA CUDA applications will run properly on the Hopper GPUs. This document provides guidance to ensure that your software applications are compatible with Hopper architecture.

Hopper Tuning Guide
Hopper GPU Architecture is NVIDIA’s 9th-generation architecture for CUDA compute applications. This guide summarizes the ways that applications can be fine-tuned to gain additional speedups by leveraging Hopper GPU Architecture’s features.

Inline PTX Assembly
This document shows how to inline PTX (parallel thread execution) assembly language statements into CUDA code. It describes available assembler statement parameters and constraints, and the document also provides a list of some pitfalls that you may encounter.

NVIDIA Ampere GPU Architecture Compatibility Guide
This application note is intended to help developers ensure that their NVIDIA CUDA applications will run properly on GPUs based on the NVIDIA Ampere GPU Architecture. This document provides guidance to ensure that your software applications are compatible with NVIDIA Ampere GPU architecture.

NVIDIA Ampere GPU Architecture Tuning Guide
NVIDIA Ampere GPU Architecture is NVIDIA’s 8th-generation architecture for CUDA compute applications. This guide summarizes the ways that applications can be fine-tuned to gain additional speedups by leveraging NVIDIA Ampere GPU Architecture’s features.

PTX Interoperability
This document shows how to write PTX that is ABI-compliant and interoperable with other CUDA code.

Turing Compatibility Guide
This application note is intended to help developers ensure that their NVIDIA CUDA applications will run properly on GPUs based on the NVIDIA Turing Architecture. This document provides guidance to ensure that your software applications are compatible with Turing.

Turing Tuning Guide
Turing is NVIDIA’s 7th-generation architecture for CUDA compute applications. This guide summarizes the ways that applications can be fine-tuned to gain additional speedups by leveraging Turing architectural features.


---


## CUDA API References


CUDA Runtime API
Fields in structures might appear in order that is different from the order of declaration.

CUDA Driver API
Fields in structures might appear in order that is different from the order of declaration.

CUDA Math API
The CUDA math API.

cuBLAS
The cuBLAS library is an implementation of BLAS (Basic Linear Algebra Subprograms) on top of the NVIDIA CUDA runtime. It allows the user to access the computational resources of NVIDIA Graphical Processing Unit (GPU), but does not auto-parallelize across multiple GPUs.

cuDLA API
The cuDLA API.

NVBLAS
The NVBLAS library is a multi-GPUs accelerated drop-in BLAS (Basic Linear Algebra Subprograms) built on top of the NVIDIA cuBLAS Library.

nvJPEG
The nvJPEG Library provides high-performance GPU accelerated JPEG decoding functionality for image formats commonly used in deep learning and hyperscale multimedia applications.

cuFFT
The cuFFT library user guide.

CUB
The user guide for CUB.

CUDA C++ Standard Library
The API reference for libcu++, the CUDA C++ standard library.

cuFile API Reference Guide
The NVIDIA® GPUDirect® Storage cuFile API Reference Guide provides information about the preliminary version of the cuFile API reference guide that is used in applications and frameworks to leverage GDS technology and describes the intent, context, and operation of those APIs, which are part of the GDS technology.

cuRAND
The cuRAND library user guide.

cuSPARSE
The cuSPARSE library user guide.

NPP
NVIDIA NPP is a library of functions for performing CUDA accelerated processing. The initial set of functionality in the library focuses on imaging and video processing and is widely applicable for developers in these areas. NPP will evolve over time to encompass more of the compute heavy tasks in a variety of problem domains. The NPP library is written to maximize flexibility, while maintaining high performance.

nvJitLink
The user guide for the nvJitLink library.

nvFatbin
The user guide for the nvFatbin library.

NVRTC (Runtime Compilation)
NVRTC is a runtime compilation library for CUDA C++. It accepts CUDA C++ source code in character string form and creates handles that can be used to obtain the PTX. The PTX string generated by NVRTC can be loaded by cuModuleLoadData and cuModuleLoadDataEx, and linked with other modules by cuLinkAddData of the CUDA Driver API. This facility can often provide optimizations and performance not possible in a purely offline static compilation.

Thrust
The C++ parallel algorithms library.

cuSOLVER
The cuSOLVER library user guide.


---


## PTX Compiler API References


PTX Compiler APIs
This guide shows how to compile a PTX program into GPU assembly code using APIs provided by the static PTX Compiler library.


---


CUDA Demo Suite
This document describes the demo applications shipped with the CUDA Demo Suite.

CUDA on WSL
This guide is intended to help users get started with using NVIDIA CUDA on Windows Subsystem for Linux (WSL 2). The guide covers installation and running CUDA applications and containers in this environment.

Multi-Instance GPU (MIG)
This edition of the user guide describes the Multi-Instance GPU feature of the NVIDIA® A100 GPU.

CUDA Compatibility
This document describes CUDA Compatibility, including CUDA Enhanced Compatibility and CUDA Forward Compatible Upgrade.

CUPTI
The CUPTI-API. The CUDA Profiling Tools Interface (CUPTI) enables the creation of profiling and tracing tools that target CUDA applications.

Debugger API
The CUDA debugger API.

GPUDirect RDMA
A technology introduced in Kepler-class GPUs and CUDA 5.0, enabling a direct path for communication between the GPU and a third-party peer device on the PCI Express bus when the devices share the same upstream root complex using standard features of PCI Express. This document introduces the technology and describes the steps necessary to enable a GPUDirect RDMA connection to NVIDIA GPUs within the Linux device driver model.

GPUDirect Storage
The documentation for GPUDirect Storage.

vGPU
vGPUs that support CUDA.


---


## Tools


NVCC
This is a reference document for nvcc, the CUDA compiler driver. nvcc accepts a range of conventional compiler options, such as for defining macros and include/library paths, and for steering the compilation process.

CUDA-GDB
The NVIDIA tool for debugging CUDA applications running on Linux and QNX, providing developers with a mechanism for debugging CUDA applications running on actual hardware. CUDA-GDB is an extension to the x86-64 port of GDB, the GNU Project debugger.

Compute Sanitizer
The user guide for Compute Sanitizer.

Nsight Eclipse Plugins Installation Guide
Nsight Eclipse Plugins Installation Guide

Nsight Eclipse Plugins Edition
Nsight Eclipse Plugins Edition getting started guide

Nsight Systems
The documentation for Nsight Systems.

Nsight Compute
The NVIDIA Nsight Compute is the next-generation interactive kernel profiler for CUDA applications. It provides detailed performance metrics and API debugging via a user interface and command line tool.

Nsight Visual Studio Edition
The documentation for Nsight Visual Studio Edition.

CUDA Binary Utilities
The application notes for cuobjdump, nvdisasm, and nvprune.

CUDA Compile Time Advisor
The application notes for Compile Time Advisor (ctadvisor).


---


## White Papers


Floating Point and IEEE 754
A number of issues related to floating point accuracy and compliance are a frequent source of confusion on both CPUs and GPUs. The purpose of this white paper is to discuss the most common issues related to NVIDIA GPUs and to supplement the documentation in the CUDA Programming Guide.

Incomplete-LU and Cholesky Preconditioned Iterative Methods
In this white paper we show how to use the cuSPARSE and cuBLAS libraries to achieve a 2x speedup over CPU in the incomplete-LU and Cholesky preconditioned iterative methods. We focus on the Bi-Conjugate Gradient Stabilized and Conjugate Gradient iterative methods, that can be used to solve large sparse nonsymmetric and symmetric positive definite linear systems, respectively. Also, we comment on the parallel sparse triangular solve, which is an essential building block in these algorithms.


---


## Application Notes


CUDA for Tegra
This application note provides an overview of NVIDIA® Tegra® memory architecture and considerations for porting code from a discrete GPU (dGPU) attached to an x86 system to the Tegra® integrated GPU (iGPU). It also discusses EGL interoperability.


---


## Compiler SDK


libNVVM API
The libNVVM API.

libdevice User’s Guide
The libdevice library is an LLVM bitcode library that implements common functions for GPU kernels.

NVVM IR
NVVM IR is a compiler IR (intermediate representation) based on the LLVM IR. The NVVM IR is designed to represent GPU compute kernels (for example, CUDA kernels). High-level language front-ends, like the CUDA C compiler front-end, can generate NVVM IR.


---


## CUDA Archives


CUDA Features Archive
The list of CUDA features by release.

CUDA C++ Programming Guide (Legacy)
This legacy guide documents the earlier CUDA C/C++ programming model and is retained for reference for existing applications.


---


## Legal Notices


EULA
The CUDA Toolkit End User License Agreement applies to the NVIDIA CUDA Toolkit, the NVIDIA CUDA Samples,
        the NVIDIA Display Driver, NVIDIA Nsight tools (Visual Studio Edition), and the associated documentation
        on CUDA APIs, programming model and development tools. If you do not agree with the terms and conditions
        of the license agreement, then do not download or use the software.