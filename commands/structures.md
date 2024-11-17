ezEdits provides multiple ways to quickly place clipboards, schematics, expression-based shapes, all categorized as 'structures'.

The relevant commands and brushes (introduced in version 0.11.0) are:
`//ezplace` (`//ezpl`) - Places a single structure at the player position.
`//ezscatter` (`//ezsc`) - Places multiple structures within a selected region.
`//ezsequence` (`//ezseq`)- Places multiple structures sequentially along a path.

`//ezbrush place` (`//ezbr pl`) - Brush that places a single structure for every brush click.
`//ezbrush scatter` (`//ezbr sc`) - Brush that places multiple structures around a brush click.
`//ezbrush sequence` (`//ezbr seq`) - Brush that places multiple structures along a brush stroke.

For completeness, one can also embed a structure, or an array of structures into a shaped spline with the ezspline subcommand:
`//ezspline structure` (`//ezsp structure`)
However, the structures are not "placed", such that e.g. the placement parameters do not apply to this command.

# Structures

## Available Structures
In the context of ezEdits, "structures" are an arrangement of blocks in 3D space. Each of the above mentioned commands requires the user to provide a `<structure>` argument.

Currently available structures are:

<details>

<summary><mark style="color:red;"><strong>&#x3C;Clipboard (C)></strong></mark></summary>

A structure based on your current WorldEdit Clipboard.

Options:
* Origin (O). Defaults to INHERENT.
  - INHERENT (I) will use the position it was copied at
  - CENTER (C) will use the geometric center of the clipboard
* PasteMethod (PM). Defaults to FAST.
  - FAST (fast): Default unaltered pasting of clipboards
  - SMOOTHED (smooth): Applies interpolation when the placement cannot be matched onto the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.
  * Example: Clipboard(Origin:INHERENT,PasteMethod:SMOOTHED) or C(O:I,PM:smooth)

</details>

<details>

<summary><mark style="color:red;"><strong>&#x3C;Schematic (Sc)></strong></mark></summary>

A structure based on a schematic file.

Options:
* Filename (N) (mandatory parameter)
* Format (F)
* Origin (O). Defaults to INHERENT.
  - INHERENT (I) will use the position it was copied at
  - CENTER (C) will use the geometric center of the clipboard
* PasteMethod (PM). Defaults to FAST.
  - FAST (fast): Default unaltered pasting of clipboards
  - SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.

</details>

<details>

<summary><mark style="color:red;"><strong>&#x3C;Shape (S)></strong></mark></summary>

An expression based shape. EzEdits provides plenty of predefined ones. Material defined by a pattern.

Options:
* Shape (S)
* Pattern (P)

</details>

<details>

<summary><mark style="color:red;"><strong>&#x3C;TexturedShape (TS)></strong></mark></summary>

An expression based shape with an expression based texturing. Material defined the Texturing-Shape and a Palette.

Options:
* Shape (S)
* TexturingShape (T)
* Palette (P)

</details>

## Placement Parameters

Whenever a structure is placed, it goes through the following pipeline (in that order):

- Custom Dimensions (`-s`)
- Random Scaling (`-t`)
- Orientation (`-c` and `-k`)
- Random Flips (`-f`)
- Random 90° Rotation (`-r`)
- **Alignment** (`<primary>` and `<secondary>`)

ezEdits lets you fully customise this pipeline. In brackets are the flags and arguments that apply changes to each step respectively.

### Controlling Dimensions

The dimensions define the size of a structure placement, by setting its bounding box size.

> The flag `-s <size>` sets the desired absolute base dimensions of the placement (overriding the default values).

By default, expression based structures have dimensions `20,20,20`, while Schematic/Clipboard structures are placed with their inherent original dimensions.

Depending on your choice of values, the structure might appear stretched or compressed. For example if your clipboard is inherently of size 7x7x7, then setting the dimensions as `-s 7,14,7` will stretch out the structure placement along its y-axis.

### Random Scaling

Most of the structure commands place multiple structure placements at once. To give a bit of variety you can apply some random scaling for each placement.

> The `-t <range>` flag lets you specify a range of values. A random number from this range is chosen for each placement. This scaling factor then scales the placement.

By default, the range is `1,1`, meaning the scaling factor is always 1, and thus, does nothing.

### Random Flips

> The `-f <axes>` flag enables random flipping of the structure across any of the axes for each placement. 

Flips are applied after orientation but before alignment.

### Random 90°-Rotations

> The `-r <axis>` flag enables random 90° rotation of the structure across either of the axes for each placement.

90°-rotations are applied after orientation but before alignment.

### Alignment (most important)

Alignment defines at which orientation the structure is placed at.

Every structure has an inherent "up" direction and an inherent "forward" direction. By default (rather if you set primary and secondary to CONSTANT), structures are placed with their up direction facing, well, up (+y) and with their forward direction facing forward (+x).

Most important thing is now: You can define how a structure is placed by defining where its up direction should face and where its forward direction should face (aka. aligning it's internal coordinate system).

We let the user define the alignment using two directions:

> The `<primary>` direction will always align the structures internal +y direction.

> The `<secondary>` direction, together with the primary direction, imply the structures +x direction.

(The secondary must not necessarily align since the structures internal coordinate system always has right angles, but the primary and secondary can be any direction.)

The primary and secondary can be set to:

###### `Constant(Direction:<direction>)` Abr.: `C(V:<direction>)`
Explicitly set a constant direction for all placements.
  - Default direction is +y if you're setting the primary.
  - Default direction is +x if you're setting the secondary.

###### `Random` Abr.: `R`
Random direction for each placement.

###### `Aim` Abr.: `A`
Your player aim direction.

###### `PlayerRelative` Abr.: `P`
The direction from the placements position towards the current player position.

###### `SurfaceNormal` Abr.: `S`
The approximate surface normal in the region of the placements position.

###### `ViewDiff` Abr.: `V`
Define a direction using two clicks. Exclusively for brushes.

###### `Tangential` Abr.: `T`
The direction tangential to the path. Exclusively for sequences.

###### `Orthogonal` Abr.: `O`
The direction orthogonal to the path. Exclusively for sequences.

### Orientation (advanced)

Defining an orientation means defining which internal coordinate system the structure has.
That coordinate system is then used in the random flips/rotations and during alignment. Defining an orientation is "defining which way is up and which way is forward".

> On orientation is set by a rotation axis (`-k <direction>`) and a rotation angle (`-c <angle>`). That works similar to `//ezd rotate`.

By default, the rotation axis `-k` is `y` or `up` and the rotation angle `-c` is `0`, and thus, does nothing.

For example if you set the rotation axis to `-k x` and the rotation angle to `-c 90` then your structure is rotated to the side. Its eastern side will now be its top side and so on.

### //ezplace 