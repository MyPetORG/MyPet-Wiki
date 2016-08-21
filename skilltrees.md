# Skilltrees

**Skilltree**s are the way to specify when which *MyPet* will unlock/upgrade which abilities.\\ You can think of skilltrees like classes for players (for example knight and archer).\\

### Skilltrees

Within the pet-type-file you can create the **skilltree**. Each **skilltree** needs its own name, which means that you aren't allowed to create **2 or more** skilltrees with **the same name** in the same file.
If you create more than one, only the first will be used.
### Level

Within a skilltree you can specify from which levels the *MyPet* should get a new ability or rather when existing abilities should be updated. 

### Skills

Within the levels you can specify which ability will be learnd or should be updated.
Any Ability has it's own custom option that can be set in the skilltrees.\\
## Inheritance

**Skilltree**s are capable of inheritance which means if **skilltree** ''a'' inherits from **skilltree** ''b'', **skilltree** ''a'' will have all the settings form **skilltree** ''b'' and in adition to the own settings.
The inheritance of already inherted skills can be disabled by setting `<color coral>`MyPet.Skilltree.InheritAlreadyInheritedSkills`</color>` to ''false''.

## The structure

The struckture of the **skilltree**s is easy.\\
For each *MyPet*-type exists a file (`<//MyPet///-type>`.st'') in which the **skilltree**s of the *MyPet*-types are saved. There is a file ''default.st'' too, that applies for all *MyPet*-types. The priority of the specific *MyPet*-type files is higher than the ''default.st'' which means that you can override the default **skilltree** for specific *MyPet*-types.\\

At the first start of the plugin it will create a folder in the plugin directory named ''skilltrees''  in which the **skilltree**-files have to be saved. 
