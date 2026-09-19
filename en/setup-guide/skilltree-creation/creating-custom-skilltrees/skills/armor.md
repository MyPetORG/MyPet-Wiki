---
description: Give your Pet armor to reduce the damage it takes.
icon: shield-halved
---

# Armor

The Armor skill gives your Pet real **armor points** and **armor toughness**, using the same damage-reduction formula Minecraft applies to players. Because vanilla armor also softens **explosion** damage, an armored Pet can survive a creeper blast that would otherwise one-shot it — without inflating its health pool.

The armor is applied as attribute modifiers whenever the Pet spawns and is refreshed on level up or skilltree change, so it never stacks up or lingers after the skill is removed.

### Settings <a href="#settings" id="settings"></a>

| Setting   | Key         | Type    | Meaning                                                  |
| --------- | ----------- | ------- | -------------------------------------------------------- |
| Armor     | `armor`     | integer | Armor points to add (each point works like vanilla armor). |
| Toughness | `toughness` | integer | Armor toughness to add (softens high-damage hits more).  |

```json
"Armor": {
  "Upgrades": {
    "1": { "Armor": "+20", "Toughness": "+8" },
    "5": { "Armor": "+5" }
  }
}
```
