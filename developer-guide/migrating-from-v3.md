---
icon: arrows-rotate
description: Migrating plugins from the MyPet 3.x API to the 4.0 API.
---

# Migrating from v3.x

This page is the migration guide for plugin authors porting an existing integration from the MyPet 3.x API (the `master` branch) to the **4.0** API. Every entry has a migration path; entries without one say so explicitly.

The scope is the published `mypet-api` Maven artifact. For what happens to a server's existing config, database, and skilltree data on upgrade, see [Updating from MyPet 3 to 4](../setup-guide/getting-started/updating-from-3-to-4.md).

{% hint style="warning" %}
**v4 is a breaking release.** Every plugin that imports a class from `de.Keyle.MyPet.api.event.*` or calls a method on `MyPetApi` will need source-level changes before it compiles against 4.0. Recompilation alone will not fix it — old `MyPet*Event` classes do not exist in 4.0.
{% endhint %}

## Cheat sheet

| 3.x | 4.0 | Notes |
| --- | --- | --- |
| `MyPetType` | `PetType` | Same class, renamed |
| `MyPetInfo` | `PetInfo` | Same class, renamed |
| `MyPetManager` | `PetManager` | Now an abstract class, not an interface |
| `MyPetApi.getMyPetManager()` | `MyPetApi.getPetManager()` | |
| `MyPetApi.getMyPetInfo()` | `MyPetApi.getPetInfo()` | |
| `MyPetApi.getRepository()` | _removed_ | No replacement in the public API |
| `MyPet*Event` | `Pet*Event` | All 22 surviving events renamed |
| `event.getMyPet()` | `event.getPet()` | All events |
| `MyPetPlayer.getExtendedInfo()` | `MyPetPlayer.getExtendedInfo(plugin, key)` | Now namespaced |
| `MyPetPlayer.setExtendedInfo(tag)` | `MyPetPlayer.addExtendedInfo(plugin, key, tag)` | Now namespaced |
| `PetManager.getMyPetFromEntity(e)` | `PetManager.getPetFromEntity(e)` | Also handles `ComplexEntityPart` |
| `PetManager.getInactiveMyPetFromMyPet(p)` | `PetManager.snapshot(activePet)` | New name, narrowed parameter |
| `StoredMyPet` / `InactiveMyPet` | `PersistedPet` | Now an immutable `record` in the api module |
| Raw `getSkillInfo()` NBT blob | `skillState(SkillClass, StateClass)` + `SkillStateCodec` | Typed; codec is the only write path |
| Legacy color codes (`&2`, `§a`) | MiniMessage (`<green>`) | All display strings |
| Old NBT library | Adventure NBT (`CompoundBinaryTag`) | Shaded into the jar |

## Removed APIs

### `Repository` interface

The entire `Repository` interface (including `getAllPets()`, `addPet()`, `savePet()`, `updatePet()`, `removePet()`, `getMyPetPlayer()`) is gone from the public API. `MyPetApi.getRepository()` no longer exists.

**No migration path.** Direct repository I/O from third-party plugins was always fragile — it bypassed `PetManager`'s active-pet tracking. Use `PetManager.getStoredPets(owner)` to read a player's pets and `PetManager.activatePet` / `PetManager.deactivatePet` for lifecycle changes. For admin-style bulk reads, `PetManager.getAllActivePets()` returns live pets only.

### `PlatformHelper`

`PlatformHelper` is gone. It exposed NMS-era reflection helpers (NMS class loading, version-specific entity spawning) that no longer apply now that v4 is NMS-free.

**No migration path.** The capabilities it provided are handled internally without NMS.

### `CompatUtil`

`CompatUtil` is removed from the public API. It previously exposed `compareWithMinecraftVersion(String)` and a reflection-based class loader.

**No migration path.** For MC version gating in your own plugin, use Paper's `Bukkit.getMinecraftVersion()` or check the existence of an `EntityType` directly.

