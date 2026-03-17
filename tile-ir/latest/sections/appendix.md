# 11\. Appendix[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#appendix "Link to this heading")

## 11.1. Programming Model Example Programs[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#programming-model-example-programs "Link to this heading")

### 11.1.1. Hello Tile Block[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#hello-tile-block "Link to this heading")

cuda\_tile.module @hello\_world\_module {
    entry @hello\_world\_kernel() {
        print "Hello World!\\n"
    }
}

Copy to clipboard

### 11.1.2. Vector Addition Block 128x1[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#vector-addition-block-128x1 "Link to this heading")

// A basic implementation of 128 sized vector addition using unstructured load/stores.
//
// This implements addition over a 1-d tensor (vector) with size 128.
//
// 128x1 + 128x1 => 128x1
cuda\_tile.module @vector\_block\_add\_128x1 {
    entry @vector\_block\_add\_128x1\_kernel(
        %a\_ptr\_base\_scalar : !cuda\_tile.tile<ptr<f32\>>,
        %b\_ptr\_base\_scalar : !cuda\_tile.tile<ptr<f32\>>,
        %c\_ptr\_base\_scalar : !cuda\_tile.tile<ptr<f32\>>)
{
    // Create an offset on the inclusive (0, 127) interval.
    %offset \= iota : tile<128xi32\>
    // We need a tile<ptr<T>> in order to perform a load or store.
    //
    // We will now convert each raw base pointer into such a pointer.
    //
    // First reshape the scalar pointer ptr<f32> to tile<1xptr<f32>> so it has the correct rank.
    %a\_ptr\_base\_tensor \= reshape %a\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1xptr<f32\>>
    // Next broadcast the pointer so we have a tensor of (base, ..., base) containing 128 elements.
    %a\_ptr \= broadcast %a\_ptr\_base\_tensor : tile<1xptr<f32\>> \-> tile<128xptr<f32\>>
    // Finally add the offset tensor to the tensor of pointers to obtain a tile<128xptr<f32>> that contains
    // pointers of (base + 0, ..., base + 127) as its values.
    %a\_tensor \= offset %a\_ptr, %offset :
        tile<128xptr<f32\>>, tile<128xi32\> \-> tile<128xptr<f32\>>

    // Now we do the same for B.
    %b\_ptr\_base\_tensor \=reshape %b\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1xptr<f32\>>
    %b\_ptr \= broadcast %b\_ptr\_base\_tensor : tile<1xptr<f32\>> \-> tile<128xptr<f32\>>
    %b\_tensor \= offset %b\_ptr, %offset :
        tile<128xptr<f32\>>, tile<128xi32\> \-> tile<128xptr<f32\>>

    // And the same for C.
    %c\_ptr\_base\_tensor \= reshape %c\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1xptr<f32\>>
    %c\_ptr \= broadcast %c\_ptr\_base\_tensor : tile<1xptr<f32\>> \-> tile<128xptr<f32\>>
    %c\_tensor \= offset %c\_ptr, %offset :
        tile<128xptr<f32\>>, tile<128xi32\> \-> tile<128xptr<f32\>>

    // Now that we have prepared all the pointers we can do the real work.
    //
    // First we load A, and B into %a\_val and %b\_val.
    %a\_val, %token\_a \= load\_ptr\_tko weak %a\_tensor : tile<128xptr<f32\>> \-> tile<128xf32\>, token
    %b\_val, %token\_b \= load\_ptr\_tko weak %b\_tensor : tile<128xptr<f32\>> \-> tile<128xf32\>, token
    // We then compute floating-point vector addition using addf
    %c\_val \= addf %a\_val, %b\_val rounding<nearest\_even\> : tile<128xf32\>
    // Finally we store the result to C.
    store\_ptr\_tko weak %c\_tensor, %c\_val : tile<128xptr<f32\>>, tile<128xf32\> \-> token
  }
}

Copy to clipboard

### 11.1.3. Hello Tile Grid[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#hello-tile-grid "Link to this heading")

cuda\_tile.module @hello\_world\_module {
    // TileIR kernel function
    entry @hello\_world\_kernel() {
        // Step 1. Get the tile block ID
        %block\_x\_index, %block\_y\_index, %block\_z\_index \= cuda\_tile.get\_tile\_block\_id : tile<i32\>

        // Step 2. Get the tile block dimensions
        %block\_dim\_x, %block\_dim\_y, %block\_dim\_z \= cuda\_tile.get\_num\_tile\_blocks : tile<i32\>

        // Step 3. Print the tile block ID and dimensions. Each tile executes the 
        // following print statement and prints a single line.
        cuda\_tile.print "Hello, I am tile <%i, %i, %i> in a kernel with <%i, %i, %i> tiles.\\n",
            %block\_x\_index, %block\_y\_index, %block\_z\_index, %block\_dim\_x, %block\_dim\_y, %block\_dim\_z
            : tile<i32\>, tile<i32\>, tile<i32\>,
              tile<i32\>, tile<i32\>, tile<i32\>
        }
}

Copy to clipboard

### 11.1.4. GEMM Single 64x64 Block[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#gemm-single-64x64-block "Link to this heading")

// An implementation of GEMM for a single statically shaped square 64x64 block.
cuda\_tile.module @gemm\_block\_64x64\_module {
    entry @gemm\_block\_64x64\_kernel(
        %a\_ptr\_base\_scalar: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>,
        %b\_ptr\_base\_scalar: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>,
        %c\_ptr\_base\_scalar: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>
    ) {

    %offset\_flat \= iota : tile<4096xi32\>
    %offset \= reshape %offset\_flat :
        tile<4096xi32\> \-> tile<64x64xi32\>
    // Can we have iota support producing tensors directly?
    // %offset = iota : tile<64x64xi32>

    %a\_ptr\_base\_tensor \= reshape %a\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
    %a\_ptr \= broadcast %a\_ptr\_base\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
    %a\_tensor \= offset %a\_ptr, %offset :
        tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

    // Now we do the same for B.
    %b\_ptr\_base\_tensor \= reshape %b\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
    %b\_ptr \= broadcast %b\_ptr\_base\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
    %b\_tensor \= offset %b\_ptr, %offset :
        tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

    // And the same for C.
    %c\_ptr\_base\_tensor \= reshape %c\_ptr\_base\_scalar :
        tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
    %c\_ptr \= broadcast %c\_ptr\_base\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
    %c\_tensor \= offset %c\_ptr, %offset :
         tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

    // Load a single 64x64 matrix from the tile.
    %A\_block, %token\_a \= load\_ptr\_tko weak %a\_tensor :
        tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token

    // Load a single 64x64 matrix from the tile.
    %B\_block, %token\_b \= load\_ptr\_tko weak %b\_tensor :
        tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token

    %init\_accum \= cuda\_tile.constant <f32: 0.000000e+00\> : !cuda\_tile.tile<64x64xf32\>

    // WHy did this type check? %C\_block = cuda\_tile.dot %A\_frag, %B\_frag, %init\_accum: tile<64x64xf16>, tile<64x64xf16>, tile<64x64xf32>
    //
    // I feel like we should seriously reconsider naming this \`dot\` it is super confusing because it doesn't actually implement true dot-product.
    %C\_block \= mmaf %A\_block, %B\_block, %init\_accum: tile<64x64xf32\>, tile<64x64xf32\>, tile<64x64xf32\>

    store\_ptr\_tko weak %c\_tensor, %C\_block :
        tile<64x64xptr<f32\>>, tile<64x64xf32\> \-> token
    }
}

Copy to clipboard

### 11.1.5. GEMM 4096x4096 Block[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#gemm-4096x4096-block "Link to this heading")

