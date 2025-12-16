# Quickstart


This page will guide you through getting setup and running with cuTile Python, including running a first example.


## Prerequisites


cuTile Python requires the following:


> - Linux x86_64, Linux aarch64 or Windows x86_64
>  - A GPU with compute capability 10.x or 12.x
>  - NVIDIA Driver r580 or later
>  - CUDA Toolkit 13.1 or later
>  - Python version 3.10, 3.11, 3.12 or 3.13


## Installing cuTile Python


With the [prerequisites](quickstart.html#quickstart-prereqs) met, installing cuTile Python is a simple pip install:


```
pip install cuda-tile
```


## Other Packages


Some of the cuTile Python samples also use other Python packages.


The quickstart sample on this page uses cupy, which can be installed with:


```
pip install cupy-cuda13x
```


The cuTile Python samples in the `samples/` directory also use pytest, torch, and numpy packages.


For PyTorch installation instructions, see [https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/).


Pytest and Numpy can be installed with:


```
pip install pytest numpy
```


## Example Code


The following example shows vector addition, a typical first kernel for CUDA, but uses cuTile for tile-based programming. This makes use of a 1-dimensional tile to add two 1-dimensional vectors.


This example shows a structure common to cuTile kernels:


 - Load one or more tiles from GPU memory
 - Perform computation(s) on the tile(s), resulting in new tile(s)
 - Write the resulting tile(s) out to GPU memory


In this case, the kernel loads tiles from two vectors, `a` and `b`. These loads create tiles called `a_tile` and `b_tile`. These tiles are added together to form a third tile, called `result`. In the last step, the kernel stores the `result` tile to the output vector `c`. More samples can be found in the cuTile Python [repository](https://github.com/nvidia/cutile-python).


```
# SPDX-FileCopyrightText: Copyright (c) <2025> NVIDIA CORPORATION & AFFILIATES. All rights reserved.
#
# SPDX-License-Identifier: Apache-2.0

"""
Example demonstrating simple vector addition.
Shows how to perform elementwise operations on vectors.
"""

import cupy as cp
import numpy as np
import cuda.tile as ct

@ct.kernel
def vector_add(a, b, c, tile_size: ct.Constant[int]):
    # Get the 1D pid
    pid = ct.bid(0)

    # Load input tiles
    a_tile = ct.load(a, index=(pid,), shape=(tile_size,))
    b_tile = ct.load(b, index=(pid,), shape=(tile_size,))

    # Perform elementwise addition
    result = a_tile + b_tile

    # Store result
    ct.store(c, index=(pid, ), tile=result)

def test():
    # Create input data
    vector_size = 212
    tile_size = 24
    grid = (ct.cdiv(vector_size, tile_size), 1, 1)

    a = cp.random.uniform(-1, 1, vector_size)
    b = cp.random.uniform(-1, 1, vector_size)
    c = cp.zeros_like(a)

    # Launch kernel
    ct.launch(cp.cuda.get_current_stream(),
              grid,  # 1D grid of processors
              vector_add,
              (a, b, c, tile_size))

    # Copy to host only to compare
    a_np = cp.asnumpy(a)
    b_np = cp.asnumpy(b)
    c_np = cp.asnumpy(c)

    # Verify results
    expected = a_np + b_np
    np.testing.assert_array_almost_equal(c_np, expected)

    print("✓ vector_add_example passed!")

if __name__ == "__main__":
    test()
```


Run this from a command line as shown below. If everything has been setup correctly, the test will print that the example passed.


```
$ python3 samples/quickstart/VectorAdd_quickstart.py
✓ vector_add_example passed!
```


To run more of the cuTile Python examples, you can directly run the samples by invoking them in the same way as the quickstart example:


```
$ python3 samples/FFT.py
# output not shown
```


You can also use pytest to run all the samples:


```
$  pytest samples
========================= test session starts =========================
platform linux -- Python 3.12.3, pytest-9.0.1, pluggy-1.6.0
rootdir: /home/ascudiero/sw/cutile-python
configfile: pytest.ini
collected 6 items

samples/test_samples.py ......                                  [100%]

========================= 6 passed in 30.74s ==========================
```


## Developer Tools


[NVIDIA Nsight Compute](https://developer.nvidia.com/nsight-compute) can profile cuTile Python kernels in the same way as SIMT CUDA kernels. With NVIDIA Nsight Compute installed, the quickstart vector addition kernel introduced here can be profiled using the following command to create a profile:


```
ncu -o VecAddProfile --set detailed python3 VectorAdd_quickstart.py
```


This profile can then be loaded in a graphical instance of Nsight Compute and the kernel `vector_add` selected to see statistics about the kernel.


Note


Capturing detailed statistics for cuTile Python kernels requires running on NVIDIA Driver r590 or later.