---
description: Let your Pet sniff out and dig up an item over time.
icon: magnifying-glass
---

# Sniff

The Sniff skill makes your Pet periodically "sniff out" an item from its **drop pool** — it plays a short sniffer digging animation and then drops that item beside itself. The Pet only sniffs while it has all paws on solid ground, pausing while it is swimming in deep water or in the air.

The drop pool is configured **per skilltree** — each level of the Sniff skill can add its own entries. When it's time to sniff, the Pet rolls a weighted random pick across every entry granted so far and drops a random amount of that item.

### Settings <a href="#settings" id="settings"></a>

| Setting  | Key        | Type    | Meaning                          |
| -------- | ---------- | ------- | --------------------------------- |
| Interval | `interval` | integer | Seconds between each dig/drop.    |
| Drops    | `drops`    | list    | The items this level adds to the drop pool — each an entry (see below). |

Each entry in `drops` has four fields:

| Field       | Type    | Meaning                                                                        |
| ----------- | ------- | ------------------------------------------------------------------------------- |
| `item`      | item    | The item to drop — either a `minecraft:…` item/data-component string, or a `base64:…` code copied from `/petadmin info item` (see below). |
| `weight`    | integer | Relative odds of this entry being picked, ≥1. Equal weights across entries mean a uniform random pick. |
| `amountMin` | integer | Minimum stack size dropped, ≥1.                                                 |
| `amountMax` | integer | Maximum stack size dropped, ≥ `amountMin`.                                      |

Drop entries are cumulative: an entry added at one level stays in the pool at every level above it.

### Capturing an exact item <a href="#capture" id="capture"></a>

To grant an item with a custom name, lore, or enchantments, hold it in your main hand and run [`/petadmin info item`](../../../../player-guide/commands/admin-commands.md#petadmin) — click the **\[Copy]** button on the output to copy the item's exact `base64:…` string to your clipboard, then paste it as the `item` value.

```json
"Sniff": {
  "Upgrades": {
    "1": {
      "interval": 60,
      "drops": [
        { "item": "minecraft:wheat",   "weight": 10, "amountMin": 1, "amountMax": 3 },
        { "item": "minecraft:diamond", "weight": 3,  "amountMin": 1, "amountMax": 1 }
      ]
    }
  }
}
```
