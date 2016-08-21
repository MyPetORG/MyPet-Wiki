# Changelog

### Version 1.3.0
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.8...HEAD)
*  <font color="gold">o</font> improved NBT pet storage
*  <font color="red">-</font> fixed some bugs

----

### Version 1.2.9
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.8...HEAD)

*  <font color="green">+</font> Wiki-URL can be changed in the config
*  <font color="gold">o</font> namefilter now ignores colors
*  <font color="gold">o</font> added EnderDragon as an option to the SkilltreeCreator
*  <font color="red">-</font> fixed a bug that allowed players to spawn more than one MyPet entity
*  <font color="red">-</font> fix pet-config.yml contained all nodes

----

### Version 1.2.8
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.7...1.2.8

*  <font color="green">+</font> added a limit([permissions](permissions)) to the **/petswitch store** command
*  <font color="green">+</font> added eggs as projectiles to the Ranged skill
*  <font color="green">+</font> (P) added Shield skill <font color="DarkCyan"></font>
*  <font color="gold">o</font> Beacon range is now calculated differently when using the Hunger System
*  <font color="gold">o</font> Ride speed is not affected by the Hunger System
*  <font color="gold">o</font> food items are now stored in a list (please delete the pet-config.yml when you haven't changed it at all)
*  <font color="red">-</font> fixed a bug that could prevent pets from being saved correctly
*  <font color="red">-</font> fixed a bug that caused the plugin to overwrite the pet-config.yml

----

### Version 1.2.7
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.6...1.2.7)

*  <font color="green">+</font> readded */petadmin clean* command
*  <font color="green">+</font> added */petswitch* command
*  <font color="green">+</font> add [SkillAPI](http://dev.bukkit.org/bukkit-plugins/skillapi/) support
*  <font color="red">-</font> fixed pet size
*  <font color="red">-</font> fixed a bug with return values from EXP script (JS)

----

### Version 1.2.6
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.5...1.2.6)

*  <font color="green">+</font> add /petoptions idle-volume command to set the volume of the idle sound from pets
*  <font color="green">+</font> add random skilltree assignment

----

### Version 1.2.5
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.3...1.2.5)

*  <font color="red">-</font> fixed chat spamming bug

----

### Version 1.2.3
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.2...1.2.3)

*  <font color="green">+</font> added a name filter
*  <font color="green">+</font> added Ender Dragon as possible pet (not recommended for usage)(ProtocolLib required)
*  <font color="gold">o</font> changed some config options
    * pet configuration moved to *pet-config.yml*
    * *MyPet.Info.OverHead* ⇒ *MyPet.Name.OverHead*
    * *MaxPetNameLength* ⇒ *Name.MaxLength*
*  <font color="gold">o</font> JavaScript XP-Scripts need the [rhino.jar](https://github.com/mozilla/rhino/releases) inside the MyPet folder now
*  <font color="gold">o</font> improved translation handling (for example *pt_br* is possible now)
*  <font color="red">-</font> fixed bugs

----

### Version 1.2.2
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.1...1.2.2)

*  <font color="green">+</font> added a levelcap (default is 100)
*  <font color="gold">o</font> dropped Java 6 support
*  <font color="red">-</font> fixed a lot of bugs
*  <font color="red">-</font> fixed a memory leak

----

### Version 1.2.1
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.0...1.2.1)

*  <font color="green">+</font> add health bar (action bar)
*  <font color="green">+</font> pet notifies owner when it's hungry
*  <font color="green">+</font> donator perk is back (**NOT** in BukkitDev version, get it [here](http://build.keyle.de/job/MyPet/682/))
*  <font color="red">-</font> fixed some bugs

----

### Version 1.2.0
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.9...1.2.0)

*  <font color="green">+</font> make pet invisible when the owner is
*  <font color="green">+</font> add config option to always grant passive XP
*  <font color="green">+</font> disable trample of farmland by MyPets
*  <font color="gold">o</font> change the follow speed so pets can catch up mostly

----

### Version 1.1.9
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.8...1.1.9)

