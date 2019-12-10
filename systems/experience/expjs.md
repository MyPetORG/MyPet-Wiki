# Experience-Script

With the **Experience-Script** `exp.js` it's possible to customize when a pet will level up. As you can see at the file ending, the used language is **JavaScript**.

## Installation

1. Download [Rhino](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/Download_Rhino), rename the jar to `rhino.jar` and put the file into the MyPet folder.
2. Set `LevelSystem.CalculationMode` to **`JavaScript`** int the **`config.yml`.**
3. Edit the `exp.js` to your likings.

## Script

To make a fully functional exp-script that can be used by _MyPet_ you have to implement the following method:

{% code title="exp.js" %}
```javascript
function getExpByLevel(level, petType, worldGroup) {
  var exp = 0;
  return exp;
}
```
{% endcode %}

### **Differentiating between pet types and world groups**

Examples:

{% tabs %}
{% tab title="Pet Type" %}
{% code title="exp.js" %}
```javascript
function getExpByLevel(level, petType, worldGroup) {
  var exp = 10;
  if(petType == "Cow") {
    exp = 15;
  }
  return exp;
}
```
{% endcode %}
{% endtab %}

{% tab title="World Group" %}
{% code title="exp.js" %}
```javascript
function getExpByLevel(level, petType, worldGroup) {
  var exp = 10;
  if(worldGroup == "LuckyWorlds") {
    exp = 20;
  }
  return exp;
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Debugging

To provide an easy method to debug your scripts the plugin adds a print method to the usable JavaScript functions.

```javascript
print("message");
```

## Example

{% code title="exp.js" %}
```javascript
//  Level 2-16 cost 17 XP points each
//  Level 17-31 cost 3 more XP points than the previous
//  Level 32-∞ cost 7 more XP points than the previous

function getExpByLevel(level, petType, worldGroup) {
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
{% endcode %}

