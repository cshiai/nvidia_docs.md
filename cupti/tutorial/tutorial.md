# 5. Tutorial


This section provides detailed instructions on using various CUPTI APIs for tracing and profiling CUDA applications. You will learn how to utilize these APIs to gather performance metrics, analyze execution behavior, and optimize your CUDA applications effectively.


## 5.1. CUDA kernel tracing using Activity API


This tutorial provides a guide to profiling a simple CUDA kernel using the CUPTI Activity API. Starting with a basic vector addition kernel, it incrementally introduces CUPTI API calls to collect and display the kernel name and execution duration.


### 5.1.1. Simple Vector Addition in CUDA C


First, let’s write a vector addition kernel in CUDA C:


```
#include <cuda_runtime.h>
#include <stdio.h>

// CUDA kernel for vector addition
__global__ void VectorAdd(const float *A, const float *B, float *C, int N) {
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    if (idx < N)
        C[idx] = A[idx] + B[idx];
}

int main() {
    int vectorLen = 1024 * 1024;
    size_t size = vectorLen * sizeof(float);

    // Host memory allocation
    float *h_A = (float*)malloc(size);
    float *h_B = (float*)malloc(size);
    float *h_C = (float*)malloc(size);

    // Initialize vectors
    for (int i = 0; i < vectorLen; ++i) {
        h_A[i] = rand() / (float)RAND_MAX;
        h_B[i] = rand() / (float)RAND_MAX;
    }

    // Device memory allocation
    float *d_A, *d_B, *d_C;
    cudaMalloc((void )&d_A, size);
    cudaMalloc((void )&d_B, size);
    cudaMalloc((void )&d_C, size);

    cudaMemcpy(d_A, h_A, size, cudaMemcpyHostToDevice);
    cudaMemcpy(d_B, h_B, size, cudaMemcpyHostToDevice);

    int threadsPerBlock = 128;
    int blocksPerGrid = (vectorLen + threadsPerBlock - 1) / threadsPerBlock;

    // Launch the kernel
    VectorAdd<<<blocksPerGrid, threadsPerBlock>>>(d_A, d_B, d_C, vectorLen);
    cudaMemcpy(h_C, d_C, size, cudaMemcpyDeviceToHost);
    cudaDeviceSynchronize();

    cudaFree(d_A); cudaFree(d_B); cudaFree(d_C);
    free(h_A); free(h_B); free(h_C);

    return 0;
}
```


This code runs a vector addition on the GPU. At this point, no profiling information is being collected.


### 5.1.2. Step 1: Register CUPTI Callbacks


Next, include the CUPTI API, define callback functions for activity buffer requested and completed, then register them. This is normally done right after initialization and before launching the kernel.


```
#include <cupti.h>

// Callback for buffer requests
static void BufferRequested(uint8_t buffer, size_t* size, size_t* maxNumRecords) {
    *size = 8 * 1024 * 1024; // 8MB buffer
    *maxNumRecords = 0;
    *buffer = (uint8_t*)malloc(*size);
}

// Callback for buffer completed
static void BufferCompleted(CUcontext ctx, uint32_t streamId, uint8_t* buffer, size_t size, size_t validSize) {
    CUpti_Activity *record = NULL;

    if (validSize > 0)
    {
        // Parse CUPTI activity records here, print kernel name and duration
        while (cuptiActivityGetNextRecord(buffer, validSize, &record) == CUPTI_SUCCESS)
        {
            if (record->kind == CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL) {
                CUpti_ActivityKernel10 *kernel = (CUpti_ActivityKernel10 *)record;
                printf("kernel name = %s\n", kernel->name);
                printf("kernel duration (ns) = %llu\n", (unsigned long long)(kernel->end - kernel->start));
            }
        }
    }
    free(buffer);
}

cuptiActivityRegisterCallbacks(BufferRequested, BufferCompleted);
```


### 5.1.3. Step 2: Enable CUPTI Activity Collection


Then, enable kernel activity collection. Add the following line after registering the callbacks and before launching the kernel:


```
cuptiActivityEnable(CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL);
```


### 5.1.4. Step 3: Flushing and Disabling CUPTI Activity


After profiling is complete, flush any remaining activity records and disable CUPTI activity collection. Add these lines after the synchronization call:


```
cuptiActivityFlushAll(1);
cuptiActivityDisable(CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL);
```


Your final code should look like this:


```
#include <cuda_runtime.h>
#include <stdio.h>
#include <cupti.h>

// Callback for buffer requests
static void BufferRequested(uint8_t buffer, size_t* size, size_t* maxNumRecords) {
    *size = 8 * 1024 * 1024; // 8MB buffer
    *maxNumRecords = 0;
    *buffer = (uint8_t*)malloc(*size);
}

// Callback for buffer completed
static void BufferCompleted(CUcontext ctx, uint32_t streamId, uint8_t* buffer, size_t size, size_t validSize) {
    CUpti_Activity *record = NULL;

    if (validSize > 0)
    {
        // Parse CUPTI activity records here, print kernel name and duration
        while (cuptiActivityGetNextRecord(buffer, validSize, &record) == CUPTI_SUCCESS)
        {
            if (record->kind == CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL) {
                CUpti_ActivityKernel10 *kernel = (CUpti_ActivityKernel10 *)record;
                printf("kernel name = %s\n", kernel->name);
                printf("kernel duration (ns) = %llu\n", (unsigned long long)(kernel->end - kernel->start));
            }
        }
    }
    free(buffer);
}

// CUDA kernel for vector addition
__global__ void VectorAdd(const float *A, const float *B, float *C, int N) {
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    if (idx < N)
        C[idx] = A[idx] + B[idx];
}

int main() {
    int vectorLen = 1024 * 1024;
    size_t size = vectorLen * sizeof(float);

    // Step 1: Register CUPTI callbacks
    cuptiActivityRegisterCallbacks(BufferRequested, BufferCompleted);

    // Step 2: Enable CUPTI Activity Collection
    cuptiActivityEnable(CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL);

    // Host memory allocation
    float *h_A = (float*)malloc(size);
    float *h_B = (float*)malloc(size);
    float *h_C = (float*)malloc(size);

    // Initialize vectors
    for (int i = 0; i < vectorLen; ++i) {
        h_A[i] = rand() / (float)RAND_MAX;
        h_B[i] = rand() / (float)RAND_MAX;
    }

    // Device memory allocation
    float *d_A, *d_B, *d_C;
    cudaMalloc((void )&d_A, size);
    cudaMalloc((void )&d_B, size);
    cudaMalloc((void )&d_C, size);

    cudaMemcpy(d_A, h_A, size, cudaMemcpyHostToDevice);
    cudaMemcpy(d_B, h_B, size, cudaMemcpyHostToDevice);

    int threadsPerBlock = 128;
    int blocksPerGrid = (vectorLen + threadsPerBlock - 1) / threadsPerBlock;

    // Launch the kernel (profiler will capture this call)
    VectorAdd<<<blocksPerGrid, threadsPerBlock>>>(d_A, d_B, d_C, vectorLen);
    cudaMemcpy(h_C, d_C, size, cudaMemcpyDeviceToHost);
    cudaDeviceSynchronize();

    cudaFree(d_A); cudaFree(d_B); cudaFree(d_C);
    free(h_A); free(h_B); free(h_C);

    // Step 3: Flushing and Disabling CUPTI Activity
    cuptiActivityFlushAll(1);
    cuptiActivityDisable(CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL);

    return 0;
}
```


### 5.1.5. Expected Output


When the above code is run, output similar to the following should be seen:


```
kernel name = _Z10vector_addPKfS0_Pfi
kernel duration (ns) = <some number>
```


This indicates that CUPTI has successfully captured and reported the name of the CUDA kernel that was launched.


## 5.2. CUDA memcpy API tracing using CUPTI Callback API


This tutorial demonstrates how to collect information for CUDA memcpy API using the CUPTI Callback API. We start with a basic vector addition example and, step by step, add CUPTI calls to collect and display profiling information such as memcpy size and kind.


