# REMS Fishing 1.0.0

By REMS. A fishing overhaul for 7 Days to Die V3.4: active angling, unattended traps, shoreline gathering, stocked
ponds and cooking, decided on the server so it works the same in single player, co-op and on dedicated servers.

## What it adds

- **Angling.** Tap for a short cast or hold to charge a long one. Strike when the float goes under, then fight the
  fish with your own stamina against its runs and the line tension. Lean against a run with the strafe keys (A or D),
  and ease off to recover stamina. A card shows the catch, and you keep it or release it.
- **Two rods.** The Standard rod and the Precision rod, with quality levels from the Fishing crafting skill.
- **Bait, lures and rod mods.** Earthworms, cut bait, dough bait and glow bait; four lures (spinner, jig, crankbait,
  trout fly); and eight rod mods fitted at a workbench (Smooth Drag, Braided Line, Fluorocarbon, Wire Leader, Cork
  Grip, Slip Float, Bottom Sinker, Bite Bell). Bait and lures go on the rod, like ammo in a gun. The rod's Modify
  screen has a Tackle panel with a Bait slot for one stack of bait and a Lure slot for one lure. A loaded lure is cast
  instead of bait. Hold Reload with the rod out to choose from a wheel of what you carry, or tap it to top up the
  bait. Bait refills automatically with the same kind from your pack, and casting with an empty rod loads the first
  bait you carry. The ammo counter shows what's on the line. Each bite uses one bait, even if you miss. Lures aren't
  used up and are only lost if the line snaps. Scrapping or selling a rod returns its bait and lure to your pack.
- **A catch roster.** Ten fish plus the eel, crayfish, crab, shrimp, two turtles, clams, mussels, snails and two
  frogs. Each species has its own biomes, depths, times and liked baits.
- **The Fishing Trap.** Bait it and leave it in water. It has one catch chance every 4 in-game hours and catches up
  to 48 hours when its area loads again. It opens its own window: a bait slot, what lives in that water and how
  likely each catch is, the catch grid, and tiles for the catch count, the time to the next check, the water and its
  fish stock. Three trap mods fit in it: the Funnel Entrance (+25% catch chance), the Bait Box (40% of catches keep
  their bait) and the Bigger Cage (holds 10 catches instead of 6). Traps in the same water share what it can give.
- **Shoreline gathering.** Clam beds, mussel beds and snail patches in shallow water, and frogs on the bank at dusk
  and night. Catch frogs by hand, or swing the Dip Net at them from a few metres away. Swing it through shallow
  water near the bank to scoop up shrimp, crayfish and small panfish.
- **Stocked ponds.** Dig a pond at least 7 by 7 and 3 deep, fill it, place a Pond Marker at its edge and release
  fingerlings from traders. A stocked pond belongs to whoever stocked it: its fish bite for them, their allies and
  party, and players with build rights in a land claim around it. Anyone else fishing there catches wild fish only.
- **Food.** Clean and fillet catches, then cook them into fish meals. With REMS Culinary Hearth installed, a seventh
  challenge chapter about cooking your catch appears, and REMS Fishing leaves out its own Fish and Chips, which
  Culinary Hearth already has.
