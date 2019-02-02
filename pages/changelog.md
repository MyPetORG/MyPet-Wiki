# Changelog

## Version 1.3.0

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.8...HEAD)

* o improved NBT pet storage
* - fixed some bugs

## Version 1.2.9

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.8...1.2.9)

* + Wiki-URL can be changed in the config
* o namefilter now ignores colors
* o added EnderDragon as an option to the SkilltreeCreator
* - fixed a bug that allowed players to spawn more than one MyPet entity
* - fix pet-config.yml contained all nodes

## Version 1.2.8

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.7...1.2.8)

* + added a limit\([permissions](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/permissions/README.md)\) to the **/petswitch store** command
* + added eggs as projectiles to the Ranged skill
* + !\[$\]\(/wiki/images/premium.gif\) added Shield skill
* o Beacon range is now calculated differently when using the Hunger System
* o Ride speed is not affected by the Hunger System
* o food items are now stored in a list \(please delete the pet-config.yml when you haven't changed it at all\)
* - fixed a bug that could prevent pets from being saved correctly
* - fixed a bug that caused the plugin to overwrite the pet-config.yml

## Version 1.2.7

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.6...1.2.7)

* + readded _/petadmin clean_ command
* + added _/petswitch_ command
* + add [SkillAPI](http://dev.bukkit.org/bukkit-plugins/skillapi/) support
* - fixed pet size
* - fixed a bug with return values from EXP script \(JS\)

## Version 1.2.6

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.5...1.2.6)

* + add /petoptions idle-volume command to set the volume of the idle sound from pets
* + add random skilltree assignment

## Version 1.2.5

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.3...1.2.5)

* - fixed chat spamming bug

## Version 1.2.3

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.2...1.2.3)

* + added a name filter
* + added Ender Dragon as possible pet \(not recommended for usage\)\(ProtocolLib required\)
* o changed some config options
  * pet configuration moved to _pet-config.yml_
  * _MyPet.Info.OverHead_ ⇒ _MyPet.Name.OverHead_
  * _MaxPetNameLength_ ⇒ _Name.MaxLength_
* o JavaScript XP-Scripts need the [rhino.jar](https://github.com/mozilla/rhino/releases) inside the MyPet folder now
* o improved translation handling \(for example _pt\_br_ is possible now\)
* - fixed bugs

## Version 1.2.2

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.1...1.2.2)

* + added a levelcap \(default is 100\)
* o dropped Java 6 support
* - fixed a lot of bugs
* - fixed a memory leak

## Version 1.2.1

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.2.0...1.2.1)

* + add health bar \(action bar\)
* + pet notifies owner when it's hungry
* + donator perk is back \(**NOT** in BukkitDev version, get it [here](http://build.keyle.de/job/MyPet/682/)\)
* - fixed some bugs

## Version 1.2.0

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.9...1.2.0)

* + make pet invisible when the owner is
* + add config option to always grant passive XP
* + disable trample of farmland by MyPets
* o change the follow speed so pets can catch up mostly

## Version 1.1.9

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.8...1.1.9)

* + add support for [Ultimate Survival Games](http://dev.bukkit.org/bukkit-plugins/ultimatesurvivalgames/)
* + add party support for the beacon skill
* + add pet switch admin command option
* + add RetainEquipmentOnTame config option
* o LowHP leashflag now requires a mob to be below 10% health instead of static 2 HP
* - fixed some bugs

## Version 1.1.8

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.7...1.1.8)

* + Mooshrooms can give soup now
* + added ticket command \(**/petadmin ticket**\)
* + added PvPManager support
* + prefix and suffix of pet nametags can now contain ownername and level
  * `<ownername>`
  * `<level>`
* o improved Towny support
* o improved /petinfo and /petsendaway command
* - fixed some bugs

## Version 1.1.7

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.6...1.1.7)

* + added Stomp skill
* - removed support for the old color format \(`%color%`\)
* - fixed some bugs

## Version 1.1.6

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.5...1.1.6)

