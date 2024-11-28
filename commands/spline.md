# Spline

All sub-commands are under `//ezspline` (`//ezsp`)\
e.g `//ezspline beads`

_Note that every spline can only be run with a Convex Selection type (\`//sel convex\`)._

## `//ezspline ...`

### `beads`

<details>

<summary>Bead Spline</summary>

**`//ezsp beads <pattern> <radii> [-p <kb_parameters>] [-q <quality>]`**\
&#xNAN;**`[-n <normalMode>] [-g] [-h]`**

Generates a beads-shaped spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `chainlink`

<details>

<summary>Chain Link Spline</summary>

**`//ezsp chainlink <pattern> <radii> [inner] [offset] [stretch] [spin] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Generates a chainlink-shaped spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Inner** (Default: 1.0): The inner radius ratio of each link.
* **Offset** (Default: 0.0): Amount to offset each link by, adjusting the alignment of the links in the chain.
* **Stretch** (Default: 1.0): The amount to stretch the individual links along the chain.
* **Spin** (Default: 0.0): Adds twist to the spline.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `cubes`

<details>

<summary>Cube Spline</summary>

**`//ezsp cubes <pattern> <radii> [gap] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Generates a spline out of cubes along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Gap** (Default: 1.0): Sets the gap between cubes.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `expression`

<details>

<summary>Expression Spline</summary>

**`//ezsp expression <pattern> <radii> [spin] <expression> [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Generates a spline shaped by the given WorldEdit expression along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Spin** (Default: 0): Adds twist to the spline.
* **Expression**: The WorldEdit expression defining the shape of the spline. Supports "x", "y", "z" as variables.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-z**: Normalize the Z-Axis, that runs along the path of the spline, to the \[-1,1] domain.
* **-h**: Shows the help page.

A local coordinate system is merged onto the path of the spline. The z-axis runs along the path. The x- and y-axis run perpendicular to the path.

If the -z flag _is not_ set, then the domain of the z-axis is \[0,L) whereby L is the length of the path divided by the radius.

If the -z flag _is_ set, then the domain of the z-axis is \[-1,1], such that z=-1 is at the beginning and z=1 at the end of the spline.

The domain of the x-axis is \[-1,1], such that x=-1 / x=1 is the left / right plane at the radius boundary.

The domain of the y-axis is \[-1,1], such that y=-1 / y=1 is the bottom / top plane at the radius boundary.

Example of an expression spline:\
`//ezsp expression red 20,5 0 -q 4 x^2+y^2<1-z%1`\
&#xNAN;_&#x4E;ote that the expression must come last_

</details>

### `fishnet`

<details>

<summary>Fishnet Spline</summary>

**`//ezsp fishnet <pattern> <radii> [spacing] [depth] [width] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Generates a fishnet-shaped spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Spacing** (Default: 10): The mesh spacing of the net..
* **Depth** (Default: 2): The depth of each string within the net.
* **Width** (Default: 2): The width of each string.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `noise`

<details>

<summary>Noise Spline</summary>

**`//ezsp noise <pattern> <radii> [strength] [stretch] [spin] <noise> [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Creates a noise-based spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Strength** (Default: 0.5): Determines the noise strength, affecting the intensity of the noise.
* **Stretch** (Default: 4.0): Controls the stretch factor of noise along the spline.
* **Spin** (Default: 0): Adds twist to the spline.
* **Noise** (Default: `Perlin(Freq:3)`): Specifies the type of noise to use for generation.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `oscillate`

<details>

<summary>Oscillation Spline</summary>

**`//ezsp oscillate <pattern> <radii> [depth] [interval] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Generates a spline with an oscillating thickness along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Depth** (Default: 2): Determines the ridge depth of the oscillation, affecting the amplitude of the waves.
* **Interval** (Default: 5): Sets the ridge interval, controlling the frequency of the oscillation along the spline.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `polygon`

<details>

<summary>Polygonal Spline</summary>

**`//ezsp polygon <pattern> <radii> [sides] [spin] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Creates a regular polygon-shaped spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Sides** (Default: 6): Determines the number of sides to the polygon.
* **Spin** (Default: 0.0): Adds twist to the spline.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `rings`

<details>

<summary>Rings Spline</summary>

**`//ezsp rings <pattern> <radii> [count] [thickness] [innerRadius] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Creates a spline of rings along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Count** (Default: 8): Determines the number of rings.
* **Thickness** (Default: 3.0): Determines the size of the rings in the direction of the spline.
* **Inner Radius** (Default: 0.7): A value between 0 and 1 which determines the size of the central hole in the ring.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `rope`

<details>

<summary>Rope Spline</summary>

**`//ezsp rope <pattern> <radii> [ropeCount] [spin] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Creates a rope-shaped spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **RopeCount** (Default: 3): Determines the number of intertwining ropes.
* **Spin** (Default: 2.0): Adds twist to the spline.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `simple`

<details>

<summary>Simple Spline</summary>

**`//ezsp simple <pattern> <radii> [-p <kb_parameters>] [-q <quality>]`**\
&#xNAN;**`[-n <normalMode>] [-g] [-h]`**

Creates a simple cylindrical spline along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `structure`

<details>

<summary>Structure Spline</summary>

**`//ezsp structure <structure> <radii> [-p <kb_parameters>] [-q <quality>]`**\
&#xNAN;**`[-n <normalMode>] [-g] [-h]`**

Embeds a structure along the path defined by the selected convex region.

* **Structure**: Specifies the structure to embed along the path.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

The structure will be placed in its Z-direction facing along the path. If you use -g, then one instance of the structure will be stretched across the whole length of the path. Otherwise, multiple instances will be repeated one after another.

</details>
