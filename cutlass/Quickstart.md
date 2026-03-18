Quickstart
Prerequisites
CUTLASS requires:

NVIDIA CUDA Toolkit (11.4 or later required, 12.0 recommended)

CMake 3.18+

host compiler supporting C++17 or greater (minimum g++ 7.5.0)

Python 3.6+

CUTLASS may be optionally compiled and linked with

cuBLAS

cuDNN v7.6 or later

Initial build steps
Construct a build directory and run CMake.

$ export CUDACXX=${CUDA_INSTALL_PATH}/bin/nvcc

$ mkdir build && cd build

$ cmake .. -DCUTLASS_NVCC_ARCHS=90a            # compiles for NVIDIA Hopper GPU architecture
$ cmake .. -DCUTLASS_NVCC_ARCHS=100a           # compiles for NVIDIA Blackwell SM100 GPU architecture
If your goal is strictly to build only the CUTLASS Profiler and to minimize compilation time, we suggest executing the following CMake command in an empty build/ directory.

$ cmake .. -DCUTLASS_NVCC_ARCHS=90a -DCUTLASS_ENABLE_TESTS=OFF -DCUTLASS_UNITY_BUILD_ENABLED=ON
This reduces overall compilation time by excluding unit tests and enabling the unity build.

You may reduce build times by compiling only certain operations by setting the CUTLASS_LIBRARY_OPERATIONS flag as shown below, executed from an empty build/ directory. This only compiles 2-D convolution kernels.

$ cmake .. -DCUTLASS_NVCC_ARCHS=90a -DCUTLASS_LIBRARY_OPERATIONS=conv2d
You may also filter kernels by name by supplying a filter string with flag CUTLASS_LIBRARY_KERNELS. For example the below command selects only CUTLASS-3 kernels.

$ cmake .. -DCUTLASS_NVCC_ARCHS=90a -DCUTLASS_LIBRARY_KERNELS=cutlass3x*
See more examples on selectively compiling CUTLASS GEMM and convolution kernels here.

You may explicitly exclude cuBLAS and cuDNN as dependencies with the following CMake flags.

-DCUTLASS_ENABLE_CUBLAS=OFF

-DCUTLASS_ENABLE_CUDNN=OFF

Build and run the CUTLASS Profiler
From the build/ directory created above, compile the CUTLASS Profiler.

$ make cutlass_profiler -j12
Then execute the CUTLASS Profiler computing GEMM, execute the following command.

$ ./tools/profiler/cutlass_profiler --kernels=sgemm --m=4352 --n=4096 --k=4096

=============================
  Problem ID: 1

    Provider: CUTLASS
   Operation: cutlass_simt_sgemm_128x128_nn

 Disposition: Passed
      Status: Success

   Arguments:  --m=4352 --n=4096 --k=4096 --A=f32:column --B=f32:column --C=f32:column --alpha=1 --beta=0  \
               --split_k_slices=1 --batch_count=1 --op_class=simt --accum=f32 --cta_m=128 --cta_n=128 --cta_k=8  \
               --stages=2 --warps_m=2 --warps_n=2 --warps_k=1 --inst_m=1 --inst_n=1 --inst_k=1 --min_cc=50  \
               --max_cc=1024

       Bytes: 52428800  bytes
       FLOPs: 146064539648  flops

     Runtime: 10.5424  ms
      Memory: 4.63158 GiB/s

        Math: 13854.9 GFLOP/s
To execute the CUTLASS Profiler for convolution, run the following example.

$ ./tools/profiler/cutlass_profiler --kernels=s1688fprop --n=8 --h=224 --w=224 --c=128 --k=128 --r=3 --s=3 --pad_h=1 --pad_w=1
To execute all CUTLASS 2-D convolution operators, execute the following.

$ ./tools/profiler/cutlass_profiler --operation=conv2d --n=8 --h=224 --w=224 --c=128 --k=128 --r=3 --s=3


=============================
  Problem ID: 1

        Provider: CUTLASS
   OperationKind: conv2d
       Operation: cutlass_simt_sfprop_optimized_128x128_8x2_nhwc

          Status: Success
    Verification: ON
     Disposition: Passed

reference_device: Passed

       Arguments: --conv_kind=fprop --n=8 --h=224 --w=224 --c=128 --k=128 --r=3 --s=3 --p=224 --q=224 --pad_h=1 --pad_w=1  \
                  --stride_h=1 --stride_w=1 --dilation_h=1 --dilation_w=1 --Activation=f32:nhwc --Filter=f32:nhwc --Output=f32:nhwc  \
                  --conv_mode=cross --iterator_algorithm=optimized --alpha=1 --beta=0 --split_k_mode=serial --split_k_slices=1  \
                  --eq_gemm_provider=none --op_class=simt --accum=f32 --cta_m=128 --cta_n=128 --cta_k=8 --stages=2 --warps_m=4  \
                  --warps_n=2 --warps_k=1 --inst_m=1 --inst_n=1 --inst_k=1 --min_cc=50 --max_cc=1024

           Bytes: 2055798784  bytes
           FLOPs: 118482796544  flops

         Runtime: 8.13237  ms
          Memory: 235.431 GiB/s

            Math: 14569.3 GFLOP/s
See documentation for the CUTLASS Profiler for more details.

Build and run CUTLASS Unit Tests
From the build/ directory created above, simply build the target test_unit to compile and run all unit tests.

$ make test_unit -j
...
...
...
[----------] Global test environment tear-down
[==========] 946 tests from 57 test cases ran. (10812 ms total)
[  PASSED  ] 946 tests.
$
The exact number of tests run is subject to change as we add more functionality.

No tests should fail. Unit tests automatically construct the appropriate runtime filters to avoid executing on architectures that do not support all features under test.

The unit tests are arranged hierarchically mirroring the CUTLASS Template Library. This enables parallelism in building and running tests as well as reducing compilation times when a specific set of tests are desired.

For example, the following executes strictly the warp-level GEMM tests.

$ make test_unit_gemm_warp -j
...
...
[----------] 3 tests from SM75_warp_gemm_tensor_op_congruous_f16
[ RUN      ] SM75_warp_gemm_tensor_op_congruous_f16.128x128x8_32x128x8_16x8x8
[       OK ] SM75_warp_gemm_tensor_op_congruous_f16.128x128x8_32x128x8_16x8x8 (0 ms)
[ RUN      ] SM75_warp_gemm_tensor_op_congruous_f16.128x128x32_64x64x32_16x8x8
[       OK ] SM75_warp_gemm_tensor_op_congruous_f16.128x128x32_64x64x32_16x8x8 (2 ms)
[ RUN      ] SM75_warp_gemm_tensor_op_congruous_f16.128x128x32_32x32x32_16x8x8
[       OK ] SM75_warp_gemm_tensor_op_congruous_f16.128x128x32_32x32x32_16x8x8 (1 ms)
[----------] 3 tests from SM75_warp_gemm_tensor_op_congruous_f16 (3 ms total)
...
...
[----------] Global test environment tear-down
[==========] 104 tests from 32 test cases ran. (294 ms total)
[  PASSED  ] 104 tests.
[100%] Built target test_unit_gemm_warp
Building for Multiple Architectures
To minimize compilation time, specific GPU architectures can be enabled via the CMake command, selected by CUDA Compute Capability.

NVIDIA Blackwell Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS=100a              # compiles for NVIDIA Blackwell GPU architecture
NVIDIA Hopper Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS=90a              # compiles for NVIDIA Hopper GPU architecture
NVIDIA Ampere Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS=80               # compiles for NVIDIA Ampere GPU architecture
NVIDIA Turing Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS=75               # compiles for NVIDIA Turing GPU architecture
NVIDIA Volta Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS=70               # compiles for NVIDIA Volta GPU architecture
NVIDIA Pascal Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS="60;61"          # compiles for NVIDIA Pascal GPU architecture
NVIDIA Maxwell Architecture.

$ cmake .. -DCUTLASS_NVCC_ARCHS="50;53"          # compiles for NVIDIA Maxwell GPU architecture
Using CUTLASS within other applications
Applications should list /include within their include paths. They must be compiled as C++17 or greater.

Example: print the contents of a variable storing half-precision data.

#include <iostream>
#include <cutlass/cutlass.h>
#include <cutlass/numeric_types.h>
#include <cutlass/core_io.h>

int main() {

  cutlass::half_t x = 2.25_hf;

  std::cout << x << std::endl;

  return 0;
}
Launching a GEMM kernel in CUDA
Example: launch a mixed-precision GEMM targeting Turing Tensor Cores.

Note, this example uses CUTLASS Utilities. Be sure tools/util/include is listed as an include path.

#include <cutlass/numeric_types.h>
#include <cutlass/gemm/device/gemm.h>

#include <cutlass/util/host_tensor.h>

int main() {

  // Define the GEMM operation
  using Gemm = cutlass::gemm::device::Gemm<
    cutlass::half_t,                           // ElementA
    cutlass::layout::ColumnMajor,              // LayoutA
    cutlass::half_t,                           // ElementB
    cutlass::layout::ColumnMajor,              // LayoutB
    cutlass::half_t,                           // ElementOutput
    cutlass::layout::ColumnMajor,              // LayoutOutput
    float,                                     // ElementAccumulator
    cutlass::arch::OpClassTensorOp,            // tag indicating Tensor Cores
    cutlass::arch::Sm75                        // tag indicating target GPU compute architecture
  >;

  Gemm gemm_op;
  cutlass::Status status;

  //
  // Define the problem size
  //
  int M = 512;
  int N = 256;
  int K = 128;

  float alpha = 1.25f;
  float beta = -1.25f;

  //
  // Allocate device memory
  //

  cutlass::HostTensor<cutlass::half_t, cutlass::layout::ColumnMajor> A({M, K});
  cutlass::HostTensor<cutlass::half_t, cutlass::layout::ColumnMajor> B({K, N});
  cutlass::HostTensor<cutlass::half_t, cutlass::layout::ColumnMajor> C({M, N});

  cutlass::half_t const *ptrA = A.device_data();
  cutlass::half_t const *ptrB = B.device_data();
  cutlass::half_t const *ptrC = C.device_data();
  cutlass::half_t       *ptrD = C.device_data();

  int lda = A.device_ref().stride(0);
  int ldb = B.device_ref().stride(0);
  int ldc = C.device_ref().stride(0);
  int ldd = C.device_ref().stride(0);
  //
  // Launch GEMM on the device
  //

  status = gemm_op({
    {M, N, K},
    {ptrA, lda},            // TensorRef to A device tensor
    {ptrB, ldb},            // TensorRef to B device tensor
    {ptrC, ldc},            // TensorRef to C device tensor
    {ptrD, ldd},            // TensorRef to D device tensor - may be the same as C
    {alpha, beta}           // epilogue operation arguments
  });

  if (status != cutlass::Status::kSuccess) {
    return -1;
  }

  return 0;
}
Note, the above could be simplified as follows using helper methods defined in HostTensor.

  cutlass::HostTensor<cutlass::half_t, cutlass::layout::ColumnMajor> A({M, K});
  cutlass::HostTensor<cutlass::half_t, cutlass::layout::ColumnMajor> B({K, N});
  cutlass::HostTensor<cutlass::half_t, cutlass::layout::ColumnMajor> C({M, N});

  //
  // Use the TensorRef returned by HostTensor::device_ref().
  //

  status = gemm_op({
    {M, N, K},
    A.device_ref(),            // TensorRef to A device tensor
    B.device_ref(),            // TensorRef to B device tensor
    C.device_ref(),            // TensorRef to C device tensor
    C.device_ref(),            // TensorRef to D device tensor - may be the same as C
    {alpha, beta}              // epilogue operation arguments
  });
Launching a GEMM kernel using CUTLASS 3.0 or newer
Example: launch a mixed-precision GEMM targeting Hopper Tensor Cores.

#include "cutlass/cutlass.h"
#include "cutlass/epilogue/collective/default_epilogue.hpp"
#include "cutlass/epilogue/thread/linear_combination.h"
#include "cutlass/gemm/collective/collective_builder.hpp"
#include "cutlass/gemm/device/gemm_universal_adapter.h"
#include "cutlass/gemm/kernel/gemm_universal.hpp"

#include "cutlass/util/host_tensor.h"
#include "cutlass/util/packed_stride.hpp"

using namespace cute;

int main(int argc, char const **args) {

  // A matrix configuration
  using         ElementA    = cutlass::half_t;                                // Element type for A matrix operand
  using         LayoutA     = cutlass::layout::RowMajor;                      // Layout type for A matrix operand
  constexpr int AlignmentA  = 128 / cutlass::sizeof_bits<ElementA>::value;    // Memory access granularity/alignment of A matrix in units of elements (up to 16 bytes)

  // B matrix configuration
  using         ElementB    = cutlass::half_t;                                // Element type for B matrix operand
  using         LayoutB     = cutlass::layout::ColumnMajor;                   // Layout type for B matrix operand
  constexpr int AlignmentB  = 128 / cutlass::sizeof_bits<ElementB>::value;    // Memory access granularity/alignment of B matrix in units of elements (up to 16 bytes)

  // C/D matrix configuration
  using         ElementC    = cutlass::half_t;                                // Element type for C and D matrix operands
  using         LayoutC     = cutlass::layout::ColumnMajor;                   // Layout type for C and D matrix operands

  // Core kernel configurations
  using ElementAccumulator  = float;                                          // Element type for internal accumulation
  using ArchTag             = cutlass::arch::Sm90;                            // Tag indicating the minimum SM that supports the intended feature
  using OperatorClass       = cutlass::arch::OpClassTensorOp;                 // Operator class tag
  using TilesShape          = Shape<_128,_128,_64>;                           // Threadblock-level tile size
  using ClusterShape        = Shape<_1,_2,_1>;                                // Shape of the threadblocks in a cluster
  using StageCountType = cutlass::gemm::collective::StageCountAuto;           // Stage count maximized based on the tile size
  using KernelSchedule = cutlass::gemm::collective::KernelScheduleAuto;       // Kernel to launch based on the default setting in the Collective Builder

  using CollectiveMainloop = typename cutlass::gemm::collective::CollectiveBuilder<
      ArchTag, OperatorClass,
      ElementA, LayoutA, AlignmentA,
      ElementB, LayoutB, AlignmentB,
      ElementAccumulator,
      TilesShape, ClusterShape,
      cutlass::gemm::collective::StageCountAuto,
      cutlass::gemm::collective::KernelScheduleAuto
    >::CollectiveOp;

  using CollectiveEpilogue = cutlass::epilogue::collective::DefaultEpilogue<
      cutlass::gemm::TagToStrideC_t<LayoutC>,
      cutlass::gemm::TagToStrideC_t<LayoutC>,
      cutlass::epilogue::thread::LinearCombination<ElementC, 1, ElementAccumulator, ElementAccumulator>>;

  using GemmKernel = cutlass::gemm::kernel::GemmUniversal<
      Shape<int,int,int>, // Indicates ProblemShape
      CollectiveMainloop,
      CollectiveEpilogue
  >;

  using Gemm = cutlass::gemm::device::GemmUniversalAdapter<GemmKernel>;

  Gemm gemm_op;
  cutlass::Status status;

  //
  // Define the problem size
  //

  int M = 512;
  int N = 256;
  int K = 128;

  float alpha = 1.25f;
  float beta = -1.25f;

  //
  // Allocate device memory
  //

  cutlass::DeviceAllocation<typename Gemm::ElementA> block_A;
  cutlass::DeviceAllocation<typename Gemm::ElementB> block_B;
  cutlass::DeviceAllocation<typename Gemm::ElementC> block_C;
  cutlass::DeviceAllocation<typename Gemm::EpilogueOutputOp::ElementOutput> block_D;

  using StrideA = typename Gemm::GemmKernel::StrideA;
  using StrideB = typename Gemm::GemmKernel::StrideB;
  using StrideC = typename Gemm::GemmKernel::StrideC;
  using StrideD = typename Gemm::GemmKernel::StrideD;

  StrideA stride_A;
  StrideB stride_B;
  StrideC stride_C;
  StrideD stride_D;

  stride_A = cutlass::make_cute_packed_stride(StrideA{}, {M, K, 1});
  stride_B = cutlass::make_cute_packed_stride(StrideB{}, {N, K, 1});
  stride_C = cutlass::make_cute_packed_stride(StrideC{}, {M, N, 1});
  stride_D = cutlass::make_cute_packed_stride(StrideD{}, {M, N, 1});

  block_A.reset(M * K);
  block_B.reset(K * N);
  block_C.reset(M * N);
  block_D.reset(M * N);

  //
  // Launch GEMM on the device
  //

  status = gemm_op({
    cutlass::gemm::GemmUniversalMode::kGemm,
    {M, N, K},
    block_A.get(),
    stride_A,
    block_B.get(),
    stride_B,
    {block_C.get(), stride_C, block_D.get(), stride_D, {alpha, beta}}
  });

  if (status != cutlass::Status::kSuccess) {
    return -1;
  }

  return 0;
}
CUTLASS Library
The CUTLASS Library defines an API for managing and executing collections of compiled kernel instances and launching them from host code without template instantiations in client code.

