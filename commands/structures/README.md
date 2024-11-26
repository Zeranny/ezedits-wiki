# Structures

## Overview

ezEdits provides multiple ways to quickly place clipboards, schematics, and expression-based shapes, all categorized as 'structures'.

The relevant commands and brushes (introduced in version 0.11.0) are:

<table data-column-title-hidden data-view="cards" data-full-width="false"><thead><tr><th>Command / Brush</th><th>Description</th></tr></thead><tbody><tr><td><a href="./#ezplace"><code>//ezplace</code> (<code>//ezpl</code>)</a> </td><td>Places a <strong>single</strong> structure at the <strong>player's position.</strong></td></tr><tr><td><a href="./#ezscatter"><code>//ezscatter</code> (<code>//ezsc</code>)</a> </td><td>Places <strong>multiple</strong> structures within a <strong>selected region</strong>.</td></tr><tr><td><a href="./#ezarray"><code>//ezarray</code> (<code>//ezar</code>)</a></td><td>Places <strong>multiple</strong> structures sequentially <strong>along a path</strong>.</td></tr><tr><td><a href="./#ezbrush-place"><code>//ezbrush place</code> (<code>//ezbr pl</code>)</a></td><td>Brush that places a <strong>single</strong> structure at each <strong>brush click's target</strong>.</td></tr><tr><td><a href="./#ezbrush-scatter"><code>//ezbrush scatter (//ezbr sc)</code></a></td><td>Brush that places <strong>multiple</strong> structures in the area of each <strong>brush click's target</strong>.</td></tr><tr><td><a href="./#ezbrush-array"><code>//ezbrush array</code> (<code>//ezbr ar</code>)</a></td><td>Brush that places <strong>multiple</strong> structures along a <strong>brush stroke</strong>.</td></tr></tbody></table>

For completeness, one can also embed a structure or an array of structures into a shaped spline with the ezspline subcommand `//ezspline structure` (`//ezsp structure`). However, the structures are not "placed" as much as they are embedded into the spline path, meaning that, for example, the [placement parameters](placement-parameters.md) do not apply to that command. Which is why it is documented on the [splines page](../spline.md) instead.



***

## Commands

This section lists the syntax of all structure commands with links to the corresponding sections.&#x20;

***

### `//ezplace`

Alias: `//ezpl`

Places a **single** structure at the **player's position.**

`//ezplace` [`<structure>`](available-structures.md) [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)

### `//ezbrush place`

Alias: `//ezbr pl`

Brush that places a **single** structure at each **brush click's target**.

`//ezbrush place` [`<structure>`](available-structures.md) [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)

***

### `//ezscatter`

Alias: `//ezsc`

Places **multiple** structures within a **selected region**.

`//ezscatter` [`<structure>`](available-structures.md) [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than) [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than) [`[-d <filterDirections>]  [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than) [`[-t]`](scatter-parameters.md#trimming-filter-t) [`[-c]`](scatter-parameters.md#cut-off-outside-the-selection-c)

### `//ezbrush scatter`

Alias: `//ezbr sc`

Brush that places **multiple** structures in the area of each **brush click's target**.

`//ezbrush scatter` [`<structure>`](available-structures.md) [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than) [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than) [`[-d <filterDirections>]  [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than) [`[-t]`](scatter-parameters.md#trimming-filter-t) [`[-c]`](scatter-parameters.md#cut-off-outside-the-selection-c)

***

### `//ezarray`

Alias: `//ezar`

Places **multiple** structures sequentially **along a path**.

`//ezarray` [`<structure>`](available-structures.md) [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than) [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than)

### `//ezbrush array`

Alias: `//ezbr ar`

Brush that places **multiple** structures along a **brush stroke**.

`//ezbrush array` [`<structure>`](available-structures.md) [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than) [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than)&#x20;

***

## Subpage structure

This Structure Wiki has multiple subpages. Here's an overview of the subpages.

* [**Available Structures**](available-structures.md)&#x20;
  * Covers the [`<structure>`](available-structures.md) parameter (necessary for place/scatter/array (and ezspline structure)).
* [**Primary+Secondary Alignment**](primary+secondary-alignment.md)&#x20;
  * Covers the [`[<primary>]  [<secondary>]`](primary+secondary-alignment.md) parameters (available for place/scatter/array).
* [**Placement Parameters**](placement-parameters.md)&#x20;
  * Covers the following flags (available for place/scatter/array):
    * [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than)
    * [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than)
    * [`[-c <orientationAngle>]  [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great)
    * [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than)
    * [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)
* [**Scatter Parameters**](scatter-parameters.md)&#x20;
  * Covers the following flags (only available for scatter):
    * [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than)
    * [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than)
    * [`[-d <filterDirections>]  [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than)
    * [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than)
    * [`[-t]`](scatter-parameters.md#trimming-filter-t)
    * [`[-c]`](scatter-parameters.md#cut-off-outside-the-selection-c)
* [**Array Parameters**](array-parameters.md)
  * Covers the following flags (only available for array):
    * [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than)
    * [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than)
    * [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than)
    * [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than)&#x20;
