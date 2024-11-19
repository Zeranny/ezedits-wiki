# Scatter Parameters

`//ezscatter` and `//ezbrush scatter` place multiple shapes within a region. The positions that these commands choose can be customized with the parameters described on this page.

`scatter` first determines a list of potential placement positions. The amount or density and uniformity of the distribution can be set with the `-n <density>` and the `-u <iterations>` parameters. From these potential placement positions you can then filter out ones that do not match certain conditions using `-d <directions>` & `-e <threshold>`, `-m <mask>`, and `-t`.

***

### Density: `-n <density>`

Determines how many placements are placed, by specifying a density percentage.

The density value is a percentage. It determines what percentage of surface blocks a structure should be placed.

To be overly specific: Let amountSurfaceBlocks be the result of `//count [!air]&[~air]`, then the final amount of structures placed is equal to _amountSurfaceBlocks \* density / 100_. (The total amount can be lower due to the mask filter, the directional filter, and the trimming flag)

Examples:

* `-n 2%` (default)
* `-n 0.05%`
* `-n 0.05` ('%'-sign is optional)

Note: `0.5` is equal to `0.5%` not `50%`.

***

### Uniformity: `-u <iterations>`

Determines how uniformly spread out all placement positions are. Expecting an integer between 0 and 20.

Examples:

* `-u 0` (fully random distribution)
* `-u 2` (slightly uniform distribution)
* `-u 15` (very uniform distribution)



***

### Directional Filter: `-d <directions>` and `-e <threshold>`

Enables filtering out placement positions on surfaces that are facing certain directions. 

The `-d <directions>` parameter defines the list of directions in which the surface, on which the placement positions points are placed at, must face. If a placement position does not satisy this condition, no structure will be placed there.

The `-e <threshold>` parameter defines how much the surface normal at the placement position must align with any of the directions given by `-d`. The higher the value the stronger the filter

Examples:

* `-d up -e 0.4` (scatter points must be on a surface facing roughly upwards)
* `-d up -e 0.8` (scatter points must be on a surface facing mostly upwards)
* `-d n,s,w,e -e 0.5` (scatter points must be on a surface facing any of the cardinal directions, leaving out up and down.)

***

### Mask Filter: `-m <mask>`

Enables filtering out placement positions that do not match a mask given by `-m <mask>`. Placement positions must satisfy the mask for a structure to be placed.

Examples:

* `-m stone`
* `-m !stone`
* `-m =y>95`

***

### Trimming Filter: `-t`

The trimming flag removes all placement positions that are close enough to the edge or your selected region that they're bounding box is not fully inside the selection.

### Cut off outside the selection: `-c`

By default `scatter` will determine placement positions within the currently selected region, but will place blocks outside the region if e.g. a placement position is at the border of the currently selected region. You may cut off any such blocks with the `-c` flag. Effectively runs the command with `//gmask #region`