* + added level cap for skilltrees
* + added level requirement for skilltrees
* + added config option to enable: Zombies attacking _MyPets_
* + Pickup can also pick up XP now
* + added config option to set a maximum petname length
* + added permission for colors in petnames \(default: `true`\)
  * `MyPet.user.command.name.color`
* o speed and jump height can be set for the Ride skill
* o improved the performance of the XP-JavaScript part \(example: [exp.js](https://github.com/xXKeyleXx/MyPet/blob/master/experience-scripts/exp.js)\)
* o improved the Beacon skill
  * choosable receiver \(owner, everyone\)
  * more buffs \(12\)
  * no tribute item required
  * easy on/off switching
* o the exp option of the admin command can now change the level too \(like the vanilla `/xp` command\)
  * example: `/petadmin exp Keyle 5L add`
* - levelsystem can not be disabled anymore
* - fixed some bugs

## Version 1.1.5

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.4...1.1.5)

* o MyPet is usable with Java6 again
* - removed the donator perk \(had to because the BukkitDev team said that\)

## Version 1.1.4

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.3...1.1.4)

* + items in config can now have [custom data](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/configitems/README.md)
* + added config option for releasing pets when they die
* + added per pettype leashitem config option
* + the rate of fire for the Ranged skill can be set by skilltrees
* o optimizations
* - fixed some bugs

## Version 1.1.3

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.2...1.1.3)

* + Skilltrees can now be selected by an ItemMenu
* - fixed some bugs
* _If you still have the default skilltrees please delete/rename your skilltree file \(_`default.st`_\)_

## Version 1.1.2

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.1...1.1.2)

* + update to Minecraft 1.6.2
* + added horses & squids
* + added some donator effects
* + added some particle effects to skills
* + added LevelUp-Message \(can be set in the skilltrees\)
* o changed colorcode format from `%color%` to `<color>`
  * default colorcodes are now usable too. Example: `<0>` for black or `<f>` for white
