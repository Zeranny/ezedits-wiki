# Available Structures

In the context of ezEdits, we call an arrangement of blocks in 3D space a "structure". Each placement command requires the user to provide a `<structure>` argument.

Currently available structures are:

<details>

<summary><mark style="color:blue;"><strong>Clipboard (Cl)</strong></mark></summary>

A structure based on your current WorldEdit Clipboard (//copy).

Syntax: <mark style="color:orange;">`Clipboard`</mark>

Abbr.: <mark style="color:orange;">`Cl`</mark>

Options:

* <mark style="color:blue;">**`Origin`**</mark><mark style="color:blue;">**&#x20;**</mark><mark style="color:blue;">**(O)**</mark>. Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* <mark style="color:blue;">**`PasteMethod`**</mark><mark style="color:blue;">**&#x20;**</mark><mark style="color:blue;">**(PM**</mark><mark style="color:blue;">)</mark>. Defaults to FAST. See [#comparison-between-fast-and-smooth-pastemethod](available-structures.md#comparison-between-fast-and-smooth-pastemethod "mention")
  * FAST (fast): Default unaltered pasting of clipboards, like //paste
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.
  * See [#comparison-between-fast-and-smooth-pastemethod](available-structures.md#comparison-between-fast-and-smooth-pastemethod "mention")

- Example: <mark style="color:orange;">`Clipboard(Origin:INHERENT,PasteMethod:SMOOTHED)`</mark> <mark style="color:orange;">or</mark> <mark style="color:orange;">`Cl(O:I,PM:smooth)`</mark>

</details>

<details>

<summary><mark style="color:blue;"><strong>Schematic (Sc)</strong></mark></summary>

A structure based on a schematic file.

Syntax: <mark style="color:orange;">`Schematic(Filename:<name>,...)`</mark>

Abbr.: <mark style="color:orange;">`Sc(N:<name>,...)`</mark>

Mandatory parameters:

* <mark style="color:orange;">**`Filename`**</mark> **(**<mark style="color:orange;">**`N`**</mark>**)**. A regex pattern for specifying all filenames of the schematics you want to place.
  * For example, if you type in `Sc(N:tree_.*)` we will fetch all schematic files that match the regex `tree.*,` e.g. `tree_1`, `tree_2`, `tree_3` etc.
  * In case you use FAWE's per-player-schematics path system, in which schematics are separated into folders named after each player's UUID, you can use the shortcut `%p` to denote your own UUID and access your folder through e.g. `%p/your_schematic.schem`

Options:

* <mark style="color:blue;">**`Format`**</mark> **(**<mark style="color:blue;">**`F`**</mark>**)**. Format of the schematic file. Defaults to <mark style="color:blue;">`sponge.3`</mark> (or FAWE's fast if you're using FAWE). The default value should work for the majority of cases.
* <mark style="color:blue;">**`Origin`**</mark> **(**<mark style="color:blue;">**`O`**</mark>**)**. Defaults to <mark style="color:blue;">`INHERENT`</mark>.
  * INHERENT (I) will use the position it was copied at.
  * CENTER (C) will use the center of the clipboard's region as the origin instead.
* <mark style="color:blue;">**`PasteMethod`**</mark> **(**<mark style="color:blue;">**`PM`**</mark>). Defaults to <mark style="color:blue;">`FAST`</mark>.
  * FAST (fast): Default unaltered pasting of clipboards, like //paste
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.
  * See [#comparison-between-fast-and-smooth-pastemethod](available-structures.md#comparison-between-fast-and-smooth-pastemethod "mention")

</details>

<details>

<summary><mark style="color:blue;"><strong>Shape (Sh)</strong></mark></summary>

An expression-based shape. EzEdits provides plenty of predefined ones. Material defined by a pattern.

Syntax: <mark style="color:orange;">`Shape(Shape:<shape>,Pattern:<pattern>)`</mark>

Abbr.: <mark style="color:orange;">`Sh(S:<shape>,P:<pattern>)`</mark>

Mandatory Parameters:

* <mark style="color:orange;">**`Shape`**</mark> (<mark style="color:orange;">**`S`**</mark>). Well, defines the shape of the Shape structure. Additional parameters are given within the parenthesis after. Available shapes are:
  *   `Cone`

      ![](../../.gitbook/assets/StructuresShapesCone.png)
  *   `Crystal([Sides:<sides>],[Extrusion:<value>])`

      ![](../../.gitbook/assets/StructuresShapesCrystal.gif)
  *   `Cuboid`

      ![](../../.gitbook/assets/StructuresShapesCuboid.png)
  *   `Curl`

      ![](../../.gitbook/assets/StructuresShapesCurl.png)
  *   `Cylinder`

      ![](../../.gitbook/assets/StructuresShapesCylinder.png)
  *   `Ellipsoid`

      ![](../../.gitbook/assets/StructuresShapesEllipsoid.png)
  *   `Fur`

      ![](../../.gitbook/assets/StructuresShapesFur.png)
  *   `Heart`

      ![](../../.gitbook/assets/StructuresShapesHeart.png)
  *   `Jellybean`

      ![](../../.gitbook/assets/StructuresShapesJellybean.png)
  *   `Leaf`

      ![](../../.gitbook/assets/StructuresShapesLeaf.png)
  *   `Lemon`

      ![](../../.gitbook/assets/StructuresShapesLemon.png)
  *   `Onion`

      ![](../../.gitbook/assets/StructuresShapesOnion.png)
  *   `Polygon([Sides:<sides>])`

      ![](../../.gitbook/assets/StructuresShapesPolygon.gif)
  *   `Pyramid([Sides:<sides>])`

      ![](../../.gitbook/assets/StructuresShapesPyramid.gif)
  *   `Supersphere(Exponent:<exponent>)`

      ![](../../.gitbook/assets/StructuresShapesSupersphere.gif)
  *   `Tetrahedron`

      ![](../../.gitbook/assets/StructuresShapesTetrahedron.png)
  *   `Torus(Thickness:<value>)`

      ![](../../.gitbook/assets/StructuresShapesTorus.gif)
  * `=<expression>`
    * In addition to predefined shapes, you can also define your own shape with a WorldEdit expression.
    * For example, this expression will create spirals:\
      <mark style="color:blue;">`Shape(S:`</mark><mark style="color:blue;">**`=x+=sin(2*pi*y)/2;z+=cos(2*pi*y)/2;x*x+z*z<0.3^2`**</mark><mark style="color:blue;">`,P:clay)`</mark>
* <mark style="color:orange;">**`Pattern`**</mark> (<mark style="color:orange;">**`P`**</mark>). The pattern which the shape should be made of.
  * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a pattern that uses commas then you need to put your Pattern argument in quotes: E.g. <mark style="color:blue;">`Sh(S:Cone,Pattern:`</mark><mark style="color:blue;">**`"dirt,diamond_block"`**</mark><mark style="color:blue;">`)`</mark>

</details>

<details>

<summary><mark style="color:blue;"><strong>Expression (Ex)</strong></mark></summary>

An expression-based shape. One expression defines both the shape and the texturing.

Syntax: <mark style="color:orange;">`Expression(Expression:=<expression>,Palette:<palette>)`</mark>

Abbr.: <mark style="color:orange;">`Ex(E:=<expression>,P:<palette>)`</mark>

Mandatory Parameters:

* <mark style="color:orange;">**`Expression`**</mark> **(**<mark style="color:orange;">**`E`**</mark>**)**. Input variables are `x`, `y`, `z`, all between \[-1,1], and `seed`.
  * `x=0`,`y=0`,`z=0` is the origin of the structure.
  * If the expression f(x,y,z) evaluates as _f_≤_0_, 0 or negative, then the position will be air.
  * If it evaluates as _1>f>0_, between 0 and 1, then the according palette block is placed.
  * Otherwise, any value 1 or larger will place the last palette block.
  * `seed` is a random integer between 0 and 2147483647, different for each placement (but most importantly constant within a single placement)
* <mark style="color:orange;">**`Palette`**</mark> **(**<mark style="color:orange;">**`P`**</mark>**)**. The set of blocks of which the structure should be made of.
  * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a palette that uses commas then you need to put your Palette argument in quotes: E.g. <mark style="color:blue;">`Ex(E:=y*.5+.5,Palette:`</mark><mark style="color:blue;">**`"##GlowOrange,-##GlowPurple"`**</mark><mark style="color:blue;">`)`</mark>

Example:

<mark style="color:blue;">`Ex(E:"=x*x+y*y+z*z<perlin(seed,x,y,z,1,1,.5)",P:clay)`</mark>

<img src="../../.gitbook/assets/StructuresExpression_example1.gif" alt="" data-size="original">

</details>

<details>

<summary><mark style="color:blue;"><strong>TexturedShape (TS)</strong></mark></summary>

An expression-based shape with an expression-based texturing. The Shape parameter defines its shape. The Palette and Texturing-Shape parameters define its material.

Syntax: <mark style="color:orange;">`TexturedShape(Shape:<shape>,TexturingShape:<shape>,Palette:<palette>)`</mark>

Abbr.: <mark style="color:orange;">`TS(S:<shape>,T:<shape>,P:<palette>)`</mark>

Mandatory Parameters:

* <mark style="color:orange;">**`Shape`**</mark> **(**<mark style="color:orange;">**`S`**</mark>**)**. See [Shape Structure](available-structures.md#shape-sh).
* <mark style="color:orange;">**`TexturingShape`**</mark> **(**<mark style="color:orange;">**`T`**</mark>**)**. Defines which parts of the shape are painted with which blocks of the palette. Accepts a shape, just like the Shape Parameter.
* <mark style="color:orange;">**`Palette`**</mark> **(**<mark style="color:orange;">**`P`**</mark>**)**<mark style="color:orange;">.</mark> The set of blocks of which the shape should be made of.
  * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a palette that uses commas then you need to put your Palette argument in quotes: E.g. <mark style="color:blue;">`TS(S:Cone,T:=y*.5+.5;Palette:`</mark><mark style="color:blue;">**`"dirt,diamond_block"`**</mark><mark style="color:blue;">`)`</mark>

</details>

<details>

<summary><mark style="color:blue;"><strong>Icosphere (Ic)</strong></mark></summary>

(<mark style="color:red;">**`!`**</mark>) Only available if [Arceon](https://www.patreon.com/c/arcaniax/home) v0.4.9 or higher is running on your server.

A deformed icosphere. Popularised in the building community under the [Arceon Boulder](https://github.com/Brennian/Arceon-1.14/wiki/Brushes#boulder-brush).

Syntax: <mark style="color:orange;">`Icosphere(Pattern:<pattern>,Randomness:<value>,Subdivisions:<value>)`</mark>

Abbr.: <mark style="color:orange;">`Ic(P:<pattern>,R:<value>,S:<value>)`</mark>

Mandatory Parameters:

* <mark style="color:orange;">**`Pattern`**</mark> (<mark style="color:orange;">**`P`**</mark>). The pattern which the shape should be made of.
  * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a pattern that uses commas then you need to put your Pattern argument in quotes: E.g. <mark style="color:blue;">`Ic(P:`</mark><mark style="color:blue;">**`"dirt,diamond_block"`**</mark><mark style="color:blue;">`)`</mark>

Optional Parameters:

* <mark style="color:blue;">**`Randomness`**</mark> **(**<mark style="color:blue;">**`R`**</mark>**)**. Defines how strongly the icosphere is deformed.
  * Defaults to <mark style="color:blue;">`0.5`</mark>.
  * Accepts a value between 0 and 1:
    * 0 resulting in a perfectly uniform icosphere,
    * ![](../../.gitbook/assets/StructuresIcosphere_example1.png)
    * 0.5 results in a fairly deformed boulder shape.
    * ![](../../.gitbook/assets/StructuresIcosphere_example2.gif)
    * 1 resulting in a maximally deformed boulder shape.
    * ![](../../.gitbook/assets/StructuresIcosphere_example3.gif)
    * All above examples at Subdivisions=0.
* <mark style="color:blue;">**`Subdivisions`**</mark> **(**<mark style="color:blue;">**`S`**</mark>**)**. Determines the amount of polygons used.
  * Defaults to <mark style="color:blue;">`0`</mark>.
  * Choose between 0, 1, 2, 3, 4:
    * 0 results in the most low-poly look
    * ![](../../.gitbook/assets/StructuresIcosphere_example2.gif)
    * 1
    * ![](../../.gitbook/assets/StructuresIcosphere_example4.gif)
    * 2
    * ![](../../.gitbook/assets/StructuresIcosphere_example5.gif)
    * 3
    * ![](../../.gitbook/assets/StructuresIcosphere_example6.gif)
    * 4 results in many polygons used, but also limits the amount of randomness, resulting in a pretty spherical look even with maximum randomness as you can already see with 3 subdivisions.
  * (<mark style="color:red;">**`!`**</mark>) Large number of subdivisions have a large performance impact.

Remember: All of the given examples were rendered with equal dimensions across all three axes. Use the [dimensions parameter](placement-parameters.md#dimensions-s) to stretch and squish along the three axes.

</details>

***

### Comparison between FAST and SMOOTH PasteMethod:

[Clipboard](available-structures.md#clipboard-cl) and [Schematic](available-structures.md#schematic-sc) both have the PasteMethod parameter. Here's a comparison of both modes:

<details>

<summary><mark style="color:blue;">Comparison</mark></summary>

Let's say this is our clipboard or our schematic:

<img src="../../.gitbook/assets/StructuresPasteMethod_example1.png" alt="" data-size="original">

Here's how it would look pasted at an odd angle when using

* `PasteMethod:FAST`

<img src="../../.gitbook/assets/StructuresPasteMethod_example2.png" alt="" data-size="original">

* vs `PasteMethod:SMOOTHED`

<img src="../../.gitbook/assets/StructuresPasteMethod_example3.png" alt="" data-size="original">

Or when pasted a significantly larger size:

* `PasteMethod:FAST`

<img src="../../.gitbook/assets/StructuresPasteMethod_example4.png" alt="" data-size="original">

* vs `PasteMethod:SMOOTHED`

<img src="../../.gitbook/assets/StructuresPasteMethod_example5.png" alt="" data-size="original">

There's also an additional parameter to the SMOOTHED PasteMethod: The `FillBias`. It allows you to specify whether the tool should try to place _more_ blocks or try to place _less_ blocks. This could be particularly helpful for e.g., particularly thin structures.

Let's say this curved one-block thick sheet is our clipboard/schematic now.

<img src="../../.gitbook/assets/StructuresPasteMethod_example6.png" alt="" data-size="original">

Here's how _it_ would look pasted **at an odd angle** when using

* `//paste` or`PasteMethod:FAST`

<img src="../../.gitbook/assets/StructuresPasteMethod_example7.png" alt="" data-size="original">

* compared to `PasteMethod:SMOOTHED`

<img src="../../.gitbook/assets/StructuresPasteMethod_example9.png" alt="" data-size="original">

* compared to `PasteMethod:SMOOTHED,FillBias:3` (default FillBias is 1.0)

<img src="../../.gitbook/assets/StructuresPasteMethod_example8.png" alt="" data-size="original">

* compared to a GIF going from `Fillbias:`**`0.25`** up to `Fillbias:`**`3.0`**

<img src="../../.gitbook/assets/StructuresPasteMethod_example10.gif" alt="" data-size="original">

</details>
