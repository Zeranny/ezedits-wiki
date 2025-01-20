# Spline

ezEdits provides an extensive interface to place and embed various shapes and structures along a 1-dimensional interpolated path in 3-D space.

The paths are defined by WorldEdits convex selections (`//sel convex`). When using a cuboid selection, the spline will be a direct line from pos1 to pos2.

All sub-commands are under <mark style="color:orange;">**`//ezspline`**</mark>\
The abbreviation/alias of it is <mark style="color:orange;">**`//ezsp`**</mark>

***

## Subpage Overview

* [**Common Parameters**](common-parameters.md)
  * covers all arguments and flags that are available to **all** `ezspline` subcommands. These are:
    * [`<radii>`](common-parameters.md#radii)
    * [`[-p <kbParameters>]`](common-parameters.md#kochanek-bartels-parameters)
    * [`[-q <quality>]`](common-parameters.md#quality)
    * [`[-r <startingRoll>]`](common-parameters.md#roll)
    * [`[-s <stretchFactor>]`](common-parameters.md#stretch)
    * [`[-t <twistAngle>]`](common-parameters.md#twist)
    * [`[-n <normalMode>]`](common-parameters.md#normal-mode)
* [**2D Spline Shapes**](2d-spline-shapes.md)
  * covers the `//ezsp` 2d subcommand:
    * [`//ezsp 2d Circle (Ci) (//ezsp basic)`](2d-spline-shapes.md#ezspline-2d-circle-ci-ezspline-basic)
    * [`//ezsp 2d Square (Sq)`](2d-spline-shapes.md#ezspline-2d-square-sq)
    * [`//ezsp 2d Diamond (Di)`](2d-spline-shapes.md#ezspline-2d-diamond-di)
    * [`//ezsp 2d RoundedSquare (RS)`](2d-spline-shapes.md#ezspline-2d-roundedsquare-rs)
    * [`//ezsp 2d SuperCircle (SC)`](2d-spline-shapes.md#ezspline-2d-supercircle-sc)
    * [`//ezsp 2d CirclesCircle (CC) (//ezsp rope)`](2d-spline-shapes.md#ezspline-2d-circlescircle-cc-ezspline-rope)
    * [`//ezsp 2d Polygon (Po)`](2d-spline-shapes.md#ezspline-2d-polygon-po)
    * [`//ezsp 2d Rectangle (Re)`](2d-spline-shapes.md#ezspline-2d-rectangle-re)
    * [`//ezsp 2d Star (St)`](2d-spline-shapes.md#ezspline-2d-star-st)
    * [`//ezsp 2d Flower (Fl)`](2d-spline-shapes.md#ezspline-2d-flower-fl)
* [**3D Spline Shapes**](3d-spline-shapes.md)
  * covers the following subcommands:
    * [`//ezsp 3d Beads`](3d-spline-shapes.md#ezspline-3d-beads-be)
    * [`//ezsp 3d Chainlink`](3d-spline-shapes.md#ezspline-3d-chainlink-ch)
    * [`//ezsp 3d Cubes`](3d-spline-shapes.md#ezspline-3d-cubes-cu)
    * [`//ezsp 3d Fishnet`](3d-spline-shapes.md#ezspline-3d-fishnet-fi)
    * [`//ezsp 3d Oscillate`](3d-spline-shapes.md#ezspline-3d-oscillate-os)
    * [`//ezsp 3d Rings`](3d-spline-shapes.md#ezspline-3d-rings-ri)
    * [`//ezsp 3d Scales`](3d-spline-shapes.md#ezspline-3d-scales-sc)
    * [`//ezsp 3d Noodles`](3d-spline-shapes.md#ezspline-3d-noodles-no)
* [**Advanced Spline Shapes**](advanced-spline-shapes.md)
  * covers the following subcommands:
    * [`//ezsp noise`](advanced-spline-shapes.md#ezspline-noise)
    * [`//ezsp expression`](advanced-spline-shapes.md#ezspline-expression)
    * [`//ezsp structure`](advanced-spline-shapes.md#ezspline-structure)
