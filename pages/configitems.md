# Custom-Item-Data in Config

Since MyPet-1.1.4 it is possible to set the `item data` (like wool color) and `NBT data` (like enchantments, name and lore) for items in the MyPet config.

You have to provide the Item properties in this order:

*  <font color="green">Item-ID</font> <font color="Purple">Item-Data</font> <font color="blue">NBT-Data</font>

----

Example:

*  <font color="green">363</font> <font color="Purple">0</font> <font color="blue">{display:{Name:"Wolf Food",Lore:["Tasty wolf food","Tastes like banana"]}}</font><br>
When you set the food of the wolf to this, a player needs an item that is like in this picture:
{{ :images:configitem.png?nolink&200 |}}
This will allow server owners to set the food and leash items (and some other items used by MyPet) to items that can only be obtained by shops etc.

## NBT data

The syntax for the NBT data is the same like in the `/give` command in *Minecraft 1.7*. You can find all possible NBT properties [here](http://www.minecraftwiki.net/wiki/Player.dat_Format#Item_structure). A detailed description will follow soon (hopefully).

