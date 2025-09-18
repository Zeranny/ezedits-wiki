---
hidden: true
---

# Cylindrify & Spherify

***

#### ![](../../.gitbook/assets/ezdeform_cylindrify.png)

### //ezdeform <mark style="color:orange;">cylindrify</mark>

<details>

<summary><mark style="color:blue;">Cylindrify</mark></summary>

**`//ezdeform cylindrify [`**<mark style="color:orange;">**`-afost`**</mark>**`] [`**<mark style="color:orange;">**`-r <radii>`**</mark>**`] [`**<mark style="color:orange;">**`-d <depth>`**</mark>**`] [`**<mark style="color:orange;">**`-x <axisMap>`**</mark>**`] [`**<mark style="color:orange;">**`-i <primary>`**</mark>**`] [`**<mark style="color:orange;">**`-j <secondary>`**</mark>**`] [`**<mark style="color:orange;">**`-w <profile>`**</mark>**`]`**

Projects the region onto and generates a cylinder.

* <mark style="color:orange;">**-r \<radii>**</mark>: Set the radii and the halfsize of the generated cylinder. If not set, it is calculated based on the size of your selected region.&#x20;
* <mark style="color:orange;">**-d \<depth>**</mark>: Determines how deep the projection pattern should go towards the center of the generated cylinder. If not set, it is calculated based on the size of your selected region.&#x20;
* <mark style="color:orange;">**-x \<axisMap>**</mark>: Determines which input axis becomes which output axis. X/Y/Z are the axes of the input region. EW/UD/NS are the axes of the generated cylinder.
  * Examples:
* <mark style="color:orange;">**-i \<primary>**</mark> (defaults to `y`): Determines the orientation of the generated cylinder in space.
* <mark style="color:orange;">**-j \<secondary>**</mark> (defaults to `x`): Determines the orientation of the generated cylinder in space.
* <mark style="color:orange;">**-a**</mark>: Do not place a cuboid of air around the generated shape. (Air will still be placed if the input region contains air)
* <mark style="color:orange;">**-f**</mark>: Fill shape. Extrude the innermost layer into the center.
* <mark style="color:orange;">**-o**</mark>: Place shape around player instead of above/next-to the selection.
* <mark style="color:orange;">**-s**</mark>: Ignore half a block from the input in the east-west directions (Useful when stitching together a pattern.)
* <mark style="color:orange;">**-t**</mark>: Generate cylinder with a two-block center (requires -r to be set.)

- <mark style="color:orange;">**-w \<profile>**</mark>: See [Smoothblocks](../../smoothblocks/smoothblocks.md).

</details>

***

#### ![](../../.gitbook/assets/ezdeform_spherify.png)

### //ezdeform <mark style="color:orange;">spherify</mark>

<details>

<summary><mark style="color:blue;">Spherify</mark></summary>

**`//ezdeform spherify [`**<mark style="color:orange;">**`-aflost`**</mark>**`] [`**<mark style="color:orange;">**`-r <radii>`**</mark>**`] [`**<mark style="color:orange;">**`-d <depth>`**</mark>**`] [`**<mark style="color:orange;">**`-x <axisMap>`**</mark>**`] [`**<mark style="color:orange;">**`-i <primary>`**</mark>**`] [`**<mark style="color:orange;">**`-j <secondary>`**</mark>**`] [`**<mark style="color:orange;">**`-w <profile>`**</mark>**`]`**

Projects the region onto and generates a sphere / an ellipsoid using either Mercator projection (default) or a (single-patch) LAEA projection (<mark style="color:orange;">`-l`</mark>).

* <mark style="color:orange;">**-r \<radii>**</mark>: Set the radii of the generated sphere/ellipsoid.
* <mark style="color:orange;">**-d \<depth>**</mark>: Determines how deep the projection pattern should go towards the center of the generated sphere.
* <mark style="color:orange;">**-x \<axisMap>**</mark>: Determines which input axis becomes which output axis. X/Y/Z are the axes of the input region. EW/UD/NS are the axes of the generated sphere.
* <mark style="color:orange;">**-i \<primary>**</mark> (defaults to `y`): Determines the orientation of the generated sphere in space.
* <mark style="color:orange;">**-j \<secondary>**</mark> (defaults to `x`): Determines the orientation of the generated sphere in space.
* <mark style="color:orange;">**-a**</mark>: Do not place a cuboid of air around the generated sphere. (Air will still be placed if the input region contains air)
* <mark style="color:orange;">**-f**</mark>: Fill shape. Extrude the innermost layer into the center.
* <mark style="color:orange;">**-l**</mark>: Use LAEA projection instead of Mercator.
* <mark style="color:orange;">**-o**</mark>: Place sphere around player instead of above/next-to the selection.
* <mark style="color:orange;">**-s**</mark>: Ignore half a block from the input in the east-west directions (Useful when stitching together a pattern.)
* <mark style="color:orange;">**-t**</mark>: Generate sphere with a two-block center (requires -r to be set.)

- <mark style="color:orange;">**-w \<profile>**</mark>: See [Smoothblocks](../../smoothblocks/smoothblocks.md).

</details>

***
