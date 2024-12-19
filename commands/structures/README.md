# Structure commands

## Overview

ezEdits provides multiple ways to quickly place clipboards, schematics, and expression-based shapes, all categorized as 'structures'.

The relevant commands and brushes (introduced in version 0.12.0) are:

<table data-column-title-hidden data-view="cards" data-full-width="false"><thead><tr><th>Command / Brush</th><th>Description</th></tr></thead><tbody><tr><td><a href="./#ezplace"><code>//ezplace</code> (<code>//ezpl</code>)</a></td><td>Places a <strong>single</strong> structure at the <strong>player's position.</strong></td></tr><tr><td><a href="./#ezscatter"><code>//ezscatter</code> (<code>//ezsc</code>)</a></td><td>Places <strong>multiple</strong> structures within a <strong>selected region</strong>.</td></tr><tr><td><a href="./#ezarray"><code>//ezarray</code> (<code>//ezar</code>)</a></td><td>Places <strong>multiple</strong> structures sequentially <strong>along a path</strong>.</td></tr><tr><td><a href="./#ezbrush-place"><code>//ezbrush place</code> (<code>//ezbr pl</code>)</a></td><td>Brush that places a <strong>single</strong> structure at each <strong>brush click's target</strong>.</td></tr><tr><td><a href="./#ezbrush-scatter"><code>//ezbrush scatter (//ezbr sc)</code></a></td><td>Brush that places <strong>multiple</strong> structures in the area of each <strong>brush click's target</strong>.</td></tr><tr><td><a href="./#ezbrush-array"><code>//ezbrush array</code> (<code>//ezbr ar</code>)</a></td><td>Brush that places <strong>multiple</strong> structures along a <strong>brush stroke</strong>.</td></tr></tbody></table>

For completeness, one can also embed a structure or an array of structures into a shaped spline with the ezspline subcommand `//ezspline structure` (`//ezsp structure`). However, the structures are not "placed" as much as they are embedded into the spline path, meaning that the [alignment settings](primary+secondary-alignment.md) and the [placement parameters](placement-parameters.md) do not apply to that command. Which is why it is documented on the [splines page](../spline/) instead.

***

## Commands

This section lists the syntax of all structure commands with links to the corresponding sections.

***

### `//ezplace`

Alias: `//ezpl`

Places a **single** structure at the **player's position.**

`//ezplace` [`<structure>`](available-structures.md) [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>] [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-a]`](placement-parameters.md#place-air-a)

### `//ezbrush place`

Alias: `//ezbr pl`

Brush that places a **single** structure at each **brush click's target**.

`//ezbrush place` [`<structure>`](available-structures.md) [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>] [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-a]`](placement-parameters.md#place-air-a)

***

### `//ezscatter`

Alias: `//ezsc`

Places **multiple** structures within a **selected region**.