// An implementation of GEMM for a square 4096x4096 @ 4096x4096 multiplication.
//
// This would be launched on a 64x64 grid where each tile block computes 64x64 output
// tiles of C.
cuda\_tile.module @gemm\_square\_4096\_tile\_64x64\_module {
    entry @gemm\_square\_4096\_tile\_64x64\_kernel(
        %a\_ptr\_base\_scalar: tile<ptr<f32\>>,
        %b\_ptr\_base\_scalar: tile<ptr<f32\>>,
        %c\_ptr\_base\_scalar: tile<ptr<f32\>>
    ) {
        // We first setup up some state for the kernel.
        //
        // Keep this line of space for the spec right now.
        // Read Tile block id's.
        %block\_x\_index, %block\_y\_index, %block\_z\_index \= get\_tile\_block\_id : tile<i32\>

        // We assume we have tiled a 4096x4096 @ 4096x4096 matrix mupltiplication split into
        // // 64x64 tiles so the tile m, n, k are all 64.
        // %stride\_A\_m = constant <i32: 64> : tile<i32>
        // %stride\_ = constant <i32: 64> : tile<i32>
        // %k\_tile\_size = constant <i32: 64> : tile<i32>

        // We assume we have tiled a 4096x4096 @ 4096x4096 matrix mupltiplication split into
        // 64x64 tiles so the tile m, n, k are all 64.
        %m\_tile\_size \= constant <i32: 64\> : tile<i32\>
        %m\_stride\_factor \= cuda\_tile.constant <i32: 64\> : tile<64x64xi32\> // todo fix the line # and restore this %n\_tile\_size = cuda\_tile.constant <i32: 64> : tile<i32>
        %k\_tile\_size \= cuda\_tile.constant <i32: 64\> : tile<i32\>

        %range\_start \= cuda\_tile.constant <i32: 0\> : tile<i32\>
        %range\_step \= cuda\_tile.constant <i32: 1\> : tile<i32\>
        %init\_accum \= cuda\_tile.constant <f32: 0.000000e+00\> : tile<64x64xf32\>

        // The shared range from (0, 63).
        %tile\_size\_range \= cuda\_tile.iota : tile<64xi32\>

        // We must first compute the tensors of initial offsets for A and B so that we can obtain a tensor of
        // pointers for each to load them.
        //
        // First we compute the starting indices of A's tile in this case this will be the "top-corner"
        // of a row-major tile specified by block\_x\_index.
        //
        // The only way to contruct the offset matrix for a tile is by building up a tensor step by step.
        //
        // Conceptually we start by computing the offsets of the M dimension:
        //
        // m\_offsets = block\_x\_index \* k\_tile\_size + arange(0, k\_tile\_size)
        //
        // This produces a vector starting from the "top-corner" of the tile at (block\_x\_index \* tile\_size, block\_x\_index \* tile\_size + tile\_size).
        %a\_tile\_base \= cuda\_tile.muli %block\_x\_index, %k\_tile\_size : tile<i32\>
        %a\_tile\_base\_reshape \= cuda\_tile.reshape %a\_tile\_base : tile<i32\> \-> tile<1xi32\>
        %a\_tile\_base\_tensor \= cuda\_tile.broadcast %a\_tile\_base\_reshape :
            tile<1xi32\> \-> tile<64xi32\>
        %m\_offsets\_vec \= cuda\_tile.addi %a\_tile\_base\_tensor, %tile\_size\_range : tile<64xi32\>

        // The striding of the A matrix is (64, 1) meaning that we don't need to do anything special for the K
        // dimension we just want each row of the offset matrix to be sequential.
        //
        // We can reuse %tile\_size\_range as k\_offs = torch.arange(0, k\_tile\_size).
        //
        // a\_tile = reshape(m\_offs, (64, 1)) \* m\_stride + reshape(k\_offs, (1, 64)) \* k\_stride
        //
        // We first broadcast the m\_offsets into a matrix where each column is identical and scaled by stride.
        %m\_offsets\_matrix \= cuda\_tile.reshape %m\_offsets\_vec :
            tile<64xi32\> \-> tile<64x1xi32\>
        %m\_offsets\_broadcast \= cuda\_tile.broadcast %m\_offsets\_matrix :
            tile<64x1xi32\> \-> tile<64x64xi32\>
        %m\_offsets \= cuda\_tile.muli %m\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

        // We then broadcast the k\_offsets into a matrix where row is identical and scaled by stride.
        %ak\_offsets\_matrix \= cuda\_tile.reshape %tile\_size\_range :
             tile<64xi32\> \-> tile<1x64xi32\>
        %ak\_offsets\_broadcast \= cuda\_tile.broadcast %ak\_offsets\_matrix :
            tile<1x64xi32\> \-> tile<64x64xi32\>
        %ak\_offsets \= cuda\_tile.muli %ak\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

        // Finally we add them together resulting in the final offset matrix for A.
        %a\_tile\_offsets \= cuda\_tile.addi %m\_offsets, %ak\_offsets : tile<64x64xi32\>

        // Now we do the same for B, first prepare the set of n\_offsets.
        // n\_offs = j \* n\_tile\_size + torch.arange(0, n\_tile\_size)
        %b\_tile\_base \= cuda\_tile.muli %block\_y\_index, %k\_tile\_size : tile<i32\>
        %b\_tile\_base\_reshape \= cuda\_tile.reshape %b\_tile\_base :
            tile<i32\> \-> tile<1xi32\>
        %b\_tile\_base\_tensor \= cuda\_tile.broadcast %b\_tile\_base\_reshape :
            tile<1xi32\> \-> tile<64xi32\>
        %n\_offsets\_vec \= cuda\_tile.addi %b\_tile\_base\_tensor, %tile\_size\_range : tile<64xi32\>

        // b\_tile = k\_offs\[:, None\] \* k\_stride + n\_offs\[None, :\] \* n\_stride
        %bk\_offsets\_matrix \= cuda\_tile.reshape %tile\_size\_range : tile<64xi32\> \-> tile<64x1xi32\>
        // Stride is one.
        %bk\_offsets \= cuda\_tile.broadcast %bk\_offsets\_matrix : tile<64x1xi32\> \-> tile<64x64xi32\>
        // %bk\_offsets = cuda\_tile.muli %bk\_offsets\_broadcast, %k\_tile\_size : tile<i32>

        %n\_offsets\_matrix \= cuda\_tile.reshape %n\_offsets\_vec : tile<64xi32\> \-> tile<1x64xi32\>
        %n\_offsets\_broadcast \= cuda\_tile.broadcast %n\_offsets\_matrix :  tile<1x64xi32\> \-> tile<64x64xi32\>
        %n\_offsets \= cuda\_tile.muli %n\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

        %b\_tile\_offsets \= cuda\_tile.muli %bk\_offsets, %n\_offsets : tile<64x64xi32\>

        // Now the rest of the kernel looks like what we did before we simply convert the base pointer
        // to a tensor, add the offset matrix, and continue.
        %a\_ptr\_base\_tensor \= cuda\_tile.reshape %a\_ptr\_base\_scalar :
            tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
        %a\_ptr \= cuda\_tile.broadcast %a\_ptr\_base\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
        %a\_tile\_ptr \= offset %a\_ptr, %a\_tile\_offsets :
            tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

        // And the same for B.
        %b\_ptr\_tile\_tensor \= reshape %b\_ptr\_base\_scalar :
            tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
        %b\_ptr \= broadcast %b\_ptr\_tile\_tensor : tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
        %b\_tile\_ptr \= offset %b\_ptr, %b\_tile\_offsets :
            tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

        %C\_tile, %a\_ptr\_final, %b\_ptr\_final \= for %k in (%range\_start to %k\_tile\_size, step %range\_start) : tile<i32\>
            iter\_values(
                %acc\_prev \= %init\_accum,
                %a\_tile\_ptr\_prev \= %a\_tile\_ptr,
                %b\_tile\_ptr\_prev \= %b\_tile\_ptr
            ) \-> (tile<64x64xf32\>, tile<64x64xptr<f32\>>, tile<64x64xptr<f32\>>)
        {
            // Load a single 64x64 matrix from the tile.
            %A\_tile, %token\_a \= load\_ptr\_tko weak %a\_tile\_ptr :
                tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token

            // Load a single 64x64 matrix from the tile.
            %B\_tile, %token\_b \= load\_ptr\_tko weak %b\_tile\_ptr :
                tile<64x64xptr<f32\>> \-> tile<64x64xf32\>, token

            %C\_tile\_acc \= mmaf %A\_tile, %B\_tile, %acc\_prev: tile<64x64xf32\>, tile<64x64xf32\>, tile<64x64xf32\>

            // Advance by K block size.
            %block\_size \= constant <i32: 64\> : tile<64x64xi32\>
            %a\_tile\_ptr\_next \= offset %a\_tile\_ptr\_prev, %block\_size
                : tile<64x64xptr<f32\>>, tile<64x64xi32\>
                    \-> tile<64x64xptr<f32\>>
            %b\_tile\_ptr\_next \= offset %b\_tile\_ptr\_prev, %block\_size
                : tile<64x64xptr<f32\>>, tile<64x64xi32\>
                    \-> tile<64x64xptr<f32\>>

            // Store the partial sum to the 64x64 accumulator.
            continue %C\_tile\_acc, %a\_tile\_ptr\_next, %b\_tile\_ptr\_next : tile<64x64xf32\>, tile<64x64xptr<f32\>>, tile<64x64xptr<f32\>>
        }

        // We now need to do the thing for the offsets in C, but not inside the loop.
        //
        // The equivalent Triton code for this computation is:
        //
        // offs\_cm = block\_x\_index \* BLOCK\_SIZE\_M + tl.arange(0, BLOCK\_SIZE\_M)
        //
        // We first start by computing the offset at which the tile starts on the x coordinate of the matrix.
        %c\_tile\_x\_start \= muli %block\_x\_index, %k\_tile\_size :
            tile<i32\>
        %c\_tile\_x\_start\_reshape \= reshape %c\_tile\_x\_start :
            tile<i32\> \-> tile<1xi32\>
        %c\_tile\_x\_start\_tensor \= broadcast %c\_tile\_x\_start\_reshape :
            tile<1xi32\> \-> tile<64xi32\>
        // We now have a vector which goes from (block\_x\_index \* tile\_size\_m, block\_x\_index \* tile\_size\_m + 63)
        %c\_tile\_x\_offsets\_vec \= addi %c\_tile\_x\_start\_tensor, %tile\_size\_range : tile<64xi32\>

        // We do the same for this computation:
        //
        // offs\_cn = pid\_n \* BLOCK\_SIZE\_N + tl.arange(0, BLOCK\_SIZE\_N)
        %c\_tile\_y\_start \= muli %block\_x\_index, %k\_tile\_size : tile<i32\>
        %c\_tile\_y\_start\_reshape \= reshape %c\_tile\_y\_start : tile<i32\> \-> tile<1xi32\>
        %c\_tile\_y\_start\_tensor \= broadcast %c\_tile\_y\_start\_reshape :
            tile<1xi32\> \-> tile<64xi32\>
        %c\_tile\_y\_offsets\_vec \= addi %c\_tile\_y\_start\_tensor, %tile\_size\_range : tile<64xi32\>

        // We now want to do broadcating addition to get the file tensor of offsets which represent the tile.
        //
        // c\_ptrs = c\_ptr + stride\_cm \* offs\_cm\[:, None\] + stride\_cn \* offs\_cn\[None, :\]
        //
        // We first prepare: stride\_cm \* offs\_cm\[:, None\]
        %c\_tile\_x\_offsets\_matrix \= reshape %c\_tile\_x\_offsets\_vec : tile<64xi32\> \-> tile<64x1xi32\>
        %c\_tile\_x\_offsets\_broadcast \= broadcast %c\_tile\_x\_offsets\_matrix : tile<64x1xi32\> \-> tile<64x64xi32\>
        %c\_tile\_x\_offsets \= muli %c\_tile\_x\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

        // We then prepare:  stride\_cn \* offs\_cn\[None, :\]
        %c\_tile\_y\_offsets\_matrix \= reshape %c\_tile\_y\_offsets\_vec : tile<64xi32\> \-> tile<1x64xi32\>
        %c\_tile\_y\_offsets\_broadcast \= broadcast %c\_tile\_y\_offsets\_matrix : tile<1x64xi32\> \-> tile<64x64xi32\>

        // Finally we add the X and the Y coordinates together to get a complete matrix.
        %c\_tile\_y\_offsets \= muli %c\_tile\_y\_offsets\_broadcast, %m\_stride\_factor : tile<64x64xi32\>

        %c\_tile\_offsets \= muli %c\_tile\_x\_offsets, %c\_tile\_y\_offsets : tile<64x64xi32\>

          // And the same for C.
        %c\_ptr\_base\_tensor \= reshape %c\_ptr\_base\_scalar :
            tile<ptr<f32\>> \-> tile<1x1xptr<f32\>>
        %c\_ptr \= broadcast %c\_ptr\_base\_tensor :
            tile<1x1xptr<f32\>> \-> tile<64x64xptr<f32\>>
        %c\_tile\_ptr \= offset %c\_ptr, %c\_tile\_offsets :
            tile<64x64xptr<f32\>>, tile<64x64xi32\> \-> tile<64x64xptr<f32\>>

        store\_ptr\_tko weak %c\_tile\_ptr, %C\_tile :
            tile<64x64xptr<f32\>>, tile<64x64xf32\> \-> token
    }
}

