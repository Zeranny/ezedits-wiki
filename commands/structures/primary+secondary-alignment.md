# Primary+Secondary Alignment

Alignment defines the orientation at which the structure is placed.

## Explanation

Every structure has an intrinsic "up" direction and an intrinsic "forward" direction. By default, structures are placed with their up direction facing, well, up (+y), and with their forward direction facing forward (+x).

The most important thing is now: You can define how a structure is placed by defining where its up direction should face and where its forward direction should face (aka. aligning its internal coordinate system).

We let the user define the alignment using two directions:

{% hint style="info" %}
The `<primary>` direction defines the placement's +y direction.

The `<secondary>` direction together with the primary direction imply the placement's +x direction.

Note: The primary and secondary may not be the same direction.
{% endhint %}

<details>

<summary>More in-depth explanation using examples:</summary>

Let's say this is our build that we want to place, by for example having it as our current WorldEdit clipboard.

<img src="../../.gitbook/assets/AlignmentGuide_example1.png" alt="" data-size="original">

For reference, the red beam is facing towards positive x (east), the blue beam is facing towards positive z (south), and the green beam is facing towards positive y (up).

We now want to place it at various orientations using any of the ezEdits structure commands. For this we may to define a `<primary>` and `<secondary>` direction. Let us go through a few examples for a few such assignments of these parameters and try to understand what is happening:

Let's set the `<primary>` to `up` and the `<secondary>` to `east` (These are their default directions):

<img src="../../.gitbook/assets/AlignmentGuide_example1.png" alt="" data-size="original">

Our shape is pasted exactly in the same orientation as we copied it. Up is still up, right is still right, and so on.

Now, consider the following two examples:

1. The **`<primary>`** is set to **`south`** and the `<secondary>` remains at `east`:

<img src="../../.gitbook/assets/AlignmentGuide_example2.png" alt="" data-size="original">

Notice how, what was originally "up" when we copied it, i.e. the green beam in our case, is pointing into the direction that we set the primary to: south. Meanwhile what was originally east, is still east. The blue beam is going down as a consequence of this 90° rotation.

2. The **`<primary>`** is set to the vector **`(0,1,1)`**, i.e. the direction going "diagonally" up and south, and the `<secondary>` to `east`:

<img src="../../.gitbook/assets/AlignmentGuide_example3.png" alt="" data-size="original">

Notice, again, how, what was originally "up" when we copied it, i.e. the green beam in our case, is pointing into the direction that we set the primary to: diagonally up and south.

Here's another interesting example:

The **`<primary>`** is set to the vector **`(1,1,0)`**, i.e. the direction going diagonally up and **east**, while the `<secondary>` is set to `east`:

<img src="../../.gitbook/assets/AlignmentGuide_example4.png" alt="" data-size="original">

The green beam is correctly pointing along the primary direction, diagonally up and east. Whatever was pointing up when we //copy'd our clipboard is always aligned with whatever direction the primary is set to!

But now, notice how, even though the secondary is set to east, the red beam is not pointing directly east anymore (but diagonally down and east). This is intended behavior.

Imagine if it were pointing east: Then the green and red beam would be at a 45° angle instead of the original 90° angle. Our structure would be deformed/bent/sheared.