The host-side launch API is designed to be analogous to BLAS implementations for convenience, though its kernel selection procedure is intended only to be functionally sufficient. It may not launch the optimal tile size for a given problem. It chooses the first available kernel whose data types, layouts, and alignment constraints satisfy the given problem. Kernel instances and a data structure describing them are completely available to client applications which may choose to implement their own selection logic.

cuBLAS offers the best performance and functional coverage for dense matrix computations on NVIDIA GPUs.

The CUTLASS Library is used by the CUTLASS Profiler to manage kernel instances, and it is also used by several SDK examples.

10_planar_complex

11_planar_complex_array

The CUTLASS Library defines enumerated types describing numeric data types, matrix and tensor layouts, math operation classes, complex transformations, and more.

Client applications should specify tools/library/include in their include paths and link against libcutlas_lib.so.

The CUTLASS SDK example 10_planar_complex specifies its dependency on the CUTLASS Library with the following CMake command.

target_link_libraries(
  10_planar_complex
  PRIVATE
  cutlass_lib
  cutlass_tools_util_includes
)
A sample kernel launch from host-side C++ is shown as follows.

#include "cutlass/library/library.h"
#include "cutlass/library/handle.h"

int main() {

  //
  // Define the problem size
  //
  int M = 512;
  int N = 256;
  int K = 128;

  float alpha = 1.25f;
  float beta = -1.25f;

  //
  // Allocate device memory
  //

  cutlass::HostTensor<float, cutlass::layout::ColumnMajor> A({M, K});
  cutlass::HostTensor<float, cutlass::layout::ColumnMajor> B({K, N});
  cutlass::HostTensor<float, cutlass::layout::ColumnMajor> C({M, N});

  float const *ptrA = A.device_data();
  float const *ptrB = B.device_data();
  float const *ptrC = C.device_data();
  float       *ptrD = C.device_data();

  int lda = A.device_ref().stride(0);
  int ldb = B.device_ref().stride(0);
  int ldc = C.device_ref().stride(0);
  int ldd = D.device_ref().stride(0);

  //
  // CUTLASS Library call to execute device GEMM
  //

  cutlass::library::Handle handle;

  //
  // Launch GEMM on CUDA device.
  //

  cutlass::Status status = handle.gemm(
    M,
    N,
    K,

    cutlass::library::NumericTypeID::kF32,          // data type of internal accumulation
    cutlass::library::NumericTypeID::kF32,          // data type of alpha/beta scalars

    &alpha,                                         // pointer to alpha scalar

    cutlass::library::NumericTypeID::kF32,          // data type of A matrix
    cutlass::library::LayoutTypeID::kColumnMajor,   // layout of A matrix
    ptrA,                                           // pointer to A matrix in device memory
    lda,                                            // leading dimension of A matrix

    cutlass::library::NumericTypeID::kF32,          // data type of B matrix
    cutlass::library::LayoutTypeID::kColumnMajor,   // layout of B matrix
    ptrB,                                           // pointer to B matrix in device memory
    ldb,                                            // leading dimension of B matrix

    &beta,                                          // pointer to beta scalar

    cutlass::library::NumericTypeID::kF32,          // data type of C and D matrix

    ptrC,                                           // pointer to C matrix in device memory
    ldc,                                            // leading dimension fo C matrix

    ptrD,                                           // pointer to D matrix in device memory
    ldd                                             // leading dimension of D matrix
  );

  if (status != cutlass::Status::kSuccess) {
    return -1;
  }

  return 0;
}
Example CMake Commands
To instantiate all operations supporting all tile sizes, data types, and alignment constraints, specify -DCUTLASS_LIBRARY_KERNELS=all when running cmake.

$ cmake .. -DCUTLASS_NVCC_ARCHS='70;75;80' -DCUTLASS_LIBRARY_KERNELS=all
The above command line generates about twenty thousand kernels targeting NVIDIA Ampere, Turing, and Volta architectures. Compiling thousands of kernels for three different architectures is time-consuming. Additionally, this would also result in a large binary size and on some platforms linker to fail on building the library.

Enabling the “unity build” instantiates multiple kernel instances in each compilation unit, thereby reducing binary size and avoiding linker limitations on some platforms.

$ cmake .. -DCUTLASS_NVCC_ARCHS="70;75;80" -DCUTLASS_LIBRARY_KERNELS=all -DCUTLASS_UNITY_BUILD_ENABLED=ON
It is advised to only compile CUTLASS kernels for NVIDIA architectures one plans on running. Furthermore, kernels can be selectively included in the CUTLASS Library by specifying filter strings and wildcard characters when executing CMake.

Several examples are defined below for convenience. They may be combined as a comma-delimited list. Compling only the kernels desired reduces compilation time.

GEMM CMake Examples
Example. All GEMM kernels targeting NVIDIA Ampere Tensor Cores.

$ cmake .. -DCUTLASS_NVCC_ARCHS=80 -DCUTLASS_LIBRARY_KERNELS=tensorop*gemm
Example. All GEMM kernels targeting NVIDIA Turing Tensor Cores.

$ cmake .. -DCUTLASS_NVCC_ARCHS=75 -DCUTLASS_LIBRARY_KERNELS=tensorop*gemm
Example. All GEMM kernels with FP32 accumulation targeting NVIDIA Ampere, Turing, and Volta architectures.

$ cmake .. -DCUTLASS_NVCC_ARCHS="70;75;80" -DCUTLASS_LIBRARY_KERNELS=s*gemm
Example. All kernels which expect A and B to be column-major or row-major targeting NVIDIA Ampere, Turing, and Volta architectures.

$ cmake .. -DCUTLASS_NVCC_ARCHS="70;75;80" -DCUTLASS_LIBRARY_KERNELS=gemm*nn,gemm*tt
Example. All planar complex GEMM variants targeting NVIDIA Ampere, Turing, and Volta architectures.

$ cmake .. -DCUTLASS_NVCC_ARCHS="70;75;80" -DCUTLASS_LIBRARY_KERNELS=planar_complex
Convolution CMake Examples
Example. All convolution kernels targeting NVIDIA Ampere’s 16816 Tensor Core operation

$ cmake .. -DCUTLASS_NVCC_ARCHS='80' -DCUTLASS_LIBRARY_KERNELS=s16816fprop,s16816dgrad,s16816wgrad
Example. All forward propagation (fprop) convolution kernels targeting CUDA Cores for multiple NVIDIA architectures

$ cmake .. -DCUTLASS_NVCC_ARCHS='50;60;61;70;75;80' -DCUTLASS_LIBRARY_KERNELS=sfprop
Example. All forward propagation (fprop) convolution kernels with FP32 accumulation and FP16 input targeting NVIDIA Ampere’s 16816 Tensor Core operation

$ cmake .. -DCUTLASS_NVCC_ARCHS='80' -DCUTLASS_LIBRARY_KERNELS=s16816fprop_*_f16
Example. All backward weight gradient (wgrad) convolution kernels with FP32 accumulation, FP16 input, and optimized global memory iterator targeting NVIDIA Ampere, Turing, and Volta Tensor Core operations

$ cmake .. -DCUTLASS_NVCC_ARCHS='70;75;80' -DCUTLASS_LIBRARY_KERNELS=tensorop*s*wgrad_optimized_f16
Instantiating a Blackwell SM100 GEMM kernel
Blackwell SM100 kernels are instantiated very similarly to Hopper kernels. Let us start with an FP8 GEMM without blockscaling as an example.

The kernel starts with setting up datatypes and cluster shapes.

  using LayoutA = cutlass::layout::RowMajor;
  using LayoutB = cutlass::layout::ColumnMajor;
  using LayoutC = cutlass::layout::ColumnMajor;
  using ElementA = cutlass::float_e4m3_t;
  using ElementB = cutlass::float_e4m3_t;
  using ElementC = cutlass::float_e4m3_t;
  using ElementD = cutlass::float_e4m3_t;
  using ElementAccumulator = float;
  using ElementCompute = float;
  using ElementBias = cutlass::half_t;
  using MmaTileShape = cute::Shape<_128,_64,Int<128 / sizeof(ElementA)>>;
  using ClusterShape = cute::Shape<_1,_1,_1>;
The epilogue needs to be instantiated first as the mainloop collective builder takes the shared memory budget of epilogue in the template parameter list. The 3.x epilogue collective builder API has not changed for Blackwell, so the epilogue fusion is built in a same way as an SM90 epilogue.

  using EpilogueSchedule = cutlass::epilogue::TmaWarpSpecialized1Sm;

  using FusionOperation = cutlass::epilogue::fusion::LinearCombination<
    ElementD,
    ElementCompute,
    ElementC
  >;

  using CollectiveEpilogue = typename cutlass::epilogue::collective::CollectiveBuilder<
      cutlass::arch::Sm100, cutlass::arch::OpClassTensorOp,
      MmaTileShape, ClusterShape,
      cutlass::epilogue::collective::EpilogueTileAuto,
      ElementAccumulator, ElementCompute,
      ElementC, LayoutC, 16 / sizeof(ElementC),
      ElementD, LayoutC, 16 / sizeof(ElementD),
      EpilogueSchedule,
      FusionOperation
    >::CollectiveOp;
One can refer to our Sm100 unit tests as examples of how to correctly choose mainloop schedules. All of our dispatch policies can be found in dispatch_policy.hpp and more comprehensive Blackwell specific documentation for valid dispatch policies can be in blackwell_functionality.md.

  using MainloopSchedule = cutlass::gemm::KernelTmaWarpSpecialized1SmSm100;
  using CollectiveMainloop = typename cutlass::gemm::collective::CollectiveBuilder<
      cutlass::arch::Sm100, cutlass::arch::OpClassTensorOp,
      ElementA, LayoutA, 16 / sizeof(ElementA),
      ElementB, LayoutB, 16 / sizeof(ElementB),
      ElementAccumulator,
      MmaTileShape, ClusterShape,
      cutlass::gemm::collective::StageCountAutoCarveout<static_cast<int>(sizeof(typename CollectiveEpilogue::SharedStorage))>,
      MainloopSchedule
    >::CollectiveOp;

  using GemmKernel = cutlass::gemm::kernel::GemmUniversal<
      Shape<int,int,int,int>,
      CollectiveMainloop,
      CollectiveEpilogue
  >;
Instantiating a blockscaled GEMM kernel is slightly different. Referring to an MXFP8 GEMM sample unit test, it takes a different tensor operation class:

  using ElementA = cutlass::mx_float8_t<cutlass::float_e4m3_t>;
  using ElementB = cutlass::mx_float8_t<cutlass::float_e4m3_t>;
are needed in the mainloop builder:

  using CollectiveMainloop = typename cutlass::gemm::collective::CollectiveBuilder<
      cutlass::arch::Sm100, cutlass::arch::OpClassTensorOp,
      ElementA, LayoutA, 16,
      ElementB, LayoutB, 16,
      ElementAccumulator,
      MmaTileShape, ClusterShape,
      cutlass::gemm::collective::StageCountAutoCarveout<static_cast<int>(sizeof(typename CollectiveEpilogue::SharedStorage))>,
      cutlass::gemm::KernelScheduleAuto
    >::CollectiveOp;
We encourage a user to refer to Sm100 unit tests and the generated profiler-based kernels as more comprehensive samples.

# IDE Setup for CUTLASS Development[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#ide-setup-for-cutlass-development "Link to this heading")

This document outlines instructions and tips for setting up a local editor for CUTLASS development, including support for intellisense, go-to-definition, code formatting, and so on.

## Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#overview "Link to this heading")

In order for any intellisense tool to work with CUTLASS, the following things need to be configured with it:

-   Include paths, i.e. where the compiler (or in this case, the intellisense tool) should look for header files
-   Compiler flags; especially the C++ standard (`--std`)
-   Preprocessor variables; especially CUDA-related ones

One usually needs to configure the above variables in a settings file. Below, two config approaches are described: for VSCode, and for any editor that uses the clangd language server, which includes Vim, Emacs, NeoVim, Sublime Text, and so on. Note that VSCode can also be configured to use clangd. It might be worth setting up clangd for VSCode rather than the default intellisense, and you might see faster responses and more stable performance with clangd.

## VSCode Setup[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#vscode-setup "Link to this heading")

