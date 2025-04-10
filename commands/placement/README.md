# Placement

## Overview

ezEdits provides multiple ways to quickly and precisely place clipboards, schematics, and expression-based shapes, which we refer to as 'structures'.

The relevant commands and brushes (introduced in version 0.12.0) are:

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th>Command / Brush</th><th>Abbreviation</th><th>Description</th><th>Syntax</th><th>Parameters</th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><mark style="color:orange;"><strong><code>//ezplace</code></strong></mark></td><td><mark style="color:orange;"><strong><code>//ezpl</code></strong></mark></td><td>Places a <strong>single</strong> structure at the <strong>player's position.</strong></td><td><code>//ezplace</code> <a href="available-structures.md"><code>&#x3C;structure></code></a> <a href="primary+secondary-alignment.md"><code>[&#x3C;primary>][&#x3C;secondary>]</code></a></td><td>Accepts <a data-mention href="placement-parameters.md">placement-parameters.md</a>.</td><td></td></tr><tr><td><mark style="color:orange;"><strong><code>//ezbrush place</code></strong></mark></td><td><mark style="color:orange;"><strong><code>//ezbr pl</code></strong></mark></td><td>Brush that places a <strong>single</strong> structure at each <strong>brush click's target</strong>.</td><td><code>//ezbrush place</code> <a href="available-structures.md"><code>&#x3C;structure></code></a> <a href="primary+secondary-alignment.md"><code>[&#x3C;primary>] [&#x3C;secondary>]</code></a></td><td>Accepts <a data-mention href="placement-parameters.md">placement-parameters.md</a>.</td><td></td></tr><tr><td><mark style="color:orange;"><strong><code>//ezscatter</code></strong></mark></td><td><mark style="color:orange;"><strong><code>//ezsc</code></strong></mark></td><td>Places <strong>multiple</strong> structures within a <strong>selected region</strong>.</td><td><code>//ezscatter</code><a href="available-structures.md"><code>&#x3C;structure></code></a> <a href="primary+secondary-alignment.md"><code>[&#x3C;primary>] [&#x3C;secondary>]</code></a></td><td>Accepts <a data-mention href="placement-parameters.md">placement-parameters.md</a> and <a data-mention href="scatter-parameters.md">scatter-parameters.md</a>.</td><td></td></tr><tr><td><mark style="color:orange;"><strong><code>//ezbrush scatter</code></strong></mark></td><td><mark style="color:orange;"><strong><code>//ezbr sc</code></strong></mark></td><td>Brush that places <strong>multiple</strong> structures in the area of each <strong>brush click's target</strong>.</td><td><code>//ezbrush scatter</code><a href="available-structures.md"><code>&#x3C;structure></code></a> <a href="primary+secondary-alignment.md"><code>[&#x3C;primary>] [&#x3C;secondary>]</code></a></td><td>Accepts <a data-mention href="placement-parameters.md">placement-parameters.md</a> and <a data-mention href="scatter-parameters.md">scatter-parameters.md</a>.</td><td></td></tr><tr><td><mark style="color:orange;"><strong><code>//ezarray</code></strong></mark></td><td><mark style="color:orange;"><strong><code>//ezar</code></strong></mark></td><td>Places <strong>multiple</strong> structures sequentially <strong>along a path</strong>.</td><td><code>//ezarray</code><a href="available-structures.md"><code>&#x3C;structure></code></a> <a href="primary+secondary-alignment.md"><code>[&#x3C;primary>][&#x3C;secondary>]</code></a></td><td>Accepts <a data-mention href="placement-parameters.md">placement-parameters.md</a> and <a data-mention href="array-parameters.md">array-parameters.md</a>.</td><td></td></tr><tr><td><mark style="color:orange;"><strong><code>//ezbrush array</code></strong></mark></td><td><mark style="color:orange;"><strong><code>//ezbr ar</code></strong></mark></td><td>Brush that places <strong>multiple</strong> structures along a <strong>brush stroke</strong>.</td><td><code>//ezbrush array</code><a href="available-structures.md"><code>&#x3C;structure></code></a> <a href="primary+secondary-alignment.md"><code>[&#x3C;primary>] [&#x3C;secondary>]</code></a></td><td>Accepts <a data-mention href="placement-parameters.md">placement-parameters.md</a> and <a data-mention href="array-parameters.md">array-parameters.md</a>.</td><td></td></tr></tbody></table>

All six commands are based on the same underlying placement method. As a result, all six commands share the same syntax and parameters.

{% hint style="info" %}
For completeness, one can also embed a structure or an array of structures into a shaped spline with the ezspline subcommand `//ezspline structure` (`//ezsp structure`). However, the structures are not "placed" as much as they are embedded into the spline path, meaning that the [alignment settings](primary+secondary-alignment.md) and the [placement parameters](placement-parameters.md) do not apply to that command. Which is why it is documented on the [splines page](../spline/) instead.
{% endhint %}

***

## Subpage structure

This Placement wiki has multiple subpages. Below you find an overview of the subpages.

{% hint style="info" %}
We suggest reading the [**Primary+Secondary Alignment**](primary+secondary-alignment.md) page more carefully, as it covers one of the fundamental concepts of the tools. The remaining chapters can be treated as reference materials, useful for specific tasks or to delve deeper into the tool's capabilities.
{% endhint %}

