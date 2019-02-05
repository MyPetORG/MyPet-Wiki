---
description: >-
  Skilltrees are the way to specify when which pet will unlock/upgrade which
  abilities.
---

# Skilltrees

 You can think of skilltrees like classes for players \(for example knight and archer\).

#### Skilltrees \(.st.json\)

This is a skilltree file. Every skilltree has it's own file.

#### Skills

Any Ability has it's own custom option that can be set in the skilltrees.

#### Upgrades

An upgrade will change the settings of a skill. It can add a row to the inventory or add more damage.  
Every upgrade is applied on a level rule that determines when it will applied.  
An upgrade can be applied on fixed levels or on repeating schedules like every 3 level.

### Inheritance

Skilltrees are capable of inheritance which means if **skilltree** `a` inherits from **skilltree** `b`, **skilltree** `a` will have all the upgrades form **skilltree** `b` and in adition to the own upgrades.

