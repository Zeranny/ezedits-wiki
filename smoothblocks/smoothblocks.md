# Smoothblocks

Generate, place shapes, and perform edits using shaping blocks like slabs, stairs, snow layers, water levels, etc.

### Currently supported commands are:

[Placement Commands](../commands/placement/)

[Spline Commands](../commands/spline/)

### How to use

Add the <mark style="color:orange;">**`-w <profile>`**</mark> flag when using one of the supported(!) commands.

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

Comparing generating a noise spline with and without the SlabsOnly profile.

* `//ezspline noise ##grayscale 20`

- `//ezspline noise ##grayscale 20`` `<mark style="color:orange;">**`-w SlabsOnly`**</mark>

![](../.gitbook/assets/Smoothblocks_example3.gif)



Comparing pasting a rotated mushroom schematic with and without the SlabsOnly profile.

* `//ezplace Clipboard Aim`
* `//ezplace Clipboard Aim`` `<mark style="color:orange;">**`-w SlabsOnly`**</mark>

![](../.gitbook/assets/Smoothblocks_example5.gif)

</details>

### Profiles

There are different smoothblocks profiles. One may, for example, use only slabs, the other may use stairs and slabs, and yet another may also use stairs and slabs but with different orientations. We hardcoded each preset to achieve a certain result. Each preset uses a specific subset of shaping blocks. We named each preset by which shaping blocks they use. Depending on their complexity, some may take longer to run than others.

<figure><img src="../.gitbook/assets/Smoothblocks_example6.png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:blue;">Examples</mark></summary>

Comparing <mark style="color:blue;">**`//ezspline 3d ch smooth_sandstone -w <profile>`**</mark>

No smoothblocks\
![](../.gitbook/assets/Smoothblocks_example11.png)\


-w Slabs\
![](../.gitbook/assets/Smoothblocks_example10.png)\


-w SlabsAndStairs\
![](../.gitbook/assets/Smoothblocks_example9.png)\


-w SlabsAndStairs2D\
![](../.gitbook/assets/Smoothblocks_example8.png)\


-w Layers\
![](../.gitbook/assets/Smoothblocks_example7.png)

</details>

### Materials

By default, the <mark style="color:orange;">**closest color**</mark> shaping block to the specified [pattern](https://worldedit.enginehub.org/en/latest/usage/general/patterns/), [palette](../palettes/palettes-explained.md) or block that would've been placed instead.

<details>

<summary><mark style="color:blue;">Example</mark></summary>

If you generate a [Structure](../commands/placement/available-structures.md) (e.g. an [Icosphere](../commands/placement/available-structures.md#icosphere-ic)) using the pattern <mark style="color:blue;">**`clay`**</mark> using the <mark style="color:blue;">**`SlabsOnly`**</mark> smoothblocks profile. Then, since there is no clay slab, it will use the slab variant that is **closest in colour** (determined using the default minecraft textures), which for clay would be a stone slab.

![](../.gitbook/assets/Smoothblocks_example1.png)

</details>

You may also <mark style="color:orange;">**override**</mark> the material of each shaping block variant, by setting the material yourself, e.g.: <mark style="color:orange;">**`-w SlabsOnly(Slab:acacia)`**</mark>
