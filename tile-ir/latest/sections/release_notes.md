# 12. Release Notes


## 12.1. Known Issues


 - The programming model is missing a section on a cross-tile block kernel such as split-k.
 - The bytecode section does not provide exact encoding of each operation, expect this to be introduced in a future release.
 - The semi-formal memory model section is written but does not provide detailed examples of how to to utilize it.
 - Atomics are currently limited in Tile IR and will be expanded in a future release.


## 12.2. Changelog


### 12.2.1. Spec 13.1 (2025-12-08)


#### Bugfixes


 - Fixed typo in the type section, where the tile size was incorrectly specified as 128x64 instead of 128x4.


#### Improved Documentation


 - Fixed numerous small typos
 - Strengthen the wording around the stability of the textual format of Tile IR.