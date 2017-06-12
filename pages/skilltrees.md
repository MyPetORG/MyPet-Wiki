# Skilltrees

**Skilltree**s are the way to specify when which pet will unlock/upgrade which abilities.
You can think of skilltrees like classes for players (for example knight and archer).

### Skilltrees

Within the pet-type-file you can create the **skilltree**. Each **skilltree** needs its own name, which means that you aren't allowed to create **2 or more** skilltrees with **the same name** in the same file.
If you create more than one, only the first will be used.
### Level

Within a skilltree you can specify from which levels the pet should get a new ability or rather when existing abilities should be updated.

### Skills

Within the levels you can specify which ability will be learnd or should be updated.
Any Ability has it's own custom option that can be set in the skilltrees.
## Inheritance

**Skilltree**s are capable of inheritance which means if **skilltree** `a` inherits from **skilltree** `b`, **skilltree** `a` will have all the settings form **skilltree** `b` and in adition to the own settings.
The inheritance of already inherted skills can be disabled by setting <font color="coral">MyPet.Skilltree.InheritAlreadyInheritedSkills</font> to `false`.
