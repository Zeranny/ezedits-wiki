# Scatter Parameters

`//ezscatter` and `//ezbrush scatter` place multiple shapes within a region. The positions that these commands choose can be customized with the following parameters:

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

Determines how uniformly spread out all placement positions are. Expected value: An integer between 0 and 20.

Examples:

* `-u 0` (fully random distribution)
* `-u 2` (slightly uniform distribution)
* `-u 15` (very uniform distribution)



***

### Directional Filter: `-d <directions>` and `-e <threshold>`

Enables filtering out placement positions on surfaces that are facing certain directions.

Examples:

* \-d up



***

### Mask Filter: `-m <mask>`



***

### Trimming Flag: `-t`

