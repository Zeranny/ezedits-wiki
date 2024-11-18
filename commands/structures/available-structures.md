# Available Structures

In the context of ezEdits, we call an arrangement of blocks in 3D space a "structure". Each of the above-mentioned commands requires the user to provide a `<structure>` argument.

Currently available structures are:

<details>

<summary><strong>Clipboard (C)</strong></summary>

A structure based on your current WorldEdit Clipboard.

Options:

* Origin (O). Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* PasteMethod (PM). Defaults to FAST.
  * FAST (fast): Default unaltered pasting of clipboards
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched onto the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.
* Example: `Clipboard(Origin:INHERENT,PasteMethod:SMOOTHED)` or `C(O:I,PM:smooth)`

</details>

<details>

<summary><strong>Schematic (Sc)</strong></summary>

A structure based on a schematic file.

Options:

* Filename (N) (mandatory parameter)
* Format (F)
* Origin (O). Defaults to INHERENT.
  * INHERENT (I) will use the position it was copied at
  * CENTER (C) will use the geometric center of the clipboard
* PasteMethod (PM). Defaults to FAST.
  * FAST (fast): Default unaltered pasting of clipboards
  * SMOOTHED (smooth): Applies interpolation when the placement cannot be matched into the world grid, e.g. when placing with a 45° rotated orientation. Has a slightly more smoothed look to it, which may preferred for freely rotated placements.

</details>

<details>

<summary><strong>Shape(Pattern:&#x3C;pattern>,Shape:&#x3C;shape>) (S(P:&#x3C;pattern>,S:&#x3C;shape>))</strong></summary>

An expression-based shape. EzEdits provides plenty of predefined ones. Material defined by a pattern.

Options:

### Shape (S)

**Current shapes**

_Additional parameters are given within the parenthesis after a shape._

* bean
* cube
* curl
* cylinder
* ellipsoid
* fur
* leaf
* lemon
* onion
* polygon(_Sides_)
* pyramid(_Sides_)
* spike
* supersphere(_Exponent_)
* tetrahedron
* torus(_Thickness_)

In addition to these, you can also define your own shape with a WorldEdit expression

**`Expression;<expression>`** or **`Expr;<expression>`**

For example, this expression will create spirals:\
`//ezsc expr;x+=sin(2*pi*y)/2;z+=cos(2*pi*y)/2;x*x+z*z<0.3^`

### Pattern (P)



</details>

<details>

<summary><strong>TexturedShape (TS)</strong></summary>

An expression-based shape with an expression-based texturing. Material defined the Texturing-Shape and a Palette.

Options:

* Shape (S)
* TexturingShape (T)
* Palette (P)

</details>
