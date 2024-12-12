# Scatter Parameters

[`//ezscatter`](./#ezscatter) and [`//ezbrush scatter`](./#ezbrush-scatter) place multiple structures within a region. The positions that these commands choose can be customized with the parameters described on this page.

`scatter` first extracts all surface blocks (all non-air blocks touching air) from a region of your choice. You can filter out surfaces that do not match certain conditions using `-d <directions>` & `-e <threshold>`, and `-m <mask>`. On the remaining surfaces, a placement position distribution according to the given density `-n <density>` and uniformity  `-u <iterations>` is calculated and structures are placed.&#x20;

***

### Scatter Region: <mark style="color:orange;">`-h <region>`</mark>

Determines the region in which the placement positions are scattered.

* Defaults to:
  * Your currently selected region for `//ezscatter`, or
  * a 40x40x40 cuboid region around the clicked position for `//ezbrush scatter`.

Available options:

* _Box_ (_B_): A cuboid region. (Named Box to have single-letter abbreviations)
* _Ellipsoid_ (_E_): An ellipsoidal region
* _Cylinder_ (_C_): A cylindrical region
* _Saved_ (_S_): A selection saved using //ezsel save.
* _Active_ (_A_): Your currently selected region.

The dimensions of the first three can be set using the _Dimensions_ (_D_) parameter, e.g. `Box(Dimensions:"60,30,60")`  or `B(D:"60,30,60")`. It defaults to `"40,40,40"`.

By default, all regions are centered around the player position (for `//ezsc`) or the clicked position (for `//ezbr sc`). You may define an offset using the _Offset_ (_O_) parameter to move the center of the region relative to its target position.

> #### Examples:
>
> Ex. command: `//ezbrush scatter Clipboard`` `**`-h <region>`**
>
> Gif going through
>
> * `-h Box`
> * `-h Cylinder`
> * `-h Saved(Name:$triangle)`
> * `-h Saved(Name:$triangle,Offset:(0,0,10))`&#x20;
>
> after using the brush once at the same position:
>
> ![](../../.gitbook/assets/ScatterRegion_example1.gif)
>
> Whereby `$triangle` is just some 3-point polyhedral selection I saved with //ezsel.
>
> Selection is visualised using pink wool for clarity (using the [-l flag](scatter-parameters.md#mask-cover-block-b-less-than-pattern-greater-than)).

***

### Directional Filter: <mark style="color:orange;">`-d <directions>`</mark> and <mark style="color:orange;">`-e <threshold>`</mark>

Enables filtering out placement positions on surfaces that are facing certain directions.

The `-d <directions>` parameter defines the list of cardinal directions (up, down, north, east, south, west) in which the surface, on which the placement positions points are placed at, must face. If a placement position does not satisfy this condition, no structure will be placed there.

The `-e <threshold>` parameter defines how much the surface normal at the placement position must align with any of the directions given by `-d`. The higher the value the stronger the filter.

`-d` has defaults to an empty list (nothing).

`-e` defaults to 0.5. Expected value range is -1 to 1.

> #### Example
>
> Ex. command: `//ezsc Clipboard S C`` `**`-d <directions> -e <threshold>`** (with the clipboard being a default vanilla oak tree for no particular reason)
>
>
>
> **`-d west,up`** (scatter points must be on a surface facing either west or up)![](../../.gitbook/assets/ScatterDirectionalFilter_example.png)
>
>
>
> **`-d up -e <threshold>`** (scatter points must be on a surface facing roughly upwards)
>
> GIF
>
> * starts at **`-e -1.0`** (weakest filter threshold, all shapes are placed)
> * pauses at **`-e 0.0`** (half of all directions are filtered out)
> * and ends at **`-e 1.0`** (strongest filter threshold, no shapes are placed anymore).
>
> ![](../../.gitbook/assets/ScatterDirectionalFilter_demo.gif)

***

### Mask Filter: <mark style="color:orange;">`-m <mask>`</mark>

Enables filtering out placement positions that do not match a mask given by `-m <mask>`. Placement positions must satisfy the mask for a structure to be placed.

> #### Examples:
>
> Ex. command: `//ezsc Clipboard S C`` `**`-m <mask>`** (with the clipboard being a default vanilla oak tree for no particular reason)
>
>
>
> GIF going through
>
> * **`-m red`** (only placement positions on red wool blocks are chosen)
> * **`-m !red`** (only placements positions on anything but red wool blocks are chosen)
> * **`-m =y>95`** (only placement positions which are above y>95 are chosen)
> * and the region before the execution of the command.
>
> ![](../../.gitbook/assets/ScatterMaskFilter_demo.gif)

***

### Density: <mark style="color:orange;">`-n <density>`</mark>

Determines how many placements are placed, by specifying a density percentage.

The density value is a percentage. It determines what percentage of surface blocks a structure is placed on. Specifically, it determines the percentage of positions _after_ the directional filter and the mask filter have been applied.

To be overly specific: Let _N_ be the remaining surface blocks (e.g. the result of `//count [!air]&[~air]` if neither filter is used), then the final amount of structures placed is equal to _N \* density / 100_.

Note: Percent sign is optional. `0.5` is equal to `0.5%`.

> #### Examples:
>
> Ex. command: **`//ezsc Clipboard C C -n <density>`** (with the clipboard being a default vanilla oak tree for no particular reason)
>
>
>
> **`-n 2%`** (default) or **`-n 2`** ('%'-sign is optional):
>
> ![](../../.gitbook/assets/ScatterDensity_example1.png)
>
>
>
> **`-n 0.5%`**
>
> &#x20;![](../../.gitbook/assets/ScatterDensity_example2.png)
>
>
>
> **`-n 5%`**
>
> ![](../../.gitbook/assets/ScatterDensity_example3.png)

{% hint style="info" %}
The density specifies the percentage of _**remaining**_ surface blocks on which a placement is placed.&#x20;

If for example, you use the mask filter to restrict the placement to a specific block which only rarely occurs within your selection, e.g. with the following region and `-m sea_lantern`,

![](../../.gitbook/assets/2024-12-10_13.54.52.png)

Then `-n 2%`, the default density, implies that from all sea\_lantern blocks (that touch air) only 2% are chosen as a placement position. The result of doing `//ezsc Clipboard -m sea_lantern` is therefore:

![](../../.gitbook/assets/2024-12-10_13.54.43.png)

For cases like these, where you want to place a structure at every instance of a specific block you'd therefore use `-n 100%`. Doing `//ezsc Clipboard -m sea_lantern -n 100%` in our example results in:

![](../../.gitbook/assets/2024-12-10_13.54.33.png)
{% endhint %}

***

### Distribution Seed: <mark style="color:orange;">`-i <seed>`</mark>

Sets the seed for the random number generator which chooses the initial random placement positions.&#x20;

Defaults to -1 (random seed), meaning that the placement positions differ in each execution of the scatter command.

***

### Uniformity: <mark style="color:orange;">`-u <iterations>`</mark>

Determines how uniformly spread out all placement positions are. Expecting a positive integer including 0.

Defaults to 15.

The uniformity algorithm works by starting with fully random placement positions, and iteratively repelling all positions apart from one another. This parameter sets the number of repelling iterations to perform. Thus, 0 means the placement positions within your region are purely random.

> #### Example:
>
> Ex. command: `//ezsc Clipboard C C`` `**`-u <iterations>`** (with the clipboard being a default vanilla oak tree for no particular reason)
>
>
>
> * `-u 0` (fully random distribution)
> * `-u 2` (slightly uniform distribution)
> * `-u 20` (very uniform distribution)
>
>
>
> GIF starting with **`-u 0`** and ending with **`-u 20`**:
>
> ![](../../.gitbook/assets/ScatterUniformity_demo.gif)

***

### Mask Cover Block: <mark style="color:orange;">`-l <pattern>`</mark>

After placing all structures, replace all unaffected surface blocks within the region that match the mask filter (-m) with the given block. (-m must be set for this flag to take effect.)

This is a niche utility option for cases in which you apply a scatter multiple times in a neighbouring region but do not want to place structures in areas where you already did scatter before. So using this flag, you can (temporarily within your workflow) overwrite all surface blocks within your region with the given block, such that any following scatter operations that overlap with already covered regions, do not place structures there because the surface blocks have been "covered".

> Examples:
>
> `//ezbrush scatter Clipboard -m clay`
>
> Running ezbrush scatter **without** the `-l` flag results in densely placed area whereever the clicked areas overlap, which may not be the desired result.
>
> ![](../../.gitbook/assets/ScatterMaskCoverBlock_example1.gif)
>
>
>
> `//ezbrush scatter Clipboard -m clay -b pink`
>
> Running ezbrush scatter **with** `-b pink`, whereby pink wool is just some random block in this case, covers the affected areas such that, combined with the `-m clay` mask filter subsequent brush clicks do not place any new shapes there, even when the regions overlap.
>
> ![](../../.gitbook/assets/ScatterMaskCoverBlock_example2.gif)

***

### Trim outside selection: <mark style="color:orange;">`-t`</mark>

By default `scatter` will determine placement positions within the currently selected region, but will place blocks outside the region if a placement position is at the border of the currently selected region. You may cut off any such blocks (prevent them from being placed) with this `-t` flag.

Turning on this flag is comparable to running the command with `//gmask #region` (for //ezscatter at least).

> Examples:
>
> If this is our selected region:
>
> ![](../../.gitbook/assets/2024-12-02_21.46.25.png)
>
> Then executing the ezsc command without the flag will result in blocks potentially being placed outside the region. Only the placement/origin positions are restricted to the region.
>
> Without `-t` flag:
>
> `//ezsc Cl C C -s 15,21,15 -n 0.5%`
>
> ![](../../.gitbook/assets/2024-12-02_21.46.36.png)
>
> With `-t` flag:
>
> `//ezsc Cl C C -s 15,21,15 -n 0.5%`` `**`-t`**
>
> ![](../../.gitbook/assets/2024-12-02_21.46.46.png)



***
