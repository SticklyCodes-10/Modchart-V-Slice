# Modchart V-Slice

A drag-and-drop Friday Night Funkin' V-Slice modchart runtime inspired by the modifier and timeline model of FunkinModchart.

## Install

1. Download this repository as a ZIP.
2. Put the folder containing _polymod_meta.json directly inside your FNF mods/ directory.
3. Enable Modchart V-Slice in the game's Mods menu.
4. Start a song. The module is loaded by V-Slice's existing Polymod/HScript module system.

No game source edits, Haxe compiler, haxelib install, or executable patching are required.

## Current port

- Persistent Module with gameplay and Freeplay callbacks.
- Beat-indexed set, ease, and add timelines.
- One-shot callback and beat-repeat repeater events.
- Runtime modifier values through setPercent, getPercent, and addModifier.
- Visual receptor/note effects: drunk, tipsy, confusion, bumpy, stealth, mini, flip, rotate, wave, pulse, and alpha.
- Automatic restoration of modified sprite transforms when a song ends or retries.
- Main Menu and Freeplay integration: Freeplay selection callbacks trigger a lightweight menu pulse, while the optional menuWave modifier can animate menu item motion.

Example usage from another HScript module:

```haxe
var chart = ModchartVSliceModule.instance;
chart.setPercent('drunk', 0.35);
chart.ease('confusion', 16, 8, 1.0, FlxEase.quadInOut);
chart.set('tipsy', 32, 0.6);
chart.ease('tipsy', 48, 8, 0.0, FlxEase.sineInOut);
chart.callback(64, function() trace('64 beats!'));
chart.repeater(80, 16, function(beat) trace('loop at ' + beat));
```

The built-in module starts with no modifiers enabled, so it does not alter a chart unless another script activates them.

## Compatibility

Targets the V-Slice 0.8.x Polymod API (api_version 0.8.0). The runtime uses the game's own Strumline, StrumlineNote, and NoteSprite objects. It does not bundle the archived FunkinModchart renderer, which depends on a compile-time HaxeFlixel adapter and macro setup unavailable to ordinary drag-and-drop mods.

## Development status

This is an initial native HScript port, not a complete recreation of every original renderer feature. Multiple independent playfields, custom 3D camera/projection, shader/vertex rendering, and arrow-path rendering still need a dedicated V-Slice renderer and are not claimed as implemented.

Test against the exact game build you use. V-Slice's mod API and internal note rendering can change between releases.
