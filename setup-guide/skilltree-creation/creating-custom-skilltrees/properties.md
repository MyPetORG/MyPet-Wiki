---
icon: sliders-up
---

# Properties

<figure><img src="../../.gitbook/assets/Skilltree Properties.webp" alt="The Properties of the MyPet Skilltree Creator showing the ID, Inheritance, and Weight fields." width="563"><figcaption></figcaption></figure>

The `Properties` tab of the [Skilltree Creator](./) allows you to configure the skilltree ID, Inheritance, and Weight.

### ID

The skilltree `ID` is the internal identifier used by the plugin. It is the same identifier used when selecting a skilltree using the `/petchooseskilltree [ID]` command. It is advisable to make this ID the same as the Skilltree Name on the [Appearance](appearance.md) tab.

### Inheritance

This option allows you to select a _parent_ skilltree that the current (_child_) skilltree will inherit from. The child skilltree will then contain all of the parent skilltree's skills **plus its own skills**. This can allow for many options including the use of a base set of skills that are built upon by several child skilltrees.

For example, if `Skilltree A` is our _parent_ skilltree and `Skilltree B` is our _child_ skilltree, and `Skilltree A` contains the [Backpack](skills/backpack.md) skill at Level 2 but _does not_ contain the Pickup skill, but `Skilltree B` contains the [Pickup](skills/pickup.md) skill at Level 2, then pets with just `Skilltree A` at Level 2 would **only** have the Backpack skill while pets with `Skilltree B` at Level 2 would have **both** Backpack and Pickup skills.

### Weight

The Skilltree `Weight` determines which skilltree should take precedence in the event of a conflict.
