# Main Configuration

The *config.yml* file is the main configfile of *MyPet*. All pet type related options can be found in the [pet-config.yml](petconfig).

----

|  Setting  |  Type  |  Default  |  ![$](/wiki/images/premium.gif)  |  Description  |
| :------- | :------: |  :------: |  :------: | -------: |
|**MyPet:**|||||
|  **Miscellaneous Settings**  |||||
|&nbsp;&nbsp;**Leash:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;Consume:|  boolean  |  `false`  |  -  |Enable to consume the leash item when a new pet is leashed.|
|&nbsp;&nbsp;OwnerCanAttackPet:|  boolean  |  `false`  |  -  |Enable to allow the owner to hit his own pet.|
|&nbsp;&nbsp;DisablePetVersusPlayer:|  boolean  |  `false`  |  -  |Prevents combat between players and pets.|
|&nbsp;&nbsp;RemovePetsAfterRelease:|  boolean  |  `false`  |  -  |Enable to remove pets when they get released. Prevents players from griefing other players by releasing monsters in their vicinity.|
|&nbsp;&nbsp;ReleasePetsOnDeath:|  boolean  |  `false`  |  -  |Enable to release the pet when it dies. Player that have the <font color="Purple">_MyPet.admin_</font> permission are excluded from this.|
|&nbsp;&nbsp;FollowStartDistance:|  double  |  `7.0`  |  -  |Sets the distance from the player where the pet starts to follow him.|
|&nbsp;&nbsp;RetainEquipmentOnTame:|  boolean  |  `true`  |  -  |Allows mobs to keep their equipment after leashed (based on the drop chance).|
|&nbsp;&nbsp;Make-Pet-Invisible-When-Owner-Is-Invisible:|  boolean  |  `true`  |  -  |Makes the pet invisible when the owner has the `Invisible` effect. Does not affect vanished players.|
|&nbsp;&nbsp;**Log:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;Level:|  string  |  `INFO`  |  -  |Set the level at which the messages will be logged to the file. All possible log levels can be found [here](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Level.html#field_summary).|
|&nbsp;&nbsp;**Info:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;Wiki-URL:|  string  |  `https://wiki.mypet-plugin.de`  |  -  |This can be changed if the server has it's own Wiki for MyPet.|
|&nbsp;&nbsp;Max-Stored-Pet-Count:|  integer  |  `45`  |  -  |Sets the maximum amount of inactive (stored) pets a player can have.|
|&nbsp;&nbsp;**Update:**|||||
|&nbsp;&nbsp;&nbsp;Check:|  boolean  |  `true`  |  -  |Sets if the plugin will check for updates when it is loaded. This will not download the new version.|
|&nbsp;&nbsp;&nbsp;Download:|  boolean  |  `false`  |  -  |Sets if the plugin will download the update.|
|&nbsp;&nbsp;&nbsp;ReplaceOld:|  boolean  |  `false`  |  -  |Sets if the plugin will load the update on the next server start.|
|&nbsp;&nbsp;&nbsp;Token:|  String  |  `''`  |  ![$](/wiki/images/premium.gif)  |The download token you need to download the latest MyPet-Premium version. You can get your token [here](https://mypet-plugin.de/download).|
|&nbsp;&nbsp;Activate-Resourcepack-By-Default:|  boolean  |  `false`  |  ![$](/wiki/images/premium.gif)  |This will actiave the ressource pack by default. Players can still disable it.|
|&nbsp;&nbsp;Throw-PlayerMoveEvent-While-Riding:|  boolean  |  `true`  |  -  |Disable this when other plugins cause bugs  because of the thrown events.|
|&nbsp;&nbsp;OverwriteLanguages:|  string  |  `''`  |  -  |If you don't want per player language detection you can use this to overwrite the language for all players. Available languages can be found [here](https://github.com/xXKeyleXx/MyPet-Translations). Example: `pt_br` |
|  **Repository Settings**  |||||
|&nbsp;&nbsp;**Repository:**||||
|&nbsp;&nbsp;&nbsp;&nbsp;Type:|  string  |  `SQLite`  |  ![$](/wiki/images/premium.gif)  |The storage type where the plugin will save the pets into. ![$](/wiki/images/premium.gif) Premium users also have access to `MySQL` and `MongoDB`.|
|&nbsp;&nbsp;&nbsp;&nbsp;ConvertFrom:|  string  |  `''`  |  ![$](/wiki/images/premium.gif)  |This options allows to migrate from one storage type to another. For example from `NBT` to `MySQL`.|
|&nbsp;&nbsp;&nbsp;&nbsp;**MySQL:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Database:|  string  |  `mypet`  |  ![$](/wiki/images/premium.gif)  |The name of the MySQL database.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TablePrefix:|  string  |  `''`  |  ![$](/wiki/images/premium.gif)  |The table prefix if the database is shared with other applications.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Host:|  string  |  `localhost`  |  ![$](/wiki/images/premium.gif)  |The address of the MySQL server.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Port:|  integer  |  `3306`  |  ![$](/wiki/images/premium.gif)  |The port of the MySQL server.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Password:|  string  |  `''`  |  ![$](/wiki/images/premium.gif)  |The password of the MySQL user.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;User:|  string  |  `root`  |  ![$](/wiki/images/premium.gif)  |The username of the MySQL user.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MaxConnections:|  integer  |  `CPU cores * 2`  |  ![$](/wiki/images/premium.gif)  |The amount of simultaneous connections the plugin will create to the MySQL server. You can find more about the best pool size [here](https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing).|
|&nbsp;&nbsp;&nbsp;&nbsp;**MongoDB:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Database:|  string  |  `mypet`  |  ![$](/wiki/images/premium.gif)  |The name of the MongoDB database.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CollectionPrefix:|  string  |  `''`  |  ![$](/wiki/images/premium.gif)  |The collection prefix if the database is shared with other applications.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Host:|  string  |  `localhost`  |  ![$](/wiki/images/premium.gif)  |The address of the MongoDB server.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Port:|  integer  |  `3306`  |  ![$](/wiki/images/premium.gif)  |The port of the MongoDB server.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Password:|  string  |  `''`  |  ![$](/wiki/images/premium.gif)  |The password of the MongoDB user.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;User:|  string  |  `''`  |  ![$](/wiki/images/premium.gif)  |The username of the MongoDB user.|
|  **Respawn Settings**   |||||
|&nbsp;&nbsp;**Respawn:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;**Time:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Default:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Factor:|  integer  |  `5`  |  -  |Determines how long the owner has to wait until the pet respawns when it **wasn't** killed by a player.<br> `Respawntime = Factor * (Level of MyPet) + Fixed`|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fixed:|  integer|  `0`  |  -  |See `Factor`|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Player:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Factor:|  integer  |  `5`  |  -  |Determines how long the owner has to wait until the pet respawns when it **was** killed by a player.<br> `Respawntime = Factor * (Level of MyPet) + Fixed`|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fixed:|  integer  |  `0`  |  -  |See `Factor`|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**EconomyCost:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Factor:|  double  |  `5`  |  -  |Determines how much it will cost if you want to revive a dead MyPet.<br> `Costs = Factor * (Respawn Time in sec.) + Fixed`|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fixed:|  double  |  `0`  |  -  |See `Factor`|
|  **Permission Settings**  |||||
|&nbsp;&nbsp;**Permissions:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;Enabled:|  boolean  |  `true`  |  -  |Disable the use of [permissions](permissions) and fall back to the OP permission system.|
|&nbsp;&nbsp;&nbsp;&nbsp;Extended:|  boolean  |   `false`  |  -  |Enable if you want to use some addition permissions that can be found [here](permissions#extended_mypet_permissions).|
|&nbsp;&nbsp;&nbsp;&nbsp;Legacy:|  boolean  |   `false`  |  -  |Enable if you want to use the pre 2.0.0 permissions.|
|  **Level System Settings**  |||||
|&nbsp;&nbsp;**LevelSystem:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;CalculationMode:|  string  |  `Default`  |  -  |Set this to `JS` or `JavaScript` if you want use a custom [exp.js](expjs).|
|  **Hunger System Settings**  |||||
|&nbsp;&nbsp;**HungerSystem:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;Active:|  boolean  |  `true`  |  -  |Disable the [hungersystem](hungersystem) if you don't want your pets need food to survive.|
|&nbsp;&nbsp;&nbsp;&nbsp;Time:|  integer  |  `60`  |  -  |Sets the interval (in seconds) in which the hunger counter will be reduced by `1`.|
|&nbsp;&nbsp;&nbsp;&nbsp;HungerPointsPerFeed:|  double  |  `6.0`  |  -  |Sets the value the hunger counter will be increased by if the pet is fed.|
|  **Skilltree Settings**  |||||
|&nbsp;&nbsp;**Skilltree:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;AutomaticAssignment:|  boolean  |  `false`  |  -  |Enable to automatically assign a skilltree to a pet when it is leashed.|
|&nbsp;&nbsp;&nbsp;&nbsp;RandomAssignment:|  boolean  |  `false`  |  -  |Like `AutomaticAssignment` but the skilltree is selected randomly.|
|&nbsp;&nbsp;&nbsp;&nbsp;InheritAlreadyInheritedSkills:|  boolean  |  `false`  |  -  |Enable this if you want skill that are inherited by another skilltree can be inherited again.|
|&nbsp;&nbsp;&nbsp;&nbsp;ChooseOnce:|  boolean  |  `false`  |  -  |Enable this if players shouldn't be able to pick another skilltree once the pet has a skilltree.|
|&nbsp;&nbsp;&nbsp;&nbsp;PreventLevellingWithout:|  boolean  |  `true`  |  -  |Pets without a skilltree will not gain XP if it is set to `true`.|
|&nbsp;&nbsp;&nbsp;&nbsp;**SwitchFee:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Admin:|  boolean  |  `false`  |  -  |Set this to `true` if admins should pay the same skilltree switch penalty like normal players.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Percent:|  integer  |  `5`  |  -  |The percentage of XP a players has to pay if he switches to another skilltree.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fixed:|  double  |  `0.0`  |  -  |The amount of XP a players has to pay if he switches to another skilltree.|
|  **Name Settings**  |||||
|&nbsp;&nbsp;**Name:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;Filter:|  list  |  `whore, fuck`  |  -  |Every pet name is checked against this list of filters (string/regular expression).|
|&nbsp;&nbsp;&nbsp;&nbsp;MaxLength:|  integer  |  `32`  |  -  |The maximum length a petname can have.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Tag:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Show:|  boolean  |  `true`  |  -  |Set this to `false` if you don't want nametags for MyPets.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Prefix:|  string  |  `<aqua>`  |  -  |This text will be added in front of the name. You can use color codes and these placeholders:<br> `<owner>` ⇒ name of the owner<br> `<level>` ⇒ level of the pet|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Suffix:|  string  |  `''`  |  -  |This text will be added the end of the name. You can use color codes and these placeholders:<br> `<owner>` ⇒ name of the owner<br> `<level>` ⇒ level of the pet|
|  **Experience Settings**  |||||
|&nbsp;&nbsp;**Exp:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;DamageWeightedExperienceDistribution:|  boolean  |  `false`  |  -  |This setting allows pets to gain XP even if they did not kill the enemy. Every bit of damage is counted and when the enemy dies the XP will be split up to reflect the damage given to that enemy. So if a pet does 50% of the damage it will gain 50% of the total XP.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Passive:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Always-Grant-Passive-XP:|  boolean  |  `false`  |  -  |This setting allows the pet to always gain XP when the owner kills a monster, even if it has a damage skill ([Damage](skills/damage) or [Ranged](skills/ranged)).|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PercentPerMonster:|  integer  |  `25`  |  -  |Sets the percentage of XP a pet will get when the owner kills an enemy.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Loss:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Drop:|  boolean  |  `true`  |  -  |If this setting is set to `true` the lost XP is dropped on the ground and can be picked up by others.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Percent:|  integer  |  `0`  |  -  |Sets the percentage of XP a pet will lose when it dies.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fixed:|  double  |  `0.0`  |  -  |Sets the XP a pet will lose when it dies.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Gain:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PreventFromSpawnReason:|  list  |  `[]`  |  -  |This setting is a list of spawn reasons. Every mob that is spawned by any of these spawn reasons will not grant any XP. All spawn reasons can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html#enum_constant_summary). **This resets on every server reload/restart so it will not prevent it after them!**|
|&nbsp;&nbsp;&nbsp;&nbsp;LevelCap:|  integer  |  `100`  |  -  |A pet can not gain any XP and level up if that level is reached.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Active:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;**[ENTITY_TYPE](https://hub.spigotmc.org/javadocs/bukkit/):**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Min:|  double  |  `5.0`  |  -  |The minimal amount of XP that this entity type grants.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Max:|  double  |  `5.0`  |  -  |The maximum amount of XP that this entity type grants.|
|||  **Skill Settings**  |||
|&nbsp;&nbsp;**Skill:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;**[Control](skills/control):**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Item:|  string  |  `420`  |  -  |Sets the item that allows the player to use the [Control](skills/control) skill the pet. This setting follows the [config item](configitem) guidelines|
|&nbsp;&nbsp;&nbsp;&nbsp;**[Rride](skills/ride]]:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Item:|  string  |  `420`  |  -  |Sets the item that allows the player to mount the pet. This setting follows the [config item](configitem) guidelines|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HungerPerMeter:|  double  |  `0.01`  |  -  |If the [Hunger-System](hungersystem) is active, this setting set the value the hunger value is decreased by for every ridden meter.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**FlyZones:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**<font color="#1CA8D6">SomeWorld</font>**::**<font color="#86C48B">SomeRegion</font>**:<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**<font color="#1CA8D6">SomeWorld</font>**::**<font color="#86C48B">__global__</font>**:<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**…**|  boolean  |  `true`  |  ![$](/wiki/images/premium.gif)  |This setting allows to disable flying in WorldGuard regions. For every region you want to allow/disable flying you have to add a new line that looks like this:<br> **<font color="#1CA8D6">&lt;World&gt;</font>**::**<font color="#86C48B">&lt;RegionName&gt;</font>**: false<br> Regions with higher priorities will overwrite regions with a lower priorities. This allows to have small regions that allow flying in big regions where flying is diabled and vice versa.<br> An example can be found [here](skills/ride#example).|
|&nbsp;&nbsp;&nbsp;&nbsp;**[[skills:backpack|Inventory]]:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Creative:|  boolean  |  `false`  |  -  |Allows players to open the inventory of their pet when they are in creative mode.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DropWhenOwnerDies:|  boolean  |  `false`  |  -  |When this is set to `true` the pet will drop the content in it's inventory when the owner dies.|
|&nbsp;&nbsp;&nbsp;&nbsp;**[Beacon](skills/beacon):**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HungerDecreaseTime:|  integer  |  `100`  |  -  |If the [Hunger-System](hungersystem) is active, this setting sets the interval in which the value the hunger value is decreased by 1.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Party-Support:|  boolean  |  `true`  |  -  |Enables the support for parties from these plugins: [MCMMO](https://www.spigotmc.org/resources/mcmmo.2445/), [Heroes](https://www.spigotmc.org/resources/heroes.305/), [Ancient](http://dev.bukkit.org/bukkit-plugins/ancient-rpg/)<br> If you have any party plugins MyPet should support please [contact me](contact).|
|  **Hooks Settings**  |||||
|&nbsp;&nbsp;**Hooks:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;AncientRPG:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the AncientRPG plugin like **parties**. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;Towny:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the Towny plugin. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;MCMMO:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the MCMMO plugin like **parties**. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;Factions:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the Factions plugin. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;Heroes:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the Heroes plugin like **minimum PvP level** or **parties**. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;WorldGuard:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the WorldGuard like **region flags**. If the owner of a pet can attack a player, the MyPet can attack this player too. This will not affect **Fly Zones** ![$](/wiki/images/premium.gif) because they can be disabled by just removing all zones.|
|&nbsp;&nbsp;&nbsp;&nbsp;Residence:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the Residence. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;GriefPrevention:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the GriefPrevention. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;PvPManager:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player following the rules of the PvPManager. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;Citizens:|  boolean  |  `true`  |  -  |Checks whether the target NPC can be damaged by a MyPet. NPCs can't be leashed.|
|&nbsp;&nbsp;&nbsp;&nbsp;**MobArena:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Enabled:|  boolean  |  `true`  |  -  |Enables the MobArena hook. (This allows the pet to deal damage in arenas)|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;RespectPvPRule:|  boolean  |  `true`  |  -  |If `true` pets will respects the PvP rules of an arena. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;AllowPets:|  boolean  |  `true`  |  -  |If `true` pets will be able to enter arenas.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Minigames:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DisablePetsInGames:|  boolean  |  `true`  |  -  |Disables MyPets in any minigame completely.|
|&nbsp;&nbsp;&nbsp;&nbsp;**PvPArena:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PvP:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player inside an arena. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DisablePetsInArena:|  boolean  |  `true`  |  -  |Disables MyPets in the arenas completely.|
|&nbsp;&nbsp;&nbsp;&nbsp;**SurvivalGames:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PvP:|  boolean  |  `true`  |  -  |Checks whether the MyPet-owner can attack a target player inside a survival game match. If the owner of a pet can attack a player, the MyPet can attack this player too.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DisablePetsInGames:|  boolean  |  `true`  |  -  |Disables MyPets in survival game matches completely.|
|&nbsp;&nbsp;&nbsp;&nbsp;**MyHungerGames:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DisablePetsInGames:|  boolean  |  `true`  |  -  |Disables MyPets in survival game matches completely.|
|&nbsp;&nbsp;&nbsp;&nbsp;**BattleArena:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DisablePetsInArena:|  boolean  |  `true`  |  -  |Disables MyPets in the arenas completely.|
|&nbsp;&nbsp;&nbsp;&nbsp;**Vault:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Economy:|  boolean  |  `true`  |  -  |Enables the economy support. Used by ![$](/wiki/images/premium.gif) trading, respawning and storing pets.|
|&nbsp;&nbsp;&nbsp;&nbsp;**SkillAPI:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;GrantExp:|  boolean  |  `true`  |  -  |This setting allows pets to gain XP when the owner gains SkillAPI XP.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Disable-Vanilla-Exp:|  boolean  |  `false`  |  -  |This setting disables XP gain of normal sources at all. The only way pets can get any XP is when the owner gets XP via SkillAPI.|