`//ezscatter` [`<structure>`](available-structures.md) [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>] [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-h <region>]`](scatter-parameters.md#scatter-region-h-less-than-region-greater-than) [`[-d <filterDirections>] [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than) [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than) [`[-i <seed>]`](scatter-parameters.md#distribution-seed-i-less-than-seed-greater-than) [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than) [`[-l <coverPattern>]`](scatter-parameters.md#mask-cover-block-b-less-than-pattern-greater-than) [`[-a]`](placement-parameters.md#place-air-a) [`[-t]`](scatter-parameters.md#cut-off-outside-the-selection-c)&#x20;

### `//ezbrush scatter`

Alias: `//ezbr sc`

Brush that places **multiple** structures in the area of each **brush click's target**.

`//ezbrush scatter` [`<structure>`](available-structures.md) [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](./#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](./#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>] [-k <orientationAxis>]`](./#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](./#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-h <region>]`](scatter-parameters.md#scatter-region-h-less-than-region-greater-than) [`[-d <filterDirections>] [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than) [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than) [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than) [`[-i <seed>]`](scatter-parameters.md#distribution-seed-i-less-than-seed-greater-than) [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than) [`[-l <coverPattern>]`](scatter-parameters.md#mask-cover-block-b-less-than-pattern-greater-than) [`[-a]`](placement-parameters.md#place-air-a) [`[-t]`](scatter-parameters.md#cut-off-outside-the-selection-c)&#x20;

***

### `//ezarray`

Alias: `//ezar`

Places **multiple** structures sequentially **along a path**.

`//ezarray` [`<structure>`](available-structures.md) [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>] [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than) [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than) [`[-a]`](placement-parameters.md#place-air-a) [`[-b]`](array-parameters.md#snap-placements-to-surfaces-b)

### `//ezbrush array`

Alias: `//ezbr ar`

Brush that places **multiple** structures along a **brush stroke**.

`//ezbrush array` [`<structure>`](available-structures.md) [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than) [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than) [`[-c <orientationAngle>] [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great) [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than) [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than) [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than) [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than) [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than) [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than) [`[-a]`](placement-parameters.md#place-air-a) [`[-b]`](array-parameters.md#snap-placements-to-surfaces-b)

***

{% hint style="info" %}
Note for server admins: The three structure brushes spawn BlockDisplay entities (only visible to the player using their brush) to help visualise the [Alignment](primary+secondary-alignment.md) of the brushes. You may disable the visualisation entities entirely or change how often they are updated in the `config.yml` under `visualisations`.

Additionally, the command `//ezdebug removeVisualiserEntities` will remove any entities spawned by ezEdits from your world in case they got bugged somehow and were not despawned correctly, which should never happen, but there you go.
{% endhint %}

***

## Subpage structure

This Structure Wiki has multiple subpages. Below you find an overview of the subpages.

{% hint style="info" %}
We suggest reading the [**Primary+Secondary Alignment**](primary+secondary-alignment.md) page more carefully, as it covers one of the fundamental concepts of the tools. The remaining chapters can be treated as reference materials, useful for specific tasks or to delve deeper into the tool's capabilities.
{% endhint %}

* [**Available Structures**](available-structures.md)
  * Covers the [`<structure>`](available-structures.md) parameter (necessary for place/scatter/array (and ezspline structure)).
* [**Primary+Secondary Alignment**](primary+secondary-alignment.md)
  * Covers the [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) parameters (available for place/scatter/array) and the accompanying flags:
    * [`[-j <snapDirections>]`](primary+secondary-alignment.md#snap-to-angles-j-less-than-anglesset-greater-than)
    * [`[-x]`](primary+secondary-alignment.md#perturb-secondary-x)
* [**Placement Parameters**](placement-parameters.md)
  * Covers the following flags (available for place/scatter/array):
    * [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than)
    * [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than)
    * [`[-c <orientationAngle>] [-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great)
    * [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than)
    * [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)
    * [`[-a]`](placement-parameters.md#place-air-a)
* [**Scatter Parameters**](scatter-parameters.md)
  * Covers the following flags (only available for scatter):
    * [`[-h <region>]`](scatter-parameters.md#scatter-region-h-less-than-region-greater-than)
    * [`[-d <filterDirections>] [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than)
    * [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than)
    * [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than)
    * [`[-i <seed>]`](scatter-parameters.md#distribution-seed-i-less-than-seed-greater-than)
    * [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than)
    * [`[-l <coverPattern>]`](scatter-parameters.md#mask-cover-block-b-less-than-pattern-greater-than)
    * [`[-t]`](scatter-parameters.md#trim-outside-selection-t)
* [**Array Parameters**](array-parameters.md)
  * Covers the following flags (only available for array):
    * [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than)
    * [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than)
    * [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than)
    * [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than)
    * [`[-b]`](array-parameters.md#snap-placements-to-surfaces-b)

<details>

<summary>Here are the <em>same</em> flags <em>again</em>, but in alphabetical order:</summary>

* [`[-a]`](placement-parameters.md#place-air-a)
* [`[-b]`](array-parameters.md#snap-placements-to-surfaces-b)
* [`[-c <orientationAngle>]` ](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great)
* [`[-d <filterDirections>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than)
* [`[-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-less-than-directions-greater-than-and-e-less-than-threshold-greater-than)
* [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f-less-than-randomflipsaxes-greater-than)
* [`[-g <gap>]`](array-parameters.md#distance-g-less-than-gap-greater-than)
* [`[-h <region>]`](scatter-parameters.md#scatter-region-h-less-than-region-greater-than)
* [`[-i <seed>]`](scatter-parameters.md#distribution-seed-i-less-than-seed-greater-than)
* [`[-j <restrictedAngles>]`](primary+secondary-alignment.md#snap-to-angles-j-less-than-anglesset-greater-than)
* [`[-k <orientationAxis>]`](placement-parameters.md#orientation-advanced-k-less-than-orientationaxis-greater-than-and-c-less-than-orientationangle-great)
* [`[-l <coverPattern>]`](scatter-parameters.md#mask-cover-block-b-less-than-pattern-greater-than)
* [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m-less-than-mask-greater-than)
* [`[-n <density>]`](scatter-parameters.md#density-n-less-than-density-greater-than)
* [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than)
* [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o-less-than-sizemultiplierrange-greater-than)
* [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p-less-than-kbparameters-greater-than)
* [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q-less-than-radii-greater-than)
* [`[-r <randomRotationAxis>]`](placement-parameters.md#random-90-rotations-r-less-than-randomrotationaxis-greater-than)
* [`[-s <dimensions>]`](placement-parameters.md#controlling-dimensions-s-less-than-dimensions-greater-than)
* [`[-t]`](scatter-parameters.md#trim-outside-selection-t)
* [`[-u <iterations>]`](scatter-parameters.md#uniformity-u-less-than-iterations-greater-than)
*

</details>



*