- **Progression.** The Fishing crafting skill (Angler's Monthly magazines, levels 1 to 50) unlocks rod quality,
  tackle, the trap, the Dip Net and the Pond Marker. The Patient Angler is a set of seven books with optional
  technique bonuses, and reading all seven unlocks Master Angler.
- **Fishing Jobs board.** Ask any trader "Got any fishing work?" for fishing jobs. Finished jobs raise your Angler
  standing (ranks 1 to 5).
- **Challenges.** A REMS Fishing challenge category with six chapters (seven with Culinary Hearth).
- **Fishing Journal.** Press J. It holds species notes, records, help pages and your personal bests.
- **Junk and treasure.** Rod bites can bring up junk or a Waterlogged Strongbox. Both can be tuned or switched off.

## Requirements

- 7 Days to Die V3.4.
- Easy Anti-Cheat off. REMS Fishing contains a DLL (REMS.Fishing.dll), and the game only loads mod DLLs with EAC off.
- Optional: [Gears](https://www.nexusmods.com/7daystodie/mods/4017) puts the settings below in the game's menus.
- Optional: REMS Culinary Hearth adds a cooking challenge chapter. Nothing in REMS Fishing needs it.

## Installing

1. Close the game.
2. Extract the `zzzz_REMS_Fishing` folder into your `Mods` folder, so the path is `Mods/zzzz_REMS_Fishing/ModInfo.xml`.
   The `zzzz_` makes it load after your other mods, so a trader or loot overhaul can't wipe out its additions.
3. Start the game with EAC off.

### Multiplayer

- **Install it on the server and on every player's game.** The server decides every catch, bite, trap catch, gather,
  pond fish and job, and each player's game draws the HUD, the fight and the windows and sends requests. Both sides
  run the DLL and must have the same version. The server sends its XML to players, but not DLLs, icons or models.
- **Hosted co-op:** the host and every player who joins need the mod.
- **Dedicated server:** put the mod in the server's `Mods` folder and in each player's `Mods` folder.
- Rewards are tied to ids the server hands out, so a lost or repeated message never pays twice, and a player's own
  settings never change anyone's odds.

## Settings

REMS Fishing works without any other mod. With Gears installed, its options appear in the game's menus.

### Your own options (Mod Settings > REMS Fishing)

Each player sets these for themselves, in the main menu or in game. They apply at once and never change the odds.

| Option | Default | Choices |
|---|---|---|
| Reel input | Hold | Hold: hold Primary to reel, let go to ease off. Toggle: tap to start reeling, tap again to ease off. |
| Fish stamina bar | On | Shows how much fight the hooked fish has left (the Resistance pips on the fight panel). |
| Bite prompt size | 100% | 75% to 150%: the size of the bite ring around the crosshair. |
| Catch card | On | Off: only the usual pickup line after a catch. |
| Key hints | On | Off: hides the cast, reel and journal keys under the crosshair. |
| First-time tips | On | Off: no tips the first time you hold a rod, the Dip Net or a lure. |
| Fight panel position | Bottom | Bottom (centre, above the toolbelt) or Lower left. |

### World rules (New Game or Continue > Mod settings)

These belong to the world, and the host or server decides them for everyone. The server rolls every catch with its
own values and sends them to each player.

| Setting | Default | Range |
|---|---|---|
| Junk catches | On | On / Off (Off also stops junk in Fishing Traps) |
| Junk chance (rod) | 8% | 0% to 25% |
| Treasure catches | On | On / Off (Off also stops treasure in Fishing Traps) |
| Treasure chance (rod) | 1% | 0% to 5% |
| Treasure rewards | Modest | Modest / Standard |
| Salvage in traps | Off | Off / Junk only / Junk and treasure |
| Trap junk chance | 2% | 0% to 10%, used when traps allow junk |
| Trap treasure chance | 0.1% | 0% to 1%, used when traps allow treasure |
| Trap check interval | 4h | 2h / 4h / 6h / 8h of in-game time between catch checks |
| Trap catch-up limit | 48h | 24h / 48h / 72h / Unlimited: how long a trap keeps fishing while its area is unloaded |
| Trap mods | On | Off: the three trap mods can't be crafted, the trap window has no mod slots, fitted mods do nothing |
| Dip Net scooping | On | Off: the Dip Net only swings at frogs |
| Catch amount | 1x | 0.5x / 1x / 1.5x / 2x: crayfish, shrimp, crabs and the like per trap catch or scoop (a fish is always one fish) |
| Frogs | On | Off: no frogs come out, and any already out leave |
| Gathering beds | On | Off: no new beds, and existing beds can't be gathered |
| Fishing jobs | On | Off: no new jobs can be taken (jobs already taken can still be turned in) |
| Salvage items | All on | A group switch each for Scrap metal (scrap iron, brass), Trash (empty jars, polymers) and Supplies (cloth, duct tape, lost spinner), a switch for each item, and one for each strongbox. An item comes up only while its group and its own switch are both on. |
| Show category chances | On | On / Off: whether the fishing help and the trap window show chances as percentages or as words |

With the defaults, a rod bite is 91% wildlife, 8% junk and 1% treasure. Junk and treasure never count as fish: not
for discoveries, trophies or wildlife challenges. Changes apply at the next catch; a bite that has already rolled
keeps its result.

### Dedicated servers

- **With Gears:** the first start writes `Saves/<World>/<Save>/WorldModSettings.xml`. Stop the server, edit the
  `REMS_Fishing` values there (use one of the listed values, with the % sign), then start it again.
- **Without Gears:** edit the `defaultValue` of each setting in `ModSettings.xml` in the REMS Fishing folder, then
  restart. Players without Gears can set their own options (the first table above) the same way.

### Console commands

- `remsfishsettings` (or `rfset`): lists the rules in use and where they came from. On a client it shows the copy the
  server sent.
- `remsfishskill` (or `rfskill`): shows each player's Fishing skill, the Patient Angler volumes read and the bonuses
  in use. `rfskill <name>` shows the players whose name contains `<name>`. Run it on the server or the host.

## Compatibility

- All config changes are XPath patches. No vanilla file is replaced.
- Traders get a dialogue line, so the Fishing Jobs board also works at other mods' traders. No trader buildings are
  edited.
- Rod mods use their own mod slots. Tool mods from other mods that load after REMS Fishing may still fit rods.
- The Fishing Trap and the rod's Tackle panel use their own windows, built from vanilla sprites and named colours, so
  UI mods that restyle the vanilla windows restyle them too. A UI mod that rebuilds the backpack window still works;
  shift-click into the trap or the Tackle panel needs the vanilla item-stack controller.
- Other mods that patch the methods below work alongside REMS Fishing. Every REMS patch is a postfix or a prefix. Only
  three prefixes ever skip the original, and only for REMS Fishing's own things: opening a Fishing Trap, and
  shift-clicking bait, a lure or a trap mod into the trap or the Tackle panel.

## Harmony patches

REMS Fishing patches only what the game gives no other hook for. Every patch is listed here with its reason.

**Game methods**

| Method | Kind | Why |
|---|---|---|
| `AIDirector.NotifyNoise` | Postfix | Gunshots and explosions within 30 m spook fish for a minute (server side). |
| `XUiC_ItemActionList.AddActionActions` | Postfix | Catches open with the vanilla bundle action; this labels the button Fillet or Clean instead of Open. |
| `XUiC_ItemInfoWindow.GetBindingValueInternal` | Postfix | Adds the stored weight, length and day to a trophy's description. |
| `Challenges.Challenge.Read` | Postfix | Restores REMS Fishing challenge objectives after a save loads. They save in the shape of a vanilla objective, so a save stays loadable without the mod. |
| `EntityPlayerLocal.MoveByInput` | Prefix | While a fish is on, the strafe keys lean against a run instead of moving you. Only while fighting a fish with a rod; the original method always runs. |
| `TEFeatureStorage.OnLockResponseLocal` | Prefix | A Fishing Trap opens its own window instead of the loot window. Skips the original only for a Fishing Trap; every other container opens as usual. |
| `XUiC_ItemStack.HandleMoveToPreferredLocation` | Prefix (two) | Shift-click on bait, a lure or a trap mod in the backpack or toolbelt puts it in the open trap's slots or the rod's Tackle panel. Skips the original only when it does that. |
| `XUiC_RecipeList.Update` | Prefix | With trap mods switched off by the host, their three recipes leave the crafting lists. |
| `ItemActionEntryScrap.HandleRemoveAmmo` | Postfix | Scrapping or selling a rod hands its bait and lure back, the way vanilla unloads a gun. |
| `ItemActionEntryAssemble.OnActivated` | Prefix | Opening Modify keeps the tackle on the rod (that call also unloads guns). |
| `XUiC_CombineGrid.SetResult` | Prefix | A combined rod comes out without the first rod's tackle, which goes back to your pack. |
| `XUiC_HUDStatBar.setupActiveItemEntry`, `.Update`, `.GetBindingValueInternal` | Postfix, prefix, postfix | The ammo counter shows the bait on the rod and in your pack, or an infinity sign for a lure. |

**REMS Fishing's own code** (patched by hand at start-up; each turns itself off with a log warning if its target
changes)

| Method | Kind | Why |
|---|---|---|
| `REMS.Fishing.FishingServer.SendResult` | Postfix (stocked ponds) | The pond catch ledger: a pond fish that is never landed, or is released, goes back to the pond. |
| `REMS.Fishing.FishingServer.SendResult` | Postfix (jobs) | Feeds server-side catches to the Fishing Jobs board, so turn-ins are checked by the server. |
| `REMS.Fishing.FishingServer.SendResult` | Postfix (bank landing) | Catches of 8 kg or more are pulled up the bank: the server picks a safe spot beside the angler and tells nearby players. |
| `REMS.Fishing.FishingServer.RollCatch` | Prefix and postfix (stocked ponds) | Reads which player a bite belongs to, so a stocked pond's fish bite only for its owners and their allies. |
| `REMS.HUD.XUiC_RemsHudData` ammo readout | Postfix (only with REMS HUD loaded) | REMS HUD's ammo readout shows a held rod's bait or lure like a gun's ammo. Without REMS HUD nothing is patched. |

## Save data

The server keeps REMS Fishing's world data in the save folder (`Saves/<World>/<Save>/`):

- `REMS_FishingTraps.txt`: trap clocks, catch units and what each trap has caught.
- `REMS_FishingPonds.txt`: stocked ponds, their species and who stocked them.
- `REMS_FishingShore.txt`: gathering beds.
- `REMS_Fishing/Jobs.xml`: the Fishing Jobs boards and each player's Angler standing.
- `REMS_FishingLedger.txt`: catch ids already paid out and each player's pending catch roll, so a restart or reconnect
  never pays a catch twice or rerolls it.

Each file is written beside itself first and then swapped in, so after a crash or an interrupted save you may also see
copies ending in `.tmp` or `.bak` (for example `REMS_FishingPonds.txt.bak`). They are spare copies the mod can load
from when a save was cut short, so leave them in place while the mod is installed.

Fishing skill, records, discoveries and challenge progress are saved on each player.

## Removing the mod

- The game can't load items or blocks from a mod that is gone. Before you remove REMS Fishing from a save, pick up
  your Fishing Traps and Pond Markers and get rid of REMS Fishing items, or start a new world.
- The challenge journal stays readable without the mod. REMS Fishing challenges are dropped, and vanilla challenges
  keep their progress.
- The files listed under Save data, the `REMS_Fishing` folder and any `.tmp` or `.bak` copies of them can be deleted
  once the mod is removed.

## Credits

REMS.