1.  Install the [Official C/C++ extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
2.  Open settings…
    
    1.  `Ctrl+Shift+P` to open the command palette
    2.  Enter “C/C++” to filter results
    3.  Select “C/C++ Edit Configurations (UI)” (or “… (JSON)” if you feel like editing the raw JSON)
    4.  View the documentation for these settings [here](https://code.visualstudio.com/docs/cpp/customize-cpp-settings)
3.  Edit “Include Path” to set up **include paths**. For CUTLASS, this includes the following:
    
    -   `${workspaceFolder}/include`
    -   `${workspaceFolder}/tools/util/include`
    -   `${workspaceFolder}/examples/common`
    -   …others, depending on which files you edit
4.  Edit C++ standard to be `c++17`, `gnu++17`, or equivalent.
5.  Edit `defines` to define preprocessor variables. See [Global Config below](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#global-config) for examples. The important ones include `__CUDACC_VER_MAJOR__`, `__CUDA_ARCH__`, `__CUDA_ARCH_FEAT_SM90_ALL__`. But configure them according to your target architecture.
6.  …and possible edit any other fields for your specific setup.

## clangd Setup[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#clangd-setup "Link to this heading")

`clangd` is a C++ language server that is part of the LLVM project. You must first set it up your specific IDE:

-   `clangd` official [documentation](https://clangd.llvm.org/installation#editor-plugins) for editor setup.
-   NeoVim setup is possible through [lsp](https://neovim.io/doc/user/lsp.html) and either manually installing clangd or using an installation manager like Mason.

Then, one needs to edit the config ([documentation](https://clangd.llvm.org/config)). One typically has a **global** and a **per-project** config.

### Global Config[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#global-config "Link to this heading")

Here is one example for a global config. On linux this is usually located at `~/.config/clangd/config.yaml` . Here is one example config for CUDA projects on SM90. The key settings here are the preprocessor vars (`-D__CUDACC_VER_MAJOR__` , `-D__CUDA_ARCH__`)

CompileFlags:
  Compiler: /usr/local/cuda/bin/nvcc
  Add:
    - --cuda-path=/usr/local/cuda
    - --cuda-gpu-arch=sm\_90a
    - -I/usr/local/cuda/include
    - "-xcuda"
    # report all errors
    - "-ferror-limit=0"
    - --cuda-gpu-arch=sm\_90a
    - --std=c++17
    - "-D\_\_INTELLISENSE\_\_"
    - "-D\_\_CLANGD\_\_"
    - "-DCUDA\_12\_0\_SM90\_FEATURES\_SUPPORTED"
    - "-DCUTLASS\_ARCH\_MMA\_SM90\_SUPPORTED=1"
    - "-D\_LIBCUDACXX\_STD\_VER=12"
    - "-D\_\_CUDACC\_VER\_MAJOR\_\_=12"
    - "-D\_\_CUDACC\_VER\_MINOR\_\_=3"
    - "-D\_\_CUDA\_ARCH\_\_=900"
    - "-D\_\_CUDA\_ARCH\_FEAT\_SM90\_ALL"
    - "-Wno-invalid-constexpr"
  Remove:
    # strip CUDA fatbin args
    - "-Xfatbin\*"
    # strip CUDA arch flags
    - "-gencode\*"
    - "--generate-code\*"
    # strip CUDA flags unknown to clang
    - "-ccbin\*"
    - "--compiler-options\*"
    - "--expt-extended-lambda"
    - "--expt-relaxed-constexpr"
    - "-forward-unknown-to-host-compiler"
    - "-Werror=cross-execution-space-call"
Hover:
  ShowAKA: No
InlayHints:
  Enabled: No
Diagnostics:
  Suppress:
    - "variadic\_device\_fn"
    - "attributes\_not\_allowed"

Copy to clipboard

### Local Config[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#local-config "Link to this heading")

Local config is needed to specify per-project settings, especially include paths. An example is:

CompileFlags:
  Add:
    - -I</absolute/path/to/cutlass>/include/
    - -I</absolute/path/to/cutlass>/tools/util/include/
    - -I</absolute/path/to/cutlass>/cutlass/examples/common/

Copy to clipboard

Note that absolute paths are needed since clangd doesn’t support relative paths.

### Note on compile\_commands.json[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/ide_setup.html#note-on-compile-commands-json "Link to this heading")

For typical C++ projects, clangd can _automatically_ configure itself by parsing the `compile_commands.json` generated by your CMake build. The path to such a file is by default `build/compile_commands.json` and is configured by the `CompilationDatabase` config.

This is usually a convenient way to configure projects, but it’s not as simple for CUDA/nvcc projects, since clang doesn’t understand many of the compiler flags used by nvcc. Hence, for now, we don’t recommend using `compile_commands.json` to configure your CUDA project.

# Building with Clang as host compiler[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/build/building_with_clang_as_host_compiler.html#building-with-clang-as-host-compiler "Link to this heading")

CUTLASS 3.2(.1) reintroduces support for building with Clang as host compiler, and NVCC as device compiler. This is NOT the same as building with Clang as both host and device compiler (“CUDA Clang”).

## Software prerequisites[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/build/building_with_clang_as_host_compiler.html#software-prerequisites "Link to this heading")

1.  Clang (regularly tested with Clang 17; occasionally tested with Clang 10 and greater)
2.  CUDA Toolkit (tested with 12.2; other versions likely work)
3.  CMake (at least 3.18)
4.  git
5.  Python (at least 3.6)

Experience with Ubuntu 22.04 LTS is that clang requires the following packages to be installed.

$ sudo apt-get install clang cmake ninja-build pkg-config libgtk-3-dev liblzma-dev libstdc++-12-dev

Copy to clipboard

A symptom of not installing all needed dependencies is the following error when attempting to use clang: `"/usr/bin/ld: cannot find -lstdc++: No such file or directory"`.

## Running CMake[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/build/building_with_clang_as_host_compiler.html#running-cmake "Link to this heading")

### Required CMake options[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/build/building_with_clang_as_host_compiler.html#required-cmake-options "Link to this heading")

The Clang build requires specifying the following CMake options. Replace `<path-to-clang++>` with the path to your `clang++` executable. You may use `clang++` directly if it is in your `PATH`.

-   `CMAKE_CXX_COMPILER=<path-to-clang++>`
-   `CMAKE_CUDA_HOST_COMPILER=<path-to-clang++>`

One must set both! It’s not enough just to set the `CXX` environment variable, for example. Symptoms of only setting `CMAKE_CXX_COMPILER` (or only setting the `CXX` environment variable) include `cc1plus` (GCC’s compiler executable) reporting build errors due to it not understanding Clang’s command-line options.

Users can also specify a particular CUDA Toolkit version by setting the CMake option `CMAKE_CUDA_COMPILER` to the path to the `nvcc` executable that lives in the CUDA Toolkit’s directory. For example, if `${PATH_TO_CUDA_TOOLKIT}` is the CUDA Toolkit directory, then one can set `CMAKE_CUDA_COMPILER` as follows.

-   `CMAKE_CUDA_COMPILER=${PATH_TO_CUDA_TOOLKIT}/bin/nvcc`

# Functionality[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#functionality "Link to this heading")

Note : CUTLASS-3 requires users to use CUDA 11.4 or newer, and SM70 or newer, for the target toolkit and architecture, respectively.

-   N - Column Major Matrix
-   T - Row Major matrix
-   {N,T} x {N,T} - All combinations, i.e., NN, NT, TN, TT
-   [NHWC](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/layout/tensor.h#L63-206) - 4 dimension tensor used for convolution
-   [NCxHWx](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/layout/tensor.h#L290-395) - Interleaved 4 dimension tensor used for convolution
-   f - floating point
-   s - signed int
-   b - bit
-   cf - complex float
-   bf16 - bfloat16
-   tf32 - tfloat32
-   Simt - Use Simt CUDA Core MMA
-   TensorOp - Use Tensor Core MMA
-   SpTensorOp - Use Sparse Tensor Core MMA
-   WmmaTensorOp - Use WMMA abstraction to use Tensor Core MMA

## Device-level GEMM[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#device-level-gemm "Link to this heading")

The following tables summarize device-level GEMM kernels in CUTLASS, organized by opcode class, data type, and layout. Hyperlinks to relevant unit tests demonstrate how specific template instances may be defined.

### CUTLASS 3.x Kernels[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#cutlass-3-x-kernels "Link to this heading")

| **Opcode Class** | **Compute Capability** | **CUDA Toolkit** | **Data Type** | **Layouts** | **Unit Test** |
| --- | --- | --- | --- | --- | --- |
| **TensorOp** | 90a | 12.0+ | `f16 * f16 + { f16, f32 } => { f16, f32 }` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/sm90_gemm_f16_f16_f16_tensor_op_f32_cluster_warpspecialized.cu) |
| **TensorOp** | 90a | 12.0+ | `bf16 * bf16 + { f16, f32 } => { bf16, f32 }` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/sm90_gemm_bf16_bf16_bf16_tensor_op_f32.cu) |
| **TensorOp** | 90a | 12.0+ | `{f32, tf32} * {f32, tf32} + f32 => f32` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/sm90_gemm_f32_f32_f32_tensor_op_f32.cu) |
| **TensorOp** | 90a | 12.0+ | `s8 * s8 + s32 => {s32, s8}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/sm90_gemm_s8_s8_s8_tensor_op_s32.cu) |

### CUTLASS 2.x Kernels[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#cutlass-2-x-kernels "Link to this heading")

| **Opcode Class** | **Compute Capability** | **CUDA Toolkit** | **Data Type** | **Layouts** | **Unit Test** |
| --- | --- | --- | --- | --- | --- |
| **Simt** | 50+ | 11.4+ | `f32 * f32 + f32 => f32` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/simt_sgemm_nt_sm50.cu) |
| **Simt** | 50+ | 11.4+ | `f64 * f64 + f64 => f64` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/simt_dgemm_nt_sm50.cu) |
| **Simt** | 60+ | 11.4+ | `f16 * f16 + f16 => f16` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/simt_hgemm_nt_sm50.cu) |
| **Simt** | 61+ | 11.4+ | `s8 * s8 + s32 => {s32,s8}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/simt_igemm_nt_sm50.cu) |
| **WmmaTensorOp** | 70+ | 11.4+ | `f16 * f16 + f16 => f16` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16t_f16t_f16n_wmma_tensor_op_f16_sm70.cu) |
| **WmmaTensorOp** | 70+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16t_f16t_f16n_wmma_tensor_op_f32_sm70.cu) |
| **WmmaTensorOp** | 75+ | 11.4+ | `s8 * s8 + s32 => {s32, s8}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_s8t_s8n_s8t_wmma_tensor_op_s32_sm72.cu) |
| **WmmaTensorOp** | 75+ | 11.4+ | `s4 * s4 + s32 => {s32, s4}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/blob/main/test/unit/gemm/device/gemm_s4t_s4n_s32t_wmma_tensor_op_s32_sm75.cu) |
| **WmmaTensorOp** | 75+ | 11.4+ | `b1 ^ b1 + s32 => {s32, b1}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/blob/main/test/unit/gemm/device/gemm_b1t_b1n_s32n_wmma_tensor_op_s32_sm75.cu) |
| **TensorOp** | 70+ | 11.4+ | `f16 * f16 + f16 => f16` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16t_f16t_volta_tensor_op_f16_sm70.cu) |
| **TensorOp** | 70+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16t_f32t_volta_tensor_op_f32_sm70.cu) |
| **TensorOp** | 75+ | 11.4+ | `f16 * f16 + f16 => f16` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16t_f16t_tensor_op_f16_sm75.cu) |
| **TensorOp** | 75+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/blob/main/test/unit/gemm/device/gemm_f16n_f16t_f32t_tensor_op_f32_sm75.cu) |
| **TensorOp** | 75+ | 11.4+ | `s8 * s8 + s32 => {s32, s8}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_s8t_s8n_s32n_tensor_op_s32_sm75.cu) |
| **TensorOp** | 75+ | 11.4+ | `s4 * s4 + s32 => {s32, s4}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/blob/main/test/unit/gemm/device/gemm_s4t_s4n_s32n_tensor_op_s32_sm75.cu) |
| **TensorOp** | 75+ | 11.4+ | `b1 ^ b1 + s32 => {s32, b1}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_b1t_b1n_s32n_tensor_op_s32_sm75.cu) |
| **TensorOp** | 80+ | 11.4+ | `f16 * f16 + f16 => f16` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16t_f16t_tensor_op_f16_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16t_f16t_tensor_op_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `bf16 * bf16 + f32 => {bf16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/blob/main/test/unit/gemm/device/gemm_bf16t_bf16t_bf16t_tensor_op_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `tf32 * tf32 + f32 => f32` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/blob/main/test/unit/gemm/device/gemm_tf32n_tf32t_f32t_tensor_op_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `s8 * s8 + s32 => {s32, s8}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_s8t_s8n_s32n_tensor_op_s32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `s4 * s4 + s32 => {s32, s4}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_s4t_s4n_s32n_tensor_op_s32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `b1 ^ b1 + s32 => {s32, b1}` | { T } x { N } => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_b1t_b1n_s32n_tensor_op_s32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `f64 * f64 + f64 => f64` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f64n_f64t_f64t_tensor_op_f64_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `cf32 * cf32 + cf32 => cf32` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_cf32n_cf32t_cf32t_tensor_op_tf32_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `cf64 * cf64 + cf64 => cf64` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_cf64n_cf64t_cf64t_tensor_op_f64_sm80.cu), [Gaussian 3m](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_cf64n_cf64t_cf64t_tensor_op_f64_gaussian_sm80.cu) |
| **SpTensorOp** | 80+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16n_f32t_tensor_op_f32_sparse_sm80.cu) |
| **SpTensorOp** | 80+ | 11.4+ | `bf16 * bf16 + f32 => {bf16, f32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f16n_f16n_f32t_tensor_op_f32_sparse_sm80.cu) |
| **SpTensorOp** | 80+ | 11.4+ | `tf32 * tf32 + f32 => f32` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f32n_f32n_f32t_tensor_op_f32_sparse_sm80.cu) |
| **SpTensorOp** | 80+ | 11.4+ | `s8 * s8 + s32 => {s8, s32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_s8t_s8n_s32t_tensor_op_s32_sparse_sm80.cu) |
| **SpTensorOp** | 80+ | 11.4+ | `s4 * s4 + s32 => {s4, s32}` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_s4t_s4n_s32t_tensor_op_s32_sparse_sm80.cu) |
| **TensorOp** | 90+ | 11.8+ | `f64 * f64 + f64 => f64` | {N,T} x {N,T} => {N,T} | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/gemm/device/gemm_f64n_f64t_f64t_tensor_op_f64_sm90.cu) |

## Device-level Implicit GEMM convolution[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#device-level-implicit-gemm-convolution "Link to this heading")

The following table summarizes device-level implicit GEMM convolution kernels in CUTLASS, organized by opcode class, data type, and layout. Hyperlinks to relevant conv2d fprop unit tests demonstrate how specific template instances may be defined. One can find and/or create equivalent dgrad and wgrad convolutional operators.

| **Opcode Class** | **Compute Capability** | **CUDA Toolkit** | **Data Type** | **Layouts** | **Unit Test** |
| --- | --- | --- | --- | --- | --- |
| **Simt** | 50+ | 11.4+ | `f32 * f32 + f32 => f32` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_f32nhwc_f32nhwc_f32nhwc_simt_f32_sm50.cu) |
| **Simt** | 50+ | 11.4+ | `cf32 * cf32 + cf32 => cf32` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_cf32nhwc_cf32nhwc_cf32nhwc_simt_f32_sm50.cu) |
| **TensorOp** | 70+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_f16nhwc_f16nhwc_f32nhwc_tensor_op_f32_sm70.cu) |
| **TensorOp** | 75+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_f16nhwc_f16nhwc_f32nhwc_tensor_op_f32_sm75.cu) |
| **TensorOp** | 75+ | 11.4+ | `s8 * s8 + s32 => {s32, s8}` | NHWC, NCxHWx | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s8nhwc_s8nhwc_s32nhwc_tensor_op_s32_sm75.cu), [ncxhwx](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s8ncxhwx_s8cxrskx_s8ncxhwx_tensor_op_s32_sm75.cu) |
| **TensorOp** | 75+ | 11.4+ | `s4 * s4 + s32 => {s32, s4}` | NHWC, NCxHWx | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s4nhwc_s4nhwc_s32nhwc_tensor_op_s32_sm75.cu), [ncxhwx](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s4ncxhwx_s4cxrskx_s4ncxhwx_tensor_op_s32_sm75.cu) |
| **Simt** | 80+ | 11.4+ | `f32 * f32 + f32 => f32` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_f32nhwc_f32nhwc_f32nhwc_simt_f32_sm80.cu) |
| **Simt** | 80+ | 11.4+ | `cf32 * cf32 + cf32 => cf32` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_cf32nhwc_cf32nhwc_cf32nhwc_simt_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `f16 * f16 + f32 => {f16, f32}` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_f16nhwc_f16nhwc_f32nhwc_tensor_op_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `f16 * f16 + f16 => f16` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_f16nhwc_f16nhwc_f32nhwc_tensor_op_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `tf32 * tf32 + f32 => f32` | NHWC | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_tf32nhwc_tf32nhwc_f32nhwc_tensor_op_f32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `s8 * s8 + s32 => {s32, s8}` | NHWC, NCxHWx | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s8nhwc_s8nhwc_s32nhwc_tensor_op_s32_sm80.cu), [ncxhwx](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s8ncxhwx_s8cxrskx_s8ncxhwx_tensor_op_s32_sm80.cu) |
| **TensorOp** | 80+ | 11.4+ | `s4 * s4 + s32 => {s32, s4}` | NHWC, NCxHWx | [example](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s4nhwc_s4nhwc_s32nhwc_tensor_op_s32_sm80.cu), [ncxhwx](https://github.com/NVIDIA/cutlass/tree/main/test/unit/conv/device/conv2d_fprop_implicit_gemm_s4ncxhwx_s4cxrskx_s4ncxhwx_tensor_op_s32_sm80.cu) |

## Warp-level Matrix Multiply with Tensor Cores[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#warp-level-matrix-multiply-with-tensor-cores "Link to this heading")

The following table summarizes supported warp level shapes for each TensorOp instruction.

| **Opcode Class** | **Instruction Shape** | **Warp Shapes** |
| --- | --- | --- |
| **TensorOp** | 8-by-8-by-4 | 32x32x4, 32x64x4, 64x32x4, 64x64x4 |
| **TensorOp** | 16-by-8-by-8 | 32x32x8, 32x64x8, 64x32x8, 64x64x8 |
| **TensorOp** | 16-by-8-by-16 | 32x32x16, 32x64x16, 64x32x16, 64x64x16 |
| **TensorOp** | 8-by-8-by-16 | 32x32x16, 32x64x16, 64x32x16, 64x64x16 |
| **TensorOp** | 8-by-8-by-32 | 32x32x32, 32x64x32, 64x32x32, 64x64x32 |
| **TensorOp** | 16-by-8-by-32 | 32x32x32, 32x64x32, 64x32x32, 64x64x32 |
| **TensorOp** | 16-by-8-by-64 | 32x32x64, 32x64x64, 64x32x64, 64x64x64 |
| **TensorOp** | 8-by-8-by-128 | 32x32x128, 32x64x128, 64x32x128, 64x64x128 |
| **TensorOp** | 16-by-8-by-256 | 32x32x256, 32x64x256, 64x32x256, 64x64x256 |
| **SpTensorOp** | 16-by-8-by-16 | 64x64x16, 64x32x16, 32x64x16, 32x32x16 |
| **SpTensorOp** | 16-by-8-by-32 | 64x64x32, 64x32x32, 32x64x32, 32x32x32 |
| **SpTensorOp** | 16-by-8-by-64 | 64x64x64, 64x32x64, 32x64x64, 32x32x64 |
| **SpTensorOp** | 16-by-8-by-128 | 64x64x128, 64x32x128, 32x64x128, 32x32x128 |

TensorOp instructions depend on a permuted shared memory layout that can be efficiently loaded from. The following tables summarize the destination shared memory layout that can be targeted by matrix operands. It is assumed that each thread loads 128b vectors from global memory with layout specified in the column “GMEM Layout.”

**TensorOp 8-by-8-by-4.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `half_t` | `ColumnMajor` | `ColumnMajorVoltaTensorOpCongruous<16>` |
| **A** | `half_t` | `RowMajor` | `RowMajorVoltaTensorOpCrosswise<16>` |
| **B** | `half_t` | `ColumnMajor` | `ColumnMajorVoltaTensorOpCrosswise<16>` |
| **B** | `half_t` | `RowMajor` | `RowMajorVoltaTensorOpCongruous<16>` |
| **C** | `half_t` | `RowMajor` | `RowMajor` |
| **C** | `float` | `RowMajor` | `RowMajor` |

**TensorOp 16-by-8-by-8.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `half_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<16>` |
| **A** | `half_t` | `RowMajor` | `RowMajorTensorOpCrosswise<16>` |
| **B** | `half_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<16>` |
| **B** | `half_t` | `RowMajor` | `RowMajorTensorOpCongruous<16>` |
| **C** | `half_t` | `RowMajor` | `RowMajor` |
| **C** | `float` | `RowMajor` | `RowMajor` |

**TensorOp 16-by-8-by-8.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `tfloat32_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<32>` |
| **A** | `tfloat32_t` | `RowMajor` | `RowMajorTensorOpCrosswise<32>` |
| **B** | `tfloat32_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<32>` |
| **B** | `tfloat32_t` | `RowMajor` | `RowMajorTensorOpCongruous<32>` |
| **C** | `float` | `RowMajor` | `RowMajor` |

**TensorOp 16-by-8-by-16.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `half_t`, `bfloat16_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<16>` |
| **A** | `half_t`, `bfloat16_t` | `RowMajor` | `RowMajorTensorOpCrosswise<16>` |
| **B** | `half_t`, `bfloat16_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<16>` |
| **B** | `half_t`, `bfloat16_t` | `RowMajor` | `RowMajorTensorOpCongruous<16>` |
| **C** | `half_t` | `RowMajor` | `RowMajor` |
| **C** | `float` | `RowMajor` | `RowMajor` |

**TensorOp 8-by-8-by-4.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `double` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<64>` |
| **A** | `double` | `RowMajor` | `RowMajorTensorOpCrosswise<64>` |
| **B** | `double` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<64>` |
| **B** | `double` | `RowMajor` | `RowMajorTensorOpCongruous<64>` |
| **C** | `double` | `RowMajor` | `RowMajor` |

**TensorOp 8-by-8-by-16.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `int8_t` | `RowMajor` | `RowMajorTensorOpCrosswise<8>` |
| **B** | `int8_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<8>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