*  <font color="green">+</font> add support for [Ultimate Survival Games](http://dev.bukkit.org/bukkit-plugins/ultimatesurvivalgames/)
*  <font color="green">+</font> add party support for the beacon skill
*  <font color="green">+</font> add pet switch admin command option
*  <font color="green">+</font> add RetainEquipmentOnTame config option
*  <font color="gold">o</font> LowHP leashflag now requires a mob to be below 10% health instead of static 2 HP
*  <font color="red">-</font> fixed some bugs

----

### Version 1.1.8
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.7...1.1.8)

*  <font color="green">+</font> Mooshrooms can give soup now
*  <font color="green">+</font> added ticket command (**/petadmin ticket**)
*  <font color="green">+</font> added PvPManager support
*  <font color="green">+</font> prefix and suffix of pet nametags can now contain ownername and level
    * `<ownername>`
    * `<level>`
*  <font color="gold">o</font> improved Towny support
*  <font color="gold">o</font> improved /petinfo and /petsendaway command
*  <font color="red">-</font> fixed some bugs

----

### Version 1.1.7
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.6...1.1.7)

*  <font color="green">+</font> added Stomp skill
*  <font color="red">-</font> removed support for the old color format (`%color%`)
*  <font color="red">-</font> fixed some bugs

----

### Version 1.1.6
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.5...1.1.6)

*  <font color="green">+</font> added level cap for skilltrees
*  <font color="green">+</font> added level requirement for skilltrees
*  <font color="green">+</font> added config option to enable: Zombies attacking *MyPets*
*  <font color="green">+</font> Pickup can also pick up XP now
*  <font color="green">+</font> added config option to set a maximum petname length
*  <font color="green">+</font> added permission for colors in petnames (default: `true`)
    * `MyPet.user.command.name.color`
*  <font color="gold">o</font> speed and jump height can be set for the Ride skill
*  <font color="gold">o</font> improved the performance of the XP-JavaScript part (example: [exp.js](https://github.com/xXKeyleXx/MyPet/blob/master/experience-scripts/exp.js))
*  <font color="gold">o</font> improved the Beacon skill
    * choosable receiver (owner, everyone)
    * more buffs (12)
    * no tribute item required
    * easy on/off switching
*  <font color="gold">o</font> the exp option of the admin command can now change the level too (like the vanilla `/xp` command)
    * example: `/petadmin exp Keyle 5L add`
*  <font color="red">-</font> levelsystem can not be disabled anymore
*  <font color="red">-</font> fixed some bugs

----

### Version 1.1.5
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.4...1.1.5)

*  <font color="gold">o</font> MyPet is usable with Java6 again
*  <font color="red">-</font> removed the donator perk (had to because the BukkitDev team said that)

----

### Version 1.1.4
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.3...1.1.4)

*  <font color="green">+</font> items in config can now have [custom data](configitems)
*  <font color="green">+</font> added config option for releasing pets when they die
*  <font color="green">+</font> added per pettype leashitem config option
*  <font color="green">+</font> the rate of fire for the Ranged skill can be set by skilltrees
*  <font color="gold">o</font> optimizations
*  <font color="red">-</font> fixed some bugs

----

### Version 1.1.3
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.2...1.1.3)

*  <font color="green">+</font> Skilltrees can now be selected by an ItemMenu
*  <font color="red">-</font> fixed some bugs

*  *If you still have the default skilltrees please delete/rename your skilltree file (`default.st`)*

----

### Version 1.1.2
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.1...1.1.2)

*  <font color="green">+</font> update to Minecraft 1.6.2
*  <font color="green">+</font> added horses & squids
*  <font color="green">+</font> added some donator effects
*  <font color="green">+</font> added some particle effects to skills
*  <font color="green">+</font> added LevelUp-Message (can be set in the skilltrees)
*  <font color="gold">o</font> changed colorcode format from `%color%` to `%%`<color>`%%`
    * default colorcodes are now usable too. Example: `<0>` for black or `<f>` for white
*  <font color="gold">o</font> changed permissions for the commands
    * `MyPet.user.command.capturehelper`
    * `Mypet.user.command.release`
    * `Mypet.user.command.respawn`
    * `MyPet.user.command.name` <font color="green">(new)</font>
