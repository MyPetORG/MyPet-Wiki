---
description: Frequently Asked Questions
---

# FAQ

## Is MyPet EULA compliant?

{% page-ref page="eula.md" %}

## Is there a max levelcap?

Yes, there are 3 ways to activate a level cap: 1. via [config](../setup/configurations/config.yml.md) 2. via [skilltrees](../systems/skilltrees/) 3. create your own [expjs](../systems/experience/expjs.md) and add a levelcap in there

## How can I equip my Zombie/Skeleton/PigZombie?

Just rightclick your pet with the item you want them to wear while sneaking. To remove the equipment just rightclick your pet with shears while sneaking. ![$](../.gitbook/assets/exclaim.gif) **Weapons/Armor are only visually and have no effect on the pet** ![$](../.gitbook/assets/exclaim.gif)

## How can I control my pet while riding it?

Riding a pet is like riding a horse with a saddle.

## How can I get a pet?

{% page-ref page="../tutorials/how\_to\_get\_a\_mypet.md" %}

## How can I feed my pet?

Firstly look what you pet wants as food here. Then just rightclick your pet while holding the food item in your hand. It will first increase the [saturation](../systems/hungersystem.md) of your pet your pet and when it is at 100 saturation it will heal it. Every food item has a **saturation** of **6points** and every missing saturation and HP will use **1 point**.

## Is there a way to have more than 1 pet?

No. You can only have **one** active pet at the same time. However you can _store_ pets and switch between them \([NPC](../hooks/npc.md) or [command](../setup/commands.md)\).

## Why does the pets on my server can't attack anything?

Your pets just don't have a damage skill \([Damage](../skills/damage.md) or [Ranged](../skills/ranged.md)\). Select a skilltree with a damage skill or add a damage skill to your existing skilltrees.

## Why can't I tame the Enderdragon?

ProtocolLib is required for the Enderdragon to be tame-able.

## Why doesn't the Enderdragon/Bat/Phantom etc; fly?

There is no Flying AI in Minecraft.  
Pets utilize the Tamed Wolf AI once they are tamed as a MyPet.

