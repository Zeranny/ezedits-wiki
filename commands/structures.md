# Structures

## Overview

ezEdits provides multiple ways to quickly place clipboards, schematics, and expression-based shapes, all categorized as 'structures'.

The relevant commands and brushes (introduced in version 0.11.0) are:

<table data-column-title-hidden data-view="cards" data-full-width="false"><thead><tr><th>Command / Brush</th><th>Description</th></tr></thead><tbody><tr><td><code>//ezplace</code> (<code>//ezpl</code>) </td><td>Places a <strong>single</strong> structure at the <strong>player's position.</strong></td></tr><tr><td><code>//ezscatter</code> (<code>//ezsc</code>) </td><td>Places <strong>multiple</strong> structures within a <strong>selected region</strong>.</td></tr><tr><td><code>//ezarray</code> (<code>//ezar</code>)</td><td>Places <strong>multiple</strong> structures sequentially <strong>along a path</strong>.</td></tr><tr><td><code>//ezbrush place</code> (<code>//ezbr pl</code>)</td><td>Brush that places a <strong>single</strong> structure at each <strong>brush click's target</strong>.</td></tr><tr><td><code>//ezbrush scatter</code> (<code>//ezbr sc</code>)</td><td>Brush that places <strong>multiple</strong> structures in the area of each <strong>brush click's target</strong>.</td></tr><tr><td><code>//ezbrush array</code> (<code>//ezbr ar</code>)</td><td>Brush that places <strong>multiple</strong> structures along a <strong>brush stroke</strong>.</td></tr></tbody></table>

For completeness, one can also embed a structure or an array of structures into a shaped spline with the ezspline subcommand `//ezspline structure` (`//ezsp structure`). However, the structures are not "placed" as much as they are embedded into the spline path, meaning that, for example, the placement parameters do not apply to that command. Which is why it is documented on the [splines page](spline.md) instead.

***

## Available Structures

In the context of ezEdits, we call an arrangement of blocks in 3D space a "structure". Each of the above-mentioned commands requires the user to provide a `<structure>` argument.

Currently available structures are:

<details>

<summary><strong>Clipboard (C)</strong></summary>

A structure based on your current WorldEdit Clipboard.

Options:

* Origin (O). Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* PasteMethod (PM). Defaults to FAST.
  * FAST (fast): Default unaltered pasting of clipboards
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched onto the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.
* Example: `Clipboard(Origin:INHERENT,PasteMethod:SMOOTHED)` or `C(O:I,PM:smooth)`

</details>

<details>

<summary><strong>Schematic (Sc)</strong></summary>

A structure based on a schematic file.

Options:

* Filename (N) (mandatory parameter)
* Format (F)
* Origin (O). Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* PasteMethod (PM). Defaults to FAST.
  * FAST (fast): Default unaltered pasting of clipboards
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.

</details>

<details>

<summary><strong>Shape (S)</strong></summary>

An expression-based shape. EzEdits provides plenty of predefined ones. Material defined by a pattern.

Options:

* Shape (S)
* Pattern (P)

</details>

<details>

<summary><strong>TexturedShape (TS)</strong></summary>

An expression-based shape with an expression-based texturing. Material defined the Texturing-Shape and a Palette.

Options:

* Shape (S)
* TexturingShape (T)
* Palette (P)

</details>

***

## Placement Parameters

Whenever a structure is placed, it goes through the following pipeline (in that order):