### 5.2.1. Simple Vector Addition in CUDA C


First, let’s write a vector addition kernel in CUDA C, as demonstrated in the section on [simple vector addition in CUDA C](tutorial.html#simple-vector-addition-in-cuda-c).


### 5.2.2. Step 1: Subscribe to CUPTI callbacks


Next, include the CUPTI API, define a callback function, and register it with CUPTI. This must be done early, before launching any kernels.


```
#include <cupti.h>

CUpti_SubscriberHandle subscriber;

// Subscribe to CUPTI callbacks.
cuptiSubscribe(&subscriber, (CUpti_CallbackFunc)CallbackHandler, NULL);
```


### 5.2.3. Step 2: Enable callback for specific domains and callback IDs


Once subscribed, enable callbacks for specific domains and callback IDs. For this example, we track the CUDA Runtime API cudaMemcpy.


```
void CUPTIAPI
CallbackHandler(void *userData, CUpti_CallbackDomain domain, CUpti_CallbackId callbackId, const CUpti_CallbackData *callbackData) {
    switch(domain)
    {
        case CUPTI_CB_DOMAIN_RUNTIME_API:
            if (callbackData->callbackSite == CUPTI_API_ENTER)
            {
                // access parameters passed to cudaMemcpy
                if (callbackId == CUPTI_RUNTIME_TRACE_CBID_cudaMemcpy_v3020)
                {
                    printf("Memcpy size = %zu\n", ((cudaMemcpy_v3020_params *)(callbackData->functionParams))->count);
                    printf("Memcpy kind = %d\n", ((cudaMemcpy_v3020_params *)(callbackData->functionParams))->kind);
                }
            }
            break;
        default:
            break;
    }
}

// Enable all CUDA Runtime API callbacks
// Callback will be invoked at the entry and exit points of each of the CUDA Runtime API.
cuptiEnableDomain(1, subscriber, CUPTI_CB_DOMAIN_RUNTIME_API);
```


### 5.2.4. Step 3: Disable Callbacks and Cleanup


After profiling, disable the domain and unsubscribe to release resources:


```
cuptiEnableDomain(0, subscriber, CUPTI_CB_DOMAIN_RUNTIME_API);
cuptiUnsubscribe(subscriber);
```


Your final code should look like this:


```
#include <cuda_runtime.h>
#include <stdio.h>
#include <cupti.h>

void CUPTIAPI
CallbackHandler(void *userData, CUpti_CallbackDomain domain, CUpti_CallbackId callbackId, const CUpti_CallbackData *callbackData) {
    switch(domain)
    {
        case CUPTI_CB_DOMAIN_RUNTIME_API:
            if (callbackData->callbackSite == CUPTI_API_ENTER)
            {
                // access parameters passed to cudaMemcpy
                if (callbackId == CUPTI_RUNTIME_TRACE_CBID_cudaMemcpy_v3020)
                {
                    printf("Memcpy size = %zu\n", ((cudaMemcpy_v3020_params *)(callbackData->functionParams))->count);
                    printf("Memcpy kind = %d\n", ((cudaMemcpy_v3020_params *)(callbackData->functionParams))->kind);
                }
            }
            break;
        default:
            break;
    }
}

// CUDA kernel for vector addition
__global__ void VectorAdd(const float *A, const float *B, float *C, int N) {
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    if (idx < N)
        C[idx] = A[idx] + B[idx];
}

int main() {
    int vectorLen = 1024 * 1024;
    size_t size = vectorLen * sizeof(float);

    // Step 1: Subscribe to CUPTI callbacks
    CUpti_SubscriberHandle subscriber;
    cuptiSubscribe(&subscriber, (CUpti_CallbackFunc)CallbackHandler, NULL);

    // Step 2: Enable callback for specific domains and callback IDs
    // Enable all callbacks for CUDA Runtime APIs.
    // Callback will be invoked at the entry and exit points of each of the CUDA Runtime API.
    cuptiEnableDomain(1, subscriber, CUPTI_CB_DOMAIN_RUNTIME_API);

    // Host memory allocation
    float *h_A = (float*)malloc(size);
    float *h_B = (float*)malloc(size);
    float *h_C = (float*)malloc(size);

    // Initialize vectors
    for (int i = 0; i < vectorLen; ++i) {
        h_A[i] = rand() / (float)RAND_MAX;
        h_B[i] = rand() / (float)RAND_MAX;
    }

    // Device memory allocation
    float *d_A, *d_B, *d_C;
    cudaMalloc((void )&d_A, size);
    cudaMalloc((void )&d_B, size);
    cudaMalloc((void )&d_C, size);

    cudaMemcpy(d_A, h_A, size, cudaMemcpyHostToDevice);
    cudaMemcpy(d_B, h_B, size, cudaMemcpyHostToDevice);

    int threadsPerBlock = 128;
    int blocksPerGrid = (vectorLen + threadsPerBlock - 1) / threadsPerBlock;

    // Launch the kernel (profiler will capture this call)
    VectorAdd<<<blocksPerGrid, threadsPerBlock>>>(d_A, d_B, d_C, vectorLen);
    cudaMemcpy(h_C, d_C, size, cudaMemcpyDeviceToHost);
    cudaDeviceSynchronize();

    cudaFree(d_A); cudaFree(d_B); cudaFree(d_C);
    free(h_A); free(h_B); free(h_C);

    // Step 3: Disable callback for domains and callback IDs
    cuptiEnableDomain(0, subscriber, CUPTI_CB_DOMAIN_RUNTIME_API);
    cuptiUnsubscribe(subscriber);

    return 0;
}
```


### 5.2.5. Expected Output


When the above code is run, output similar to the following should be seen:


```
Memcpy size = 4194304
Memcpy kind = 1
Memcpy size = 4194304
Memcpy kind = 1
Memcpy size = 4194304
Memcpy kind = 2
```


This confirms CUPTI successfully intercepted and reported cudaMemcpy calls.


## 5.3. Periodic metric sampling using PM Sampling API


This tutorial provides a guide to periodic collection of performance metrics from a CUDA kernel using the CUPTI PM Sampling API. Starting with a basic vector addition kernel, it incrementally introduces CUPTI PM Sampling API calls to collect hardware performance counters at regular intervals during kernel execution.


### 5.3.1. Simple Vector Addition in CUDA C


First, let’s write a vector addition kernel in CUDA C, as demonstrated in the section on [simple vector addition in CUDA C](tutorial.html#simple-vector-addition-in-cuda-c).


### 5.3.2. Step 1: Initialize CUDA and Include Headers


First, include the CUPTI PM Sampling headers and define global variables:


```
#include <cupti_target.h>
#include <cupti_pmsampling.h>
#include <cupti_profiler_target.h>
#include <cupti_profiler_host.h>

// Global variables for PM Sampling
CUpti_PmSampling_Object* g_pPmSamplingObject = NULL;

std::string g_chipName;
std::vector<uint8_t> g_configImage;
std::vector<uint8_t> g_counterDataImage;

std::vector<const char*> g_metrics =
{
    "gr__cycles_active.avg",      // GPU Active Cycles
    "gr__cycles_elapsed.max",     // GPU Elapsed Cycles
    "sm__cycles_active.avg"       // SM Active Cycles
};
```


### 5.3.3. Step 2: Initialize CUPTI Profiler and Enable PM Sampling


Initialize the CUPTI profiler, enable PM sampling on the device, and retrieve the chip name required for the configuration image.


```
// Helper function to initialize PM Sampling
void InitializeAndEnablePmSampling(int deviceIndex)
{
    // Initialize CUPTI Profiler
    CUpti_Profiler_Initialize_Params profilerInitializeParams = { CUpti_Profiler_Initialize_Params_STRUCT_SIZE };
    cuptiProfilerInitialize(&profilerInitializeParams);

    CUpti_Device_GetChipName_Params getChipNameParams = { CUpti_Device_GetChipName_Params_STRUCT_SIZE };
    getChipNameParams.deviceIndex = deviceIndex;
    cuptiDeviceGetChipName(&getChipNameParams);
    g_chipName = getChipNameParams.pChipName;
    printf("Chip Name: %s\n", g_chipName.c_str());

    // Enable PM sampling
    CUpti_PmSampling_Enable_Params enableParams = { CUpti_PmSampling_Enable_Params_STRUCT_SIZE };
    enableParams.deviceIndex = deviceIndex;
    cuptiPmSamplingEnable(&enableParams);
    g_pPmSamplingObject = enableParams.pPmSamplingObject;
}
```


### 5.3.4. Step 3: Create Config Image and Configure PM Sampling


Create the configuration image that encapsulates metric scheduling, then configure PM sampling parameters - buffer size, sampling interval etc.


```
void ConfigurePmSampling(uint64_t hardwareBufferSize, uint64_t samplingInterval)
{
    // Need to create the config image which will have the scheduling information for the metrics
    CreateConfigImage();

    // Set configuration
    CUpti_PmSampling_SetConfig_Params setConfigParams = { CUpti_PmSampling_SetConfig_Params_STRUCT_SIZE };
    setConfigParams.pPmSamplingObject = g_pPmSamplingObject;
    setConfigParams.configSize = configImage.size();
    setConfigParams.pConfig = configImage.data();
    setConfigParams.hardwareBufferSize = hardwareBufferSize;
    setConfigParams.samplingInterval = samplingInterval;
    setConfigParams.triggerMode = CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_SYSCLK_INTERVAL;
    cuptiPmSamplingSetConfig(&setConfigParams);
}
```


### 5.3.5. Step 4: Start and Stop PM Sampling before and after Launching Workload


Begin data collection and stop it after the workload is launched (refer to the complete example below for the usage of these helper functions):


```
// Helper function to start PM sampling
void StartPmSampling()
{
    CUpti_PmSampling_Start_Params startParams = { CUpti_PmSampling_Start_Params_STRUCT_SIZE };
    startParams.pPmSamplingObject = g_pPmSamplingObject;
    cuptiPmSamplingStart(&startParams);
}

// Helper function to stop PM sampling
void StopPmSampling()
{
    CUpti_PmSampling_Stop_Params stopParams = { CUpti_PmSampling_Stop_Params_STRUCT_SIZE };
    stopParams.pPmSamplingObject = g_pPmSamplingObject;
    cuptiPmSamplingStop(&stopParams);
}
```


### 5.3.6. Step 5: Create Counter Data Image and Decode Sampling Data


Create counter data image which will store the decoded data from the hardware buffer and then decode the sampling data and print first 10 samples:


```
// Helper function to create counter data image
void CreateCounterDataImage(uint64_t maxSamplesInCounterDataImage)
{
    CUpti_PmSampling_GetCounterDataSize_Params getCounterDataSizeParams = { CUpti_PmSampling_GetCounterDataSize_Params_STRUCT_SIZE };
    getCounterDataSizeParams.pPmSamplingObject = g_pPmSamplingObject;
    getCounterDataSizeParams.numMetrics = g_metrics.size();
    getCounterDataSizeParams.pMetricNames = g_metrics.data();
    getCounterDataSizeParams.maxSamples = maxSamplesInCounterDataImage;
    cuptiPmSamplingGetCounterDataSize(&getCounterDataSizeParams);

    g_counterDataImage.resize(getCounterDataSizeParams.counterDataSize);
    CUpti_PmSampling_CounterDataImage_Initialize_Params initializeParams = { CUpti_PmSampling_CounterDataImage_Initialize_Params_STRUCT_SIZE };
    initializeParams.pPmSamplingObject = g_pPmSamplingObject;
    initializeParams.counterDataSize = g_counterDataImage.size();
    initializeParams.pCounterData = g_counterDataImage.data();
    cuptiPmSamplingCounterDataImageInitialize(&initializeParams);
}

void DecodeAndPrintSamplingData()
{
    // Create counter data image which will store the decoded data from the hardware buffer
    constexpr uint64_t maxSamplesInCounterDataImage = 10000;
    CreateCounterDataImage(maxSamplesInCounterDataImage);

    // Decode sampling data
    CUpti_PmSampling_DecodeData_Params decodeParams = { CUpti_PmSampling_DecodeData_Params_STRUCT_SIZE };
    decodeParams.pPmSamplingObject = g_pPmSamplingObject;
    decodeParams.pCounterDataImage = g_counterDataImage.data();
    decodeParams.counterDataImageSize = g_counterDataImage.size();
    cuptiPmSamplingDecodeData(&decodeParams);

    // Get information about decoded data
    CUpti_PmSampling_GetCounterDataInfo_Params counterDataInfo = { CUpti_PmSampling_GetCounterDataInfo_Params_STRUCT_SIZE };
    counterDataInfo.pCounterDataImage = g_counterDataImage.data();
    counterDataInfo.counterDataImageSize = g_counterDataImage.size();
    cuptiPmSamplingGetCounterDataInfo(&counterDataInfo);
    printf("Number of completed samples: %zu\n", counterDataInfo.numCompletedSamples);

    // Print sample information (first 10 samples)
    size_t maxSamplesToShow = (counterDataInfo.numCompletedSamples > 10) ? 10 : counterDataInfo.numCompletedSamples;
    EvaluateAndPrintAllSamples(maxSamplesToShow);
}
```


### 5.3.7. Step 6: Cleanup PM Sampling


Disable PM Sampling and release all allocated resources:


```
void CleanupPmSampling()
{
    // Disable PM sampling
    CUpti_PmSampling_Disable_Params disableParams = { CUpti_PmSampling_Disable_Params_STRUCT_SIZE };
    disableParams.pPmSamplingObject = g_pPmSamplingObject;
    cuptiPmSamplingDisable(&disableParams);

    // Deinitialize profiler
    CUpti_Profiler_DeInitialize_Params profilerDeInitializeParams = { CUpti_Profiler_DeInitialize_Params_STRUCT_SIZE };
    cuptiProfilerDeInitialize(&profilerDeInitializeParams);
}
```


### 5.3.8. Complete Example


Your final code should look like this:


```
#include <cuda_runtime.h>
#include <cuda.h>
#include <stdio.h>
#include <vector>
#include <cupti_target.h>
#include <cupti_pmsampling.h>
#include <cupti_profiler_target.h>
#include <cupti_profiler_host.h>

// Global variables for PM Sampling
CUpti_PmSampling_Object* g_pPmSamplingObject = NULL;

std::string g_chipName;
std::vector<uint8_t> g_configImage;
std::vector<uint8_t> g_counterDataImage;

std::vector<const char*> g_metrics =
{
    "gr__cycles_active.avg",     // GPU Active Cycles
    "gr__cycles_elapsed.max",     // GPU Elapsed Cycles
    "sm__cycles_active.avg"     // SM Active Cycles
};

// CUDA kernel for vector addition
__global__ void VectorAdd(const int *A, const int *B, int *C, int N)
{
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    if (idx < N)
        C[idx] = A[idx] + B[idx];
}

// Helper function to initialize PM Sampling
void InitializeAndEnablePmSampling(int deviceIndex);
void ConfigurePmSampling(uint64_t hardwareBufferSize, uint64_t samplingInterval);
void StartPmSampling();
void StopPmSampling();
void DecodeAndPrintSamplingData();
void CleanupPmSampling();

int main()
{
    const int vectorLen = 4096 * 4096 * 2;
    size_t size = vectorLen * sizeof(int);

    // Initialize CUDA
    cuInit(0);

    // Setup CUDA workload
    int *h_A = (int*)malloc(size);
    int *h_B = (int*)malloc(size);
    int *h_C = (int*)malloc(size);

    for (int i = 0; i < vectorLen; ++i) {
        h_A[i] = i;
        h_B[i] = i * 2;
    }

    int *d_A, *d_B, *d_C;
    cudaMalloc((void )&d_A, size);
    cudaMalloc((void )&d_B, size);
    cudaMalloc((void )&d_C, size);

    cudaMemcpy(d_A, h_A, size, cudaMemcpyHostToDevice);
    cudaMemcpy(d_B, h_B, size, cudaMemcpyHostToDevice);

    // Initalize and Enable PM Sampling
    constexpr int deviceIndex = 0;
    InitializeAndEnablePmSampling(deviceIndex);

    // Configure PM Sampling
    constexpr size_t hardwareBufferSize = 512 * 1024 * 1024; // 512MB buffer
    constexpr uint64_t samplingInterval = 100000; // 100us interval
    ConfigurePmSampling(hardwareBufferSize, samplingInterval);

    // Start PM Sampling
    StartPmSampling();

    // Launch CUDA workload
    int threadsPerBlock = 512;
    int blocksPerGrid = (vectorLen + threadsPerBlock - 1) / threadsPerBlock;
    for (int i = 0; i < 100; ++i) {
        VectorAdd<<<blocksPerGrid, threadsPerBlock>>>(d_A, d_B, d_C, vectorLen);
    }
    cudaDeviceSynchronize();

    // Stop PM Sampling
    StopPmSampling();

    // Decode and print sampling data
    DecodeAndPrintSamplingData();

    // Cleanup PM Sampling
    CleanupPmSampling();

    // Cleanup
    cudaMemcpy(h_C, d_C, size, cudaMemcpyDeviceToHost);
    cudaFree(d_A); cudaFree(d_B); cudaFree(d_C);
    free(h_A); free(h_B); free(h_C);
    return 0;
}

void CreateConfigImage()
{
    CUpti_Profiler_Host_Initialize_Params hostInitializeParams = {CUpti_Profiler_Host_Initialize_Params_STRUCT_SIZE};
    hostInitializeParams.profilerType = CUPTI_PROFILER_TYPE_PM_SAMPLING;
    hostInitializeParams.pChipName = g_chipName.c_str();
    hostInitializeParams.pCounterAvailabilityImage = nullptr;
    cuptiProfilerHostInitialize(&hostInitializeParams);
    CUpti_Profiler_Host_Object* pHostObject = hostInitializeParams.pHostObject;

    CUpti_Profiler_Host_ConfigAddMetrics_Params configAddMetricsParams {CUpti_Profiler_Host_ConfigAddMetrics_Params_STRUCT_SIZE};
    configAddMetricsParams.pHostObject = pHostObject;
    configAddMetricsParams.ppMetricNames = g_metrics.data();
    configAddMetricsParams.numMetrics = g_metrics.size();
    cuptiProfilerHostConfigAddMetrics(&configAddMetricsParams);

    CUpti_Profiler_Host_GetConfigImageSize_Params getConfigImageSizeParams {CUpti_Profiler_Host_GetConfigImageSize_Params_STRUCT_SIZE};
    getConfigImageSizeParams.pHostObject = pHostObject;
    cuptiProfilerHostGetConfigImageSize(&getConfigImageSizeParams);
    g_configImage.resize(getConfigImageSizeParams.configImageSize);

    CUpti_Profiler_Host_GetConfigImage_Params getConfigImageParams = {CUpti_Profiler_Host_GetConfigImage_Params_STRUCT_SIZE};
    getConfigImageParams.pHostObject = pHostObject;
    getConfigImageParams.pConfigImage = g_configImage.data();
    getConfigImageParams.configImageSize = g_configImage.size();
    cuptiProfilerHostGetConfigImage(&getConfigImageParams);

    CUpti_Profiler_Host_GetNumOfPasses_Params getNumOfPassesParam {CUpti_Profiler_Host_GetNumOfPasses_Params_STRUCT_SIZE};
    getNumOfPassesParam.pConfigImage = g_configImage.data();
    getNumOfPassesParam.configImageSize = g_configImage.size();
    cuptiProfilerHostGetNumOfPasses(&getNumOfPassesParam);
    printf("Num of Passes: %d\n", getNumOfPassesParam.numOfPasses);

    CUpti_Profiler_Host_Deinitialize_Params deinitializeParams = {CUpti_Profiler_Host_Deinitialize_Params_STRUCT_SIZE};
    deinitializeParams.pHostObject = pHostObject;
    cuptiProfilerHostDeinitialize(&deinitializeParams);
    pHostObject = nullptr;
}

void EvaluateAndPrintForSample(size_t sampleIndex, CUpti_Profiler_Host_Object* pHostObject, std::vector<uint8_t>& counterDataImage)
{
    CUpti_PmSampling_CounterData_GetSampleInfo_Params getSampleInfoParams = {CUpti_PmSampling_CounterData_GetSampleInfo_Params_STRUCT_SIZE};
    getSampleInfoParams.pPmSamplingObject = g_pPmSamplingObject;
    getSampleInfoParams.pCounterDataImage = counterDataImage.data();
    getSampleInfoParams.counterDataImageSize = counterDataImage.size();
    getSampleInfoParams.sampleIndex = sampleIndex;
    cuptiPmSamplingCounterDataGetSampleInfo(&getSampleInfoParams);
    printf("Sample Index: %zu, Start Timestamp: %llu, End Timestamp: %llu\n", sampleIndex, getSampleInfoParams.startTimestamp, getSampleInfoParams.endTimestamp);

    std::vector<double> metricValues(g_metrics.size());
    CUpti_Profiler_Host_EvaluateToGpuValues_Params evalauateToGpuValuesParams {CUpti_Profiler_Host_EvaluateToGpuValues_Params_STRUCT_SIZE};
    evalauateToGpuValuesParams.pHostObject = pHostObject;
    evalauateToGpuValuesParams.pCounterDataImage = counterDataImage.data();
    evalauateToGpuValuesParams.counterDataImageSize = counterDataImage.size();
    evalauateToGpuValuesParams.ppMetricNames = g_metrics.data();
    evalauateToGpuValuesParams.numMetrics = g_metrics.size();
    evalauateToGpuValuesParams.rangeIndex = sampleIndex;
    evalauateToGpuValuesParams.pMetricValues = metricValues.data();
    cuptiProfilerHostEvaluateToGpuValues(&evalauateToGpuValuesParams);

    for (size_t i = 0; i < g_metrics.size(); ++i) {
        printf("\t%s: %f\n", g_metrics[i], metricValues[i]);
    }
    printf("\n");
}

void EvaluateAndPrintAllSamples(size_t numOfSamples)
{
    CUpti_Profiler_Host_Initialize_Params hostInitializeParams = {CUpti_Profiler_Host_Initialize_Params_STRUCT_SIZE};
    hostInitializeParams.profilerType = CUPTI_PROFILER_TYPE_PM_SAMPLING;
    hostInitializeParams.pChipName = g_chipName.c_str();
    hostInitializeParams.pCounterAvailabilityImage = nullptr;
    cuptiProfilerHostInitialize(&hostInitializeParams);
    CUpti_Profiler_Host_Object* pHostObject = hostInitializeParams.pHostObject;

    for (size_t sampleIndex = 0; sampleIndex < numOfSamples; ++sampleIndex) {
        EvaluateAndPrintForSample(sampleIndex, pHostObject, g_counterDataImage);
    }

    CUpti_Profiler_Host_Deinitialize_Params deinitializeParams = {CUpti_Profiler_Host_Deinitialize_Params_STRUCT_SIZE};
    deinitializeParams.pHostObject = pHostObject;
    cuptiProfilerHostDeinitialize(&deinitializeParams);
    pHostObject = nullptr;
}

// Helper function to initialize PM Sampling
void InitializeAndEnablePmSampling(int deviceIndex)
{
    // Initialize CUPTI Profiler
    CUpti_Profiler_Initialize_Params profilerInitializeParams = { CUpti_Profiler_Initialize_Params_STRUCT_SIZE };
    cuptiProfilerInitialize(&profilerInitializeParams);

    CUpti_Device_GetChipName_Params getChipNameParams = { CUpti_Device_GetChipName_Params_STRUCT_SIZE };
    getChipNameParams.deviceIndex = deviceIndex;
    cuptiDeviceGetChipName(&getChipNameParams);
    g_chipName = getChipNameParams.pChipName;
    printf("Chip Name: %s\n", g_chipName.c_str());

    // Enable PM sampling
    CUpti_PmSampling_Enable_Params enableParams = { CUpti_PmSampling_Enable_Params_STRUCT_SIZE };
    enableParams.deviceIndex = deviceIndex;
    cuptiPmSamplingEnable(&enableParams);
    g_pPmSamplingObject = enableParams.pPmSamplingObject;
}

void ConfigurePmSampling(uint64_t hardwareBufferSize, uint64_t samplingInterval)
{
    // Need to create the config image which will have the scheduling information for the metrics
    CreateConfigImage();

    // Set configuration
    CUpti_PmSampling_SetConfig_Params setConfigParams = { CUpti_PmSampling_SetConfig_Params_STRUCT_SIZE };
    setConfigParams.pPmSamplingObject = g_pPmSamplingObject;
    setConfigParams.configSize = g_configImage.size();
    setConfigParams.pConfig = g_configImage.data();
    setConfigParams.hardwareBufferSize = hardwareBufferSize;
    setConfigParams.samplingInterval = samplingInterval;
    setConfigParams.triggerMode = CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_SYSCLK_INTERVAL;
    cuptiPmSamplingSetConfig(&setConfigParams);
}

// Helper function to start PM sampling
void StartPmSampling()
{
    CUpti_PmSampling_Start_Params startParams = { CUpti_PmSampling_Start_Params_STRUCT_SIZE };
    startParams.pPmSamplingObject = g_pPmSamplingObject;
    cuptiPmSamplingStart(&startParams);
}

// Helper function to stop PM sampling
void StopPmSampling()
{
    CUpti_PmSampling_Stop_Params stopParams = { CUpti_PmSampling_Stop_Params_STRUCT_SIZE };
    stopParams.pPmSamplingObject = g_pPmSamplingObject;
    cuptiPmSamplingStop(&stopParams);
}

// Helper function to create counter data image
void CreateCounterDataImage(uint64_t maxSamplesInCounterDataImage)
{
    CUpti_PmSampling_GetCounterDataSize_Params getCounterDataSizeParams = { CUpti_PmSampling_GetCounterDataSize_Params_STRUCT_SIZE };
    getCounterDataSizeParams.pPmSamplingObject = g_pPmSamplingObject;
    getCounterDataSizeParams.numMetrics = g_metrics.size();
    getCounterDataSizeParams.pMetricNames = g_metrics.data();
    getCounterDataSizeParams.maxSamples = maxSamplesInCounterDataImage;
    cuptiPmSamplingGetCounterDataSize(&getCounterDataSizeParams);

    g_counterDataImage.resize(getCounterDataSizeParams.counterDataSize);
    CUpti_PmSampling_CounterDataImage_Initialize_Params initializeParams = { CUpti_PmSampling_CounterDataImage_Initialize_Params_STRUCT_SIZE };
    initializeParams.pPmSamplingObject = g_pPmSamplingObject;
    initializeParams.counterDataSize = g_counterDataImage.size();
    initializeParams.pCounterData = g_counterDataImage.data();
    cuptiPmSamplingCounterDataImageInitialize(&initializeParams);
}

// Helper function to decode and print sampling data
void DecodeAndPrintSamplingData()
{
    // Create counter data image which will store the decoded data from the hardware buffer
    constexpr uint64_t maxSamplesInCounterDataImage = 10000;
    CreateCounterDataImage(maxSamplesInCounterDataImage);

    // Decode sampling data
    CUpti_PmSampling_DecodeData_Params decodeParams = { CUpti_PmSampling_DecodeData_Params_STRUCT_SIZE };
    decodeParams.pPmSamplingObject = g_pPmSamplingObject;
    decodeParams.pCounterDataImage = g_counterDataImage.data();
    decodeParams.counterDataImageSize = g_counterDataImage.size();
    cuptiPmSamplingDecodeData(&decodeParams);

    // Get information about decoded data
    CUpti_PmSampling_GetCounterDataInfo_Params counterDataInfo = { CUpti_PmSampling_GetCounterDataInfo_Params_STRUCT_SIZE };
    counterDataInfo.pCounterDataImage = g_counterDataImage.data();
    counterDataInfo.counterDataImageSize = g_counterDataImage.size();
    cuptiPmSamplingGetCounterDataInfo(&counterDataInfo);
    printf("Number of completed samples: %zu\n", counterDataInfo.numCompletedSamples);

    // Print sample information (first 10 samples)
    size_t maxSamplesToShow = (counterDataInfo.numCompletedSamples > 10) ? 10 : counterDataInfo.numCompletedSamples;
    EvaluateAndPrintAllSamples(maxSamplesToShow);
}

void CleanupPmSampling()
{
    // Disable PM sampling
    CUpti_PmSampling_Disable_Params disableParams = { CUpti_PmSampling_Disable_Params_STRUCT_SIZE };
    disableParams.pPmSamplingObject = g_pPmSamplingObject;
    cuptiPmSamplingDisable(&disableParams);

    // Deinitialize profiler
    CUpti_Profiler_DeInitialize_Params profilerDeInitializeParams = { CUpti_Profiler_DeInitialize_Params_STRUCT_SIZE };
    cuptiProfilerDeInitialize(&profilerDeInitializeParams);
}
```


### 5.3.9. Expected Output


When the above code is run, output similar to the following should be seen:


```
Chip Name: AD104
Num of Passes: 1
Number of completed samples: 1770
Sample Index: 0, Start Timestamp: 1756793790519908305, End Timestamp: 1756793790687993793
        gr__cycles_active.avg: 0.000000
        gr__cycles_elapsed.max: 1160086.000000
        sm__cycles_active.avg: 0.000000

Sample Index: 1, Start Timestamp: 1756793790687993793, End Timestamp: 1756793790688045473
        gr__cycles_active.avg: 0.000000
        gr__cycles_elapsed.max: 100001.000000
        sm__cycles_active.avg: 0.000000

Sample Index: 2, Start Timestamp: 1756793790688045473, End Timestamp: 1756793790688097153
        gr__cycles_active.avg: 49047.000000
        gr__cycles_elapsed.max: 100001.000000
        sm__cycles_active.avg: 0.000000

Sample Index: 3, Start Timestamp: 1756793790688097153, End Timestamp: 1756793790688149058
        gr__cycles_active.avg: 79180.000000
        gr__cycles_elapsed.max: 100001.000000
        sm__cycles_active.avg: 73766.214286
...
```


This indicates that CUPTI PM Sampling has successfully collected performance metrics during the execution of your CUDA kernels.


### 5.3.10. Advanced Usage: Continuous Decode Thread


For long-running workloads, use a dedicated thread for continuous decoding to avoid hardware buffer overflow:


```
#include <pthread.h>
#include <atomic>

struct DecodeThreadArgs
{
    CUpti_PmSampling_Object* pPmSamplingObject;
    uint8_t* counterDataImage;
    size_t counterDataImageSize;
    std::atomic<bool>* stopFlag;
};

void* DecodeThread(void* args)
{
    DecodeThreadArgs* threadArgs = (DecodeThreadArgs*)args;
    while (!threadArgs->stopFlag->load())
    {
        CUpti_PmSampling_DecodeData_Params decodeParams = { CUpti_PmSampling_DecodeData_Params_STRUCT_SIZE };
        decodeParams.pPmSamplingObject = threadArgs->pPmSamplingObject;
        decodeParams.pCounterDataImage = threadArgs->counterDataImage;
        decodeParams.counterDataImageSize = threadArgs->counterDataImageSize;
        cuptiPmSamplingDecodeData(&decodeParams);

        // Process decoded data here

        // Reset counter data image for next batch
        CUpti_PmSampling_CounterDataImage_Initialize_Params resetParams = { CUpti_PmSampling_CounterDataImage_Initialize_Params_STRUCT_SIZE };
        resetParams.pPmSamplingObject = threadArgs->pPmSamplingObject;
        resetParams.counterDataSize = threadArgs->counterDataImageSize;
        resetParams.pCounterData = threadArgs->counterDataImage;
        cuptiPmSamplingCounterDataImageInitialize(&resetParams);

        usleep(10000); // 10ms sleep
    }
    return NULL;
}
```


Note: For detailed information on creating configuration images with specific metrics and evaluating counter data to obtain metric values, refer to the Host API Tutorial section.


## 5.4. GPU Performance Profiling using Range Profiler API


This tutorial provides a guide to collecting performance metrics from a CUDA kernel using the CUPTI Range Profiler API. Starting with a basic vector addition kernel, it incrementally introduces CUPTI Range Profiler API calls to collect hardware performance counters for specific ranges of CUDA kernel execution.


### 5.4.1. Simple Vector Addition in CUDA C


First, let’s write a vector addition kernel in CUDA C, as demonstrated in the section on [simple vector addition in CUDA C](tutorial.html#simple-vector-addition-in-cuda-c).


### 5.4.2. Step 1: Include Headers and Define Global Variables


First, include the CUPTI Range Profiler headers and declare these globals:


> - Range profiler object: holds per-context range profiling state.
>  - Counter data image: stores decoded hardware profiling results.
>  - Config image: built via host APIs; contains metric scheduling for collection.
>  - CUDA context: the context where range profiling is enabled and data is collected.
>  - Metric list: the set of metrics to capture during range profiling.


```
#include <cupti_profiler_host.h>
#include <cupti_range_profiler.h>
#include <cupti_target.h>

// Global variables for Range Profiler
CUpti_RangeProfiler_Object* g_pRangeProfilerObject = NULL;

std::vector<uint8_t> g_counterDataImage;
std::vector<uint8_t> g_configImage;

CUcontext g_cuContext;
std::string g_chipName;

std::vector<const char*> g_metrics =
{
    "sm__warps_launched.sum",     // Number of warps launched
    "sm__ctas_launched.sum"       // Number of CTAs launched
};
```


### 5.4.3. Step 2: Initialize CUPTI Profiler and Enable Range Profiler


Initialize the CUPTI profiler, enable Range Profiler on the device, and retrieve the chip name required for the configuration image:


```
// Helper function to initialize CUDA context and Range Profiler
void InitializeAndEnableRangeProfiler(CUcontext cuContext)
{
    // Initialize CUPTI Profiler
    CUpti_Profiler_Initialize_Params profilerInitializeParams = { CUpti_Profiler_Initialize_Params_STRUCT_SIZE };
    cuptiProfilerInitialize(&profilerInitializeParams);

    CUdevice device;
    cuCtxGetDevice(&device);
    CUpti_Device_GetChipName_Params getChipNameParams = { CUpti_Device_GetChipName_Params_STRUCT_SIZE };
    getChipNameParams.deviceIndex = (size_t)device;
    cuptiDeviceGetChipName(&getChipNameParams);
    g_chipName = std::string(getChipNameParams.pChipName);
    printf("Chip Name: %s\n", g_chipName.c_str());

    // Enable Range profiler
    CUpti_RangeProfiler_Enable_Params enableRange = { CUpti_RangeProfiler_Enable_Params_STRUCT_SIZE };
    enableRange.ctx = cuContext;
    cuptiRangeProfilerEnable(&enableRange);
    g_pRangeProfilerObject = enableRange.pRangeProfilerObject;
}
```


### 5.4.4. Step 3: Create Counter Data Image and Configure Range Profiler


Create the configuration image with metric scheduling, then create the counter data image to hold decoded hardware results, and configure the profiler:


```
// Helper function to create counter data image
void CreateCounterDataImage(size_t maxNumOfRangesInCounterDataImage)
{
    // Get counter data size
    CUpti_RangeProfiler_GetCounterDataSize_Params ctDataSize = { CUpti_RangeProfiler_GetCounterDataSize_Params_STRUCT_SIZE };
    ctDataSize.pRangeProfilerObject = g_pRangeProfilerObject;
    ctDataSize.pMetricNames = g_metrics.data();
    ctDataSize.numMetrics = g_metrics.size();
    ctDataSize.maxNumOfRanges = maxNumOfRangesInCounterDataImage;
    ctDataSize.maxNumRangeTreeNodes = maxNumOfRangesInCounterDataImage;
    cuptiRangeProfilerGetCounterDataSize(&ctDataSize);

    // Initialize counter data image
    g_counterDataImage.resize(ctDataSize.counterDataSize);
    CUpti_RangeProfiler_CounterDataImage_Initialize_Params initCtImg = { CUpti_RangeProfiler_CounterDataImage_Initialize_Params_STRUCT_SIZE };
    initCtImg.pRangeProfilerObject = g_pRangeProfilerObject;
    initCtImg.pCounterData = g_counterDataImage.data();
    initCtImg.counterDataSize = g_counterDataImage.size();
    cuptiRangeProfilerCounterDataImageInitialize(&initCtImg);
}

void ConfigureRangeProfiler(CUpti_ProfilerRange range, CUpti_ProfilerReplayMode replayMode, size_t numOfRanges)
{
    // Create config image
    CreateConfigImage();

    // Create counter data image
    CreateCounterDataImage(numOfRanges);

    CUpti_RangeProfiler_SetConfig_Params setConfig = { CUpti_RangeProfiler_SetConfig_Params_STRUCT_SIZE };
    setConfig.pRangeProfilerObject = g_pRangeProfilerObject;
    setConfig.configSize = g_configImage.size();
    setConfig.pConfig = g_configImage.data();
    setConfig.counterDataImageSize = g_counterDataImage.size();
    setConfig.pCounterDataImage = g_counterDataImage.data();
    setConfig.range = range;
    setConfig.replayMode = replayMode;
    setConfig.maxRangesPerPass = numOfRanges;
    setConfig.numNestingLevels = 1;
    setConfig.minNestingLevel = 1;
    setConfig.passIndex = 0;
    setConfig.targetNestingLevel = 0;
    cuptiRangeProfilerSetConfig(&setConfig);
}
```


### 5.4.5. Step 4: Start and Stop Range Profiling Around Workload


Begin data collection and stop it after the workload is launched:


```
// Helper function to start range profiling
void StartRangeProfiler()
{
    CUpti_RangeProfiler_Start_Params startRangeProfiler = { CUpti_RangeProfiler_Start_Params_STRUCT_SIZE };
    startRangeProfiler.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerStart(&startRangeProfiler);
}

// Helper function to stop range profiling
void StopRangeProfiler()
{
    CUpti_RangeProfiler_Stop_Params stopRangeProfiler = { CUpti_RangeProfiler_Stop_Params_STRUCT_SIZE };
    stopRangeProfiler.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerStop(&stopRangeProfiler);
}
```


### 5.4.6. Step 5: Decode and Evaluate Profiling Data


Decode the collected profiling data and evaluate metrics:


```
// Helper function to decode and print profiling data
void DecodeAndPrintProfilingData()
{
    // Decode profiling data
    CUpti_RangeProfiler_DecodeData_Params decodeData = { CUpti_RangeProfiler_DecodeData_Params_STRUCT_SIZE };
    decodeData.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerDecodeData(&decodeData);

    // Get information about profiled ranges
    CUpti_RangeProfiler_GetCounterDataInfo_Params cdiParams = { CUpti_RangeProfiler_GetCounterDataInfo_Params_STRUCT_SIZE };
    cdiParams.pCounterDataImage = g_counterDataImage.data();
    cdiParams.counterDataImageSize = g_counterDataImage.size();
    cuptiRangeProfilerGetCounterDataInfo(&cdiParams);
    printf("Number of profiled ranges: %zu\n", cdiParams.numTotalRanges);

    // Evaluate and print profiling data
    const size_t numRangesToPrint = cdiParams.numTotalRanges > 10 ? 10 : cdiParams.numTotalRanges;
    EvaluateAndPrintAllRanges(numRangesToPrint);
}
```


### 5.4.7. Step 7: Cleanup Range Profiler


Disable Range Profiler and release all allocated resources:


```
void CleanupRangeProfiler()
{
    // Disable Range profiler
    CUpti_RangeProfiler_Disable_Params disableRangeProfiler = { CUpti_RangeProfiler_Disable_Params_STRUCT_SIZE };
    disableRangeProfiler.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerDisable(&disableRangeProfiler);

    // Deinitialize profiler
    CUpti_Profiler_DeInitialize_Params profilerDeInitializeParams = { CUpti_Profiler_DeInitialize_Params_STRUCT_SIZE };
    cuptiProfilerDeInitialize(&profilerDeInitializeParams);
}
```


### 5.4.8. Complete Example


Your final code should look like this:


```
#include <cuda_runtime.h>
#include <cuda.h>
#include <stdio.h>
#include <stdint.h>
#include <vector>
#include <cupti_profiler_host.h>
#include <cupti_range_profiler.h>
#include <cupti_target.h>

// Global variables for Range Profiler
CUpti_RangeProfiler_Object* g_pRangeProfilerObject = NULL;

std::vector<uint8_t> g_counterDataImage;
std::vector<uint8_t> g_configImage;

CUcontext g_cuContext;
std::string g_chipName;

std::vector<const char*> g_metrics =
{
    "sm__warps_launched.sum",     // Number of warps launched
    "sm__ctas_launched.sum"
};

// CUDA kernel for vector addition
__global__ void VectorAdd(const float *A, const float *B, float *C, int N)
{
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    if (idx < N)
        C[idx] = A[idx] + B[idx];
}

// Helper function declarations
void InitializeAndEnableRangeProfiler(CUcontext cuContext);
void ConfigureRangeProfiler(CUpti_ProfilerRange range, CUpti_ProfilerReplayMode replayMode, size_t numOfRanges);
void StartRangeProfiler();
void StopRangeProfiler();
void DecodeAndPrintProfilingData();
void CleanupRangeProfiler();

int main()
{
    const int vectorLen = 1024 * 1024;
    const size_t size = vectorLen * sizeof(float);

    // Initialize CUDA and create context
    cuInit(0);
    cuCtxCreate(&g_cuContext, (CUctxCreateParams*)0, 0, 0);

    // Initialize and Enable Range Profiler
    InitializeAndEnableRangeProfiler(g_cuContext);

    // Configure Range Profiler
    constexpr size_t numOfRanges = 10;
    ConfigureRangeProfiler(CUPTI_AutoRange, CUPTI_KernelReplay, numOfRanges);

    // Setup CUDA workload
    float *h_A = (float*)malloc(size);
    float *h_B = (float*)malloc(size);
    float *h_C = (float*)malloc(size);

    for (int i = 0; i < vectorLen; ++i) {
        h_A[i] = rand() / (float)RAND_MAX;
        h_B[i] = rand() / (float)RAND_MAX;
    }

    float *d_A, *d_B, *d_C;
    cudaMalloc((void )&d_A, size);
    cudaMalloc((void )&d_B, size);
    cudaMalloc((void )&d_C, size);

    cudaMemcpy(d_A, h_A, size, cudaMemcpyHostToDevice);
    cudaMemcpy(d_B, h_B, size, cudaMemcpyHostToDevice);

    int threadsPerBlock = 128;
    int blocksPerGrid = (vectorLen + threadsPerBlock - 1) / threadsPerBlock;

    // Start Range Profiling
    StartRangeProfiler();

    // Launch CUDA workload
    VectorAdd<<<blocksPerGrid, threadsPerBlock>>>(d_A, d_B, d_C, vectorLen);

    // Stop Range Profiling
    StopRangeProfiler();

    // Decode and evaluate profiling data
    DecodeAndPrintProfilingData();

    // Cleanup Range Profiler
    CleanupRangeProfiler();

    cudaMemcpy(h_C, d_C, size, cudaMemcpyDeviceToHost);
    cudaDeviceSynchronize();

    // Cleanup
    cudaFree(d_A); cudaFree(d_B); cudaFree(d_C);
    free(h_A); free(h_B); free(h_C);
    return 0;
}

void CreateConfigImage()
{
    CUpti_Profiler_Host_Initialize_Params hostInitializeParams = {CUpti_Profiler_Host_Initialize_Params_STRUCT_SIZE};
    hostInitializeParams.profilerType = CUPTI_PROFILER_TYPE_RANGE_PROFILER;
    hostInitializeParams.pChipName = g_chipName.c_str();
    hostInitializeParams.pCounterAvailabilityImage = nullptr;
    cuptiProfilerHostInitialize(&hostInitializeParams);
    CUpti_Profiler_Host_Object* pHostObject = hostInitializeParams.pHostObject;

    CUpti_Profiler_Host_ConfigAddMetrics_Params configAddMetricsParams {CUpti_Profiler_Host_ConfigAddMetrics_Params_STRUCT_SIZE};
    configAddMetricsParams.pHostObject = pHostObject;
    configAddMetricsParams.ppMetricNames = g_metrics.data();
    configAddMetricsParams.numMetrics = g_metrics.size();
    cuptiProfilerHostConfigAddMetrics(&configAddMetricsParams);

    CUpti_Profiler_Host_GetConfigImageSize_Params getConfigImageSizeParams {CUpti_Profiler_Host_GetConfigImageSize_Params_STRUCT_SIZE};
    getConfigImageSizeParams.pHostObject = pHostObject;
    cuptiProfilerHostGetConfigImageSize(&getConfigImageSizeParams);
    g_configImage.resize(getConfigImageSizeParams.configImageSize);

    CUpti_Profiler_Host_GetConfigImage_Params getConfigImageParams = {CUpti_Profiler_Host_GetConfigImage_Params_STRUCT_SIZE};
    getConfigImageParams.pHostObject = pHostObject;
    getConfigImageParams.pConfigImage = g_configImage.data();
    getConfigImageParams.configImageSize = g_configImage.size();
    cuptiProfilerHostGetConfigImage(&getConfigImageParams);

    CUpti_Profiler_Host_GetNumOfPasses_Params getNumOfPassesParam {CUpti_Profiler_Host_GetNumOfPasses_Params_STRUCT_SIZE};
    getNumOfPassesParam.pConfigImage = g_configImage.data();
    getNumOfPassesParam.configImageSize = g_configImage.size();
    cuptiProfilerHostGetNumOfPasses(&getNumOfPassesParam);
    printf("Num of Passes: %d\n", getNumOfPassesParam.numOfPasses);

    CUpti_Profiler_Host_Deinitialize_Params deinitializeParams = {CUpti_Profiler_Host_Deinitialize_Params_STRUCT_SIZE};
    deinitializeParams.pHostObject = pHostObject;
    cuptiProfilerHostDeinitialize(&deinitializeParams);
    pHostObject = nullptr;
}

void EvaluateAndPrintForRange(size_t rangeIndex, CUpti_Profiler_Host_Object* pHostObject)
{
    std::vector<double> metricValues(g_metrics.size());
    CUpti_Profiler_Host_EvaluateToGpuValues_Params evalauateToGpuValuesParams {CUpti_Profiler_Host_EvaluateToGpuValues_Params_STRUCT_SIZE};
    evalauateToGpuValuesParams.pHostObject = pHostObject;
    evalauateToGpuValuesParams.pCounterDataImage = g_counterDataImage.data();
    evalauateToGpuValuesParams.counterDataImageSize = g_counterDataImage.size();
    evalauateToGpuValuesParams.ppMetricNames = g_metrics.data();
    evalauateToGpuValuesParams.numMetrics = g_metrics.size();
    evalauateToGpuValuesParams.rangeIndex = rangeIndex;
    evalauateToGpuValuesParams.pMetricValues = metricValues.data();
    cuptiProfilerHostEvaluateToGpuValues(&evalauateToGpuValuesParams);

    for (size_t i = 0; i < g_metrics.size(); ++i) {
        printf("\t%s: %f\n", g_metrics[i], metricValues[i]);
    }
    printf("\n");
}

void EvaluateAndPrintAllRanges(size_t numOfRanges)
{
    CUpti_Profiler_Host_Initialize_Params hostInitializeParams = {CUpti_Profiler_Host_Initialize_Params_STRUCT_SIZE};
    hostInitializeParams.profilerType = CUPTI_PROFILER_TYPE_RANGE_PROFILER;
    hostInitializeParams.pChipName = g_chipName.c_str();
    hostInitializeParams.pCounterAvailabilityImage = nullptr;
    cuptiProfilerHostInitialize(&hostInitializeParams);
    CUpti_Profiler_Host_Object* pHostObject = hostInitializeParams.pHostObject;

    for (size_t i = 0; i < numOfRanges; ++i)
    {
        CUpti_RangeProfiler_CounterData_GetRangeInfo_Params getRangeInfoParams = {CUpti_RangeProfiler_CounterData_GetRangeInfo_Params_STRUCT_SIZE};
        getRangeInfoParams.counterDataImageSize = g_counterDataImage.size();
        getRangeInfoParams.pCounterDataImage = g_counterDataImage.data();
        getRangeInfoParams.rangeIndex = i;
        getRangeInfoParams.rangeDelimiter = "/";
        cuptiRangeProfilerCounterDataGetRangeInfo(&getRangeInfoParams);

        printf("Range: %s\n", getRangeInfoParams.rangeName);
        printf("Metric Values:\n");
        EvaluateAndPrintForRange(i, pHostObject);
    }

    CUpti_Profiler_Host_Deinitialize_Params deinitializeParams = {CUpti_Profiler_Host_Deinitialize_Params_STRUCT_SIZE};
    deinitializeParams.pHostObject = pHostObject;
    cuptiProfilerHostDeinitialize(&deinitializeParams);
    pHostObject = nullptr;
}

void InitializeAndEnableRangeProfiler(CUcontext cuContext)
{
    // Initialize CUPTI Profiler
    CUpti_Profiler_Initialize_Params profilerInitializeParams = { CUpti_Profiler_Initialize_Params_STRUCT_SIZE };
    cuptiProfilerInitialize(&profilerInitializeParams);

    CUdevice device;
    cuCtxGetDevice(&device);
    CUpti_Device_GetChipName_Params getChipNameParams = { CUpti_Device_GetChipName_Params_STRUCT_SIZE };
    getChipNameParams.deviceIndex = (size_t)device;
    cuptiDeviceGetChipName(&getChipNameParams);
    g_chipName = std::string(getChipNameParams.pChipName);
    printf("Chip Name: %s\n", g_chipName.c_str());

    // Enable Range profiler
    CUpti_RangeProfiler_Enable_Params enableRange = { CUpti_RangeProfiler_Enable_Params_STRUCT_SIZE };
    enableRange.ctx = cuContext;
    cuptiRangeProfilerEnable(&enableRange);
    g_pRangeProfilerObject = enableRange.pRangeProfilerObject;
}

void CreateCounterDataImage(size_t maxNumOfRangesInCounterDataImage)
{
    // Get counter data size
    CUpti_RangeProfiler_GetCounterDataSize_Params ctDataSize = { CUpti_RangeProfiler_GetCounterDataSize_Params_STRUCT_SIZE };
    ctDataSize.pRangeProfilerObject = g_pRangeProfilerObject;
    ctDataSize.pMetricNames = g_metrics.data();
    ctDataSize.numMetrics = g_metrics.size();
    ctDataSize.maxNumOfRanges = maxNumOfRangesInCounterDataImage;
    ctDataSize.maxNumRangeTreeNodes = maxNumOfRangesInCounterDataImage;
    cuptiRangeProfilerGetCounterDataSize(&ctDataSize);

    // Initialize counter data image
    g_counterDataImage.resize(ctDataSize.counterDataSize);
    CUpti_RangeProfiler_CounterDataImage_Initialize_Params initCtImg = { CUpti_RangeProfiler_CounterDataImage_Initialize_Params_STRUCT_SIZE };
    initCtImg.pRangeProfilerObject = g_pRangeProfilerObject;
    initCtImg.pCounterData = g_counterDataImage.data();
    initCtImg.counterDataSize = g_counterDataImage.size();
    cuptiRangeProfilerCounterDataImageInitialize(&initCtImg);
}

void ConfigureRangeProfiler(CUpti_ProfilerRange range, CUpti_ProfilerReplayMode replayMode, size_t numOfRanges)
{
    // Create config image
    CreateConfigImage();

    // Create counter data image
    CreateCounterDataImage(numOfRanges);

    CUpti_RangeProfiler_SetConfig_Params setConfig = { CUpti_RangeProfiler_SetConfig_Params_STRUCT_SIZE };
    setConfig.pRangeProfilerObject = g_pRangeProfilerObject;
    setConfig.configSize = g_configImage.size();
    setConfig.pConfig = g_configImage.data();
    setConfig.counterDataImageSize = g_counterDataImage.size();
    setConfig.pCounterDataImage = g_counterDataImage.data();
    setConfig.range = range;
    setConfig.replayMode = replayMode;
    setConfig.maxRangesPerPass = numOfRanges;
    setConfig.numNestingLevels = 1;
    setConfig.minNestingLevel = 1;
    setConfig.passIndex = 0;
    setConfig.targetNestingLevel = 0;
    cuptiRangeProfilerSetConfig(&setConfig);
}

void StartRangeProfiler()
{
    CUpti_RangeProfiler_Start_Params startRangeProfiler = { CUpti_RangeProfiler_Start_Params_STRUCT_SIZE };
    startRangeProfiler.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerStart(&startRangeProfiler);
}

void StopRangeProfiler()
{
    CUpti_RangeProfiler_Stop_Params stopRangeProfiler = { CUpti_RangeProfiler_Stop_Params_STRUCT_SIZE };
    stopRangeProfiler.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerStop(&stopRangeProfiler);
}

void DecodeAndPrintProfilingData()
{
    // Decode profiling data
    CUpti_RangeProfiler_DecodeData_Params decodeData = { CUpti_RangeProfiler_DecodeData_Params_STRUCT_SIZE };
    decodeData.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerDecodeData(&decodeData);

    // Get information about profiled ranges
    CUpti_RangeProfiler_GetCounterDataInfo_Params cdiParams = { CUpti_RangeProfiler_GetCounterDataInfo_Params_STRUCT_SIZE };
    cdiParams.pCounterDataImage = g_counterDataImage.data();
    cdiParams.counterDataImageSize = g_counterDataImage.size();
    cuptiRangeProfilerGetCounterDataInfo(&cdiParams);
    printf("Number of profiled ranges: %zu\n", cdiParams.numTotalRanges);

    // Evaluate and print profiling data
    const size_t numRangesToPrint = cdiParams.numTotalRanges > 10 ? 10 : cdiParams.numTotalRanges;
    EvaluateAndPrintAllRanges(numRangesToPrint);
}

void CleanupRangeProfiler()
{
    // Disable Range profiler
    CUpti_RangeProfiler_Disable_Params disableRangeProfiler = { CUpti_RangeProfiler_Disable_Params_STRUCT_SIZE };
    disableRangeProfiler.pRangeProfilerObject = g_pRangeProfilerObject;
    cuptiRangeProfilerDisable(&disableRangeProfiler);

    // Deinitialize profiler
    CUpti_Profiler_DeInitialize_Params profilerDeInitializeParams = { CUpti_Profiler_DeInitialize_Params_STRUCT_SIZE };
    cuptiProfilerDeInitialize(&profilerDeInitializeParams);
}
```


### 5.4.9. Expected Output


When the above code is run, output similar to the following should be seen:


```
Number of profiled ranges: 1
Range: 0
Metric Values:
    sm__warps_launched.sum: 32768.000000
    sm__ctas_launched.sum: 8192.000000
```


This indicates that CUPTI Range Profiler has successfully collected performance metrics for the vector addition kernel execution.


Note: For detailed information on available metrics and their meanings, refer to the CUPTI documentation and use the Host API to query available metrics for your GPU architecture.