# Primary+Secondary Alignment

Alignment defines the orientation at which the structure is placed.

Every structure has an intrinsic "up" direction and an intrinsic "forward" direction. By default, structures are placed with their up direction facing, well, up (+y), and with their forward direction facing forward (+x) ("default" meaning setting both to just `Constant`).

The most important thing is now: You can define how a structure is placed by defining where its up direction should face and where its forward direction should face (aka. aligning its internal coordinate system).

We let the user define the alignment using two directions:

> The `<primary>` direction will always align the structures internal +y direction.

> The `<secondary>` direction together with the primary direction imply the structures +x direction.



The primary and secondary can be set to:

<table data-view="cards" data-full-width="false"><thead><tr><th>Name</th><th>Abbreviation</th><th>Description</th></tr></thead><tbody><tr><td><strong><code>Constant</code></strong></td><td><strong><code>C</code></strong></td><td>Explicitly set a constant direction for all placements.</td></tr><tr><td><strong><code>Random</code></strong></td><td><strong><code>R</code></strong></td><td>Random direction for each placement.</td></tr><tr><td><strong><code>Aim</code></strong></td><td><strong><code>A</code></strong></td><td>Your player aim direction.</td></tr><tr><td><strong><code>PlayerRelative</code></strong></td><td><strong><code>P</code></strong></td><td>The direction from the placement's position towards the current player position.</td></tr><tr><td><strong><code>SurfaceNormal</code></strong></td><td><strong><code>S</code></strong></td><td>The approximate surface-normal in the region of the placement's position.</td></tr><tr><td><strong><code>ViewDiff</code></strong></td><td><strong><code>V</code></strong></td><td>Define a direction using two clicks. Exclusively for brushes.</td></tr><tr><td><strong><code>Tangential</code></strong></td><td><strong><code>T</code></strong></td><td>The direction tangential to the path. Exclusively for arrays.</td></tr><tr><td><strong><code>Orthogonal</code></strong></td><td><strong><code>O</code></strong></td><td>The direction orthogonal to the path. Exclusively for arrays.</td></tr></tbody></table>

Note: If you use Constant(Direction:\<direction>) without specifying a \<direction>, then:

* the default direction is **+y** if you're setting the `<primary>`.
* the default direction is **+x** if you're setting the `<secondary>`.

<details>

<summary>More in-depth explanation using examples:</summary>

Let's say this is our build that we want to place:

![](../../.gitbook/assets/2024-11-18\_03.12.06.png)

For reference, the red beam is facing towards positive x (east), the blue beam is facing towards positive z (south), and the green beam is facing towards positive y (up).

Let's go through a few examples and try to understand what is happening:

Let's set the `<primary>` to `up` (and the `<secondary>` to `east`):

![](../../.gitbook/assets/2024-11-18\_03.12.06.png)

Our shape is pasted exactly in the same orientation as we copied it.

Consider the following two examples:

1. The `<primary>` is set to `south` and the `<secondary>` to `east`:

![](../../.gitbook/assets/2024-11-18\_03.12.34.png)

2. The `<primary>` is set to the vector `(0,1,1)`, i.e. the direction going diagonally up and south, and the `<secondary>` to `east`:&#x20;

![](../../.gitbook/assets/2024-11-18\_03.19.20.png)

Notice how, what was originally "up" when we copied it, i.e. the green beam in our case, is facing the direction that we set the primary to.

Here's an interesting example:

The `<primary>` is set to the vector `(1,1,0)`, i.e. the direction going diagonally up and **east**, while the `<secondary>` is set to `east`:

![](../../.gitbook/assets/2024-11-18\_03.21.06.png)

The green beam is correctly pointing along the primary direction. But notice how, even though the secondary is set to east, the red beam is not pointing east (but diagonally down and east).

Imagine if it were pointing east though: Then the green and red beam would be at a 45° angle instead of the original 90° angle. Our structure would be deformed/bent/sheared.

What we decided to implement instead, is that while we align the structure's +y direction with the given primary direction, instead of aligning the structure's +x direction with the given secondary direction, we choose the direction that is most similar to the given secondary direction and that is still perpendicular to the primary.

For a set primary direction here's a small gif that shows the remaining possible secondary directions that keep everything perpendicular:

![](<../../.gitbook/assets/2024-11-18 04-25-47.gif>)



</details>



#### Examples and GIFs:

<details>

<summary>Constant</summary>

Explicitly set a constant direction for all placements.

There are various ways to define a direction. From using the axes, using cardinal directions or using vector notation, or player relative directions like forward, left, right, etc. You can also add directions together using the '+' sign, like `east+south`&#x20;

`//ezsc Clipboard C(v:(0,2,0)) C(v:east)`

![](../../.gitbook/assets/2024-11-18\_04.33.26.png)

`//ezsc Clipboard C(v:(-1,2,-1)) C(v:east)`

![](<../../.gitbook/assets/2024-11-18\_04.33.57 (1).png>)

`//ezsc Clipboard C(v:(-1,2,-1)) C(v:-aim)`

![](<../../.gitbook/assets/2024-11-18\_04.36.35 (1).png>)

</details>

<details>

<summary>Random</summary>

Random direction for each placement.



</details>