**TensorOp 16-by-8-by-32.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `int8_t` | `RowMajor` | `RowMajorTensorOpCrosswise<8>` |
| **B** | `int8_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<8>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

**TensorOp 8-by-8-by-32.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `int4b_t` | `RowMajor` | `RowMajorTensorOpCrosswise<4>` |
| **B** | `int4b_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<4>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

**TensorOp 16-by-8-by-64.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `int4b_t` | `RowMajor` | `RowMajorTensorOpCrosswise<4>` |
| **B** | `int4b_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<4>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

**TensorOp 8-by-8-by-128.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `bin1_t` | `RowMajor` | `RowMajorTensorOpCrosswise<4>` |
| **B** | `bin1_t` | `ColumnMajor` | `ColumnMajorTensorOpCongruous<4>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

**SpTensorOp 16-by-8-by-16.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `tfloat32_t` | `RowMajor` | `RowMajorTensorOpCrosswise<32, 32>` |
| **B** | `tfloat32_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<32, 32>` |
| **C** | `float` | `RowMajor` | `RowMajor` |

**SpTensorOp 16-by-8-by-32.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `half_t` | `RowMajor` | `RowMajorTensorOpCrosswise<16, 64>` |
| **B** | `half_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<16, 64>` |
| **C** | `float` | `RowMajor` | `RowMajor` |

