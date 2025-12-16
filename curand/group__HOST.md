# cuRAND

[< Previous](modules.html) | [Next >](group__DEVICE.html)  cuRAND ([PDF](https://docs.nvidia.com/cuda/pdf/CURAND_Library.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20cuRAND)
## 5.1. Host API




### Functions


curandStatus_t CURANDAPI curandCreateGenerator (  curandGenerator_t* generator, curandRngType_t rng_type )
Create new random number generator.

curandStatus_t CURANDAPI curandCreateGeneratorHost (  curandGenerator_t* generator, curandRngType_t rng_type )
Create new host CPU random number generator.

curandStatus_t CURANDAPI curandCreatePoissonDistribution (  double  lambda, curandDiscreteDistribution_t* discrete_distribution )
Construct the histogram array for a Poisson distribution.

curandStatus_t CURANDAPI curandDestroyDistribution (  curandDiscreteDistribution_t discrete_distribution )
Destroy the histogram array for a discrete distribution (e.g. Poisson).

curandStatus_t CURANDAPI curandDestroyGenerator (  curandGenerator_t generator )
Destroy an existing generator.

curandStatus_t CURANDAPI curandGenerate (  curandGenerator_t generator, unsigned int* outputPtr, size_t num )
Generate 32-bit pseudo or quasirandom numbers.

curandStatus_t CURANDAPI curandGenerateLogNormal (  curandGenerator_t generator, float* outputPtr, size_t n, float  mean, float  stddev )
Generate log-normally distributed floats.

curandStatus_t CURANDAPI curandGenerateLogNormalDouble (  curandGenerator_t generator, double* outputPtr, size_t n, double  mean, double  stddev )
Generate log-normally distributed doubles.

curandStatus_t CURANDAPI curandGenerateLongLong (  curandGenerator_t generator, unsigned long long* outputPtr, size_t num )
Generate 64-bit quasirandom numbers.

curandStatus_t CURANDAPI curandGenerateNormal (  curandGenerator_t generator, float* outputPtr, size_t n, float  mean, float  stddev )
Generate normally distributed doubles.

curandStatus_t CURANDAPI curandGenerateNormalDouble (  curandGenerator_t generator, double* outputPtr, size_t n, double  mean, double  stddev )
Generate normally distributed doubles.

curandStatus_t CURANDAPI curandGeneratePoisson (  curandGenerator_t generator, unsigned int* outputPtr, size_t n, double  lambda )
Generate Poisson-distributed unsigned ints.

curandStatus_t CURANDAPI curandGenerateSeeds (  curandGenerator_t generator )
Setup starting states.

curandStatus_t CURANDAPI curandGenerateUniform (  curandGenerator_t generator, float* outputPtr, size_t num )
Generate uniformly distributed floats.

curandStatus_t CURANDAPI curandGenerateUniformDouble (  curandGenerator_t generator, double* outputPtr, size_t num )
Generate uniformly distributed doubles.

curandStatus_t CURANDAPI curandGetDirectionVectors32 (  curandDirectionVectors32_t* vectors, curandDirectionVectorSet_t set )
Get direction vectors for 32-bit quasirandom number generation.

curandStatus_t CURANDAPI curandGetDirectionVectors64 (  curandDirectionVectors64_t* vectors, curandDirectionVectorSet_t set )
Get direction vectors for 64-bit quasirandom number generation.

curandStatus_t CURANDAPI curandGetProperty (  libraryPropertyType type, int* value )
Return the value of the curand property.

curandStatus_t CURANDAPI curandGetScrambleConstants32 (  unsigned int constants )
Get scramble constants for 32-bit scrambled Sobol' .

curandStatus_t CURANDAPI curandGetScrambleConstants64 (  unsigned long long constants )
Get scramble constants for 64-bit scrambled Sobol' .

curandStatus_t CURANDAPI curandGetVersion (  int* version )
Return the version number of the library.

curandStatus_t CURANDAPI curandSetGeneratorOffset (  curandGenerator_t generator, unsigned long long offset )
Set the absolute offset of the pseudo or quasirandom number generator.

curandStatus_t CURANDAPI curandSetGeneratorOrdering (  curandGenerator_t generator, curandOrdering_t order )
Set the ordering of results of the pseudo or quasirandom number generator.

curandStatus_t CURANDAPI curandSetPseudoRandomGeneratorSeed (  curandGenerator_t generator, unsigned long long seed )
Set the seed value of the pseudo-random number generator.

curandStatus_t CURANDAPI curandSetQuasiRandomGeneratorDimensions (  curandGenerator_t generator, unsigned int  num_dimensions )
Set the number of dimensions.

curandStatus_t CURANDAPI curandSetStream (  curandGenerator_t generator, cudaStream_t stream )
Set the current stream for CURAND kernel launches.


### Enumerations


enum HOST::curandDirectionVectorSet [inherited]
CURAND choice of direction vector set

                                 Values



CURAND_DIRECTION_VECTORS_32_JOEKUO6 = 101
Specific set of 32-bit direction vectors generated from polynomials recommended by S. Joe and F. Y. Kuo, for up to 20,000
                                    dimensions.

CURAND_SCRAMBLED_DIRECTION_VECTORS_32_JOEKUO6 = 102
Specific set of 32-bit direction vectors generated from polynomials recommended by S. Joe and F. Y. Kuo, for up to 20,000
                                    dimensions, and scrambled.

CURAND_DIRECTION_VECTORS_64_JOEKUO6 = 103
Specific set of 64-bit direction vectors generated from polynomials recommended by S. Joe and F. Y. Kuo, for up to 20,000
                                    dimensions.

CURAND_SCRAMBLED_DIRECTION_VECTORS_64_JOEKUO6 = 104
Specific set of 64-bit direction vectors generated from polynomials recommended by S. Joe and F. Y. Kuo, for up to 20,000
                                    dimensions, and scrambled.

enum HOST::curandOrdering [inherited]
CURAND ordering of results in memory

                                 Values



CURAND_ORDERING_PSEUDO_BEST = 100
Best ordering for pseudorandom results.
CURAND_ORDERING_PSEUDO_DEFAULT = 101
Specific default thread sequence for pseudorandom results, same as CURAND_ORDERING_PSEUDO_BEST.
CURAND_ORDERING_PSEUDO_SEEDED = 102
Specific seeding pattern for fast lower quality pseudorandom results.
CURAND_ORDERING_PSEUDO_LEGACY = 103
Specific legacy sequence for pseudorandom results, guaranteed to remain the same for all cuRAND release.
CURAND_ORDERING_PSEUDO_DYNAMIC = 104
Specific ordering adjusted to the device it is being executed on, provides the best performance.
CURAND_ORDERING_QUASI_DEFAULT = 201
Specific n-dimensional ordering for quasirandom results.

enum HOST::curandRngType [inherited]
CURAND generator types

                                 Values



CURAND_RNG_TEST = 0

CURAND_RNG_PSEUDO_DEFAULT = 100
Default pseudorandom generator.
CURAND_RNG_PSEUDO_XORWOW = 101
XORWOW pseudorandom generator.
CURAND_RNG_PSEUDO_MRG32K3A = 121
MRG32k3a pseudorandom generator.
CURAND_RNG_PSEUDO_MTGP32 = 141
Mersenne Twister MTGP32 pseudorandom generator.
CURAND_RNG_PSEUDO_MT19937 = 142
Mersenne Twister MT19937 pseudorandom generator.
CURAND_RNG_PSEUDO_PHILOX4_32_10 = 161
PHILOX-4x32-10 pseudorandom generator.
CURAND_RNG_QUASI_DEFAULT = 200
Default quasirandom generator.
CURAND_RNG_QUASI_SOBOL32 = 201
Sobol32 quasirandom generator.
CURAND_RNG_QUASI_SCRAMBLED_SOBOL32 = 202
Scrambled Sobol32 quasirandom generator.
CURAND_RNG_QUASI_SOBOL64 = 203
Sobol64 quasirandom generator.
CURAND_RNG_QUASI_SCRAMBLED_SOBOL64 = 204
Scrambled Sobol64 quasirandom generator.

enum HOST::curandStatus [inherited]
CURAND function call status types

                                 Values



CURAND_STATUS_SUCCESS = 0
No errors.
CURAND_STATUS_VERSION_MISMATCH = 100
Header file and linked library version do not match.
CURAND_STATUS_NOT_INITIALIZED = 101
Generator not initialized.
CURAND_STATUS_ALLOCATION_FAILED = 102
Memory allocation failed.
CURAND_STATUS_TYPE_ERROR = 103
Generator is wrong type.
CURAND_STATUS_OUT_OF_RANGE = 104
Argument out of range.
CURAND_STATUS_LENGTH_NOT_MULTIPLE = 105
Length requested is not a multple of dimension.
CURAND_STATUS_DOUBLE_PRECISION_REQUIRED = 106
GPU does not have double precision required by MRG32k3a.
CURAND_STATUS_LAUNCH_FAILURE = 201
Kernel launch failure.
CURAND_STATUS_PREEXISTING_FAILURE = 202
Preexisting failure on library entry.
CURAND_STATUS_INITIALIZATION_FAILED = 203
Initialization of CUDA failed.
CURAND_STATUS_ARCH_MISMATCH = 204
Architecture mismatch, GPU does not support requested feature.
CURAND_STATUS_INTERNAL_ERROR = 999
Internal library error.


### Functions


curandStatus_t CURANDAPI curandCreateGenerator (  curandGenerator_t* generator, curandRngType_t rng_type )
Create new random number generator.

                                 Parameters



generator
- Pointer to generator
rng_type
- Type of generator to create

Returns

CURAND_STATUS_ALLOCATION_FAILED, if memory could not be allocated


CURAND_STATUS_INITIALIZATION_FAILED if there was a problem setting up the GPU


CURAND_STATUS_VERSION_MISMATCH if the header file version does not match the dynamically linked library version


CURAND_STATUS_TYPE_ERROR if the value for rng_type is invalid


CURAND_STATUS_SUCCESS if generator was created successfully



Description
CURAND generator CURAND distribution CURAND distribution M2 Creates a new random number generator of type rng_type and returns it in *generator.

Legal values for rng_type are:


CURAND_RNG_PSEUDO_DEFAULT

CURAND_RNG_PSEUDO_XORWOW

CURAND_RNG_PSEUDO_MRG32K3A

CURAND_RNG_PSEUDO_MTGP32

CURAND_RNG_PSEUDO_MT19937

CURAND_RNG_PSEUDO_PHILOX4_32_10

CURAND_RNG_QUASI_DEFAULT

CURAND_RNG_QUASI_SOBOL32

CURAND_RNG_QUASI_SCRAMBLED_SOBOL32

CURAND_RNG_QUASI_SOBOL64

CURAND_RNG_QUASI_SCRAMBLED_SOBOL64

When rng_type is CURAND_RNG_PSEUDO_DEFAULT, the type chosen is CURAND_RNG_PSEUDO_XORWOW.
                                 When rng_type is CURAND_RNG_QUASI_DEFAULT, the type chosen is CURAND_RNG_QUASI_SOBOL32.

The default values for rng_type = CURAND_RNG_PSEUDO_XORWOW are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_PSEUDO_MRG32K3A are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_PSEUDO_MTGP32 are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_PSEUDO_MT19937 are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


* The default values for rng_type = CURAND_RNG_PSEUDO_PHILOX4_32_10 are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SOBOL32 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SOBOL64 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SCRAMBBLED_SOBOL32 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SCRAMBLED_SOBOL64 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT

curandStatus_t CURANDAPI curandCreateGeneratorHost (  curandGenerator_t* generator, curandRngType_t rng_type )
Create new host CPU random number generator.

                                 Parameters



generator
- Pointer to generator
rng_type
- Type of generator to create

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_INITIALIZATION_FAILED if there was a problem setting up the GPU


CURAND_STATUS_VERSION_MISMATCH if the header file version does not match the dynamically linked library version


CURAND_STATUS_TYPE_ERROR if the value for rng_type is invalid


CURAND_STATUS_SUCCESS if generator was created successfully



Description
Creates a new host CPU random number generator of type rng_type and returns it in *generator.

Legal values for rng_type are:


CURAND_RNG_PSEUDO_DEFAULT

CURAND_RNG_PSEUDO_XORWOW

CURAND_RNG_PSEUDO_MRG32K3A

CURAND_RNG_PSEUDO_MTGP32

CURAND_RNG_PSEUDO_MT19937

CURAND_RNG_PSEUDO_PHILOX4_32_10

CURAND_RNG_QUASI_DEFAULT

CURAND_RNG_QUASI_SOBOL32

CURAND_RNG_QUASI_SCRAMBLED_SOBOL32

CURAND_RNG_QUASI_SOBOL64

CURAND_RNG_QUASI_SCRAMBLED_SOBOL64

When rng_type is CURAND_RNG_PSEUDO_DEFAULT, the type chosen is CURAND_RNG_PSEUDO_XORWOW.
                                 When rng_type is CURAND_RNG_QUASI_DEFAULT, the type chosen is CURAND_RNG_QUASI_SOBOL32.

The default values for rng_type = CURAND_RNG_PSEUDO_XORWOW are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_PSEUDO_MRG32K3A are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_PSEUDO_MTGP32 are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_PSEUDO_MT19937 are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


* The default values for rng_type = CURAND_RNG_PSEUDO_PHILOX4_32_10 are:


seed = 0


offset = 0


ordering = CURAND_ORDERING_PSEUDO_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SOBOL32 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SOBOL64 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SCRAMBLED_SOBOL32 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT


The default values for rng_type = CURAND_RNG_QUASI_SCRAMBLED_SOBOL64 are:


dimensions = 1


offset = 0


ordering = CURAND_ORDERING_QUASI_DEFAULT

curandStatus_t CURANDAPI curandCreatePoissonDistribution (  double  lambda, curandDiscreteDistribution_t* discrete_distribution )
Construct the histogram array for a Poisson distribution.

                                 Parameters



lambda
- lambda for the Poisson distribution
discrete_distribution
- pointer to the histogram in device memory

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_DOUBLE_PRECISION_REQUIRED if the GPU does not support double precision


CURAND_STATUS_INITIALIZATION_FAILED if there was a problem setting up the GPU


CURAND_STATUS_NOT_INITIALIZED if the distribution pointer was null


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_OUT_OF_RANGE if lambda is non-positive or greater than 400,000


CURAND_STATUS_SUCCESS if the histogram was generated successfully



Description
Construct the histogram array for the Poisson distribution with lambda lambda. For lambda greater than 2000, an approximation with a normal distribution is used.

curandStatus_t CURANDAPI curandDestroyDistribution (  curandDiscreteDistribution_t discrete_distribution )
Destroy the histogram array for a discrete distribution (e.g. Poisson).

                                 Parameters



discrete_distribution
- pointer to device memory where the histogram is stored

Returns

CURAND_STATUS_NOT_INITIALIZED if the histogram was never created


CURAND_STATUS_SUCCESS if the histogram was destroyed successfully



Description
Destroy the histogram array for a discrete distribution created by curandCreatePoissonDistribution.

curandStatus_t CURANDAPI curandDestroyGenerator (  curandGenerator_t generator )
Destroy an existing generator.

                                 Parameters



generator
- Generator to destroy

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_SUCCESS if generator was destroyed successfully



Description
Destroy an existing generator and free all memory associated with its state.

curandStatus_t CURANDAPI curandGenerate (  curandGenerator_t generator, unsigned int* outputPtr, size_t num )
Generate 32-bit pseudo or quasirandom numbers.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
num
- Number of random 32-bit values to generate

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_TYPE_ERROR if the generator is a 64 bit quasirandom generator. (use curandGenerateLongLong() with 64 bit quasirandom generators)

CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate num 32-bit results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 32-bit values with every bit random.

curandStatus_t CURANDAPI curandGenerateLogNormal (  curandGenerator_t generator, float* outputPtr, size_t n, float  mean, float  stddev )
Generate log-normally distributed floats.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
n
- Number of floats to generate
mean
- Mean of associated normal distribution
stddev
- Standard deviation of associated normal distribution

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension, or is not
                                       a multiple of two for pseudorandom generators


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate n float results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 32-bit floating point values with log-normal distribution based on an associated normal distribution with mean
                                 mean and standard deviation stddev.

Normally distributed results are generated from pseudorandom generators with a Box-Muller transform, and so require n to be even. Quasirandom generators use an inverse cumulative distribution function to preserve dimensionality. The normally
                                 distributed results are transformed into log-normal distribution.

There may be slight numerical differences between results generated on the GPU with generators created with curandCreateGenerator() and results calculated on the CPU with generators created with curandCreateGeneratorHost(). These differences arise because of differences in results for transcendental functions. In addition, future versions of
                                 CURAND may use newer versions of the CUDA math library, so different versions of CURAND may give slightly different numerical
                                 values.

curandStatus_t CURANDAPI curandGenerateLogNormalDouble (  curandGenerator_t generator, double* outputPtr, size_t n, double  mean, double  stddev )
Generate log-normally distributed doubles.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
n
- Number of doubles to generate
mean
- Mean of normal distribution
stddev
- Standard deviation of normal distribution

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension, or is not
                                       a multiple of two for pseudorandom generators


CURAND_STATUS_DOUBLE_PRECISION_REQUIRED if the GPU does not support double precision


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate n double results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 64-bit floating point values with log-normal distribution based on an associated normal distribution with mean
                                 mean and standard deviation stddev.

Normally distributed results are generated from pseudorandom generators with a Box-Muller transform, and so require n to be even. Quasirandom generators use an inverse cumulative distribution function to preserve dimensionality. The normally
                                 distributed results are transformed into log-normal distribution.

There may be slight numerical differences between results generated on the GPU with generators created with curandCreateGenerator() and results calculated on the CPU with generators created with curandCreateGeneratorHost(). These differences arise because of differences in results for transcendental functions. In addition, future versions of
                                 CURAND may use newer versions of the CUDA math library, so different versions of CURAND may give slightly different numerical
                                 values.

curandStatus_t CURANDAPI curandGenerateLongLong (  curandGenerator_t generator, unsigned long long* outputPtr, size_t num )
Generate 64-bit quasirandom numbers.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
num
- Number of random 64-bit values to generate

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_TYPE_ERROR if the generator is not a 64 bit quasirandom generator


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate num 64-bit results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 64-bit values with every bit random.

curandStatus_t CURANDAPI curandGenerateNormal (  curandGenerator_t generator, float* outputPtr, size_t n, float  mean, float  stddev )
Generate normally distributed doubles.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
n
- Number of floats to generate
mean
- Mean of normal distribution
stddev
- Standard deviation of normal distribution

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension, or is not
                                       a multiple of two for pseudorandom generators


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate n float results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 32-bit floating point values with mean mean and standard deviation stddev.

Normally distributed results are generated from pseudorandom generators with a Box-Muller transform, and so require n to be even. Quasirandom generators use an inverse cumulative distribution function to preserve dimensionality.

There may be slight numerical differences between results generated on the GPU with generators created with curandCreateGenerator() and results calculated on the CPU with generators created with curandCreateGeneratorHost(). These differences arise because of differences in results for transcendental functions. In addition, future versions of
                                 CURAND may use newer versions of the CUDA math library, so different versions of CURAND may give slightly different numerical
                                 values.

curandStatus_t CURANDAPI curandGenerateNormalDouble (  curandGenerator_t generator, double* outputPtr, size_t n, double  mean, double  stddev )
Generate normally distributed doubles.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
n
- Number of doubles to generate
mean
- Mean of normal distribution
stddev
- Standard deviation of normal distribution

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension, or is not
                                       a multiple of two for pseudorandom generators


CURAND_STATUS_DOUBLE_PRECISION_REQUIRED if the GPU does not support double precision


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate n double results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 64-bit floating point values with mean mean and standard deviation stddev.

Normally distributed results are generated from pseudorandom generators with a Box-Muller transform, and so require n to be even. Quasirandom generators use an inverse cumulative distribution function to preserve dimensionality.

There may be slight numerical differences between results generated on the GPU with generators created with curandCreateGenerator() and results calculated on the CPU with generators created with curandCreateGeneratorHost(). These differences arise because of differences in results for transcendental functions. In addition, future versions of
                                 CURAND may use newer versions of the CUDA math library, so different versions of CURAND may give slightly different numerical
                                 values.

curandStatus_t CURANDAPI curandGeneratePoisson (  curandGenerator_t generator, unsigned int* outputPtr, size_t n, double  lambda )
Generate Poisson-distributed unsigned ints.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
n
- Number of unsigned ints to generate
lambda
- lambda for the Poisson distribution

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension


CURAND_STATUS_DOUBLE_PRECISION_REQUIRED if the GPU or sm does not support double precision


CURAND_STATUS_OUT_OF_RANGE if lambda is non-positive or greater than 400,000


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate n unsigned int results into device memory at outputPtr. The device memory must have been previously allocated and must be large enough to hold all the results. Launches are done
                                 with the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 32-bit unsigned int point values with Poisson distribution, with lambda lambda.

curandStatus_t CURANDAPI curandGenerateSeeds (  curandGenerator_t generator )
Setup starting states.

                                 Parameters



generator
- Generator to update

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_SUCCESS if the seeds were generated successfully



Description
Generate the starting state of the generator. This function is automatically called by generation functions such as curandGenerate() and curandGenerateUniform(). It can be called manually for performance testing reasons to separate timings for starting state generation and random number
                                 generation.

curandStatus_t CURANDAPI curandGenerateUniform (  curandGenerator_t generator, float* outputPtr, size_t num )
Generate uniformly distributed floats.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
num
- Number of floats to generate

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate num float results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 32-bit floating point values between 0.0f and 1.0f, excluding 0.0f and including 1.0f.

curandStatus_t CURANDAPI curandGenerateUniformDouble (  curandGenerator_t generator, double* outputPtr, size_t num )
Generate uniformly distributed doubles.

                                 Parameters



generator
- Generator to use
outputPtr
- Pointer to device memory to store CUDA-generated results, or Pointer to host memory to store CPU-generated results
num
- Number of doubles to generate

Returns

CURAND_STATUS_ALLOCATION_FAILED if memory could not be allocated


CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_PREEXISTING_FAILURE if there was an existing error from a previous kernel launch


CURAND_STATUS_LAUNCH_FAILURE if the kernel launch failed for any reason


CURAND_STATUS_LENGTH_NOT_MULTIPLE if the number of output samples is not a multiple of the quasirandom dimension


CURAND_STATUS_DOUBLE_PRECISION_REQUIRED if the GPU does not support double precision


CURAND_STATUS_SUCCESS if the results were generated successfully



Description
Use generator to generate num double results into the device memory at outputPtr. The device memory must have been previously allocated and be large enough to hold all the results. Launches are done with
                                 the stream set using curandSetStream(), or the null stream if no stream has been set.

Results are 64-bit double precision floating point values between 0.0 and 1.0, excluding 0.0 and including 1.0.

curandStatus_t CURANDAPI curandGetDirectionVectors32 (  curandDirectionVectors32_t* vectors, curandDirectionVectorSet_t set )
Get direction vectors for 32-bit quasirandom number generation.

                                 Parameters



vectors
- Address of pointer in which to return direction vectors
set
- Which set of direction vectors to use

Returns

CURAND_STATUS_OUT_OF_RANGE if the choice of set is invalid


CURAND_STATUS_SUCCESS if the pointer was set successfully



Description
Get a pointer to an array of direction vectors that can be used for quasirandom number generation. The resulting pointer will
                                 reference an array of direction vectors in host memory.

The array contains vectors for many dimensions. Each dimension has 32 vectors. Each individual vector is an unsigned int.
Legal values for set are:


CURAND_DIRECTION_VECTORS_32_JOEKUO6 (20,000 dimensions)

CURAND_SCRAMBLED_DIRECTION_VECTORS_32_JOEKUO6 (20,000 dimensions)

curandStatus_t CURANDAPI curandGetDirectionVectors64 (  curandDirectionVectors64_t* vectors, curandDirectionVectorSet_t set )
Get direction vectors for 64-bit quasirandom number generation.

                                 Parameters



vectors
- Address of pointer in which to return direction vectors
set
- Which set of direction vectors to use

Returns

CURAND_STATUS_OUT_OF_RANGE if the choice of set is invalid


CURAND_STATUS_SUCCESS if the pointer was set successfully



Description
Get a pointer to an array of direction vectors that can be used for quasirandom number generation. The resulting pointer will
                                 reference an array of direction vectors in host memory.

The array contains vectors for many dimensions. Each dimension has 64 vectors. Each individual vector is an unsigned long
                                 long.

Legal values for set are:


CURAND_DIRECTION_VECTORS_64_JOEKUO6 (20,000 dimensions)

CURAND_SCRAMBLED_DIRECTION_VECTORS_64_JOEKUO6 (20,000 dimensions)

curandStatus_t CURANDAPI curandGetProperty (  libraryPropertyType type, int* value )
Return the value of the curand property.

                                 Parameters



type
- CUDA library property
value
- integer value for the requested property

Returns

CURAND_STATUS_SUCCESS if the property value was successfully returned


CURAND_STATUS_OUT_OF_RANGE if the property type is not recognized



Description
Return in *value the number for the property described by type of the dynamically linked CURAND library.

curandStatus_t CURANDAPI curandGetScrambleConstants32 (  unsigned int constants )
Get scramble constants for 32-bit scrambled Sobol' .

                                 Parameters



constants
- Address of pointer in which to return scramble constants

Returns

CURAND_STATUS_SUCCESS if the pointer was set successfully



Description
Get a pointer to an array of scramble constants that can be used for quasirandom number generation. The resulting pointer
                                 will reference an array of unsinged ints in host memory.

The array contains constants for many dimensions. Each dimension has a single unsigned int constant.

curandStatus_t CURANDAPI curandGetScrambleConstants64 (  unsigned long long constants )
Get scramble constants for 64-bit scrambled Sobol' .

                                 Parameters



constants
- Address of pointer in which to return scramble constants

Returns

CURAND_STATUS_SUCCESS if the pointer was set successfully



Description
Get a pointer to an array of scramble constants that can be used for quasirandom number generation. The resulting pointer
                                 will reference an array of unsinged long longs in host memory.

The array contains constants for many dimensions. Each dimension has a single unsigned long long constant.

curandStatus_t CURANDAPI curandGetVersion (  int* version )
Return the version number of the library.

                                 Parameters



version
- CURAND library version

Returns

CURAND_STATUS_SUCCESS if the version number was successfully returned



Description
Return in *version the version number of the dynamically linked CURAND library. The format is the same as CUDART_VERSION from the CUDA Runtime.
                                 The only supported configuration is CURAND version equal to CUDA Runtime version.

curandStatus_t CURANDAPI curandSetGeneratorOffset (  curandGenerator_t generator, unsigned long long offset )
Set the absolute offset of the pseudo or quasirandom number generator.

                                 Parameters



generator
- Generator to modify
offset
- Absolute offset position

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_SUCCESS if generator offset was set successfully



Description
Set the absolute offset of the pseudo or quasirandom number generator.
All values of offset are valid. The offset position is absolute, not relative to the current position in the sequence.

curandStatus_t CURANDAPI curandSetGeneratorOrdering (  curandGenerator_t generator, curandOrdering_t order )
Set the ordering of results of the pseudo or quasirandom number generator.

                                 Parameters



generator
- Generator to modify
order
- Ordering of results

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_OUT_OF_RANGE if the ordering is not valid


CURAND_STATUS_SUCCESS if generator ordering was set successfully



Description
Set the ordering of results of the pseudo or quasirandom number generator.
Legal values of order for pseudorandom generators are:


CURAND_ORDERING_PSEUDO_DEFAULT

CURAND_ORDERING_PSEUDO_BEST

CURAND_ORDERING_PSEUDO_SEEDED

CURAND_ORDERING_PSEUDO_LEGACY

Legal values of order for quasirandom generators are:


CURAND_ORDERING_QUASI_DEFAULT

curandStatus_t CURANDAPI curandSetPseudoRandomGeneratorSeed (  curandGenerator_t generator, unsigned long long seed )
Set the seed value of the pseudo-random number generator.

                                 Parameters



generator
- Generator to modify
seed
- Seed value

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_TYPE_ERROR if the generator is not a pseudorandom number generator


CURAND_STATUS_SUCCESS if generator seed was set successfully



Description
Set the seed value of the pseudorandom number generator. All values of seed are valid. Different seeds will produce different
                                 sequences. Different seeds will often not be statistically correlated with each other, but some pairs of seed values may generate
                                 sequences which are statistically correlated.

curandStatus_t CURANDAPI curandSetQuasiRandomGeneratorDimensions (  curandGenerator_t generator, unsigned int  num_dimensions )
Set the number of dimensions.

                                 Parameters



generator
- Generator to modify
num_dimensions
- Number of dimensions

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_OUT_OF_RANGE if num_dimensions is not valid


CURAND_STATUS_TYPE_ERROR if the generator is not a quasirandom number generator


CURAND_STATUS_SUCCESS if generator ordering was set successfully



Description
Set the number of dimensions to be generated by the quasirandom number generator.
Legal values for num_dimensions are 1 to 20000.

curandStatus_t CURANDAPI curandSetStream (  curandGenerator_t generator, cudaStream_t stream )
Set the current stream for CURAND kernel launches.

                                 Parameters



generator
- Generator to modify
stream
- Stream to use or NULL for null stream

Returns

CURAND_STATUS_NOT_INITIALIZED if the generator was never created


CURAND_STATUS_SUCCESS if stream was set successfully



Description
Set the current stream for CURAND kernel launches. All library functions will use this stream until set again.


---