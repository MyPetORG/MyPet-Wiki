# Custom-Item-Data in Config

It is possible to set the `item data` \(like wool color\) and `NBT data` \(like enchantments, name and lore\) for items in the MyPet config.

You have to provide the Item properties in this order:

* `1.13-Item-ID` `NBT-Data`

Example:

{% tabs %}
{% tab title="1.13" %}
`beef {display:{Name:"Wolf Food",Lore:["Tasty wolf food","Tastes like banana"]}}`
{% endtab %}

{% tab title="1.14" %}
`beef {"display":{"Name":"[{\"text\":\"Wolf Food\"}]","Lore":["{\"text\":\"Tasty wolf food\"}","{\"text\":\"Tastes like banana\"}"]}}`
{% endtab %}
{% endtabs %}

When you set the food of the wolf to this, a player needs an item that is like in this picture: ![Custom-Item-Example](../../.gitbook/assets/configitem.png) 

This will allow server owners to set the food and leash items \(and some other items used by MyPet\) to items that can only be obtained by shops etc.

## Item generators

You can create any item you want but sometimes MyPet will not recognize these items. This happens because the item comparison is very harsh in MyPet. To make it easier to setup config items the plugin now has the `/petadmin info item` command. This command will output the item you are currently holding in your main hand to the server logs \(don't copy from console\). Copy and paste this output to your config and it should work fine.

You can use item generators from various site like these:

* [http://mapmaking.fr/give/](http://mapmaking.fr/give/)
* [https://ezekielelin.com/give/](https://ezekielelin.com/give/)
* [https://minecraftcommand.science/de/custom-item-generator](https://minecraftcommand.science/de/custom-item-generator)

Just copy the generated command and remove the `/give @a`.

## NBT data

The syntax for the NBT data is the same like in the `/give` command in _Minecraft_. You can find all possible NBT properties [here](http://www.minecraftwiki.net/wiki/Player.dat_Format#Item_structure) or just use one of the generators from above.