* o changed permissions for the commands \* \`MyPet.user.command.capturehelper\` \* \`Mypet.user.command.release\` \* \`Mypet.user.command.respawn\` \* \`MyPet.user.command.name\` \(new\)
* o W A S D riding
* o improved Thorns skill
* o improved some SkilltreeCreator things
  * Change the strucure of YAML skilltrees slightly
* o players need to sneak for every optical change now
* **Known Issues:**
  * You can **NOT** downgrade to 1.1.1
  * GriefPrevention 7.7 will **not** fully supported anymore. Use a 7.8 devbuild instead.

## Version 1.1.1

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.1.0...1.1.1)

* + added config option for consumable leash items
* + added first attempt of an API
* + added more projectile types for the Ranged skill
* + added [MyHungerGames](http://dev.bukkit.org/bukkit-mods/myhungergames/) support
* o improved Lightning skill
* - fixed MobArena damage problem
* - fixed experience loss

## Version 1.1.0

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.9...1.1.0)

* + added [Multiworld](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/Multiworld/README.md)
* + added [BattleArena](http://dev.bukkit.org/bukkit-mods/battlearena/) & [Survival Games](http://dev.bukkit.org/bukkit-plugins/survival-games/) support
* + color of the level-up firework can be changed now
* - removed the YAML and JSON support from the SkilltreeCreator.
  * For YAML and JSON you have to download it seperatly now!
  * You can download the full version of the SkilltreeCreator [here](http://build.keyle.de/job/MyPet-SkilltreeCreator/).
* - removed MyWolf wolf converter
* **Known Issues:**
  * You can **NOT** downgrade to 1.0.9

## Version 1.0.9

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.8...1.0.9)

* + added new locale system -&gt; [en:translations](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/translations/README.md)
* + added [Minigames](http://dev.bukkit.org/server-mods/minigames/) & [PvPArena](http://dev.bukkit.org/bukkit-mods/pvparena/) support
* o improved pet creation admin command option
* o improved CaptureHelper
* - fixed behavior mode switch bug
* - fixed 2 beacon bugs
* **Known Issues:**
  * You can **NOT** downgrade to 1.0.8

## Version 1.0.8

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.7...1.0.8)

* + added CaptureHelper command
* + added [Grief Prevention](http://dev.bukkit.org/server-mods/grief-prevention/) support
* + new levelup effect \(fireworks\)
* + petowners can make the name of their pets colorfull
* + added backup system for the `My.Pets`-file
* + added option do disable sheep wool regrowth
* + added Ghasts as tamable pet
* + added Sprint skill
* + added skill for ranged attacks \(arrows only :-\( \)
* + added simple pet-creation admin command option
* + added damage weighted experience distribution system
* o melee attack range of slimes/magmacubes depends on size now
* o lowered the following stop distance from 5 to 2
* o changed the interval-calculation for the HP-Regeneration skill
* - removed Update-Check \(updates come not frequently enough for this\)

## === Version 1.0.7 ===

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.6...1.0.7)

* + added Wither as leadable mobtype
* + added extenden permission node for Inventory
* + added overhead names
* + added TAB auto completion
* o improved Exp-Script and Exp-Script handling
* o made _SkilltreeCreator_ independent of `craftbukkit.jar`
* - removed `Keep` permission
* - removed `Damage` from pet configuration \(use Damage skill for this purpose\)
* - fixed pickup item dupe bug
* - fixed equipment dupe bug
* - fixed height when riding pets
* - fixed a lot of bugs

## Version 1.0.6

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.5...1.0.6)

* + added config reload option to admin command
* + skilltrees are configurable in JSON format
* + new default skilltree \(thanks to [GaseousMaximus](http://dev.bukkit.org/profiles/GaseousMaximus/)\)
* + skilltrees will now inherit already inherited skilltrees
* + AncientRPG damage fix
* + Skeleton, PigZombie, Zombie can now wear equipment \(only optic\)
* + improved Beacon skill
* + new skills: Wither, Lightning, Knockback, Slow
* + Giant, Blaze, Witch are leadable
* + config options for special abilities of Cow, Sheep, Chicken and Irongolem
* + now all font options are available for language file
* + added PvP support for AncientRPG, Regios, mcMMO, MobArena and Residence
* o default skilltree format is now NBT\([Skilltreecreator](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/skilltreecreator/README.md)\)
* + improved [Skilltreecreator](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/skilltreecreator/README.md) for the new NBT format
* - removed Vault dependency for permissions
* - fixed skill upgrade messages
* - fixed HP bug
* - fixed pet switch to default state bug
* - fixed legacy support for old MyWolf database

## Version 1.0.5

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.4...1.0.5)

* + Angry & Impossible leashflags
* + Beacon & Fire skill
* + more text is translatable
* + Snowman \(snow on the ground is only on clientside so I can't do anything against it :/ \)
* + config options to set the walking speed of the pets \(be carefull\)
* o skilltree files must be lower case now!
* + colorfull console output
* - fixed a lot of bugs!
* **Known Issues:**
  * HP will not become grater than 20
  * pet switch to default state
  * legacy support for old MyWolf database is not working

## Version 1.0.4

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.3...1.0.4)

* + skilltree-switch penalty
* o pets will not attack tamed animals of the owner in aggressive mode
* + Thorns skill
* - fixed a lot of bugs!

## Version 1.0.3

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.2...1.0.3)

* o add items to visible inventory when size gets smaller
* + CanBreed leashflag
* + skilltrees selectable/switchable
* + option to let user choose the skilltree of their pet only once
* - fixed a lot of bugs!

## Version 1.0.2

[GitHub Compare](https://github.com/xXKeyleXx/MyPet/compare/1.0.1...1.0.2)

* - fixed a target finder bug \(can crash the server\)
* + Behavior-modes can now be disabled

## Version 1.0.1

* + MyPets are rideable
* + Hunger-System
* + Configurable Damage/Hitpoints/Food/LeashFlags
* + Skilltrees are configurable for every MyPet-type
* + SkilltreeCreator
* + UpdateChecker
* - fixed tons of bugs

