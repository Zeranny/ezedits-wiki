# Array Parameters

`//ezarray` and `//ezbrush array` place multiple shapes along a path. The following parameters apply to these commands:

***

### Distance: `-g <gap>`

Control how close all placements are by defining the gap distance between each placement.

Defaults to 0. Meaning in straight line each placement comes right after another with no gap.

Positive values will increase that distance and place less in total

Negative values are allowed.


#### Examples

First image: `//ezarray Clipboard C C `**`-g 0`** (default value)

Second image: `//ezarray Clipboard C C `**`-g 10`** (placements are now further apart)

Third image: `//ezarray Clipboard C C `**`-g -10`** (placement now overlap)


***

### Progressive Scaling: `-q <radii>`

Similar to Random Scaling, this modifier allows to scale the placements using relative values, e.g. 1 keeps the scale as is, 2 means doubling the size and 0.5 halfs the size.

The scaling factors are defined as a progression along the spline. Meaning you may specify as many comma-separated scaling factors as you like, and the spline path will smoothly interpolate through all entries.

#### Examples

First image: `//ezarray Clipboard C C `**`-q 1`** (default value)

Second image: `//ezarray Clipboard C C `**`-q 1,2`** (placements are scaled by at the beginning and slowly get bigger up to double their original size towards the end of the spline path)

Third image: `//ezarray Clipboard C C `**`-g 1.5,0.5,1,0.2`**

***

### Path Parameters: `-p <kbParameters>`

Modifies how the path is created from the input (convex selection) points. See *LINK_TO_SPLINES_PAGE*.

***

### Spline orientation: `-n <normalMode>`

Modifies how the TANGENTIAL and ORTHOGONAL options for the `<primary>` and `<secondary>` arguments behave. See *LINK_TO_SPLINES_PAGE*.

#### Examples

First image: `//ezarray Clipboard O T`**`-n CONSISTENT`** (default value)

Second image: `//ezarray Clipboard O T `**`-n UPRIGHT`** (placements are not as tilted anymore)

***

### Snap placements to surfaces: `-b`

By default structures are placed along the spline path that's induced by the input (convex selection) points. This flag moves the placement positions to the nearest surface block instead, in case the position on the path is in midair or submerged in blocks.


#### Example

First image: `//ezarray Clipboard C C` (placements are placed along path)

Second image: `//ezarray Clipboard C C `**`-b`** (placements positions moved to nearest surface block)

