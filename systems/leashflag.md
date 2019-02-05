---
description: >-
  Leash Flags are the requirements that a mob needs to meet in order to become a
  pet.
---

# Leash Flags / Requirements

All Leash Flags can be combined with each others but some of them will only apply on some  
mob types, some require other plugins and some will overwrite others depending on the order  
they are written in the [pet-config.yml](../setup/configurations/petconfig.md).  
  


* `Impossible`
  * if this is a requirement every other LeashFlags will be ignored and you can't make this mob type a pet
* `LowHP`
  * mob types with this LeashFlag need to be lower than 10% of it's max health
* `Baby`
  * mob types with this leashflag need to be a baby
* `Adult`
  * mob types with this leashflag need to be grown up
* `Tamed`
  * mob types with this leashflag need to be tamed
  * can only be applied to animals that can be tamed
* `UserCreated`
  * mob types with this leashflag need to be constructed by a player
  * can only be applied Iron Golems
* `Wild`
  * mob types with this leashflag need to be wild
  * can only be applied to Wolves, Ocelots and Iron Golems
* `CanBreed`
  * mob types with this leashflag need to be willing to breed
  * can only be applied to animals that can be bred
* `Angry`
  * mob types with this leashflag need to be angry
  * can only be applied to wolves
* `World` flag
  * `World:<world name>:...`
  * Examples:
    * `World:default`
    * `World:default:nether`
* `Size` flag
  * works only for slimes and magma cubes
  * `Size:min=<min size>:max=<max size>`
    * `min` is an optional parameter
    * `max` is an optional parameter
  * `Size:<exact size>`
  * Examples:
    * `Size:min=2`
    * `Size:min=2:max=4`
    * `Size:max=2`
    * `Size:3`
* `BelowHP`
  * checks if a mob is below a certain health threshold
  * `BelowHP:<health>[%]`
    * `%` is optional
  * Examples:
    * `BelowHP:2`
    * `BelowHP:2.5`
    * `BelowHP:10%`
* `Chance`
  * with this flag you can add a random factor to the leashing
  * `Chance:<chance>`
    * `<chance>` is the chance in percent \(%\)
  * Examples:
    * `Chance:2`
    * `Chance:50`
* `mcMMO`
  * checks if a player has a skill above a certain level
  * `mcMMO:<job>=<level>:...`
  * if multiple jobs are specified all requirements must be fullfilled
  * Examples:
    * `mcMMO:Mining=10`
    * `mcMMO:Mining=2:Taming=25`
* `MythicMobs`
  * checks if a mob is from a specific MythicMob type
  * `MythicMobs:<type name>:...`
  * Examples:
    * `MythicMobs:SkeletalKnight`
    * `MythicMobs:StaticallyChargedSheep:SkeletonKing`

