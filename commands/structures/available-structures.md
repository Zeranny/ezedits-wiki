# Available Structures

In the context of ezEdits, we call an arrangement of blocks in 3D space a "structure". Each of the above-mentioned commands requires the user to provide a `<structure>` argument.

Currently available structures are:

<details>

<summary><strong>Clipboard (Cl)</strong></summary>

A structure based on your current WorldEdit Clipboard (//copy).

Syntax: `Clipboard`

Abbr.: `Cl`

Options:

* **Format (F)**. Defaults to sponge.3 (or FAWE's fast if you're using FAWE)
* **Origin (O)**. Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* **PasteMethod (PM**). Defaults to FAST.
  * FAST (fast): Default unaltered pasting of clipboards
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.

- Example: `Clipboard(Origin:INHERENT,PasteMethod:SMOOTHED)` or `Cl(O:I,PM:smooth)`

</details>

<details>

<summary><strong>Schematic (Sc)</strong></summary>

A structure based on a schematic file.

Syntax: `Schematic(Filename:<name>,...)`

Abbr.: `Sc(N:<name>,...)`

Mandatory parameters:

* **Filename (N)**

Options:

* **Format (F)**. Defaults to sponge.3 (or FAWE's fast if you're using FAWE)
* **Origin (O)**. Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* **PasteMethod (PM**). Defaults to FAST.
  * FAST (fast): Default unaltered pasting of clipboards
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.

</details>

<details>

<summary><strong>Shape (Sh)</strong></summary>

An expression-based shape. EzEdits provides plenty of predefined ones. Material defined by a pattern.

Syntax: `Shape(Shape:<shape>,Pattern:<pattern>)`

Abbr.: `Sh(S:<shape>,P:<pattern>)`

Mandatory Parameters:

* **Shape (S)**. Well, defines the shape of the Shape structure. Additional parameters are given within the parenthesis after. Available shapes are:
  * Cone
  * Cuboid
  * Curl
  * Cylinder
  * Ellipsoid
  * Fur
  * Jellybean
  * Leaf
  * Lemon
  * Onion
  * Polygon(_Sides_)
  * Pyramid(_Sides_)
  * Supersphere(_Exponent_)
  * Tetrahedron
  * Torus(_Thickness_)
  * \=_\<expression>_
    * In addition to predefined shapes, you can also define your own shape with a WorldEdit expression.
    * For example, this expression will create spirals:\
      `Shape(S:=x+=sin(2*pi*y)/2;z+=cos(2*pi*y)/2;x*x+z*z<0.3^2`
* **Pattern (P)**. The pattern which the shape should be made of.
  * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a pattern that uses commas then you need to put your Pattern argument in quotes: E.g. `Sh(S:Cone,Pattern:`**`"dirt,diamond_block"`**`)`



</details>

<details>

<summary><strong>Expression (Ex)</strong></summary>

An expression-based shape. One expression defines both the shape and the texturing.

Syntax: `Expression(Expression:=<expression>,Palette:<palette>)`

Abbr.: `Ex(E:=<expression>,P:<palette>)`

Mandatory Parameters:

* **Expression (E)**. Input variables are `x`, `y`, and `z`, all between \[-1,1]. `x=0`,`y=0`,`z=0` is the origin of the structure.
  * If the expression f(x,y,z) evaluates as _f_≤_0_, 0 or negative, then the position will be air.
  * If it evaluates as _1>f>0_, between 0 and 1, then the according palette block is placed.&#x20;
  * Otherwise, any value 1 or larger will place the last palette block.
*   **Palette (P)**. The set of blocks of which the structure should be made of.

    * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a palette that uses commas then you need to put your Palette argument in quotes: E.g. `Ex(E:=y*.5+.5,Palette:`**`"##GlowOrange,-##GlowPurple"`**`)`



</details>

<details>

<summary><strong>TexturedShape (TS)</strong></summary>

An expression-based shape with an expression-based texturing. The Shape parameter defines its shape. The Palette and Texturing-Shape parameters define its material.

Syntax: `TexturedShape(Shape:<shape>,TexturingShape:<shape>,Palette:<palette>)`

Abbr.: `TS(S:<shape>,T:<shape>,P:<palette>)`

Mandatory Parameters:

* **Shape (S)**. See [Shape Structure](available-structures.md#shape-sh).
* **TexturingShape (T)**. Defines which parts of the shape are painted with which blocks of the palette. Accepts a shape, just like the Shape Parameter.
*   **Palette (P)**.  The set of blocks of which the shape should be made of.

    * Note: Commas `,` being part of the argument breaks the input parser. If you want to use a palette that uses commas then you need to put your Palette argument in quotes: E.g. `TS(S:Cone,T:=y*.5+.5;Palette:`**`"dirt,diamond_block"`**`)`



</details>

