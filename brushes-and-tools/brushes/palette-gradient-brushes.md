# Palette Gradient Brushes

### `//ezbr`` `<mark style="color:orange;">`gradient`</mark>

<details>

<summary>Gradient Brush</summary>

**`//ezbr gradient <palette> [radius] [interpolation] [strength] [-av] [-n <noise>] [-z <scale>] [-d <distanceFunction>]`**

The `gradient` brush allows you to first define a plane by selecting 2 points, you can then paint with your gradient with blocks chosen based on distance along this plane.

**Left Click to start a plane at your target block**\
**Sneak + Left Click to start a plane at the player position**\
**Right Click to set the end of the plane at your target block OR paint palette blocks if the plane is set**\
**Sneak + Right Click to set the end of the plane at the player position OR paint palette blocks if the plane is set**\
**Swap Hands (Default F key) to toggle between GLOBAL and PER\_ITEM active gradients**

* **Palette**: Specifies the palette to use for the gradient.
* **Radius** (Default: 8): Sets the radius of the brush.
* **Interpolation** (Default: NONE): Determines the type of interpolation used in the gradient transition.
* **Strength** (Default: 0.5): Adjusts the strength of interpolation, with a normal range from 0 to 1.
* **-a**: When activated, the gradient is allowed to replace air blocks.
* **-v**: Deactivates WorldEditCUI integration.
* **-n \<noise>** (Default: `White()`): Adds an underlying noise field to the gradient effect.
* **-z \<scale>** (Default: 1): Modifies the scale of the noise.
* **-d \<distanceFunction>** (Default: NONE): Sets the distance mode changing the brush to work based on distance from the initial block with the given distance function.

</details>

### `//ezbr`` `<mark style="color:orange;">`gradientstroke`</mark>

<details>

<summary>Gradient Stroke Brush</summary>

**`//ezbr gradientstroke <palette> [radius] [interpolation] [strength] [-adv] [-n <noise>] [-z <scale>]`**

The `gradientstroke` brush allows for gradient application along a path (stroke) defined by selecting points.

**Left Click to add points**\
**Sneak + Left Click to remove the last point**\
**Right Click to confirm & place the gradient stroke**\
**Sneak + Right Click to clear all points**\
**Swap Hands (Default F key) to toggle between GLOBAL and PER\_ITEM active gradients**

* **Palette**: Specifies the block pattern for the gradient.
* **Radius** (Default: 8): Sets the radius of the brush.
* **Interpolation** (Default: LINEAR): Determines the type of interpolation used in the gradient transition.
* **Bleed** (Default: 0.5): Adjusts the strength of interpolation, with a normal range from 0 to 1.
* **-a**: When activated, allows the gradient to replace air blocks.
* **-d**: Activates the 'distance to center' mode which applies the gradient based on distance to the middle of the stroke line instead of distance along the stroke.
* **-v**: Deactivates WorldEditCUI integration.
* **-n \<noise>** (Default: `White()`): Adds an underlying noise field to the gradient effect.
* **-z \<scale>** (Default: 1): Modifies the scale of the noise.

</details>

## Gradient Parameters

There are a few parameters to creating a gradient.

### Bleed

First off, the <mark style="color:orange;">**`bleed`**</mark> parameter.

* ![](../../.gitbook/assets/GradientInterpolationTapered2.gif)

The bleed parameter determines how much the colors bleed into each other.

### Noise

The pattern of how this bleeding takes place can be determined by <mark style="color:orange;">**`noise`**</mark>. The GIF above was using White noise (`-n White`). Meanwhile, the following GIFs use Perlin noise (`-n Perlin(Freq:0.25)`)

* ![](../../.gitbook/assets/GradientInterpolationTapered.gif)

You can also put in any noise. Here are a few more examples:

* `-n Perlin(Freq:0.25)`
  * ![](../../.gitbook/assets/GradientInterpolationNoise_example1.png)
* `-n Cellular(Freq:0.15)`
  * ![](../../.gitbook/assets/GradientInterpolationNoise_example3.png)
* `-n @@ridged(Freq:0.15)`
  * ![](../../.gitbook/assets/GradientInterpolationNoise_example2.png)
* `-n Shard(Freq:0.15)`
  * ![](../../.gitbook/assets/GradientInterpolationNoise_example4.png)

### Interpolation Mode

In the following, we compare the five different <mark style="color:orange;">**`interpolation modes`**</mark> of applying the noise to the gradient. The GIF goes through increasing and decreasing bleed values between 0 and 1. The blue square's top and bottom sides show the gradient's start and end positions.

#### NONE

No noise is applied.

* ![](../../.gitbook/assets/GradientInterpolationNone.png)

#### LINEAR

The noise is applied with a constant factor throughout the entire gradient. Because of that, the gradient is "clipping" outside our two selected positions.

* ![](../../.gitbook/assets/GradientInterpolationLinear.gif)

#### TAPERED

Applies the noise strongest in the middle of the gradient and tapers off towards the start and end to avoid "clipping" outside of the given positions.

* ![](../../.gitbook/assets/GradientInterpolationTapered.gif)

#### BEZIER

Uses Bezier interpolation to apply the noise more softly and smoothly. Breaks for a bleed value of >1.

* ![](../../.gitbook/assets/GradientInterpolationBezier.gif)

#### SIN

* ![](../../.gitbook/assets/GradientInterpolationSin.gif)

