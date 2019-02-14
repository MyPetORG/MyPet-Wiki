# Experience

As well as player, pets can also gain experience and level up. In each level they can get special [abilities](../../skills/) like [Backpack](../../skills/backpack.md).

There are two different ways the experience is converted into levels, etc at the moment.

## Default

`Default` is the default way the experience part is calculated. When `MyPet.LevelSystem.CalculationMode` is set to `default` all pets will level up like normal players would level up like in [Minecraft Pre-Snapshot 12w23a](https://minecraft.gamepedia.com/Experience#Values_of_Beta_1.8_-_Before_1.3.1_.2812w23a.29).

## [JavaScript](expjs.md)

This is the advanced way where you can create your own level behavior. When `MyPet.LevelSystem.CalculationMode` is set to `JS` or `JavaScript` the plugin uses the `exp.js` in the _MyPet_-folder to calculate the required experience to levelup. In order to use this feature the plugin needs the [rhino.jar](https://github.com/mozilla/rhino/releases) inside the _MyPet_ folder.

You can find an example [here](expjs.md#example) and a further discription [here](expjs.md). If you have any questions related to this topic please send me a message on [Discord ](http://discord.mypet-plugin.de)in the help channel.