Copy to clipboard

### 11.1.6. Vector Addition with tensor\_view[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#vector-addition-with-tensor-view "Link to this heading")

// Tiled SAXPY is an optimized implementation of the SAXPY operation.
// This kernel uses memref abstractions for data load and store operations that allow structured load and store and can map accelerator memory engines in our hardware.
// The program divides X and Y into smaller tiles to enable parallelism on multiple tiles.
// Each Tile Block computes a tile of X and Y and stores the result back.

// This example can also be added in the blog post
// "Six Ways to SAXPY": https://developer.nvidia.com/blog/six-ways-saxpy/

cuda\_tile.module @saxpy {
    // TileIR kernel function
    entry @saxpy\_memref(%X: tile<ptr<f32\>>,
                        %Y: tile<ptr<f32\>>,
                        %alpha: tile<f32\>,
                        %M : tile<i32\>,
                        %N : tile<i32\>) {

        // Step 1. Get the tile block ID
        %tileIdX, %tileIdY, %tileIdZ \= get\_tile\_block\_id : tile<i32\>

        // Step 2. Reshape and broadcast the alpha scalar
        %alpha\_reshaped \= reshape %alpha : tile<f32\> \-> tile<1x1xf32\>
        %alpha\_tensor \= broadcast %alpha\_reshaped : tile<1x1xf32\> \-> tile<128x256xf32\>

        // Step 3. Create tensor\_view for X and Y
        %x\_memref \= make\_tensor\_view %X, shape \= \[%M, %N\], strides \= \[%M, 1\] : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,1\]\>
        %y\_memref \= make\_tensor\_view %Y, shape \= \[%M, %N\], strides \= \[%M, 1\] : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,1\]\>

        // Step 4. Create partition view for X and Y
        %x\_view \= make\_partition\_view %x\_memref : partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>
        %y\_view \= make\_partition\_view %y\_memref : partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>

        // Step 5. Load tile from X and Y
        %x\_tile, %token\_x \= load\_view\_tko weak %x\_view\[%tileIdX, %tileIdY\] :
            partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>, tile<i32\> \-> tile<128x256xf32\>, token
        %y\_tile, %token\_y \= load\_view\_tko weak %y\_view\[%tileIdX, %tileIdY\] :
            partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>, tile<i32\> \-> tile<128x256xf32\>, token

        // Step 6. Compute sAXPY: y = alpha \* A + y
        %9 \= mulf %alpha\_tensor, %x\_tile rounding<nearest\_even\> : tile<128x256xf32\>
        %result\_tile \= addf %9, %y\_tile rounding<nearest\_even\> : tile<128x256xf32\>

        // Step 7. Store the result tile to Y
        store\_view\_tko weak %result\_tile, %y\_view\[%tileIdX, %tileIdY\] :
            tile<128x256xf32\>, partition\_view<tile\=(128x256), tensor\_view<?x?xf32, strides\=\[?,1\]\>>, tile<i32\> \-> token
    }
}

Copy to clipboard

### 11.1.7. GEMM Tiled with tensor\_view[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#gemm-tiled-with-tensor-view "Link to this heading")

