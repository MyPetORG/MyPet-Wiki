---
description: Make your Pet pull hostile mobs' aggro off you.
icon: bullhorn
---

# Taunt

The Taunt skill makes your Pet growl at nearby **hostile** mobs that are attacking you and pull their aggro onto itself, tanking for you. It works both on a timer and instantly, the moment a mob first targets you within range.

Only hostile mobs that are targeting you are affected — provoked neutral animals, other players, and other players' Pets are never touched. A Pet set to **Friendly** [behavior](behavior.md) will not taunt.

### Settings <a href="#settings" id="settings"></a>

| Setting  | Key        | Type    | Meaning                                       |
| -------- | ---------- | ------- | --------------------------------------------- |
| Range    | `range`    | number  | How far (in blocks) the Pet pulls aggro from. |
| Interval | `interval` | integer | Seconds between taunt pulses.                 |

```json
"Taunt": {
  "Upgrades": {
    "1": { "Range": "+10", "Interval": "+1" }
  }
}
```
