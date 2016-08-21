# Experience

As well as player, *MyPet*s can also gain experience and level up.\\
In each level they can get special [abilities](en/skills) like [Inventory](en/skills/backpack).
----
 There are two different ways the experience is converted into levels, etc at the moment.

## The normal Way

The normal way aka ''Default'' is the default way the experience part is calculated.
When `<color Coral>`MyPet.LevelSystem.CalculationMode`</color>` is set to ''default'' all *MyPet*s will level up like normal players would level up like in [Minecraft Pre-Snapshot 12w23a](http://www.minecraftwiki.net/wiki/Experience#Pre-Snapshot_12w23a).

## JavaScript

This is the advanced way where you can create your own level behavior. When `<color Coral>`MyPet.LevelSystem.CalculationMode`</color>` is set to ''JS'' or ''JavaScript'' the plugin used the ''exp.js'' in the *MyPet*-pluginfolder to calculate everything. In order to use this feature the plugin needs the [rhino.jar](https///github.com/mozilla/rhino/releases) inside the *MyPet* folder (//since MyPet 1.2.3//).

You can find an example [here](https///github.com/xXKeyleXx/MyPet/blob/master/experience-scripts/exp.js) and a further discription [here](expjs).
`<box red>`If you have any questions related to this topic please send me a [private message](http://dev.bukkit.org/home/send-private-message/?to=xXKeyleXx) on BukkitDev`</box>`
