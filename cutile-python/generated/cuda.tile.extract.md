# cuda.tile.extract



### `cuda.tile.extract(x, /, index, shape)`

Extracts a smaller tile from input tile.
Partition the input tile into a grid with subtile shape
and return a tile given the index into the grid. Similar
to load() but performed on a tile.

Parameters:

x (Tile) – input tile.
index (Shape) – An index in the sub tile space.
shape (Shape) – The shape of the extracted tile.

Return type:
Tile

Examples
>>> tile = ct.full((8, 8), 3.14, dtype=ct.float32)
>>> sub_tile = ct.extract(x, (0, 0), shape=(4, 4))
>>> sub_tile.shape
(4, 4)