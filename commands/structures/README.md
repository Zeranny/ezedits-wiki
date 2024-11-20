# Structures

## Overview

ezEdits provides multiple ways to quickly place clipboards, schematics, and expression-based shapes, all categorized as 'structures'.

The relevant commands and brushes (introduced in version 0.11.0) are:

<table data-column-title-hidden data-view="cards" data-full-width="false"><thead><tr><th>Command / Brush</th><th>Description</th></tr></thead><tbody><tr><td><a href="./#ezplace"><code>//ezplace</code> (<code>//ezpl</code>)</a> </td><td>Places a <strong>single</strong> structure at the <strong>player's position.</strong></td></tr><tr><td><a href="./#ezscatter"><code>//ezscatter</code> (<code>//ezsc</code>)</a> </td><td>Places <strong>multiple</strong> structures within a <strong>selected region</strong>.</td></tr><tr><td><a href="./#ezarray"><code>//ezarray</code> (<code>//ezar</code>)</a></td><td>Places <strong>multiple</strong> structures sequentially <strong>along a path</strong>.</td></tr><tr><td><a href="./#ezbrush-place"><code>//ezbrush place</code> (<code>//ezbr pl</code>)</a></td><td>Brush that places a <strong>single</strong> structure at each <strong>brush click's target</strong>.</td></tr><tr><td><a href="./#ezbrush-scatter"><code>//ezbrush scatter (//ezbr sc)</code></a></td><td>Brush that places <strong>multiple</strong> structures in the area of each <strong>brush click's target</strong>.</td></tr><tr><td><a href="./#ezbrush-array"><code>//ezbrush array</code> (<code>//ezbr ar</code>)</a></td><td>Brush that places <strong>multiple</strong> structures along a <strong>brush stroke</strong>.</td></tr></tbody></table>

For completeness, one can also embed a structure or an array of structures into a shaped spline with the ezspline subcommand `//ezspline structure` (`//ezsp structure`). However, the structures are not "placed" as much as they are embedded into the spline path, meaning that, for example, the [placement parameters](placement-parameters.md) do not apply to that command. Which is why it is documented on the [splines page](../spline.md) instead.



***

## Commands

***

### `//ezplace`

Alias: `//ezpl`

Places a **single** structure at the **player's position.**

`//ezplace` [`<structure>`](available-structures.md) [`<primary>  <secondary>`](placement-parameters.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](./#random-90-rotations-r-less-than-randomrotationaxis-greater-than)

### `//ezbrush place`

Alias: `//ezbr pl`

Brush that places a **single** structure at each **brush click's target**.

`//ezbrush place` [`<structure>`](available-structures.md) [`<primary>  <secondary>`](placement-parameters.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](./#random-90-rotations-r-less-than-randomrotationaxis-greater-than)

***

### `//ezscatter`

Alias: `//ezsc`

Places **multiple** structures within a **selected region**.

`//ezscatter` [`<structure>`](available-structures.md) [`<primary>  <secondary>`](placement-parameters.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](./#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-n <density>]`](./#density-n-less-than-density-greater-than) [`[-u <iterations>]`](./#uniformity-u-less-than-iterations-greater-than) [`[-d <filterDirections>]  [-e <filterThreshold>]`](./#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](./#mask-filter-m-less-than-mask-greater-than) [`[-t]`](./#trimming-flag-t)

### `//ezbrush scatter`

Alias: `//ezbr sc`

Brush that places **multiple** structures in the area of each **brush click's target**.

`//ezscatter` [`<structure>`](available-structures.md) [`<primary>  <secondary>`](placement-parameters.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](./#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-n <density>]`](./#density-n-less-than-density-greater-than) [`[-u <iterations>]`](./#uniformity-u-less-than-iterations-greater-than) [`[-d <filterDirections>]  [-e <filterThreshold>]`](./#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](./#mask-filter-m-less-than-mask-greater-than) [`[-t]`](./#trimming-flag-t)

***

### `//ezarray`

Alias: `//ezar`

Places **multiple** structures sequentially **along a path**.

`//ezarray` [`<structure>`](available-structures.md) [`<primary>  <secondary>`](placement-parameters.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](./#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](./#distance-g-less-than-distance-greater-than) [`[-q <radiiMultiplier>]`](./#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](./#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](./#spline-orientation-n-less-than-normalmode-greater-than)

### `//ezbrush array`

Alias: `//ezbr ar`

Brush that places **multiple** structures along a **brush stroke**.

`//ezbrush array` [`<structure>`](available-structures.md) [`<primary>  <secondary>`](placement-parameters.md#alignment-most-important-less-than-primary-greater-than-and-less-than-secondary-greater-than) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>]  [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](./#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](./#distance-g-less-than-distance-greater-than) [`[-q <radiiMultiplier>]`](./#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](./#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](./#spline-orientation-n-less-than-normalmode-greater-than)
