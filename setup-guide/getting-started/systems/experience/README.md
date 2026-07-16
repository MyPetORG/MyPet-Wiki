---
icon: flask
---

# Experience

Like the player, pets can also gain experience and level up. In each level they can get special [abilities](../../../skilltree-creation/creating-custom-skilltrees/skills/) like [Backpack](../../../skilltree-creation/creating-custom-skilltrees/skills/backpack.md).

How much experience a pet needs for each level is decided by the **calculation mode**, set with `MyPet.LevelSystem.CalculationMode` in the [config.yml](../../configuration/config.yml.md#levelsystem). There are four modes to choose from, and the mode names are not case-sensitive.

Every mode describes the **total** experience needed to reach a level, not the amount gained since the previous level. Level 1 always costs `0`.

{% tabs %}
{% tab title="Default" %}
### Default

The default mode, used when `CalculationMode` is set to `Default` (or `MyPet`). Pets level up like players did in [Minecraft Pre-Snapshot 12w23a](https://minecraft.wiki/w/Experience#Values_from_Java_Edition_Beta_1.8_to_1.3.1_\(12w23a\)): level 2 costs `7`, and each level after that costs `3.5` more than the one before it.

This mode has no settings to tweak. If you want to shape the curve yourself, use one of the three modes below.
{% endtab %}

{% tab title="Linear" %}
### Linear

Every level costs the same amount. Set `CalculationMode` to `Linear`.

`exp = Base * (level - 1)`

| Setting                               | Default | Description                       |
| ------------------------------------- | ------- | --------------------------------- |
| `MyPet.LevelSystem.Curve.Linear.Base` | `17.0`  | Experience needed for each level. |

With the default `Base` of `17.0`, level 2 costs `17`, level 3 costs `34`, level 10 costs `153`, and so on.
{% endtab %}

{% tab title="Power" %}
### Power

Each level costs more than the last, and the increase itself grows as the pet levels up. Set `CalculationMode` to `Power`.

`exp = sum of (Factor * level^Exponent) for every level below this one`

| Setting                                  | Default | Description                                                                                |
| ---------------------------------------- | ------- | ------------------------------------------------------------------------------------------ |
| `MyPet.LevelSystem.Curve.Power.Factor`   | `7.0`   | Scales the whole curve. Raise it to make every level more expensive.                        |
| `MyPet.LevelSystem.Curve.Power.Exponent` | `1.5`   | How sharply the cost accelerates. `1.0` behaves like `Linear`, higher values climb faster.  |
{% endtab %}

{% tab title="Exponential" %}
### Exponential

Each level costs a fixed **percentage** more than the one before it. Set `CalculationMode` to `Exponential`.

`exp = Base * (Growth^(level - 1) - 1) / (Growth - 1)`

| Setting                                      | Default | Description                                                                      |
| -------------------------------------------- | ------- | -------------------------------------------------------------------------------- |
| `MyPet.LevelSystem.Curve.Exponential.Base`   | `10.0`  | Experience needed for level 2 — the starting point of the curve.                 |
| `MyPet.LevelSystem.Curve.Exponential.Growth` | `1.1`   | Cost multiplier per level. `1.1` means each level costs 10% more than the last.   |

A `Growth` of exactly `1.0` makes every level cost `Base`, which is the same as the `Linear` mode.

{% hint style="warning" %}
Exponential curves get expensive very quickly. Check where your curve lands at your `MyPet.Exp.LevelCap` before using it on a live server.
{% endhint %}
{% endtab %}
{% endtabs %}

## Notes

{% hint style="info" %}
**Values are clamped.** `Base`, `Factor` and `Growth` are forced to a minimum of `0.000001`. A curve that flattens out or goes down would leave a pet unable to ever reach the next level, so the plugin refuses to build one.
{% endhint %}

{% hint style="info" %}
**Changing a curve clears the cache.** MyPet caches the calculated experience thresholds in the `exp.cache` file. When you change the mode or any curve setting and run `/mypet reload`, the plugin notices and recalculates it, logging `Current Exp-Cache is invalid, it will be recalculated.` to the console.
{% endhint %}

{% hint style="warning" %}
**Unknown modes fall back to Default.** If `CalculationMode` is set to something MyPet does not know, it logs `Unknown experience CalculationMode '<x>'; using the default (MyPet) curve.` and uses the `Default` curve.
{% endhint %}

## Upgrading from the JavaScript experience-script

Before MyPet 4, `CalculationMode` also accepted `JS` / `JavaScript`, which ran an `exp.js` script through the [Rhino](https://github.com/mozilla/rhino) engine. **This mode has been removed** and replaced by the `Linear`, `Power` and `Exponential` modes above.

If you are upgrading a server that used it:

* `CalculationMode: JS` is no longer valid. It falls back to the `Default` curve with the warning above, so pick one of the four modes instead.
* The `exp.js` and `rhino.jar` files in your `MyPet` folder are no longer read by the plugin and can be deleted.
* To keep a similar curve, match your old script to a mode: a flat cost per level is `Linear`, a cost that accelerates is `Power`, and a percentage increase per level is `Exponential`.

If you had a script that none of the modes can reproduce, please tell us about it on [Discord](http://discord.mypet-plugin.de/) in the help channel.
