# Quickstart[#](https://docs.nvidia.com/cuda/cutile-python/quickstart.html#quickstart "Link to this heading")

This page will guide you through getting setup and running with cuTile Python, including running a first example.

## Prerequisites[#](https://docs.nvidia.com/cuda/cutile-python/quickstart.html#prerequisites "Link to this heading")

cuTile Python requires the following:

> -   Linux x86\_64, Linux aarch64 or Windows x86\_64
> -   A GPU with compute capability 8.x 10.x, 11.x or 12.x
> -   NVIDIA Driver r580 or later
> -   Python version 3.10, 3.11, 3.12 or 3.13

## Installing cuTile Python[#](https://docs.nvidia.com/cuda/cutile-python/quickstart.html#installing-cutile-python "Link to this heading")

cuTile Python depends on CUDA TileIR compiler `tileiras`, which futher depends on `ptxas` and `libnvvm` from the CUDA Toolkit.

If your system does not have system-wide CUDA Toolkit (13.1+), you can install cuTile Python along with `[tileiras]`, which installs `nvidia-cuda-tileiras`, `nvidia-cuda-nvcc` and `nvidia-nvvm` into your Python virtual environment.

pip install cuda-tile\[tileiras\]

Note: the package versions for `nvidia-cuda-tileiras`, `nvidia-cuda-nvcc` and `nvidia-nvvm` must match up to the same major.minor version.

Alternatively if you already have system-wide CUDA Toolkit (13.1+) installed, you can install cuTile Python as a standalone package. cuTile automatically searches for `tileiras` from the location of CUDA Toolkit.

pip install cuda-tile

## Other Packages[#](https://docs.nvidia.com/cuda/cutile-python/quickstart.html#other-packages "Link to this heading")

Some of the cuTile Python samples also use other Python packages.

The quickstart sample on this page uses cupy, which can be installed with:

pip install cupy-cuda13x

The cuTile Python samples in the `samples/` directory also use pytest, torch, and numpy packages.

For PyTorch installation instructions, see [https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/).

Pytest and Numpy can be installed with:

pip install pytest numpy

## Example Code[#](https://docs.nvidia.com/cuda/cutile-python/quickstart.html#example-code "Link to this heading")

The following example shows vector addition, a typical first kernel for CUDA, but uses cuTile for tile-based programming. This makes use of a 1-dimensional tile to add two 1-dimensional vectors.

This example shows a structure common to cuTile kernels:

-   Load one or more tiles from GPU memory
-   Perform computation(s) on the tile(s), resulting in new tile(s)
-   Write the resulting tile(s) out to GPU memory

In this case, the kernel loads tiles from two vectors, `a` and `b`. These loads create tiles called `a_tile` and `b_tile`. These tiles are added together to form a third tile, called `result`. In the last step, the kernel stores the `result` tile to the output vector `c`. More samples can be found in the cuTile Python [repository](https://github.com/nvidia/cutile-python).

\# SPDX-FileCopyrightText: Copyright (c) <2025> NVIDIA CORPORATION & AFFILIATES. All rights reserved.
#
\# SPDX-License-Identifier: Apache-2.0

"""
Example demonstrating simple vector addition.
Shows how to perform elementwise operations on vectors.
"""

import cupy as cp
import numpy as np
import cuda.tile as ct

@ct.kernel
def vector\_add(a, b, c, tile\_size: ct.Constant\[int\]):
    \# Get the 1D pid
    pid \= ct.bid(0)

    \# Load input tiles
    a\_tile \= ct.load(a, index\=(pid,), shape\=(tile\_size,))
    b\_tile \= ct.load(b, index\=(pid,), shape\=(tile\_size,))

    \# Perform elementwise addition
    result \= a\_tile + b\_tile

    \# Store result
    ct.store(c, index\=(pid, ), tile\=result)

def test():
    \# Create input data
    vector\_size \= 2\*\*12
    tile\_size \= 2\*\*4
    grid \= (ct.cdiv(vector\_size, tile\_size), 1, 1)

    rng \= cp.random.default\_rng()
    a \= rng.random(vector\_size)
    b \= rng.random(vector\_size)
    c \= cp.zeros\_like(a)

    \# Launch kernel
    ct.launch(cp.cuda.get\_current\_stream(),
              grid,  \# 1D grid of processors
              vector\_add,
              (a, b, c, tile\_size))

    \# Copy to host only to compare
    a\_np \= cp.asnumpy(a)
    b\_np \= cp.asnumpy(b)
    c\_np \= cp.asnumpy(c)

    \# Verify results
    expected \= a\_np + b\_np
    np.testing.assert\_array\_almost\_equal(c\_np, expected)

    print("✓ vector\_add\_example passed!")

if \_\_name\_\_ \== "\_\_main\_\_":
    test()

Run this from a command line as shown below. If everything has been setup correctly, the test will print that the example passed.

$ python3 samples/quickstart/VectorAdd\_quickstart.py
✓ vector\_add\_example passed!

To run more of the cuTile Python examples, you can directly run the samples by invoking them in the same way as the quickstart example:

$ python3 samples/FFT.py
\# output not shown

You can also use pytest to run all the samples:

$  pytest samples
\========================= test session starts \=========================
platform linux \-- Python 3.12.3, pytest-9.0.1, pluggy-1.6.0
rootdir: /home/ascudiero/sw/cutile-python
configfile: pytest.ini
collected 6 items

samples/test\_samples.py ......                                  \[100%\]

\========================= 6 passed in 30.74s \==========================

## Developer Tools[#](https://docs.nvidia.com/cuda/cutile-python/quickstart.html#developer-tools "Link to this heading")

[NVIDIA Nsight Compute](https://developer.nvidia.com/nsight-compute) can profile cuTile Python kernels in the same way as SIMT CUDA kernels. With NVIDIA Nsight Compute installed, the quickstart vector addition kernel introduced here can be profiled using the following command to create a profile:

ncu \-o VecAddProfile \--set detailed python3 VectorAdd\_quickstart.py

This profile can then be loaded in a graphical instance of Nsight Compute and the kernel `vector_add` selected to see statistics about the kernel.

Note

Capturing detailed statistics for cuTile Python kernels requires running on NVIDIA Driver equals or later than r580.126.09 (linux) or r582.16 (windows).
