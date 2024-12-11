# Spline

All sub-commands are under `//ezspline` (`//ezsp`)\
e.g `//ezspline beads`

_Note that every spline can only be run with a Convex Selection type (\`//sel convex\`)._

***

## Common parameters

The following parameters and flags are common between all //ezspline subcommands.

***

### Radius progression: <mark style="color:yellow;">`<radii>`</mark>

Defines the thickness (course) of the spline.

**Acceptable values are:** one or more comma-separated entries, where each entry is either:

1. A **radius value** (e.g., `10`, `6.9`). Radius values must be greater than 0.
2. A **position and radius**, separated by a colon, where the position is a decimal between 0 and 1 (e.g., `0:10`, `0.5:15.5`).

Whereby if specified, each _position_ must be strictly ascending, and the first and last entries must be positions of `0` and `1`. If positions are omitted, they will be set and interpolated automatically.

<details>

<summary><mark style="color:blue;">Examples:</mark></summary>

Example command: `//ezsp rope clay`` `**`<radii>`**

Single radius entry: GIF going from `//ezsp rope clay`` `**`5`** through up to `//ezsp rope clay`` `**`10`**.

![](../.gitbook/assets/SplinesRadii_example1.gif)&#x20;

Two radii entries: `//ezsp rope clay`` `**`1,12`** . The spline starts with radius 1 and progressively gets thicker up to radius 12 at the end.

![](../.gitbook/assets/SplinesRadii_example2.png)

Triple radii entries: `//ezsp rope clay`` `**`1,12,1`**. The spline starts with radius 1, and progressively gets larger up until the middle of the spline (50% of the path) where it reaches 12 and goes back to radius 1 towards the end:

![](../.gitbook/assets/SplinesRadii_example3.png)

As the first and last values always define the start- and end-radius of the spline and as all unspecified positions in between are interpolated, that means `1,12,1` (no positions specified) is expanded to **`0`**`:1,`**`0.5`**`:12,`**`1`**`:1` when you execute the command. You may also specify the positions yourself though.

Here's a GIF going from `1,`**`0.1`**`:12,1` up through `1,`**`0.9`**`:12,1`. This shifts the "keyframe position" of our radius-12-entry throughout the spline (start and end are fixed at radius 1):

![](../.gitbook/assets/SplinesRadii_example4.gif)&#x20;

You may define any number of entries and their respective positions.

`//ezsp rope clay 2,10,2,12,2,10,2`

![](../.gitbook/assets/SplinesRadii_example5.png)

</details>

***

### Twist: <mark style="color:yellow;">`-t <angle>`</mark>

Defines how much to twist the shape along the spline. The input is an angle.

Specifics: The angle determines how much the shape is rotated throughout the length of the current diameter of the spline. Meaning, that if the diameter is 30 blocks, then after 30 blocks of path length, the shape will have rotated by the given angle.

<details>

<summary><mark style="color:blue;">Example:</mark></summary>

Example command: `//ezsp polygon clay 10 4`` `**`-t <angle>`**

Gif starts at `-t 0` and increases up to `-t 90`.

![](../.gitbook/assets/SplinesTwist_example.gif)

</details>

***

### Kochanek-Bartel-Parameters: <mark style="color:yellow;">`-p <kbParameters>`</mark>

Parameters for the flow of the spline. Determines what path the spline takes through the given node positions.

Provide `<tension>:<bias>:<continuity>`, colon-separated in that order (default is `0:0:0`). The expected value range for each parameter is `[-1..1]`.

[This diagram](https://en.wikipedia.org/wiki/Kochanek%E2%80%93Bartels_spline#/media/File:Kochanek_bartels_spline.svg) shows what each parameter does (Note: the order in the diagram (c,t,b) is different than what ezspline expects (t,b,c)).

<details>

<summary><mark style="color:blue;">Examples:</mark></summary>

Example command: `//ezsp polygon clay 10 4`` `**`-p <kbParameters>`**

**`-p 0:0:0`**

![](../.gitbook/assets/SplinesKBParameters_example1.png)

**`-p 0:-1:0`**

![](../.gitbook/assets/SplinesKBParameters_example2.png)

**`-p -1:0:0`**

![](../.gitbook/assets/SplinesKBParameters_example4.png)

**`-p 0:1:0`**

![](../.gitbook/assets/SplinesKBParameters_example3.png)

</details>

***

### Quality: <mark style="color:yellow;">`-q <quality>`</mark>

Sets the number of samples of the shape per dimension per block. Must be greater than 0.

If you get air gaps, set the quality to a higher value.

{% hint style="warning" %}
Higher values for the `-q` parameter can significantly increase processing time. While small values (e.g., `-q 2`) are relatively quick, larger values (e.g., `-q 10`) may take several minutes. Additionally, the benefit of increasing the `-q` value diminishes beyond a certain point. We suggest using 2 while testing parameters and rendering with 4-6 for the final placement.
{% endhint %}

<details>

<summary><mark style="color:blue;">Example</mark></summary>

Example command: `//ezspline beads clay 10`` `**`-q <quality>`**

Gif start at `-q 1` and moves up to `-q 7`.

![](../.gitbook/assets/SplinesQuality_example.gif)

For this example, `-q 2` took less than a second, and `-q 7` already took 20 seconds.

</details>

***

### Spline Normal Mode: <mark style="color:yellow;">`-n <normalMode>`</mark>

There are three modes:

1. `CONSISTENT` aims to appear smooth and consistent by rolling itself in curves.
2. `HORIZONTAL` prevents the spline shape from "rolling sideways".
3. `UPRIGHT` makes the internal spline shape's y-axis with the world's y-axis.

<details>

<summary><mark style="color:blue;">Examples:</mark></summary>

Example command: `//ezspline expression black,red,blue,white,yellow -o 5`` `**`-n <normalMode>`**` ``((z%2)>1.5?5:2*(x>0)+(y>0))+0.001`

`-n CONSISTENT`: The default value. The spline curves around the path in a smooth fashion. Towards the end, a noticeable amount of rolling has accumulated since (at the start white+red is the top surface, while towards the end white+blue is at the top -> the spline "rolled").

![](../.gitbook/assets/SplinesNormalMode_example1.png)

`-n HORIZONTAL`: The spline tries to align the originally upwards-facing surface to remain upwards, preventing itself from "rolling sideways". You can see that by the fact the white+red face is facing upwards throughout the entire spline.

![](../.gitbook/assets/SplinesNormalMode_example2.png)

`-n UPRIGHT`: The internal y-axis is always aligned with the world's y-axis instead of being perpendicular to the path. Notice how the yellow lines are perfectly straight now.

![](../.gitbook/assets/SplinesNormalMode_example3.png)



#### Another more dramatic example (same command, different path):

`-n CONSISTENT`

![](../.gitbook/assets/SplinesNormalMode_example4.png)

`-n HORIZONTAL`: Spline is forced to twist itself at steep/vertical sections to remain horizontal. (Here, it always tries to put the white+red surface at the top).

![](../.gitbook/assets/SplinesNormalMode_example5.png)

`-n UPRIGHT`: As you'd expect, when the spline's y-axis is perfectly vertical, then it does not like steep/vertical path sections...

![](../.gitbook/assets/SplinesNormalMode_example6.png)

</details>

***

## Predefined Spline Shapes

The following //ezsp subcommands feature predefined shapes with a smaller set of parameters.

### `//ezspline`` `<mark style="color:yellow;">`beads`</mark>

<details>

<summary><mark style="color:blue;">Bead spline</mark></summary>

**`//ezsp beads <pattern>`** [**`<radii>`**](spline.md#radius-progression-less-than-radii-greater-than) [**`[-p <kb_parameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) **`[-h]`**

Generates a beads-shaped spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block pattern.
* [**`<Radii>`**](spline.md#radius-progression-less-than-radii-greater-than):
  * The thickness of the spline, defined by comma-separated entries.
* [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) (Default: 0):
  * Defines how much to twist the shape along the spline. Note: Since beads are symmetric there is no visible effect.
* [**`[-p <kbParameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) (Default: "0:0:0"):
  * Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) (Default: 2.0):
  * Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) (Default: "CONSISTENT"):
  * Determines how the spline will orient itself.
* **`[-h]`**:
  * Shows the help page.

</details>

### `//ezspline`` `<mark style="color:yellow;">`chainlink`</mark>

<details>

<summary><mark style="color:blue;">Chain Link Spline</mark></summary>

**`//ezsp chainlink <pattern>`** [**`<radii>`**](spline.md#radius-progression-less-than-radii-greater-than) **`[inner] [offset] [stretch]`** [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) [**`[-p <kb_parameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) **`[-h]`**

Generates a chainlink-shaped spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block pattern.
* [**`<Radii>`**](spline.md#radius-progression-less-than-radii-greater-than):
  * The thickness of the spline, defined by comma-separated entries.
* **`[inner]`** (Default: 1.0):
  * The inner radius ratio of each link.
* **`[offset]`** (Default: 0.0):
  * Amount to offset each link by, adjusting the alignment of the links in the chain.
* **`[stretch]`** (Default: 1.0):
  * The amount to stretch the individual links along the chain.
* [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) (Default: 0):
  * Defines how much to twist the shape along the spline.
* [**`[-p <kbParameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) (Default: "0:0:0"):
  * Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) (Default: 2.0):
  * Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) (Default: "CONSISTENT"):
  * Determines how the spline will orient itself.
* **`[-h]`**:
  * Shows the help page.

</details>

### `//ezspline`` `<mark style="color:yellow;">`cubes`</mark>

<details>

<summary><mark style="color:blue;">Cube Spline</mark></summary>

**`//ezsp cubes <pattern>`** [**`<radii>`**](spline.md#radius-progression-less-than-radii-greater-than) **`[gap]`** [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) [**`[-p <kb_parameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) **`[-h]`**

Generates a chainlink-shaped spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block pattern.
* [**`<Radii>`**](spline.md#radius-progression-less-than-radii-greater-than):
  * The thickness of the spline, defined by comma-separated entries.
* **`[gap]`** (Default: 1.0):
  * Sets the gap between cubes
* [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) (Default: 0):
  * Defines how much to twist the shape along the spline.
* [**`[-p <kbParameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) (Default: "0:0:0"):
  * Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) (Default: 2.0):
  * Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) (Default: "CONSISTENT"):
  * Determines how the spline will orient itself.
* **`[-h]`**:
  * Shows the help page.

</details>

### `//ezspline`` `<mark style="color:yellow;">`fishnet`</mark>

<details>

<summary><mark style="color:blue;">Fishnet Spline</mark></summary>

**`//ezsp fishnet <pattern>`** [**`<radii>`**](spline.md#radius-progression-less-than-radii-greater-than) **`[inner] [offset] [stretch]`** [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) [**`[-p <kb_parameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) **`[-h]`**

Generates a fishnet-shaped spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block pattern.
* [**`<Radii>`**](spline.md#radius-progression-less-than-radii-greater-than):
  * The thickness of the spline, defined by comma-separated entries.
* **`[spacing]`** (Default: 10):
  * The distance between the strings of the net. Measured in blocks.
* **`[depth]`** (Default: 2):
  * The depth of each string within the net. How much it protrudes towards the center of the spline. Measured in blocks.
* **`[width]`** (Default: 2):
  * The width of each string. Measured in blocks.
* [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) (Default: 0):
  * Defines how much to twist the shape along the spline.
* [**`[-p <kbParameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) (Default: "0:0:0"):
  * Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) (Default: 2.0):
  * Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) (Default: "CONSISTENT"):
  * Determines how the spline will orient itself.
* **`[-h]`**:
  * Shows the help page.

</details>

### `//ezspline`` `<mark style="color:yellow;">`oscillate`</mark>

<details>

<summary><mark style="color:blue;">Oscillation Spline</mark></summary>

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

### `//ezspline`` `<mark style="color:yellow;">`polygon`</mark>

<details>

<summary><mark style="color:blue;">Polygonal Spline</mark></summary>

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

### `//ezspline`` `<mark style="color:yellow;">`rings`</mark>

<details>

<summary><mark style="color:blue;">Rings Spline</mark></summary>

**`//ezsp rings <pattern> <radii> [count] [thickness] [innerRadius] [-p <kb_parameters>] [-q <quality>] [-n <normalMode>] [-g] [-h]`**

Creates a spline of rings along the selected convex region.

* **Pattern**: Specifies the block pattern.
* **Radii**: The thickness of the spline, defined by up to three comma-separated values.\
  &#xNAN;_&#x41; radius of 10 will be 10 from the start to the end of the spline, 10,5,15 will start at 10, decreasing to 5 around the middle, and increasing to 15 at the end._
* **Count** (Default: 8): Determines the number of rings.
* **Thickness** (Default: 3.0): Determines the size of the rings in the direction of the spline.
* **Inner Radius** (Default: 0.7): A value between 0 and 1 which determines the size of the central hole in the ring.
* **-p** (Default: "0:0:0"): Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* ### `noise`
* **-q** (Default: 1.85): Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* **-n** (Default: "CONSISTENT"): Determines the mode for spline normal calculation.
* **-g**: When used, calculates the center radii using the geometric center for three radii.
* **-h**: Shows the help page.

</details>

### `//ezspline`` `<mark style="color:yellow;">`rope`</mark>

<details>

<summary><mark style="color:blue;">Rope Spline</mark></summary>

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

### `//ezspline`` `<mark style="color:yellow;">`simple`</mark>

<details>

<summary><mark style="color:blue;">Simple Spline</mark></summary>

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

***

## Advanced Spline Shapes

The following //ezspline subcommands feature three very powerful but more advanced spline shapes with effectively limitless customizability.

### `//ezspline`` `<mark style="color:yellow;">`noise`</mark>

<details>

<summary><mark style="color:blue;">Noise Spline</mark></summary>

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

### `//ezspline`` `<mark style="color:yellow;">`expression`</mark>

<details>

<summary><mark style="color:blue;">Expression Spline</mark></summary>

**`//ezsp expression <palette>`** [**`<radii>`**](spline.md#radius-progression-less-than-radii-greater-than) [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) [**`[-p <kb_parameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) **`[-z] [-o] [-h]`**

Generates a spline shaped by the given WorldEdit expression along the selected positions.

* **`<Palette>`**:
  * Specifies the block palette.
* [**`<Radii>`**](spline.md#radius-progression-less-than-radii-greater-than):
  * The thickness of the spline, defined by comma-separated entries.
* [**`[-t <angle>]`**](spline.md#twist-t-less-than-angle-greater-than) (Default: 0):
  * Defines how much to twist the shape along the spline.
* [**`[-p <kbParameters>]`**](spline.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) (Default: "0:0:0"):
  * Sets the parameters for the flow of the spline, including tension, bias, and continuity, provided in a colon-separated format.
* [**`[-q <quality>]`**](spline.md#quality-q-less-than-quality-greater-than) (Default: 2.0):
  * Adjusts the quality of the spline generation. Increase this value to reduce air gaps, noting that higher values increase processing time.
* [**`[-n <normalMode>]`**](spline.md#spline-normal-mode-n-less-than-normalmode-greater-than) (Default: "CONSISTENT"):
  * Determines how the spline will orient itself.
* **`[-z]:`**
  * Without setting this flag, the domain of the z-axis is 0 to the length of the spline divided by the radius. You may set this flag to normalize the Z-Axis, that runs along the path of the spline, to the \[-1,1] domain.
* **`[-o]`**:
  * By default, expression output maps >0..1 to the palette. Use this flag to instead map the output to whole numbers.
* **`[-h]`**:
  * Shows the help page.

</details>

### `//ezspline`` `<mark style="color:yellow;">`structure`</mark>

<details>

<summary><mark style="color:blue;">Structure Spline</mark></summary>

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
