FLAMETHROWER TURRET - SOURCE HOTFIX
Version 1.1.1 for 7 Days to Die 3.0

THIS ARCHIVE CONTAINS NO DLL

It contains the three C# source files, project file and corrected XML configuration.
Compile it locally against the matching 7 Days to Die 3.0 and 0_TFP_Harmony assemblies.
Single-player, the listen server, the dedicated server and every connecting client must use
the same compiled build and configuration.

FIXES IN 1.1.1

- Restored the original working hit-volume defaults for held and deployed flame turrets.
- Deployed flame turrets can damage and ignite zombies and players.
- Powered flame traps can ignite players again.
- Removed the drone flamethrower's custom movement, path clearing and forced Attack state.
  Vanilla drone AI now owns Follow, Sentry and all navigation at all times.
- Added a dedicated, saved flame-fuel reservoir to the drone (maximum 10,000 units).
- Added a Flame fuel [REFUEL] row to the drone modification window. Click the row to move
  Gas Cans from the player's inventory into the reservoir.
- Refuelling and fuel consumption are authoritative on the server and synchronized to clients.
- The vanilla drone weapon model remains visible while a flamethrower module is installed.

IMPORTANT

The flame-fuel row is shown only when one of the three drone flamethrower modules is installed.
Normal drone cargo slots are no longer used as live ammunition slots by the flamethrower.
