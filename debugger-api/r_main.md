# Debugger API

This document describes the API for the set routines and data structures available in the CUDA library to any debugger.

   Starting with 3.0, the CUDA debugger API includes several major changes, of which only few are directly visible to end-users:
 - Performance is greatly improved, both with respect to interactions with the debugger and the performance of applications being debugged.
 - The format of cubins has changed to ELF and, as a consequence, most restrictions on debug compilations have been lifted. More information about the new object format is included below.

 The debugger API has significantly changed, reflected in the CUDA-GDB sources.