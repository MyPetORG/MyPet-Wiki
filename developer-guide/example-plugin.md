---
icon: code-branch
description: A complete, runnable Bukkit plugin that registers a custom MyPet skill end-to-end.
---

# Example Plugin

[**MyPet-APIExamplePlugin**](https://github.com/MyPetORG/MyPet-APIExamplePlugin) is the canonical reference implementation for third-party plugins that integrate with the MyPet API. It exercises the full custom-skill registration path — both the legacy `registerSkill` call and the newer `registerUpgradeParser` call introduced in MyPet 4.0.

The example skill is **Glow**: when a pet lands a hit, there's a chance the target gets the vanilla Minecraft `GLOWING` potion effect. Two upgrade parameters scale per skilltree level: `chance` (0–100) and `duration` (in ticks).

## What it demonstrates

The whole plugin is two API calls in `ExamplePlugin#onEnable`:

```java
SkillManager skills = MyPetApi.getSkillManager();

skills.registerSkill(GlowImpl.class);

skills.registerUpgradeParser(Glow.class, UpgradeSchema.builder()
        .integer("chance").label("Chance %").suffix("%").cumulative()
        .integer("duration").label("Duration (s)").cumulative()
        .build(), json -> new GlowUpgrade()
        .chance(UpgradeParsers.parseInteger(UpgradeParsers.get(json, "chance")))
        .duration(UpgradeParsers.parseInteger(UpgradeParsers.get(json, "duration"))));
```

* **`registerSkill(GlowImpl.class)`** — tells MyPet to instantiate one `GlowImpl` per pet. Supported since MyPet 1.x.
* **`registerUpgradeParser(Glow.class, schema, ...)`** — teaches the skilltree JSON loader how to read a `Skills.Glow.Upgrades.<level>` block out of any `.st.json` file. Introduced in MyPet 4.0. The middle `UpgradeSchema` argument is required: it describes the upgrade fields to the web editor so `Glow` gets a typed editing form in `/mypet editor` like any built-in skill. Without the call, the loader logs `Unknown skill 'Glow'` and silently skips the upgrade entries — the pet still gets a `GlowImpl`, but it never receives upgrades, so it never fires.

The skill identifier (`"Glow"`) is read from the `@SkillName` annotation on `Glow.class` — there is no hand-typed string to keep in sync. The parser's return type is also type-checked: register `Glow.class` with a lambda that returns the wrong upgrade type and the call won't compile.

### Upgrade schemas

The second argument to `registerUpgradeParser` is an `UpgradeSchema` describing your
skill's upgrade fields. It is required — the web editor uses it to render a typed
editing form and to validate skilltrees, so custom skills work in `/mypet editor`
automatically. Field names must be the exact JSON keys your parser reads.

* `number(name)` / `integer(name)` — signed modifier strings (`"+5"`, `"-2.5"`)
* `bool(name)` — booleans
* `enumOf(name, MyEnum.class)` — fixed value sets
* `group(name, g -> ...)` — one level of nested fields
* Per field: `.label("Chance %")` (English fallback shown in the editor), `.suffix("%")`, `.cumulative()` (adds a running-total display)

Labels localize through MyPet's locale files: the editor looks up `Editor.Skill.<SkillName>.<field>` in every loaded language bundle, and the skill's display name uses the existing `Name.Skill.<SkillName>` key.

## Repository layout

The skill-related files below are the focus of this page. The example plugin also includes a custom requirement, leash flag, event listener, and command — see the [example plugin's README](https://github.com/MyPetORG/MyPet-APIExamplePlugin) for those.

| File | Role |
|------|------|
| `ExamplePlugin.java` | Bukkit plugin entry point. The two API calls above are the entire `onEnable`. |
| `skills/Glow.java` | Skill **interface**. Carries `@SkillName("Glow")`. Extends `Skill, OnHitSkill`. Declares the upgrade-aware getters. |
| `skills/GlowImpl.java` | Skill **implementation**. Constructed once per pet via the `(Pet)` constructor. State lives on `UpgradeComputer` fields so applied/unapplied upgrades automatically update the effective values. |
| `upgrades/GlowUpgrade.java` | Data carrier — one instance per `Upgrades.<level>` block. Annotated `@SkillName("Glow")` so MyPet's level-up dispatch matches it to the live `Glow` skill on the pet. |
| `resources/plugin.yml` | Bukkit plugin descriptor. `softdepend: [MyPet]` is mandatory. |
| `resources/glow-example.st.json` | Sample skilltree referencing both the new `Glow` skill and a built-in `Damage` skill — a good integration smoke test. |

## Building

The example consumes the MyPet API as a published snapshot, so it builds standalone:

```bash
git clone https://github.com/MyPetORG/MyPet-APIExamplePlugin
cd MyPet-APIExamplePlugin
./gradlew build
```

Output JAR: `build/libs/MyPetAPIExample-1.0.0.jar`.

Because `4.0.1-SNAPSHOT` is a moving version, Gradle caches it for 24 hours. To pick up a freshly-published API change immediately, run `./gradlew build --refresh-dependencies`.

## Running

{% stepper %}
{% step %}
### Drop the jar into `plugins/`
Place `MyPetAPIExample-1.0.0.jar` into a Paper server's `plugins/` directory **alongside** the MyPet jar.
{% endstep %}

{% step %}
### Install the sample skilltree
Copy `glow-example.st.json` from the example's `src/main/resources/` into the server's `plugins/MyPet/skilltrees/` directory.
{% endstep %}

{% step %}
### Restart and verify
Start the server. The console should log:

```
[MyPetAPIExample] Glow skill and upgrade parser registered with MyPet.
```
{% endstep %}

{% step %}
### Try it in-game
Assign the new skilltree to your pet:

```
/mypet skilltree assign glow-example
```

Tame a mob, level it to 1, and hit something — at level 1 there's a 10% chance per hit to apply Glowing for 60 ticks (3 seconds).
{% endstep %}
{% endstepper %}

## Using it as a template

For your own plugin:

1. Fork or clone the repository.
2. Rename the `dev.userderezzed.mypetapiexample` package to your own.
3. Replace `Glow` / `GlowImpl` / `GlowUpgrade` with your skill (keeping the four-class structure).
4. Update `@SkillName(...)` everywhere it appears — it must match between the interface, the upgrade class, and the JSON key in any `.st.json` referring to the skill.
5. Update `plugin.yml` with your plugin name and main class.

The build script is already wired against `https://repo.userderezzed.dev/snapshots`, so no changes are needed to consume the MyPet API.

{% hint style="warning" %}
**`softdepend: [MyPet]` is mandatory** in your `plugin.yml`. Without it, `MyPetApi.getSkillManager()` in `onEnable` will throw `IllegalStateException` because MyPet hasn't loaded yet. Guard early-access paths with `MyPetApi.isReady()` if you need to call into MyPet from a non-`onEnable` context.
{% endhint %}
