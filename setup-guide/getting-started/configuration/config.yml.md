---
description: MyPet's main config file.
icon: gear
---

# config.yml

The `config.yml` file is the main config file of MyPet. All pet type related options can be found in the [pet-config.yml](pet-config.yml/).

Below are the available settings, their types and descriptions.

***

## MyPet:

### Disable-All-Actionbar-Messages

* Type: boolean
* Description: If true, no action bar messages will be used.

### Recall-Pet-After-Despawn

* Type: boolean
* Description: Not yet documented.

### PetKillsGivePlayerRewards

* Type: boolean
* Description: When true, mobs killed by a MyPet will drop experience and loot as if killed by a player.

### OwnerCanAttackPet

* Type: boolean
* Description: Enable to allow the owner to hit their own pet.

### DisablePetVersusPlayer

* Type: boolean
* Description: Prevents combat between players and pets.

### Make-Pet-Invisible-When-Owner-Is-Invisible

* Type: boolean
* Description: Makes the pet invisible when the owner has the `Invisible` effect. Does not affect vanished players.

### RetainEquipmentOnTame

* Type: boolean
* Description: Allows mobs to keep their equipment after leashed (based on the default MC drop chance).

### FollowStartDistance

* Type: double
* Description: Sets the distance from the player where the pet starts to follow him.

### Max-Stored-Pet-Count

* Type: integer
* Description: Sets the maximum amount of inactive ([stored](../systems/pet-storage.md)) pets a player can have.

### Throw-PlayerMoveEvent-While-Riding

* Type: boolean
* Description: Disable this when other plugins cause bugs because of the thrown events.

### OverwriteLanguages

* Type: string
* Description: If you don't want per player language detection you can use this to overwrite the language for all players. Available languages can be found [here](https://github.com/MyPetORG/MyPet-Translations).\
  Example: `pt_br`

### Right-Click-Command

* Type: string
* Description: A command that will be executed when a player right clicks their own pet. Supports the following placeholders:
  * `%pet_owner%`
  * `%pet_level%`
  * `%pet_status%`
  * `%pet_type%`
  * `%pet_uuid%`
  * `%pet_world_group%`
  * `%pet_skilltree_name%`
  * `%pet_name%`

***

### Entity

* Skip-Target-AI-Ticks
  * Type: integer
  * Default: 1
  * Description: The default value of 1 will skip every 2nd AI tick. Carefully increasing the value will skip the set number of server ticks, decreasing load on the server, at the cost of tracking behavior.
* FollowStartDistance
  * Type: double
  * Description: Distance at which the pet begins to follow the player.

***

### Leash

* #### Consume
  * Type: boolean
  * Description: Enable to consume the leash item when a new pet is leashed.
* #### AllowRanged
  * Type: boolean
  * Description: Enable to allow players to catch pets with projectiles when the leash item is a bow.

***

### Log