What we decided to implement instead, is that (while we align the structure's +y direction with the given primary direction) instead of aligning the structure's +x direction with the given secondary direction, we choose the direction that is most similar to the given secondary direction but that is still perpendicular to the primary.

So, if the primary and secondary are not perfectly perpendicular, as in the example above, the secondary is swapped out with the most similar but still perpendicular vector!

Just for reference, here's a small GIF that shows the remaining perpendicular secondary directions for a set primary direction:

<img src="../../.gitbook/assets/AlignmentGuide_example5.gif" alt="" data-size="original">

To give a final example:

The **`<primary>`** is set to the vector **`(-1,2,-1)`**, i.e. a direction going up and northwest, while the **`<secondary>`** is set to **`west`**:

<img src="../../.gitbook/assets/AlignmentGuide_example6.png" alt="" data-size="original">

As you can see, the green beam, or what was originally up in our build when we copied it, is now pointing into our specified `northwest+2*up` direction, while the red beam, or what was originally east when we copied, is now pointing as `west` as it can while still being perpendicular to the primary.

All of this applies independently of your current clipboard. Here's another structure at its original orientation followed by its placement aligned just like the previous example.

<img src="../../.gitbook/assets/AlignmentGuide_example7.png" alt="" data-size="original">

<img src="../../.gitbook/assets/AlignmentGuide_example8.png" alt="" data-size="original">

Can you see why setting the primary to `(-1,2-1)` and the secondary to `west` leads to the leaf being oriented like that?

\*\*\*

By the way, the command used was

`//ezbrush place Clipboard Constant(Direction:(-1,2,-1)) Constant(Direction:west)`

or, if you fancy abbreviations,

`//ezbr pl Cl C(D:(-1,2,-1)) C(D:west)`

With this primary + secondary system, we hope that you can easily and quickly construct your desired 3D orientation for each structure placement in any scenario.

</details>

## Overview

The primary and secondary can be set to either:

<table data-view="cards" data-full-width="false"><thead><tr><th>Name</th><th>Abbreviation</th><th>Description</th></tr></thead><tbody><tr><td><a href="primary+secondary-alignment.md#constant"><strong><code>Constant</code></strong></a></td><td><strong><code>C</code></strong></td><td>Explicitly set a constant direction for all placements.</td></tr><tr><td><a href="primary+secondary-alignment.md#random"><strong><code>Random</code></strong></a></td><td><strong><code>R</code></strong></td><td>Random direction for each placement.</td></tr><tr><td><a href="primary+secondary-alignment.md#noise"><strong><code>Noise</code></strong></a></td><td><strong><code>N</code></strong></td><td>Direction based on the evaluation of a noise function at the placement's position.</td></tr><tr><td><a href="primary+secondary-alignment.md#aim"><strong><code>Aim</code></strong></a></td><td><strong><code>A</code></strong></td><td>Your player aim direction.</td></tr><tr><td><a href="primary+secondary-alignment.md#playerrelative"><strong><code>PlayerRelative</code></strong></a></td><td><strong><code>P</code></strong></td><td>The direction from the placement's position towards the current player position.</td></tr><tr><td><a href="primary+secondary-alignment.md#surfacenormal"><strong><code>SurfaceNormal</code></strong></a></td><td><strong><code>S</code></strong></td><td>The approximate surface-normal in the region of the placement's position.</td></tr><tr><td><a href="primary+secondary-alignment.md#viewdiff"><strong><code>ViewDiff</code></strong></a></td><td><strong><code>V</code></strong></td><td>Define a direction using two clicks. Exclusively for brushes.</td></tr><tr><td><a href="primary+secondary-alignment.md#tangential"><strong><code>Tangential</code></strong></a></td><td><strong><code>T</code></strong></td><td>The direction tangential to the path. Exclusively for arrays.</td></tr><tr><td><a href="primary+secondary-alignment.md#orthogonal"><strong><code>Orthogonal</code></strong></a></td><td><strong><code>O</code></strong></td><td>The direction orthogonal to the path. Exclusively for arrays.</td></tr></tbody></table>

## Settings

### Constant

Explicitly set a constant direction for all placements.

Syntax: `Constant(Direction:<direction>)`

Abbreviation: `C(D:<direction>)`

If you do not specify a `<direction>`, then:

* the default direction is **+y** if you're setting the `<primary>`.
* the default direction is **+x** if you're setting the `<secondary>`.

There are various ways to define a direction. From using the axes, cardinal directions, vector notation, or player relative directions like forward, left, right, etc. Pro tip: You can also add directions together using simple arithmetic operators, like `east-z+(0,0.5,0)`. Pro tip²: Put `=` at the end to evaluate your direction expression as you are typing it.

<details>

<summary>Examples</summary>

`//ezsc Clipboard C(v:(0,2,0)) C(v:east)`

<img src="../../.gitbook/assets/ConstantAlignment_example1.png" alt="" data-size="original">

`//ezsc Clipboard C(v:(-1,2,-1)) C(v:east)`

<img src="../../.gitbook/assets/ConstantAlignment_example2.png" alt="" data-size="original">

`//ezsc Clipboard C(v:(-1,2,-1)) C(v:-aim)`

<img src="../../.gitbook/assets/ConstantAlignment_example3.png" alt="" data-size="original">

</details>

### Random

Random direction for each placement.

Syntax: `Random`

Abbreviation: `R`

<details>

<summary>Examples</summary>

`//ezsc Clipboard Constant Random`

* Only setting the `<secondary>` to Random, primary remains pointing up
* Notice how our structure's up direction (green beam) remains up (primary is set to up), but each placement is randomly rotated around the primary (y-axis in this case) since the secondary is random.

<img src="../../.gitbook/assets/RandomAlignment_demo1.png" alt="" data-size="original">

`//ezsc Clipboard Random Constant`

* Only setting the `<primary>` to Random, secondary remains pointing east.
* Terrain replaced with glass so you can see better.
* Notice how the green beam is now facing all kinds of directions, but the red beam is roughly pointing east for all placements.

<img src="../../.gitbook/assets/RandomAlignment_demo2.png" alt="" data-size="original">

`//ezsc Clipboard Random Random`

* Setting both to Random

<img src="../../.gitbook/assets/RandomAlignment_demo3.png" alt="" data-size="original">

</details>

### Noise

Direction based on the evaluation of a noise function at the placement's position.

Syntax: `Noise(Noise:<noise>)`

Abbreviation: `N(N:<noise>)`

<details>

<summary>Examples</summary>

`//ezsc Clipboard Constant Noise`

![](../../.gitbook/assets/2024-12-01_13.55.50.png)

`//ezsc Clipboard Constant Noise(N:Vor(Freq:0.02,DistReturn:cell))`

![](../../.gitbook/assets/2024-12-01_13.54.01.png)

a

a

</details>

### Aim

Your player's aim direction.

Syntax: `Aim`

Abbreviation: `A`

Note: For brushes, `Constant(Direction:aim)` will use your player's aim direction at the time of brush binding, while `Aim` will use the player's aim direction at the time of each brush act.

<details>

<summary>Examples</summary>

`//ezsc Clipboard Aim Constant`

<img src="../../.gitbook/assets/AimAlignment_demo1.png" alt="" data-size="original"><img src="../../.gitbook/assets/AimAlignment_demo2.png" alt="" data-size="original">

</details>

### PlayerRelative

The direction from the placement's position towards the current player position.

Syntax: `PlayerRelative`

Abbreviation: `P`

<details>

<summary>Examples</summary>

`//ezsc Clipboard PlayerRelative Constant`

<img src="../../.gitbook/assets/PlayerRelative_demo1.png" alt="" data-size="original">  <img src="../../.gitbook/assets/PlayerRelative_demo2.png" alt="" data-size="original">

`//ezbr place Shape(S:Cone,Pattern:diamond_block) PlayerRelative Constant -s 12,36,12`

<img src="../../.gitbook/assets/PlayerRelative_demo3.gif" alt="" data-size="original">

</details>

### SurfaceNormal

The approximate surface-normal in the region of the placement's position.

Syntax: `SurfaceNormal`

Abbreviation: `S`

By [normal](https://en.wikipedia.org/wiki/Normal_\(geometry\)) we mean the direction perpendicular to the terrain in question.

<details>

<summary>Examples</summary>

`//ezbr shape Shape(P:57,S:Cone) SurfaceNormal Constant -s 12,36,12`

<img src="../../.gitbook/assets/SurfaceNormal_demo1.gif" alt="" data-size="original">

</details>

### ViewDiff

Define a direction using two clicks. Exclusively for brushes.

Syntax: `ViewDiff`

Abbreviation: `V`

Each placement requires a right click and a left click. The first right click sets the placement position at the targeted block. Left-clicking somewhere else then defines a direction: From your first (right) click target position to your second (left) click.

<details>

<summary>Examples</summary>

`//ezbr place Clipboard SurfaceNormal ViewDiff`

Here I set the primary to SurfaceNormal and control the secondary direction with a second click through the ViewDiff mode. Pay attention to my hand. You can see me alternating between right- and left-clicks. A right click sets the placement position, and a left click sets the ViewDiff direction.

![](../../.gitbook/assets/output.gif)



`//ezbr place Shape(S:Torus(Thickness:0.4),P:57) PlayerRelative ViewDiff -s 20,20,30 -k x -c 90`

This torus shape required a few more parameters, so this example turned out a bit longer than usual. What's important to see here is that the primary is set to PlayerRelative, meaning the top of the torus always faces the player. The final orientation is determined with a second click though. Here I alternate between left-clicking above and left/right from the placement position to create a linked chain.

![](<../../.gitbook/assets/output (1).gif>)

</details>

### Tangential

The direction tangential to the path. Exclusively for arrays.

Syntax: `Tangential`

Abbreviation: `T`

<details>

<summary>Examples</summary>

`//ezarray Clipboard Tangential Constant -g 11 -o 2`

The _Tangential_ direction points tangential to the spline path at the position of the placement. If you set the primary to _Tangential_, the top of the shape is pointing along the spline like this.

![](../../.gitbook/assets/2024-12-01_16.11.04.png)



</details>

### Orthogonal

The direction orthogonal to the path. Exclusively for arrays.

Syntax: `Orthogonal(Angle:<angle>)`

Abbreviation: `O(A:<angle>)`

The angle, given in degrees, defines the initial direction of the orthogonal direction, whereby 0° and 360°, will face up (at the first part of the spline), 90° and 270° face left and right, and 180° faces down.

<details>

<summary>Examples</summary>

`//ezarray Clipboard Orthogonal Constant -g 11 -o 2`

The _Orthogonal_ direction points perpendicular to the spline path at the position of the placement. If you set the primary to _Orthogonal_, the top of the shape will point perpendicular to the spline path like this.

![](../../.gitbook/assets/2024-12-01_16.16.08.png)



`//ezarray Clipboard Orthogonal Constant -g 11 -o 2 -n HORIZONTAL`

The [-n flag](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than) has a direct influence on the orthogonal direction.

![](../../.gitbook/assets/2024-12-01_16.16.19.png)

</details>