*  <font color="gold">o</font> `<key>`w`</key>` `<key>`a`</key>` `<key>`s`</key>` `<key>`d`</key>` riding
*  <font color="gold">o</font> improved Thorns skill
*  <font color="gold">o</font> improved some SkilltreeCreator things
    * Change the strucure of YAML skilltrees slightly
*  <font color="gold">o</font> players need to sneak for every optical change now

*  **Known Issues:**
    * You can **NOT** downgrade to 1.1.1
    * GriefPrevention 7.7 will **not** fully supported anymore. Use a 7.8 devbuild instead.


----

### Version 1.1.1
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.0...1.1.1)

*  <font color="green">+</font> added config option for consumable leash items
*  <font color="green">+</font> added first attempt of an API
*  <font color="green">+</font> added more projectile types for the Ranged skill
*  <font color="green">+</font> added [MyHungerGames](http://dev.bukkit.org/bukkit-mods/myhungergames/) support
*  <font color="gold">o</font> improved Lightning skill
*  <font color="red">-</font> fixed MobArena damage problem
*  <font color="red">-</font> fixed experience loss

----

### Version 1.1.0
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.9...1.1.0)

*  <font color="green">+</font> added [Multiworld](Multiworld)
*  <font color="green">+</font> added [BattleArena](http://dev.bukkit.org/bukkit-mods/battlearena/) & [Survival Games](http://dev.bukkit.org/bukkit-plugins/survival-games/) support
*  <font color="green">+</font> color of the level-up firework can be changed now
*  <font color="red">-</font> removed the YAML and JSON support from the SkilltreeCreator.
    * For YAML and JSON you have to download it seperatly now!
    * You can download the full version of the SkilltreeCreator [here](http://build.keyle.de/job/MyPet-SkilltreeCreator/).
*  <font color="red">-</font> removed MyWolf wolf converter

*  **Known Issues:**
    * You can **NOT** downgrade to 1.0.9

----

### Version 1.0.9
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.8...1.0.9)

*  <font color="green">+</font> added new locale system -> [en:translations](translations)
*  <font color="green">+</font> added [Minigames](http://dev.bukkit.org/server-mods/minigames/) & [PvPArena](http://dev.bukkit.org/bukkit-mods/pvparena/) support
*  <font color="gold">o</font> improved pet creation admin command option
*  <font color="gold">o</font> improved CaptureHelper
*  <font color="red">-</font> fixed behavior mode switch bug
*  <font color="red">-</font> fixed 2 beacon bugs

*  **Known Issues:**
    * You can **NOT** downgrade to 1.0.8

----

### Version 1.0.8
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.7...1.0.8)

*  <font color="green">+</font> added CaptureHelper command
*  <font color="green">+</font> added [Grief Prevention](http://dev.bukkit.org/server-mods/grief-prevention/) support
*  <font color="green">+</font> new levelup effect (fireworks)
*  <font color="green">+</font> petowners can make the name of their pets colorfull
*  <font color="green">+</font> added backup system for the `My.Pets`-file
*  <font color="green">+</font> added option do disable sheep wool regrowth
*  <font color="green">+</font> added Ghasts as tamable pet
*  <font color="green">+</font> added Sprint skill
*  <font color="green">+</font> added skill for ranged attacks (arrows only :-( )
*  <font color="green">+</font> added simple pet-creation admin command option
*  <font color="green">+</font> added damage weighted experience distribution system
*  <font color="gold">o</font> melee attack range of slimes/magmacubes depends on size now
*  <font color="gold">o</font> lowered the following stop distance from 5 to 2
*  <font color="gold">o</font> changed the interval-calculation for the HP-Regeneration skill
*  <font color="red">-</font> removed Update-Check (updates come not frequently enough for this)

----

### === Version 1.0.7 ===
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.6...1.0.7)

*  <font color="green">+</font> added Wither as leadable mobtype
*  <font color="green">+</font> added extenden permission node for Inventory
*  <font color="green">+</font> added overhead names
*  <font color="green">+</font> added TAB auto completion
*  <font color="gold">o</font> improved Exp-Script and Exp-Script handling
*  <font color="gold">o</font> made *SkilltreeCreator* independent of `craftbukkit.jar`
*  <font color="red">-</font> removed `Keep` permission
*  <font color="red">-</font> removed `Damage` from pet configuration (use Damage skill for this purpose)
*  <font color="red">-</font> fixed pickup item dupe bug
*  <font color="red">-</font> fixed equipment dupe bug
*  <font color="red">-</font> fixed height when riding pets
*  <font color="red">-</font> fixed a lot of bugs

----

### Version 1.0.6
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.5...1.0.6)

*  <font color="green">+</font> added config reload option to admin command
*  <font color="green">+</font> skilltrees are configurable in JSON format
*  <font color="green">+</font> new default skilltree (thanks to [GaseousMaximus](http://dev.bukkit.org/profiles/GaseousMaximus/))
*  <font color="green">+</font> skilltrees will now inherit already inherited skilltrees
*  <font color="green">+</font> AncientRPG damage fix
*  <font color="green">+</font> Skeleton, PigZombie, Zombie can now wear equipment (only optic)
*  <font color="green">+</font> improved Beacon skill
*  <font color="green">+</font> new skills: Wither, Lightning, Knockback, Slow
*  <font color="green">+</font> Giant, Blaze, Witch are leadable
*  <font color="green">+</font> config options for special abilities of Cow, Sheep, Chicken and Irongolem
*  <font color="green">+</font> now all font options are available for language file
*  <font color="green">+</font> added PvP support for AncientRPG, Regios, mcMMO, MobArena and Residence
*  <font color="gold">o</font> default skilltree format is now NBT([Skilltreecreator](skilltreecreator))
*  <font color="green">+</font> improved [Skilltreecreator](skilltreecreator) for the new NBT format
*  <font color="red">-</font> removed Vault dependency for permissions
*  <font color="red">-</font> fixed skill upgrade messages
*  <font color="red">-</font> fixed HP bug
*  <font color="red">-</font> fixed pet switch to default state bug
*  <font color="red">-</font> fixed legacy support for old MyWolf database

----

### Version 1.0.5
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.4...1.0.5)

*  <font color="green">+</font> Angry & Impossible leashflags
*  <font color="green">+</font> Beacon & Fire skill
*  <font color="green">+</font> more text is translatable
*  <font color="green">+</font> Snowman (snow on the ground is only on clientside so I can't do anything against it :/ )
*  <font color="green">+</font> config options to set the walking speed of the pets (be carefull)
*  <font color="gold">o</font> skilltree files must be lower case now!
*  <font color="green">+</font> colorfull console output
*  <font color="red">-</font> fixed a lot of bugs!

*  **Known Issues:**
    * HP will not become grater than 20
    * pet switch to default state
    * legacy support for old MyWolf database is not working

----

### Version 1.0.4
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.3...1.0.4)

*  <font color="green">+</font> skilltree-switch penalty
*  <font color="gold">o</font> pets will not attack tamed animals of the owner in aggressive mode
*  <font color="green">+</font> Thorns skill
*  <font color="red">-</font> fixed a lot of bugs!

----

### Version 1.0.3
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.2...1.0.3)

*  <font color="gold">o</font> add items to visible inventory when size gets smaller
*  <font color="green">+</font> CanBreed leashflag
*  <font color="green">+</font> skilltrees selectable/switchable
*  <font color="green">+</font> option to let user choose the skilltree of their pet only once
*  <font color="red">-</font> fixed a lot of bugs!

----

### Version 1.0.2
[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.1...1.0.2)

*  <font color="red">-</font> fixed a target finder bug (can crash the server)
*  <font color="green">+</font> Behavior-modes can now be disabled

### Version 1.0.1

----

*  <font color="green">+</font> MyPets are rideable
*  <font color="green">+</font> Hunger-System
*  <font color="green">+</font> Configurable Damage/Hitpoints/Food/LeashFlags
*  <font color="green">+</font> Skilltrees are configurable for every MyPet-type
*  <font color="green">+</font> SkilltreeCreator
*  <font color="green">+</font> UpdateChecker
*  <font color="red">-</font> fixed tons of bugs
