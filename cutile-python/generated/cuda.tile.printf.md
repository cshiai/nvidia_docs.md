# cuda.tile.printf



### `cuda.tile.printf(format, *args)`

Print the values at runtime from the device

Parameters:

format (str) – a c-printf style format string
in the form of %[flags][width][.precision][length]specifier,
where specifier is limited to integer and float for now, i.e.
[diuoxXeEfFgGaA]
*args (tuple[Tile, ...]) – Only tile input is supported.

Examples
>>> tile = ct.arange(4, dtype=ct.int32)
>>> ct.printf("one tile: %d", tile)
>>> ct.printf("two tiles: %d, %f", tile, tile * 2.0)

Notes
This operation has significant overhead, and should only be used
for debugging purpose.
When printing from multiple tile blocks, outputs will be interleaved.
One workaround is to set optimization level to 0:
@ct.kernel(opt_level=0)
def my_print_kernel():
    ct.printf("%d", 123)