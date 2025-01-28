# Palettes Explained

Palettes in ezEdits represent a list of blocks that can be used in several commands where the order of blocks will be maintained.\\

Palettes can be saved and accessed using the **`#`** prefix for user-saved palettes, and **`##`** for inbuilt preset palettes.\
e.g `##LegacyWool` represents the inbuilt wool palette starting from white wool, orange wool up to red wool and finally black wool.

Some of the many features that use palettes include:

* `//eztexture ...` - _Texturing Commands_
* `#palette` - _Masks_
* `//ezbrush gradient ...` - _Brushes_

Palettes can be constructed as a simple list of blocks, or via several modifiers:

* **`,`** - Concatenate: Adds one block or palette on to the end of the preceding block or palette.\
  e.g `stone,dirt` is a 2 block palette of stone and dirt. `stone,##LegacyWool` is a palette made of stone and the blocks of the ##LegacyWool preset palette.
* **`-`** - Invert: Reverses the order of a palette.\
  e.g `-##LegacyWool` is the wool preset palette in reverse order (starts with black instead of white)
* **`(start:end)`** - Sub-palette: Returns a portion of a palette.\
  e.g `##LegacyWool(1:8)` will return the first 8 blocks of the ##LegacyWool preset palette.
* **`*`** - Repeater: Repeats the previous segment a given number of times.\
  e.g `gold_block*10,diamond_block` will return a palette of 10 gold blocks, followed by a single diamond block.
* **`[]`** - Grouping: Groups palettes together to allow a modifer to treat them as a single palette.\
  e.g `-##LegacyWool,gold_block` will return the ##LegacyWool preset palette in reverse order, with a gold block at the end. Where `-[##LegacyWool,gold_block]` will return the gold block at the start.
* **`=`** - Result: Allows a palette to be tab-completed into its list of blocks if needed.

## Default Palettes

By default, palettes are saved per player. However, server admins may define a set of default palettes accessible to all players in `plugins/ezEdits/resources/DefaultPalettes.json`. We also come with a predefined set of default palettes:

<figure><img src="../.gitbook/assets/palette_Grayscale.png" alt=""><figcaption><p>##Grayscale</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GrayRough.png" alt=""><figcaption><p>##GrayRough</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GrayWarm.png" alt=""><figcaption><p>##GrayWarm</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GrayCold.png" alt=""><figcaption><p>##GrayCold</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_BlueWhiteRed.png" alt=""><figcaption><p>##BlueWhiteRed</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Infrared.png" alt=""><figcaption><p>##Infrared</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Magma.png" alt=""><figcaption><p>##Magma</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Beige.png" alt=""><figcaption><p>##Beige</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowRed.png" alt=""><figcaption><p>##GlowRed</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowOrange.png" alt=""><figcaption><p>##GlowOrange</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowYellow.png" alt=""><figcaption><p>##GlowYellow</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowLime.png" alt=""><figcaption><p>##GlowLime</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowCyan.png" alt=""><figcaption><p>##GlowCyan</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowBlue.png" alt=""><figcaption><p>##GlowBlue</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowPurple.png" alt=""><figcaption><p>##GlowPurple</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_GlowMagenta.png" alt=""><figcaption><p>##GlowMagenta</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeRed.png" alt=""><figcaption><p>##FadeRed</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeOrange.png" alt=""><figcaption><p>##FadeOrange</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeGold.png" alt=""><figcaption><p>##FadeGold</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeLime.png" alt=""><figcaption><p>##FadeLime</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeCyan.png" alt=""><figcaption><p>##FadeCyan</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeBlue.png" alt=""><figcaption><p>##FadeBlue</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadePurple.png" alt=""><figcaption><p>##FadePurple</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_FadeMagenta.png" alt=""><figcaption><p>##FadeMagenta</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_LegacyWool.png" alt=""><figcaption><p>##LegacyWool</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Light.png" alt=""><figcaption><p>##Light</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Moss.png" alt=""><figcaption><p>##Moss</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Ice.png" alt=""><figcaption><p>##Ice</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Rocks.png" alt=""><figcaption><p>##Rocks</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Leaf.png" alt=""><figcaption><p>##Leaf</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_LeavesAll.png" alt=""><figcaption><p>##LeavesAll</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Sand.png" alt=""><figcaption><p>##Sand</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_EnchantedDark.png" alt=""><figcaption><p>##EnchantedDark</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_EnchantedWarm.png" alt=""><figcaption><p>##EnchantedWarm</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_EnchantedBright.png" alt=""><figcaption><p>##EnchantedBright</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_ShiningGold.png" alt=""><figcaption><p>##ShiningGold</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_Brown.png" alt=""><figcaption><p>##Brown</p></figcaption></figure>

<figure><img src="../.gitbook/assets/palette_DustyBrown.png" alt=""><figcaption><p>##DustyBrown</p></figcaption></figure>




