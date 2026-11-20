# Modchart V-Slice

A small drag-and-drop mod for **Friday Night Funkin' (V-Slice)**. It adds a subtle beat-synced camera lean, hit accents, and miss counter-kicks using the game's built-in Polymod/HScript module system.

## Install

1. Download this repository (or the packaged `modchart-v-slice` folder).
2. Copy the `modchart-v-slice` folder into your Friday Night Funkin' install's `mods/` directory.
3. Enable **Modchart V-Slice** in the game's Mods menu (or enable the mod in your existing mod configuration).
4. Start a song. The effect runs automatically; no chart edits or source rebuild are required.

The folder you copy should look like this:

```text
mods/
└── modchart-v-slice/
    ├── _polymod_meta.json
    └── scripts/
        └── ModchartVSlice.hxc
```

## What it does

- Alternates a restrained camera tilt on each beat.
- Adds a small accent on note hits.
- Adds a counter-kick on misses.
- Smoothly returns the camera toward neutral.
- Does not alter note data, hit windows, score, health, or chart files.

## Compatibility

This mod targets the current V-Slice Polymod API line (`>=0.8.0 <0.9.0`). It uses the stock scripted `Module` callbacks and HScript runtime, so it is installed like an ordinary V-Slice mod.

### About FunkinModchart

[dotaxel/FunkinModchart](https://github.com/dotaxel/FunkinModchart) is the visual/modifier reference for this project. Its README currently warns that the library is unmaintained, and its setup requires a compiled HaxeFlixel haxelib plus an engine adapter wired into the game's source/build configuration. That is not something the stock V-Slice drag-and-drop Polymod loader can load directly.

For that reason, this repository implements a native, source-free V-Slice modchart first. Full lane transforms, 3D playfields, and arrow-path rendering would require a compatible compiled V-Slice adapter/library integration rather than a plain mod folder.

## Development

The script lives at `mods/modchart-v-slice/scripts/ModchartVSlice.hxc`. Edit it, then use the game's mod hot-reload workflow (or restart the game) to test changes.

## License

MIT
