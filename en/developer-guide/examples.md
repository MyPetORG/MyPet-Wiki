---
icon: lightbulb
description: Copy-paste recipes for common MyPet integrations.
---

# Examples

Each recipe below is a complete, drop-in `Listener` class. They assume you've already added the API dependency per the [Developer Guide](README.md). Register the listener in your plugin's `onEnable()`:

```java
getServer().getPluginManager().registerEvents(new YourListener(this), this);
```

{% hint style="info" %}
**Coming from MyPet 3.x?** All event class names changed (`MyPet*Event` → `Pet*Event`) and the `getMyPet()` accessor on each event is now `getPet()`. The recipes below already use the 4.0 names — see [Migrating from v3.x](migrating-from-v3.md) for the porting reference.
{% endhint %}

## Announce when a pet levels up

Broadcasts a server-wide message every time any pet levels up.

```java
package com.example.recipes;

import de.Keyle.MyPet.api.event.PetLevelUpEvent;
import net.kyori.adventure.text.Component;
import org.bukkit.Bukkit;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;

public final class LevelUpAnnouncer implements Listener {

    @EventHandler
    public void onLevelUp(PetLevelUpEvent event) {
        String owner = event.getOwner().getName();
        int newLevel = event.getLevel();
        Bukkit.broadcast(
            Component.text(owner + "'s pet just hit level " + newLevel + "!")
        );
    }
}
```

**How it works:** `PetLevelUpEvent` inherits `getLevel()` (the new post-level-up value) and `getOwner()` (a `MyPetPlayer`) from `PetLevelEvent`. Adventure's `Component.text()` produces the message and `Bukkit.broadcast(Component)` is the modern Paper broadcast API. Use `event.fromLevel()` if you also need the previous level — note the record-style accessor (no `get` prefix).

## Block pets from being called in a region

Cancels a pet-call attempt if the player is standing in a WorldGuard region named `no-pets`.

```java
package com.example.recipes;

import com.sk89q.worldedit.bukkit.BukkitAdapter;
import com.sk89q.worldguard.WorldGuard;
import com.sk89q.worldguard.protection.regions.RegionContainer;
import com.sk89q.worldguard.protection.regions.RegionQuery;
import de.Keyle.MyPet.api.event.PetCallEvent;
import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;

public final class NoPetsRegion implements Listener {

    @EventHandler
    public void onCall(PetCallEvent event) {
        Player player = event.getPlayer();
        if (player == null) return;

        RegionContainer container = WorldGuard.getInstance().getPlatform().getRegionContainer();
        RegionQuery query = container.createQuery();
        boolean inNoPets = query.getApplicableRegions(BukkitAdapter.adapt(player.getLocation()))
            .getRegions()
            .stream()
            .anyMatch(r -> r.getId().equalsIgnoreCase("no-pets"));

        if (inNoPets) {
            event.setCancelled(true);
            player.sendMessage("You can't summon your pet here.");
        }
    }
}
```

**How it works:** `PetCallEvent` implements `Cancellable`. We resolve the calling player from the event, look up WorldGuard regions at their current location, and cancel if any region is named `no-pets`.

{% hint style="info" %}
This recipe assumes WorldGuard is on the classpath. Add `softdepend: [WorldGuard]` to your `plugin.yml` and gate the listener registration behind a `Bukkit.getPluginManager().getPlugin("WorldGuard") != null` check if WorldGuard is optional.
{% endhint %}

## Award currency on level-up

Pays the pet's owner 100 currency units (via Vault) every time their pet levels up.

```java
package com.example.recipes;

import de.Keyle.MyPet.api.event.PetLevelUpEvent;
import net.milkbowl.vault.economy.Economy;
import org.bukkit.Bukkit;
import org.bukkit.OfflinePlayer;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;

public final class LevelUpReward implements Listener {

    private final Economy economy;

    public LevelUpReward(Economy economy) {
        this.economy = economy;
    }

    @EventHandler
    public void onLevelUp(PetLevelUpEvent event) {
        OfflinePlayer owner = Bukkit.getOfflinePlayer(event.getOwner().getUniqueId());
        economy.depositPlayer(owner, 100.0);
    }
}
```

**How it works:** Vault's `Economy` service is injected via the constructor — resolve it from `Bukkit.getServicesManager().getRegistration(Economy.class)` in your `onEnable()`. `MyPetPlayer#getUniqueId()` plus `Bukkit.getOfflinePlayer(...)` gives Vault an `OfflinePlayer` that `depositPlayer` accepts even when the owner isn't currently online — so a level-up that happens while the owner is logged out still pays out.

## Track pet creation by source

Counts how many pets are created via each `PetCreateEvent.Source` and logs a running tally.

```java
package com.example.recipes;

import de.Keyle.MyPet.api.event.PetCreateEvent;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;

import java.util.EnumMap;
import java.util.Map;
import java.util.logging.Logger;

public final class CreationStats implements Listener {

    private final Map<PetCreateEvent.Source, Integer> counts =
        new EnumMap<>(PetCreateEvent.Source.class);
    private final Logger logger;

    public CreationStats(Logger logger) {
        this.logger = logger;
    }

    @EventHandler
    public void onCreate(PetCreateEvent event) {
        counts.merge(event.getSource(), 1, Integer::sum);
        logger.info("Pet created (" + event.getSource() + "); totals: " + counts);
    }
}
```

**How it works:** `PetCreateEvent.Source` is a nested enum with values `LEASH`, `ADMIN_COMMAND`, `PET_SHOP`, and `OTHER`. An `EnumMap` keyed by the enum is the most efficient way to tally per-source counts. The event is *not* `Cancellable` — by the time it fires, the pet already exists.

## React to a skill on a successful hit

Spawns a particle effect at the pet's location whenever any on-hit skill (Fire, Poison, Thorns, etc.) is about to apply.

```java
package com.example.recipes;

import de.Keyle.MyPet.api.event.PetOnHitSkillEvent;
import org.bukkit.Particle;
import org.bukkit.entity.Mob;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;

public final class SkillSparkles implements Listener {

    @EventHandler
    public void onSkillHit(PetOnHitSkillEvent event) {
        Mob petEntity = event.getPet().getBukkitEntity();
        if (petEntity == null) return;

        petEntity.getWorld().spawnParticle(
            Particle.HAPPY_VILLAGER,
            petEntity.getLocation().add(0, 1, 0),
            10
        );
    }
}
```

**How it works:** `PetOnHitSkillEvent` fires once per landed hit that has an `OnHitSkill` attached, and it exposes the attacking pet via `getPet()`. `Pet#getBukkitEntity()` returns the underlying Bukkit `Mob` directly (or `null` if the pet was just despawned). We then spawn 10 happy-villager particles a block above the pet's head.

{% hint style="info" %}
The standalone "any active skill triggered" event from MyPet 3.x (`MyPetActiveSkillEvent`) was removed in 4.0 — the on-hit hook is the canonical replacement when you want to react to skill activations. Cancel `event` if you want to suppress the skill effect for this hit only.
{% endhint %}

---

Have a recipe to share? Open a PR against the [MyPet Wiki repository](https://github.com/MyPetORG/MyPet-Wiki).
