---
icon: sliders-up
---

# Properties

<figure><img src="../../.gitbook/assets/Skilltree Properties.webp" alt="The Properties section showing the ID, Inheritance, and Weight fields." width="563"><figcaption></figcaption></figure>

The `Properties` section of the [Configurator's](./) Inspector allows you to configure the skilltree ID, Inheritance, and Weight.

### ID

The skilltree `ID` is the internal identifier used by the plugin. It is the same identifier used when selecting a skilltree using the `/petchooseskilltree [ID]` command. It is advisable to make this ID the same as the Skilltree Name in the [Appearance](appearance.md) section.

### Inheritance

This option allows you to select a _parent_ skilltree that the current (_child_) skilltree will inherit from. The child skilltree will then contain all of the parent skilltree's skills **plus its own skills**. This can allow for many options including the use of a base set of skills that are built upon by several child skilltrees.

For example, if `Skilltree A` is our _parent_ skilltree and `Skilltree B` is our _child_ skilltree, and `Skilltree A` contains the [Backpack](skills/backpack.md) skill at Level 2 but _does not_ contain the Pickup skill, but `Skilltree B` contains the [Pickup](skills/pickup.md) skill at Level 2, then pets with just `Skilltree A` at Level 2 would **only** have the Backpack skill while pets with `Skilltree B` at Level 2 would have **both** Backpack and Pickup skills.

### Weight

The Skilltree `Weight` sets the relative probability of this skilltree being picked when a skilltree is assigned randomly (`MyPet.Skilltree.RandomAssignment` in [config.yml](../../getting-started/configuration/config.yml.md#skilltree)). Higher values make the tree more likely; the default is `1.0`.

Since MyPet 4 the weight can also differ per pet type by writing a map instead of a number in the `.st.json` file:

```json
"Weight": {
  "Default": 2.0,
  "Horse": 3.0
}
```

`Default` applies to every pet type without an explicit entry. The Configurator's Weight field currently edits the single-number form; per-type weights are maintained directly in the file.
