# Primary+Secondary Alignment

The two alignment directions define the _orientation_ at which the structure is placed.

## Explanation

Every structure has an intrinsic "up" direction and an intrinsic "forward" direction. By default, structures are placed with their up direction facing, well, up (+y), and with their forward direction facing forward (+x).

The most important thing is that now you can control how a structure is placed by defining where its up direction and where its forward direction should face.

We let the user define the alignment using two directions:

{% hint style="info" %}
The `<primary>` direction _defines_ the placement's +y direction.

The `<secondary>` direction _implies_ the placement's +x direction. From all directions perpendicular to the primary direction, the chosen +x direction is the one that most closely aligns with the given secondary direction.

Note: The primary and secondary may not be the same direction.
{% endhint %}

<details>

<summary><mark style="color:blue;">More in-depth explanation using examples:</mark></summary>

Let's say this is our build that we want to place, by for example having it as our current WorldEdit clipboard.

<img src="../../.gitbook/assets/AlignmentGuide_example1.png" alt="" data-size="original">

For reference, the red beam is facing towards positive x (east), the blue beam is facing towards positive z (south), and the green beam is facing towards positive y (up).

We now want to place it at various orientations using any of the ezEdits structure commands. For this, we may define a `<primary>` and `<secondary>` direction. Let us go through a few examples for a few such assignments of these parameters and try to understand what is happening:

Let's set the `<primary>` to `up` and the `<secondary>` to `east` (You'd use the [Constant](primary+secondary-alignment.md#constant) mode for that.) (These directions are the default directions):

<img src="../../.gitbook/assets/AlignmentGuide_example1.png" alt="" data-size="original">

Our shape is pasted exactly in the same orientation as we copied it. Up is still up, right is still right, and so on.

Now, consider the following three examples:

1. The **`<primary>`** is set to **`south`** and the `<secondary>` remains at `east`:

<img src="../../.gitbook/assets/AlignmentGuide_example2.png" alt="" data-size="original">

Notice how, what was originally _"up"_ when we copied it, i.e. the green beam in our case, is pointing into the direction that we set the primary to: _south_. Meanwhile what was originally _east_, is still _east_. The blue beam is going down as a consequence of this 90° rotation.

2. The **`<primary>`** is set to the vector **`(0,1,1)`**, i.e. the direction going "diagonally" up and south, and the `<secondary>` to `east`:

<img src="../../.gitbook/assets/AlignmentGuide_example3.png" alt="" data-size="original">

Notice again, how what was originally _"up"_ when we copied it, i.e. the green beam in our case, is pointing into the direction that we set the primary to: _diagonally up and south_.

3. The **`<primary>`** is set to the vector **`(1,1,0)`**, i.e. the direction going diagonally up and **east**, while the `<secondary>` is set to `east`:

<img src="../../.gitbook/assets/AlignmentGuide_example4.png" alt="" data-size="original">

The green beam is correctly pointing along the primary direction, diagonally up and east. Whatever was pointing _up_ when we //copy'd our clipboard is always aligned with whatever direction the primary is set to!

But now, even though the secondary is set to _east_, the red beam is not pointing directly east anymore (but diagonally down and east). This is intended behaviour.

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

<img src="../../.gitbook/assets/AlignmentGuide_example7.png" alt="" data-size="original"><img src="../../.gitbook/assets/AlignmentGuide_example8.png" alt="" data-size="original">

Can you see why setting the primary to `(-1,2-1)` and the secondary to `west` leads to the leaf being oriented like that?

***

By the way, the command used was

`//ezbrush place Clipboard Constant(Direction:(-1,2,-1)) Constant(Direction:west)`

or, if you fancy abbreviations,

`//ezbr pl Cl C(D:(-1,2,-1)) C(D:west)`

With this primary + secondary system, we hope that you can easily and quickly construct your desired 3D orientation for each structure placement in any scenario.

</details>

***

## Overview

The primary and secondary can be set to either:

<table data-view="cards" data-full-width="false"><thead><tr><th>Name</th><th>Abbreviation</th><th>Description</th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><a href="primary+secondary-alignment.md#constant"><strong><code>Constant</code></strong></a></td><td><strong><code>C</code></strong></td><td>Explicitly set a constant direction for all placements.</td><td><a href="primary+secondary-alignment.md#constant">#constant</a></td></tr><tr><td><a href="primary+secondary-alignment.md#random"><strong><code>Random</code></strong></a></td><td><strong><code>R</code></strong></td><td>Random direction for each placement.</td><td><a href="primary+secondary-alignment.md#random">#random</a></td></tr><tr><td><a href="primary+secondary-alignment.md#noise"><strong><code>Noise</code></strong></a></td><td><strong><code>N</code></strong></td><td>Direction based on the evaluation of a noise function at the placement's position.</td><td><a href="primary+secondary-alignment.md#noise">#noise</a></td></tr><tr><td><a href="primary+secondary-alignment.md#aim"><strong><code>Aim</code></strong></a></td><td><strong><code>A</code></strong></td><td>Your player aim direction.</td><td><a href="primary+secondary-alignment.md#aim">#aim</a></td></tr><tr><td><a href="primary+secondary-alignment.md#playerrelative"><strong><code>PlayerRelative</code></strong></a></td><td><strong><code>P</code></strong></td><td>The direction from the placement's position towards the current player position.</td><td><a href="primary+secondary-alignment.md#playerrelative">#playerrelative</a></td></tr><tr><td><a href="primary+secondary-alignment.md#surfacenormal"><strong><code>SurfaceNormal</code></strong></a></td><td><strong><code>S</code></strong></td><td>The approximate surface-normal in the region of the placement's position.</td><td><a href="primary+secondary-alignment.md#surfacenormal">#surfacenormal</a></td></tr><tr><td><a href="primary+secondary-alignment.md#viewdiff"><strong><code>ViewDiff</code></strong></a></td><td><strong><code>V</code></strong></td><td>Define a direction using two clicks. Exclusively for brushes.</td><td><a href="primary+secondary-alignment.md#viewdiff">#viewdiff</a></td></tr><tr><td><a href="primary+secondary-alignment.md#tangential"><strong><code>Tangential</code></strong></a></td><td><strong><code>T</code></strong></td><td>The direction tangential to the path. Exclusively for arrays.</td><td><a href="primary+secondary-alignment.md#tangential">#tangential</a></td></tr><tr><td><a href="primary+secondary-alignment.md#orthogonal"><strong><code>Orthogonal</code></strong></a></td><td><strong><code>O</code></strong></td><td>The direction orthogonal to the path. Exclusively for arrays.</td><td><a href="primary+secondary-alignment.md#orthogonal">#orthogonal</a></td></tr></tbody></table>

***

## Settings

***

### Constant

Explicitly set a constant direction for all placements.

Syntax: <mark style="color:orange;">**`Constant`**</mark> or <mark style="color:orange;">**`Constant(Direction:<direction>)`**</mark>

Abbreviation: <mark style="color:orange;">**`C`**</mark> or <mark style="color:orange;">**`C(D:<direction>)`**</mark>

If you do not specify a `<direction>`, then:

* the default direction is **+y** if you're setting the `<primary>`.
* the default direction is **+x** if you're setting the `<secondary>`.

There are various ways to define a direction. From using the axes, cardinal directions, vector notation, or player relative directions like forward, left, right, etc. Pro tip: You can also add directions together using simple arithmetic operators, like `east-z+(0,0.5,0)`. Pro tip²: Put `=` at the end to evaluate your direction expression as you are typing it.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezsc Clipboard C(D:(0,2,0)) C(D:east)`

<img src="../../.gitbook/assets/ConstantAlignment_example1.png" alt="" data-size="original">

`//ezsc Clipboard C(D:(-1,2,-1)) C(D:east)`

<img src="../../.gitbook/assets/ConstantAlignment_example2.png" alt="" data-size="original">

`//ezsc Clipboard C(D:(-1,2,-1)) C(D:-aim)`

<img src="../../.gitbook/assets/ConstantAlignment_example3.png" alt="" data-size="original">

</details>

***

### Random

Random direction for each placement.

Syntax: <mark style="color:orange;">**`Random`**</mark>

Abbreviation: <mark style="color:orange;">**`R`**</mark>

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezsc Clipboard Constant Random`

Only setting the `<secondary>` to Random here, primary remains pointing up. Notice how our structure's up direction (green beam) remains up (primary is set to up), but each placement is randomly rotated around the primary (y-axis in this case) since the secondary is random.

<img src="../../.gitbook/assets/RandomAlignment_demo1.png" alt="" data-size="original">

`//ezsc Clipboard Random Constant`

Only setting the `<primary>` to Random, secondary remains pointing east. The terrain was replaced with glass so you can see better. Notice how the green beam is now facing all kinds of directions, but the red beam is roughly pointing east for all placements.

<img src="../../.gitbook/assets/RandomAlignment_demo2.png" alt="" data-size="original">

`//ezsc Clipboard Random Random`

If we set both to Random, then we get true random chaos.

<img src="../../.gitbook/assets/RandomAlignment_demo3.png" alt="" data-size="original">

</details>

***

### Noise

Direction based on the evaluation of a noise function at the placement's position.

Syntax: <mark style="color:orange;">**`Noise`**</mark> or <mark style="color:orange;">**`Noise(Noise:<noise>)`**</mark>

Abbreviation: <mark style="color:orange;">**`N`**</mark> or <mark style="color:orange;">**`N(N:<noise>)`**</mark>

The default `<noise>` is `Perlin(Freq:0.01)`.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezsc Clipboard Constant Noise`

* Top-down screenshot
* `<primary>` is still up and only the `<secondary>` is set to Noise.
* The default Noise is Perlin Noise.

<img src="../../.gitbook/assets/NoiseAlignment_example2.png" alt="" data-size="original">

`//ezsc Clipboard Constant Noise(N:Vor(Freq:0.02,DistReturn:cell))`

* Same scenario as above but using [Cellular Noise](https://en.wikipedia.org/wiki/Voronoi_diagram#/media/File:Coloured_Voronoi_3D_slice.svg).
* You can recognize how each cell has its own random direction.

<img src="../../.gitbook/assets/NoiseAlignment_example1.png" alt="" data-size="original">

</details>

***

### Aim

Your player's aim direction.

Syntax: <mark style="color:orange;">**`Aim`**</mark>

Abbreviation: <mark style="color:orange;">**`A`**</mark>

Note: For brushes, `Constant(Direction:aim)` will use your player's aim direction at the time of brush binding, while `Aim` will use the player's aim direction during each brush act.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezsc Clipboard Aim Constant`

If we set the `<primary>` to `Aim` then the up direction of our structure, the green beam in our example, will align with our current player's aim direction.

My player model is included in the picture for reference. That's where I was looking when I executed the command. _The aim direction is visualized in F3+B with the thin blue line_

<img src="../../.gitbook/assets/AimAlignment_demo1.png" alt="" data-size="original"> <img src="../../.gitbook/assets/AimAlignment_demo2.png" alt="" data-size="original">

</details>

***

### PlayerRelative

The direction from the placement's position towards the current player position.

Syntax: <mark style="color:orange;">**`PlayerRelative`**</mark>

Abbreviation: <mark style="color:orange;">**`P`**</mark>

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezsc Clipboard PlayerRelative Constant`

If you set the `<primary>` to `PlayerRelative`, then each structure is placed such that its up direction is pointing towards your player position.

If you look closely, you can see my player model in the pictures. That's where I executed the command.

<img src="../../.gitbook/assets/PlayerRelative_demo1.png" alt="" data-size="original"> <img src="../../.gitbook/assets/PlayerRelative_demo2.png" alt="" data-size="original">

`//ezbr place Shape(S:Cone,P:diamond_block) PlayerRelative Constant -s 12,36,12`

<img src="../../.gitbook/assets/PlayerRelative_demo3.gif" alt="" data-size="original">

</details>

***

### SurfaceNormal

The approximate surface-normal in the region of the placement's position.

Syntax: <mark style="color:orange;">**`SurfaceNormal`**</mark>

Abbreviation: <mark style="color:orange;">**`S`**</mark>

By [normal](https://en.wikipedia.org/wiki/Normal_\(geometry\)) we mean the direction perpendicular to the terrain in question.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezbr place Shape(P:57,S:Cone) SurfaceNormal Constant -s 12,36,12`

You can see our ingame alignment visualizer dynamically orient itself depending on which part of the terrain you are looking at when you are holding the brush.

<img src="../../.gitbook/assets/SurfaceNormal_demo1.gif" alt="" data-size="original">

</details>

***

### ViewDiff

Define a direction using two clicks. Exclusively for brushes.

Syntax: <mark style="color:orange;">**`ViewDiff`**</mark>

Abbreviation: <mark style="color:orange;">**`V`**</mark>

Each placement requires a right click and a left click. The first right click sets the placement position at the targeted block. Left-clicking somewhere else then defines a direction: From your first (right) click target position to your second (left) click.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezbr place Clipboard SurfaceNormal ViewDiff`

Here I set the primary to SurfaceNormal and control the secondary direction with a second click through the ViewDiff mode. Pay attention to my hand. You can see me alternating between right- and left-clicks. A right click sets the placement position, and a left click sets the ViewDiff direction. Our ingame alignment visualizer dynamically updates depending on your movement and your actions.

<img src="../../.gitbook/assets/output.gif" alt="" data-size="original">

`//ezbr place Shape(S:Torus(Thickness:0.4),P:57) PlayerRelative ViewDiff -s 20,20,30 -k x -c 90`

This torus shape required a few more parameters, so this example turned out a bit longer than usual. What's important to notice though is that the primary is set to PlayerRelative, meaning the top of the torus always faces the player, and the secondary is set to ViewDiff, meaning the final orientation is determined with a second click. Here, after each right-click, I alternate between left-clicking above and left/right from the placement position to create a linked chain.

<img src="../../.gitbook/assets/output (1).gif" alt="" data-size="original">

</details>

***

### Tangential

The direction tangential to the path. Exclusively for arrays.

Syntax: <mark style="color:orange;">**`Tangential`**</mark>

Abbreviation: <mark style="color:orange;">**`T`**</mark>

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezarray Clipboard Tangential Constant -g 11 -o 2`

The _Tangential_ direction points tangential to the spline path at the position of the placement. If you set the primary to _Tangential_, the top of the shape is pointing along the spline like this.

<img src="../../.gitbook/assets/TangentialAlignment_example1.png" alt="" data-size="original">

</details>

***

### Orthogonal

The direction orthogonal to the path. Exclusively for arrays.

Syntax: <mark style="color:orange;">**`Orthogonal`**</mark> or <mark style="color:orange;">**`Orthogonal(Angle:<angle>)`**</mark>

Abbreviation: <mark style="color:orange;">**`O`**</mark> or <mark style="color:orange;">**`O(A:<angle>)`**</mark>

The angle, given in degrees, defines the initial direction of the orthogonal direction, whereby 0° and 360°, will face up, 90° and 270° face left and right, and 180° faces down (at the first part of the spline at least. It may twist further along if the normal mode is set to CONSISTENT, which is the default setting).

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezarray Clipboard Orthogonal Constant`

The _Orthogonal_ direction points perpendicular to the spline path at the position of the placement. If you set the primary to _Orthogonal_, the top of the shape will point perpendicular to the spline path like this.

<img src="../../.gitbook/assets/OrthogonalAlignment_example1.png" alt="" data-size="original">

Here's a GIF going through the `<angle>` parameter:

<img src="../../.gitbook/assets/StructuresAlignmentsOrthogonal_example.gif" alt="" data-size="original">

`//ezarray Clipboard Orthogonal Constant -n HORIZONTAL`

The [-n flag](array-parameters.md#spline-orientation-n-less-than-normalmode-greater-than) has a direct influence on the orthogonal direction.

<img src="../../.gitbook/assets/OrthogonalAlignment_example2.png" alt="" data-size="original">

</details>

***

## Parameters

The following flags adjust how Alignments are calculated.

***

### Snap to certain directions: <mark style="color:orange;">`[-j <snapDirections>]`</mark>

This parameter allows you to restrict the chosen alignment direction to the specified subset. E.g. snapping to / only allowing cardinal direction, i.e. 90° rotations.

Available options:

* <mark style="color:orange;">**`MULTIPLES_90`**</mark>
  * Only allows multiples of 90°, i.e. all axis-aligned directions.
* <mark style="color:orange;">**`MULTIPLES_45`**</mark>
  * Only allows multiples of 45°, i.e. axis-aligned directions AND all perfect diagonals.
* <mark style="color:orange;">**`MULTIPLES_22_5`**</mark>
  * Only allows multiples of 22.5°.
* <mark style="color:orange;">**`MULTIPLES_15`**</mark>
  * Only allows multiples of 15°.
* <mark style="color:orange;">**`DIAGONALS_1_1`**</mark>
  * Only allows axis-aligned directions, and perfect "1:1" diagonals.
* <mark style="color:orange;">**`DIAGONALS_2_1`**</mark>
  * Only allows the <mark style="color:orange;">`DIAGONALS_1_1`</mark> directions and any "2:1" diagonals.
* <mark style="color:orange;">**`DIAGONALS_3_1`**</mark>
  * Only allows the <mark style="color:orange;">`DIAGONALS_2_1`</mark> directions and any "3:1" diagonals.
* <mark style="color:orange;">**`DIAGONALS_4_1`**</mark>
  * Only allows the <mark style="color:orange;">`DIAGONALS_3_1`</mark> directions and any "4:1" diagonals.
* <mark style="color:orange;">**`DIAGONALS_5_1`**</mark>
  * Only allows the <mark style="color:orange;">`DIAGONALS_4_1`</mark> directions and any "5:1" diagonals.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezbrush Cl Constant ViewDiff -j MULTIPLES_45`

<img src="../../.gitbook/assets/AlignmentSnapToAngles_example.gif" alt="" data-size="original">

</details>

***

### Perturb Secondary: <mark style="color:orange;">\[-x]</mark>

In our primary+secondary system, placement fails if both vectors are collinear (which simply means they are on the same line).

By enabling this flag ezEdits tries to circumvent that case by perturbing the secondary direction by a small amount.

***
