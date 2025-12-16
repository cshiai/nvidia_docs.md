# cuRAND

Note:
The new cuRAND Device Extensions ([cuRANDDx](https://docs.nvidia.com/cuda/curanddx/)) library is a device side API extension for generating random numbers inside CUDA kernels. By fusing random number generations with other numerical operations, you can achieve better performance for your application and lower latency.


 - You can access the cuRANDDx documentation here: [cuRANDDx documentation](https://docs.nvidia.com/cuda/curanddx/).
 - cuRANDDx is not a part of the CUDA Toolkit. cuRANDDx is a part of the MathDx package and can be downloaded from here: [cuRANDDx downloads](https://developer.nvidia.com/curanddx-downloads).

   Warning: The legacy cuRAND device API will be deprecated in a future release.
Note that in this section, all references to the "cuRAND device API" refer to the legacy cuRAND device API. cuRANDDx is not covered in this section.


To use the device API, include the file curand_kernel.h in files that define kernels that use cuRAND device functions. The device API includes functions [pseudorandom generation](device-api-overview.html#pseudorandom-sequences) for and [quasirandom generation](device-api-overview.html#quasirandom-sequences).