# Patterns

### `#aim`

<details>

<summary>#aim Pattern</summary>

Takes the block the player is aiming at as the pattern.

<img src="../.gitbook/assets/aimPattern.gif" alt="" data-size="original">

</details>

### `#eznoise`

<details>

<summary>#eznoise Pattern</summary>

**`#eznoisepattern[palette][noisePreset][<scale>][<seed>]`**\
**Alias: `#eznp`**

Uses a noise preset values to return palette blocks.\
**Which also has the following in-built presets:**

* **`#ridged[palette][<scale>][<seed>]`**
* **`#smoothcells[palette][<scale>][<seed>]`**&#x20;
* **`#voronoiedge[palette][<scale>][<seed>]`**

</details>

### `#palette`

<details>


<summary>#palette Pattern</summary>

**`#palette[palette]`**

Takes the given palette and returns a list of palette blocks.
Can be used as a random block pattern.

e.g. `//set #palette[##ice]` is the same as `//set [blue_ice,packed_ice,ice]`

</details>

### `#selection`

<details>


<summary>#selection Pattern</summary>

**`#selection[selection][<offset>]`**

Shorthand: **`#sel[selection][<offset>]`**

Sets blocks using  the blocks currently in world at the location of the saved selection.\
Acts as if the selection were tiled/stacked.

Optional `<offset>` variable to offset the pattern by a given vector.

</details>

### `#vectorgradient`

<details>

<summary>#vectorgradient Pattern</summary>

**`#vectorgradientpattern[palette][vector][distance][<noisePreset>][<noiseScale>][<noiseSeed>]`**\
**Alias: `#vgradientp`**

Sets palette blocks along a vector with a given distance length with the block chosen based on distance plus a blending factor. Can also use noise presets.

</details>
