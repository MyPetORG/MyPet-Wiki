---
icon: sitemap
---

# Custom-Item-Data in Config

It is possible to set the item data (like wool color) and NBT data (like enchantments, name and lore) for items in the MyPet config.

You have to provide the Item properties in this order:

* `Item-ID`  `NBT-Data`

Example:

{% tabs %}
{% tab title="1.21" %}
```json
beef[item_name="Wolf Food",lore=["Tasty wolf food","Tastes like banana"]]
```
{% endtab %}

{% tab title="1.14" %}
```json
beef {"display":{"Name":"[{\"text\":\"Wolf Food\"}]","Lore":["{\"text\":\"Tasty wolf food\"}","{\"text\":\"Tastes like banana\"}"]}}
```
{% endtab %}

{% tab title="1.13" %}
```json
beef {display:{Name:"Wolf Food",Lore:["Tasty wolf food","Tastes like banana"]}}
```
{% endtab %}
{% endtabs %}

When you set the food of the wolf to this, a player needs an item that is like in this picture:\
![Custom-Item-Example](<../../.gitbook/assets/image (8)>)

This will allow server owners to set the food and leash items (and some other items used by MyPet) to items that can only be obtained by shops, etc.

### Item generators

You can create any item you want but sometimes MyPet will not recognize these items. This happens because the item comparison is very strict in MyPet. To make it easier to set up config items the plugin has the `/petadmin info item` command. Hold the item in your main hand, run the command, and click one of the two buttons in the output to copy it to your clipboard:

* **\[Copy]** gives the material name (`SHEARS`) — matches any item of that type.
* **\[Copy with NBT]** gives the full component string (`. minecraft:shears[minecraft:damage=6]`) — matches only that exact item, including its name, lore, enchantments and damage.

Paste the copied value into your config and it should work fine. Run the command as a player, not from the console.

You can use item generators from various sites like these:

* [https://mapmaking.fr/give1.21/](https://mapmaking.fr/give1.21/)
* [https://mcstacker.net/?cmd=give](https://mcstacker.net/?cmd=give)

Just copy the generated command and remove the `/give @a`.

### Item Components/NBT data

The syntax for the NBT data is the same as in the `/give` command in Minecraft. You can find all possible NBT properties [here](https://minecraft.wiki/w/Data_component_format#Item_format) or just use one of the generators from above.
