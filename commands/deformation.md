# Deformation

All sub-commands are under `//ezdeform` (`//ezd`)\
e.g `//ezdeform hexagonalize`

## `//ezdeform ...`

### `hexagonalize`

<details>

<summary>Hexagonalize</summary>

**`//ezdeform hexagonalize [size] [air_gap] [x_rotation] [z_rotation] [offset_angle] [-w <profile>]`**

* **Size** (Default: 12): Sets the size of hexagons.
* **Air Gap** (Default: 0.0): Defines the width of the air gap between columns.
* **X Rotation** (Default: 0.0): Sets the column rotation angle along the X-axis, in degrees.
* **Z Rotation** (Default: 0.0): Sets the column rotation angle along the Z-axis, in degrees.
* **Offset Angle** (Default: 60.0): Adjusts the offset angle, controlling the shape (range: 0-90 degrees).
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `noise`

<details>

<summary>Noise</summary>

**`//ezdeform noise <noise> [strength] [-z <scale>] [-s <seed>] [-w <profile>]`**

* **Noise**: Specifies the type of noise to use for deformation.
* **Strength** (Default: 2.0): Sets the strength of the noise effect.
* **Scale** (Default: 1): Determines the scale of the noise.
* **-s** (Default: -1): Optional seed for the noise pattern.
* **-h**: When used, only deforms the region horizontally.
* **-v**: When used, only deforms the region vertically.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `rotate`

<details>

<summary>Rotate</summary>

**`//ezdeform rotate <angle> [-o] [-w <profile>]`**

* **Angle**: Sets the angle of rotation, in degrees.
* **-o**: When used, uses the player's position as the center of rotation instead of the selection's center.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `voronoialize`

<details>

<summary>Voronoialize</summary>

**`//ezdeform voronoialize [size] [air_gap] [-s <seed>] [-w <profile>]`**

* **Size** (Default: 12): Determines the size of the voronoi cells.
* **Air Gap** (Default: 0.0): Specifies the width of the air gap between cells.
* **-s** (Default: -1): Optional seed for generating the pattern.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `voronoialize2`

<details>

<summary>Alternative Voronoialize</summary>

**`//ezdeform voronoialize2 <amount> [air_gap] [-s <seed>] [-r <seed_repulsion>] [-n <normalOffset>] [-w <profile>]`**

* **Amount**: Specifies the cell amount in the voronoi pattern.
* **Air Gap** (Default: 0.0): Determines the width of the air gap between cells.
* **-s** (Default: -1): Optional seed for generating the pattern.
* **-r** (Default: 15): Sets the voronoi seed point repulsion factor.
* **-n** (Default: 5): Adjusts the normal offset factor, which can be decreased for thinner shapes.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `voxelize`

<details>

<summary>Voxelize</summary>

**`//ezdeform voxelize <scales> <gap> <distortion> [-i <primary>] [-j <secondary>] [-s <seed>] [-hv] [-w <profile>]`**

* **Scales** (Default: 3,3,3): Sets the scale for each dimension.
* **Gap** (Default: 0.0): Defines the width of the air gap between voxels.
* **Distortion** (Default: 0.0): Adjusts the strength of random grid distortion (range: 0-1).
* **-i** (Default: y): Specifies the primary axis for grid rotation.
* **-j** (Default: -x): Specifies the secondary axis for grid rotation.
* **-s** (Default: -1): Optional seed for random distortion.
* **-h**: When used, only voxelizes horizontally.
* **-v**: When used, only voxelizes vertically.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>
