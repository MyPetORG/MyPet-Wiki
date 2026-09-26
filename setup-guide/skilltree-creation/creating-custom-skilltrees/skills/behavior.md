---
description: Change the behavior of your Pet.
icon: people-arrows
---

# Behavior

With this skill you can change the behavior of the pet. There are 6 behavior-modes:

* `normal` -> behaves like a normal tamed wolf.
* `friendly` -> the pet doesn't fight, even when being attacked.
* `aggressive` -> attacks everything within 15 blocks of the owner.
* `farm` -> attacks every **monster** within 15 blocks of the owner.
* `raid` -> similar to normal behavior, but the pet doesn't attack players and their minions.
* `duel` -> pets will attack other pets with active duel behavior within a 5 block radius.

To toggle the behavior mode, use the command `/petbehavior [`**`normal`**`/`**`friendly`**`/`**`aggressive`**`/`**`farm`**`/`**`raid`**`/`**`duel`**`]`.

`normal` is always available. **Every other mode has to be unlocked by the skilltree** — a pet whose skilltree never grants Behavior is stuck in `normal`, and `/petbehavior` will not appear in its help output.

### Settings <a href="#settings" id="settings"></a>

Each mode is its own boolean. There is no numeric value to raise: the mode is either unlocked at that level or it isn't.

| Setting    | Key      | Type    | Meaning                                     |
| ---------- | -------- | ------- | ------------------------------------------- |
| Friendly   | `Friend` | boolean | Unlocks the `friendly` mode.                |
| Aggressive | `Aggro`  | boolean | Unlocks the `aggressive` mode.              |
| Farm       | `Farm`   | boolean | Unlocks the `farm` mode.                    |
| Raid       | `Raid`   | boolean | Unlocks the `raid` mode.                    |
| Duel       | `Duel`   | boolean | Unlocks the `duel` mode.                    |

```json
"Behavior": {
  "Upgrades": {
    "5":  { "Duel": true, "Friend": false, "Aggro": false, "Farm": false, "Raid": false },
    "14": { "Duel": true, "Friend": true,  "Aggro": true,  "Farm": false, "Raid": false }
  }
}
```

{% hint style="warning" %}
**Restate every mode in every row.** A `false` does not mean "leave alone" — it actively **removes** that mode, and the last row the pet has reached wins outright. In the example above, level 14 has to repeat `"Duel": true`; if it only listed `Friend` and `Aggro`, the pet would silently lose duelling at level 14.
{% endhint %}

### In the default skilltrees <a href="#in-the-default-skilltrees" id="in-the-default-skilltrees"></a>

Every [default skilltree](../../default-skilltrees.md) grants Behavior. `duel` and `friendly` are baseline everywhere; `aggressive`, `farm` and `raid` depend on the pet's family or habitat path — see [Behavior modes](../../default-skilltrees.md#behavior-modes).

### Demonstration <a href="#demonstration" id="demonstration"></a>

![](https://wiki.mypet-plugin.de/~gitbook/image?url=https%3A%2F%2F3869790376-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-LXhRZyUgDZpPIQrYK1o%252F-LXxWKQYf9wXYs_gqnV-%252F-LXxWfDqndwXgczPNHJ5%252Fbehavior.gif%3Falt%3Dmedia%26token%3D3c0f82ff-8860-4f47-ba65-297d5f4e480b\&width=768\&dpr=4\&quality=100\&sign=13ff9d76\&sv=2)