* [**Available Structures**](available-structures.md)
  * Covers the [`<structure>`](available-structures.md) parameter (necessary for place/scatter/array (and ezspline structure)).
* [**Primary+Secondary Alignment**](primary+secondary-alignment.md)
  * Covers the [`[<primary>] [<secondary>]`](primary+secondary-alignment.md) parameters (available for place/scatter/array) and the accompanying flags:
    * [`[-j <snapDirections>]`](primary+secondary-alignment.md#snap-to-angles-j)
    * [`[-x]`](primary+secondary-alignment.md#perturb-secondary-x)
* [**Placement Parameters**](placement-parameters.md)
  * Covers the following flags (available for place/scatter/array):
    * [`[-s <dimensions>]`](placement-parameters.md#dimensions-s)
    * [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o)
    * [`[-c <orientationAngle>] [-k <orientationAxis>]`](placement-parameters.md#orientation-c-k)
    * [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f)
    * [`[-r <randomRotationAxis>]`](placement-parameters.md#random-rotations-r)
    * [`[-a]`](placement-parameters.md#place-air-a)
* [**Scatter Parameters**](scatter-parameters.md)
  * Covers the following flags (only available for scatter):
    * [`[-h <region>]`](scatter-parameters.md#scatter-region-h)
    * [`[-d <filterDirections>] [-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-e)
    * [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m)
    * [`[-n <density>]`](scatter-parameters.md#density-n)
    * [`[-i <seed>]`](scatter-parameters.md#distribution-seed-i)
    * [`[-u <iterations>]`](scatter-parameters.md#uniformity-u)
    * [`[-l <coverPattern>]`](scatter-parameters.md#mask-cover-pattern-l)
    * [`[-t]`](scatter-parameters.md#trim-outside-selection-t)
* [**Array Parameters**](array-parameters.md)
  * Covers the following flags (only available for array):
    * [`[-g <gap>]`](array-parameters.md#distance-g)&#x20;
    * ### [`[-y <maxOffset>]`](array-parameters.md#max-vertical-offset-y)  <a href="#max-vertical-offset-y" id="max-vertical-offset-y"></a>
    * [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q)
    * [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p)
    * [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n)
    * [`[-b]`](array-parameters.md#snap-to-surfaces-b)

<details>

<summary>Here are the <em>same</em> flags <em>again</em>, but in alphabetical order:</summary>

* [`[-a]`](placement-parameters.md#place-air-a)
* [`[-b]`](array-parameters.md#snap-to-surfaces-b)
* [`[-c <orientationAngle>]`](placement-parameters.md#orientation-c-k)
* [`[-d <filterDirections>]`](scatter-parameters.md#directional-filter-d-e)
* [`[-e <filterThreshold>]`](scatter-parameters.md#directional-filter-d-e)
* [`[-f <randomFlipsAxes>]`](placement-parameters.md#random-flips-f)
* [`[-g <gap>]`](array-parameters.md#distance-g)
* [`[-h <region>]`](scatter-parameters.md#scatter-region-h)
* [`[-i <seed>]`](scatter-parameters.md#distribution-seed-i)
* [`[-j <restrictedAngles>]`](primary+secondary-alignment.md#snap-to-angles-j)
* [`[-k <orientationAxis>]`](placement-parameters.md#orientation-c-k)
* [`[-l <coverPattern>]`](scatter-parameters.md#mask-cover-pattern-l)
* [`[-m <maskFilter>]`](scatter-parameters.md#mask-filter-m)
* [`[-n <density>]`](scatter-parameters.md#density-n)
* [`[-n <normalMode>]`](array-parameters.md#spline-orientation-n)
* [`[-o <sizeMultiplierRange>]`](placement-parameters.md#random-scaling-o)
* [`[-p <kbParameters>]`](array-parameters.md#path-parameters-p)
* [`[-q <radiiMultiplier>]`](array-parameters.md#progressive-scaling-q)
* [`[-r <randomRotationAxis>]`](placement-parameters.md#random-rotations-r)
* [`[-s <dimensions>]`](placement-parameters.md#dimensions-s)
* [`[-t]`](scatter-parameters.md#trim-outside-selection-t)
* [`[-u <iterations>]`](scatter-parameters.md#uniformity-u)
* [`[-x]`](primary+secondary-alignment.md#perturb-secondary-x)
* ### [`[-y <maxOffset>]`](array-parameters.md#max-vertical-offset-y)  <a href="#max-vertical-offset-y" id="max-vertical-offset-y"></a>

</details>

***

{% hint style="warning" %}
Note for server admins: The three placement brushes spawn BlockDisplay entities (only visible to the player using their brush) to help visualise the [Alignment](primary+secondary-alignment.md) of the brushes. You may disable the visualisation entities entirely or change how often they are updated in the `config.yml` under `visualisations`.

Additionally, the command `//ezdebug removeVisualiserEntities` will remove any entities spawned by ezEdits from your world in case they got bugged somehow and were not despawned correctly, which should never happen, but there you go.
{% endhint %}

***
