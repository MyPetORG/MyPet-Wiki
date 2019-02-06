---
description: >-
  Leash Flags are the requirements that a mob needs to meet in order to become a
  pet.
---

# Leash Flags / Requirements

All Leash Flags can be combined with each others but some of them will only apply on some  
mob types, some require other plugins and some will overwrite others depending on the order  
they are written in the [pet-config.yml](../setup/configurations/petconfig.md).  
  


* \`\`
  * `None`
    * if this is a requirement every other LeashFlags will be irgnored and the mob type can be directly taken on a lead
  * `Impossible`
    * if this is a requirement every other LeashFlags will be ignored and you can't take this mob type on a lead
  * `LowHP`
    * mob types with this LeashFlag need to be lower than 10% of it's max health
  * `Baby`
    * mob types with this leashflag need to be a baby
  * `Adult`
    * mob types with this leashflag need to be grown up
  * `Tamed`
    * mob types with this leashflag need to be tamed
  * `UserCreated`
    * mob types with this leashflag need to be constructed by a player
  * `Wild`
    * mob types with this leashflag need to be wild
  * `CanBreed`
    * mob types with this leashflag need to be willing to breed
  * `Angry`
    * mob types with this leashflag need to be angry \(wolves\)