**SpTensorOp 16-by-8-by-64.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `int8_t` | `RowMajor` | `RowMajorTensorOpCrosswise<8, 128>` |
| **B** | `int8_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<8, 128>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

**SpTensorOp 16-by-8-by-128.**

| **Operand** | **Element** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- | --- |
| **A** | `int4b_t` | `RowMajor` | `RowMajorTensorOpCrosswise<4, 256>` |
| **B** | `int4b_t` | `ColumnMajor` | `ColumnMajorTensorOpCrosswise<4, 256>` |
| **C** | `int32_t` | `RowMajor` | `RowMajor` |

## Warp-level Matrix Multiply with CUDA WMMA API[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/functionality.html#warp-level-matrix-multiply-with-cuda-wmma-api "Link to this heading")

The following table summarizes supported warp level shapes for each WmmaTensorOp instruction.

| **Opcode Class** | **Instruction Shape** | **Warp Shapes** |
| --- | --- | --- |
| **WmmaTensorOp** | 16-by-16-by-16 | 32x32x16, 32x64x16, 64x32x16 |
| **WmmaTensorOp** | 8-by-32-by-16 | 32x32x16, 32x64x16, 64x32x16 |
| **WmmaTensorOp** | 32-by-8-by-16 | 32x32x16, 32x64x16, 64x32x16 |
| **WmmaTensorOp** | 8-by-8-by-32 | 32x32x32, 32x64x32, 64x32x32, 64x64x32 |
| **WmmaTensorOp** | 8-by-8-by-128 | 32x32x128, 32x64x128, 64x32x128, 64x64x128 |

CUDA exposes warp-level matrix operations in the CUDA C++ WMMA API. The CUDA C++ WMMA API exposes Tensor Cores via a set of functions and types in the `nvcuda::wmma` namespace. The functions and types in `nvcuda::wmma` provide target-independent APIs and implement architecture-specific tensor operation using TensorOp instruction underneath. CUTLASS exposes WMMA API through WmmaTensorOp. The WmmaTensorOp supports canonical shared memory layouts. The following table summarizes the destination shared memory layout that can be targeted by matrix operands. The WMMA API expects that matrices in shared memory loaded by `nvcuda::wmma::load_matrix_sync()` satisfy 128 bit alignment.

**WmmaTensorOp (all matrix sizes and data types).**

| **Operand** | **GMEM Layout** | **SMEM Layout** |
| --- | --- | --- |
| **A** | `RowMajor`, `ColumnMajor` | `RowMajor`, `ColumnMajor` |
| **B** | `RowMajor`, `ColumnMajor` | `RowMajor`, `ColumnMajor` |
| **C** | `RowMajor`, `ColumnMajor` | `RowMajor`, `ColumnMajor` |

# CUTLASS Terminology[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/terminology.html#cutlass-terminology "Link to this heading")

**cute::Layout**: A `cute::Layout` vocabulary type composed of the hierarchical `cute::Shape` and `cute::Stride` tuples that is used throughout CUTLASS 3.0 to represent and manipulate thread and data layouts. More details are included in the [CuTe specific tensor type documentation](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html).

**cute::Tensor**: A pointer backed by a `cute::Layout` used to represent a tensor. More details are included in the [CuTe specific tensor type documentation](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/03_tensor.html).

**Capacity**: (scalar) physical number of elements in memory required to store a multidimensional object; expressed as the type’s LongIndex type

-   example: the capacity of a column-major matrix is `lda * N`

**Element**: data type describing one item in a multidimensional tensor, array, or matrix

**Extent**: (vector-valued quantity) the logical size of each dimension of a multidimensional index space. Consistent with the [C++ Standard Library](https://en.cppreference.com/w/cpp/types/extent).

-   `Coord<N> extent()`
-   `Index extent(int dim)`

**Fragment**: a register-backed array of elements used to store a thread’s part of a tile

**Index**: signed integer representing quantities aligned with a logical dimension

**Layout**: functor mapping logical coordinates of a tensor to linear offset (as LongIndex); owns stride vectors, if any.

**LongIndex**: signed integer representing offsets in memory; typically wider than Index type

**Numeric Type**: a CUTLASS data type used to represent real-valued quantities; is trivially copyable.

**Pitch Linear**: linear memory allocation obtained from a user-defined 2-D size, which specifies the contiguous and strided dimensions of a tile.

**Planar Complex**: representation of complex tensors as two real-valued tensors, with real elements in one part and imaginary elements in another part of identical layout, separated by an offset

**Policy**: additional details extending the interface of a template guiding internal implementation; typically used to target specific design points known to be efficient

**Rank**: number of dimensions in a multidimensional index space, array, tensor, or matrix. Consistent with [C++ Standard Library](https://en.cppreference.com/w/cpp/types/rank)

**Register**: in device code, registers are the most efficient storage for statically sized arrays of elements. Arrays may be expected to be stored in registers if all accesses are made via constexpr indices or within fully unrolled loops.

**Residue**: partial tile or matrix computation which may require special accommodation for functional correctness or performance

**Size**: (scalar) number of logical elements in a tensor; equal to the product of each member of `extent()`

-   `LongIndex size()`

`sizeof_bits<T>::value` - template pattern returning the size of a numeric type or array in units of bits

**Storage**: when appropriate, refers to some alternative type used to store a packed collection of elements; may be used to handle bit-level packing or make types safe for use in unions

**TensorRef**: contains base pointer and _Layout_ object for referencing infinitely-sized tensor object

**TensorView**: contains _TensorRef_ and extent of a finite mathematical object

**Tile**: partitions of a tensor that have constant extents and layout known at compile time

**Trait**: characteristics of a fully-specialized type, typically used in metaprogramming reflection

**View**: an object containing references to a data structure that it does not own; typically, construction of views is lightweight

**Warp**: a collection of hardware threads executing in lock-step; warp-level operations typically rely on cooperation among the threads within the warp

`AlignedBuffer<T, N>`: statically sized array type; union-safe, no construction guarantee for elements

`Array<T, N>`: container for holding numeric types - handles bit packing for small numeric types (e.g. int4\_t, uint4\_t, bin1\_t) `sizeof(Array<T, N>)` - gives expected value in units of bytes with minimum storage of `1 B`: (sizeof\_bits::value \* N) / 8

**Operator**: an object performing a computation on matrix or tensor objects. May be further refined by scope within the execution model hierarchy. Deprecated starting CUTLASS 3.0, replaced by [MMA and Copy atoms from CuTe](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0t_mma_atom.html).

**Tile Iterator**: abstraction for accessing and traversing a sequence of tiles in a tensor; CUTLASS specifies [formal concepts for tile iterators](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/tile_iterator_concept.html). Deprecated starting CUTLASS 3.0. Replaced by `cute::Layout` in equivalent usage scenarios to represent data tensors.

**Thread Map**: abstraction for defining how threads are mapped to a given tile. Deprecated starting CUTLASS 3.0. Replaced by `cute::Layout` in equivalent usage scenarios to represent thread tensors.

# Fundamental Types[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#fundamental-types "Link to this heading")

CUTLASS defies several fundamental numeric and container classes upon which computations and algorithms algorithms for linear algebra computations are implemented.

Where possible, CUTLASS fundamental types mirror the C++ Standard Library. However, there are circumstances that necessitate divergence from the Standard Library’s specification. In such cases, the CUTLASS implementation adopts unique capitalization to distinguish that standard vocabulary types may not be safely substituted in all cases.

Most types in CUTLASS are usable in both host code and device code. Moreover, they are functional regardless of compute capability, but they may only be efficient when hardware support is present.

## Numeric Types[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#numeric-types "Link to this heading")

CUTLASS defines classes for the following numeric data types.

-   `half_t`: IEEE half-precision floating point (exponent: 5b, mantissa: 10b; literal suffix `_hf`)
-   `bfloat16_t`: BFloat16 data type (exponent: 8b, mantissa: 7b; literal suffix `_bf16`)
-   `tfloat32_t`: Tensor Float 32 data type (exponent: 8b, mantissa: 10b; literal suffix `_tf32`)
-   `int4_t`, `uint4_t`: 4b signed and unsigned integer (literal suffx `_s4`, `_u4`)
-   `bin1_t`: 1b binary numeric type (literal suffix `_b1`)
-   `float_e5m2_t`: 8bits signed float (exponent: 5 bits, mantissa: 2 bits)
-   `float_e4m3_t`: 8bits signed float (exponent: 4 bits, mantissa: 3 bits)
-   `float_ue4m3_t`: 8bits unsigned float (exponent: 4 bits, mantissa: 3 bits)
-   `float_ue8m0_t`: 8bits unsigned float (exponent: 8 bits, mantissa: 0 bits)
-   `float_e3m2_t`: 6bits signed float (exponent: 3 bits, mantissa: 2 bits)
-   `float_e2m3_t`: 6bits signed float (exponent: 2 bits, mantissa: 3 bits)
-   `float_e2m1_t`: 4bits signed float (exponent: 2 bits, mantissa: 1 bits)
-   `type_erased_dynamic_float8_t`: Type agnostic 8 bits signed float allowing the user to provide a specific datatype as runtime argument.
-   `type_erased_dynamic_float6_t`: Type agnostic 6 bits signed float allowing the user to provide a specific datatype as runtime argument.
-   `type_erased_dynamic_float4_t`: Type agnostic 4 bits signed float allowing the user to provide a specific datatype as runtime argument.
-   `mx_float8_t<float_e5m2_t>` or `mx_float8_t<float_e4m3_t>` : Block scaled data type with fp8 element type and float\_ue8m0\_t scale factor and vector size of 32.
-   `mx_float6_t<float_e3m2_t>` or `mx_float6_t<float_e2m3_t>` : Block scaled data type with fp6 element type and float\_ue8m0\_t scale factor and vector size of 32.
-   `mx_float4_t<float_e2m1_t>` : Block scaled data type with signed e2m1 element type and float\_ue8m0\_t scale factor and vector size of 32.
-   `nv_float4_t<float_e2m1_t>` : Block scaled data type with signed e2m1 element type and float\_ue4m3\_t scale factor and vector size of 16.
-   `complex<T>`: defines complex-valued data type based on the supplied real-valued numeric type

Numeric types in CUTLASS may be used in both host and device code and are intended to function like any other plain-old-data type.

If CUTLASS is compiled with `CUTLASS_F16C_ENABLED`, then hardware conversion is used for half-precision types in host code. Regardless, `cutlass::half_t` uses the most efficient NVIDIA GPU hardware instructions available in device code.

Example:

#include <iostream>
#include <cutlass/numeric\_types.h>

\_\_global\_\_ void kernel(cutlass::half\_t x) {
  printf("Device: %f\\n", float(x \* 2.0\_hf));
}

int main() {

  cutlass::half\_t x \= 0.5\_hf;

  std::cin \>> x;

  std::cout << "Host: " << 2.0\_hf \* x << std::endl;

  kernel<<< dim3(1,1), dim3(1,1,1) \>>>(x);

  return 0;
}

Copy to clipboard

## Containers[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#containers "Link to this heading")

CUTLASS uses the following containers extensively for implementing efficient CUDA kernels.

### Array[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#array "Link to this heading")

template <
  typename T,       // element type
  int N             // number of elements
\>
struct Array;

Copy to clipboard

`Array<class T, int N>` defines a statically sized array of elements of type _T_ and size _N_. This class is similar to [`std::array<>`](https://en.cppreference.com/w/cpp/container/array) in the Standard Library with one notable exception: partial specializations exist to pack or unpack elements smaller than one byte.

`Array<>` is intended to be a convenient and uniform container class to store arrays of numeric elements regardless of data type or vector length. The storage needed is expected to be the minimum necessary given the logical size of each numeric type in bits (numeric types smaller than one byte are densely packed). Nevertheless, the size reported by `sizeof(Array<T, N>)` is always an integer multiple of bytes.

Storing numeric elements in a C++ STL-style container class enables useful modern C++ mechanisms such as range-based for loops. For example, to print the elements of `Array<>`, the following range-based for loop syntax is always valid regardless of numeric data type, compute capability, or context in host or device code.

Example:

int const kN;
Array<T, kN\> elements;

CUTLASS\_PRAGMA\_UNROLL                        // required to ensure array remains in registers
for (auto x : elements) {
  printf("%d, %f", int64\_t(x), double(x));   // explictly convert to int64\_t or double
}

Copy to clipboard

When copying `Array<>` objects or passing them as arguments to methods, it is best to avoid accessing individual elements. This enables the use of vector instructions to perform the operation more efficiently. For example, setting all elements to zero is best performed by calling the `clear()` method. Copies should be performed by assigning the entire object.

Example:

#include <cutlass/array.h>

int const kN;
Array<T, kN\> source;
Array<T, kN\> destination;

source.clear();         // set all elements to value of zero

destination \= source;   // copy to \`destination\`

Copy to clipboard

`Array<>` may be used to store elements smaller than one byte such as 4b integers.

Array<int4b\_t, 2\> packed\_integers;

static\_assert(
  sizeof(packed\_integers) \== 1,
 "Packed storage of sub-byte data types is compact.");

// Access array elements using usual indirection and assignment operators
packed\_integers\[0\] \= 2\_s4;
packed\_integers\[1\] \= 3\_s4;

CUTLASS\_PRAGMA\_UNROLL
for (auto x : elements) {
  printf("%d", int(x));       // access elements normally
}

Copy to clipboard

### AlignedArray[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#alignedarray "Link to this heading")

template <
  typename T,          // element type
  int N,               // number of elements
  int Alignment        // alignment requirement in bytes
\>
class AlignedArray;

Copy to clipboard

`AlignedArray` is derived from `Array<T, N>` and supports an optional alignment field. Pointers to objects of type `AlignedArray<>` reliably yield vectorized memory accesses when dereferenced.

Example:

int const kN \= 8;
ArrayAligned<half\_t, kN\> source;
ArrayAligned<half\_t, kN\> const \*ptr \= ...;

source \= \*ptr;          // 128b aligned memory access

Copy to clipboard

### AlignedBuffer[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#alignedbuffer "Link to this heading")

template <
  typename T,          // element type
  int N,               // number of elements
  int Alignment        // alignment requirement in bytes
\>
class AlignedBuffer;

Copy to clipboard

`AlignedBuffer` provides a uniform way to define aligned memory allocations for all data types. This is particularly useful in defining allocations within shared memory with guaranteed memory alignment needed for vectorized access. Note, constructors of the elements within AlignedBuffer<> are not called, and so the elements are initially in an undefined state.

Use `AlignedBuffer<>::data()` to obtain a pointer to the first element of the buffer.

**Example:** Guaranteed aligned shared memory allocation. Note, shared memory contents are uninitialized.

int const kN \= 32;
int const kAlignment \= 16;                  // alignment in bytes

// Define a shared memory allocation in device code
\_\_shared\_\_ AlignedBuffer<complex<half\_t\>, kN, kAlignment\> matrix\_tile;

complex<half\_t\> \*ptr \= matrix\_tile.data();  // ptr is guaranteed to have 128b (16 Byte) alignment

Copy to clipboard

Note, `AlignedBuffer<>` only guarantees that its internal memory allocation is aligned, obtained by `AlignedBuffer<>::data()`. There is no guarantee that the `AlignedBuffer<>` object itself satisfies alignment constraints or that its internal memory allocation is contiguous. Device code performing vectorized memory accesses should use the `AlignedArray<>` type.

**_Example_:** Vectorized memory access to shared memory allocations.

int const kN \= 1024;

\_\_shared\_\_ AlignedBuffer<half\_t, kN\> smem\_buffer;

AlignedArray<half\_t, 8\> \*ptr \= reinterpret\_cast<AlignedArray<half\_t, 8\> \*>(smem\_buffer.data());

AlignedArray<half\_t, 8\> x \= ptr\[threadIdx.x\];     // 128b shared memory load

Copy to clipboard

### Numeric Conversion[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#numeric-conversion "Link to this heading")

CUTLASS defines procedures for performing numeric conversion between data types in `cutlass/numeric_conversion.h`. Where possible, these target hardware acceleration on the target architecture and support multiple rounding modes.

#include "cutlass/numeric\_conversion.h"
#include "cutlass/numeric\_types.h"

NumericConverter<half\_t, float\>     convert\_f32\_to\_f16;
NumericConverter<tfloat32\_t, float\> convert\_f32\_to\_tf32;

half\_t     x \= convert\_f32\_to\_f16(3.14159f);
tfloat32\_t y \= convert\_f32\_to\_tf32(3.14159f);

Copy to clipboard

Recent GPU architectures such as NVIDIA Turing and Ampere combine numeric conversion with efficient packing into bit vectors. Consequently, CUTLASS defines conversion on both scalars and `Array<>` objects to implement the optimal code sequence on all architectures.

//
// Example: convert and pack 32b signed integers to a vector of packed signed 8-bit integers.
//
int const kN \= 16;
Array<int8\_t, kN\> destination;
Array<int,    kN\> source;

NumericConverter<descltype(destination), decltype(source)\> convert;

destination \= convert(source);

Copy to clipboard

### Coord[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#coord "Link to this heading")

template <
  int Rank,
  typename Index \= int
\>
class Coord;

Copy to clipboard

`Coord<Rank, class T = int>` is a container used explicitly for defining logical coordinates in tensors of known rank. Traditional vector operators are defined such as `+`, `-`, and scalar multiplication `*` to simplify the creation of vector-valued expressions on tensor coordinates.

**Example:** Vector operations on coordinates.

Coord<2\> compute\_offset(Coord<2\> const & base) {
  
  Coord<2\> stride \= make\_Coord(1, kM);

  return base + stride \* make\_Coord(threadIdx.x, threadIdx.y); 
}

Copy to clipboard

Instances of `Coord<>` are used throughout CUTLASS to compute indices into tensors. Frequently, the dimensions of tensors of known layouts may be given names such as “rows” or “columns”. To clarify the code, we have implemented several classes derived from `Coord<>` with accessors for each coordinate member.

Such classes include:

struct MatrixCoord : public Coord<2\> {
  Index & row();
  Index & column();
};

Copy to clipboard

and

struct Tensor4DCoord : public Coord<4\> {
  Index & n();
  Index & h();
  Index & w();
  Index & c();
};

Copy to clipboard

### PredicateVector[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#predicatevector "Link to this heading")

`PredicateVector<int Bits>` contains a statically sized array of hardware predicates packed into registers to enable efficient access within unrolled loops.

This container is optimized for sequential access through iterators, though these are only efficient when used within fully unrolled loops.

Moreover, instances of `PredicateVector<>` are not guaranteed to be updated until any non-const iterator objects have gone out of scope. This is because iterators are effectively caches that update the `PredicateVector<>` instance’s internal storage as a batch.

**Example:** Managing an array of predicates.

unsigned mask;
PredicateVector<kBits\> predicates;

// Nested scope to update predicates via an iterator
{
  auto pred\_it \= predicates.begin();

  CUTLASS\_PRAGMA\_UNROLL
  for (int bit \= 0; bit < kBits; ++bit, ++pred\_it) {
    bool guard \= (mask & (1u << bit));
    pred\_it.set(guard);
  }
}

// Efficient use of predicates to guard memory instructions
T \*ptr;
Array<T, kAccesses\> fragment;

auto pred\_it \= predicates.const\_begin();
for (int access \= 0; access < kAccesses; ++access, ++pred\_it) {
  if (\*pred\_it) {
    fragment\[access\] \= ptr\[access\];
  }
}

Copy to clipboard

Note: `PredicateVector<>` is not efficient when accessed via dynamic random access. If an array of bits is needed with dynamic random access (in contrast with access via _constexpr_ indices), then `Array<bin1_t, N>` should be used instead.

## Functional[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#functional "Link to this heading")

CUTLASS defines function objects corresponding to basic arithmetic operations modeled after C++ Standard Library’s `<functional>` header.

CUTLASS extends this by defining `multiply_add<T>` which computes `d = a * b + c`. The partial specialization `multiply_add<complex<T>>` computes complex-valued multiplication and addition using four real-valued multiply-add operations; these may correspond to native hardware instructions.

Example:

complex<float\> a;
complex<float\> b;
complex<float\> c;
complex<float\> d;

multiply\_add<complex<float\>> mad\_op;

d \= mad\_op(a, b, c);    // four single-precision multiply-add instructions

Copy to clipboard

CUTLASS defines partial specializations for type `Array<T, N>`, performing elementwise operations on each element. A further partial specialization for `Array<half_t, N>` targets may target native SIMD instructions for compute capability SM60 and beyond.

**Example:** Fused multiply-add of arrays of half-precision elements.

static int const kN \= 8;

Array<half\_t, kN\> a;
Array<half\_t, kN\> b;
Array<half\_t, kN\> c;
Array<half\_t, kN\> d;

multiply\_add<Array<half\_t, kN\>> mad\_op;

d \= mad\_op(a, b, c);   // efficient multiply-add for Array of half-precision elements

Copy to clipboard

## Numeric Conversion[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#id1 "Link to this heading")

Operators are define to convert between numeric types in `numeric_conversion.h`. Conversion operators are defined in terms of individual numeric elements and on arrays which enable the possibility of efficient hardware support on current and future NVIDIA GPUs.

**Example:** Converting between 32-b and 8-b integers.

# Programming Guidelines[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#programming-guidelines "Link to this heading")

## Hierarchical Organization[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#hierarchical-organization "Link to this heading")

The [CUTLASS 3.0 GEMM API](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/gemm_api_3x.html) document explains CUTLASS 3.0’s hierarchical organization, based conceptually on parallelization strategy. This differs from CUTLASS 2.x’s approach, which more closely mirrors the GPU hardware hierarchy of thread blocks, warps, and threads.

## Design Patterns[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#design-patterns "Link to this heading")

CUTLASS aims for the highest performance possible on NVIDIA GPUs. It also offers flexible components that can be assembled and customized to solve new problems related to deep learning and linear algebra. Given a tradeoff between simplicity and performance, CUTLASS chooses performance. Consequently, several design patterns are necessary to yield a composable structure while also satisfying these performance objectives.

### Templates[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#templates "Link to this heading")

CUDA C++ templates and modern generic programming techniques enable CUTLASS device code to span a large design space.

This design space includes:

-   Mixed precision arithmetic and data storage
-   Kernels specialized for layout and problem size
-   Support for kernel fusion

Moreover, templates provided a structured approach to collecting compile-time constants such as tile dimensions. These must be template arguments to target static array allocation and take advantage of loop unrolling, constant folding, and function inlining.

### Constant Memory[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#constant-memory "Link to this heading")

Several CUTLASS template classes exhibit a pattern in which problem-specific internal state is known at kernel launch time and remains invariant throughout the execution of a kernel. For example, tile iterators compute several offsets based on the strides of the input tensor that is added to an internal pointer when loading the elements of a tile. These are computed from the tensor stride and never updated; the per-thread internal state consists only of the internal global memory pointer.

CUTLASS can take advantage of this CUDA grid-invariant property by constructing the object in host code and passing a composed parameters structure to the kernel. This confers two benefits: (1.) invariant state is held in constant memory, and (2.) there is no overhead to compute the initial state by each thread.

The design pattern in CUTLASS is for classes with nontrivial constructors to define `struct Params` as an inner class which contains grid-invariant state. These should define a constructor and an `initialize()` method. The `Params` structure should also include a data member corresponding to each data member in the parent class, so these too can be properly constructed in host code. The parent class should define a constructor which accepts `Params const &` as its first argument.

### Composable Shared Memory[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#composable-shared-memory "Link to this heading")

Shared memory requires explicit effort by the programmer to allocate and de-allocate. CUTLASS follows the paradigm introduced by [CUB](https://nvlabs.github.io/cub/) to define composed structures for storing data intended to be held in shared memory. Any object requiring shared memory storage for itself or its data members should define a child structure called `SharedStorage`. This holds data needed by the class and also instantiates `SharedStorage` objects for each data member.

To be consistent, this pattern defines a convention in which classes define internal shared memory storage requirements. Classes should consider all SharedStorage structures to be opaque other than their own child class. When the lifetimes of child objects are known to be non-overlapping, `union`s may be used to alias multiple SharedStorage objects to the same shared memory region and reduce overall shared memory capacity. Developers should carefully note that C++ `union` rules require that they only access the most recently written (“active”) member of the `union`; this differs from C rules.

For host to device ABI compatibility, inheritance from a class is only permitted if the superclass is unique to the child class. This is most easily achieved by templating the parent class by the child class (CRTP).

### Loop Unrolling[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#loop-unrolling "Link to this heading")

CUTLASS requires tiles of data to be stored in registers for high-bandwidth access. Simultaneously, high-throughput math instructions must be issued concurrently with memory instructions to hide latency with relatively few concurrent threads. These objectives are achieved by unrolling loops whose iteration counts are known at compile time.

Consequently, most loops within the CUTLASS GEMM implementation are specified by constant values and template arguments. The CUDA compiler is able to unroll the loop bodies, map array elements to registers, and construct an efficient instruction schedule.

All loops expected to be unrolled should be annotated with `CUTLASS_PRAGMA_UNROLL` to explicitly direct the compiler to unroll them.

int const kN \= 8;
Array<float, kN\> x;                       // Array we would like to store in registers

CUTLASS\_PRAGMA\_UNROLL                     // Directs the CUDA compiler to unroll this loop.
for (int idx \= 0; idx < kN; ++idx) {      // Loop has constant number of iterations.

  x\[i\] \= float(idx);                      // Indirect access by induction variable results in
                                          // direct register access.
}

Copy to clipboard

## Style[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#style "Link to this heading")

### If you see an issue in code formatting, fix it[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#if-you-see-an-issue-in-code-formatting-fix-it "Link to this heading")

You are empowered to reformat code. Please, however, consider making reformatting changes separately from content-related changes.

### No automatic code formatting[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#no-automatic-code-formatting "Link to this heading")

Do not use any kind of automatic code formatting, like `clang-format`, on CUTLASS code.

### C++ style[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#c-style "Link to this heading")

#### CUTLASS is a C++ project[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#cutlass-is-a-c-project "Link to this heading")

CUTLASS is a C++ project. CUDA C++ is a C++ dialect. Therefore, we write using standard C++ idioms as much as possible. We aim for portability to as many compilers as possible, by writing host code in Standard C++ and device code in CUDA C++ that resembles Standard C++ as much as possible. This improves usability for the general community of C++ developers, and makes it easier for new staff to join the project.

#### Follow Standard C++ idioms where possible[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#follow-standard-c-idioms-where-possible "Link to this heading")

Regarding “standard C++ idioms,” CUTLASS source code follows the following guidelines, with deviations only because of compiler limitations or where performance absolutely requires it. “Performance requires it” implies measurement. Deviations should be limited in scope and we should always strive to eliminate them.

-   [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)
-   [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)

#### C is not a subset of C++[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#c-is-not-a-subset-of-c "Link to this heading")

C is not a subset of C++. Some valid C is not valid C++, and some valid “C-looking” C++ is not valid C. See e.g., the informative C++ Standard Committee (WG21) document [P2735R0](https://isocpp.org/files/papers/P2735R0.pdf), which explains ways in which the same code has different behavior in C vs. C++. In some cases, code that compiles in both C and C++, and is correct in C, has undefined behavior (can crash or worse) in C++. The “type.punning” section of P2735R0 specifically relates to unions.

#### Spacing and line length[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#spacing-and-line-length "Link to this heading")

-   Use spaces, not tabs.
-   Use 2 spaces to indent.
-   Use at most 100 characters per line.

(Right-align tensor shape layout comments at column 120. Please see below.) Lines longer than 100 characters typically wrap unfavorably when viewed in Github’s pretty printer.

#### Formatting function declarations and definitions[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#formatting-function-declarations-and-definitions "Link to this heading")

Short function headers can go on one line.

Do not insert a newline between the parenthesis that closes the function’s parameters and the curly bracket that opens the function’s body.

int short\_name(int x, int y) {
  return x + y;
}

Copy to clipboard

If the function name and its parameters are too long to fit on one line, break the line immediately after the opening parenthesis that starts the parameter list. Then, double-indent the parameters to distinguish them from the body of the function.

void indeed\_my\_fellowbeings\_this\_function\_name\_is\_unusually\_long(
    std::uint32\_t foo, // parameters are double-indented
    std::uint32\_t const\* bar,
    TypeA a,
    TypeB b,
    TypeC c) { // the ) and { go on the same line still
  auto d \= body\_of\_the\_function(a, b, c); // body is single-indented
  // ... more code ...
}

Copy to clipboard

For a constructor with a long parameter list, break the line after the parentheses, just as with other functions. Align the colon that starts the constructor’s initializer list flush with the comma on the next line.

As with functions, double-indent the parameters to distinguish them from the constructor body. Here is an example.

class YesTheCommunityAgreesThatTheNameOfThisClassIsIndeedExtremelyLong {
public:
  CUTLASS\_HOST\_DEVICE
  YesTheCommunityAgreesThatTheNameOfThisClassIsIndeedExtremelyLong(
      int this\_is\_the\_first\_parameter\_and\_its\_name\_is\_long,
      int this\_is\_the\_second\_parameter\_and\_its\_name\_is\_also\_long,
      int this\_is\_the\_third\_parameter\_and\_its\_name\_is\_long\_too)
  : x\_(this\_is\_the\_first\_parameter\_and\_its\_name\_is\_long)
  , y\_(this\_is\_the\_second\_parameter\_and\_its\_name\_is\_also\_long)
  , z\_(this\_is\_the\_third\_parameter\_and\_its\_name\_is\_long\_too) {
    // constructor body
    // more of the constructor body
  }

private:
  int x\_ \= 0;
  int y\_ \= 0;
  int z\_ \= 0;
};

Copy to clipboard

#### Formatting function calls[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#formatting-function-calls "Link to this heading")

When calling a function or function object with a long name, break the line right after the invoking open parenthesis. Here are some examples.

detail::very\_long\_function\_object\_name<TemplateArgument\>{}(
  params.long\_parameter\_name, some\_operator.another\_long\_function\_name());

detail::an\_even\_longer\_function\_object\_name<TemplateArgument1, TemplateArgument2\>{}(
  params.long\_parameter\_name, some\_operator.long\_member\_function\_name(),
  another\_operator.another\_long\_member\_function\_name(x, y, z));

Copy to clipboard

#### If-else brackets and spacing[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#if-else-brackets-and-spacing "Link to this heading")

-   Always use braces with conditionals such as `if`, even if the body is a single line.
-   Use a space after control flow keywords such as `if`, `for`, and `while`.
-   Use a space after the parenthesis closing a conditional such as `if`, and the curly bracket opening a scope.
-   Use a new line between the closing brace of an `if` branch, and the `else` keyword.

if (condition) { // space after if, and between ) and {
  // ... code ...
} // newline after }
else {
  // ... other code ...
}

// space after keyword for
for (int k \= 0; k < num\_iters; ++k) {
  // ... still more code ...
}

Copy to clipboard

#### East const[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#east-const "Link to this heading")

CUTLASS uses the [“East const”](http://slashslash.info/2018/02/a-foolish-consistency/) convention. That is, the `const` or `constexpr` keyword goes after the type, not before. The general rule is that `const` or `constexpr` modifies the type to the left of it. Here are some examples.

float constexpr compile\_time\_constant \= 42.3f;

float const const\_float \= /\* whatever \*/;
float const& reference\_to\_const\_float \= const\_float;
float const\* pointer\_to\_const\_float \= &const\_float;
float const\* const const\_pointer\_to\_const\_float \= &const\_float;

float nonconst\_float;
float& reference\_to\_nonconst\_float \= nonconst\_float;
float\* pointer\_to\_nonconst\_float \= &nonconst\_float;
float\* const pointer\_to\_nonconst\_float \= &nonconst\_float;

Copy to clipboard

Contrast this with “West const” style, e.g.,

const float const\_float \= /\* whatever \*/;
const float\* pointer\_to\_const\_float \= &const\_float;

Copy to clipboard

#### Alignment of reference and pointer types[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#alignment-of-reference-and-pointer-types "Link to this heading")

For reference and pointer types, align the `&` resp. `*` flush against the type that it modifies. This is called “left alignment.”

For example, do this:

int const& var;
int const\* var;

Copy to clipboard

and not this.

int const &var;
int const \*var;

Copy to clipboard

#### Avoid calling functions “fast” or “optimized”[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#avoid-calling-functions-fast-or-optimized "Link to this heading")

Putting words like “fast” or “optimized” in the name of a function assumes that the “fast” path is actually faster. That might be true now, but later changes (in the code, compilers, or GPU hardware) might make it false. In that case, your name could be unintentionally misleading. Consider instead a name that briefly describes the algorithm or feature that is relevant for optimization. For example, `compute_on_host` is more meaningful than `compute_slowly`, and computing on host might be faster in some cases (e.g., if the data are already on host and the algorithm is not GPU-friendly).

CUTLASS code has not always followed this rule in the past. Some functions and classes might have words like “fast” in their name. New code should follow this rule, however.

#### Avoid creating unconstrained templated functions with common names[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#avoid-creating-unconstrained-templated-functions-with-common-names "Link to this heading")

See [C++ Core Guidelines T.47](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#t47-avoid-highly-visible-unconstrained-templates-with-common-names): “Avoid highly visible unconstrained templates with common names.” Argument-dependent lookup (ADL) means that if users call a function name without specifying the namespace, the compiler can find overloads of that function in any namespace. This can lead to ambiguous overloads in users’ code, just because they happened to include one of your header files that exposes an unconstrained function template. The following illustrates this with an unconstrained swap overload in the `cutlass` namespace.

#include <cassert>
#include <memory>
#include <utility>

// Uncomment the line below to observe unwarranted build errors.
//#define BAD\_CUTLASS\_SWAP 1

namespace cutlass {
struct Bar {
  float f;
};
} // namespace cutlass

#ifdef BAD\_CUTLASS\_SWAP
namespace cutlass {

// don't do this
template<class T\>
void swap(T& a, T& b) {
  T tmp \= a;
  a \= b;
  b \= tmp;
}

} // namespace cutlass
#endif // BAD\_CUTLASS\_SWAP

namespace other {

#ifdef BAD\_CUTLASS\_SWAP
using cutlass::swap;
#endif // BAD\_CUTLASS\_SWAP

// Imagine for the sake of this example
// that "foo" is a less common name,
// and that T is constrained via
// std::enable\_if or a requires clause.
template<class T\>
void foo(T& a, T& b) {
  // The usual idiom for using std::swap is the "swap two-step":
  //
  // 1. import std::swap into the current scope, then
  // 2. call swap without namespace qualification.
  //
  // That won't build if we have another swap
  // overload available in the scope already.

  using std::swap;
  swap(a, b); // OBSERVE UNWARRANTED BUILD ERROR HERE
}

} // namespace other

int main() {
  int x \= 42;
  int y \= 43;
  other::foo(x, y);
  assert(x \== 43);
  assert(y \== 42);

  cutlass::Bar a{42.0};
  cutlass::Bar b{43.0};
  other::foo(a, b);
  assert(a.f \== 43.0);
  assert(b.f \== 42.0);

  // GCC 7.5 std::unique\_ptr::reset calls swap,
  // leading to the same issue as above.
  // GCC 12.2's implementation of std::unique\_ptr
  // does not have this issue.  Nevertheless,
  // breaking the swap two-step will break users' code,
  // just by them happening to include your headers.
  auto ptr \= std::make\_unique<cutlass::Bar\>(cutlass::Bar{666.0f});
  ptr.reset(new cutlass::Bar{777.0f}); // OBSERVE UNWARRANTED BUILD ERROR HERE

  return 0;
}

Copy to clipboard

#### Function return values and in-out parameters[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#function-return-values-and-in-out-parameters "Link to this heading")

##### Prefer return values to output parameters[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#prefer-return-values-to-output-parameters "Link to this heading")

In general, avoid in-out mutable references to return a value. If you need to return multiple values, you can return them by `struct` or `tuple`, rather than by output references. This includes the special case of error reporting by returning either a value or an error code. Please see the next section for details.

// Instead of passing in-out mutable references ...
void not\_preferred(float& input\_and\_output); // not preferred

// keep functions pure and return value types instead
float preferred(float input); // preferred

Copy to clipboard

##### Return multiple values by struct or tuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#return-multiple-values-by-struct-or-tuple "Link to this heading")

Sometimes a function needs to return multiple values. In that case, consider the following, in decreasing order of preference.

1.  Return a `struct`. This lets you name the fields (for more self-documenting code), yet still permits use of structured binding.
2.  Return a `tuple`. If you need a tuple type that works on device, use `cute::tuple`. (Please note that `cute::tuple` does not work for all the types that work in `std::tuple`. CuTe’s documentation explains.)
3.  Resort to “returning” multiple values by output references only if performance requires it.

Here is an example of the struct approach for named values. For a comparable example in the C++ Standard, please see [`std::allocate_at_least`](https://en.cppreference.com/w/cpp/memory/allocate_at_least), which returns `std::allocation_result`.

struct my\_computation\_result {
  float value \= 0.0f;
  float relative\_error \= 0.0f;
  bool success \= false;
};

my\_computation\_result my\_computation(float tolerance);

void foo(float tolerance) {
  // Approach 1: Use structured binding.  The names
  // you choose on the left-hand side have nothing
  // to do with the struct, so it's up to you
  // to get the order right.  On the other hand,
  // this code works whether my\_computation returns
  // a struct or a tuple.
  auto \[val, rel\_err, ok\] \= my\_computation(tolerance);

  // Approach 2: Keep the struct and use its named fields.
  // This approach prevents errors like mixing the order of return types.
  // However, it only works for structs, not for tuples.

  auto result \= my\_computation(tolerance);
  if (not result.success) {
    // computation did not succeed
  }
  else if (result.relative\_error \> tolerance) {
    // successful but relative error too large
  }
  else {
    // successful and relative error is in bounds
  }
}

Copy to clipboard

##### Reporting errors from a function that returns one or more values[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#reporting-errors-from-a-function-that-returns-one-or-more-values "Link to this heading")

We may want to return one or more values from a function that could fail or otherwise report errors. That is, the function either

-   returns one or more valid values, or
-   does not return any values and reports an error,

but NOT BOTH. We contrast this with cases when it’s meaningful to report both a result and whether the result is satisfactory. For example, when solving a system of nonlinear equations iteratively, users may want the approximate computed solution, even if the iteration did not succeed by converging to the desired tolerance in the desired number of steps. (Users may want to invest more steps, or use the current approximation to jump-start a different algorithm.)

We’re talking here about the “either valid value(s), or error, but not both” case. For this case, C++ offers a few options.

1.  Return the value(s), or throw an exception on error
2.  `std::expected` (requiring C++23) or something like it
3.  `std::optional` (for a Boolean error state) or something like it
4.  `std::variant` (a C++17 fall-back for `std::expected`) or something like it
5.  C-style interface: return an error code, and “return” the values as output parameters

We usually cannot or do not want to throw exceptions on device. Some code projects forbid exceptions entirely (on host or device) and tell the compiler to disable them. If we exclude a C-style interface (the last option) as not idiomatic C++, then for host-only code, `std::expected`, `std::optional`, and `std::variant` all work. For code that needs to build and run on device, we can fall back to libcu++ equivalents in the `cuda::std::` namespace, when they exist. Otherwise, we must resort to returning a struct or tuple with the value and the error information, and ask users not to use the value on error. This is acceptable if the value can be constructed cheaply with a reasonable default.

##### Performance of different value-or-error reporting methods[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#performance-of-different-value-or-error-reporting-methods "Link to this heading")

[P1886R0](https://wg21.link/P1886R0) (Ben Craig, “Error speed benchmarking”) surveys different ways in Standard C++ to report errors from a function that returns one or more values, and compares their (host-only) performance with different compilers.

##### Use aggregate initialization when returning a struct or tuple[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#use-aggregate-initialization-when-returning-a-struct-or-tuple "Link to this heading")

Use aggregate initialization when returning a struct or tuple. This avoids duplication of the return type name.

struct foo\_result {
  float value \= 0.0f;
  float error \= 0.0f;
  bool success \= false;
};

foo\_result foo(std::span<const float\> input) {
  // ... code  ...

  // Prefer this.  We know what type the function returns.
  return {val, err, ok}; // prefer this

  // Naming foo\_result again here is unnecessary.
  // return foo\_result{val, err, ok};
}

Copy to clipboard

However, note that this won’t work if the function returns `auto`. The general rule is to avoid code duplication.

auto foo(std::span<const float\> input) {
  // ... code  ...

  if constexpr (some\_condition) {
    return foo\_result{val, err, ok};
  }
  else {
    return bar\_result{val, err, ok};
  }
}

Copy to clipboard

##### Prefer using the actual return type to auto, if you know the type[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#prefer-using-the-actual-return-type-to-auto-if-you-know-the-type "Link to this heading")

C++ lets you use `auto` to deduce the type returned from a function.

-   If you know the actual type, prefer using the type instead of `auto`.
-   Use [Constructor Type Argument Deduction](https://en.cppreference.com/w/cpp/language/class_template_argument_deduction) (CTAD) if you know that a function returns some type (e.g., `Tensor`), but don’t know the type’s template arguments.
-   Use `auto` in structured bindings (where you have to use it anyway). This also makes your code agnostic of whether the return type is a `struct`, `tuple`, `pair`, or other tuple-like type.
-   Be careful using `auto` with types that provide expression templates.

Contrast this with “Almost Always Auto” (AAA) style. We deliberately choose not to follow AAA style, for the following reasons.

-   Using the actual type when we know it can help prevent common loss-of-precision errors in mixed-precision computations, an important use case for CUTLASS.
-   CTAD gives us much of the brevity of AAA, with more clarity.
-   Using the actual type instead of `auto` can prevent common dangling errors with expression templates.

#### Classes and structs[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#classes-and-structs "Link to this heading")

Type names use `CamelCase`. That is, words start with capital letters. The remaining letters in the word are lower case, and words are joined with no intervening underscores. The only exception is when implementations are a drop-in replacement for C++ Standard Library components.

Follow the [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rc-struct) to decide whether to use `class` or `struct`.

-   Use `class` when the object must maintain an invariant. Data members related to the invariant should be `private`.
-   Use `struct` when the class has no invariant to maintain, and data members may vary arbitrarily with respect to each other.

Prefer nonmember functions and statelessness where possible. Member functions imply invariants. More invariants make code maintenance and testing harder.

#### Class members[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#class-members "Link to this heading")

Methods and members are written using `snake_case`.

Private data and function members have suffix `_`.

#### Class Member Order[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#class-member-order "Link to this heading")

Members within classes and structures should be organized as follows:

1.  Type and constant definitions
2.  Data members
3.  Constructors
4.  Other methods

This convention follows the [CUB library](https://nvlabs.github.io/cub/) and is also described by [Howard Hinnant](https://howardhinnant.github.io/classdecl.html). It also approximates the usual ordering of chapters in a typical Systems and Controls textbook. That is, it

1.  identifies relevant constants,
2.  defines a state-space representation of the dynamical system under study (the class’s data members), and then
3.  devotes the remaining “chapters” to defining the system’s dynamical behavior (the class’s methods).

Here is an example class.

class A {
public:
  // type definitions
protected:
  // protected type definitions
private:
  // private type definitions

public:
  // data members
protected:
  // protected data members
  // STRONGLY TO BE AVOIDED;
  // please see C++ Core Guidelines
private:
  // private data members

public:
  // methods
protected:
  // protected methods
private:
  // private methods
};

Copy to clipboard

#### For code reuse, prefer composition over inheritance[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#for-code-reuse-prefer-composition-over-inheritance "Link to this heading")

-   [C++ Core Guidelines C.129](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c129-when-designing-a-class-hierarchy-distinguish-between-implementation-inheritance-and-interface-inheritance): “When designing a class hierarchy, distinguish between implementation inheritance and interface inheritance”
-   [C++ Core Guidelines ES.63](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Res-slice): “Don’t slice”

Suppose that a class hierarchy exists entirely for implementation convenience, so that implementers can reuse code and “program by difference” (changing or adding only what’s different from the base class). In the example below, both `PipelineA` and `PipelineB` are used by themselves. `PipelineB` inherits from `PipelineA` just to avoid duplicating code. There are no virtual member functions, and users don’t expect to rely on run-time polymorphism.

class PipelineA {
public:
  PipelineA(Arg0 arg0, Arg1 arg1)
    : arg0\_(arg0), arg1\_(arg1)
  {}

  void producer\_acquire(uint32\_t stage, uint32\_t phase, uint32\_t skip\_wait) {
    // ... implementation ... 
  }

  void consumer\_release(uint32\_t stage, uint32\_t skip) {
    // ... implementation ...
  }

private:
  Arg0 arg0\_;
  Arg1 arg1\_;
};

class PipelineB : public PipelineA {
public:
  PipelineB(Arg0 arg0, Arg1 arg1, Arg2 arg2) :
    PipelineA(arg0, arg1), arg2\_(arg2)
  {}

  // Reuse PipelineA::producer\_acquire via inheritance

  // Override PipelineA::consumer\_release
  void consumer\_release(uint32\_t stage, uint32\_t skip) {
    // ... some other implementation, not invoking parent ...
  }

private:
  Arg2 arg2\_;
};

Copy to clipboard

The problem with public inheritance here is that `PipelineB` is NOT a (versus “is-a,” i.e., substitutable-as) `PipelineA`. In particular, the following code would be incorrect.

void consume\_and\_release\_pipeline(PipelineA\* parent) {
  // ... code ...
  parent\->consumer\_release(stage, skip);
  // ... code ...
}

void use\_pipeline( /\* other args \*/ ) {
  // ... code ...
  PipelineB child{arg0, arg1, arg2};
  // ... code ...

  // WRONG!!! SLICES CHILD TO PARENT!!!
  consume\_and\_release\_pipeline(&child); // BAD

  // ... code ...
}

Copy to clipboard

`PipelineA::consumer_release` is not a virtual member function, so `consume_and_release_pipeline` would not actually be polymorphic, as callers might have expected from an interface that takes a base class pointer. What’s worse is that the resulting slicing could violate `PipelineB`’s invariants, thus putting it in an incorrect state.

The most straightforward way to reuse code would be by changing from inheritance (is-a) to composition (has-a).

namespace detail {

// Implementation class; not for users
class PipelineImpl {
public:
  PipelineImpl(Arg0 arg0, Arg1 arg1)
    : arg0\_(arg0), arg1\_(arg1)
  {}

  void producer\_acquire(uint32\_t stage, uint32\_t phase, uint32\_t skip\_wait) {
    // ... implementation ...
  }

  void consumer\_release(uint32\_t stage, uint32\_t skip) {
    // ... implementation ...
  }

private:
  Arg0 arg0\_;
  Arg1 arg1\_;
};

} // namespace detail

class PipelineA {
public:
  PipelineA(Arg0 arg0, Arg1 arg1) :
    impl\_(arg0, arg1)
  {}

  void producer\_acquire(uint32\_t stage, uint32\_t phase, uint32\_t skip\_wait) {
    impl\_.producer\_acquire(stage, phase, skip\_wait);
  }

  void consumer\_release(uint32\_t stage, uint32\_t skip) {
    impl\_.consumer\_release(stage, skip);
  }

private:
  detail::PipelineImpl impl\_;
};

// A second kind of pipeline.
// Note that this does NOT inherit from PipelineB!
// The two pipeline classes have the same compile-time interface
// (for compile-time polymorphism), but do not belong in an 
// inheritance hierarchy (as would imply run-time polymorphism).
class PipelineB {
public:
  PipelineB(Arg0 arg0, Arg1 arg1, Arg2 arg2) :
    impl\_(arg0, arg1), otherTwo\_(arg2)
  {}

  void producer\_acquire(uint32\_t stage, uint32\_t phase, uint32\_t skip\_wait) {
    impl\_.producer\_acquire(stage, phase, skip\_wait);
  }

  void consumer\_release(uint32\_t stage, uint32\_t skip) {
    // this class doesn't actually use impl\_ here
    otherTwo\_.other\_action(stage, skip);
    // ... some other code not using impl\_ ...
  }

private:
  detail::PipelineImpl impl\_;
  OtherTwo otherTwo\_;
  // ... other member data ...
};

Copy to clipboard

This design prevents users at compile time from incorrectly assuming that `PipelineB` is a `PipelineA`. Implementers continue to get compile-time polymorphism, as long as `PipelineA` and `PipelineB` implement the same compile-time interface.

##### Behavioral subtyping[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#behavioral-subtyping "Link to this heading")

Another reason to avoid public inheritance would be if the public member functions of `PipelineA` and `PipelineB` have different behavior, such that the invariants satisfied by the member functions of the base class `PipelineA` are not satisfied by the correspondingly named member functions of the subclass `PipelineB`. For example, suppose that both classes have a public `producer_arrive` member function. However, for `PipelineA`, this issues a producer arrival only for its own block, whereas for `PipelineB`, this issues a producer arrival for all blocks in the cluster. Again, PipelineB “is-not-a” PipelineA. The child class doesn’t just add behavior onto the parent class; it has completely different behavior. Thus, it fails to satisfy behavioral subtyping: invariants of the parent class’s member functions are not satisfied by the child class. Behavioral subtyping is especially important when reasoning about already difficult things like parallel synchronization. The inheritance design would give developers the false impression that `PipelineB` just adds behavior atop `PipelineA`, whereas in fact, developers would need to understand both pipeline classes completely to build a correct mental model about their behavior.

The fix is the same: Use composition, not inheritance. As [C++ Core Guidelines C.120](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c120-use-class-hierarchies-to-represent-concepts-with-inherent-hierarchical-structure-only) explains: “Use class hierarchies to represent concepts with inherent hierarchical structure (only).”

1.  “Make sure the idea represented in the base class exactly matches all derived types and there is not a better way to express it than using the tight coupling of inheritance.”
2.  “Do not use inheritance when simply having a data member will do.”

#### Use scoped enums[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#use-scoped-enums "Link to this heading")

Use scoped enums (a C++11 feature) for enumerated types. Use capital letters for the enumerated type name and prefix `k` for enumerators like other constants.

enum class MatrixOperation {
  kNone,
  kTranspose,
  kConjugate,
  kHermitian
};

Copy to clipboard

#### Namespaces[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#namespaces "Link to this heading")

Namespaces are all lower case. The top-level namespace is `cutlass::`. The second nested namespace refers to the general category of operation performed by its members: e.g., `gemm::`. The third nested namespace refers to the operations’ position in the conceptual hierarchy: e.g., `device::`, `kernel::`, or `collective::`.

The bodies of namespace definitions should not be indented. Comments on the closing brace to indicate the namespace being closed are welcome.

namespace cutlass {
namespace gemm {
namespace kernel {

struct AnotherGemmKernel {
  // ... contents ...
};

} // namespace kernel
} // namespace gemm
} // namespace cutlass

Copy to clipboard

#### File Names[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#file-names "Link to this heading")

New files should be named using `snake_case` with extension `.hpp` for header files, `.cu` for CUDA sources, and `.cpp` for C++ host-only source files.

Header files with extension `.h` are CUTLASS 2.x legacy headers.

#### Macros[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#macros "Link to this heading")

Only use macros when the preprocessor is the only way to accomplish the task. Do not use macros for literal constants. Instead, if inside the body of a function, use `constexpr` values, and if at namespace scope, use [`inline constexpr` variables](https://en.cppreference.com/w/cpp/language/inline) (a C++17 feature).

“Namespace” macros by starting them with the module name, e.g., `CUTLASS_`. Macros and ONLY MACROS use all capital letters with underscores between words. For example:

#define CUTLASS\_MACROS\_USE\_ALL\_CAPS inline \_\_host\_\_ \_\_device\_\_

Copy to clipboard

Header files such as [cutlass/cutlass.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/cutlass.h) and [cute/config.hpp](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/cutlass.h) offer macros for expressing compiler-dependent behavior. These include

-   replacements for `__device__` and/or `__host__` annotations:
    
    -   `CUTLASS_HOST_DEVICE` or `CUTE_HOST_DEVICE` for functions that run on the host and the device,
    -   `CUTLASS_DEVICE` or `CUTE_DEVICE` for functions that run on the device only,
    -   `CUTE_HOST` for functions that run on the host only, and
    -   `CUTE_HOST_RTC` for functions that run on the host only, but occur as unevaluated operands (of e.g., `decltype` or `sizeof`; see C++ Standard, `[expr.context]` 1) in device code; and
-   annotations to loop unrolling:
    
    -   `CUTLASS_PRAGMA_UNROLL` or `CUTE_UNROLL` for full unrolling of loops with constant trip counts, and
    -   `CUTLASS_PRAGMA_NO_UNROLL` or `CUTE_NO_UNROLL` to prevent unrolling.

#### Guard all headers with `#pragma once`[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#guard-all-headers-with-pragma-once "Link to this heading")

