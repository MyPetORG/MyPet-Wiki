---
description: Open portable workstations from your Pet.
icon: toolbox
---

# Toolbox

The Toolbox skill lets you open portable workstations straight from your Pet — no placed blocks needed. Each of the seven stations is unlocked independently: **crafting table, anvil, grindstone, smithing table, stonecutter, loom, and cartography table**.

Open the toolbox with the `/pettoolbox` command (alias `/ptoolbox`), or from the Pet menu. If only one station is unlocked it opens directly; with several unlocked, a chooser menu lets you pick one. Using the command requires the `MyPet.extended.toolbox` permission.

> Furnaces, blast furnaces, and smokers are intentionally not included — their menus need a real block to smelt, so they cannot work block-free.

### Settings <a href="#settings" id="settings"></a>

Each station is a separate boolean unlock:

| Station           | Key           |
| ----------------- | ------------- |
| Crafting table    | `crafting`    |
| Anvil             | `anvil`       |
| Grindstone        | `grindstone`  |
| Smithing table    | `smithing`    |
| Stonecutter       | `stonecutter` |
| Loom              | `loom`        |
| Cartography table | `cartography` |

```json
"Toolbox": {
  "Upgrades": {
    "1": { "crafting": true },
    "3": { "anvil": true, "smithing": true },
    "5": { "grindstone": true, "stonecutter": true, "loom": true, "cartography": true }
  }
}
```
