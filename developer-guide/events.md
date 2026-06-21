---
icon: bell
description: Listen for and modify pet behavior via the MyPet event API.
---

# Events

MyPet publishes 23 event classes in the `de.Keyle.MyPet.api.event` package. They integrate with Bukkit's standard `Listener` / `@EventHandler` pattern. Some implement `Cancellable`; others carry mutable getters and setters that let you change behavior without cancelling.

{% hint style="info" %}
**Threading note:** Most events fire on the main server thread and may freely call Bukkit APIs. A few (`PetSaveEvent` in particular) may fire from `CompletableFuture` callbacks driven by the persistence layer — check the relevant entry below before scheduling sync-only work from a handler.
{% endhint %}

{% hint style="warning" %}
**Migrating from MyPet 3.x?** Every event class was renamed from `MyPet*Event` to `Pet*Event`, the `getMyPet()` accessor on each event is now `getPet()`, and the nested source / action / result enums moved from `PascalCase` to `UPPER_SNAKE_CASE` (e.g. `Source.Leash` is now `Source.LEASH`). Two events — `MyPetActiveSkillEvent` and `MyPetActiveTargetSkillEvent` — were removed outright. See [Migrating from v3.x](migrating-from-v3.md) for the full porting guide.
{% endhint %}

## How to listen

Implement `org.bukkit.event.Listener`, mark your handler methods with `@EventHandler`, and register the listener in your plugin's `onEnable()`:

```java
package com.example.mypetintegration;

import de.Keyle.MyPet.api.event.PetLevelUpEvent;
import org.bukkit.event.EventHandler;
import org.bukkit.event.EventPriority;
import org.bukkit.event.Listener;
import org.bukkit.plugin.java.JavaPlugin;

public final class MyPlugin extends JavaPlugin implements Listener {

    @Override
    public void onEnable() {
        getServer().getPluginManager().registerEvents(this, this);
    }

    @EventHandler(priority = EventPriority.NORMAL)
    public void onLevelUp(PetLevelUpEvent event) {
        getLogger().info(event.getOwner().getName() + "'s pet leveled up!");
    }
}
```

Use `EventPriority` to control ordering relative to other plugins listening for the same event. For events that mutate values (e.g. `PetDamageEvent#setDamage`), prefer `MONITOR` only for read-only inspection — modifications belong on `LOWEST`–`HIGHEST`.

---

## Lifecycle

### PetCreateEvent

Fires when a new pet enters a player's collection — via leashing, the pet shop, or an admin command. Not cancellable; by the time it fires the pet already exists. Carries a nested `Source` enum (`LEASH`, `ADMIN_COMMAND`, `PET_SHOP`, `OTHER`).

**Accessors**

* `getSource()` — which path created this pet
* `getPet()` — the new `StoredPet`
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onCreate(PetCreateEvent event) {
    if (event.getSource() == PetCreateEvent.Source.LEASH) {
        event.getPlayer().sendMessage("You tamed a new pet!");
    }
}
```

### PetLoadEvent

Fires when a pet is loaded from the repository — typically the first time its owner is seen on the server after a restart. Not cancellable.

**Accessors**

* `getPet()` — the loaded `StoredPet`
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player` (may be null if the owner is not online yet)

```java
@EventHandler
public void onLoad(PetLoadEvent event) {
    getLogger().info("Loaded pet for " + event.getOwner().getName());
}
```

### PetCallEvent

`Cancellable`