Use `#pragma once` to guard all headers.

### CuTe Layout Comments[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#cute-layout-comments "Link to this heading")

-   Right-align tensor shape layout comments at column 120.
-   If layout comment is too long do your best to align it.
-   If layout comment is too long and there are many related tensors that the reader should read together, try to align the layout comments of related tensors.

Here are a couple examples.

Tensor mC \= make\_tensor(make\_gmem\_ptr(params.ptr\_C), make\_shape(M,N), params.dC);                              // (M,N)
Tensor mD \= make\_tensor(make\_gmem\_ptr(params.ptr\_D), make\_shape(M,N), params.dD);                              // (M,N)
Tensor mAux \= make\_tensor(make\_gmem\_ptr(params.ptr\_Aux), make\_shape(M,N), params.dAux);                        // (M,N)

auto thr\_mma \= tiled\_mma.get\_thread\_slice(thread\_idx);
Tensor tCgD \= thr\_mma.partition\_C(gD);                                                             // (VEC,THR\_M,THR\_N)
Tensor tCgC \= thr\_mma.partition\_C(gC);                                                             // (VEC,THR\_M,THR\_N)
Tensor tCgAux \= thr\_mma.partition\_C(gAux);                                                         // (VEC,THR\_M,THR\_N)

Copy to clipboard

