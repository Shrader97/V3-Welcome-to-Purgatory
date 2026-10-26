# Circle Minimap

A round minimap for **7 Days to Die**, drawn from your own explored map (the same data as the M map).
Tested on **V3.3 (b18)**.

## Features
- Turns with your view; the arrow shows where you (or your vehicle) face.
- Shows the same icons as the M map: traders, your bedroll and land claim, quests, waypoints, your backpack,
  supply drops, vending machines, your vehicles and drone, allies, and other loaded vehicles.
  Things your compass tracks stay pinned to the rim when they are far away, so you always know which way to go.
- In a vehicle it zooms out as you speed up and back in as you slow down.
- Move it anywhere on screen and resize it with the mouse; it remembers where you put it.
- Rebind its keys in game, no file editing needed.
- Hides itself while the inventory, map or a menu is open, and when the HUD is hidden.
- Client-side only: no server install, works in single player and on servers that don't run it.

## Keys
| Key | Action |
|---|---|
| F2 / Numpad + | Zoom in |
| F3 / Numpad − | Zoom out |
| F5 | Move mode: drag the map, mouse wheel resizes, F5 or Enter to save |
| Delete | Show / hide |

### Changing keys
Press **F5**. A **Key bindings** panel opens next to the map: click a key, then press the new one
(Esc or right click cancels). Picking a key another map action already uses swaps the two, and keys the
game itself uses get a warning. Your keys are saved right away and survive updates of the mod.
F3 is also one of the game's own keys, so you may want to change Zoom out to something else.

## Install
1. Launch the game **with EAC off** (this is a DLL mod).
2. Unzip so that you get `7 Days To Die/Mods/CircleMinimap/CircleMinimap.dll`.
3. Start the game.

## Settings
`settings.xml` holds position, size, zoom, opacity, rotation and auto-zoom options, each with a comment.
Whatever you set in game (position, size, keys) is written to `settings.local.xml`; delete that file to go
back to `settings.xml`.
