# Experience-Script

With the **Experience-Script** `exp.js` it's possible to customize when a pet will level up. As you can see at the file ending, the used language is **JavaScript**.

## Script

### Result Methods

To make a fully functional exp-script that can be used by _MyPet_ you have to implement the following methods:

{% tabs %}
{% tab title="Function" %}
{% code-tabs %}
{% code-tabs-item title="exp.js" %}
```javascript
function getExpByLevel(level, mypet) {
  return exp;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="Lambda" %}
{% code-tabs %}
{% code-tabs-item title="exp.js" %}
```javascript
getExpByLevel = (level, mypet) => exp;
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}

**Usable Methods**

You can use the following methods to react individually on some pets:

* `MyPet.getType()` -&gt; pet-type of the _MyPet_.
* `MyPet.getOwnerName()` -&gt; name of the owner.
* `MyPet.getSkilltree()` -&gt; selected skilltree.
* `MyPet.getUUID()` -&gt; internal UUID of the _MyPet_.
* `MyPet.getWorldGroup()` -&gt; worldgroup the _MyPet_ is in.

If you have any questions related to this topic please contact me on Discord or the Spigot forums.

## Examples

You can find a working example [here](https://github.com/xXKeyleXx/MyPet/blob/master/experience-scripts/exp.js) \(it calculates it the same way as it was calculated for players in [Minecraft 1.3.1](http://www.minecraftwiki.net/wiki/Experience#Leveling_Up)\).