* [Applying Dimensions](structures.md#controlling-dimensions) (`-s`)
* [Random Scaling](structures.md#random-scaling) (`-t`)
* [Orientation](structures.md#orientation-advanced) (`-c` and `-k`)
* [Random Flips](structures.md#random-flips) (`-f`)
* [Random 90° Rotations](structures.md#random-90-rotations) (`-r`)
* [**Alignment**](structures.md#alignment-most-important) (`<primary>` and `<secondary>`)

ezEdits lets you fully customize this pipeline. In brackets are the flags and arguments that apply changes to each step respectively.



### Controlling Dimensions: `-s <dimensions>`

The dimensions define the size of a structure placement, by setting its bounding box size.

> The flag `-s <dimensions>` sets the desired absolute base dimensions of the placement (overriding the default values).

By default, expression-based structures have dimensions `20,20,20`, while Schematic/Clipboard structures are placed with their inherent original dimensions.

Note: The structure might appear stretched or compressed depending on your choice of values. For example, if your clipboard is inherently of size 5x7x5, then setting the dimensions as `-s 5,14,5` will stretch out the structure placement along its y-axis:

<details>

<summary>Example of stretching of structure using -s</summary>

First image: `//ezsc Clipboard C C -s 5,7,5` (original clipboard size)

Second image: `//ezsc Clipboard C C -s 5,14,5`

![](../.gitbook/assets/2024-11-18\_00.51.13.png) ![](../.gitbook/assets/2024-11-18\_00.51.19.png)

</details>

### Random Scaling: `-o <sizeMultiplierRange>`

Most of the structure commands place multiple structure placements at once. To give a bit of variety you can apply some random scaling for each placement.

> The `-o <sizeMultiplierRange>` flag lets you specify a range of values. A random number from this range is chosen for each placement. This scaling factor then scales the placement.

By default, the range is `1,1`, meaning the scaling factor is always 1, and thus, does nothing.

<details>

<summary>Example of random scaling:</summary>

By setting the range as `-o 0.5,2.0` we get placements of e.g. our clipboard at random sizes between half the desired size and double the desired size,

`//ezsc Clipboard C C -o 0.5,2.0`

![](../.gitbook/assets/2024-11-18\_00.57.48.png)

(Same tree clipboard at various different sizes)

</details>

### Random Flips: `-f <randomFlipsAxes>`

> The `-f <randomFlipsAxes>` flag enables random flipping of the structure across any of the axes for each placement.

Available values are:

* None (default)
* X
* Y
* Z
* XY
* XZ
* YZ
* XYZ

Flips are applied after orientation but before alignment.

<details>

<summary>Example:</summary>

First Image: `//ezsc Clipboard C C` (no random flips)

Second Image: `//ezsc Clipboard C C -f XZ` (random mirrors along x- and z-axis, but not y)

![](../.gitbook/assets/2024-11-18\_01.25.41.png) ![](../.gitbook/assets/2024-11-18\_01.25.50.png)

</details>



### Random 90°-Rotations: `-r <randomRotationAxis>`

> The `-r <randomRotationAxis>` flag enables random 90° rotation of the structure across either of the axes for each placement.

Available values are:

* X
* Y
* Z

By default, the flag is not set, and thus random rotations are disabled.

90°-rotations are applied after orientation but before alignment.

<details>

<summary>Example:</summary>

First Image: `//ezsc Clipboard C C` (no random rotations)

Second Image: `//ezsc Clipboard C C -r Y` (random 90°-rotations around the y-axis)

![](../.gitbook/assets/2024-11-18\_01.26.44.png) ![](../.gitbook/assets/2024-11-18\_01.26.29.png)

</details>



### Alignment (most important): `<primary>` and `<secondary>`

Alignment defines at which orientation the structure is placed at.

Every structure has an inherent "up" direction and an inherent "forward" direction. By default (rather, if you set primary and secondary to `Constant`), structures are placed with their up direction facing, well, up (+y), and with their forward direction facing forward (+x).

Most important thing is now: You can define how a structure is placed by defining where its up direction should face and where its forward direction should face (aka. aligning it's internal coordinate system).

We let the user define the alignment using two directions:

> The `<primary>` direction will always align the structures internal +y direction.

> The `<secondary>` direction, together with the primary direction, imply the structures +x direction.



The primary and secondary can be set to:

<table data-full-width="true"><thead><tr><th width="208">Name</th><th width="47">Abbreviation</th><th>Description</th></tr></thead><tbody><tr><td><strong><code>Constant(Direction:&#x3C;direction>)</code></strong></td><td><strong><code>C</code></strong></td><td>Explicitly set a constant direction for all placements.</td></tr><tr><td><strong><code>Random</code></strong></td><td><strong><code>R</code></strong></td><td>Random direction for each placement.</td></tr><tr><td><strong><code>Aim</code></strong></td><td><strong><code>A</code></strong></td><td>Your player aim direction.</td></tr><tr><td><strong><code>PlayerRelative</code></strong></td><td><strong><code>P</code></strong></td><td>The direction from the placement's position towards the current player position.</td></tr><tr><td><strong><code>SurfaceNormal</code></strong></td><td><strong><code>S</code></strong></td><td>The approximate surface-normal in the region of the placement's position.</td></tr><tr><td><strong><code>ViewDiff</code></strong></td><td><strong><code>V</code></strong></td><td>Define a direction using two clicks. Exclusively for brushes.</td></tr><tr><td><strong><code>Tangential</code></strong></td><td><strong><code>T</code></strong></td><td>The direction tangential to the path. Exclusively for arrays.</td></tr><tr><td><strong><code>Orthogonal</code></strong></td><td><strong><code>O</code></strong></td><td>The direction orthogonal to the path. Exclusively for arrays.</td></tr></tbody></table>

Note: If you use Constant without specifying a \<direction>, then:

* the default direction is **+y** if you're setting the `<primary>`.
* the default direction is **+x** if you're setting the `<secondary>`.

<details>

<summary>More in-depth explanation using examples:</summary>

Let's say this is our build that we want to place:

![](../.gitbook/assets/2024-11-18\_03.12.06.png)

For reference, the red beam is facing towards positive x (east), the blue beam is facing towards positive z (south), and the green beam is facing towards positive y (up).

Let's go through a few examples and try to understand what is happening:

Let's set the `<primary>` to `up` (and the `<secondary>` to `east`):

![](../.gitbook/assets/2024-11-18\_03.12.06.png)

Our shape is pasted exactly in the same orientation as we copied it.

Consider the following two examples:

1. The `<primary>` is set to `south` and the `<secondary>` to `east`:

![](../.gitbook/assets/2024-11-18\_03.12.34.png)

2. The `<primary>` is set to the vector `(0,1,1)`, i.e. the direction going diagonally up and south, and the `<secondary>` to `east`:&#x20;

![](../.gitbook/assets/2024-11-18\_03.19.20.png)

Notice how, what was originally "up" when we copied it, i.e. the green beam in our case, is facing the direction that we set the primary to.

Here's an interesting example:

The `<primary>` is set to the vector `(1,1,0)`, i.e. the direction going diagonally up and **east**, while the `<secondary>` is set to `east`:

![](../.gitbook/assets/2024-11-18\_03.21.06.png)

The green beam is correctly pointing along the primary direction. But notice how, even though the secondary is set to east, the red beam is not pointing east (but diagonally down and east).

Imagine if it were pointing east though: Then the green and red beam would be at a 45° angle instead of the original 90° angle. Our structure would be deformed/bent/sheared.

What we decided to implement instead, is that while we align the structure's +y direction with the given primary direction, instead of aligning the structure's +x direction with the given secondary direction, we choose the direction that is most similar to the given secondary direction and that is still perpendicular to the primary.

For a set primary direction here's a small gif that shows the remaining possible secondary directions that keep everything perpendicular:

![](<../.gitbook/assets/2024-11-18 04-25-47.gif>)



</details>



#### Examples and Gifs:

<details>

<summary>Constant</summary>

Explicitly set a constant direction for all placements.

There are various ways to define a direction. From using the axes, using cardinal directions or using vector notation, or player relative directions like forward, left, right, etc. You can also add directions together using the '+' sign, like `east+south`&#x20;

`//ezsc Clipboard C(v:(0,2,0)) C(v:east)`

![](../.gitbook/assets/2024-11-18\_04.33.26.png)

`//ezsc Clipboard C(v:(-1,2,-1)) C(v:east)`

![](<../.gitbook/assets/2024-11-18\_04.33.57 (1).png>)

`//ezsc Clipboard C(v:(-1,2,-1)) C(v:-aim)`

![](<../.gitbook/assets/2024-11-18\_04.36.35 (1).png>)

</details>

<details>

<summary>Random</summary>

Random direction for each placement.



</details>





### Orientation (advanced): `-k <orientationAxis>` and `-c <orientationAngle>`

Defining an orientation means defining which internal coordinate system the structure has. That coordinate system is then used in the random flips/rotations and during alignment. Defining an orientation is "defining which way is up and which way is forward".

> On orientation is set by a rotation axis (`-k <direction>`) and a rotation angle (`-c <angle>`).

It works identically to `//ezd rotate`.

By default, the rotation axis `-k` is `y` or `up` and the rotation angle `-c` is `0`, and thus, does nothing.

For example, if you set the rotation axis to `-k x` and the rotation angle to `-c 90` then your structure is rotated to the side. Its eastern side will now be its top side and so on.



***

## Scatter Parameters

`//ezscatter` and `//ezbrush scatter` place multiple shapes within a region. The positions that these commands choose can be customized with the following parameters:



### Density: `-n <density>`

Determines how many placements are placed, by specifying a density percentage.

The density value is a percentage. It determines what percentage of surface blocks a structure should be placed.

To be overly specific: Let amountSurfaceBlocks be the result of `//count [!air]&[~air]`, then the final amount of structures placed is equal to _amountSurfaceBlocks \* density / 100_. (The total amount can be lower due to the mask filter, the directional filter, and the trimming flag)

Examples:

* `-n 2%` (default)
* `-n 0.05%`
* `-n 0.05` ('%'-sign is optional)

Note: `0.5` is equal to `0.5%` not `50%`.



### Uniformity: `-u <iterations>`

Determines how uniformly spread out all placement positions are. Expected value: An integer between 0 and 20.

Examples:

* `-u 0` (fully random distribution)
* `-u 2` (slightly uniform distribution)
* `-u 15` (very uniform distribution)



### Directional Filter: `-d <directions>` and `-e <threshold>`

Enables filtering out placement positions on surfaces that are facing certain directions.

Examples:

* \-d up



### Mask Filter: `-m <mask>`



### Trimming Flag: `-t`



***

## Array Parameters

`//ezarray` and `//ezbrush array` place multiple shapes along a path. The positions that these commands choose can be customized with the following parameters:

### Distance: `-g <distance>`



### Progressive Scaling: `-q <radii>`



### Path Parameters: `-p <kbParameters>`



### Spline orientation: `-n <normalMode>`



***

## Commands

### `//ezplace`

Alias: `//ezpl`

`//ezplace` [`<structure>`](structures.md#available-structures) [`<primary>  <secondary>`](structures.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](structures.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](structures.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](structures.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](structures.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](structures.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)

### `//ezbrush place`

Alias: `//ezbr pl`

`//ezbrush place` [`<structure>`](structures.md#available-structures) [`<primary>  <secondary>`](structures.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](structures.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](structures.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](structures.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](structures.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](structures.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)

### `//ezscatter`

Alias: `//ezsc`

`//ezscatter` [`<structure>`](structures.md#available-structures) [`<primary>  <secondary>`](structures.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](structures.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](structures.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](structures.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](structures.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](structures.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-n <density>]`](structures.md#density-n-less-than-density-greater-than) [`[-u <iterations>]`](structures.md#uniformity-u-less-than-iterations-greater-than) [`[-d <filterDirections>]  [-e <filterThreshold>]`](structures.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](structures.md#mask-filter-m-less-than-mask-greater-than) [`[-t]`](structures.md#trimming-flag-t)

### `//ezbrush scatter`

Alias: `//ezbr sc`

`//ezscatter` [`<structure>`](structures.md#available-structures) [`<primary>  <secondary>`](structures.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](structures.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](structures.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](structures.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](structures.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](structures.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-n <density>]`](structures.md#density-n-less-than-density-greater-than) [`[-u <iterations>]`](structures.md#uniformity-u-less-than-iterations-greater-than) [`[-d <filterDirections>]  [-e <filterThreshold>]`](structures.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](structures.md#mask-filter-m-less-than-mask-greater-than) [`[-t]`](structures.md#trimming-flag-t)

### `//ezarray`

Alias: `//ezar`

`//ezarray` [`<structure>`](structures.md#available-structures) [`<primary>  <secondary>`](structures.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](structures.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](structures.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](structures.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](structures.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](structures.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](structures.md#distance-g-less-than-distance-greater-than) [`[-q <radiiMultiplier>]`](structures.md#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](structures.md#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](structures.md#spline-orientation-n-less-than-normalmode-greater-than)

### `//ezbrush array`

Alias: `//ezbr ar`

`//ezbrush array` [`<structure>`](structures.md#available-structures) [`<primary>  <secondary>`](structures.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](structures.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](structures.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](structures.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](structures.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](structures.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](structures.md#distance-g-less-than-distance-greater-than) [`[-q <radiiMultiplier>]`](structures.md#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](structures.md#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](structures.md#spline-orientation-n-less-than-normalmode-greater-than)
