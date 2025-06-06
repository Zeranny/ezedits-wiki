# Smoothing

### `//ezsmooth`

<details>

<summary>Smooth</summary>

**`//ezsmooth <radii> <iterations> <bias> [-w <profile>]`**

**`Alias: //ezsm`**

The `//ezsmooth` command smooths the edges and surfaces of a selected region using a 3 dimensional smoothing algorithm.

* **Radii**: The smoothing radius or radii, which can be a single value or three comma-separated values for the East/West, Up/Down, and North/South directions, respectively. This parameter controls the extent of the smoothing effect.
* **Iterations**: The number of times the smoothing operation is executed. More iterations lead to a smoother outcome but increase processing time.
* **Bias**: A value between -1.0 and 1.0 that adjusts the smoothing effect's expansion or contraction. Positive values expand the smoothed area, while negative values contract it.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `//ezinflate`

<details>

<summary>Inflate</summary>

**`//ezinflate <radius> [-w <profile>]`**

**`Alias: //inflate`**

The `//ezinflate` command expands the volume of blocks within a selected region by a specified amount, effectively "inflating" the build.

* **Radius**: Specifies the expansion distance in blocks. This value determines how far from the original surfaces the new, inflated surfaces will be created.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `//ezdeflate`

<details>

<summary>Deflate</summary>

**`//ezdeflate <radius> [-w <profile>]`**

**`Alias: //deflate`**

The `//ezdeflate` command contracts the volume of blocks within a selected region by a specified amount, effectively "deflating" the build.

* **Radius**: Specifies the expansion distance in blocks. This value determines how far inwards from the original surfaces that blocks will be removed.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

### `//ezsmoothblocks` (v0.15.0 and above)

<details>

<summary>Smooth Blocks</summary>

**`//ezsmoothblocks <profile> <radius> <bias>`**

**`Alias: //ezsb`**

The `//ezsmoothblocks` command modifies a selected region by placing slabs, stairs, and walls to create a significantly smoother surface.

* **Profile**: Determines the set of shaping blocks used. See [#profiles](../smoothblocks/smoothblocks.md#profiles "mention").

- **Radius**: Specifies the smoothing radius in blocks. This value determines the area around each block that is considered during the smoothing process. The larger the value to more aggressive the smoothing.

* **Bias**: A value between -1.0 and 1.0 that adjusts the smoothing effect which determines how many blocks are added or removed. Positive values will lead to more blocks being placed than removed, while negative values will remove more blocks than add.
* **-w**: See [Smoothblocks](../smoothblocks/smoothblocks.md).

</details>

#### `//ezsmoothblocks` (v0.14.0 and older)

<details>

<summary>Smooth Blocks (Legacy)</summary>

**`//ezsmoothblocks <radius> <iterations> <bias> [-s] [-t] [-w]`**

**`Alias: //smoothblocks`**

The `//ezsmoothblocks` command modifies a selected region by placing slabs, stairs, and walls to create a significantly smoother surface.

* **Radius**: Specifies the smoothing radius in blocks. This value determines the area around each block that is considered during the smoothing process.
* **Iterations**: The number of times the smoothing operation is executed. More iterations result in a smoother outcome but increase processing time.
* **Bias**: A value between -1.0 and 1.0 that adjusts the smoothing effect's expansion or contraction. Positive values tend to expand the smoothed area, while negative values contract it, offering control over the final appearance.
* **-s**: Limits the smoothing process to only use slabs.
* **-t**: Excludes walls from smoothing.
* **-w**: Uses an alternative set of blocks.

</details>

***
