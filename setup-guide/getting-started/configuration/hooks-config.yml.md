---
description: Contains options for plugin hooks.
icon: anchor
---

# hooks-config.yml

MyPet hooks into a lot of plugins ([list](../plugin-hooks/)). Some of these hooks simply make MyPet compatible with other plugins and others provide custom settings you can change.

The `hooks-config.yml` is automatically generated and updated on plugin start when the plugin detects other compatible plugins that it hooks into. These are enabled by default and populated with all options with placeholder values.

The lists below show only the custom settings that you are able to modify. Remember that not all values will be present if MyPet is not able to detect the plugin on your system.

### Hooks

* #### AncientRPG
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of the AncientRPG plugin like parties. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### BattleArena
  * Options:&#x20;
    * DisablePetsInArena
      * Type: boolean
      * Description: Disables MyPets in the arenas completely.
* #### Citizens
  * Type: boolean
  * Description: Checks whether the target NPC can be damaged by a MyPet. NPCs can't be leashed.
* #### Factions
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of the Factions plugin. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### GriefPrevention
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of GriefPrevention. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### Heroes
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of the Heroes plugin like minimum PvP level or parties. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### MCMMO
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of the MCMMO plugin like parties. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### Minigames
  * Options:
    * DisablePetsInGames
      * Type: boolean
      * Description: Disables MyPets in any minigame completely.
* #### MobArena
  * Options:
    * Enabled
      * Type: boolean
      * Description: Enables the MobArena hook. (This allows the pet to deal damage in arenas)
    * RespectPvPRule
      * Type: boolean
      * Description: If true, pets will respect the PvP rules of an arena. If the owner of a pet can attack a player, the MyPet can attack this player too.
    * AllowPets
      * Type: boolean
      * Description: If true, pets will be able to enter arenas.
* #### MyHungerGames
  * Options:
    * DisablePetsInGames
      * Type: boolean
      * Description: Disables MyPets in survival game matches completely.
* #### PvPArena
  * Options:
    * PvP
      * Type: boolean
      * Description: Checks whether the MyPet owner can attack a target player inside an arena. If the owner of a pet can attack a player, the MyPet can attack this player too.
    * DisablePetsInArena
      * Type: boolean
      * Description: Disables MyPets in the arenas completely.
* #### PvPManager
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of PvPManager. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### Residence
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of Residence. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### SkillAPI
  * Options:
    * GrantExp
      * Type: boolean
      * Description: This setting allows pets to gain XP when the owner gains SkillAPI XP.
    * Disable-Vanilla-Exp
      * Type: boolean
      * Description: This setting disables XP gain from normal sources entirely. The only way pets can get any XP is when the owner gets XP via SkillAPI.
* #### SurvivalGames
  * Options:
    * PvP
      * Type: boolean
      * Description: Checks whether the MyPet owner can attack a target player inside a survival game match. If the owner of a pet can attack a player, the MyPet can attack this player too.
    * DisablePetsInGames
      * Type: boolean
      * Description: Disables MyPets in survival game matches completely.
* #### Towny
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of the Towny plugin. If the owner of a pet can attack a player, the MyPet can attack this player too.
* #### Vault
  * Options:
    * Economy
      * Type: boolean
      * Description: Enables the economy support. Used by trading, respawning and storing pets.
* #### WorldGuard
  * Type: boolean
  * Description: Checks whether the MyPet owner can attack a target player following the rules of WorldGuard region flags. If the owner of a pet can attack a player, the MyPet can attack this player too.
