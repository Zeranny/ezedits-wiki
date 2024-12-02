# Scatter Parameters

[`//ezscatter`](./#ezscatter) and [`//ezbrush scatter`](./#ezbrush-scatter) place multiple structures within a region. The positions that these commands choose can be customized with the parameters described on this page.

`scatter` first extracts surfaces from your region (all non-air blocks touching air). You can filter out surfaces that do not match certain conditions using `-d <directions>` & `-e <threshold>`, `-m <mask>`, and `-t`. On the remaining surfaces, a placement position distribution according to the given density `-n <density>` and uniformity  `-u <iterations>` is calculated and structures are placed.&#x20;

***

### Density: `-n <density>`

Determines how many placements are placed, by specifying a density percentage.

The density value is a percentage. It determines what percentage of surface blocks a structure should be placed.

To be overly specific: Let N be the result of `//count [!air]&[~air]`, then the final amount of structures placed is equal to _N \* density / 100_. (The total amount can be lower due to the mask filter, and the directional filter)

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

***

### Uniformity: `-u <iterations>`

Determines how uniformly spread out all placement positions are. Expecting an integer between 0 and 20.

Defaults to 15.

> #### Example:
>
> Ex. command: `//ezsc Clipboard C C`` `**`-u <iterations>`** (with the clipboard being a default vanilla oak tree for no particular reason)
>
>
>
> * `-u 0` (fully random distribution)
> * `-u 2` (slightly uniform distribution)
> * `-u 20` (maximal uniform distribution)
>
>
>
> GIF starting with **`-u 0`** and ending with **`-u 20`**:
>
> ![](../../.gitbook/assets/ScatterUniformity_demo.gif)

***

### Directional Filter: `-d <directions>` and `-e <threshold>`

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

### Mask Filter: `-m <mask>`

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

### Trim outside selection: `-t`

By default `scatter` will determine placement positions within the currently selected region, but will place blocks outside the region if a placement position is at the border of the currently selected region. You may cut off any such blocks (prevent them from being placed) with this `-t` flag.

Turning on this flag is comparable to running the command with `//gmask #region`.

Note: This flag is only available for the scatter command, not the brush.

> Examples:
>
> If this is our selected region:
>
> ![](../../.gitbook/assets/2024-12-02_21.46.25.png)
>
> Then executing the ezsc command without the flag will result in blocks potentially being placed outside the region. Only the placement/origin positions are restricted to the region. Without flag:
>
> `//ezsc Cl C C -s 15,21,15 -n 0.5%`
>
> ![](../../.gitbook/assets/2024-12-02_21.46.36.png)
>
> With `-t` flag:
>
> `//ezsc Cl C C -s 15,21,15 -n 0.5% -t`
>
> ![](../../.gitbook/assets/2024-12-02_21.46.46.png)



***
