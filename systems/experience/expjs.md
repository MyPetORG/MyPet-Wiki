# Experience-Script

With the **Experience-Script** `exp.js` it's possible to customize when a pet will level up. As you can see at the file ending, the used language is **JavaScript**.

## Installation

1. Download [Rhino](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/Download_Rhino) and put the `rhino.jar`/`rhino-1.7.9.jar`/`rhino-1.7.10.jar` into the MyPet folder.
2. Set `LevelSystem.CalculationMode` to **`JavaScript`** int the **`config.yml`.**
3. Edit the `exp.js` to your likings.

## Script

To make a fully functional exp-script that can be used by _MyPet_ you have to implement the following method:

{% code-tabs %}
{% code-tabs-item title="exp.js" %}
```javascript
function getExpByLevel(level, petType, worldGroup) {
  var exp = 0;
  return exp;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### **Differentiating between pet types and world groups**

Examples:

{% tabs %}
{% tab title="Pet Type" %}
{% code-tabs %}
{% code-tabs-item title="exp.js" %}
```javascript
function getExpByLevel(level, petType, worldGroup) {
  var exp = 10;
  if(petType == "Cow") {
    exp = 15;
  }
  return exp;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="World Group" %}
{% code-tabs %}
{% code-tabs-item title="exp.js" %}
```javascript
function getExpByLevel(level, petType, worldGroup) {
  var exp = 10;
  if(worldGroup == "LuckyWorlds") {
    exp = 20;
  }
  return exp;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}
{% endtabs %}

If you have any questions related to this topic please contact me on Discord or the Spigot forums.

## Example

{% code-tabs %}
{% code-tabs-item title="exp.js" %}
```javascript
//  Level 2-16 cost 17 XP points each
//  Level 17-31 cost 3 more XP points than the previous
//  Level 32-∞ cost 7 more XP points than the previous

function getExpByLevel(level, petType, worldGroup) {
    if (level <= 1) {
        return 0;
    }
    var exp = 0, i;
    if (level > 31) {
        exp = 887;
        level -= 31;
        for (i = 1; i < level; i++) {
            exp += 62 + (i * 7);
        }
        return exp;
    }
    if (level > 17) {
        exp = 272;
        level -= 17;
        for (i = 1; i <= level; i++) {
            exp += 17 + (i * 3);
        }
        return exp;
    }
    return (level - 1) * 17;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

