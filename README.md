# BlockPaletteArchive
Archive of previous Minecraft Bedrock block palettes of interest, useful for world format upgrading

This repository contains (to my knowledge, at the time of writing) every unique NBT block palette from 1.9 to 1.18.10. This is highly useful for testing blockstate deserializers designed to handle older worlds.

Versions older than 1.9 are not included, since versions prior to 1.9 did not use NBT blockstates, relying exclusively on ID and meta.

Note that in some cases (e.g. 1.9, 1.10, 1.12) these are **NOT** the same as the palettes sent over the wire. Versions prior to 1.13 still used legacy ID + meta to represent blocks; however, they used blockstate NBT to represent blockitems on disk, which is why their palettes are present here.
