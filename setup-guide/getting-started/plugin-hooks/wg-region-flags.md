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

## Releasing pets in protected regions

Since 4.0.1, **releasing** a pet (`/petrelease` or the Release button) is refused in regions that don't permit that mob type to spawn — a released pet becomes a genuine wild mob, so WorldGuard's own `mob-spawning` and `deny-spawn` flags apply to it, per mob type. The same works with any other protection plugin that cancels mob spawns. A refused release leaves the pet completely unharmed.

**Calling a pet is not affected** — pets are exempt from region mob-spawning rules everywhere. Use `mypet-deny` to keep pets out of a region entirely.
