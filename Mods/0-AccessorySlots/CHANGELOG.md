# Changelog

## 0.6.0 — 2026-10-26

- **Models on the character.** An item can now show on the player while it is worn - a ring on a finger, a
  pendant at the neck - for you in third person and for everyone who can see you. A mod gives its item a model
  made in Unity (`AccessoryModel`) and, if it wants, an offset, rotation, scale and bone; each slot names the bone
  its models hang on (necklace at the neck, bracelet on the left wrist, the two rings on the left and right ring
  fingers). Asked for in a Nexus comment ("make a mesh in unity and then show up on the character").
- For modders placing one: `acs model bones` lists the skeleton, `acs model bone <name>` says which way a bone
  points, `acs model set ring#1 offset 0,0.02,0` moves the worn model at once, and `acs model xml` prints the
  lines to paste. README "A model on the character" has the Unity side (version, colour space, build target).
- The second ring, on the right hand, shows the mirror image of the first, so a mod places its ring once and it
  fits both hands.
- Your own models hide in first person, and come back when you switch to third person, respawn or change armor.
- From code, a mod can hide its item's model for a while (`Accessories.HideModel`) - Glider hides its packed glider
  while the glider is open.
- **Fix for mods that hang things on the body themselves** (the game's `AddPart` on `onSelfEquipStart`): those
  parts now come back after switching between first and third person, as they do for armor. The game gives worn
  armor a fresh "put on" whenever it rebuilds the body; accessories missed it.
- On its own the framework still adds no items and no models. Nothing changes for an item without a model.
- **Claims game 3.4.0.** Checked on a 3.4.0 dedicated server (every self-check) and in a 3.4.0 game: models on the
  character, first person, view switches, armor changes and Glider's packed glider all behave as on 3.3.

## 0.5.0 — 2026-10-16

- **An item decides whether two of it can be worn.** New item property `AccessoryUnique`: `false` lets two
  of the same ring - or bracelet, or anything - be worn together, even in a slot that says `unique`; `true`
  allows only one of it on you, in any of its slots. An item that does not say follows the slot, as before,
  so every existing item and add-on behaves exactly as it did.
- Why on the item: the slot's `unique` is one setting for every mod's rings, so two mods sharing the ring
  slots could not each have their way - whichever loaded last decided for both. Asked for by an overhaul
  author who wants their own rings to stack.
- Checked on dedicated servers 3.0, 3.2 and 3.3 (selftests w to z); the tab itself is unchanged.

## 0.4.4 — 2026-10-13

- **Russian.** With the game set to Russian, the Accessories tab, its two headings, the necklace,
  bracelet and ring slot names and the two "that does not go here" messages are in Russian. Every other
  language shows English, as before.
- The name of an item, or of a slot another mod adds, comes from that mod - this does not translate
  those.
- No code changed.

## 0.4.3 — 2026-10-05

- **Game 3.3: the Accessories tab works.** On 3.3 the tab came up as a block of blank slots, some
  drawn over the "From other mods" heading, and none of them took an item - nothing could be worn, a
  glider included (players' reports, the day 3.3 went stable). Game 3.3 moved the character screen's
  tabs inside a part that never passes on "the screen was opened", and that is the moment this tab
  sorts its slots. It never got it; now it does. Shift-click into a slot was off on 3.3 for the same
  reason and is back.
- This was broken on 3.3 from 0.4.1, the first version said to run there. 0.4.1 and 0.4.2 were
  checked on a 3.3 dedicated server, which has no screens, so the tab was never looked at on 3.3.
- 3.0 to 3.2 are unchanged.
- Checked on a 3.3.0 game joined to a 3.3.0 dedicated server: the tab shows its slots, and a Scrap
  Chute was crafted, worn and flown. Also checked in a 3.2 game with its character screen put in
  3.3's shape (0.4.2 there shows exactly the reported tab, 0.4.3 the right one, and a glider goes in
  by drag and by shift-click) and on 3.2 as it is.

## 0.4.2 — 2026-10-05

- **Claims game 3.3.0. No code changed.** Game 3.3 is the stable release now and this mod already
  works on it, so `GAME_VERSIONS` widens from `V3.0.0-V3.2.0` to `V3.0.0-V3.3.0`. Checked, not
  assumed: every game member the DLL binds to resolves against the 3.3.0 (b18) build, every Harmony
  patch target is still there, and the mod loads on a 3.3.0 dedicated server with no errors. It has
  not yet been played on a 3.3 game: no 3.3 client was available when this was cut.

## 0.4.1 — 2026-09-27

- Works on the game's **3.3 experimental** build (tested on b14) as well as 3.0 through 3.2, with the same
  download. 3.3 changed how the game stores an item, and 0.4.0 could not read the items in your accessory
  slots there: they loaded empty, and the next save kept them empty. Glider 0.1.1 hit the same change harder -
  its save reader broke the game's own, so every load fell back to the character's backup save (one save
  older). Update both.
- Moving a world from 3.2 to 3.3: update Accessory Slots (and Glider) **before** loading it on 3.3. A character
  saved on 3.2 with 0.4.0 then loads on 3.3 with every accessory, its quality, wear and mods (tested).
- 3.3 only: the character screen no longer logs 32 "EquipmentStack slot does not have a proper 'slot' value"
  errors, and putting an item in an accessory slot no longer reaches into the game's armor slots.
- 3.3 only: the Accessories tab icon no longer sits on top of the game's new Backpack tab icon; the icons are
  spaced out along the row. The three "XML patch ... did not apply" warnings are gone.
- Dropping worn accessories into your backpack on death (Drop On Death = Everything or Equipment) keeps
  working on 3.3, where the game packs the backpack differently.
- Nothing changes on 3.0 - 3.2, and nothing changes for saves: a character saved with 0.4.0 loads as before.

## 0.4.0 — 2026-09-20

- Accessory Slots no longer adds its slot file to the game's own list of config files. It reads the file itself
  and hands it to clients the way Gears hands out its settings file. 0.3.1 worked around the clash that caused
  on servers running Gears; now there is nothing to work around, and no other mod can be caught by it either.
- **With thanks to Laydor, author of [Gears](https://github.com/s7092910/Gears)** - carrying the slot file to
  clients this way is Gears' idea, borrowed with credit.
- Nothing changes for players or for saves: the same file, the same slots, the same server tweaks, the same
  items in the same slots. A 0.3.x client can still join a 0.4.0 server, and a 0.4.0 client a 0.3.x server, so
  a server and its players do not have to update on the same day.
- The merged slot file now appears in the save's `ConfigsDump/` folder, like every other config, so a server
  admin can see exactly which slots their server ended up with.

## 0.3.1 — 2026-09-20

- Fixed: on a dedicated server running Gears, no player could join. The first join threw a
  NullReferenceException on the server and the client sat there, never receiving the game's config files.
  Gears rewrites the game method that sends those files, and a rewritten method never saw the entry this
  mod adds for `accessoryslots.xml` - it read the game's list of config files as empty. Any mod that
  rewrites that method the same way had the same effect. Single player was never affected.

## 0.3.0 — 2026-09-18

- The Accessories tab has two sections. **Jewelry** always shows the necklace, bracelet and rings, even when no
  installed mod adds anything that goes in them, so players know the slots are there to use. A slot nothing fits
  yet is faded, and hovering it says no installed mod adds one yet. **From other mods** shows the slots other
  mods add (Glider's glider slot), once an installed item goes in them, as before.
- The tab now shows whenever the server has the mod. A server that wants no empty jewelry slots can remove them
  from `Config/accessoryslots.xml` like any other slot.
- An unused jewelry slot is only shown: nothing can be put in it and it gives no bonuses.
- Empty slots no longer write their name under the picture; hovering shows it, as on armor slots. The name is
  written only when the game has no picture for the slot, so such a slot is never a blank box. The faded
  picture of an empty slot is a little stronger, so the light jewelry pictures can be seen.
- Section headings and slot names are white, with an outline, so they read over any background.

## 0.2.0 — 2026-09-18

- An item can fit more than one slot. A modder lists them, `<property name="AccessorySlot" value="ring,necklace"/>`,
  and the item can be worn in any of them; shift-click fills the first empty one in that order.
- Slots can have `aliases` - other names that mean the same slot - so two mods that named the same place
  differently end up sharing one slot. The built-in slots keep the names Minecraft's Curios uses (necklace,
  bracelet, ring), and the body part now works too: `neck`, `wrist` and `finger` mean the same three slots.
- Nothing changes for players, saves, server tweaks or Glider.
- For code: `Accessories.SlotsFor(item)` and `Accessories.Fits(item, slot)`; every call that takes a slot
  or a key also takes an alias.
- A mod using a slot list or an alias needs 0.2.0 on the server and every client; an older client reads
  `ring,necklace` as one slot with a strange name.

## 0.1.3 — 2026-09-18

- An empty slot shows its name ("Glider", "Ring 1") and a dimmed colour picture of what goes in it. 0.1.2 did
  not fix the blank slot for the player who reported it, so an empty slot no longer uses the game's faded
  copy of the picture at all; the normal picture, which does show for them, is drawn dimmed instead. The name
  shows even if no picture can be drawn.

## 0.1.2 — 2026-09-17

- An empty slot always shows a faded picture of what goes in it. A player saw the glider slot blank, with
  no picture, although a glider worn in it showed fine: their game had the glider's picture but not the
  faded copy the game makes for empty slots. The slot now draws the normal picture dimmed when that copy is
  missing, and says so once in the log.
- `acs icons` lists each slot's empty-slot picture and whether the game has it, for bug reports.
- The mod's log line now shows its real version (0.1.1 still said v0.1.0).

## 0.1.1 — 2026-09-17

- The character screen's tab icons space themselves out when another mod's tab lands on the same spot. Vanilla
  leaves exactly one free position in that row, so two mods adding a tab both take it and their icons draw on
  top of each other — with Packwisely, you had to guess which half of the icon to click. The row is now laid
  out when the screen opens, and only when icons actually overlap: a row that already reads fine is left alone.
- Icons in a crowded row stay easy to hit: each one keeps a clickable area the size of its place in the row, so
  hovering and clicking work across the whole icon rather than a small square in the middle of it.

## 0.1.0 — 2026-09-17

- First version: an Accessories tab on the character screen with necklace, bracelet and two ring slots by
  default. Other mods add or change slots from their own `Config/accessoryslots.xml`, and a slot only shows once
  an installed item uses it (`<property name="AccessorySlot" value="..."/>`).
- Worn accessories give their bonuses like armor, fire equip/unequip events, and are synced to the server and
  other players.
- Worn accessories follow the world's armor rules on death and quit (Drop On Death, Drop On Quit, Lose Items On
  Death, Degrade Items On Death).
- Saved inside the player's own save; saves still load with the mod removed. Items in a slot that no longer
  exists are kept.
- Joining a server without the mod still works (the tab stays hidden).
- Worn items are saved with their names and found by name on load, so adding or removing mods with items
  can never turn a worn accessory into a different item.
- Accessory Slots' own slots always come first on the tab; slots other mods add follow them.
- The tab has its own icon (an outlined breastplate with a plus) and keeps the character screen's tab row
  evenly spaced.
- `acs` console command with a headless selftest.
- `Accessories.AddToSaveData` for mods moving their own older save data into a slot.
- First mod using it: Glider (its glider slot).
