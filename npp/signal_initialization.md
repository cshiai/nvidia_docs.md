# Signal Initialization Functions


Functions that provide functionality of initialization signal like: set, zero or copy other signal.


## Signal Set


### Set


The set of set initialization operations available in the library.


Set


Set methods for 1D vectors of various types.


The copy methods operate on vector data given as a pointer to the underlying data-type (e.g. 8-bit vectors would be passed as pointers to Npp8u type) and length of the vectors, i.e. the number of items.


NppStatus nppsSet_8u_Ctx(Npp8u nValue, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_8s_Ctx(Npp8s nValue, Npp8s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit signed char, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_16u_Ctx(Npp16u nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned integer, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_16s_Ctx(Npp16s nValue, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed integer, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_16sc_Ctx(Npp16sc nValue, Npp16sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit integer complex, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_32u_Ctx(Npp32u nValue, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_32s_Ctx(Npp32s nValue, Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_32sc_Ctx(Npp32sc nValue, Npp32sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit integer complex, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_32f_Ctx(Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit float, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_32fc_Ctx(Npp32fc nValue, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit float complex, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_64s_Ctx(Npp64s nValue, Npp64s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit long long integer, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_64sc_Ctx(Npp64sc nValue, Npp64sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit long long integer complex, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_64f_Ctx(Npp64f nValue, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit double, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSet_64fc_Ctx(Npp64fc nValue, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit double complex, vector set method.

Parameters

nValue – Value used to initialize the vector pDst.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Zero


### Zero


The set of zero initialization operations available in the library.


Zero


Set signals to zero.


NppStatus nppsZero_8u_Ctx(Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_16s_Ctx(Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit integer, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_16sc_Ctx(Npp16sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit integer complex, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_32s_Ctx(Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit integer, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_32sc_Ctx(Npp32sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit integer complex, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_32f_Ctx(Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit float, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_32fc_Ctx(Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit float complex, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_64s_Ctx(Npp64s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit long long integer, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_64sc_Ctx(Npp64sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit long long integer complex, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_64f_Ctx(Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit double, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZero_64fc_Ctx(Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit double complex, vector zero method.

Parameters

pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Copy


### Copy


The set of copy initialization operations available in the library.


Copy


Copy methods for various type signals.


Copy methods operate on signal data given as a pointer to the underlying data-type (e.g. 8-bit vectors would be passed as pointers to Npp8u type) and length of the vectors, i.e. the number of items.


NppStatus nppsCopy_8u_Ctx(const Npp8u *pSrc, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char, vector copy method

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_32s_Ctx(const Npp32s *pSrc, Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit float, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_64s_Ctx(const Npp64s *pSrc, Npp64s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit signed integer, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_16sc_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit complex short, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_32sc_Ctx(const Npp32sc *pSrc, Npp32sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex signed integer, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex float, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_64sc_Ctx(const Npp64sc *pSrc, Npp64sc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex signed integer, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCopy_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex double, vector copy method.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.