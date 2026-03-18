# Dependent kernel launches[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/dependent_kernel_launch.html#dependent-kernel-launches "Link to this heading")

The Hopper and Blackwell architectures supports a new feature through which two kernels in the same stream can overlap their execution, named [Programmatic Dependent Launch (PDL)](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#programmatic-dependent-launch-and-synchronization). This allows kernels with conflict in global memory to programmatically and safely overlap portions of their execution. Primary kernel can signal it is about to finish execution, and the next kernel is expected to programmatically wait on the previous kernel to finish flushing its memory.

We enable PDL by setting a flag through the extended CUDA launch APIs. All CUTLASS kernels with PDL support will wait on the prior kernel to flush its output to memory and signal the next kernel to start. This means they can safely be dropped in with any other set of kernels using PDL as long as they also adhere to waiting on the prior to flush its memory as well.

For more information, we refer you to the [PDL section in the CUDA Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#programmatic-dependent-launch-and-synchronization).

## Using dependent launch in CUTLASS[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/dependent_kernel_launch.html#using-dependent-launch-in-cutlass "Link to this heading")

When building CUTLASS, you can use the `CUTLASS_ENABLE_GDC_FOR_SM90` and `CUTLASS_ENABLE_GDC_FOR_SM100` macro respectively to enable PDL-related instructions:

cmake . -DCUTLASS\_ENABLE\_GDC\_FOR\_SM90=1

Copy to clipboard

Note that this only adds PDL-related instructions to the _kernels_, but to actually allow a dependent launch, you must also run your GEMM kernel with PDL:

gemm.run(
  /\* stream = \*/ stream,
  /\* cuda\_adapter = \*/ nullptr,
  /\* launch\_with\_pdl = \*/ true
);\_

Copy to clipboard

## Model-Aware Optimizations with PDL[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/dependent_kernel_launch.html#model-aware-optimizations-with-pdl "Link to this heading")

In [example 63](https://github.com/NVIDIA/cutlass/tree/main/examples/63_hopper_gemm_with_weight_prefetch/README.md), we use PDL to explicitly optimize for performance of kernels where we know that one of the input matrices (our weights) will not be produced by a prior kernel. In that case, we only need to wait on the prior kernels memory flush in order to load the other input matrix (our activations). During our prologue, we can prefetch our weights to improve performance for memory bandwidth-bound problem sizes. For more information, we refer the reader to [the example](https://github.com/NVIDIA/cutlass/tree/main/examples/63_hopper_gemm_with_weight_prefetch/README.md).