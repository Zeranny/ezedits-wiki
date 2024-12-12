# 2D Spline Shapes

The following //ezsp subcommands feature splines made from predefined 2D shapes that were swept along the spline path.

***

### ![](../../.gitbook/assets/SplinesSimple.png)

### `//ezspline`` `<mark style="color:orange;">`simple`</mark>

<details>

<summary><mark style="color:blue;">Simple Spline</mark></summary>

**`//ezsp simple <pattern>`** [**`<radii>`**](common-parameters.md#radius-progression-less-than-radii-greater-than) [**`[-t <angle>]`**](common-parameters.md#twist-t-less-than-angle-greater-than) [**`[-p <kbParameters>]`**](common-parameters.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](common-parameters.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](common-parameters.md#spline-normal-mode-n-less-than-normalmode-greater-than) [**`[-h]`**](common-parameters.md#ingame-help-page-h)

Generates a simple cylindrical spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block(s) the spline is made out of.

The remaining arguments are outlined on the [Common Parameters](common-parameters.md) subpage.

</details>

***

### ![](../../.gitbook/assets/SplinesPolygon.gif)

### `//ezspline`` `<mark style="color:orange;">`polygon`</mark>

<details>

<summary><mark style="color:blue;">Polygon Spline</mark></summary>

**`//ezsp polygon <pattern>`** [**`<radii>`**](common-parameters.md#radius-progression-less-than-radii-greater-than) **`[sides]`** [**`[-t <angle>]`**](common-parameters.md#twist-t-less-than-angle-greater-than) [**`[-p <kbParameters>]`**](common-parameters.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](common-parameters.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](common-parameters.md#spline-normal-mode-n-less-than-normalmode-greater-than) [**`[-h]`**](common-parameters.md#ingame-help-page-h)

Generates a polygon-shaped spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block(s) the spline is made out of.
* **`[sides]`** (Default: 6):
  * The number of sides of the polygon. 3 means triangle, 4 means square, 5 means pentagon, etc.

The remaining arguments are outlined on the [Common Parameters](common-parameters.md) subpage.

</details>

***

### ![](../../.gitbook/assets/SplinesRope.png)

### `//ezspline`` `<mark style="color:orange;">`rope`</mark>

<details>

<summary><mark style="color:blue;">Rope Spline</mark></summary>

**`//ezsp rope <pattern>`** [**`<radii>`**](common-parameters.md#radius-progression-less-than-radii-greater-than) **`[count]`** [**`[-t <angle>]`**](common-parameters.md#twist-t-less-than-angle-greater-than) [**`[-p <kbParameters>]`**](common-parameters.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](common-parameters.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](common-parameters.md#spline-normal-mode-n-less-than-normalmode-greater-than) [**`[-h]`**](common-parameters.md#ingame-help-page-h)&#x20;

Generates a rope-shaped spline along the selected positions.

* **`<Pattern>`**:
  * Specifies the block(s) the spline is made out of.
* **`[count]`** (Default: 3):
  * The amount of intertwining ropes.
* [**`[-t <angle>]`**](2d-spline-shapes.md#twist-t-less-than-angle-greater-than) (Default: <mark style="background-color:yellow;">**90**</mark>):
  * Defines how much to twist the shape along the spline. Unlike all other subcommands, the rope spline has a default twist angle of 90°.

The remaining arguments are outlined on the [Common Parameters](common-parameters.md) subpage.

</details>

***

### ![](../../.gitbook/assets/SplinesSweep.gif)

### `//ezspline`` `<mark style="color:orange;">`sweep`</mark>&#x20;

The sweep spline is the general command that can do all of the above and more. You may treat the above as shortcuts.

<details>

<summary><mark style="color:blue;">Sweep Spline</mark></summary>

**`//ezsp sweep <2Dshape> <pattern>`** [**`<radii>`**](common-parameters.md#radius-progression-less-than-radii-greater-than) [**`[-t <angle>]`**](common-parameters.md#twist-t-less-than-angle-greater-than) [**`[-p <kbParameters>]`**](common-parameters.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than) [**`[-q <quality>]`**](common-parameters.md#quality-q-less-than-quality-greater-than) [**`[-n <normalMode>]`**](common-parameters.md#spline-normal-mode-n-less-than-normalmode-greater-than) [**`[-h]`**](common-parameters.md#ingame-help-page-h)&#x20;

Generates a shaped spline by sweeping a 2D shape along the spline path.

* **`<2Dshape>`**:
  * The 2D shape to sweep across along the path. Available options:
    * <mark style="color:orange;">Circle (Ci)</mark> (equivalent to [`//ezsp simple`](2d-spline-shapes.md#ezspline-simple))
    * <mark style="color:orange;">Square (Sq)</mark>
    * <mark style="color:orange;">Diamond (Di)</mark>
    * <mark style="color:orange;">RoundedSquare (RS)</mark>
    * <mark style="color:orange;">SuperCircle (SC)</mark>
      * Exponent (E): Determines the shape.
      * See [https://www.desmos.com/calculator/vewqf5sc0x](https://www.desmos.com/calculator/vewqf5sc0x)
    * <mark style="color:orange;">CirclesCircle (CC)</mark> (equivalent to [`//ezsp rope`](2d-spline-shapes.md#ezspline-rope))
      * Count (C): Sets the number of circles in the circle.
      * See [https://www.desmos.com/calculator/g9baekvgx9](https://www.desmos.com/calculator/g9baekvgx9)
    * <mark style="color:orange;">Polygon (Po)</mark> (equivalent to [`//ezsp polygon`](2d-spline-shapes.md#ezspline-polygon))
      * Sides (S): Sets the number of sides of the regular polygon. E.g. 6 meaning hexagon.
      * See [https://www.desmos.com/calculator/eemibllcg8](https://www.desmos.com/calculator/eemibllcg8)
    * <mark style="color:orange;">Rectangle (Re</mark>)
      * Define a rectangle using two positions.
      * See [https://www.desmos.com/calculator/jqyaujpdsk](https://www.desmos.com/calculator/jqyaujpdsk)
    * <mark style="color:orange;">Star (St)</mark>
      * Sides (S): Sets the number of points.
      * Depth (D): Between 0-1. Sets how deep the folds of the star are towards the center.
      * See [https://www.desmos.com/calculator/gqclaezcxc](https://www.desmos.com/calculator/gqclaezcxc)
    * <mark style="color:orange;">Flower (Fl)</mark>
      * Sides (S): Sets the number of petals.
      * Depth (D): Between 0-1. Sets how deep the folds between the petals of the flower are towards the center.
      * See [https://www.desmos.com/calculator/wsutm4zmbz](https://www.desmos.com/calculator/wsutm4zmbz)
* **`<Pattern>`**:
  * Specifies the block(s) the spline should be made out of.

The remaining arguments are outlined on the [Common Parameters](common-parameters.md) subpage.

</details>

***
