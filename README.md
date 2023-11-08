# BlockPaletteArchive
Archive of previous Minecraft Bedrock block palettes of interest, useful for world format upgrading

This repository contains (to my knowledge, at the time of writing) every unique NBT block palette from 1.9 to 1.20.50.23 beta. This is highly useful for testing blockstate deserializers designed to handle older worlds.

Versions older than 1.9 are not included, since versions prior to 1.9 did not use NBT blockstates, relying exclusively on ID and meta.

Note that in some cases (e.g. 1.9, 1.10, 1.12) these are **NOT** the same as the palettes sent over the wire. Versions prior to 1.13 still used legacy ID + meta to represent blocks; however, they used blockstate NBT to represent blockitems on disk, which is why their palettes are present here.

## File format
Inside the files you will find a series of root TAG_Compounds concatenated together.

**Note:** for technical reasons, these are currently encoded using a **non-standard varint NBT**, in the same manner as the Bedrock network protocol. This format is mostly the same as standard little-endian NBT, except for the following differences:

- All strings are prefixed by an unsigned varint length instead of a short
- TAG_Int is encoded as a signed (zigzag) varint32 instead of a 4-byte LE int32
- TAG_Long is encoded as a signed (zigzag) varint64 instead of an 8-byte LE int64
- TAG_IntArray is encoded as an array of signed (zigzag) varint32s instead of 4-byte LE int32s

Using PocketMine-MP, they can be decoded like so: `var_dump((new NetworkNbtSerializer())->readMultiple(file_get_contents($file)));`

In this format, the palettes can be directly provided to [pmmp/mapping](https://github.com/pmmp/mapping) as input palettes to generate palette mapping tables.
