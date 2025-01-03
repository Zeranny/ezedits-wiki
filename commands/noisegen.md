# Noisegen

All sub-commands are under `//eznoisegen` (`//noisegen`, `//ng`)\
e.g `//ng heightmap`

## `//eznoisegen ...`

### heightmap

<details>

<summary>Heightmap (2D)</summary>

**`//eznoisegen heightmap <palette> <noise> [height] [-z <zoom>] [-s <seed>] [-o <offset>] [-ct]`**

* **Palette**: Specifies the palette of blocks to use.
* **Noise**: Defines the noise preset to use.
* **Height** (Default: 0): Controls the height from the bottom of your selection. A value of 0 will take the selection's height. _Can place blocks above the selection if the height is great enough_
* **-z** (Default: 1): Adjusts the zoom level of the noise.
* **-s** (Default: -1): Sets the noise seed.
* **-o** (Default: (0,0,0)): Offsets the noise generation coordinates by a given vector (X,Y,Z).
* **-c**: When used, centres the noise generation on the world coordinates of the selection.
* **-t**: Enables smooth mode, specifically for snow, water, and lava blocks in the palette \[Applicable only in heightmap mode].

</details>

### terrain

<details>

<summary>Terrain (3D)</summary>

**`//eznoisegen terrain <palette> <noise> [height] [strength] [-z <scale>] [-s <seed>] [-l <smear>] [-o <offset>] [-c]`**

* **Palette**: Specifies the palette of blocks to use.
* **Noise**: Defines the noise preset to use.
* **Height** (Default: 0): Controls the height from the bottom of your selection. A value of 0 will take the selection's height. _Can place blocks above the selection if the height is great enough_
* **Strength** (Default: 1,0.5,0): Takes up to 3 comma-separated values which controls the strength of noise at various heights:
  * _`0.5` would be 50% strength everywhere_
  * _`0.7,0` would be 70% strength at the very bottom and 0% at the top, with everything in-between being a smooth transition_
  * _`0,1,0` would be 0% strength at the bottom, 100% in the middle, and 0% at the top_
* **-z** (Default: 1): Adjusts the zoom level of the noise.
* **-s** (Default: -1): Sets the noise seed.
* **-l** (Default: 0): Applies a vertical smear to 3D noise.
* **-o** (Default: (0,0,0)): Offsets the noise generation coordinates by a given vector (X,Y,Z).
* **-c**: When used, centres the noise generation on the world coordinates of the selection.

</details>

### advanced

<details>

<summary>Advanced</summary>

**`//eznoisegen <palette> <noise> [lowerThreshold] [upperThreshold] [-z <scale>] [-s <seed>] [-l <smear>] [-o <offset>] [-chnt]`**

* **Palette**: Specifies the palette of blocks to use.
* **Noise**: Defines the noise preset to use.
* **Lower Threshold** (Default: 0): Sets the lower threshold for noise generation, with support for WorldEdit expressions (range: 0-1.0).
* **Upper Threshold** (Default: 0.5): Sets the upper threshold for noise generation, with support for WorldEdit expressions (range: 0-1.0).
* **-z** (Default: 1): Adjusts the zoom level of the noise.
* **-s** (Default: -1): Sets the noise seed.
* **-l** (Default: 0): Applies a vertical smear to 3D noise.
* **-o** (Default: (0,0,0)): Offsets the noise generation coordinates by a given vector (X,Y,Z).
* **-c**: When used, centres the noise generation on the world coordinates of the selection.
* **-h**: Activates heightmap mode using 2D noise.\
  &#xNAN;_&#x48;eightmap mode is only compatible with Cuboid, Cylinder, or Polygon region types._
* **-n**: Uses normalized (-1 to 1) selection-centred coordinates for noise generation.
* **-t**: Enables smooth mode, specifically for snow, water, and lava blocks in the palette \[Applicable only in heightmap mode].

</details>
