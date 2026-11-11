# REMS Fishing changelog

## 1.0.0

The first public release, for 7 Days to Die V3.4. Everything below is new.

### Angling

- Tap for a short cast or hold to charge a long one. An aim marker and one aim line show where the float lands and
  whether the water there can be fished.
- A controls line under the aim line shows cast, bait and lures, and the journal key while you wait.
- Bait and lures go on the rod, like ammo. The rod's Modify screen has a Tackle panel with a Bait slot for one stack
  of bait and a Lure slot for one lure. A loaded lure is cast instead of bait. Hold Reload with the rod out to open a
  wheel of the bait and lures you carry. Choosing one loads it and returns the old one to your pack. Choosing bait
  also removes the lure. Tap Reload to top up the bait. Bait refills automatically with the same kind from your pack.
  Casting with an empty rod loads the first bait you carry, or the first lure if you have no bait. The ammo counter
  shows bait on the rod / in your pack, or an infinity sign for a lure.
- Each bite uses one bait from the rod, even if you miss. Reel in before a bite and you keep it. Lures aren't used up
  and are only lost if the line snaps. Scrapping, selling or combining a rod returns its tackle to your pack. The
  server checks the rod's tackle when you cast.
- Strike when the float goes under, then fight the fish with your stamina against its runs and the line tension.
  Easing off recovers stamina. Reel input can be Hold or Toggle.
- Lean against a run by holding the strafe key (A or D) on the side away from it. While a fish is on, A and D lean
  instead of moving you.
- A catch card shows the species, weight and length. Keep the fish or release it. Catches of 8 kg or more are pulled
  up the bank.
- The Standard rod and the Precision rod, with six quality levels each.
- Four baits, four lures and eight rod mods.
- Water has a productivity meter: kept catches draw it down and it recovers over time. Swimming near the float, and
  gunshots or explosions nearby, spook the fish for a minute.

### Catches and food

- Ten fish plus the eel, two crayfish, crab, shrimp, two turtles, clams, mussels, snails and two frogs, each with its
  own biomes, depths, times and liked baits. The top 5% of a species' weight range is a trophy.
- Clean and fillet catches, then cook them into fish meals.

### Fishing Trap

- Bait it and leave it in water at least one block deep. It has one catch chance every 4 in-game hours, and catches
  up to 48 hours when its area loads again.
- One bait pays for one catch; a miss uses none.
- The trap opens its own window: the bait slot, what lives in that water and how likely each catch is, the catch
  grid, and tiles for the catch count, the time to the next check (with a timer bar), the water and its fish stock.
  Hover a tile for the full sentence. Shift-click puts bait or a trap mod straight into the trap; Take Catch empties it.
- Three trap mods, crafted at a workbench from Fishing 10, 20 and 30: the Funnel Entrance (+25% catch chance), the Bait
  Box (40% of catches keep their bait) and the Bigger Cage (holds 10 catches instead of 6).
- Trap catches are juveniles, within each species' trap size cap.
- Traps in the same water share what it can give, and a fished-out area catches less.

### Shoreline

- Clam beds, mussel beds and snail patches in shallow water. Each gives three gathers, then renews after three days.
- Frogs on the bank at dusk and night. Catch them by hand, or swing the Dip Net at them from a few metres away.
- Swing the Dip Net through shallow water near the bank to scoop up shrimp, crayfish and small panfish.

### Stocked ponds

- Dig and fill a pond at least 7 by 7 and 3 deep, place a Pond Marker at its edge and release fingerlings from
  traders. Each species settles in for three days.
- A stocked pond belongs to whoever stocked it. Its fish bite for them, their allies and party, and players with
  build rights in a land claim around it. Anyone else fishing there catches wild fish only.

### Progression and goals

- The Fishing crafting skill (Angler's Monthly magazines, levels 1 to 50).
- The Patient Angler: seven books with technique bonuses, and Master Angler for reading them all.
- The Fishing Jobs board at every trader, with Angler standing ranks 1 to 5.
- A REMS Fishing challenge category with six chapters, and a seventh with REMS Culinary Hearth installed.
- The Fishing Journal (press J).

### Junk and treasure

- Rod bites can bring up junk or a Waterlogged Strongbox. Rates, trap salvage and the strongbox's rewards are world
  settings, with Gears or in `ModSettings.xml`, and each junk item and strongbox has its own switch.

### Settings

- Your own options: reel input, the fish stamina bar, the bite ring size, the catch card, key hints, first-time tips
  and the fight panel's position.
- World rules for the host or server: junk and treasure, trap salvage, the trap check interval and catch-up limit,
  trap mods, Dip Net scooping, catch amount, frogs, gathering beds, Fishing Jobs and whether chances show as numbers.

### Multiplayer

- The server decides every catch, trap catch, gather, pond fish and job reward. Rewards are tied to ids the server
  hands out, so nothing is paid twice.
- A trap catch counts toward challenges only if the trap caught it. The server keeps that record, so catches a
  player put in themselves never count, across relogs and between players.
- A pond release the player's game could not complete (the jar left the inventory in the meantime) is undone on the
  server.