### `EggIconService`

Removed from the public API. It was registered in `MyPetApi.getServiceManager()` but is now plugin-internal.

**No migration path.** If you derived item icons for pet types this way, use `PetInfo.getRegisteredInfo(petType).getIconClass()`, or snapshot a spawned entity yourself.

### `MyPet.getEntity()` / `MyPetBukkitEntity` / `MyPetMinecraftEntity`

`getEntity()` is gone. The `MyPetBukkitEntity` and `MyPetMinecraftEntity` wrapper interfaces are entirely removed. Pets are now plain Bukkit `Mob` instances.

**Migration:** call `pet.getBukkitEntity()` — it now returns `Mob`. To check if a `Mob` is a pet, call `PetManager.getPetFromEntity(entity)` (returns `null` if not a pet) or read the persistent-data-container key `mypet:pet` directly.

### Raw `MyPetPlayer` extended-info blob

`MyPetPlayer.getExtendedInfo()` and `setExtendedInfo(CompoundBinaryTag)` — the variants returning or accepting the full raw blob — are removed.

**Migration:** see the namespaced extended-info API in [New APIs](#new-apis).

### `MyPetPlayer` contributor methods

`getContributorRank()` and `checkForContribution()` are removed.

**No migration path.**

### Vestigial `PetType` overloads

`PetType.byName(String, boolean)` and `PetType.byEntityTypeName(String, boolean)` (the two-arg forms with a nullable-instead-of-throw boolean) are removed.

**Migration:** use `PetType.byNameOrNull(name)` for `null`-on-miss, or `PetType.byName(name)` / `PetType.byEntityTypeName(name)` for throw-on-miss.

### `api/entity/types/` subpackage

The entire `api.entity.types` subpackage is gone. It previously held the canonical type-marker interfaces like `MyWolf`, `MyMooshroom`, `MyRabbit`, etc.

**Migration:** type-specific capabilities are now expressed via marker interfaces in `api.entity` (`PetBaby`, `PetFlyingEntity`, `PetEquipment`, etc.). For type-specific feature gating, check `petType.isFlyingPet()`, `petType.isSwimmingPet()`, or `PetType.getPetClass().isAssignableFrom(SomeMarker.class)` as appropriate.

### Removed event classes

`MyPetActiveSkillEvent` and `MyPetActiveTargetSkillEvent` are gone — they had no remaining internal callers and exposed mid-flow state that no longer maps to v4's skill model. Any `MyPet*Event` not listed in the rename tables below is similarly absent in v4.

**Migration:** for "react when a skill triggers on a hit," listen to `PetOnHitSkillEvent` (cancellable; carries the skill instance and target). For owner-initiated skills, use the skill's own `Skill#getState()` if it exposes state, or hook the underlying interaction event.

## Renamed classes and interfaces

### Core types

| 3.x | 4.0 | Package |
| --- | --- | --- |
| `MyPetType` | `PetType` | `api.entity` |
| `MyPetInfo` | `PetInfo` | `api.entity` |
| `MyPetBaby` | `PetBaby` | `api.entity` |
| `MyPetFlyingEntity` | `PetFlyingEntity` | `api.entity` |
| `MyPetSwimmingEntity` | `PetSwimmingEntity` | `api.entity` |
| `MyPetAquaticEntity` | `PetAquaticEntity` | `api.entity` |
| `MyPetAmphibiousEntity` | `PetAmphibiousEntity` | `api.entity` |
| `MyPetEquipment` | `PetEquipment` | `api.entity` |
| `MyPetNaturalDrop` | `PetNaturalDrop` | `api.entity` |
| `MyPetSunSensitive` | `PetSunSensitive` | `api.entity` |
| `MyPetZombifiable` | `PetZombifiable` | `api.entity` |
| `MyPetLavaEntity` | `PetLavaEntity` | `api.entity` |
| `StoredMyPet` / `InactiveMyPet` | `PersistedPet` | `api.entity` |

v4 also introduces new marker interfaces in `api.entity` with no 3.x equivalent: `PetNaturallyRideable` (any pet that can be ridden out-of-the-box like horses or camels) and `PetMultiPassenger` (pets that seat more than one rider, like camels and happy ghasts). `PetSaddleable` was widened to cover the new rideables in addition to its original 3.x members.

{% hint style="warning" %}
**Since 4.0.1, `PetEquipment` extends `Pet`.** This lets the interface read its own per-type configuration (it added a `retainEquipmentOnTame()` default method backed by [`RetainEquipmentOnTame`](../setup-guide/getting-started/configuration/pet-config.yml/#retainequipmentontame)), and it matches the other config-reading markers such as `PetBaby`.

Every pet type MyPet ships is already a `Pet`, so nothing changes for them. If your own plugin implements `PetEquipment` on a class that is **not** a `Pet`, it will no longer compile — implement `Pet` as well, or move the equipment handling onto your pet class.
{% endhint %}

### `MyPetApi` facade

| 3.x | 4.0 |
| --- | --- |
| `MyPetApi.getMyPetManager()` | `MyPetApi.getPetManager()` |
| `MyPetApi.getMyPetInfo()` | `MyPetApi.getPetInfo()` |

### `PetManager` methods

| 3.x | 4.0 |
| --- | --- |
| `getMyPet(MyPetPlayer)` | `getPet(MyPetPlayer)` |
| `getMyPetFromEntity(Entity)` | `getPetFromEntity(Entity)` |
| `getAllActiveMyPets()` | `getAllActivePets()` |
| `hasActiveMyPet(player)` | `hasActivePet(player)` |
| `getInactiveMyPetFromMyPet(StoredPet)` | `snapshot(Pet)` _(see [Signature changes](#signature-changes))_ |

## Renamed events

All `MyPet*Event` classes have been renamed to `Pet*Event`. The `getMyPet()` accessor on each event is now `getPet()`.

| 3.x | 4.0 |
| --- | --- |
| `MyPetActivatedEvent` | `PetActivatedEvent` |
| `MyPetCallEvent` | `PetCallEvent` |
| `MyPetCreateEvent` | `PetCreateEvent` |
| `MyPetDamageEvent` | `PetDamageEvent` |
| `MyPetExpEvent` | `PetExpEvent` |
| `MyPetExhaustionEvent` | `PetExhaustionEvent` |
| `MyPetFeedEvent` | `PetFeedEvent` |
| `MyPetInteractEvent` | `PetInteractEvent` |
| `MyPetInventoryActionEvent` | `PetInventoryActionEvent` |
| `MyPetLevelDownEvent` | `PetLevelDownEvent` |
| `MyPetLevelUpEvent` | `PetLevelUpEvent` |
| `MyPetLoadEvent` | `PetLoadEvent` |
| `MyPetNameEvent` | `PetNameEvent` |
| `MyPetOnHitSkillEvent` | `PetOnHitSkillEvent` |
| `MyPetPickupItemEvent` | `PetPickupItemEvent` |
| `MyPetPlayerJoinEvent` | `PetPlayerJoinEvent` |
| `MyPetRemoveEvent` | `PetRemoveEvent` |
| `MyPetSaveEvent` | `PetSaveEvent` |
| `MyPetSelectSkilltreeEvent` | `PetSelectSkilltreeEvent` |
| `MyPetSendAwayEvent` | `PetSendAwayEvent` |
| `MyPetSitEvent` | `PetSitEvent` |
| `MyPetStatusEvent` | `PetStatusEvent` |

## Event enum constants (PascalCase → UPPER_SNAKE_CASE)

All nested source / action / result enums on events have moved from `PascalCase` to `UPPER_SNAKE_CASE`:

| Event | 3.x constant | 4.0 constant |
| --- | --- | --- |
| `PetCreateEvent.Source` | `Leash` | `LEASH` |
| | `AdminCommand` | `ADMIN_COMMAND` |
| | `PetShop` | `PET_SHOP` |
| | `Other` | `OTHER` |
| `PetRemoveEvent.Source` | `Release` | `RELEASE` |
| | `Death` | `DEATH` |
| | `AdminCommand` | `ADMIN_COMMAND` |
| | `Other` | `OTHER` |
| `PetSelectSkilltreeEvent.Source` | `Auto` | `AUTO` |
| | `PlayerCommand` | `PLAYER_COMMAND` |
| | `AdminCommand` | `ADMIN_COMMAND` |
| | `AdminCreation` | `ADMIN_CREATION` |
| | `Shop` | `SHOP` |
| | `Other` | `OTHER` |
| `PetSitEvent.Action` | `Stay` | `STAY` |
| | `Follow` | `FOLLOW` |
| `PetInventoryActionEvent.Action` | `Open` | `OPEN` |
| | `Pickup` | `PICKUP` |
| | `Use` | `USE` |
| `PetFeedEvent.Result` | `Heal` | `HEAL` |
| | `Eat` | `EAT` |
| | `SelfFeed` | `SELF_FEED` |

The `PetSelectSkilltreeEvent.Source.BossShopPro` constant from 3.x is also gone — BossShopPro-driven assignments now arrive as `SHOP`.

## Signature changes

### `PetManager.snapshot()` — renamed and narrowed

```java
// 3.x
StoredMyPet getInactiveMyPetFromMyPet(StoredMyPet activePet);

// 4.0
PersistedPet snapshot(Pet activePet);
```

The parameter type changed from `StoredMyPet` (the old base type) to `Pet` (requires a live, active pet). You can no longer snapshot an already-inactive pet — pass only pets returned by `getPet()` or `getAllActivePets()`.

### `PetManager.getPetFromEntity()` — handles `ComplexEntityPart`

```java
// 3.x
MyPet getMyPetFromEntity(Entity entity);

// 4.0
Pet getPetFromEntity(Entity entity);  // transparently handles EnderDragon body parts
```

Passing any `ComplexEntityPart` (Ender Dragon body / head / neck / tail / wings) resolves to the parent entity before the PDC lookup. 3.x callers that unwrapped `ComplexEntityPart` manually can drop the guard.

### `PetCallEvent.getPet()` — narrowed return type

```java
// 3.x
StoredMyPet getMyPet();  // returned the base type

// 4.0
Pet getPet();  // always a live Pet
```

The event now fires only once the world entity is being created for an already-active pet. The pet is guaranteed to be live (skills loaded, NBT applied) when the event fires.

### `PetType.register()` — throws on collision

```java
// 3.x
static MyPetType register(String name, Class<? extends MyPet> petClass);  // silent overwrite

// 4.0
static PetType register(String name, Class<? extends Pet> petClass);  // throws IllegalArgumentException on duplicate
```

Guard your registration with `PetType.byNameOrNull(name) == null` before calling `register`, or catch `IllegalArgumentException`.

### `PetType.byName()` / `byEntityTypeName()` — single-arg only

```java
// 3.x
static MyPetType byName(String name, boolean throwException);

// 4.0
static PetType byName(String name);          // throws PetTypeNotFoundException
static PetType byNameOrNull(String name);    // null on miss
```

### `Pet.getBukkitEntity()` — returns `Mob`, not `LivingEntity`

```java
// 3.x
LivingEntity getEntity();

// 4.0
Mob getBukkitEntity();  // returns org.bukkit.entity.Mob
```

`Mob` is a subtype of `LivingEntity`, so most read-only callers compile without change — but every call to `getEntity()` must be renamed to `getBukkitEntity()`.

### `PetManager.getStoredPets()` — async only

```java
// 3.x
List<InactiveMyPet> getInactiveMyPets(MyPetPlayer owner);  // synchronous

// 4.0
CompletableFuture<List<StoredPet>> getStoredPets(MyPetPlayer owner);  // async
```

**Migration:**

```java
MyPetApi.getPetManager().getStoredPets(petPlayer).thenAccept(pets -> {
    // Do not touch the Bukkit API directly here — hop to the main thread first.
    Bukkit.getScheduler().runTask(plugin, () -> {
        for (StoredPet pet : pets) { /* ... */ }
    });
});
```

{% hint style="warning" %}
On Folia you must hop to a region scheduler, not the global scheduler. Touching Bukkit API directly inside a `thenAccept` continuation is a crash on Folia and undefined behavior on Paper.
{% endhint %}

### `PetPlayerJoinEvent.getPlayer()` — returns `MyPetPlayer`, not `Player`

```java
// 3.x
Player getPlayer();

// 4.0
MyPetPlayer getPlayer();
```

This is a silent API break: both types have a `sendMessage` method, but `MyPetPlayer.sendMessage` takes an Adventure `Component`, not a `String`. Any `event.getPlayer().sendMessage("text")` call from 3.x will fail to compile against 4.0. If you need the Bukkit `Player`, call `event.getPlayer().getPlayer()`.

### `PetLevelUpEvent.fromLevel()` — record-accessor style

```java
// 3.x
int getOldLevel();  // conventional getter

// 4.0
int fromLevel();  // record-style, no "get" prefix
```

## New APIs

### `StoredPet` sealed interface

`StoredPet` is now declared as `sealed interface permits PersistedPet, Pet`. It is the read-only contract shared by persisted and active pets. Code that previously accepted `StoredMyPet` should now accept `StoredPet` — it will work transparently with both forms.

### `PersistedPet` record

`PersistedPet` is a public Java `record` in the `api` module that replaces the old `InactiveMyPet` / `StoredMyPet` implementation. Mutation returns new instances:

```java
PersistedPet updated = original.withPetName("Fluffy");
PersistedPet rebuilt = original.toBuilder().petName("Fluffy").health(20).build();
```

The `info` and `skillInfo` fields are `CompoundBinaryTag` (Adventure NBT).

### Typed skill state: `SkillState`, `SkillStateCodec`, `StoredPet.skillState()`

v4 replaces the raw `getSkillInfo()` NBT blob with a typed, sealed-dispatch API. You can read a skill's state from any `StoredPet` (active or persisted) without caring which:

```java
// Works on both PersistedPet and an active Pet:
Optional<Backpack.State> state = pet.skillState(Backpack.class, Backpack.State.class);
state.ifPresent(s -> s.inventory().getContents());
```

To expose state from a custom skill, register a **codec** — a bidirectional `write` / `read` pair — at enable time:

```java
MyPetApi.getSkillManager().registerCodec(
    MySkill.class, MySkill.State.class,
    new SkillStateCodec<MySkill.State>() {
        @Override
        public CompoundBinaryTag write(MySkill.State state) {
            return CompoundBinaryTag.builder()
                .putString("someKey", state.someValue())
                .build();
        }

        @Override
        public Optional<MySkill.State> read(CompoundBinaryTag compound) {
            return Optional.of(new MySkill.State(compound.getString("someKey")));
        }
    }
);
```

`registerCodec` throws `IllegalArgumentException` on duplicate registration — re-registration is a bug, not a hot-reload path.

### `Skill.getState()` and `Skill.applyState()` defaults

The `Skill` interface (the skilltree skill) gains two default methods:

* `default Optional<? extends SkillState> getState()` — returns `Optional.empty()`. Implement it in your custom skill to expose state via `StoredPet.skillState()` on live pets. The codec calls this on save to serialize the live skill into NBT.
* `default void applyState(SkillState state)` — no-op. Implement it to absorb a deserialized state on pet activation. MyPet hands you a `SkillState` instance produced by your codec's `read`.

Together these form the round-trip: `getState() → codec.write → NBT → codec.read → applyState`.

### `PetType.unregister(String)`

```java
PetType.unregister("MyCustomMob");
```

Call this from your `onDisable` to release the `Class<? extends Pet>` reference and avoid leaking your plugin's classloader across reloads. It is a no-op if the name is not registered.

### `PetType.byNameOrNull(String)`

Returns `null` instead of throwing when the type isn't registered. Prefer this over a try/catch on `byName`.

### `PetType.getTypeID()`

Returns the lowercase snake-case persistence key (e.g. `"zombie_villager"`) derived from the Bukkit `EntityType` name. Use this wherever you previously computed the key by hand.

### `MyPetApi.isReady()`

```java
if (!MyPetApi.isReady()) return;
```

A static guard that is safe to call from `onEnable`, `onLoad`, constructors, and async threads. Returns `true` once MyPet's `onEnable` has completed. Every other `MyPetApi` method now throws `IllegalStateException` (with a helpful message) if called before this returns `true`.

### Namespaced `MyPetPlayer` extended-info

```java
// write
myPetPlayer.addExtendedInfo(plugin, "myKey", StringBinaryTag.stringBinaryTag("value"));

// read
Optional<BinaryTag> tag = myPetPlayer.getExtendedInfo(plugin, "myKey");
```

Keys are scoped per-`Plugin` instance, so two addons can't collide. The raw blob `getExtendedInfo()` / `setExtendedInfo(CompoundBinaryTag)` getters and setters are removed.

### `PetNameEvent` is now cancellable

`PetNameEvent` now `implements Cancellable`. Cancelling suppresses the rename; the pet keeps its current name. Previously it was notification-only.

### `PetInteractEvent.getItem()`

The base interact event now exposes `ItemStack getItem()` — the item the player was holding. Previously this was only available by casting to `PetFeedEvent`.

### `PetStatusEvent.getState()`

`PetStatusEvent` now exposes `Pet.PetState getState()` — the new lifecycle state the pet transitioned to. Previously you had to re-query the pet after the event fired.

### `StoredPet.getLevel()` and `StoredPet.getDisplayName()`

Both are now default methods on `StoredPet`, so they work on both `PersistedPet` and a live `Pet`:

* `getLevel()` — derives the level from raw XP via `ExperienceCache`; returns `0` if no curve is loaded yet
* `getDisplayName()` — deserializes the MiniMessage `getPetName()` string into an Adventure `Component`

### `PetManager.activatePet(StoredPet)` and `deactivatePet(MyPetPlayer, boolean)`

Both are now public abstract methods on `PetManager`, so addons can trigger activation / deactivation programmatically without going through commands.

## Behavior changes

### `MyPetApi` methods throw `IllegalStateException` on early access

In 3.x, calling `MyPetApi.getPetManager()` before MyPet had loaded would either return `null` or throw `NoSuchElementException` from a service lookup. In 4.0, every method that requires MyPet to be loaded throws `IllegalStateException` with a message that tells you what to fix (`"add 'softdepend: [MyPet]' to plugin.yml or guard with MyPetApi.isReady()"`).

Guard all early-access paths:

```java
if (!MyPetApi.isReady()) return;
```

### Pet entity detection uses PDC, not `instanceof`

Pets are no longer instances of `MyPetBukkitEntity`. The correct "is this a pet?" check is:

```java
entity.getPersistentDataContainer().has(
    new NamespacedKey("mypet", "pet"), PersistentDataType.BYTE);
```

…or, equivalently, `PetManager.getPetFromEntity(entity)` (returns `null` if the entity is not a pet). The old `instanceof MyPetBukkitEntity` check will always return `false` in 4.0.

### `PetType.register()` is collision-safe (and collision-fatal)

In 3.x, re-registering a type name silently overwrote the previous entry, which masked classloader leaks on plugin reload. In 4.0 the second registration throws `IllegalArgumentException`. Always pair `register` in `onEnable` with `unregister` in `onDisable`.

### Registration methods throw `IllegalArgumentException` on misconfiguration

`SkillManager.registerSkill`, `SkilltreeManager.registerRequirement`, `LeashFlagManager.registerLeashFlag`, and `PluginHookManager.registerHook` now throw `IllegalArgumentException` (with a specific message) when:

* The required annotation is missing (`@SkillName` / `@RequirementName` / `@LeashFlagName` / `@PluginHookName`)
* A class is registered twice
* The class doesn't implement the required base type

In 3.x the same conditions either logged a warning and returned, returned silently, or threw `NullPointerException` from `.toLowerCase()` on the missing annotation. v4 fails loudly at boot — catch the exception at the registration site or fix the annotation, rather than scanning the log for a warning.

Note that the skilltree JSON loader's log-and-skip behavior on unknown-skill upgrade blocks is unchanged: that's a data boundary, not a registration boundary.

### `getStoredPets()` completions run off the main thread

The `CompletableFuture` returned by `PetManager.getStoredPets()` completes on a database I/O thread. Touching the Bukkit API inside a `thenAccept` / `thenRun` continuation is undefined behavior on Paper and a crash on Folia. Always hop to the appropriate scheduler before interacting with Bukkit entities or player state.

### Sound name resolution uses `Registry.SOUNDS`

`Pet.makeSound(String, float, float)` now resolves sound names via `Registry.SOUNDS.get(NamespacedKey.minecraft(name))`. If the sound does not exist in the current Minecraft version, the call silently does nothing. Previously, invalid sound names could throw or fall back to a substitute.

## Build and dependency changes

| Area | Change                                                                                                                                                                                                                                                                                                                                                                           |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Java version** | Java 21 required. The 3.x minimum was Java 11.                                                                                                                                                                                                                                                                                                                                   |
| **Server platform** | Paper (and Paper forks) only. Bukkit and Spigot are not supported.                                                                                                                                                                                                                                                                                                               |
| **Minimum MC version** | 1.20.6. Earlier versions are rejected at startup.                                                                                                                                                                                                                                                                                                                                |
| **NMS modules** | The eight version-specific `nms/` modules are gone entirely. No NMS-side subclassing is needed or possible.                                                                                                                                                                                                                                                                      |
| **MongoDB** | Support dropped. Only SQLite and MySQL backends remain.                                                                                                                                                                                                                                                                                                                          |
| **ProtocolLib** | MyPet no longer exposes ProtocolLib as an integration surface to other plugins. It is still declared as a `softdepend` and used internally as a fallback for sound packet interception (PacketEvents is preferred). If your plugin depended on MyPet's old ProtocolLib-backed interaction routing, that surface is gone — drop the dependency from your `depend` / `softdepend`. |
| **NBT library** | Replaced with Adventure NBT (`net.kyori:adventure-nbt`). All NBT types are now from `net.kyori.adventure.nbt.*` (`CompoundBinaryTag`, `StringBinaryTag`, etc.).                                                                                                                                                                                                                  |
| **Text / colour formatting** | Legacy color codes (`&2`, `§a`) are gone. Display strings use MiniMessage (`<green>`, `<red>`, `<reset>`); `Component` (Adventure) is used throughout the API.                                                                                                                                                                                                                   |
| **Maven artifact** | Snapshot builds publish to the [UserDerezzed Reposilite](https://repo.userderezzed.dev) repo; release builds publish to the same host at the release coordinate. The old Sonatype / Maven Central coordinate is discontinued.                                                                                                                                                    |

{% hint style="info" %}
For a worked example of a plugin that targets the 4.0 API end-to-end (custom skill registration, upgrade parsers, MiniMessage output), see [Example Plugin](example-plugin.md).
{% endhint %}
