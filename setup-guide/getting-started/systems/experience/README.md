---
icon: flask
---

# Experience

Like the player, pets can also gain experience and level up. In each level they can get special [abilities](../../../skilltree-creation/creating-custom-skilltrees/skills/) like [Backpack](../../../skilltree-creation/creating-custom-skilltrees/skills/backpack.md).

There are two different ways the experience is converted into levels, etc. at the moment.

{% stepper %}
{% step %}
### Default

`Default` is the default way the experience part is calculated. When `MyPet.LevelSystem.CalculationMode` is set to `Default` all pets will level up like normal players would level up like in [Minecraft Pre-Snapshot 12w23a](https://minecraft.wiki/w/Experience#Values_from_Java_Edition_Beta_1.8_to_1.3.1_\(12w23a\)).
{% endstep %}

{% step %}
### JavaScript

This is the advanced way where you can create your own level behavior. When `MyPet.LevelSystem.CalculationMode` is set to `JS` or `JavaScript` the plugin uses the `exp.js` in the `MyPet` folder to calculate the required experience to level up. In order to use this feature the plugin needs the [rhino.jar](https://github.com/mozilla/rhino/releases) inside the `MyPet` folder.

You can find an example [here](experience-script.md#example) and a further description [here](experience-script.md). If you have any questions related to this topic please send me a message on [Discord](http://discord.mypet-plugin.de/) in the help channel.
{% endstep %}
{% endstepper %}