* #### Level
  * Type: string
  * Description: Set the level at which the messages will be logged to the file. [All possible log levels](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Level.html#field_summary).
* #### Report-Errors:
  * Type: boolean
  * Description: If enabled all errors that occur are reported automatically.
* #### Unique-ID
  * Type: string
  * Description: This is used to identify different users for the error reporter. This will allow the devs to see how many servers have the same problem.

{% hint style="warning" %}
❗ DO NOT CHANGE THE UNIQUE-ID STRING ❗
{% endhint %}

***

### Info

* #### Wiki-URL
  * Type: string
  * Description: This can be changed if the server has it's own Wiki for MyPet.

***

### Update

* #### Check
  * Type: boolean
  * Description: Sets if the plugin will check for updates when it is loaded. This will not download the new version.
* #### Download
  * Type: boolean
  * Description: Sets if the plugin will download the update. The downloaded jar is loaded automatically on the next server start.
* #### In-Background
  * Type: boolean
  * Description: If true the plugin will not wait until the update is downloaded on start.
* #### OP-Notification
  * Type: boolean
  * Description: If true, the plugin will notify OPs if a new version is available.

***

### Repository

* Type
  * Type: string
  * Description: The storage type where the plugin will save the pets into. Options: `SQLite`, `MySQL`, `MongoDB`.
* ConvertFrom
  * Type: string
  * Description: This option allows to migrate from one storage type to another. For example from `SQLite` to `MySQL`.
* LoadDelay
  * Type: string
  * Description: Delays database initialization.

#### MySQL

* Database
  * Type: string
  * Description: The name of the MySQL database.
* TablePrefix
  * Type: string
  * Description: The table prefix if the database is shared with other applications.
* Host
  * Type: string
  * Description: The address of the MySQL server.
* Port
  * Type: integer
  * Description: The port of the MySQL server.
* Password
  * Type: string
  * Description: The password of the MySQL user.
* User
  * Type: string
  * Description: The username of the MySQL user.
* MaxConnections
  * Type: integer
  * Description: The amount of simultaneous connections the plugin will create to the MySQL server. [More about pool sizing](https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing).
* CharacterEncoding
  * Type: string
  * Description: The encoding used by the database.

#### MongoDB

* Database
  * Type: string
  * Description: The name of the MongoDB database.
* CollectionPrefix
  * Type: string
  * Description: The collection prefix if the database is shared with other applications.
* Host
  * Type: string
  * Description: The address of the MongoDB server.
* Port
  * Type: integer
  * Description: The port of the MongoDB server.
* Password
  * Type: string
  * Description: The password of the MongoDB user.
* User
  * Type: string
  * Description: The username of the MongoDB user.

***

### Respawn

#### Time → Default

* Factor
  * Type: integer
  * Description: Determines how long the owner has to wait until the pet respawns when it wasn't killed by a player.\
    Formula: `Respawntime = Factor * (Level of MyPet) + Fixed`
* Fixed
  * Type: integer
  * Description: See `Factor`

#### Time → Player

* Factor
  * Type: integer
  * Description: Determines how long the owner has to wait until the pet respawns when it was killed by a player.\
    Formula: `Respawntime = Factor * (Level of MyPet) + Fixed`
* Fixed
  * Type: integer
  * Description: See `Factor`

#### EconomyCost

* Factor
  * Type: double
  * Description: Determines how much it will cost to revive a dead MyPet.\
    Formula: `Costs = Factor * (Respawn Time in sec.) + Fixed`
* Fixed
  * Type: double
  * Description: See `Factor`

***

### Permissions

* Enabled
  * Type: boolean
  * Description: Disable the use of permissions and fall back to the OP permission system. (https://wiki.mypet-plugin.de/setup/permissions)
* Extended
  * Type: boolean
  * Description: Enable if you want to use some additional permissions: https://wiki.mypet-plugin.de/setup/permissions#extended-mypet-permissions
* Legacy
  * Type: boolean
  * Description: Set to true to use permissions nodes from versions prior to MyPet 3.0. Not recommended.

***

### LevelSystem

* CalculationMode
  * Type: string
  * Default: "Default"
  * Description: Which curve decides how much experience a pet needs per level. One of `Default` (also accepted as `MyPet`), `Linear`, `Power` or `Exponential`. Not case-sensitive. Unknown values fall back to `Default`. [More here](../systems/experience/).
* #### Curve
  * Only the settings of the selected `CalculationMode` are used. `Default` has no settings.
  * Linear.Base
    * Type: double
    * Default: 17.0
    * Description: Experience needed for each level, when `CalculationMode` is `Linear`.
  * Power.Factor
    * Type: double
    * Default: 7.0
    * Description: Scales the whole curve, when `CalculationMode` is `Power`.
  * Power.Exponent
    * Type: double
    * Default: 1.5
    * Description: How sharply the cost accelerates, when `CalculationMode` is `Power`. `1.0` behaves like `Linear`.
  * Exponential.Base
    * Type: double
    * Default: 10.0
    * Description: Experience needed for level 2, when `CalculationMode` is `Exponential`.
  * Exponential.Growth
    * Type: double
    * Default: 1.1
    * Description: Cost multiplier per level, when `CalculationMode` is `Exponential`. `1.1` means each level costs 10% more than the last.

***

### HungerSystem

* Feed-From-Inventory
  * Type: boolean
  * Description: When true, allows pets to feed themselves from items stored in their inventories which are a configured food for that pet type.
* #### Damage
  * Time-Before-Damage
    * Type: double
    * Description: Provides a grace period before hunger related damage will be dealt to the pet.
  * Fixed
    * Type: double
    * Description: Base damage applied with each damage tick while starving.
  * Factor
    * Type: double
    * Description: Additional scaling damage component. If set to `0.0` (default), damage is purely Fixed.
  * can-kill
    * Type: boolean
    * Description: When set to true, damage dealt to a pet from hunger will be able to kill the pet.
* Active
  * Type: boolean
  * Description: Disable the [hunger system](../systems/hunger-system.md) if you don't want your pets to need food to survive.
* Time
  * Type: integer
  * Description: Sets the interval (in seconds) in which the hunger counter will be reduced by `1`.
* SaturationPerFeed
  * Type: double
  * Description: Sets the value the hunger counter will be increased by if the pet is fed.
* Affect-Ride-Speed
  * Type: boolean
  * Description: If true the [saturation](../systems/hunger-system.md) affects the ride speed.
* Affect-Beacon-Range
  * Type: boolean
  * Description: If true the [saturation](../systems/hunger-system.md) affects the beacon range.

***

### Skilltree

* AutomaticAssignment
  * Type: boolean
  * Description: Enable to automatically assign a skilltree to a pet when it is leashed.
* RandomAssignment
  * Type: boolean
  * Description: Like `AutomaticAssignment` but the skilltree is selected randomly.
* ChooseOnce
  * Type: boolean
  * Description: Enable this if players shouldn't be able to pick another skilltree once the pet has a skilltree.
* PreventLevellingWithout
  * Type: boolean
  * Description: Pets without a skilltree will not gain XP if it is set to `true`.

#### SwitchFee

* Admin
  * Type: boolean
  * Description: Set this to `true` if admins should pay the same skilltree switch penalty like normal players.
* Percent
  * Type: integer
  * Description: The percentage of XP a player has to pay if they switch to another skilltree.
* Fixed
  * Type: double
  * Description: The amount of XP a player has to pay if they switch to another skilltree.

***

### Name

* Filter
  * Type: list
  * Description: Every pet name is checked against this list of filters (string/regular expression).
* MaxLength
  * Type: integer
  * Description: The maximum length a pet name can have.

#### Tag

* Show
  * Type: boolean
  * Description: Set this to `false` if you don't want nametags for MyPets.
* Prefix
  * Type: string
  * Description: This text will be added in front of the name. You can use color codes and these placeholders:
    * `<owner>` ⇒ name of the owner
    * `<level>` ⇒ level of the pet
* Suffix
  * Type: string
  * Description: This text will be added to the end of the name. You can use color codes and these placeholders:
    * `<owner>` ⇒ name of the owner
    * `<level>` ⇒ level of the pet

***

### Exp

* DamageWeightedExperienceDistribution
  * Type: boolean
  * Description: Allows pets to gain XP even if they did not kill the enemy. Every bit of damage is counted and when the enemy dies the XP will be split up to reflect the damage given. Example: If a pet does 50% of the damage it will gain 50% of the total XP.
* LevelCap
  * Type: integer
  * Description: The maximum level at which a pet can accrue experience.
* Disabled-Worlds
  * Type: list
  * Description: List of worlds where experience cannot be gained by the pet.

#### Passive

* Always-Grant-Passive-XP
  * Type: boolean
  * Description: Allows the pet to always gain XP when the owner kills a monster, even if it has a damage skill (Damage or Ranged).
* PercentPerMonster
  * Type: integer
  * Description: Sets the percentage of XP a pet will get when the owner kills an enemy.

#### Loss

* Drop
  * Type: boolean
  * Description: If true the lost XP is dropped on the ground and can be picked up by others.
* Percent
  * Type: integer
  * Description: Sets the percentage of XP a pet will lose when it dies.
* Fixed
  * Type: double
  * Description: Sets the XP a pet will lose when it dies.
* Allow-Level-Downgrade
  * Type: boolean
  * Description: If true pets can lose levels if they die.

#### Gain

* PreventFromSpawnReason
  * Type: list
  * Description: A list of spawn reasons; mobs spawned by any of these reasons will not grant any XP. [All spawn reasons](https://jd.papermc.io/paper/1.21.11/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html#enum-constant-summary).\
    Note: This resets on every server reload/restart so it will not prevent it after a restart!
* LevelCap
  * Type: integer
  * Description: A pet cannot gain any XP or level up if this level is reached.
* Disabled-Worlds
  * Type: list
  * Description: A list of worlds where pets can't gain any XP.

#### Modifier

* Global
  * Type: double
  * Description: The global XP modifier. 1.0 equals 100% XP; 2.0 equals 200% XP.
* Use-Permissions
  * Type: boolean
  * Description: If true, the modifier can be changed via permissions too. See: https://wiki.mypet-plugin.de/setup/permissions

***

### Skill

* [Control](../../skilltree-creation/creating-custom-skilltrees/skills/control.md)
  * Item
    * Type: string
    * Description: Sets the item that allows the player to use the Control skill on the pet. Follows the [config item](custom-item-data-in-config.md) guidelines.
* [Ride](../../skilltree-creation/creating-custom-skilltrees/skills/ride.md)
  * Item
    * Type: string
    * Description: Sets the item that allows the player to mount the pet. Follows the [config item](custom-item-data-in-config.md) guidelines.
  * HungerPerMeter
    * Type: double
    * Description: If the Hunger-System is active, sets how much hunger is decreased for every ridden meter.
  * Prevent-Teleportation-While-Riding
    * Type: boolean
    * Description: When true, prevents the player from teleporting while riding a pet.
* [Backpack](../../skilltree-creation/creating-custom-skilltrees/skills/backpack.md)
  * Creative
    * Type: boolean
    * Description: Allows players to open the inventory of their pet when they are in creative mode.
  * DropWhenOwnerDies
    * Type: boolean
    * Description: When true the pet will drop the content in its inventory when the owner dies.
* [Beacon](../../skilltree-creation/creating-custom-skilltrees/skills/beacon.md)
  * Disable-Head-Textures
    * Type: boolean
    * Description: Not yet documented.
  * HungerDecreaseTime
    * Type: integer
    * Description: If the Hunger-System is active, sets the interval in which the hunger value is decreased by 1.
  * Party-Support
    * Type: boolean
    * Description: Enables support for parties from these plugins: [MCMMO](https://www.spigotmc.org/resources/official-mcmmo-original-author-returns.64348/), [Heroes](https://www.spigotmc.org/resources/%E2%9A%94-heroes-premium-%E2%9A%94-best-minecraft-spigot-rpg-plugin-ever.24734/), [Ancient RPG](https://dev.bukkit.org/bukkit-plugins/ancient-rpg/). If you have any party plugins MyPet should support please request them on GitHub or Discord.
