# Custom-Item-Data in Config

Since MyPet-1.1.4 it is possible to set the `item data` (like wool color) and `NBT data` (like enchantments, name and lore) for items in the MyPet config.

You have to provide the Item properties in this order:

*  <font color="green">Item-ID/Item-Name</font> <font color="Purple">Item-Data</font> <font color="blue">NBT-Data</font>

Examples:

*  <font color="green">363</font> <font color="Purple">0</font> <font color="blue">{display:{Name:"Wolf Food",Lore:["Tasty wolf food","Tastes like banana"]}}</font>
*  <font color="green">minecraft:beef</font> <font color="Purple">0</font> <font color="blue">{display:{Name:"Wolf Food",Lore:["Tasty wolf food","Tastes like banana"]}}</font>

When you set the food of the wolf to this, a player needs an item that is like in this picture:
![Custom-Item-Example](/wiki/images/configitem.png)
This will allow server owners to set the food and leash items (and some other items used by MyPet) to items that can only be obtained by shops etc.

----

## Item generators
You can also use item generators from various site like these:
* [http://mapmaking.fr/give/](http://mapmaking.fr/give/)
* [https://ezekielelin.com/give/](https://ezekielelin.com/give/)
* [https://minecraftcommand.science/de/custom-item-generator](https://minecraftcommand.science/de/custom-item-generator)

Just copy the generated command and remove the `/give @a`.

----

## NBT data

The syntax for the NBT data is the same like in the `/give` command in *Minecraft*. You can find all possible NBT properties [here](http://www.minecraftwiki.net/wiki/Player.dat_Format#Item_structure) or just use one of the generators from above.

