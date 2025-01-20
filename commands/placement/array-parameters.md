# Array Parameters

[`//ezarray`](./#overview) and [`//ezbrush array`](./#overview) place multiple shapes along a path. The following parameters apply to these commands:

***

### Distance: <mark style="color:orange;">`-g <gap>`</mark>  <a href="#distance-g" id="distance-g"></a>

Control how close all placements are by defining the gap distance between each placement.

Defaults to `0`. Meaning, in a straight line each placement comes right after another with no gap.

Positive values will increase that distance and place fewer structures in total.\
Negative values cause the placements to overlap.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezarray Clipboard`` `**`-g <gap>`** (with the clipboard being a default vanilla oak tree for no particular reason)

`//ezar Cl`` `**`-g 0`** : (default value, placements are right next to each other)

<img src="../../.gitbook/assets/ArrayGap_example1.png" alt="" data-size="original">

`//ezar Cl`` `**`-g 10`** : (placements are now further apart)

<img src="../../.gitbook/assets/ArrayGap_example2.png" alt="" data-size="original">

`//ezar Cl`` `**`-g -3`** (negative values cause placements to overlap)

<img src="../../.gitbook/assets/ArrayGap_example3.png" alt="" data-size="original">

</details>

***

### Progressive Scaling: <mark style="color:orange;">`-q <radii>`</mark>  <a href="#progressive-scaling-q" id="progressive-scaling-q"></a>

Similar to [Random Scaling](placement-parameters.md#random-scaling-o), this modifier allows scaling of the placements using relative values, e.g. 1 keeps the scale as is, 2 doubles the size, and 0.5 halfs the size.

The scaling factors are defined as a progression along the spline. This means you may specify as many comma-separated scaling factors as you like, and the spline path will smoothly interpolate through all entries.

The syntax is the same as [#radius-progression-less-than-radii-greater-than](../spline/common-parameters.md#radii "mention").

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezarray Clipboard`` `**`-q <radii>`**

`//ezar Cl`` `**`-q 1`**

(default value, no scaling applied)

<img src="../../.gitbook/assets/ArrayGap_example1.png" alt="" data-size="original">

`//ezar Cl`` `**`-q 0.3,3`**

(placements are down-scaled by a factor of 0.3 at the beginning of the path and slowly get bigger up to triple their original size towards the end of the spline path)

<img src="../../.gitbook/assets/ArrayScaling_example2.png" alt="" data-size="original">

`//ezar Cl`` `**`-q 1.5,0.5,5.0,2.0,0.2`**

(Tree is being scaled progressively through all given values throughout the spline path)

<img src="../../.gitbook/assets/ArrayScaling_example3.png" alt="" data-size="original">

`//ezar Cl`` `**`-q 1.5,0.5,5.0,2.0,0.2 -o 0.7,1.3`**

(Combining progressive scaling -q with [random scaling](placement-parameters.md#random-scaling-o) -o)

<img src="../../.gitbook/assets/ArrayScaling_example4.png" alt="" data-size="original">

</details>

***

### Path Parameters: <mark style="color:orange;">`-p <kbParameters>`</mark>  <a href="#path-parameters-p" id="path-parameters-p"></a>

Modifies how the path is created from the input (convex selection) points. See [#kochanek-bartel-parameters-p-less-than-kbparameters-greater-than](../spline/common-parameters.md#kb-parameters "mention")

***

### Spline orientation: <mark style="color:orange;">`-n <normalMode>`</mark>  <a href="#spline-orientation-n" id="spline-orientation-n"></a>

Modifies how the ORTHOGONAL option for the `<primary>` and `<secondary>` arguments behave. See [#spline-normal-mode-n-less-than-normalmode-greater-than](../spline/common-parameters.md#normal-mode "mention")

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

`//ezarray Clipboard Orthogonal Constant`**`-n <normalMode>`**

`//ezar Cl O C`` `**`-n CONSISTENT`**

(default value)

<img src="../../.gitbook/assets/OrthogonalAlignment_example1.png" alt="" data-size="original">

`//ezar Cl O C`` `**`-n UPRIGHT`**

(placements are not as tilted anymore)

<img src="../../.gitbook/assets/OrthogonalAlignment_example2.png" alt="" data-size="original">

</details>

***

### Snap placements to surfaces: <mark style="color:orange;">`-b`</mark>  <a href="#snap-to-surfaces-b" id="snap-to-surfaces-b"></a>

By default, structures are placed along the spline path that's induced by the input (convex selection) points. This flag moves the placement positions to the nearest surface block instead, in case the position on the path is in midair or submerged in blocks.

{% hint style="info" %}
By default the maximum search range is 96 blocks. The maximum search range can be set in the config. If no surface block is found within that range, the original position will be used instead.
{% endhint %}

<details>

<summary><mark style="color:blue;">Example</mark></summary>

GIF comparing

`//ezarray Clipboard` (placements are placed along path)

`//ezarray Clipboard`` `**`-b`** (placements positions moved to nearest surface block)

<img src="../../.gitbook/assets/ezgif.com-animated-gif-maker.gif" alt="" data-size="original">

</details>

***
