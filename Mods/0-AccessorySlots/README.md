# Accessory Slots

Extra equipment slots on a new **Accessories** tab of the character screen. By default: a necklace, a
bracelet and two rings, always on the tab under **Jewelry** so players know they are there - faded, with a
note on hover, until an installed mod adds something that goes in them. Other mods can add their own slots (a
glider, a harness, a belt...); those appear under **From other mods** once an installed item goes in them.

Worn accessories work like armor:

- their bonuses count, the same way armor bonuses do (they are ordinary `passive_effect` / `triggered_effect`
  XML on the item);
- they follow your world's armor rules on death and on quit - **Drop On Death**, **Drop On Quit**, **Lose Items
  On Death**, **Degrade Items On Death**: if armor drops, so do they; if armor stays on you, so do they;
- other players see what you wear (it is synced like armor), and the server counts it too (loot stage, for example);
- an item can show on your character while worn - a ring on your finger, a pendant on your chest - if the mod that
  adds it gives it a model (see "A model on the character").

**This is a framework.** On its own it adds no items. Install it for a mod that uses it.

## Install

Extract into `Mods/` so the folder is named **`0-AccessorySlots`** - the name matters: mods that use it must
load after it, and the game loads mods in folder-name order.

Server **and** every client. DLL mod, so the game must be launched with **EAC off**. A player without it
cannot join a server that has it (the game refuses the connection with an unknown-package message). A player
with it can still join servers that do not have it; the tab just stays hidden there.

Game V3.0.0 - V3.3.0.

What you wear is saved inside your own player save. If you uninstall the mod, saves still load and only the
worn accessories are lost - take them off first to keep them. If you uninstall a mod that ADDED a slot, what
was in that slot is kept, hidden, and comes back if you reinstall it.

## Using it

Open the character screen and pick the tab with the armor-and-plus icon (next to Gear). Drag an accessory onto its
slot, or shift-click it in your backpack while the character screen is open. Click a worn accessory for its
details and to Modify it, like worn armor.

## For server admins

Change the slots from your own small mod's `Config/accessoryslots.xml`, e.g. four rings and no bracelet:

```xml
<configs>
    <set xpath="/accessoryslots/slot[@name='ring']/@count">4</set>
    <remove xpath="/accessoryslots/slot[@name='bracelet']"/>
</configs>
```

Lowering a count never deletes anything: what was in a slot that no longer exists stays in the player's save,
does nothing, and comes back when the slot does. `keep_on_death="true"` exempts a slot from the death rules.

The jewelry slots show even when no installed mod adds jewelry. To hide them on a server that has none, remove
them the same way (`<remove xpath="/accessoryslots/slot[@name='necklace']"/>`, and so on).

## For modders

**Add items** - one property puts an item in a slot:

```xml
<item name="myRingOfSpeed">
    ...
    <property name="AccessorySlot" value="ring"/>
    <effect_group tiered="false">
        <passive_effect name="RunSpeed" operation="perc_add" value="0.1"/>
    </effect_group>
</item>
```

**An item that fits more than one slot** lists them, comma-separated, the one it prefers first:

```xml
<property name="AccessorySlot" value="ring,necklace"/>   <!-- a charm worn on a finger or on a chain -->
```

It can be dragged onto any of them. Shift-click puts it in the first empty one in that order, and only when all
of them are full does it swap out what is in the first.

**Two of the same item** - the built-in necklace, bracelet and ring slots take one of each item (`unique` on the
slot). An item can decide for itself, and its say beats the slot's:

```xml
<property name="AccessoryUnique" value="false"/>   <!-- two of these rings may be worn together -->
<property name="AccessoryUnique" value="true"/>    <!-- only one of these on you, in any of its slots -->
```

Leave it out and the slot decides, as before. It sits on the item so that mods sharing the ring slots each decide
for their own rings: one mod letting its rings stack does not let another mod's rings stack. Two of the same item
add their bonuses together. An item that gives its bonus by adding a buff on `onSelfEquipStart` and removing it on
`onSelfEquipStop` loses that buff as soon as either copy comes off, so give stackable items `passive_effect`s.

**Add a slot** - in your mod's `Config/accessoryslots.xml`:

