---
description: >-
  Leash Flags are the requirements that a mob needs to meet in order to become a
  pet.
icon: dog-leashed
---

# Leash Flags / Requirements

All Leash Flags can be combined with each other but some only apply to certain mob types, some require other plugins, and some will overwrite others depending on the order they are written in the pet-config.yml.

### Impossible

* If this is a requirement every other LeashFlags will be ignored and you can't make this mob type a pet.

### LowHP

* Mob types with this LeashFlag need to be lower than 10% of their max health.

### Baby

* Mob types with this LeashFlag need to be a baby.

### Adult

* Mob types with this LeashFlag need to be grown up.

### Tamed

* Mob types with this LeashFlag need to be tamed.
* Can only be applied to animals that can be tamed.

### UserCreated

* Mob types with this LeashFlag need to be constructed by a player.
* Can only be applied to Copper, Iron, and Snow Golems.

### Wild

* Mob types with this LeashFlag need to be wild.
* Can only be applied to Wolves, Ocelots and Iron Golems.

### CanBreed

* Mob types with this LeashFlag need to be willing to breed.
* Can only be applied to animals that can be bred.

### Angry

* Mob types with this LeashFlag need to be angry.
* Can only be applied to wolves.

### HeartLinked&#x20;

* Mob types with this LeashFlag must be linked to a [Creaking Heart](https://minecraft.wiki/w/Creaking_Heart).
* Can only be applied to creaking.

### World flag

* Syntax:

```yaml
World:<world name>:...
```

* Examples:

```yaml
World:default
World:default:nether
```

### Size flag

* Can only be applied to slimes and magma cubes.
* Syntax options:

```yaml
Size:min=<min size>:max=<max size>
```

* `min` is optional.
* `max` is optional.
* Exact size syntax:

```yaml
Size:<exact size>
```

* Examples:

```yaml
Size:min=2
Size:min=2:max=4
Size:max=2
Size:3
```

### BelowHP

* Checks if a mob is below a certain health threshold.
* Syntax:

```yaml
BelowHP:<health>[%]
```

* `%` is optional.
* Examples:

```yaml
BelowHP:2
BelowHP:2.5
BelowHP:10%
```

### Chance

* With this flag you can add a random factor to the leashing.
* Syntax:

```yaml
Chance:<chance>
```

* `<chance>` is the chance in percent (%).
* Examples:

```yaml
Chance:2
Chance:50
```

### mcMMO

* Checks if a player has a skill above a certain level.
* Syntax:

```yaml
mcMMO:<job>=<level>:...
```

* If multiple jobs are specified all requirements must be fulfilled.
* Examples:

```yaml
mcMMO:Mining=10
mcMMO:Mining=2:Taming=25
```

### MythicMobs

* Checks if a mob is from a specific MythicMob type.
* Syntax:

```yaml
MythicMobs:<type name>:...
```

* Examples:

```yaml
MythicMobs:SkeletalKnight
MythicMobs:StaticallyChargedSheep:SkeletonKing
```

{% hint style="info" %}
If you use MythicMobs or ItemsAdder to spawn modeled creatures in the world, players can tame them as custom pets. See [Custom Pet Models](custom-pet-models.md) for how to set this up.
{% endhint %}
