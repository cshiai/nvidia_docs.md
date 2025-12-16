# cuRAND

[< Previous](group__HOST.html) | [Next >](bibliography.html)  cuRAND ([PDF](https://docs.nvidia.com/cuda/pdf/CURAND_Library.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20cuRAND)
## 5.2. Device API




### Namespaces


namespace curand_detail

### Functions


__device__
                           ​ unsigned int curand (  curandStateMtgp32_t* state )
Return 32-bits of pseudorandomness from a mtgp32 generator.

__device__
                           ​ unsigned long long curand (  curandStateScrambledSobol64_t* state )
Return 64-bits of quasirandomness from a scrambled Sobol64 generator.

__device__
                           ​ unsigned long long curand (  curandStateSobol64_t* state )
Return 64-bits of quasirandomness from a Sobol64 generator.

__device__
                           ​ unsigned int curand (  curandStateScrambledSobol32_t* state )
Return 32-bits of quasirandomness from a scrambled Sobol32 generator.

__device__
                           ​ unsigned int curand (  curandStateSobol32_t* state )
Return 32-bits of quasirandomness from a Sobol32 generator.

__device__
                           ​ unsigned int curand (  curandStateMRG32k3a_t* state )
Return 32-bits of pseudorandomness from an MRG32k3a generator.

__device__
                           ​ unsigned int curand (  curandStatePhilox4_32_10_t* state )
Return 32-bits of pseudorandomness from an Philox4_32_10 generator.

__device__
                           ​ unsigned int curand (  curandStateXORWOW_t* state )
Return 32-bits of pseudorandomness from an XORWOW generator.

__device__
                           ​ uint4 curand4 (  curandStatePhilox4_32_10_t* state )
Return tuple of 4 32-bit pseudorandoms from a Philox4_32_10 generator.

__host__
                           ​__forceinline__  curandStatus_t curandMakeMTGP32Constants (  const mtgp32_params_fast_t params[], mtgp32_kernel_params_t* p )
Set up constant parameters for the mtgp32 generator.

__host__
                           ​__forceinline__  curandStatus_t CURANDAPI curandMakeMTGP32KernelState (  curandStateMtgp32_t* s, mtgp32_params_fast_t params[], mtgp32_kernel_params_t* k, int  n, unsigned long long seed )
Set up initial states for the mtgp32 generator.

__device__
                           ​ void curand_init (  curandDirectionVectors64_t direction_vectors, unsigned long long scramble_c, unsigned long long offset, curandStateScrambledSobol64_t* state )
Initialize Scrambled Sobol64 state.

__device__
                           ​ void curand_init (  curandDirectionVectors64_t direction_vectors, unsigned long long offset, curandStateSobol64_t* state )
Initialize Sobol64 state.

__device__
                           ​ void curand_init (  curandDirectionVectors32_t direction_vectors, unsigned int  scramble_c, unsigned int  offset, curandStateScrambledSobol32_t* state )
Initialize Scrambled Sobol32 state.

__device__
                           ​ void curand_init (  curandDirectionVectors32_t direction_vectors, unsigned int  offset, curandStateSobol32_t* state )
Initialize Sobol32 state.

__device__
                           ​ void curand_init (  unsigned long long seed, unsigned long long subsequence, unsigned long long offset, curandStateMRG32k3a_t* state )
Initialize MRG32k3a state.

__device__
                           ​ void curand_init (  unsigned long long seed, unsigned long long subsequence, unsigned long long offset, curandStatePhilox4_32_10_t* state )
Initialize Philox4_32_10 state.

__device__
                           ​ void curand_init (  unsigned long long seed, unsigned long long subsequence, unsigned long long offset, curandStateXORWOW_t* state )
Initialize XORWOW state.

__device__
                           ​ float curand_log_normal (  curandStateScrambledSobol64_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a scrambled Sobol64 generator.

__device__
                           ​ float curand_log_normal (  curandStateSobol64_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a Sobol64 generator.

__device__
                           ​ float curand_log_normal (  curandStateScrambledSobol32_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a scrambled Sobol32 generator.

__device__
                           ​ float curand_log_normal (  curandStateSobol32_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a Sobol32 generator.

__device__
                           ​ float curand_log_normal (  curandStateMtgp32_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an MTGP32 generator.

__device__
                           ​ float curand_log_normal (  curandStateMRG32k3a_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an MRG32k3a generator.

__device__
                           ​ float curand_log_normal (  curandStatePhilox4_32_10_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an Philox4_32_10 generator.

__device__
                           ​ float curand_log_normal (  curandStateXORWOW_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an XORWOW generator.

__device__
                           ​ float2 curand_log_normal2 (  curandStateMRG32k3a_t* state, float  mean, float  stddev )
Return two normally distributed floats from an MRG32k3a generator.

__device__
                           ​ float2 curand_log_normal2 (  curandStatePhilox4_32_10_t* state, float  mean, float  stddev )
Return two normally distributed floats from an Philox4_32_10 generator.

__device__
                           ​ float2 curand_log_normal2 (  curandStateXORWOW_t* state, float  mean, float  stddev )
Return two normally distributed floats from an XORWOW generator.

__device__
                           ​ double2 curand_log_normal2_double (  curandStateMRG32k3a_t* state, double  mean, double  stddev )
Return two log-normally distributed doubles from an MRG32k3a generator.

__device__
                           ​ double2 curand_log_normal2_double (  curandStatePhilox4_32_10_t* state, double  mean, double  stddev )
Return two log-normally distributed doubles from an Philox4_32_10 generator.

__device__
                           ​ double2 curand_log_normal2_double (  curandStateXORWOW_t* state, double  mean, double  stddev )
Return two log-normally distributed doubles from an XORWOW generator.

__device__
                           ​ float4 curand_log_normal4 (  curandStatePhilox4_32_10_t* state, float  mean, float  stddev )
Return four normally distributed floats from an Philox4_32_10 generator.

__device__
                           ​ double curand_log_normal_double (  curandStateScrambledSobol64_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a scrambled Sobol64 generator.

__device__
                           ​ double curand_log_normal_double (  curandStateSobol64_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a Sobol64 generator.

__device__
                           ​ double curand_log_normal_double (  curandStateScrambledSobol32_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a scrambled Sobol32 generator.

__device__
                           ​ double curand_log_normal_double (  curandStateSobol32_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a Sobol32 generator.

__device__
                           ​ double curand_log_normal_double (  curandStateMtgp32_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an MTGP32 generator.

__device__
                           ​__NV_SILENCE_DEPRECATION_END  double curand_log_normal_double (  curandStateMRG32k3a_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an MRG32k3a generator.

__device__
                           ​ double curand_log_normal_double (  curandStatePhilox4_32_10_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an Philox4_32_10 generator.

__device__
                           ​ double curand_log_normal_double (  curandStateXORWOW_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an XORWOW generator.

__device__
                           ​ float curand_mtgp32_single (  curandStateMtgp32_t* state )
Return a uniformly distributed float from a mtgp32 generator.

__device__
                           ​ float curand_mtgp32_single_specific (  curandStateMtgp32_t* state, unsigned char  index, unsigned char  n )
Return a uniformly distributed float from a specific position in a mtgp32 generator.

__device__
                           ​ unsigned int curand_mtgp32_specific (  curandStateMtgp32_t* state, unsigned char  index, unsigned char  n )
Return 32-bits of pseudorandomness from a specific position in a mtgp32 generator.

__device__
                           ​ float curand_normal (  curandStateScrambledSobol64_t* state )
Return a normally distributed float from a scrambled Sobol64 generator.

__device__
                           ​ float curand_normal (  curandStateSobol64_t* state )
Return a normally distributed float from a Sobol64 generator.

__device__
                           ​ float curand_normal (  curandStateScrambledSobol32_t* state )
Return a normally distributed float from a scrambled Sobol32 generator.

__device__
                           ​ float curand_normal (  curandStateSobol32_t* state )
Return a normally distributed float from a Sobol32 generator.

__device__
                           ​ float curand_normal (  curandStateMtgp32_t* state )
Return a normally distributed float from a MTGP32 generator.

__device__
                           ​ float curand_normal (  curandStateMRG32k3a_t* state )
Return a normally distributed float from an MRG32k3a generator.

__device__
                           ​ float curand_normal (  curandStatePhilox4_32_10_t* state )
Return a normally distributed float from an Philox4_32_10 generator.

__device__
                           ​__NV_SILENCE_DEPRECATION_END  float curand_normal (  curandStateXORWOW_t* state )
Return a normally distributed float from an XORWOW generator.

__device__
                           ​ float2 curand_normal2 (  curandStateMRG32k3a_t* state )
Return two normally distributed floats from an MRG32k3a generator.

__device__
                           ​ float2 curand_normal2 (  curandStatePhilox4_32_10_t* state )
Return two normally distributed floats from an Philox4_32_10 generator.

__device__
                           ​ float2 curand_normal2 (  curandStateXORWOW_t* state )
Return two normally distributed floats from an XORWOW generator.

__device__
                           ​__NV_SILENCE_DEPRECATION_END  double2 curand_normal2_double (  curandStateMRG32k3a_t* state )
Return two normally distributed doubles from an MRG32k3a generator.

__device__
                           ​ double2 curand_normal2_double (  curandStatePhilox4_32_10_t* state )
Return two normally distributed doubles from an Philox4_32_10 generator.

__device__
                           ​ double2 curand_normal2_double (  curandStateXORWOW_t* state )
Return two normally distributed doubles from an XORWOW generator.

__device__
                           ​ float4 curand_normal4 (  curandStatePhilox4_32_10_t* state )
Return four normally distributed floats from an Philox4_32_10 generator.

__device__
                           ​ double curand_normal_double (  curandStateScrambledSobol64_t* state )
Return a normally distributed double from a scrambled Sobol64 generator.

__device__
                           ​ double curand_normal_double (  curandStateSobol64_t* state )
Return a normally distributed double from a Sobol64 generator.

__device__
                           ​ double curand_normal_double (  curandStateScrambledSobol32_t* state )
Return a normally distributed double from a scrambled Sobol32 generator.

__device__
                           ​ double curand_normal_double (  curandStateSobol32_t* state )
Return a normally distributed double from an Sobol32 generator.

__device__
                           ​ double curand_normal_double (  curandStateMtgp32_t* state )
Return a normally distributed double from an MTGP32 generator.

__device__
                           ​ double curand_normal_double (  curandStateMRG32k3a_t* state )
Return a normally distributed double from an MRG32k3a generator.

__device__
                           ​ double curand_normal_double (  curandStatePhilox4_32_10_t* state )
Return a normally distributed double from an Philox4_32_10 generator.

__device__
                           ​ double curand_normal_double (  curandStateXORWOW_t* state )
Return a normally distributed double from an XORWOW generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateScrambledSobol64_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a scrambled Sobol64 generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateSobol64_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a Sobol64 generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateScrambledSobol32_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a scrambled Sobol32 generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateSobol32_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a Sobol32 generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateMtgp32_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a MTGP32 generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateMRG32k3a_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a MRG32k3A generator.

__device__
                           ​ unsigned int curand_poisson (  curandStatePhilox4_32_10_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a Philox4_32_10 generator.

__device__
                           ​ unsigned int curand_poisson (  curandStateXORWOW_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a XORWOW generator.

__device__
                           ​ uint4 curand_poisson4 (  curandStatePhilox4_32_10_t* state, double  lambda )
Return four Poisson-distributed unsigned ints from a Philox4_32_10 generator.

__device__
                           ​ float curand_uniform (  curandStateScrambledSobol64_t* state )
Return a uniformly distributed float from a scrambled Sobol64 generator.

__device__
                           ​ float curand_uniform (  curandStateSobol64_t* state )
Return a uniformly distributed float from a Sobol64 generator.

__device__
                           ​ float curand_uniform (  curandStateScrambledSobol32_t* state )
Return a uniformly distributed float from a scrambled Sobol32 generator.

__device__
                           ​ float curand_uniform (  curandStateSobol32_t* state )
Return a uniformly distributed float from a Sobol32 generator.

__device__
                           ​ float curand_uniform (  curandStateMtgp32_t* state )
Return a uniformly distributed float from a MTGP32 generator.

__device__
                           ​__NV_SILENCE_DEPRECATION_END  float curand_uniform (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed float from a Philox4_32_10 generator.

__device__
                           ​ float curand_uniform (  curandStateMRG32k3a_t* state )
Return a uniformly distributed float from an MRG32k3a generator.

__device__
                           ​ float curand_uniform (  curandStateXORWOW_t* state )
Return a uniformly distributed float from an XORWOW generator.

__device__
                           ​ double2 curand_uniform2_double (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed tuple of 2 doubles from an Philox4_32_10 generator.

__device__
                           ​ float4 curand_uniform4 (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed tuple of 4 floats from a Philox4_32_10 generator.

__device__
                           ​ double curand_uniform_double (  curandStateScrambledSobol64_t* state )
Return a uniformly distributed double from a scrambled Sobol64 generator.

__device__
                           ​ double curand_uniform_double (  curandStateSobol64_t* state )
Return a uniformly distributed double from a Sobol64 generator.

__device__
                           ​ double curand_uniform_double (  curandStateScrambledSobol32_t* state )
Return a uniformly distributed double from a scrambled Sobol32 generator.

__device__
                           ​ double curand_uniform_double (  curandStateSobol32_t* state )
Return a uniformly distributed double from a Sobol32 generator.

__device__
                           ​ double curand_uniform_double (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed double from a Philox4_32_10 generator.

__device__
                           ​ double curand_uniform_double (  curandStateMtgp32_t* state )
Return a uniformly distributed double from a MTGP32 generator.

__device__
                           ​ double curand_uniform_double (  curandStateMRG32k3a_t* state )
Return a uniformly distributed double from an MRG32k3a generator.

__device__
                           ​ double curand_uniform_double (  curandStateXORWOW_t* state )
Return a uniformly distributed double from an XORWOW generator.

template < typename T >__device__
                           ​ CURAND_STD::​enable_if < CURAND_STD::​is_same &lt; curandStateSobol64_t* > ::type skipahead (  unsigned long long n, T state )
Update Sobol64 state to skip n elements.

template < typename T >__device__
                           ​ CURAND_STD::​enable_if < CURAND_STD::​is_same &lt; curandStateSobol32_t* > ::type skipahead (  unsigned int  n, T state )
Update Sobol32 state to skip n elements.

__device__
                           ​ void skipahead (  unsigned long long n, curandStateMRG32k3a_t* state )
Update MRG32k3a state to skip n elements.

__device__
                           ​ void skipahead (  unsigned long long n, curandStatePhilox4_32_10_t* state )
Update Philox4_32_10 state to skip n elements.

__device__
                           ​ void skipahead (  unsigned long long n, curandStateXORWOW_t* state )
Update XORWOW state to skip n elements.

__device__
                           ​ void skipahead_sequence (  unsigned long long n, curandStateMRG32k3a_t* state )
Update MRG32k3a state to skip ahead n sequences.

__device__
                           ​ void skipahead_sequence (  unsigned long long n, curandStatePhilox4_32_10_t* state )
Update Philox4_32_10 state to skip ahead n subsequences.

__device__
                           ​ void skipahead_sequence (  unsigned long long n, curandStateXORWOW_t* state )
Update XORWOW state to skip ahead n subsequences.

__device__
                           ​ void skipahead_subsequence (  unsigned long long n, curandStateMRG32k3a_t* state )
Update MRG32k3a state to skip ahead n subsequences.


### Functions


__device__
                              ​ unsigned int curand (  curandStateMtgp32_t* state )
Return 32-bits of pseudorandomness from a mtgp32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
32-bits of pseudorandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of pseudorandomness from the mtgp32 generator in state, increment position of generator by the number of threads in the block. Note the number of threads in the block can not exceed
                                 256.

__device__
                              ​ unsigned long long curand (  curandStateScrambledSobol64_t* state )
Return 64-bits of quasirandomness from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
64-bits of quasirandomness as an unsigned long long, all bits valid to use.

Description
Return 64-bits of quasirandomness from the scrambled Sobol32 generator in state, increment position of generator by one.

__device__
                              ​ unsigned long long curand (  curandStateSobol64_t* state )
Return 64-bits of quasirandomness from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
64-bits of quasirandomness as an unsigned long long, all bits valid to use.

Description
Return 64-bits of quasirandomness from the Sobol64 generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand (  curandStateScrambledSobol32_t* state )
Return 32-bits of quasirandomness from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
32-bits of quasirandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of quasirandomness from the scrambled Sobol32 generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand (  curandStateSobol32_t* state )
Return 32-bits of quasirandomness from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
32-bits of quasirandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of quasirandomness from the Sobol32 generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand (  curandStateMRG32k3a_t* state )
Return 32-bits of pseudorandomness from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
32-bits of pseudorandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of pseudorandomness from the MRG32k3a generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand (  curandStatePhilox4_32_10_t* state )
Return 32-bits of pseudorandomness from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
32-bits of pseudorandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of pseudorandomness from the Philox4_32_10 generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand (  curandStateXORWOW_t* state )
Return 32-bits of pseudorandomness from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
32-bits of pseudorandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of pseudorandomness from the XORWOW generator in state, increment position of generator by one.

__device__
                              ​ uint4 curand4 (  curandStatePhilox4_32_10_t* state )
Return tuple of 4 32-bit pseudorandoms from a Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
128-bits of pseudorandomness as a uint4, all bits valid to use.

Description
Return 128 bits of pseudorandomness from the Philox4_32_10 generator in state, increment position of generator by four.

__host__
                              ​__forceinline__  curandStatus_t curandMakeMTGP32Constants (  const mtgp32_params_fast_t params[], mtgp32_kernel_params_t* p )
Set up constant parameters for the mtgp32 generator.

                                 Parameters



params
- Pointer to an array of type mtgp32_params_fast_t in host memory
p
- pointer to a structure of type mtgp32_kernel_params_t in device memory.

Returns

CURAND_STATUS_ALLOCATION_FAILED if host memory could not be allocated
CURAND_STATUS_INITIALIZATION_FAILED if the copy to device memory failed
CURAND_STATUS_SUCCESS otherwise

Description
This host-side helper function re-organizes CURAND_NUM_MTGP32_PARAMS sets of generator parameters for use by kernel functions
                                 and copies the result to the specified location in device memory.

__host__
                              ​__forceinline__  curandStatus_t CURANDAPI curandMakeMTGP32KernelState (  curandStateMtgp32_t* s, mtgp32_params_fast_t params[], mtgp32_kernel_params_t* k, int  n, unsigned long long seed )
Set up initial states for the mtgp32 generator.

                                 Parameters



s
- pointer to an array of states in device memory
params
- Pointer to an array of type mtgp32_params_fast_t in host memory
k
- pointer to a structure of type mtgp32_kernel_params_t in device memory
n
- number of parameter sets/states to initialize
seed
- seed value

Returns

CURAND_STATUS_ALLOCATION_FAILED if host memory state could not be allocated
CURAND_STATUS_INITIALIZATION_FAILED if the copy to device memory failed
CURAND_STATUS_SUCCESS otherwise

Description
This host-side helper function initializes a number of states (one parameter set per state) for an mtgp32 generator. To accomplish
                                 this it allocates a state array in host memory, initializes that array, and copies the result to device memory.

__device__
                              ​ void curand_init (  curandDirectionVectors64_t direction_vectors, unsigned long long scramble_c, unsigned long long offset, curandStateScrambledSobol64_t* state )
Initialize Scrambled Sobol64 state.

                                 Parameters



direction_vectors
- Pointer to array of 64 unsigned long longs representing the direction vectors for the desired dimension
scramble_c
Scramble constant
offset
- Absolute offset into sequence
state
- Pointer to state to initialize

Description
Initialize Sobol64 state in state with the given directionvectors and offset.

The direction vector is a device pointer to an array of 64 unsigned long longs. All input values of offset are legal.

__device__
                              ​ void curand_init (  curandDirectionVectors64_t direction_vectors, unsigned long long offset, curandStateSobol64_t* state )
Initialize Sobol64 state.

                                 Parameters



direction_vectors
- Pointer to array of 64 unsigned long longs representing the direction vectors for the desired dimension
offset
- Absolute offset into sequence
state
- Pointer to state to initialize

Description
Initialize Sobol64 state in state with the given directionvectors and offset.

The direction vector is a device pointer to an array of 64 unsigned long longs. All input values of offset are legal.

__device__
                              ​ void curand_init (  curandDirectionVectors32_t direction_vectors, unsigned int  scramble_c, unsigned int  offset, curandStateScrambledSobol32_t* state )
Initialize Scrambled Sobol32 state.

                                 Parameters



direction_vectors
- Pointer to array of 32 unsigned ints representing the direction vectors for the desired dimension
scramble_c
Scramble constant
offset
- Absolute offset into sequence
state
- Pointer to state to initialize

Description
Initialize Sobol32 state in state with the given directionvectors and offset.

The direction vector is a device pointer to an array of 32 unsigned ints. All input values of offset are legal.

__device__
                              ​ void curand_init (  curandDirectionVectors32_t direction_vectors, unsigned int  offset, curandStateSobol32_t* state )
Initialize Sobol32 state.

                                 Parameters



direction_vectors
- Pointer to array of 32 unsigned ints representing the direction vectors for the desired dimension
offset
- Absolute offset into sequence
state
- Pointer to state to initialize

Description
Initialize Sobol32 state in state with the given directionvectors and offset.

The direction vector is a device pointer to an array of 32 unsigned ints. All input values of offset are legal.

__device__
                              ​ void curand_init (  unsigned long long seed, unsigned long long subsequence, unsigned long long offset, curandStateMRG32k3a_t* state )
Initialize MRG32k3a state.

                                 Parameters



seed
- Arbitrary bits to use as a seed
subsequence
- Subsequence to start at
offset
- Absolute offset into sequence
state
- Pointer to state to initialize

Description
Initialize MRG32k3a state in state with the given seed, subsequence, and offset.

All input values of seed, subsequence, and offset are legal. subsequence will be truncated to 51 bits to avoid running into the next sequence

A value of 0 for seed sets the state to the values of the original published version of the MRG32k3a algorithm.

__device__
                              ​ void curand_init (  unsigned long long seed, unsigned long long subsequence, unsigned long long offset, curandStatePhilox4_32_10_t* state )
Initialize Philox4_32_10 state.

                                 Parameters



seed
- Arbitrary bits to use as a seed
subsequence
- Subsequence to start at
offset
- Absolute offset into subsequence
state
- Pointer to state to initialize

Description
Initialize Philox4_32_10 state in state with the given seed, p\ subsequence, and offset.

All input values for seed, subseqence and offset are legal. Each of the  264 possible values of seed selects an independent sequence of length  2130. The first  266 * subsequence + offset. values of the sequence are skipped. I.e., subsequences are of length  266.

__device__
                              ​ void curand_init (  unsigned long long seed, unsigned long long subsequence, unsigned long long offset, curandStateXORWOW_t* state )
Initialize XORWOW state.

                                 Parameters



seed
- Arbitrary bits to use as a seed
subsequence
- Subsequence to start at
offset
- Absolute offset into sequence
state
- Pointer to state to initialize

Description
Initialize XORWOW state in state with the given seed, subsequence, and offset.

All input values of seed, subsequence, and offset are legal. Large values for subsequence and offset require more computation and so will take more time to complete.

A value of 0 for seed sets the state to the values of the original published version of the xorwow algorithm.

__device__
                              ​ float curand_log_normal (  curandStateScrambledSobol64_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the scrambled Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results, then converts
                                 to log-normal distribution.

__device__
                              ​ float curand_log_normal (  curandStateSobol64_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results, then converts
                                 to log-normal distribution.

__device__
                              ​ float curand_log_normal (  curandStateScrambledSobol32_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the scrambled Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate a normally distributed result, then transforms
                                 the result to log-normal.

__device__
                              ​ float curand_log_normal (  curandStateSobol32_t* state, float  mean, float  stddev )
Return a log-normally distributed float from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate a normally distributed result, then transforms
                                 the result to log-normal.

__device__
                              ​ float curand_log_normal (  curandStateMtgp32_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an MTGP32 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the MTGP32 generator in state, increment position of generator.

The implementation uses the inverse cumulative distribution function to generate a normally distributed result, then transforms
                                 the result to log-normal.

__device__
                              ​ float curand_log_normal (  curandStateMRG32k3a_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the MRG32k3a generator in state, increment position of generator by one.

The implementation uses a Box-Muller transform to generate two normally distributed results, transforms them to log-normal
                                 distribution, then returns them one at a time. See curand_log_normal2() for a more efficient version that returns both results at once.

__device__
                              ​ float curand_log_normal (  curandStatePhilox4_32_10_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the Philox4_32_10 generator in state, increment position of generator by one.

The implementation uses a Box-Muller transform to generate two normally distributed results, transforms them to log-normal
                                 distribution, then returns them one at a time. See curand_log_normal2() for a more efficient version that returns both results at once.

__device__
                              ​ float curand_log_normal (  curandStateXORWOW_t* state, float  mean, float  stddev )
Return a log-normally distributed float from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float with mean mean and standard deviation stddev

Description
Return a single log-normally distributed float derived from a normal distribution with mean mean and standard deviation stddev from the XORWOW generator in state, increment position of generator by one.

The implementation uses a Box-Muller transform to generate two normally distributed results, transforms them to log-normal
                                 distribution, then returns them one at a time. See curand_log_normal2() for a more efficient version that returns both results at once.

__device__
                              ​ float2 curand_log_normal2 (  curandStateMRG32k3a_t* state, float  mean, float  stddev )
Return two normally distributed floats from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float2 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return two log-normally distributed floats derived from a normal distribution with mean mean and standard deviation stddev from the MRG32k3a generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results, then transforms them to log-normal.

__device__
                              ​ float2 curand_log_normal2 (  curandStatePhilox4_32_10_t* state, float  mean, float  stddev )
Return two normally distributed floats from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float2 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return two log-normally distributed floats derived from a normal distribution with mean mean and standard deviation stddev from the Philox4_32_10 generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results, then transforms them to log-normal.

__device__
                              ​ float2 curand_log_normal2 (  curandStateXORWOW_t* state, float  mean, float  stddev )
Return two normally distributed floats from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float2 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return two log-normally distributed floats derived from a normal distribution with mean mean and standard deviation stddev from the XORWOW generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results, then transforms them to log-normal.

__device__
                              ​ double2 curand_log_normal2_double (  curandStateMRG32k3a_t* state, double  mean, double  stddev )
Return two log-normally distributed doubles from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double2 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return two log-normally distributed doubles derived from a normal distribution with mean mean and standard deviation stddev from the MRG32k3a generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results, and transforms them to log-normal
                                 distribution,.

__device__
                              ​ double2 curand_log_normal2_double (  curandStatePhilox4_32_10_t* state, double  mean, double  stddev )
Return two log-normally distributed doubles from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double4 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return two log-normally distributed doubles derived from a normal distribution with mean mean and standard deviation stddev from the Philox4_32_10 generator in state, increment position of generator by four.

The implementation uses a Box-Muller transform to generate two normally distributed results, and transforms them to log-normal
                                 distribution,.

__device__
                              ​ double2 curand_log_normal2_double (  curandStateXORWOW_t* state, double  mean, double  stddev )
Return two log-normally distributed doubles from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double2 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return two log-normally distributed doubles derived from a normal distribution with mean mean and standard deviation stddev from the XORWOW generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results, and transforms them to log-normal
                                 distribution,.

__device__
                              ​ float4 curand_log_normal4 (  curandStatePhilox4_32_10_t* state, float  mean, float  stddev )
Return four normally distributed floats from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed float4 where each element is from a distribution with mean mean and standard deviation stddev

Description
Return four log-normally distributed floats derived from a normal distribution with mean mean and standard deviation stddev from the Philox4_32_10 generator in state, increment position of generator by four.

The implementation uses a Box-Muller transform to generate two normally distributed results, then transforms them to log-normal.

__device__
                              ​ double curand_log_normal_double (  curandStateScrambledSobol64_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the scrambled Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_log_normal_double (  curandStateSobol64_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_log_normal_double (  curandStateScrambledSobol32_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single log-normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the scrambled Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results, and transforms
                                 them into log-normal distribution.

__device__
                              ​ double curand_log_normal_double (  curandStateSobol32_t* state, double  mean, double  stddev )
Return a log-normally distributed double from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single log-normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results, and transforms
                                 them into log-normal distribution.

__device__
                              ​ double curand_log_normal_double (  curandStateMtgp32_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an MTGP32 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single log-normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the MTGP32 generator in state, increment position of generator.

The implementation uses the inverse cumulative distribution function to generate normally distributed results, and transforms
                                 them into log-normal distribution.

__device__
                              ​__NV_SILENCE_DEPRECATION_END  double curand_log_normal_double (  curandStateMRG32k3a_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the MRG32k3a generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results, transforms them to log-normal
                                 distribution, then returns them one at a time. See curand_log_normal2_double() for a more efficient version that returns both results at once.

__device__
                              ​ double curand_log_normal_double (  curandStatePhilox4_32_10_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the Philox4_32_10 generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results, transforms them to log-normal
                                 distribution, then returns them one at a time. See curand_log_normal2_double() for a more efficient version that returns both results at once.

__device__
                              ​ double curand_log_normal_double (  curandStateXORWOW_t* state, double  mean, double  stddev )
Return a log-normally distributed double from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update
mean
- Mean of the related normal distribution
stddev
- Standard deviation of the related normal distribution

Returns
Log-normally distributed double with mean mean and standard deviation stddev

Description
Return a single normally distributed double derived from a normal distribution with mean mean and standard deviation stddev from the XORWOW generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results, transforms them to log-normal
                                 distribution, then returns them one at a time. See curand_log_normal2_double() for a more efficient version that returns both results at once.

__device__
                              ​ float curand_mtgp32_single (  curandStateMtgp32_t* state )
Return a uniformly distributed float from a mtgp32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the mtgp32 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

Note: This alternate derivation of a uniform float is provided for completeness with the original source

__device__
                              ​ float curand_mtgp32_single_specific (  curandStateMtgp32_t* state, unsigned char  index, unsigned char  n )
Return a uniformly distributed float from a specific position in a mtgp32 generator.

                                 Parameters



state
- Pointer to state to update
index
- Index (0..255) of the position within the state to draw from and update
n
- The total number of postions in this state that are being updated by this invocation

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from position index of the mtgp32 generator in state, and increment position of generator by n positions, which must be the total number of positions upddated in the state by the thread block, for this invocation. Output
                                 range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

Note 1: Thread indices must range from 0...n - 1. The number of positions updated may not exceed 256. A thread block may update more than one state, but a given state
                                 may not be updated by more than one thread block.

Note 2: This alternate derivation of a uniform float is provided for completeness with the original source

__device__
                              ​ unsigned int curand_mtgp32_specific (  curandStateMtgp32_t* state, unsigned char  index, unsigned char  n )
Return 32-bits of pseudorandomness from a specific position in a mtgp32 generator.

                                 Parameters



state
- Pointer to state to update
index
- Index (0..255) of the position within the state to draw from and update
n
- The total number of postions in this state that are being updated by this invocation

Returns
32-bits of pseudorandomness as an unsigned int, all bits valid to use.

Description
Return 32-bits of pseudorandomness from position index of the mtgp32 generator in state, increment position of generator by n positions, which must be the total number of positions upddated in the state by the thread block, for this invocation.

Note : Thread indices must range from 0... n - 1. The number of positions updated may not exceed 256. A thread block may update
                                 more than one state, but a given state may not be updated by more than one thread block.

__device__
                              ​ float curand_normal (  curandStateScrambledSobol64_t* state )
Return a normally distributed float from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the scrambled Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ float curand_normal (  curandStateSobol64_t* state )
Return a normally distributed float from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ float curand_normal (  curandStateScrambledSobol32_t* state )
Return a normally distributed float from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the scrambled Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ float curand_normal (  curandStateSobol32_t* state )
Return a normally distributed float from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ float curand_normal (  curandStateMtgp32_t* state )
Return a normally distributed float from a MTGP32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the MTGP32 generator in state, increment position of generator.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ float curand_normal (  curandStateMRG32k3a_t* state )
Return a normally distributed float from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the MRG32k3a generator in state, increment position of generator by one.

The implementation uses a Box-Muller transform to generate two normally distributed results, then returns them one at a time.
                                 See curand_normal2() for a more efficient version that returns both results at once.

__device__
                              ​ float curand_normal (  curandStatePhilox4_32_10_t* state )
Return a normally distributed float from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the Philox4_32_10 generator in state, increment position of generator by one.

The implementation uses a Box-Muller transform to generate two normally distributed results, then returns them one at a time.
                                 See curand_normal2() for a more efficient version that returns both results at once.

__device__
                              ​__NV_SILENCE_DEPRECATION_END  float curand_normal (  curandStateXORWOW_t* state )
Return a normally distributed float from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float with mean 0.0f and standard deviation 1.0f

Description
Return a single normally distributed float with mean 0.0f and standard deviation 1.0f from the XORWOW generator in state, increment position of generator by one.

The implementation uses a Box-Muller transform to generate two normally distributed results, then returns them one at a time.
                                 See curand_normal2() for a more efficient version that returns both results at once.

__device__
                              ​ float2 curand_normal2 (  curandStateMRG32k3a_t* state )
Return two normally distributed floats from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float2 where each element is from a distribution with mean 0.0f and standard deviation 1.0f

Description
Return two normally distributed floats with mean 0.0f and standard deviation 1.0f from the MRG32k3a generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​ float2 curand_normal2 (  curandStatePhilox4_32_10_t* state )
Return two normally distributed floats from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float2 where each element is from a distribution with mean 0.0f and standard deviation 1.0f

Description
Return two normally distributed floats with mean 0.0f and standard deviation 1.0f from the Philox4_32_10 generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​ float2 curand_normal2 (  curandStateXORWOW_t* state )
Return two normally distributed floats from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float2 where each element is from a distribution with mean 0.0f and standard deviation 1.0f

Description
Return two normally distributed floats with mean 0.0f and standard deviation 1.0f from the XORWOW generator in state, increment position of generator by two.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​__NV_SILENCE_DEPRECATION_END  double2 curand_normal2_double (  curandStateMRG32k3a_t* state )
Return two normally distributed doubles from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double2 where each element is from a distribution with mean 0.0 and standard deviation 1.0

Description
Return two normally distributed doubles with mean 0.0 and standard deviation 1.0 from the MRG32k3a generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​ double2 curand_normal2_double (  curandStatePhilox4_32_10_t* state )
Return two normally distributed doubles from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double2 where each element is from a distribution with mean 0.0 and standard deviation 1.0

Description
Return two normally distributed doubles with mean 0.0 and standard deviation 1.0 from the Philox4_32_10 generator in state, increment position of generator by 2.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​ double2 curand_normal2_double (  curandStateXORWOW_t* state )
Return two normally distributed doubles from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double2 where each element is from a distribution with mean 0.0 and standard deviation 1.0

Description
Return two normally distributed doubles with mean 0.0 and standard deviation 1.0 from the XORWOW generator in state, increment position of generator by 2.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​ float4 curand_normal4 (  curandStatePhilox4_32_10_t* state )
Return four normally distributed floats from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed float2 where each element is from a distribution with mean 0.0f and standard deviation 1.0f

Description
Return four normally distributed floats with mean 0.0f and standard deviation 1.0f from the Philox4_32_10 generator in state, increment position of generator by four.

The implementation uses a Box-Muller transform to generate two normally distributed results.

__device__
                              ​ double curand_normal_double (  curandStateScrambledSobol64_t* state )
Return a normally distributed double from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the scrambled Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_normal_double (  curandStateSobol64_t* state )
Return a normally distributed double from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the Sobol64 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_normal_double (  curandStateScrambledSobol32_t* state )
Return a normally distributed double from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the scrambled Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_normal_double (  curandStateSobol32_t* state )
Return a normally distributed double from an Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the Sobol32 generator in state, increment position of generator by one.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_normal_double (  curandStateMtgp32_t* state )
Return a normally distributed double from an MTGP32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the MTGP32 generator in state, increment position of generator.

The implementation uses the inverse cumulative distribution function to generate normally distributed results.

__device__
                              ​ double curand_normal_double (  curandStateMRG32k3a_t* state )
Return a normally distributed double from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the XORWOW generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results, then returns them one at a time.
                                 See curand_normal2_double() for a more efficient version that returns both results at once.

__device__
                              ​ double curand_normal_double (  curandStatePhilox4_32_10_t* state )
Return a normally distributed double from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the Philox4_32_10 generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results, then returns them one at a time.
                                 See curand_normal2_double() for a more efficient version that returns both results at once.

__device__
                              ​ double curand_normal_double (  curandStateXORWOW_t* state )
Return a normally distributed double from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
Normally distributed double with mean 0.0 and standard deviation 1.0

Description
Return a single normally distributed double with mean 0.0 and standard deviation 1.0 from the XORWOW generator in state, increment position of generator.

The implementation uses a Box-Muller transform to generate two normally distributed results, then returns them one at a time.
                                 See curand_normal2_double() for a more efficient version that returns both results at once.

__device__
                              ​ unsigned int curand_poisson (  curandStateScrambledSobol64_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the scrambled Sobol64 generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand_poisson (  curandStateSobol64_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the Sobol64 generator in state, increment position of generator by one.

__device__
                              ​ unsigned int curand_poisson (  curandStateScrambledSobol32_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the scrambled Sobol32 generator in state, increment the position of the generator by one.

__device__
                              ​ unsigned int curand_poisson (  curandStateSobol32_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the Sobol32 generator in state, increment the position of the generator by one.

__device__
                              ​ unsigned int curand_poisson (  curandStateMtgp32_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a MTGP32 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single int from a Poisson distribution with lambda lambda from the MTGP32 generator in state, increment the position of the generator by one.

__device__
                              ​ unsigned int curand_poisson (  curandStateMRG32k3a_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a MRG32k3A generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the MRG32k3a generator in state, increment the position of the generator by a variable amount, depending on the algorithm used.

__device__
                              ​ unsigned int curand_poisson (  curandStatePhilox4_32_10_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the Philox4_32_10 generator in state, increment the position of the generator by a variable amount, depending on the algorithm used.

__device__
                              ​ unsigned int curand_poisson (  curandStateXORWOW_t* state, double  lambda )
Return a Poisson-distributed unsigned int from a XORWOW generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a single unsigned int from a Poisson distribution with lambda lambda from the XORWOW generator in state, increment the position of the generator by a variable amount, depending on the algorithm used.

__device__
                              ​ uint4 curand_poisson4 (  curandStatePhilox4_32_10_t* state, double  lambda )
Return four Poisson-distributed unsigned ints from a Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update
lambda
- Lambda of the Poisson distribution

Returns
Poisson-distributed unsigned int with lambda lambda

Description
Return a four unsigned ints from a Poisson distribution with lambda lambda from the Philox4_32_10 generator in state, increment the position of the generator by a variable amount, depending on the algorithm used.

__device__
                              ​ float curand_uniform (  curandStateScrambledSobol64_t* state )
Return a uniformly distributed float from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the scrambled Sobol64 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand().

__device__
                              ​ float curand_uniform (  curandStateSobol64_t* state )
Return a uniformly distributed float from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the Sobol64 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand().

__device__
                              ​ float curand_uniform (  curandStateScrambledSobol32_t* state )
Return a uniformly distributed float from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the scrambled Sobol32 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand().

__device__
                              ​ float curand_uniform (  curandStateSobol32_t* state )
Return a uniformly distributed float from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the Sobol32 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand().

__device__
                              ​ float curand_uniform (  curandStateMtgp32_t* state )
Return a uniformly distributed float from a MTGP32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the MTGP32 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

__device__
                              ​__NV_SILENCE_DEPRECATION_END  float curand_uniform (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed float from a Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0 and 1.0

Description
Return a uniformly distributed float between 0.0f and 1.0f from the Philox4_32_10 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

__device__
                              ​ float curand_uniform (  curandStateMRG32k3a_t* state )
Return a uniformly distributed float from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the MRG32k3a generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

The implementation returns up to 23 bits of mantissa, with the minimum return value \( 2^{-32} \)

__device__
                              ​ float curand_uniform (  curandStateXORWOW_t* state )
Return a uniformly distributed float from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0f and 1.0f

Description
Return a uniformly distributed float between 0.0f and 1.0f from the XORWOW generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

The implementation may use any number of calls to curand() to get enough random bits to create the return value. The current implementation uses one call.

__device__
                              ​ double2 curand_uniform2_double (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed tuple of 2 doubles from an Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
2 uniformly distributed doubles between 0.0 and 1.0

Description
Return a uniformly distributed 2 doubles (double4) between 0.0 and 1.0 from the Philox4_32_10 generator in state, increment position of generator by 4. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

__device__
                              ​ float4 curand_uniform4 (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed tuple of 4 floats from a Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed float between 0.0 and 1.0

Description
Return a uniformly distributed 4 floats between 0.0f and 1.0f from the Philox4_32_10 generator in state, increment position of generator by 4. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

__device__
                              ​ double curand_uniform_double (  curandStateScrambledSobol64_t* state )
Return a uniformly distributed double from a scrambled Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0 and 1.0

Description
Return a uniformly distributed double between 0.0 and 1.0 from the scrambled Sobol64 generator in state, increment position of generator. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand() to preserve the quasirandom properties of the sequence.

__device__
                              ​ double curand_uniform_double (  curandStateSobol64_t* state )
Return a uniformly distributed double from a Sobol64 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0 and 1.0

Description
Return a uniformly distributed double between 0.0 and 1.0 from the Sobol64 generator in state, increment position of generator. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand() to preserve the quasirandom properties of the sequence.

__device__
                              ​ double curand_uniform_double (  curandStateScrambledSobol32_t* state )
Return a uniformly distributed double from a scrambled Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0 and 1.0

Description
Return a uniformly distributed double between 0.0 and 1.0 from the scrambled Sobol32 generator in state, increment position of generator. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand() to preserve the quasirandom properties of the sequence.

Note that the implementation uses only 32 random bits to generate a single double precision value.

__device__
                              ​ double curand_uniform_double (  curandStateSobol32_t* state )
Return a uniformly distributed double from a Sobol32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0 and 1.0

Description
Return a uniformly distributed double between 0.0 and 1.0 from the Sobol32 generator in state, increment position of generator. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

The implementation is guaranteed to use a single call to curand() to preserve the quasirandom properties of the sequence.

Note that the implementation uses only 32 random bits to generate a single double precision value.

__device__
                              ​ double curand_uniform_double (  curandStatePhilox4_32_10_t* state )
Return a uniformly distributed double from a Philox4_32_10 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0f and 1.0f

Description
Return a uniformly distributed double between 0.0f and 1.0f from the Philox4_32_10 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

Note that the implementation uses only 32 random bits to generate a single double precision value.
curand_uniform2_double() is recommended for higher quality uniformly distributed double precision values.

__device__
                              ​ double curand_uniform_double (  curandStateMtgp32_t* state )
Return a uniformly distributed double from a MTGP32 generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0f and 1.0f

Description
Return a uniformly distributed double between 0.0f and 1.0f from the MTGP32 generator in state, increment position of generator. Output range excludes 0.0f but includes 1.0f. Denormalized floating point outputs are never returned.

Note that the implementation uses only 32 random bits to generate a single double precision value.

__device__
                              ​ double curand_uniform_double (  curandStateMRG32k3a_t* state )
Return a uniformly distributed double from an MRG32k3a generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0 and 1.0

Description
Return a uniformly distributed double between 0.0 and 1.0 from the MRG32k3a generator in state, increment position of generator. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

Note the implementation returns at most 32 random bits of mantissa as outlined in the seminal paper by L'Ecuyer.

__device__
                              ​ double curand_uniform_double (  curandStateXORWOW_t* state )
Return a uniformly distributed double from an XORWOW generator.

                                 Parameters



state
- Pointer to state to update

Returns
uniformly distributed double between 0.0 and 1.0

Description
Return a uniformly distributed double between 0.0 and 1.0 from the XORWOW generator in state, increment position of generator. Output range excludes 0.0 but includes 1.0. Denormalized floating point outputs are never returned.

The implementation may use any number of calls to curand() to get enough random bits to create the return value. The current implementation uses exactly two calls.

template < typename T >
__device__
                              ​ CURAND_STD::​enable_if < CURAND_STD::​is_same &lt; curandStateSobol64_t* > ::type skipahead (  unsigned long long n, T state )  [inline]
Update Sobol64 state to skip n elements.


                                 Parameters



n
- Number of elements to skip
state
- Pointer to state to update

Description
Update the Sobol64 state in state to skip ahead n elements.

All values of n are valid.

template < typename T >
__device__
                              ​ CURAND_STD::​enable_if < CURAND_STD::​is_same &lt; curandStateSobol32_t* > ::type skipahead (  unsigned int  n, T state )  [inline]
Update Sobol32 state to skip n elements.


                                 Parameters



n
- Number of elements to skip
state
- Pointer to state to update

Description
Update the Sobol32 state in state to skip ahead n elements.

All values of n are valid.

__device__
                              ​ void skipahead (  unsigned long long n, curandStateMRG32k3a_t* state )
Update MRG32k3a state to skip n elements.


                                 Parameters



n
- Number of elements to skip
state
- Pointer to state to update

Description
Update the MRG32k3a state in state to skip ahead n elements.

All values of n are valid. Large values require more computation and so will take more time to complete.

__device__
                              ​ void skipahead (  unsigned long long n, curandStatePhilox4_32_10_t* state )
Update Philox4_32_10 state to skip n elements.


                                 Parameters



n
- Number of elements to skip
state
- Pointer to state to update

Description
Update the Philox4_32_10 state in state to skip ahead n elements.

All values of n are valid.

__device__
                              ​ void skipahead (  unsigned long long n, curandStateXORWOW_t* state )
Update XORWOW state to skip n elements.


                                 Parameters



n
- Number of elements to skip
state
- Pointer to state to update

Description
Update the XORWOW state in state to skip ahead n elements.

All values of n are valid. Large values require more computation and so will take more time to complete.

__device__
                              ​ void skipahead_sequence (  unsigned long long n, curandStateMRG32k3a_t* state )
Update MRG32k3a state to skip ahead n sequences.


                                 Parameters



n
- Number of sequences to skip
state
- Pointer to state to update

Description
Update the MRG32k3a state in state to skip ahead n sequences. Each sequence is  2127 elements long, so this means the function will skip ahead  2127 * n elements.

All values of n are valid. Large values require more computation and so will take more time to complete.

__device__
                              ​ void skipahead_sequence (  unsigned long long n, curandStatePhilox4_32_10_t* state )
Update Philox4_32_10 state to skip ahead n subsequences.


                                 Parameters



n
- Number of subsequences to skip
state
- Pointer to state to update

Description
Update the Philox4_32_10 state in state to skip ahead n subsequences. Each subsequence is  266 elements long, so this means the function will skip ahead  266 * n elements.

All values of n are valid.

__device__
                              ​ void skipahead_sequence (  unsigned long long n, curandStateXORWOW_t* state )
Update XORWOW state to skip ahead n subsequences.


                                 Parameters



n
- Number of subsequences to skip
state
- Pointer to state to update

Description
Update the XORWOW state in state to skip ahead n subsequences. Each subsequence is  267 elements long, so this means the function will skip ahead  267 * n elements.

All values of n are valid. Large values require more computation and so will take more time to complete.

__device__
                              ​ void skipahead_subsequence (  unsigned long long n, curandStateMRG32k3a_t* state )
Update MRG32k3a state to skip ahead n subsequences.


                                 Parameters



n
- Number of subsequences to skip
state
- Pointer to state to update

Description
Update the MRG32k3a state in state to skip ahead n subsequences. Each subsequence is  2127
276 elements long, so this means the function will skip ahead  267 * n elements.

Valid values of n are 0 to  251. Note n will be masked to 51 bits


---