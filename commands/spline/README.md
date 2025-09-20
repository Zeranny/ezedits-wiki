---
description: Documentation of the //ezspline command
---

# Spline

{% embed url="https://youtu.be/dJXsPTB5NhU" %}
Video tutorial by [eztaK](https://linktr.ee/eztak)
{% endembed %}

ezEdits provides an extensive interface to place and embed various shapes and structures along a 1-dimensional interpolated path in 3-D space.

The paths are defined by WorldEdits convex selections (`//sel convex`). When using a cuboid selection, the spline will be a direct line from pos1 to pos2.

All sub-commands are under <mark style="color:orange;">**`//ezspline`**</mark>\
The abbreviation/alias of it is <mark style="color:orange;">**`//ezsp`**</mark>

***

## Subpage Overview

* [**Common Parameters**](common-parameters.md)
  * covers all arguments and flags that are available to **all** `ezspline` subcommands. These are:
    * [`<radii>`](common-parameters.md#radii)
    * [`[-p <kbParameters>]`](common-parameters.md#kb-parameters)
    * [`[-q <quality>]`](common-parameters.md#quality)
    * [`[-r <startingRoll>]`](common-parameters.md#roll)
    * [`[-s <stretchFactor>]`](common-parameters.md#stretch)
    * [`[-t <twistAngle>]`](common-parameters.md#twist)
    * [`[-n <normalMode>]`](common-parameters.md#normal-mode)
    * [`[-e <endMode>]`](common-parameters.md#end-style-e)
    * [`[-w <smoothblocks>]`](common-parameters.md#help-page)
* [**2D Spline Shapes**](2d-spline-shapes.md)
  * covers the `//ezsp` 2d subcommand:
    * [`//ezsp 2d Circle (Ci) (//ezsp basic)`](2d-spline-shapes.md#circle)
    * [`//ezsp 2d Square (Sq)`](2d-spline-shapes.md#square)
    * [`//ezsp 2d Diamond (Di)`](2d-spline-shapes.md#diamond)
    * [`//ezsp 2d RoundedSquare (RS)`](2d-spline-shapes.md#rounded-square)
    * [`//ezsp 2d SuperCircle (SC)`](2d-spline-shapes.md#super-circle)
    * [`//ezsp 2d CirclesCircle (CC) (//ezsp rope)`](2d-spline-shapes.md#circles-circle)
    * [`//ezsp 2d Polygon (Po)`](2d-spline-shapes.md#polygon)
    * [`//ezsp 2d Rectangle (Re)`](2d-spline-shapes.md#rectangle)
    * [`//ezsp 2d Star (St)`](2d-spline-shapes.md#star)
    * [`//ezsp 2d Flower (Fl)`](2d-spline-shapes.md#flower)
* [**3D Spline Shapes**](3d-spline-shapes.md)
  * covers the following subcommands:
    * [`//ezsp 3d Beads`](3d-spline-shapes.md#beads)
    * [`//ezsp 3d Chainlink`](3d-spline-shapes.md#chainlink)
    * [`//ezsp 3d Cubes`](3d-spline-shapes.md#cubes)
    * [`//ezsp 3d Fishnet`](3d-spline-shapes.md#fishnet)
    * [`//ezsp 3d Oscillate`](3d-spline-shapes.md#oscillate)
    * [`//ezsp 3d Rings`](3d-spline-shapes.md#rings)
    * [`//ezsp 3d Scales`](3d-spline-shapes.md#scales)
    * [`//ezsp 3d Noodles`](3d-spline-shapes.md#noodles)
* [**Advanced Spline Shapes**](advanced-spline-shapes.md)
  * covers the following subcommands:
    * [`//ezsp noise`](advanced-spline-shapes.md#noise)
    * [`//ezsp expression`](advanced-spline-shapes.md#expression)
    * [`//ezsp structure`](advanced-spline-shapes.md#structure)
