# CUDA Runtime API

[< Previous](structcudaGraphInstantiateParams.html) | [Next >](structcudaGraphNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.34. cudaGraphKernelNodeUpdate Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Struct to specify a single node update to pass as part of a larger array to [cudaGraphKernelNodeUpdatesApply](group__CUDART__GRAPH.html#group__CUDART__GRAPH_1g2d558cf37c9616365c67447e61ac0d6a)


### Public Variables


enumcudaGraphKernelNodeField fielduint3  gridDimunsigned int  isEnabledcudaGraphDeviceNode_t nodesize_t  offsetconst
                           void
                           * pValuecudaGraphKernelNodeUpdate::@27::@28  paramsize_t  sizecudaGraphKernelNodeUpdate::@27  updateData

### Variables


enumcudaGraphKernelNodeFieldcudaGraphKernelNodeUpdate::field [inherited]
Which type of update to apply. Determines how updateData is interpreted

uint3  cudaGraphKernelNodeUpdate::gridDim [inherited]
Grid dimensions

unsigned int  cudaGraphKernelNodeUpdate::isEnabled [inherited]
Node enable/disable data. Nonzero if the node should be enabled, 0 if it should be disabled

cudaGraphDeviceNode_tcudaGraphKernelNodeUpdate::node [inherited]
Node to update

size_t  cudaGraphKernelNodeUpdate::offset [inherited]
Offset into the parameter buffer at which to apply the update

const

                              void
                              * cudaGraphKernelNodeUpdate::pValue [inherited]
Kernel parameter data to write in

cudaGraphKernelNodeUpdate::@27::@28  cudaGraphKernelNodeUpdate::param [inherited]
Kernel parameter data

size_t  cudaGraphKernelNodeUpdate::size [inherited]
Number of bytes to update

cudaGraphKernelNodeUpdate::@27  cudaGraphKernelNodeUpdate::updateData [inherited]
Update data to apply. Which field is used depends on field's value


---