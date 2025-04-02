# Advanced Spline Shapes

The following `//ezspline` subcommands feature three very powerful but more complex spline shapes with effectively limitless customizability.

***

#### ![](../../.gitbook/assets/SplinesNoise.png)

### `//ezspline` <mark style="color:orange;">`noise`</mark> <a href="#noise" id="noise"></a>

<details>

<summary><mark style="color:blue;">Noise Spline</mark></summary>

**`//ezsp noise`** <mark style="color:orange;">**`<palette>`**</mark> [**`<radii>`**](common-parameters.md#radii) <mark style="color:orange;">**`[noise]`**</mark> <mark style="color:orange;">**`[depth]`**</mark> [**`[-s <stretch>]`**](common-parameters.md#stretch-s-less-than-stretchfactor-greater-than) [**`[-t <angle>]`**](common-parameters.md#twist) [**`[-p <kbParameters>]`**](common-parameters.md#kb-parameters) [**`[-q <quality>]`**](common-parameters.md#quality) [**`[-n <normalMode>]`**](common-parameters.md#normal-mode) [**`[-h]`**](common-parameters.md#help-page)

Generates a noise-based spline along the selected positions.

* <mark style="color:orange;">**`<Palette>`**</mark>:
  * Specifies the blocks that the spline should be made out of.
* <mark style="color:orange;">**`[noise]`**</mark> (Default: "Perlin(Freq:2,z:0.5)"):
  * The noise that should be embedded along the spline path.
* <mark style="color:orange;">**`[depth]`**</mark> (Default: 0.7):
  * How deep the noise should cut into the cylinder-shaped spline. Depths approaching 0 approach the original cylinder-shaped spline, 0.5 means the noise may reach half the radius deep, and 1.0 means the full radius, reaching the center. Larger than 1.0 will result in a choppy look.
* <mark style="color:orange;">**`[-i <expression>]`**</mark> (Default: "`r=sqrt(x*x+y*y);t=(r-1)/d+1;f=r>1?1:(4*r*(r-1))^2;g=f*t+(1-f)*n;p=max((r-1)/min(d,1)+1,.001);(g>t)*p`"):
  * Advanced parameter for nerds. Ignore if this above looks scary.
  * This expression implements the functionality of the noise cutting into a cylinder at a certain relative `<depth>`. [Derivation](https://www.desmos.com/calculator/qw8fro1npf). If you _**really**_ want to, you can come up with a different expression here to get a different result. If you don't need custom noises just use `//ezspline expression` instead though.
  * Input parameters are _`x,y,z,n,d`_ whereby _`x,y,z`_ are assigned like in [//ezspline expression](advanced-spline-shapes.md#expression-spline), _`n`_ is the evaluation of the given `<noise>` at the coordinates _`x,y,z`_ and _`d`_ is the given `<depth>` parameter.
  * An alternative expression could be:
    * `r=sqrt(x*x+y*y);(r<1&&n>0.5)*max(n,0.01)`: If you only want the noise to be restricted to a cylinder shape

_The remaining arguments are outlined on the_ [_Common Parameters_](common-parameters.md) _subpage._

Example:

`//ezspline noise ##Grayscale 10`

<img src="../../.gitbook/assets/SplinesNoise.png" alt="" data-size="original">

</details>

<details>

<summary><mark style="color:blue;">Demos</mark></summary>

![](../../.gitbook/assets/SplinesNoise_example2.png)

Just a small, quick set of noise commands I threw together to show what the noise spline can do. \~eztaK\


`//ezspline noise -##Magma 5,25 Ce(F:1.5,fO:1,cR:sub,M:OR,U:-.6) 0.6 -t 90`

![](../../.gitbook/assets/SplinesNoise_example3.png)\


`//ezspline noise ##GrayWarm(3:11),251:8*15 25,10,25 Ce(F:1.6,fO:1,cD:r,cR:r,M:OR,L:-1.1,U:-.2) 0.4`

![](../../.gitbook/assets/SplinesNoise_example4.png)\


`//ezspline noise ~PanesOnly(Palette:light_gray_stained_glass) 20,15,25 Ce(f:1.4,z:.3,m:or,l:-1,u:-0.5) 3 -t 600 -i t=0.2;r=sqrt(x*x+y*y);m=1-abs(2*r-t-1)/abs(t-1);n<m&&r<1`

![](../../.gitbook/assets/SplinesNoise_example5.png)\


//ezspline noise ##Brown 20,12 Ce(f:4,cr:sub,cj:.8,m:or,u:-.5,l:-1.3) 0.2 -s 6 -t 20

![](../../.gitbook/assets/SplinesNoise_example6.png)\


`//ezspline noise -##GlowBlue(6:16) 20,12 Ce(f:2,cr:sub,m:or,u:-.55,l:-0.551,z:0.1) 0.9 -t 200`

![](../../.gitbook/assets/SplinesNoise_example7.png)\


`//ezspline noise ~SlabsOnly(Palette:"##GrayCold(4:11),waxed_weathered_cut_copper") 20 Ce(f:1.5,cr:sub,m:or,u:-0.85,l:-.5,y:0.3) -n UPRIGHT -i (x*x+n+y*y<1&&y<0)*(y+0.97)`

![](../../.gitbook/assets/SplinesNoise_example8.png)

</details>

***

#### ![](../../.gitbook/assets/SplinesExpression.png)

### `//ezspline` <mark style="color:orange;">`expression`</mark> <a href="#expression" id="expression"></a>

<details>

<summary><mark style="color:blue;">Expression Spline</mark></summary>

**`//ezsp expression`** <mark style="color:orange;">**`<palette>`**</mark> [**`<radii>`**](common-parameters.md#radii)[**`[-s <stretch>]`**](common-parameters.md#stretch-s-less-than-stretchfactor-greater-than) [**`[-t <angle>]`**](common-parameters.md#twist) [**`[-p <kbParameters>]`**](common-parameters.md#kb-parameters) [**`[-q <quality>]`**](common-parameters.md#quality) [**`[-n <normalMode>]`**](common-parameters.md#normal-mode) <mark style="color:orange;">**`[-z] [-o]`**</mark> [**`[-h]`**](common-parameters.md#help-page) <mark style="color:orange;">**`<expression...>`**</mark>

Generates a spline shaped by the given WorldEdit expression along the selected positions.

* <mark style="color:orange;">**`<Palette>`**</mark>:
  * Specifies the block palette.
* <mark style="color:orange;">**`[-z]`**</mark>:
  * Without setting this flag, the domain of the z-axis is 0 to the length of the spline divided by the radius. You may set this flag to normalize the z-Axis, that runs along the path of the spline, to the \[-1,1] domain.
* <mark style="color:orange;">**`[-o]`**</mark>:
  * By default, expression output maps >0..1 to the palette. Use this flag to instead map the output to whole numbers.
* <mark style="color:orange;">**`<expression...>`**</mark>:
  * [A WorldEdit expression](https://worldedit.enginehub.org/en/latest/usage/other/expressions/). Input variables are
    * -1 ≤ _`x`_ ≤ 1
    * -1 ≤ _`y`_ ≤ 1
    * 0 ≤ _`z`_ ≤ L, whereby L is the length of the spline divided by its radius.
    * or -1 ≤ _`z`_ ≤ 1, if you're using the `-z` flag.
  * Output is either a normalized palette index (0,1] or if using the -o flag (0,P] whereby P is the number of blocks in the palette. Note that <=0 means not placing any block.

_The remaining arguments are outlined on the_ [_Common Parameters_](common-parameters.md) _subpage._

Example:

`//ezspline expression clay 10 -t 90 R=0.2;r=0.1;w=0.7;s=0.5;sqrt((abs(x)-w)^2+y^2)<R||sqrt(((z+1)%s-r)^2+y^2)<r&&abs(x)<w`

Expression by [imhols](https://twitter.com/imhols1)

<img src="../../.gitbook/assets/SplinesExpression.png" alt="" data-size="original">

</details>

***

#### ![](../../.gitbook/assets/SplinesStructure_example1.png)

### `//ezspline` <mark style="color:orange;">`structure`</mark> <a href="#structure" id="structure"></a>

<details>

<summary><mark style="color:blue;">Structure Spline</mark></summary>

**`//ezsp structure`** <mark style="color:orange;">**`<structure>`**</mark> [**`[radii]`**](common-parameters.md#radii)[**`[-s <stretch>]`**](common-parameters.md#stretch-s-less-than-stretchfactor-greater-than) [**`[-t <angle>]`**](common-parameters.md#twist) [**`[-p <kbParameters>]`**](common-parameters.md#kb-parameters) [**`[-q <quality>]`**](common-parameters.md#quality) [**`[-n <normalMode>]`**](common-parameters.md#normal-mode) <mark style="color:orange;">**`[-z]`**</mark> [**`[-h]`**](common-parameters.md#help-page)

Embeds a structure along the path defined by the selected convex region.

* <mark style="color:orange;">**`<structure>`**</mark>:
  * The shape/clipboard/schematic to embed along the path. See [available-structures.md](../placement/available-structures.md "mention").
* <mark style="color:orange;">**`[-z]`**</mark>:
  * Normalizes the Z-Axis, which results in exactly one structure being stretched out throughout the entire length of the path.

The structure will be placed in its Z-direction facing along the path. Multiple instances will be repeated one after another as often as its bounding box fits, unless you use `-z`, in which case one instance of the structure will be stretched across the whole length of the path.

Specifically for `//ezsp structure`, if the [`[radii]`](common-parameters.md#radii) argument is left out, we will automatically calculate the radius at which the structure is generated at its original/inherent size.

_The remaining arguments are outlined on the_ [_Common Parameters_](common-parameters.md) _subpage._

**Examples**:

`//ezsp structure TS(P:##GlowPurple,S:Heart,T:=(z+y)*.4+.5) 12`

<img src="../../.gitbook/assets/SplinesStructure_example1.png" alt="" data-size="original">

</details>

***