// An implementation of GEMM in cuda\_tile.
//
// Kernel computes MxNxK with 128x128x64 Tile Size.
// Computes F32 += f16 \* f16 + 0.0
//
// This implementation does tiling, and reduction over
// K for dynamic sizes.
cuda\_tile.module @gemm\_kloop\_module {
    entry @gemm\_kloop\_kernel(
        %A\_ptr: !cuda\_tile.tile<!cuda\_tile.ptr<f16\>>,
        %B\_ptr: !cuda\_tile.tile<!cuda\_tile.ptr<f16\>>,
        %C\_ptr: !cuda\_tile.tile<!cuda\_tile.ptr<f32\>>,
        %M: !cuda\_tile.tile<i32\>, %N: !cuda\_tile.tile<i32\>, %K: !cuda\_tile.tile<i32\>,
        %stride\_ak: !cuda\_tile.tile<i32\>, %stride\_bn: !cuda\_tile.tile<i32\>, %stride\_cm: !cuda\_tile.tile<i32\>
    ) {
        // First we need to prepare the inputs for the actual computation.
        //
        // Assume the preconditions of this kernel (i.e., the stride are all divisible by 8)
        %A\_ptr\_assume \= assume #cuda\_tile.div\_by<16\>, %A\_ptr : tile<ptr<f16\>>
        %B\_ptr\_assume \= assume #cuda\_tile.div\_by<16\>, %B\_ptr : tile<ptr<f16\>>
        %C\_ptr\_assume \= assume #cuda\_tile.div\_by<16\>, %C\_ptr : tile<ptr<f32\>>
        %stride\_ak\_assume \= assume #cuda\_tile.div\_by<8\>, %stride\_ak : tile<i32\>
        %stride\_bn\_assume \= assume #cuda\_tile.div\_by<8\>, %stride\_bn : tile<i32\>
        %stride\_cm\_assume \= assume #cuda\_tile.div\_by<8\>, %stride\_cm : tile<i32\>

        // Constants must be allocated explicitly in the program, below we allocate scalar \`0\`, \`1\`,
        // and the zero'd tensor used for accumulation.
        %i0 \= constant <i32: 0\> : !cuda\_tile.tile<i32\>
        %i1 \= constant <i32: 1\> : !cuda\_tile.tile<i32\>
        %cst \= constant <f32: 0.000000e+00\> : !cuda\_tile.tile<128x128xf32\>

        // Convert the unstructured pointers \`ptr\` to \`tensor\_view\`.
        //
        // A reference to the A tensor pointed to by A\_ptr, (K x M)
        %A \= make\_tensor\_view %A\_ptr\_assume, shape \= \[%K, %M\], strides \= \[%stride\_ak, 1\] : tile<i32\> \-> tensor\_view<?x?xf16, strides\=\[?,1\]\>
        // A reference to the B tensor pointed to by B\_ptr, (N x K)
        %B \= make\_tensor\_view %B\_ptr\_assume, shape \= \[%N, %K\], strides \= \[%stride\_bn, 1\] : tile<i32\> \-> tensor\_view<?x?xf16, strides\=\[?,1\]\>
        // A reference to the C tensor pointed to by C\_ptr, (M x N)
        %C \= make\_tensor\_view %C\_ptr\_assume, shape \= \[%M, %N\], strides \= \[%stride\_cm, 1\] : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,1\]\>

        // Now we have all the inputs as structured pointers each associated with layouts.
        //
        // Next we will tile the problem.
        //
        // Our matrix multiplication is (M\*K) @ (K\*N) = M\*N but our input tensors are transposed.
        //
        // In order to handle this we create partition view where we flip the 0th and 1st dims.

        // We are blocking A (K x M) -> block\_m x block\_k.
        %A\_block  \= make\_partition\_view %A : partition\_view<tile\=(128x64), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>
        // We are blocking B (N x K) -> block\_k x block\_n.
        %B\_block  \= make\_partition\_view %B : partition\_view<tile\=(64x128), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>
        // We are blocking C (M xN) -> block\_m x block\_n.
        %C\_block  \= make\_partition\_view %C : partition\_view<tile\=(128x128), tensor\_view<?x?xf32, strides\=\[?,1\]\>, dim\_map\=\[0, 1\]\>

        // Read Tile block id's.
        %bidx, %bidy, %bidz \= get\_tile\_block\_id : tile<i32\>

        // Because we allow for dynamic dimensions we must get the reduction dimension \`K\` dynamically.
        %mk\_len\_i32:2 \= get\_index\_space\_shape %A\_block : partition\_view<tile\=(128x64), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\> \-> tile<i32\>

        // Now that we have done all the setup, we can finally perform the  computation itself.
        //
        // We simply loop over the K dimension computing: dot(A\_block\[0, k\], B\_block\[k, 0\]).
        %result \= for %k in (%i0 to %mk\_len\_i32#1, step %i1) : tile<i32\>
            iter\_values(%acc\_prev \= %cst) \-> (tile<128x128xf32\>)
        {
            // Load a single 128x64 matrix from the tile.
            %A\_frag, %t1 \= load\_view\_tko weak %A\_block\[%bidx, %k\] : partition\_view<tile\=(128x64), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>, tile<i32\> \-> tile<128x64xf16\>, token

            // Load a single 64x128 matrix from the tile.
            %B\_frag, %t2 \= load\_view\_tko weak %B\_block \[%k, %bidy\] : partition\_view<tile\=(64x128), tensor\_view<?x?xf16, strides\=\[?,1\]\>, dim\_map\=\[1, 0\]\>, tile<i32\> \-> tile<64x128xf16\>, token

            // Compute the mma(A\_frag, B\_frag) + acc\_prev.
            %acc \= mmaf %A\_frag, %B\_frag, %acc\_prev: tile<128x64xf16\>, tile<64x128xf16\>, tile<128x128xf32\>
            // Store the partial sum to the 128x128 accumulator.
            continue %acc : tile<128x128xf32\>
        }

        // Finally store the complete 128x128 tile to the view of C.
        %t3 \= store\_view\_tko weak %result, %C\_block\[%bidx, %bidy\] : tile<128x128xf32\>, partition\_view<tile\=(128x128), tensor\_view<?x?xf32, strides\=\[?,1\]\>, dim\_map\=\[0, 1\]\>, tile<i32\> \-> token
    }
}

Copy to clipboard

## 11.2. Operation Examples[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#operation-examples "Link to this heading")

### 11.2.1. cuda\_tile.cat\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-cat-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
  %arg0 \= constant <f32: 0.0\> : tile<2x4xf32\>
  %arg1 \= constant <f32: 1.0\> : tile<2x4xf32\>

     // A valid invocation of cat.
     %0 \= cat %arg0, %arg1 dim \= 1
       : tile<2x4xf32\>, tile<2x4xf32\> \-> tile<2x8xf32\>

     // >>> %arg0 = tile(\[\[ A, B, C \],
     //                   \[ D, E, F \]\])
     // >>> %arg1 = tile(\[\[ 1, 2, 3 \],
     //                   \[ 4, 5, 6 \]\])
     // >>> %0 = tile(\[\[ A, B, C, 1, 2, 3 \],
     //                \[ D, E, F, 4, 5, 6 \]\])

     // A valid invocation of cat.
     %1 \= cat %arg0, %arg1 dim \= 0
       : tile<2x4xf32\>, tile<2x4xf32\> \-> tile<4x4xf32\>

     // >>> %arg0 = tile(\[\[ A, B, C \],
     //                   \[ D, E, F \]\])
     //
     // >>> %arg1 = tile(\[\[ 1, 2, 3 \],
     //                   \[ 4, 5, 6 \]\])
     //
     // >>> %1 = tile(\[\[ A, B, C \],
     //                \[ D, E, F \],
     //                \[ 1, 2, 3 \],
     //                \[ 4, 5, 6 \]\])
  }
}

Copy to clipboard

### 11.2.2. cuda\_tile.constant\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-constant-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
   %c0 \= constant <i32: 0\> : tile<i32\>
   %c1 \= constant <i64: 1\> : tile<i64\>
   %c2 \= constant <i32: \[0, 1, 2, 3\]\> : tile<4xi32\>
   %c3 \= constant <f32: 0.0\> : tile<2x4xf32\>
   %c4 \= constant <f64: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf64\>
 }
}

Copy to clipboard

### 11.2.3. cuda\_tile.extract\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-extract-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     // Extract a subtile from %t at dim\_0 = \[4;8) and dim\_1 = \[4;6).
     %c1 \= constant <i32: 1\> : tile<i32\>
     %c2 \= constant <i32: 2\> : tile<i32\>
     %t \= constant <f32: 0.0\> : tile<32x8xf32\>
     // Valid indices are: \[ {0, 1, 2, 3, 4, 5, 6, 7}, {0, 1, 2, 3} \]
     %0 \= extract %t\[%c1, %c2\]
         : tile<32x8xf32\> \-> tile<4x2xf32\>
  }
}

Copy to clipboard

### 11.2.4. cuda\_tile.get\_global\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-get-global-0 "Link to this heading")

cuda\_tile.module @module {
   global @val <f32: \[0.1, 0.2, 0.3, 0.4\]\> : tile<4xf32\>

   entry @example() {
     %ptr \= get\_global @val : tile<ptr<f32\>>
     return
   }
}

Copy to clipboard

### 11.2.5. cuda\_tile.get\_num\_tile\_blocks\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-get-num-tile-blocks-0 "Link to this heading")

cuda\_tile.module @module {
 entry @example() {
   %x, %y, %z \= get\_num\_tile\_blocks : tile<i32\>
   // print "x: %, y: %, z: %\\n", %x, %y, %z : tile<i32>, tile<i32>, tile<i32>
 }
}

Copy to clipboard

### 11.2.6. cuda\_tile.global\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-global-0 "Link to this heading")

cuda\_tile.module @module {
   global @val alignment \= 128 <f32: \[0.1, 0.2, 0.3, 0.4\]\> : tile<4xf32\>
   entry @example() {}
}

Copy to clipboard

### 11.2.7. cuda\_tile.permute\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-permute-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %arg0 \= constant <f16: 0.0\> : tile<2x4x8xf16\>
     %0 \= permute %arg0 \[2, 0, 1\] : tile<2x4x8xf16\> \-> tile<8x2x4xf16\>
  }
}

Copy to clipboard

### 11.2.8. cuda\_tile.reduce\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-reduce-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %input \= constant <f32: 0.0\> : tile<8xf32\>
     %0 \= reduce %input dim\=0 identities\=\[0.000000e+0 : f32\] : tile<8xf32\> \-> tile<f32\>
       (%input\_arg: tile<f32\>, %input\_accum: tile<f32\>) {
         %add\_result \= addf %input\_arg, %input\_accum : tile<f32\>
         yield %add\_result : tile<f32\>
       }
  }
}

