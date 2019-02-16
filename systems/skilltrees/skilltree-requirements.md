---
description: >-
  Skilltree requirements are used to limit skilltrees to pets that meet certain
  conditions.
---

# Skilltree Requirements

Currently these requirements are available:

*  `NoSkilltree`
  * limits this skilltree to pets that have no skilltree yet
*  `Skilltree`
  * limits this skilltree to pets that have a certain skilltree
  * requires the skilltree name as a parameter
  * Example:
    * `Skilltree:Ride`
*  `Permission`
  * limits this skilltree to pets where the owner needs the  `MyPet.skilltree.<skilltreename>` permission
  * the permission needed can be changed by using a parameter. 
    * Example:
      * `Permission:newNode` will become `MyPet.skilltree.newNode`
* `PetLevel`
  * limits this skilltree to pets that have a certain level
  * can be limited to
    * a specific level
    * min level
    * max level
  * Examples:
    * `PetLevel:min=2`
    * `PetLevel:min=2:max=4`
    * `PetLevel:max=2`
    * `PetLevel:3`

