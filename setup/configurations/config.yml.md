---
description: Main Configuration
---

# config.yml

The _config.yml_ file is the main configfile of _MyPet_. All pet type related options can be found in the [pet-config.yml](pet-config.yml.md).

| Setting | Type | Description |
| :--- | :---: | ---: |
| **MyPet:** |  |  |
| **Miscellaneous Settings** |  |  |
|   **Leash:** |  |  |
|     Consume: | boolean | Enable to consume the leash item when a new pet is leashed. |
|   OwnerCanAttackPet: | boolean | Enable to allow the owner to hit his own pet. |
|   DisablePetVersusPlayer: | boolean | Prevents combat between players and pets. |
|   RemovePetsAfterRelease: | boolean | Enable to remove pets when they get released. Prevents players from griefing other players by releasing monsters in their vicinity. |
|   ReleasePetsOnDeath: | boolean | Enable to release the pet when it dies. Player that have the _MyPet.admin_ permission are excluded from this. |
|   FollowStartDistance: | double | Sets the distance from the player where the pet starts to follow him. |
|   RetainEquipmentOnTame: | boolean | Allows mobs to keep their equipment after leashed \(based on the drop chance\). |
|   Make-Pet-Invisible-When-Owner-Is-Invisible: | boolean | Makes the pet invisible when the owner has the `Invisible` effect. Does not affect vanished players. |
|   **Log:** |  |  |
|     Level: | string | Set the level at which the messages will be logged to the file. All possible log levels can be found [here](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Level.html#field_summary). |
|   **Info:** |  |  |
|     Wiki-URL: | string | This can be changed if the server has it's own Wiki for MyPet. |
|   Max-Stored-Pet-Count: | integer | Sets the maximum amount of inactive \(stored\) pets a player can have. |
|   **Update:** |  |  |
|    Check: | boolean | Sets if the plugin will check for updates when it is loaded. This will not download the new version. |
|    Download: | boolean | Sets if the plugin will download the update. |
|    ReplaceOld: | boolean | Sets if the plugin will load the update on the next server start. |
|    Token: | String | The download token you need to download the latest MyPet-Premium version. You can get your token [here](https://mypet-plugin.de/download). |
|   Activate-Resourcepack-By-Default: | boolean | This will actiave the ressource pack by default. Players can still disable it. |
|   Throw-PlayerMoveEvent-While-Riding: | boolean | Disable this when other plugins cause bugs  because of the thrown events. |
|   OverwriteLanguages: | string | If you don't want per player language detection you can use this to overwrite the language for all players. Available languages can be found [here](https://github.com/xXKeyleXx/MyPet-Translations). Example: `pt_br` |
| **Repository Settings** |  |  |
|   **Repository:** |  |  |
|     Type: | string | The storage type where the plugin will save the pets into. 💲 Premium users also have access to `MySQL` and `MongoDB`. |
|     ConvertFrom: | string | This options allows to migrate from one storage type to another. For example from `NBT` to `MySQL`. |
|     **MySQL:** |  |  |
|       Database: | string | The name of the MySQL database. |
|       TablePrefix: | string | The table prefix if the database is shared with other applications. |
|       Host: | string | The address of the MySQL server. |
|       Port: | integer | The port of the MySQL server. |
|       Password: | string | The password of the MySQL user. |
|       User: | string | The username of the MySQL user. |
|       MaxConnections: | integer | The amount of simultaneous connections the plugin will create to the MySQL server. You can find more about the best pool size [here](https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing). |
|     **MongoDB:** |  |  |
|       Database: | string | The name of the MongoDB database. |
|       CollectionPrefix: | string | The collection prefix if the database is shared with other applications. |
|       Host: | string | The address of the MongoDB server. |
|       Port: | integer | The port of the MongoDB server. |
|       Password: | string | The password of the MongoDB user. |
|       User: | string | The username of the MongoDB user. |
| **Respawn Settings** |  |  |
|   **Respawn:** |  |  |
|     **Time:** |  |  |
|       **Default:** |  |  |
|         Factor: | integer | Determines how long the owner has to wait until the pet respawns when it **wasn't** killed by a player.  `Respawntime = Factor * (Level of MyPet) + Fixed` |
|         Fixed: | integer | See `Factor` |
|       **Player:** |  |  |
|         Factor: | integer | Determines how long the owner has to wait until the pet respawns when it **was** killed by a player.  `Respawntime = Factor * (Level of MyPet) + Fixed` |
|         Fixed: | integer | See `Factor` |
|       **EconomyCost:** |  |  |
|         Factor: | double | Determines how much it will cost if you want to revive a dead MyPet.  `Costs = Factor * (Respawn Time in sec.) + Fixed` |
|         Fixed: | double | See `Factor` |
| **Permission Settings** |  |  |
|   **Permissions:** |  |  |
|     Enabled: | boolean | Disable the use of [permissions](../permissions.md) and fall back to the OP permission system. |
|     Extended: | boolean | Enable if you want to use some addition permissions that can be found [here](../permissions.md#extended-mypet-permissions). |
|     Legacy: | boolean | Enable if you want to use the pre 2.0.0 permissions. |
| **Level System Settings** |  |  |
|   **LevelSystem:** |  |  |
|     CalculationMode: | string | Set this to `JS` or `JavaScript` if you want use a custom [exp.js](../../systems/experience/expjs.md). |
| **Hunger System Settings** |  |  |
|   **HungerSystem:** |  |  |
|     Active: | boolean | Disable the [hungersystem](../../systems/hungersystem.md) if you don't want your pets need food to survive. |
|     Time: | integer | Sets the interval \(in seconds\) in which the hunger counter will be reduced by `1`. |
|     HungerPointsPerFeed: | double | Sets the value the hunger counter will be increased by if the pet is fed. |
| **Skilltree Settings** |  |  |
|   **Skilltree:** |  |  |
|     AutomaticAssignment: | boolean | Enable to automatically assign a skilltree to a pet when it is leashed. |
|     RandomAssignment: | boolean | Like `AutomaticAssignment` but the skilltree is selected randomly. |
|     InheritAlreadyInheritedSkills: | boolean | Enable this if you want skill that are inherited by another skilltree can be inherited again. |
|     ChooseOnce: | boolean | Enable this if players shouldn't be able to pick another skilltree once the pet has a skilltree. |
|     PreventLevellingWithout: | boolean | Pets without a skilltree will not gain XP if it is set to `true`. |
|     **SwitchFee:** |  |  |
|       Admin: | boolean | Set this to `true` if admins should pay the same skilltree switch penalty like normal players. |
|       Percent: | integer | The percentage of XP a players has to pay if he switches to another skilltree. |
|       Fixed: | double | The amount of XP a players has to pay if he switches to another skilltree. |
| **Name Settings** |  |  |
|   **Name:** |  |  |
|     Filter: | list | Every pet name is checked against this list of filters \(string/regular expression\). |
|     MaxLength: | integer | The maximum length a petname can have. |
|     **Tag:** |  |  |
|       Show: | boolean | Set this to `false` if you don't want nametags for MyPets. |
|       Prefix: | string | This text will be added in front of the name. You can use color codes and these placeholders:  `<owner>` ⇒ name of the owner  `<level>` ⇒ level of the pet |
|       Suffix: | string | This text will be added the end of the name. You can use color codes and these placeholders:  `<owner>` ⇒ name of the owner  `<level>` ⇒ level of the pet |
| **Experience Settings** |  |  |
|   **Exp:** |  |  |
|     DamageWeightedExperienceDistribution: | boolean | This setting allows pets to gain XP even if they did not kill the enemy. Every bit of damage is counted and when the enemy dies the XP will be split up to reflect the damage given to that enemy. So if a pet does 50% of the damage it will gain 50% of the total XP. |
|     **Passive:** |  |  |
|       Always-Grant-Passive-XP: | boolean | This setting allows the pet to always gain XP when the owner kills a monster, even if it has a damage skill \([Damage](../../skills/damage.md) or [Ranged](../../skills/ranged.md)\). |
|       PercentPerMonster: | integer | Sets the percentage of XP a pet will get when the owner kills an enemy. |
|     **Loss:** |  |  |
|       Drop: | boolean | If this setting is set to `true` the lost XP is dropped on the ground and can be picked up by others. |
|       Percent: | integer | Sets the percentage of XP a pet will lose when it dies. |
|       Fixed: | double | Sets the XP a pet will lose when it dies. |
|     **Gain:** |  |  |
|       PreventFromSpawnReason: | list | This setting is a list of spawn reasons. Every mob that is spawned by any of these spawn reasons will not grant any XP. All spawn reasons can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html#enum_constant_summary). **This resets on every server reload/restart so it will not prevent it after them!** |
|     LevelCap: | integer | A pet can not gain any XP and level up if that level is reached. |
|   **Skill:** |  |  |
|     [**Control**](../../skills/control.md)**:** |  |  |
|       Item: | string | Sets the item that allows the player to use the [Control](../../skills/control.md) skill the pet. This setting follows the [config item](configitems.md) guidelines |
|     [**Ride**](../../skills/ride.md)**:** |  |  |
|       Item: | string | Sets the item that allows the player to mount the pet. This setting follows the [config item](configitems.md) guidelines |
|       HungerPerMeter: | double | If the [Hunger-System](../../systems/hungersystem.md) is active, this setting set the value the hunger value is decreased by for every ridden meter. |
|     [**Backpack**](../../skills/backpack.md): |  |  |
|       Creative: | boolean | Allows players to open the inventory of their pet when they are in creative mode. |
|       DropWhenOwnerDies: | boolean | When this is set to `true` the pet will drop the content in it's inventory when the owner dies. |
|     [**Beacon**](../../skills/beacon.md)**:** |  |  |
|       HungerDecreaseTime: | integer | If the [Hunger-System](../../systems/hungersystem.md) is active, this setting sets the interval in which the value the hunger value is decreased by 1. |
|       Party-Support: | boolean | Enables the support for parties from these plugins: [MCMMO](https://www.spigotmc.org/resources/mcmmo.2445/), [Heroes](https://www.spigotmc.org/resources/heroes.305/), [Ancient](http://dev.bukkit.org/bukkit-plugins/ancient-rpg/)  If you have any party plugins MyPet should support please request them on GitHub or Discord. |
|  |  |  |