Tensor my\_tensor \= make\_tensor<Type\>(Layout<Shape<\_2,\_2\>{}, Stride<\_1,\_2\>>{});                           // (2,2):(1,2)
    
// Related tensors
Tensor my\_tensor1 \= make\_tensor<Type\>(ThisIsAVeryComplicatedLayoutWithAVeryLongName);         // ((Mode0\_0,Mode0\_1,Mode0\_2),Mode1,Mode2,Mode3)
Tensor my\_tensor2\_related \= make\_tensor<Type\>(ThisIsAVeryComplicatedLayoutWithAVeryLongName); // ((Mode0\_0,Mode0\_1,Mode0\_2),Mode1,Mode2,Mode3)

Copy to clipboard

### Warnings[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#warnings "Link to this heading")

CUTLASS code aims to build free of warnings.

#### Spurious warnings[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#spurious-warnings "Link to this heading")

Some compilers, or some versions of a compiler, emit spurious warnings, that is, “false positives” for perfectly fine code. While such code is correct, the warnings can obscure errors. Users also may report warnings as bugs, and processing those bugs takes developer time away from other tasks. Thus, it’s good to try to “fix” the warnings, if doing so wouldn’t make the code worse.

#### Missing return statement[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#missing-return-statement "Link to this heading")

GCC 10 (but not 7.5, 9.4.0, or 11) has trouble deducing that a function with `auto` return type and all of its returns in an `if constexpr` … `else` statement must actually return. As a result, GCC emits spurious “missing return statement” build warnings. Such functions have one of two forms: `if constexpr` … `else` where `else` returns, and `if constexpr` … `else` where `else` is meant to fail at compile time. Here is an example of the first form.