```xml
<configs>
    <append xpath="/accessoryslots">
        <slot name="glider" group="gear" order="100" icon="myEmptyGliderIcon" label="lblMyGliderSlot"/>
    </append>
</configs>
```

| Attribute | |
|---|---|
| `name` | required; no `#` or `,`. Items claim the slot by this name. |
| `aliases` | other names for the same slot, comma-separated: an item claiming one goes in this slot, and anything saved under one moves here. A name that some slot declares is never an alias. |
| `count` | how many (keys `name#1` ... `name#count`), default 1, max 8 |
| `group`, `order` | layout: Accessory Slots' own slots always come first, then slots mods add, grouped by `group` (sorted by name), then by `order` |
| `icon` | ItemIconAtlas sprite for the empty slot |
| `label` | localization key for the empty slot's tooltip |
| `unique` | `true`: no two of the same item across the slot's copies - for items without their own `AccessoryUnique` |
| `keep_on_death` | `true`: exempt from the death and quit rules |
| `bone` | where a model worn here hangs (see below), one bone per copy: `bone="LeftHandRing1,RightHandRing1"`; a copy past the list uses the last; a copy on the first one's Left/Right twin shows the mirror image |

Use the default names (`necklace`, `bracelet`, `ring`) for jewelry so different mods' rings share the same two
ring slots. They are the names Minecraft's Curios uses, so a modder who knows it guesses right; the body part
works too - `neck`, `wrist` and `finger` are aliases of the same three slots. An item that claims a slot nobody
declared still works: the slot is created from the item itself.

### A model on the character

An item can show on the player while it is worn - a ring on a finger, a pendant on the chest - for you in third
person and for everyone who can see you. Make the model in Unity, put it in an asset bundle in your mod, and
name it on the item:

```xml
<property name="AccessoryModel" value="#@modfolder:Resources/myjewelry.unity3d?SilverRing"/>
<property name="AccessoryModelOffset" value="0,0.02,0"/>     <!-- metres, in the bone's own axes; default 0,0,0 -->
<property name="AccessoryModelRotation" value="0,0,90"/>     <!-- degrees; default 0,0,0 -->
<property name="AccessoryModelScale" value="1"/>             <!-- one number or x,y,z; default 1 -->
<property name="AccessoryModelBone" value="Head"/>           <!-- optional: otherwise the slot's own bone -->
```

The model hangs on a bone of the player's skeleton and moves with it. Each slot names its bone: `necklace` on
`Neck`, `bracelet` on the left wrist (`LeftHand`), the first `ring` on the left ring finger (`LeftHandRing1`) and
the second on the right (`RightHandRing1`). A slot your mod adds names its own with `bone="..."`; an item names
one for itself with `AccessoryModelBone`, which wins.

**Left and right:** the body's left and right bones are mirror images, so one set of numbers cannot fit both hands.
Place your model on the slot's **first** copy (the left ring finger); a later copy whose bone is the first one's
Left/Right twin (`RightHandRing1` for `LeftHandRing1`) shows the exact mirror image by itself. An item that names
its own `AccessoryModelBone` is never mirrored - its numbers are for that bone.

**A complete example to copy:** Glider (0.3.0+) shows each glider packed on your back while it is worn - a slot
`bone`, five items with `AccessoryModel`, one Linear-built bundle, and a few lines that hide the pack while the
glider is open (`HideModel`, below). Glider's README walks through it.

Placing it, in game (`acs` is the console command):

- `acs model bones` lists the bone names (`acs model bones hand` only those with "hand" in them).
- `acs model bone LeftHandRing1` says which way that bone's local x, y and z point on the body - which axis runs
  along the finger.
- `acs model set ring#1 offset 0,0.02,0` (or `rotation`, `scale`) moves your worn model at once, and every copy of
  that item on anyone else, for the rest of the session. Wear the item in the first ring slot while you place it.
- `acs model xml` prints the property lines with the numbers you settled on, to paste into your `items.xml`.
- `acs model` lists every model on every loaded player and why one is not showing.

Making the model:

- **Unity 2022.3.62f2**, the game's own version. **Linear colour space** - a bundle built in Gamma looks pale
  and hazy in game. Build for Windows with Direct3D 11, Vulkan and OpenGL so it renders for Windows and Linux
  players (macOS players will not see it).
- The prefab's origin is the point that sits on the bone; 1 unit = 1 metre. A ring around a 2 cm finger is about
  that size. Bones run through the middle of the body: at offset 0 a model sits inside the skin. The `Neck` bone is
  inside the base of the neck - a necklace needs to come up and forward from it (the test necklace: up 2 cm,
  forward 5 cm).
- A rigid model: it follows the bone but does not bend. Clothing that bends with the body is the game's own gear
  system, not this.
- Colliders and rigidbodies in the prefab are removed - it is a picture, so bullets and walls ignore it.
- On your own player it is hidden in first person (the third-person body stands still there, so the model would
  hang beside the camera). The character-screen preview does not show it.
- A model that will not load, or a bone that does not exist, writes one warning to the log; the item still works.

Every client needs your bundle, so a mod with models is installed on clients like any mod with assets. Mods that
already hang things on the body with the game's own `AddPart` triggered effect on `onSelfEquipStart` keep working,
and since 0.6.0 those parts come back after switching between first and third person too.

**From code** - reference `AccessorySlots.dll` (your mod's folder must sort after `0-AccessorySlots`):

```csharp
ItemValue worn = AccessorySlots.Accessories.Get(player, "glider");      // index 1, null if nothing / not worn
AccessorySlots.Accessories.Changed += (player, key, before, after) => { /* key like "ring#2" */ };
AccessorySlots.Accessories.Set(localPlayer, "glider#1", itemValue);     // checks slot and unique rules
IReadOnlyList<string> slots = AccessorySlots.Accessories.SlotsFor(itemValue);   // e.g. ring, necklace
bool fits = AccessorySlots.Accessories.Fits(itemValue, "necklace");
GameObject model = AccessorySlots.Accessories.Model(player, "ring", 2);   // the worn model, null if none
AccessorySlots.Accessories.HideModel(player, "glider", 1, true);          // hide it for now (e.g. while in use)
```

`HideModel` is for an item that is sometimes drawn some other way: Glider shows a packed glider on your back
while it is worn, and hides it while the glider is open and drawn by Glider itself. The hide holds when the body is
rebuilt; each client draws every player itself, so call it on every client that should hide it.

A slot's alias works anywhere its name does (`Get(player, "finger")` reads `ring#1`).

**Moving your own older save data in** - if your mod stored an item in the player save itself before, read
it in a `PlayerDataFile.Read` postfix and hand it over; it arrives in the slot as if it had been saved there:

```csharp
AccessorySlots.Accessories.AddToSaveData(__instance, "glider#1", itemValue);
```

## Console

`acs` (or `accessoryslots`): used slots and what you wear. `acs defs`: every slot definition. `acs check`: patch
status. `acs icons`: each slot's empty-slot picture and whether your game has it (add it to a bug report about a
blank slot). `acs selftest`: a save/network/effects self-check, results in the log. `acs model ...`: placing a
model on the character (see above).

## Compatibility

Languages: English and Russian. The tab, its headings, the jewelry slot names and its messages follow the
game's language; the name of an item, or of a slot another mod adds, comes from that mod's own
`Localization.csv`.

The tab is added with two XML appends. The only vanilla values it changes are the x positions of the two stats
tab icons and the movement toggle, moved 20 px right so every icon on the header is evenly spaced, and only
while they are still where vanilla puts them. A UI overhaul that replaces the whole character window can still
hide the tab; slots, bonuses and saves keep working regardless.

The slot file is not added to the game's own list of config files: Accessory Slots reads it and sends it to
clients itself, so it cannot clash with another mod that rewrites the game's config-sending code.

## Thanks

To **Laydor**, author of [Gears](https://github.com/s7092910/Gears): from 0.4.0 the slot file reaches clients
the way Gears carries its own settings file. That route is Gears' idea, used here with credit.

## License

All rights reserved, with permissions - see [LICENSE](LICENSE). Building mods that use Accessory Slots is
explicitly allowed; bundling a copy of it in your download is not.