Copy to clipboard

### 11.2.9. cuda\_tile.reduce\_1[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-reduce-1 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %input \= constant <f32: 0.0\> : tile<8x64xf32\>
     %0 \= reduce %input dim\=1 identities\=\[0.000000e+0 : f32\] : tile<8x64xf32\> \-> tile<8xf32\>
       (%input\_arg: tile<f32\>, %input\_accum: tile<f32\>) {
         %add\_result \= addf %input\_arg, %input\_accum : tile<f32\>
         yield %add\_result : tile<f32\>
       }
  }
}

Copy to clipboard

### 11.2.10. cuda\_tile.reshape\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-reshape-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %cst \= constant <i8: 0\> : tile<i8\>
     %0 \= reshape %cst
         : tile<i8\> \-> tile<1x1x1xi8\>

     %t \= constant <f32: 0.0\> : tile<8x2xf32\>
     %1 \= reshape %t
         : tile<8x2xf32\> \-> tile<2x2x4x1xf32\>
  }
}

Copy to clipboard

### 11.2.11. cuda\_tile.reshape\_1[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-reshape-1 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %cst \= constant <i32: \[\[0, 1, 2, 3\], \[4, 5, 6, 7\]\]\>
         : tile<2x4xi32\>
     %r0 \= reshape %cst
   : tile<2x4xi32\> \-> tile<2x2x2xi32\>

   // Step 1: Turn source into 1D tile. Use row-major by convention.
   // %tmp: \[0, 1, 2, 3, 4, 5, 6, 7\]
   %tmp \= reshape %cst
       : tile<2x4xi32\> \-> tile<8xi32\>

   // Step 2: Turn 1D tile into result tile. Use row-major by convention.
   // %r: \[\[\[0, 1\], \[2, 3\]\], \[\[4, 5\], \[6, 7\]\]\]
   %r1 \=  reshape %tmp
           : tile<8xi32\> \-> tile<2x2x2xi32\>

  }
}

Copy to clipboard

### 11.2.12. cuda\_tile.scan\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-scan-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
    %input \= constant <f32: 0.0\> : tile<8x16xf32\>
    %result \= scan %input dim\=1 reverse\=false identities\=\[1.0 : f32\] : tile<8x16xf32\> \-> tile<8x16xf32\>
    (%acc: tile<f32\>, %elem: tile<f32\>) {
      %prod \= mulf %acc, %elem rounding<nearest\_even\>: tile<f32\>
      yield %prod : tile<f32\>
    }
   }
  }

Copy to clipboard

### 11.2.13. cuda\_tile.assert\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-assert-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%arg0: tile<i1\>) {
     assert %arg0, "assertion failed" : tile<i1\>
  }
}

Copy to clipboard

### 11.2.14. cuda\_tile.break\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-break-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
   // Break from the body of a loop.
   loop {
       break
   }

   // Break from an if nested within the loop.
   loop  {
       %condition \= constant <i1: 1\> : tile<i1\>
       if %condition  {
           break
       }
       // ...
   }

   %initValue0 \= constant <f32: 0.0\> : tile<f32\>
   // Break from an if nested within the loop, while yielding values.
   %results \= loop iter\_values(%var0 \= %initValue0): tile<f32\> \-> tile<f32\> {
       %condition \= constant <i1: 1\> : tile<i1\>
       if %condition  {
           // ...
           yield
       } else {
           // %if.loopValue0 = ...
           %loopValue0 \= constant <f32: 1.0\> : tile<f32\>
           break %loopValue0 : tile<f32\>
       }
       %loopValue1 \= constant <f32: 1.0\> : tile<f32\>
       continue %loopValue1 : tile<f32\>
   }
  }
}

Copy to clipboard

### 11.2.15. cuda\_tile.continue\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-continue-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %lowerBound \= constant <i32: 0\> : tile<i32\>
     %upperBound \= constant <i32: 10\> : tile<i32\>
     %step \= constant <i32: 1\> : tile<i32\>
     %condition \= constant <i1: 1\> : tile<i1\>
     // Continue from the body of a loop.
     for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\> {
         continue
     }

     // Continue from an if nested within the loop.
     for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\> {
         if %condition  {
             continue
         }
         // ...
     }

   // Continue from an if nested within the loop, while yielding values.
   %initVar0 \= constant <f32: 0.0\> : tile<f32\>
   %results \= for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\>
             iter\_values(%var0 \= %initVar0) \-> (tile<f32\>)
     {
         if %condition {
             // ...
             yield
         } else {
             %loopValue0 \= constant <f32: 1.0\> : tile<f32\>
             continue %loopValue0 : tile<f32\>
         }
         %loopValue1 \= constant <f32: 1.0\> : tile<f32\>
         continue %loopValue1 : tile<f32\>
     }
  }
}

Copy to clipboard

### 11.2.16. cuda\_tile.for\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-for-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %lowerBound \= constant <i32: 0\> : tile<i32\>
     %upperBound \= constant <i32: 10\> : tile<i32\>
     %step \= constant <i32: 1\> : tile<i32\>

     // A simple loop iterating over an i32 range.
     for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\> {
         continue
     }

     %initVal0 \= constant <f32: 0.0\> : tile<f32\>
     // A similar loop to the above, but with a loop carried value, val0.
     %results \= for %iv in (%lowerBound to %upperBound, step %step) : tile<i32\>
                         iter\_values(%val00 \= %initVal0) \-> (tile<f32\>) {
       %loopVal0 \= constant <f32: 1.0\> : tile<f32\>
       continue %loopVal0 : tile<f32\>
     }
  }
}

Copy to clipboard

### 11.2.17. cuda\_tile.if\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-if-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %condition \= constant <i1: 1\> : tile<i1\>

     // A simple if operation that conditionally executes a region.
     if %condition  {
       // ...
     }

     // An if operation with an "else" branch.
     if %condition  {
       // ...
     } else {
       // ...
     }

     // An if operation that returns mixed types (f32,i32)
     %x, %y \= if %condition \-> (tile<f32\>, tile<i32\>) {
       %x\_then \= constant <f32: 1.0\> : tile<f32\>
       %y\_then \= constant <i32: 2\> : tile<i32\>
       yield %x\_then, %y\_then : tile<f32\>, tile<i32\>
     } else {
       %x\_then \= constant <f32: 1.0\> : tile<f32\>
       %y\_then \= constant <i32: 42\> : tile<i32\>
       yield %x\_then, %y\_then : tile<f32\>, tile<i32\>
     }
  }
}

Copy to clipboard

### 11.2.18. cuda\_tile.loop\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-loop-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     // A simple "while-do" loop.
     loop {
         %cond \= constant <i1: 1\> : tile<i1\>
         if %cond {
             continue
         }
         break
     }
  }
}

Copy to clipboard

### 11.2.19. cuda\_tile.loop\_1[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-loop-1 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     // A simple "do-while" loop.
     loop {
         //... body of the loop.

         %cond \= constant <i1: 1\> : tile<i1\>
         if %cond {
             continue
         }
         break
     }
  }
}

Copy to clipboard

### 11.2.20. cuda\_tile.loop\_2[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-loop-2 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %initValue0 \= constant <f32: 0.0\> : tile<f32\>
     // A loop that yields carried-iteration values, returning the final values.
     %results \= loop iter\_values(%value0 \= %initValue0) : tile<f32\> \-> tile<f32\> {
         %cond \= constant <i1: 1\> : tile<i1\>
         if %cond {
             %loopValue0 \= constant <f32: 0.0\> : tile<f32\>
             continue %loopValue0 : tile<f32\>
         }
         break %value0 : tile<f32\>
     }
  }
}

Copy to clipboard

### 11.2.21. cuda\_tile.loop\_3[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-loop-3 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %initValue0 \= constant <i32: 0\> : tile<i32\>
     // A loop that uses loop-carried values and returns a different type.
     %results \= loop iter\_values(%value0 \= %initValue0) : tile<i32\> \-> tile<f32\> {
         %cond \= constant <i1: 1\> : tile<i1\>

         if %cond {
             %newLoopValue \= constant <i32: 0\> : tile<i32\>
             continue %newLoopValue : tile<i32\>
         }

         %finalReturnValue \= constant <f32: 0.0\> : tile<f32\>
         break %finalReturnValue : tile<f32\>
     }
  }
}

Copy to clipboard

### 11.2.22. cuda\_tile.return\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-return-0 "Link to this heading")

cuda\_tile.module @module {
   entry @foo() {
     %0 \= constant <i32: 0\> : tile<i32\>
     %1 \= constant <f16: 0.0\> : tile<f16\>
     // ...
     return
   }
}

Copy to clipboard

