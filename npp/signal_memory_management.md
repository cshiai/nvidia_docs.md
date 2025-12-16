# Signal Memory Management Functions


Functions that provide memory management functionality like malloc and free.


## Malloc


Signal-allocator methods for allocating 1D arrays of data in device memory. All allocators have size parameters to specify the size of the signal (1D array) being allocated.


The allocator methods return a pointer to the newly allocated memory of appropriate type. If device-memory allocation is not possible due to resource constaints the allocators return 0 (i.e. NULL pointer).


All signal allocators allocate memory aligned such that it is beneficial to the performance of the majority of the signal-processing primitives. It is no mandatory however to use these allocators. Any valid CUDA device-memory pointers can be passed to NPP primitives.


Functions


Npp8u *nppsMalloc_8u(size_t nSize)
8-bit unsigned signal allocator.

Parameters

nSize – Number of unsigned chars in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp8s *nppsMalloc_8s(size_t nSize)
8-bit signed signal allocator.

Parameters

nSize – Number of (signed) chars in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp16u *nppsMalloc_16u(size_t nSize)
16-bit unsigned signal allocator.

Parameters

nSize – Number of unsigned shorts in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp16s *nppsMalloc_16s(size_t nSize)
16-bit signal allocator.

Parameters

nSize – Number of shorts in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp16sc *nppsMalloc_16sc(size_t nSize)
16-bit complex-value signal allocator.

Parameters

nSize – Number of 16-bit complex numbers in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp32u *nppsMalloc_32u(size_t nSize)
32-bit unsigned signal allocator.

Parameters

nSize – Number of unsigned ints in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp32s *nppsMalloc_32s(size_t nSize)
32-bit integer signal allocator.

Parameters

nSize – Number of ints in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp32sc *nppsMalloc_32sc(size_t nSize)
32-bit complex integer signal allocator.

Parameters

nSize – Number of complex integner values in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp32f *nppsMalloc_32f(size_t nSize)
32-bit float signal allocator.

Parameters

nSize – Number of floats in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp32fc *nppsMalloc_32fc(size_t nSize)
32-bit complex float signal allocator.

Parameters

nSize – Number of complex float values in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp64s *nppsMalloc_64s(size_t nSize)
64-bit long integer signal allocator.

Parameters

nSize – Number of long ints in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp64sc *nppsMalloc_64sc(size_t nSize)
64-bit complex long integer signal allocator.

Parameters

nSize – Number of complex long int values in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp64f *nppsMalloc_64f(size_t nSize)
64-bit float (double) signal allocator.

Parameters

nSize – Number of doubles in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


Npp64fc *nppsMalloc_64fc(size_t nSize)
64-bit complex complex signal allocator.

Parameters

nSize – Number of complex double valuess in the new signal.

Returns

A pointer to the new signal. 0 (NULL-pointer) indicates that an error occurred during allocation.


## Free


Free signal memory.


Functions


void nppsFree(void *pValues)
Free method for any signal memory.

Parameters

pValues – A pointer to memory allocated using nppiMalloc_<modifier>.