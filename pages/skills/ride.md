# Ride

With this skill you can ride your pet. To mount your pet rightclick your pet with the item specified in the config \(MyPet.Skill.Ride.Item\). Riding your pet is like riding a horse.

When you bought the ![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/premium.gif) premium version of MyPet you can also fly with your pet when it's enabled by your [skilltree](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/skills/skilltrees/README.md).

The ride speed \(and the ability to fly ![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/premium.gif)\) can be set via the [skilltree](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/skills/skilltrees/README.md) skill settings.

Even very small speed values will increase the speed a lot, so be carefully.

## Fly Zones

![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/premium.gif) _Fly Zones_ can be used to prevent/allow flying in certain [WorldGuard](http://dev.bukkit.org/bukkit-plugins/worldguard/) regions. Regions with higher priorities will overwrite regions with a lower priority.

### Example:

This setup prevents players to fly their pet in the world `Survival` but allows it when they are in the `spawn` region.

```text
MyPet:
  Skill:
    Ride:
      FlyZones:
        Survival::spawn: true
        Survival::__global__: false
`</code>`
`<code yaml regions.yml>`
regions:
    spawn:
        priority: 200
    __global__:
        priority: 100
```

## Demonstration

![Ride](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/skills/ride.gif)