template<class T\>
constexpr auto first\_form(T t) {
  if constexpr (some\_condition\_v<T\>) {
    return some\_function(t);
  }
  else if constexpr (another\_condition\_v<T\>) {
    return another\_function(t);
  }
  else {
    return yet\_another\_function(t);
  }
}

Copy to clipboard

In this form, the `if constexpr` … `else` sequence of branches covers all possibilities. Here is an example of the second form.

template<class T\>
constexpr auto second\_form(T t) {
  if constexpr (some\_condition\_v<T\>) {
    return some\_function(t);
  }
  else if constexpr (another\_condition\_v<T\>) {
    return another\_function(t);
  }
  else {
    static\_assert(sizeof(T) < 0, "This branch always fails");
  }
}

Copy to clipboard

In this form, the `else` branch had a `static_assert` that was meant always to fail if the `else` branch were taken, such as `static_assert(sizeof(T) < 0)`. (Note that we cannot use `static_assert(false)` here, because it will ALWAYS fail at compile time, even if the `else` branch is not taken. C++23 fixes this behavior, but CUTLASS currently requires that its code be compatible with C++17. As a result, CUTLASS includes a `dependent_false<T>` library function that you can use in place of the always-`false` test `sizeof(T) < 0`.)

One can suppress “missing return statement” warnings for both forms by invoking CUTLASS’ function-like macro `CUTE_GCC_UNREACHABLE`. When building with GCC, this invokes the GCC-specific built-in function `__builtin_unreachable()`. Actually calling this function is undefined behavior, so using this lets the programmer declare that the code path calling that function will never be taken. (C++23 introduces the `std::unreachable()` function, which achieves the same goal. Again, though, CUTLASS cannot currently use C++23 library functions.) Here is an example of how to use `CUTE_GCC_UNREACHABLE`.

template<class T\>
constexpr auto second\_form(T t) {
  if constexpr (some\_condition\_v<T\>) {
    return some\_function(t);
  }
  else if constexpr (another\_condition\_v<T\>) {
    return another\_function(t);
  }
  else {
    static\_assert(sizeof(T) < 0, "This branch always fails");
  }
  CUTE\_GCC\_UNREACHABLE;
}

Copy to clipboard

This macro should only be used if it is needed to suppress spurious warnings. Also, this function should not be used if the developer is not sure whether the code exhaustively tests all possibilities. For example, some functions may look like this.

template<class T\>
constexpr auto possibly\_nonexhaustive(T t) {
  if constexpr (some\_condition\_v<T\>) {
    return some\_function(t);
  }
  else if constexpr (another\_condition\_v<T\>) {
    return another\_function(t);
  }
 
  // NOTE lack of unadorned "else" here
}

Copy to clipboard

This is a good opportunity to review the function. If the branches are obviously meant to be exhaustive, you can add an `else` branch with a `static_assert` (see above for how to express this). If you’re not sure, leave it alone and let the compiler issue warnings.

#### Unused variable[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#unused-variable "Link to this heading")

Some compilers may emit spurious unused warnings for some variable declarations, where the variable was only being used inside a `decltype` in an `if constexpr` test. Marking the variables as `[[maybe_unused]]` (a standard C++17 attribute) suppresses these warnings. Again, please only do this if you’re sure that the code is right.

### CUDA C++ style[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#cuda-c-style "Link to this heading")

#### CUDA Built-in Variables[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#cuda-built-in-variables "Link to this heading")

Avoid direct access to CUDA built-in variables `threadIdx`, `blockIdx`, `blockDim`, and `gridDim` within CUTLASS components except in special circumstances.

Using built-in global variables directly within resuable components necessitates that all components use them consistently which may not be possible if CUTLASS components are used in other contexts.

Instead, components should accept a linear ID identifying threads, warps, and threadblocks from calling code. The top-level kernel may then decide how to map threads, warps, and blocks to the problem it is solving.

#### Use CUTLASS’s and CuTe’s fundamental types and operations[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#use-cutlass-s-and-cute-s-fundamental-types-and-operations "Link to this heading")

Use the [fundamental types and operations](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html) defined in CUTLASS consistently. This contributes to a framework of interoperable, consistent components. It reduces code duplication, which reduces build and test times. It also saves developer effort.

CUTLASS’s fundamental types and operations include

-   [Numeric types](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#numeric-types) to represent numeric data in host and device code, and
-   [functional.h](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#functional) to perform numeric operations in generic code.

CUTLASS 3.0 uses CuTe components to represent data layouts and multidimensional arrays. Please refer to the [CuTe Tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/00_quickstart.html) for details. CuTe has replaced CUTLASS 2.x components such as [Containers](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/fundamental_types.html#containers), [Layouts](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/layout.html), and [`TensorRef` and `TensorView`](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/layout.html#tensorref).

## CUTLASS idioms[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#cutlass-idioms "Link to this heading")

### Detecting major mode[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/programming_guidelines.html#detecting-major-mode "Link to this heading")

Developers sometimes need to detect whether a tensor is MN-major or K-major. (For definitions, see the [CuTe GEMM tutorial](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/cute/0x_gemm_tutorial.html).)

-   _Correct_: `cutlass::detail::is_major<0, Stride>()` or `cutlass::detail::is_k_major()` from `include/cutlass/gemm/gemm.h`
-   _Incorrect_: `get<0>(stride) == 1`

The second point is incorrect because it assumes that the mode is a single integer, not a multimode. This means that the code will fail to compile for tensor contractions. For example, suppose that a tensor A has shape `((X, Y), K)` and stride `((1, X), X*Y)`. `get<0>(stride)` is the tuple `(1, X)`, not a single integer. However, A is certainly M major if interpreted as a matrix.

# GEMM Heuristics[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#gemm-heuristics "Link to this heading")

## Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#overview "Link to this heading")

Gemm heuristics in `cutlass_library` aim to reduce the search space for runtime autotuning, so that only a subset of valid kernels need to be built and profiled for a given set of GEMM problems. This implementation uses Nvidia’s `nvidia-matmul-heuristics`, an analytical heuristic that ranks GEMM kernels by estimated performance given a problem size and hardware SKU. You can find more info in [the docs](https://docs.nvidia.com/cuda/nvidia-matmul-heuristics).

## Coverage[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#coverage "Link to this heading")

Gemm heuristics in `cutlass_library` is an experimental feature and exhaustive functional or performance coverage is not guaranteed. It currently supports the following.

Problem space:

-   Plain dense gemm for `f8`, `f16`, `f32`

Hardware:

-   Hopper (sm9x)
-   Blackwell (sm10x)

## Usage / Quick Start[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#usage-quick-start "Link to this heading")

### Install Dependencies[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#install-dependencies "Link to this heading")

Using the wheel is recommended:

pip install nvidia-matmul-heuristics

Copy to clipboard

### Prepare Input File[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#prepare-input-file "Link to this heading")

Prepare a list of gemm problem definitions, in the form of a json list, to be evaluated by the heuristic. Here is a sample file with two problems:

\[
{
     "m" : 4096,
     "n" : 4096,
     "k" : 4096,
     "batch\_count" : 1,
     "layout" : "tnn",
     "dtype\_a" : "f16",
     "dtype\_b" : "f16",
     "dtype\_c" : "f16",
     "dtype\_acc" : "f32",
     "dtype\_d" : "f16",
     "beta" : 0.0,
     "use\_fast\_acc": false
},
{
     "m" : 4096,
     "n" : 4096,
     "k" : 4096,
     "batch\_count" : 1,
     "layout": "tnn",
     "dtype\_a" : "e5m2",
     "dtype\_b" : "e5m2",
     "dtype\_c" : "f32",
     "dtype\_acc" : "f32",
     "dtype\_d" : "e5m2",
     "beta" : 0.0,
     "use\_fast\_acc": true
}
\]

Copy to clipboard

Note: `use_fast_acc` only needs to be specified for FP8 kernels on SM90. Otherwise, it is ignored.

### Build[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#build "Link to this heading")

Build CUTLASS using CMake as normal, providing heuristics-specific options to CMake. Note that hardware details are detected automatically. For offline builds, use `-DCUTLASS_LIBRARY_HEURISTICS_GPU`. For example, here is a minimal command for Nvidia’s Hopper Architecture (sm90):

$ cmake .. \\
    \-DCUTLASS\_NVCC\_ARCHS\=90a \\
    \-DCUTLASS\_LIBRARY\_HEURISTICS\_PROBLEMS\_FILE\=<path\_to\_your\_problem\_list.json> \\
    \-DCUTLASS\_LIBRARY\_HEURISTICS\_CONFIGS\_PER\_PROBLEM\=<number of configurations to build per problem> 
...
...

$ make cutlass\_profiler \-j

Copy to clipboard

This will produce a csv testlist which provides all testcases that need be run to perform autotuning over the built configurations, including kernel runtime options. The location of this file can be changed by the CMake option `-DCUTLASS_LIBRARY_HEURISTICS_TESTLIST_FILE`.

CUTLASS CMake currently supports the following for heuristics:

-   `CUTLASS_LIBRARY_HEURISTICS_PROBLEMS_FILE`: Path to the file containing a json list of GEMM problems
-   `CUTLASS_LIBRARY_HEURISTICS_CONFIGS_PER_PROBLEM`: Max number of configurations the heuristic will return for each GEMM problem. The same configuration or kernel can be suggested for multiple problems.
-   `CUTLASS_LIBRARY_HEURISTICS_RESTRICT_KERNELS`: Limits the build to only the set of kernels instantiated by the default CUTLASS CMake build flow, composing with other options such as `CUTLASS_LIBRARY_INSTANTIATION_LEVEL`. Set this to `ON` as a workaround if the heuristic suggests kernel configurations that do not build on your platform (possible for some unsupported or experimental use cases). This option is set to `OFF` by default, which builds all of the suggested configurations.
-   `CUTLASS_LIBRARY_HEURISTICS_TESTLIST_FILE`: Path to the output CSV which will contain the testcases to be used for autotuning, consumable by `cutlass_profiler`.
-   `CUTLASS_LIBRARY_HEURISTICS_GPU`: The GPU to use for heuristics; for instance, `H100_SXM5`. Used for offline builds. If unset, the hardware properties will be auto-detected using the Cuda Driver APIs. See `generator.py` for valid GPU strings

### Profile[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#profile "Link to this heading")

Use the emitted testlist CSV with `cutlass_profiler` to collect performance data, which can be used to determine the fastest built kernel configuration for each of the input problems. Example which profiles each testcase for a fixed 50ms:

cutlass\_profiler --operation=Gemm --testlist-file=<path\_to\_your\_testlist.csv> --profiling-iterations=0 --profiling-duration=50 --verification-enabled=false --output=<path\_to\_outfile>

Copy to clipboard

## Direct Usage in Python[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/heuristics.html#direct-usage-in-python "Link to this heading")

If you have pre-built CUTLASS kernels or custom CUTLASS emitters, you can use the Python APIs directly to select kernels to build or profile. See `filter_manifest_and_write_heuristics_file()` in `heuristics.py` for example usage.