### 11.2.23. cuda\_tile.yield\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-yield-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %condition \= constant <i1: true\> : tile<i1\>
     // Yield from the body of an if conditional.
     if %condition  {
         yield
     }

     // Yield values from within an if conditional.
     %x, %y \= if %condition \-> (tile<f32\>, tile<f32\>) {
         %x\_then \= constant <f32: 0.0\> : tile<f32\>
         %y\_then \= constant <f32: 1.0\> : tile<f32\>
         yield %x\_then, %y\_then : tile<f32\>, tile<f32\>
     } else {
         %x\_else \= constant <f32: 2.0\> : tile<f32\>
         %y\_else \= constant <f32: 3.0\> : tile<f32\>
         yield %x\_else, %y\_else : tile<f32\>, tile<f32\>
     }
  }
}

Copy to clipboard

### 11.2.24. cuda\_tile.load\_ptr\_tko\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-load-ptr-tko-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%ptr: tile<ptr<f32\>>) {
     %mask \= constant <i1: 1\> : tile<i1\>
     %padding \= constant <f32: 0.0\> : tile<f32\>

       // Load without token.
       %result0, %res\_token0 \= load\_ptr\_tko weak %ptr, %mask, %padding
           : tile<ptr<f32\>>, tile<i1\>, tile<f32\> \-> tile<f32\>, token

       // Load with token.
       %token0 \= make\_token : token
       %result1, %res\_token1 \= load\_ptr\_tko weak %ptr, %mask, %padding token\=%token0
           : tile<ptr<f32\>>, tile<i1\>, tile<f32\> \-> tile<f32\>, token

       return
  }
}

Copy to clipboard

### 11.2.25. cuda\_tile.atan2\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-atan2-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_atan2() {
   %x \= constant <f32: \[1.0, \-1.0, 0.0, 2.0\]\> : tile<4xf32\>
   %y \= constant <f32: \[1.0,  1.0, 1.0, 0.0\]\> : tile<4xf32\>
   %res \= atan2 %x, %y : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.26. cuda\_tile.ceil\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-ceil-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
    %source \= constant <f32: 0.5\> : tile<f32\>
   %result \= ceil %source : tile<f32\>
  }
}

Copy to clipboard

### 11.2.27. cuda\_tile.cmpf\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-cmpf-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example() {
     %lhs0 \= constant <f16: 0.0\> : tile<f16\>
     %rhs0 \= constant <f16: 0.0\> : tile<f16\>

     // Custom form of scalar "ordered equal" comparison.
     %x0 \= cmpf equal ordered %lhs0, %rhs0 : tile<f16\> \-> tile<i1\>

     %lhs1 \= constant <f16: 0.0\> : tile<2x2xf16\>
     %rhs1 \= constant <f16: 0.0\> : tile<2x2xf16\>

     // Custom form of scalar "unordered less than" comparison.
     %x2 \= cmpf less\_than unordered %lhs1, %rhs1 : tile<2x2xf16\> \-> tile<2x2xi1\>

     %lhs2 \= constant <f64: 0.0\> : tile<2x2xf64\>
     %rhs2 \= constant <f64: 0.0\> : tile<2x2xf64\>
  }
}

Copy to clipboard

### 11.2.28. cuda\_tile.cos\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-cos-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_cos() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res \= cos %in : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.29. cuda\_tile.exp2\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-exp2-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_exp2() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res \= exp2 %in : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.30. cuda\_tile.exp\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-exp-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_exp() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res \= exp %in : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.31. cuda\_tile.floor\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-floor-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %source \= constant <f32: 1.5\> : tile<f32\>
     %result \= floor %source : tile<f32\>
  }
}

Copy to clipboard

### 11.2.32. cuda\_tile.log2\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-log2-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_log2() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res \= log2 %in : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.33. cuda\_tile.maxf\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-maxf-0 "Link to this heading")

cuda\_tile.module @module {
    entry @example\_maxf(%arg0: tile<ptr<f32\>>, %arg1: tile<ptr<f32\>>) {
       // Create tensor view from a pointer to global memory
       %0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
       %1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
       // Convert tensor views to partition views and load tiles from partition views.
       %p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
       %p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
       %c0 \= constant <i32: 0\> : tile<i32\>
       %2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
       %3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
       // IEEE 754-2019's maximum
       %4 \= maxf %2, %3 propagate\_nan : tile<2x4xf32\>
       // IEEE 754-2019's maximumNumber
       %5 \= maxf %2, %3 : tile<2x4xf32\>
       // flush denormal to positive zero
       %6 \= maxf %2, %3 flush\_to\_zero : tile<2x4xf32\>
  }
}

Copy to clipboard

### 11.2.34. cuda\_tile.minf\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-minf-0 "Link to this heading")

cuda\_tile.module @module {
    entry @example\_minf(%arg0: tile<ptr<f32\>>, %arg1: tile<ptr<f32\>>) {
       // Create tensor view from a pointer to global memory
       %0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
       %1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xf32, strides\=\[4,1\]\>
       // Convert tensor views to partition views and load tiles from partition views.
       %p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
       %p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>
       %c0 \= constant <i32: 0\> : tile<i32\>
       %2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
       %3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xf32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xf32\>, token
       // IEEE 754-2019's minimum
       %4 \= minf %2, %3 propagate\_nan : tile<2x4xf32\>
       // IEEE 754-2019's minimumNumber
       %5 \= minf %2, %3 : tile<2x4xf32\>
       // flush denormal to positive zero
       %6 \= minf %2, %3 flush\_to\_zero : tile<2x4xf32\>
  }
}

Copy to clipboard

### 11.2.35. cuda\_tile.mmaf\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-mmaf-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %lhs0 \= constant <f16: 0.0\> : tile<4x8xf16\>
     %rhs0 \= constant <f16: 0.0\> : tile<8x2xf16\>
     %acc0 \= constant <f32: 0.0\> : tile<4x2xf32\>

     %0 \= mmaf %lhs0, %rhs0, %acc0
         : tile<4x8xf16\>, tile<8x2xf16\>,
           tile<4x2xf32\>

     %lhs1 \= constant <f16: 0.0\> : tile<2x4x8xf16\>
     %rhs1 \= constant <f16: 0.0\> : tile<2x8x2xf16\>
     %acc1 \= constant <f32: 0.0\> : tile<2x4x2xf32\>

     %1 \= mmaf %lhs1, %rhs1, %acc1
         : tile<2x4x8xf16\>, tile<2x8x2xf16\>,
           tile<2x4x2xf32\>
  }
}

Copy to clipboard

### 11.2.36. cuda\_tile.negf\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-negf-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %source \= constant <f32: 0.0\> : tile<4xf32\>
     %result \= negf %source : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.37. cuda\_tile.pow\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-pow-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %source \= constant <f32: 0.0\> : tile<4xf32\>
     %exponent \= constant <f32: 2.0\> : tile<4xf32\>
     %result \= pow %source, %exponent : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.38. cuda\_tile.rsqrt\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-rsqrt-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_rsqrt() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res \= rsqrt %in : tile<4xf32\>

   // Rsqrt op with flush to zero modifier
   %ftz\_res \= rsqrt %in flush\_to\_zero : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.39. cuda\_tile.sin\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-sin-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_sin() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res \= sin %in : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.40. cuda\_tile.tanh\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-tanh-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_tanh() {
   %in \= constant <f32: \[0.0, 1.0, 2.0, 3.0\]\> : tile<4xf32\>
   %res0 \= tanh %in : tile<4xf32\>

   // tanh with approx modifier
   %res1 \= tanh %in rounding<approx\> : tile<4xf32\>
  }
}

Copy to clipboard

### 11.2.41. cuda\_tile.cmpi\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-cmpi-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %lhs0 \= constant <i16: 0\> : tile<i16\>
     %rhs0 \= constant <i16: 0\> : tile<i16\>

     // Scalar "signed less than" comparison.
     %x0 \= cmpi less\_than %lhs0, %rhs0, signed : tile<i16\> \-> tile<i1\>

     %lhs1 \= constant <i64: 0\> : tile<2x2xi64\>
     %rhs1 \= constant <i64: 0\> : tile<2x2xi64\>

     // Tile equality comparison.
     // There is no difference between "signed" and "unsigned" when performing equality and inequality comparison.
     %x1 \= cmpi equal %lhs1, %rhs1, signed : tile<2x2xi64\> \-> tile<2x2xi1\>
  }
}

Copy to clipboard

### 11.2.42. cuda\_tile.maxi\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-maxi-0 "Link to this heading")

cuda\_tile.module @module {
    entry @example\_maxi(%arg0: tile<ptr<i32\>>, %arg1: tile<ptr<i32\>>) {
       // Create tensor view from a pointer to global memory
       %0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
       %1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
       // Convert tensor views to partition views and load tiles from them.
       %p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
       %p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
       %c0 \= constant <i32: 0\> : tile<i32\>
       %2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
       %3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
       // Signless i32 treated as unsigned
       %4 \= maxi %2, %3 unsigned : tile<2x4xi32\>
       // Signless i32 treated as signed
       %5 \= maxi %2, %3 signed : tile<2x4xi32\>
  }
}

