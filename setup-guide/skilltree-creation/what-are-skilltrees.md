---
description: >-
  Skilltrees are the way to specify when which pet will unlock/upgrade specified
  abilities.
icon: list-tree
---

# What are Skilltrees?

The Skilltree mechanism is a feature that allows Pets to learn Skills as they level up. You can think of Skilltrees like player classes (Archer, Swordsman, Wizard, etc.) but for Pets.&#x20;

MyPet 4 ships with [124 default skilltrees](default-skilltrees.md) arranged as a two-tier "Ascension Ladder". They are ordinary skilltrees built with the features described on these pages - fully customizable, and the ascension design itself is optional.

{% content-ref url="default-skilltrees.md" %}
[default-skilltrees.md](default-skilltrees.md)
{% endcontent-ref %}

### Skilltrees (.st.json)

This is a skilltree file. Every skilltree has its own file, which must be in proper json format and placed in the `plugins/MyPet/skilltrees` directory in your Minecraft server.

### Skills

[Skills](creating-custom-skilltrees/skills/) are the abilities that Pets gain as they level up. Any ability has its own custom option that can be set in the skilltrees.

### Upgrades

An upgrade will change the settings of a skill. It can add a row to the inventory or add more damage.\
Every upgrade is applied on a level rule that determines when it will be applied.\
An upgrade can be applied on fixed levels or on repeating schedules like every 3 levels.

### Inheritance

Skilltrees are capable of inheritance which means if **skilltree** `a` inherits from **skilltree** `b`, **skilltree** `a` will have all the upgrades from **skilltree** `b` in addition its own upgrades.
