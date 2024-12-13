# Spline

ezEdits provides an extensive interface to place and embed various shapes and structures along a 1-dimensional interpolated path in 3-D space.

The paths are defined by WorldEdits convex selections (//sel convex). Every subcommand requires the user to have a convex region selection active.

All sub-commands are under <mark style="color:orange;">**`//ezspline`**</mark>\
The abbreviation/alias of it is <mark style="color:orange;">**`//ezsp`**</mark>

***

## Subpage Overview

* [**Common Parameters**](common-parameters.md)
  * covers all arguments and flags that are available to **all** ezspline subcommands. These are:
    * [`<radii>`](common-parameters.md#radius-progression-less-than-radii-greater-than)
    * [`[-t <angle>]`](common-parameters.md#twist-t-less-than-angle-greater-than)
    * [`[-p <kbParameters>]`](common-parameters.md#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than)
    * [`[-q <quality>]`](common-parameters.md#quality-q-less-than-quality-greater-than)
    * [`[-n <normalMode>]`](common-parameters.md#spline-normal-mode-n-less-than-normalmode-greater-than)
* [**2D Spline Shapes**](2d-spline-shapes.md)
  * covers the //ezsp 2d subcommand:
    * [`//ezsp simple`](2d-spline-shapes.md#ezspline-simple)
    * [`//ezsp polygon`](2d-spline-shapes.md#ezspline-polygon)
    * [`//ezsp rope`](2d-spline-shapes.md#ezspline-rope)
    * [`//ezsp sweep`](2d-spline-shapes.md#ezspline-sweep)&#x20;
* [**3D Spline Shapes**](3d-spline-shapes.md)
  * covers the following subcommands:
    * [`//ezsp beads`](3d-spline-shapes.md#ezspline-beads)
    * [`//ezsp chainlink`](3d-spline-shapes.md#ezspline-chainlink)
    * [`//ezsp cubes`](3d-spline-shapes.md#ezspline-cubes)
    * [`//ezsp fishnet`](3d-spline-shapes.md#ezspline-fishnet)
    * [`//ezsp oscillate`](3d-spline-shapes.md#ezspline-oscillate)
    * [`//ezsp rings`](3d-spline-shapes.md#ezspline-rings)
* [**Advanced Spline Shapes**](advanced-spline-shapes.md)
  * covers the following subcommands:
    * [`//ezsp noise`](advanced-spline-shapes.md#ezspline-noise)
    * [`//ezsp expression`](advanced-spline-shapes.md#ezspline-expression)
    * [`//ezsp structure`](advanced-spline-shapes.md#ezspline-structure)