Copy to clipboard

### 11.2.43. cuda\_tile.mini\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-mini-0 "Link to this heading")

cuda\_tile.module @module {
    entry @example\_mini(%arg0: tile<ptr<i32\>>, %arg1: tile<ptr<i32\>>) {
       // Create tensor view from a pointer to global memory
       %0 \= make\_tensor\_view %arg0, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
       %1 \= make\_tensor\_view %arg1, shape \= \[2, 4\], strides \= \[4, 1\] : tensor\_view<2x4xi32, strides\=\[4,1\]\>
       // Convert tensor views to partition views and load tiles from partition views.
       %p0 \= make\_partition\_view %0 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
       %p1 \= make\_partition\_view %1 : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>
       %c0 \= constant <i32: 0\> : tile<i32\>
       %2, %token0 \= load\_view\_tko weak %p0\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
       %3, %token1 \= load\_view\_tko weak %p1\[%c0, %c0\] : partition\_view<tile\=(2x4), tensor\_view<2x4xi32, strides\=\[4,1\]\>>, tile<i32\> \-> tile<2x4xi32\>, token
       // Signless i32 treated as unsigned
       %4 \= mini %2, %3 unsigned : tile<2x4xi32\>
       // Signless i32 treated as signed
       %5 \= mini %2, %3 signed : tile<2x4xi32\>
  }
}

Copy to clipboard

### 11.2.44. cuda\_tile.mmai\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-mmai-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %lhs0 \= cuda\_tile.constant <i8: 0\> : tile<4x8xi8\>
     %rhs0 \= cuda\_tile.constant <i8: 0\> : tile<8x2xi8\>
     %acc0 \= cuda\_tile.constant <i32: 0\> : tile<4x2xi32\>

     %0 \= mmai %lhs0, %rhs0, %acc0 signed signed
         : tile<4x8xi8\>, tile<8x2xi8\>,
           tile<4x2xi32\>

     %lhs1 \= cuda\_tile.constant <i8: 0\> : tile<2x4x8xi8\>
     %rhs1 \= cuda\_tile.constant <i8: 0\> : tile<2x8x2xi8\>
     %acc1 \= cuda\_tile.constant <i32: 0\> : tile<2x4x2xi32\>

     %1 \= mmai %lhs1, %rhs1, %acc1 unsigned unsigned
         : tile<2x4x8xi8\>, tile<2x8x2xi8\>,
           tile<2x4x2xi32\>
  }
}

Copy to clipboard

### 11.2.45. cuda\_tile.mulhii\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-mulhii-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     // 2^31 \* 2 = 2^32, or 0x100000000.
     // The most significant 32 bits of the product are 0x00000001.
     // The lower 32 bits of the product are 0x00000000.
     %a \= constant <i32: 2147483648\> : tile<i32\>  // %a = 2^31
     %b \= constant <i32: 2\> : tile<i32\>           // %b = 2
     %res\_hi \= mulhii %a, %b : tile<i32\>          // %res\_hi = 1
     %res\_lo \= muli %a, %b : tile<i32\>            // %res\_lo = 0
  }
}

Copy to clipboard

### 11.2.46. cuda\_tile.negi\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-negi-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %source \= constant <i16: \[0, 1, 2, 3\]\> : tile<4xi16\>
     %result \= negi %source : tile<4xi16\>
     // %result = \[0, -1, -2, -3\]
  }
}

Copy to clipboard

### 11.2.47. cuda\_tile.xori\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-xori-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
     %lhs \= constant <i32: \[0, 1, 2, 3\]\> : tile<4xi32\>
     %rhs \= constant <i32: \[4, 5, 6, 7\]\> : tile<4xi32\>
     // This computes the bitwise XOR of each element in \`%lhs\` and \`%rhs\`, which
     // are tiles of shape \`4xi32\`, and returns the result as \`%result\`.
     %result \= xori %lhs, %rhs : tile<4xi32\>
  }
}

Copy to clipboard

### 11.2.48. cuda\_tile.atomic\_cas\_tko\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-atomic-cas-tko-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example(%ptr: tile<ptr<i32\>>) {
   %ptr\_1x \= reshape %ptr : tile<ptr<i32\>> \-> tile<1xptr<i32\>>
   %ptr\_vec \= broadcast %ptr\_1x : tile<1xptr<i32\>> \-> tile<8xptr<i32\>>
   %offsets \= iota : tile<8xi32\>
   %ptrs \= offset %ptr\_vec, %offsets : tile<8xptr<i32\>>, tile<8xi32\> \-> tile<8xptr<i32\>>
   %cmp \= constant <i32: \[0, 1, 2, 3, 4, 5, 6, 7\]\> : tile<8xi32\>
   %val \= constant <i32: \[7, 6, 5, 4, 3, 2, 1, 0\]\> : tile<8xi32\>
   %mask \= constant <i1: \[0, 1, 0, 1, 0, 1, 0, 1\]\> : tile<8xi1\>

   // Atomic CAS without input token.
   %0, %token \= atomic\_cas\_tko relaxed device %ptrs, %cmp, %val :
     tile<8xptr<i32\>>, tile<8xi32\> \-> tile<8xi32\>, token

   // Atomic CAS without input token.
   %1, %token1 \= atomic\_cas\_tko relaxed device %ptrs, %cmp, %val, %mask :
     tile<8xptr<i32\>>, tile<8xi32\>, tile<8xi1\> \-> tile<8xi32\>, token

   // Atomic CAS with input token.
   %token2 \= make\_token : token
   %2, %token3 \= atomic\_cas\_tko relaxed device %ptrs, %cmp, %val token\=%token2 :
     tile<8xptr<i32\>>, tile<8xi32\> \-> tile<8xi32\>, token

   return
  }
}

Copy to clipboard

### 11.2.49. cuda\_tile.atomic\_rmw\_tko\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-atomic-rmw-tko-0 "Link to this heading")

cuda\_tile.module @ex\_module {
  entry @example\_rmw(%ptr: tile<ptr<f32\>>) {
   // Reshape the input pointer tile to have a 1d shape
   %ptr\_1x \= reshape %ptr : tile<ptr<f32\>> \-> tile<1xptr<f32\>>
   // Broadcast the reshaped tile to a tile with 8 rows, effectively replicating the pointer 8 times
   %ptr\_vec \= broadcast %ptr\_1x : tile<1xptr<f32\>> \-> tile<8xptr<f32\>>
   // Create a tile of offsets \[0, 1, 2, ..., 7\] to index into memory
   %offsets \= iota : tile<8xi32\>
   // Add the offsets to each pointer in the vector to create 8 unique pointers
   %ptrs \= offset %ptr\_vec, %offsets : tile<8xptr<f32\>>, tile<8xi32\> \-> tile<8xptr<f32\>>
   %vals \= constant <f32: \[7.0, 6.0, 5.0, 4.0, 3.0, 2.0, 1.0, 0.0\]\> : tile<8xf32\>

   // Perform atomic addf operations on the memory locations pointed by %ptrs
   // without requiring an input token. Returns the original values and a result token
   %0, %res\_token0 \= atomic\_rmw\_tko relaxed device %ptrs, addf, %vals :
       tile<8xptr<f32\>>, tile<8xf32\> \-> tile<8xf32\>, token

   // Perform atomic add operations again, this time using the explicit input token
   %token \= make\_token : token
   %1, %res\_token1 \= atomic\_rmw\_tko relaxed device %ptrs, addf, %vals, token \= %token :
       tile<8xptr<f32\>>, tile<8xf32\> \-> tile<8xf32\>, token
  }
}

Copy to clipboard

### 11.2.50. cuda\_tile.get\_index\_space\_shape\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-get-index-space-shape-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%base: tile<ptr<f32\>>) {
   %tensor\_view \= make\_tensor\_view %base,
       shape \= \[2, 2, 4\], strides \= \[2, 2, 1\]
       : tensor\_view<2x2x4xf32, strides\=\[2,2,1\]\>
   %partition\_view \= make\_partition\_view %tensor\_view :
     partition\_view<tile\=(2x2x4), tensor\_view<2x2x4xf32, strides\=\[2,2,1\]\>>
   %dim0, %dim1, %dim2 \= get\_index\_space\_shape %partition\_view :
     partition\_view<tile\=(2x2x4), tensor\_view<2x2x4xf32, strides\=\[2,2,1\]\>> \-> tile<i64\>
  }
}

Copy to clipboard

