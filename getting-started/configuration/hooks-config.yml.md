---
description: Contains options for plugin hooks.
icon: anchor
---

# hooks-config.yml

MyPet hooks into a lot of plugins (https://wiki.mypet-plugin.de/hooks). Some of these hooks simply make MyPet compatible with other plugins and others provide custom settings you can change.

The lists below show only the custom settings.

## Hooks Settings

### Hooks

* AncientRPG (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of the AncientRPG plugin like parties. If the owner of a pet can attack a player, the MyPet can attack this player too.
* Towny (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of the Towny plugin. If the owner of a pet can attack a player, the MyPet can attack this player too.
* MCMMO (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of the MCMMO plugin like parties. If the owner of a pet can attack a player, the MyPet can attack this player too.
* Factions (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of the Factions plugin. If the owner of a pet can attack a player, the MyPet can attack this player too.
* Heroes (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of the Heroes plugin like minimum PvP level or parties. If the owner of a pet can attack a player, the MyPet can attack this player too.
* WorldGuard (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of WorldGuard like region flags. If the owner of a pet can attack a player, the MyPet can attack this player too.
* Residence (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of Residence. If the owner of a pet can attack a player, the MyPet can attack this player too.
* GriefPrevention (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of GriefPrevention. If the owner of a pet can attack a player, the MyPet can attack this player too.
* PvPManager (boolean)\
  Checks whether the MyPet owner can attack a target player following the rules of PvPManager. If the owner of a pet can attack a player, the MyPet can attack this player too.
* Citizens (boolean)\
  Checks whether the target NPC can be damaged by a MyPet. NPCs can't be leashed.

### MobArena

* Enabled (boolean)\
  Enables the MobArena hook. (This allows the pet to deal damage in arenas)
* RespectPvPRule (boolean)\
  If true, pets will respect the PvP rules of an arena. If the owner of a pet can attack a player, the MyPet can attack this player too.
* AllowPets (boolean)\
  If true, pets will be able to enter arenas.

### Minigames

* DisablePetsInGames (boolean)\
  Disables MyPets in any minigame completely.

### PvPArena

* PvP (boolean)\
  Checks whether the MyPet owner can attack a target player inside an arena. If the owner of a pet can attack a player, the MyPet can attack this player too.
* DisablePetsInArena (boolean)\
  Disables MyPets in the arenas completely.

### SurvivalGames

* PvP (boolean)\
  Checks whether the MyPet owner can attack a target player inside a survival game match. If the owner of a pet can attack a player, the MyPet can attack this player too.
* DisablePetsInGames (boolean)\
  Disables MyPets in survival game matches completely.

### MyHungerGames

* DisablePetsInGames (boolean)\
  Disables MyPets in survival game matches completely.

### BattleArena

* DisablePetsInArena (boolean)\
  Disables MyPets in the arenas completely.

### Vault

* Economy (boolean)\
  Enables the economy support. Used by trading, respawning and storing pets.

### SkillAPI

* GrantExp (boolean)\
  This setting allows pets to gain XP when the owner gains SkillAPI XP.
* Disable-Vanilla-Exp (boolean)\
  This setting disables XP gain from normal sources entirely. The only way pets can get any XP is when the owner gets XP via SkillAPI.

### Reference

* Hooks list: https://wiki.mypet-plugin.de/hooks