Fires when an owner summons their pet into the world. Cancelling prevents the pet from spawning. The pet exposed via `getPet()` is guaranteed to be live (skills loaded, NBT applied) when this event fires — see the [migration notes](migrating-from-v3.md#petcallevent-getpet-narrowed-return-type) if you're porting code that expected the old `StoredMyPet` base type.

**Accessors**

* `getPet()` — the live `Pet` being summoned
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onCall(PetCallEvent event) {
    if (event.getPlayer().getWorld().getName().equals("nopvp")) {
        event.setCancelled(true);
    }
}
```

### PetSendAwayEvent

`Cancellable`

Fires when an owner sends their pet away (despawning it back to storage). Cancelling keeps the pet present.

**Accessors**

* `getPet()` — the `StoredPet` being sent away
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onSendAway(PetSendAwayEvent event) {
    event.getPlayer().sendMessage("Your pet returns to its slumber.");
}
```

### PetSaveEvent

Fires when a pet is persisted to the configured repository. Not cancellable.

**Accessors**

* `getPet()` — the `StoredPet` being saved
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

{% hint style="warning" %}
Save operations may run on a worker thread when using a remote backend (e.g. MySQL). Schedule any Bukkit-API work back to the main thread with `Bukkit.getScheduler().runTask(...)` if needed. On Folia, hop to a region scheduler instead.
{% endhint %}

```java
@EventHandler
public void onSave(PetSaveEvent event) {
    getLogger().fine("Persisted pet " + event.getPet().getUUID());
}
```

### PetRemoveEvent

Fires when a pet is removed from its owner's collection. Not cancellable. Carries a nested `Source` enum (`RELEASE`, `DEATH`, `ADMIN_COMMAND`, `OTHER`) explaining why.

**Accessors**

* `getSource()` — why the pet was removed
* `getPet()` — the removed `StoredPet`
* `getOwner()` — the (former) owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onRemove(PetRemoveEvent event) {
    if (event.getSource() == PetRemoveEvent.Source.DEATH) {
        event.getPlayer().sendMessage("Your pet has fallen.");
    }
}
```

### PetPlayerJoinEvent

Fires when a `MyPetPlayer` joins the server (separate from Bukkit's own `PlayerJoinEvent` so MyPet-aware code can reliably react after the player's pet data is ready). Not cancellable.

**Accessors**

* `getPlayer()` — the joining `MyPetPlayer`

{% hint style="warning" %}
**v4 break:** `getPlayer()` returns `MyPetPlayer`, not Bukkit `Player`. If you need the Bukkit `Player`, call `event.getPlayer().getPlayer()`. `MyPetPlayer.sendMessage` takes an Adventure `Component`, not a `String`, so any 3.x code that called `event.getPlayer().sendMessage("text")` will fail to compile against 4.0.
{% endhint %}

```java
@EventHandler
public void onJoin(PetPlayerJoinEvent event) {
    MyPetPlayer player = event.getPlayer();
    getLogger().info(player.getName() + " joined.");
}
```

## Combat & Skills

### PetDamageEvent

`Cancellable`

Fires when an active pet is about to deal damage to another entity. Both `setDamage(double)` (clamped to ≥0) and `setCancelled(true)` are supported, so you can reduce, eliminate, or cancel the hit.

**Accessors**

* `getPet()` — the attacking `Pet`
* `getTarget()` — the Bukkit `Entity` taking damage
* `getDamage()` / `setDamage(double)` — the outgoing damage amount
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onPetDamage(PetDamageEvent event) {
    if (event.getTarget() instanceof org.bukkit.entity.Player) {
        event.setDamage(event.getDamage() * 0.5); // halve PvP damage
    }
}
```

### PetOnHitSkillEvent

`Cancellable`

Fires when an `OnHitSkill` (e.g. Fire, Poison, Thorns) is about to apply on a successful hit. Cancel to suppress the skill effect for this hit only. This is the canonical hook for "react when a skill triggers" — the standalone `MyPetActiveSkillEvent` from 3.x has been removed.

**Accessors**

* `getPet()` — the attacking `Pet`
* `getSkill()` — the `OnHitSkill` instance about to trigger
* `getTarget()` — the `LivingEntity` being hit
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onHitSkill(PetOnHitSkillEvent event) {
    if (event.getSkill().getName().equalsIgnoreCase("Fire")) {
        event.setCancelled(true); // never set targets on fire
    }
}
```

## Experience & Progression

### PetExpEvent

`Cancellable`

Fires when XP is being awarded to a pet (from kills, the experience-script system, or admin commands). Cancel to deny the XP entirely, or use `setExp(double)` to scale it.

**Accessors**

* `getPet()` — the `Pet` receiving XP
* `getExp()` / `setExp(double)` — the XP amount
* `isQuiet()` — whether MyPet should suppress its own chat / sound feedback for this gain
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onExp(PetExpEvent event) {
    event.setExp(event.getExp() * 2.0); // double XP weekend
}
```

### PetLevelEvent

Parent class of `PetLevelUpEvent` and `PetLevelDownEvent`. Listening for it directly catches both directions; listen for the specific subclass when you only care about one. Not cancellable.

**Accessors**

* `getPet()` — the `Pet`
* `getLevel()` — the new (post-change) level
* `isQuiet()` — whether MyPet should suppress its own feedback
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onLevelChange(PetLevelEvent event) {
    getLogger().info("Pet now at level " + event.getLevel());
}
```

### PetLevelUpEvent

Subclass of `PetLevelEvent`. Fires when a pet gains a level. Adds `fromLevel()` (note: no `get` prefix — record-style accessor).

**Accessors**

* `fromLevel()` — the previous level
* (plus all accessors from `PetLevelEvent`)

```java
@EventHandler
public void onLevelUp(PetLevelUpEvent event) {
    int gained = event.getLevel() - event.fromLevel();
    event.getPlayer().sendMessage("Your pet gained " + gained + " level(s)!");
}
```

### PetLevelDownEvent

Subclass of `PetLevelEvent`. Fires when a pet loses a level (e.g. via admin command or scripted XP loss). Adds `fromLevel()`.

**Accessors**

* `fromLevel()` — the previous (higher) level
* (plus all accessors from `PetLevelEvent`)

```java
@EventHandler
public void onLevelDown(PetLevelDownEvent event) {
    event.getPlayer().sendMessage(
        "Your pet dropped from level " + event.fromLevel() + " to " + event.getLevel() + "."
    );
}
```

### PetSelectSkilltreeEvent

Fires when a skilltree is assigned to a pet — by player command, admin action, the pet shop, or the auto-assignment logic. Not cancellable. Carries a nested `Source` enum (`AUTO`, `PLAYER_COMMAND`, `ADMIN_COMMAND`, `ADMIN_CREATION`, `SHOP`, `OTHER`).

**Accessors**

* `getSource()` — what triggered the selection
* `getSkilltree()` — the `Skilltree` being assigned
* `getPet()` — the `StoredPet`
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onSkilltreeSelect(PetSelectSkilltreeEvent event) {
    if (event.getSource() == PetSelectSkilltreeEvent.Source.PLAYER_COMMAND) {
        getLogger().info(event.getOwner().getName()
            + " picked skilltree " + event.getSkilltree().getName());
    }
}
```

## Interaction & State

### PetActivatedEvent

Fires once a summoned pet is fully active in the world (after `PetCallEvent` has succeeded and the underlying mob has spawned). Not cancellable; use `PetCallEvent` if you need to block the spawn.

**Accessors**

* `getPet()` — the now-active `Pet`
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onActivated(PetActivatedEvent event) {
    event.getPlayer().sendMessage("Your pet is ready.");
}
```

### PetStatusEvent

Fires when a pet's `PetState` changes (e.g. between `Here`, `Despawned`, `Dead`). Not cancellable.

**Accessors**

* `getPet()` — the `Pet` whose state changed
* `getState()` — the new `Pet.PetState` the pet just transitioned to
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onStatus(PetStatusEvent event) {
    getLogger().fine("Pet state changed to " + event.getState());
}
```

### PetSitEvent

`Cancellable` (inherits from `PetInteractEvent`)

Fires when a pet is told to stay or follow. Adds `getAction()` returning a nested `Action` enum (`STAY`, `FOLLOW`).

**Accessors**

* `getAction()` — `STAY` or `FOLLOW`
* `getPet()` — the affected `Pet` (inherited)

```java
@EventHandler
public void onSit(PetSitEvent event) {
    if (event.getAction() == PetSitEvent.Action.STAY) {
        getLogger().info("Pet is staying put.");
    }
}
```

### PetInteractEvent

`Cancellable`

Parent class for interaction events. Fires when a player right-clicks their pet. Cancel to suppress the default interaction behavior. `PetSitEvent` and `PetFeedEvent` extend this — listen to those if you want the more specific contexts.

**Accessors**

* `getPet()` — the `Pet` being interacted with
* `getItem()` — the `ItemStack` the player was holding (new in 4.0; previously only available on `PetFeedEvent`)

```java
@EventHandler
public void onInteract(PetInteractEvent event) {
    event.setCancelled(true); // suppress all default pet interactions
}
```

### PetInventoryActionEvent

`Cancellable`

Fires when a player or the pet itself acts on the pet's backpack inventory. Carries a nested `Action` enum (`OPEN`, `PICKUP`, `USE`).

**Accessors**

* `getAction()` — what kind of inventory action this is
* `getPet()` — the `Pet` whose inventory is involved
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onInventoryAction(PetInventoryActionEvent event) {
    if (event.getAction() == PetInventoryActionEvent.Action.OPEN
            && !event.getPlayer().hasPermission("myserver.pet.inventory")) {
        event.setCancelled(true);
    }
}
```

### PetNameEvent

`Cancellable` _(new in 4.0)_

Fires when a pet is being renamed. Cancelling suppresses the rename; the pet keeps its current name. `setNewName(String)` lets you sanitize names by mutating the value before the rename completes.

**Accessors**

* `getPet()` — the `Pet` being renamed
* `getNewName()` / `setNewName(String)` — the proposed new name

```java
@EventHandler
public void onName(PetNameEvent event) {
    if (event.getNewName().toLowerCase().contains("admin")) {
        event.setNewName("Cheeky"); // reject reserved word
    }
}
```

### PetFeedEvent

`Cancellable` (inherits from `PetInteractEvent`)

Fires when a pet is fed. Both the saturation amount and the resulting effect (`HEAL`, `EAT`, `SELF_FEED`) are mutable.

**Accessors**

* `getSaturation()` / `setSaturation(double)` — saturation gained from this feeding
* `getResult()` / `setResult(Result)` — what feeding does for this hit
* `getPet()` — the `Pet` (inherited)
* `getItem()` — the `ItemStack` being fed (inherited from `PetInteractEvent`)

```java
@EventHandler
public void onFeed(PetFeedEvent event) {
    event.setSaturation(event.getSaturation() * 1.5); // 50% more nutrition
}
```

### PetPickupItemEvent

`Cancellable`

Fires when a pet (with the Pickup skill) is about to grab a ground item.

**Accessors**

* `getItem()` — the dropped Bukkit `Item` entity
* `getPet()` — the `Pet` doing the pickup
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onPickup(PetPickupItemEvent event) {
    if (event.getItem().getItemStack().getType().toString().contains("SHULKER_BOX")) {
        event.setCancelled(true); // pets shouldn't carry shulker boxes
    }
}
```

## Resources

### PetExhaustionEvent

`Cancellable`

Fires when a pet is about to lose saturation from the hunger system. Cancel to keep the pet from getting hungry on this tick — useful for "creative-mode" pet plugins or temporary buffs.

**Accessors**

* `getPet()` — the `Pet` losing saturation
* `getOwner()` — the owning `MyPetPlayer`
* `getPlayer()` — the owning Bukkit `Player`

```java
@EventHandler
public void onExhaustion(PetExhaustionEvent event) {
    if (event.getPlayer().hasPermission("myserver.pet.no-hunger")) {
        event.setCancelled(true);
    }
}
```
