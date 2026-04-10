---
description: Custom flags for use with WorldGuard regions.
icon: flag-pennant
---

# WG Region Flags

MyPet hooks into WorldGuard to provide custom region flags. The WorldGuard hook must be enabled in hooks-config.yml for the flags to work.

Available flags:

* `mypet-fly`
  * Prevents flying with a pet in the region.
* `mypet-damage`
  * Checks whether the MyPet owner can attack a target player or entity following the rules of the WorldGuard region. If the owner of a pet can cause damage, the MyPet can too.
* `mypet-deny`
  * When enabled, denies the use of pets in a region. Pets will be sent away when entering and cannot be called.
