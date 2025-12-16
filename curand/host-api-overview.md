# cuRAND

To use the host API, user code should include the library header file curand.h and dynamically link against the cuRAND library. The library uses the CUDA runtime, thus when using the static cuRAND library user needs to link against CUDA Runtime too.


Random numbers are produced by generators. A generator in cuRAND encapsulates all the internal state necessary to produce a sequence of pseudorandom or quasirandom numbers. The normal sequence of operations is as follows:
1. Create a new generator of the desired type (see [Generator Types](host-api-overview.html#generator-types) ) with curandCreateGenerator().
2. Set the generator options (see [Generator Options](host-api-overview.html#generator-options)); for example, use curandSetPseudoRandomGeneratorSeed() to set the seed.
3. Allocate memory on the device with cudaMalloc().
4. Generate random numbers with curandGenerate() or another generation function.
5. Use the results.
6. If desired, generate more random numbers with more calls to curandGenerate().
7. Clean up with curandDestroyGenerator().


To generate random numbers on the host CPU, in step one above call curandCreateGeneratorHost(), and in step three, allocate a host memory buffer to receive the results. All other calls work identically whether you are generating random numbers on the device or on the host CPU.


It is legal to create several generators at the same time. Each generator encapsulates a separate state and is independent of all other generators. The sequence of numbers produced by each generator is deterministic. Given the same set-up parameters, the same sequence will be generated with every run of the program. Generating random numbers on the device will result in the same sequence as generating them on the host CPU.


Note that curandGenerate() in step 4 above launches a kernel and returns asynchronously. If you launch another kernel in a different stream, and that kernel needs to use the results of curandGenerate(), you must either call cudaDeviceSynchronize() or use the stream management/event management routines, to ensure that the random generation kernel has finished execution before the new kernel is launched.


Note that it is not valid to pass a host memory pointer to a generator that is running on the device, and it is not valid to pass a device memory pointer to a generator that is running on the CPU. Behavior in these cases is undefined.