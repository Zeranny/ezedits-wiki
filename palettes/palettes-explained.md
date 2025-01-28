# Palettes Explained

Palettes in ezEdits represent a list of blocks that can be used in several commands where the order of blocks will be maintained.

Palettes can be saved and accessed using the **`#`** prefix for user-saved palettes, and **`##`** for [inbuilt preset palettes](default-palettes.md).

For reference, here's an example:

<figure><img src="../.gitbook/assets/palette_Grayscale.png" alt=""><figcaption><p>##Grayscale</p></figcaption></figure>

Some of the many features that use palettes include:

* `//eztexture ...` - [Texturing Commands](../commands/texturing.md)
* `#palette` - [Palette mask](../masks-and-patterns/masks.md#palette-mask)
* `//ezbrush gradient ...` - [Brushes](../brushes-and-tools/brushes/)

Palettes can be constructed as a simple list of blocks, or via several modifiers:

* **`,`** - <mark style="color:orange;">**Concatenate**</mark>:
  * Adds one block or palette to the end of the preceding block or palette.\
    e.g `stone,dirt` is a 2 block palette of stone and dirt. `stone,##Grayscale` is a palette made of stone and the blocks of the ##Grayscale preset palette.
* **`-`** - <mark style="color:orange;">**Invert**</mark>:
  * Reverses the order of a palette.\
    e.g `-##Grayscale` is the ##Grayscale preset palette in reverse order (starts with white instead of black)
* **`(start:end)`** - <mark style="color:orange;">**Sub-palette**</mark>:
  * Returns a portion of a palette.\
    e.g `##Grayscale(1:8)` will return the first 8 blocks of the ##Grayscale preset palette.
* **`*`** - <mark style="color:orange;">**Repeater**</mark>:
  * Repeats the previous segment a given number of times.\
    e.g `gold_block*10,diamond_block` will return a palette of 10 gold blocks, followed by a single diamond block.
* **`[]`** - <mark style="color:orange;">**Grouping**</mark>:
  * Groups palettes together to allow a modifier to treat them as a single palette.\
    e.g `-##Grayscale,gold_block` will return the ##Grayscale preset palette in reverse order, with a gold block at the end. Where `-[##Grayscale,gold_block]` will return the gold block at the start.
* **`=`** - <mark style="color:orange;">**Result**</mark>:
  * Allows a palette to be tab-completed into its list of blocks if needed.

### Video Tutorial

[MegRae](https://megrae.art/) also made a tutorial for palettes:

{% embed url="https://youtu.be/VGsTle3g9AU" %}