### 11.2.51. cuda\_tile.get\_tensor\_shape\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-get-tensor-shape-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%base: tile<ptr<f32\>>) {
    %tensor\_view \= make\_tensor\_view %base,
        shape \= \[32, 32\], strides \= \[32, 1\]
        : tensor\_view<32x32xf32, strides\=\[32,1\]\>
   %dim0, %dim1 \= get\_tensor\_shape %tensor\_view : tensor\_view<32x32xf32, strides\=\[32,1\]\> \-> tile<i64\>
  }
}

Copy to clipboard

### 11.2.52. cuda\_tile.load\_view\_tko\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-load-view-tko-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%ptr: tile<ptr<f32\>>, %index: tile<i32\>) {
     %tensor\_view \= make\_tensor\_view %ptr, shape\=\[8192, 128\], strides\=\[128, 1\]
       : tensor\_view<8192x128xf32, strides\=\[128,1\]\>

     // This example uses the PartitionView on a 8192x128xf32 tensor\_view,
     // dividing the tensor\_view in tiles of 64x64.

     %view \= make\_partition\_view %tensor\_view : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>

     %c0 \= constant <i32: 0\> : tile<i32\>
     %c1 \= constant <i32: 1\> : tile<i32\>

     // Load a tile at index (0, 0) in the view's index space.
     // For this PartitionView, this is the rectangular tile such that
     // X=\[0,64) and Y=\[0,64), in the coordinates of tiles.
     %tile0, %res\_token0 \= load\_view\_tko weak %view\[%c0, %c0\]
       : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

     // Load a tile at index (0, 1) in the view's index space.
     // For this PartitionView, this is the rectangular tile such that
     // X=\[0,64) and Y=\[64,128), in the coordinates of tiles.
     %tile1, %res\_token1 \= load\_view\_tko weak %view\[%c0, %c1\]
       : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

     // Same example as above but with memory token as input.
     %token \= make\_token : token
     %tile2, %res\_token2 \= load\_view\_tko weak %view\[%c0, %c1\] token \= %token
       : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token

     // Loads a tile at the dynamic index (%index, %index) in the view's index space.
     %tile3, %res\_token3 \= load\_view\_tko weak %view\[%index, %index\]
       : partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> tile<64x64xf32\>, token
  }
}

Copy to clipboard

### 11.2.53. cuda\_tile.make\_partition\_view\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-make-partition-view-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%ptr: tile<ptr<f32\>>) {

     %tensor\_view0 \= make\_tensor\_view %ptr, shape\=\[8192, 8192, 64\], strides\=\[524288,64,1\]
       : tensor\_view<8192x8192x64xf32, strides\=\[524288,64,1\]\>

     // Creates a partition with 32-bit-indexed tiles of size (1024x1x32) over
     // the provided tensor\_view.
     make\_partition\_view %tensor\_view0 :
       partition\_view<
         tile\=(1024x1x32),
         tensor\_view<8192x8192x64xf32, strides\=\[524288,64,1\]\>
       \>

     %s0 \= constant <i32: 8192\> : tile<i32\>
     %str0 \= constant <i32: 524288\> : tile<i32\>

     %tensor\_view1 \= make\_tensor\_view %ptr, shape\=\[%s0, 8192, 64\], strides\=\[%str0, 64, 1\]
       : tile<i32\> \-> tensor\_view<?x8192x64xf32, strides\=\[?,64,1\]\>

     // Creates a partition with 32-bit-indexed tiles of size (1024x1x32) over
     // the provided tensor\_view. The provided tensor\_view has a
     // dynamically-sized dimension.
     make\_partition\_view %tensor\_view1 :
       partition\_view<tile\=(1024x1x32), tensor\_view<?x8192x64xf32, strides\=\[?,64,1\]\>>
  }
}

Copy to clipboard

### 11.2.54. cuda\_tile.make\_tensor\_view\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-make-tensor-view-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%base: tile<ptr<f32\>>) {
     // tensor\_view to a scalar tile of f32
     %a0 \= make\_tensor\_view %base,
         shape \= \[\], strides \= \[\] : tensor\_view<f32\>

     // tensor\_view to a tile of static shape and strides
     %a1 \= make\_tensor\_view %base,
         shape \= \[32, 32\], strides \= \[32, 1\]
         : tensor\_view<32x32xf32, strides\=\[32,1\]\>

   %sh0 \= constant <i32: 32\> : tile<i32\>
   %sh1 \= constant <i32: 32\> : tile<i32\>
   %st0 \= constant <i32: 32\> : tile<i32\>
   %st1 \= constant <i32: 1\> : tile<i32\>

     // tensor\_view to a tile with partially dynamic shape and strides
     // all dynamic values must be of the same type, here tile<i32>
     %a2 \= make\_tensor\_view %base,
             shape \= \[%sh0, %sh1\], strides \= \[%st0, %st1\]
             : tile<i32\> \-> tensor\_view<?x?xf32, strides\=\[?,?\]\>
  }
}

Copy to clipboard

### 11.2.55. cuda\_tile.store\_view\_tko\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-store-view-tko-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%ptr: tile<ptr<f32\>>) {
     %tensor\_view \= make\_tensor\_view %ptr, shape\=\[8192, 128\], strides\=\[128,1\] :
       tensor\_view<8192x128xf32, strides\=\[128,1\]\>

     // This example uses the PartitionView on a 8192x128xf32 tensor\_view,
     // dividing the tensor\_view in tiles of 64x64.
     %view \= make\_partition\_view %tensor\_view :
       partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>

     %c0 \= constant <i32: 0\> : tile<i32\>
     %c1 \= constant <i32: 1\> : tile<i32\>

     %tile \= constant <f32: 0.0\> : tile<64x64xf32\>

     // Store a tile at index (0, 0) in the view's index space.
     // For this TilePartitionView, this is the rectangular tile such that
     // X=\[0,64) and Y=\[0,64), in the coordinates of tiles.
     %res\_token0 \= store\_view\_tko weak %tile, %view\[%c0, %c0\]
       : tile<64x64xf32\>, partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> token

     // Store a tile at index (0, 1) in the view's index space.
     // For this PartitionView, this is the rectangular tile such that
     // X=\[0,64) and Y=\[64,128), in the coordinates of tiles.
     %res\_token1 \= store\_view\_tko weak %tile, %view\[%c0, %c1\]
       : tile<64x64xf32\>, partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> token

     // Same example as above but with input token.
     %token \= make\_token : token
     %res\_token2 \= store\_view\_tko weak %tile, %view\[%c0, %c1\] token \= %token
       : tile<64x64xf32\>, partition\_view<tile\=(64x64), tensor\_view<8192x128xf32, strides\=\[128,1\]\>>, tile<i32\> \-> token
    }
  }

Copy to clipboard

### 11.2.56. cuda\_tile.assume\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-assume-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example(%input: tile<ptr<f32\>>) {
   // Assume that all integers are divisible by 32.
   %int\_tile \= constant <i16: \[32, 64, 0, 0, 32, \-32, 1024, 0\]\> : tile<8xi16\>
   %div\_by\_1 \= assume div\_by<32\>, %int\_tile : tile<8xi16\>

   // Assume that every 4th element (starting with element 0) along
   // dimension 0 is divisible by 32 that and all integers are
   // montonically increasing by 1 within each group of 4.
   %int\_tile\_2 \= constant <i16: \[96, 97, 98, 99, 64, 65, 66, 67\]\> : tile<8xi16\>
   %div\_by\_2 \= assume div\_by<32, every 4 along 0\>, %int\_tile\_2 : tile<8xi16\>

   // Assume that every rectangular chunk of size \[1, 4, 2\] has the same
   // values.
    %input\_rank3 \= reshape %input : tile<ptr<f32\>> \-> tile<1x1x1xptr<f32\>>
    %ptr\_3d \= broadcast %input\_rank3 : tile<1x1x1xptr<f32\>> \-> tile<1x8x8xptr<f32\>>
   %same\_elem \= assume same\_elements<\[1, 4, 2\]\>, %ptr\_3d : tile<1x8x8xptr<f32\>>

   // Assume that every value is greater or equal to 5.
   %int\_tile\_3 \= constant <i16: \[5, 9, 10, 11, 6, 5, 5, 7\]\> : tile<8xi16\>
   %bounded \= assume bounded<5, ?\>, %int\_tile\_3 : tile<8xi16\>
  }
}

Copy to clipboard

### 11.2.57. cuda\_tile.print\_tko\_0[#](https://docs.nvidia.com/cuda/tile-ir/13.2/sections/appendix.html#cuda-tile-print-tko-0 "Link to this heading")

cuda\_tile.module @module {
  entry @example() {
      %arg \= constant <f32: 0.0\> : tile<4xf32\>
     print\_tko "Hello world: %f\\n", %arg : tile<4xf32\> \-> token
     print\_tko "%+08.3f", %arg : tile<4xf32\> \-> token
  }
}
