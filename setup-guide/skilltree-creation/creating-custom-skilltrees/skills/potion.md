---
description: Let your Pet throw splash potions — buffs for you, debuffs for your enemies.
icon: flask-round-potion
---

# Potion

The Potion skill turns your Pet into a field alchemist. The skilltree grants, per level, **which splash potions the Pet may throw** — its _arsenal_ — and gives each one its own cooldown. The Pet throws from real potions in its [Backpack](backpack.md) and aims each one automatically:

* **Helpful** potions (Healing, Strength, Speed, Fire Resistance, Night Vision, Regeneration, Water Breathing, …) are thrown at **you**.
* **Harmful** potions (Harming, Poison, Weakness, Slowness) are thrown at the **enemy your Pet is fighting**.

The Pet picks the most useful potion for the moment — an emergency heal outranks an attack, which outranks a buff — and throws **one per second** at most, so it never empties its cooldowns all at once. It only throws while it is spawned, you are online and within **16 blocks**, and it has a clear line of sight to the target — it won't waste a potion against a wall.

The Pet is never caught in its own splash, and **you are never hit by a harmful potion your Pet throws at an enemy**, even if you are standing right next to it. The Pet throws **the actual bottle you stocked**, so its strength and duration are whatever you provide — stock Splash Healing II and it throws Healing II. A grant is matched by **effect**, not exact tier: a "Healing" grant is satisfied by any healing splash potion you put in the backpack.

### Who gets hit <a href="#targeting" id="targeting"></a>

Harmful potions follow your Pet's **behaviour mode** (set in the pet menu, `/pet`) — the same setting that decides what your Pet attacks:

| Behaviour    | Harmful potions thrown at…                          |
| ------------ | --------------------------------------------------- |
| Friendly     | nobody — the Pet only throws helpful potions at you |
| Normal       | a mob once it attacks you or your Pet               |
| Aggressive   | nearby hostile mobs, on sight                       |
| Raid         | monsters, following raid targeting                  |
| Farm         | the animal your Pet is farming                      |
| Duel         | the duel opponent                                   |

### Stocking potions <a href="#stock" id="stock"></a>

By default the Pet needs the **actual splash potion in its [Backpack](backpack.md)** to throw it — granting a potion in the skilltree only _permits_ it. Each throw consumes one bottle. When a permitted potion has run out, the Pet skips it and reminds you to restock. This pairs naturally with [Backpack](backpack.md): give the Pet one and keep it stocked with the potions you want it to use.

Grant the **Materialize** upgrade (`materialize`) to remove the stock requirement — the Pet then conjures its permitted potions out of thin air, with an empty backpack (using the exact variant named in the grant). This makes a good high-level reward, mirroring the gathering skills' _No tool required_.

### Settings <a href="#settings" id="settings"></a>

| Setting     | Key           | Type    | Meaning                                                                    |
| ----------- | ------------- | ------- | -------------------------------------------------------------------------- |
| Potions     | `potions`     | list    | The potions this level adds to the arsenal — each an entry (see below).    |
| Materialize | `materialize` | boolean | When `true`, the Pet throws its permitted potions with no backpack stock.  |

Each entry in `potions` has two fields:

| Field      | Type    | Meaning                                                                          |
| ---------- | ------- | -------------------------------------------------------------------------------- |
| `type`     | potion  | The permitted potion, e.g. `minecraft:healing`. Any stocked splash potion of that **effect** satisfies it (Healing I, II, …); the editor lists every potion your server knows. |
| `cooldown` | integer | Seconds between throws of **this** potion.                                       |

The potion list in the editor is read live from your server, so any potions added by data packs or mods appear automatically — nothing is hardcoded. Grants are cumulative: a potion added at one level stays available at every level above it.

```json
"Potion": {
  "Upgrades": {
    "1": {
      "potions": [
        { "type": "minecraft:healing", "cooldown": 6 }
      ]
    },
    "5": {
      "potions": [
        { "type": "minecraft:strong_harming", "cooldown": 3 },
        { "type": "minecraft:long_strength", "cooldown": 30 }
      ]
    },
    "10": {
      "materialize": true
    }
  }
}
```
