---
description: Let a Pet climb walls on its own to take shortcuts.
icon: spider
---

# Climb

The Climb skill lets a Pet climb straight up walls, spider-style, **on its own**. When the Pet is heading somewhere higher — following you onto a ledge, or chasing a target — and a wall is directly in the way, it scales the wall as a shortcut instead of pathing all the way around, then carries on once it crests the top. It takes no fall damage from the climb, and it only climbs when it is actually trying to reach somewhere higher, not while idly wandering.

Climb does nothing for Pets that can already fly, and ordinary single steps and slabs are still handled by normal step-up, so it only kicks in on a real wall.

> Climbing **while being ridden** is a separate `climb` upgrade on the [Ride](ride.md) skill — there the Pet climbs while you steer it forward against a wall.

### Settings <a href="#settings" id="settings"></a>

| Setting | Key      | Type    | Meaning                             |
| ------- | -------- | ------- | ----------------------------------- |
| Active  | `active` | boolean | Enables autonomous wall-climbing.   |

```json
"Climb": {
  "Upgrades": {
    "1": { "Active": true }
  }
}
```
