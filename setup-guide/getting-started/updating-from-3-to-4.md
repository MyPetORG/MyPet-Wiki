---
description: >-
  What happens when you upgrade a MyPet 3.x server to 4.0, and what to check
  before you do.
icon: circle-up
---

# Updating from MyPet 3 to 4

MyPet 4.0 is a major version. Upgrading is mostly automatic — drop in the new jar and start the server, and MyPet migrates your existing data on its own — but the upgrade rewrites your config, database, and skilltree files in place. Read this before you upgrade a live server.

{% hint style="danger" %}
**This upgrade is one-way.** MyPet has no downgrade path back to 3.x. Once migration has run, getting back to MyPet 3 behavior means restoring your own pre-upgrade backup, not installing an older jar. Back up your server before you replace the jar.
{% endhint %}

## What happens when you upgrade

1. Stop the server, replace the old MyPet jar with the 4.0 jar, start the server.
2. On startup, MyPet checks whether your database still has the old 3.x table structure. If it does, it treats this as an upgrade and runs its migration step before pets, hooks, or anything else loads.
3. Before changing anything, MyPet backs up the data it's about to touch to `plugins/MyPet/backups/migration-<version>-<timestamp>/`. Depending on what needs migrating, this can include your database (or table dumps, on MySQL), your `.yml` config files, and your `.st.json` skilltree files.
4. Migrations run in a fixed, dependency-ordered sequence and each one is recorded once it succeeds, so re-running the server later won't redo them.
5. If everything succeeds, the server starts normally. **If anything fails, MyPet disables itself for that startup** rather than run on half-migrated data — see [If the upgrade fails](#if-the-upgrade-fails).

{% hint style="info" %}
The automatic backup in step 3 is a safety net for MyPet's own migration step — it only covers MyPet's data folder and database, and old backup folders aren't cleaned up automatically. It isn't a substitute for backing up your server yourself first.
{% endhint %}

## What changes for you as an admin

Your pets, their levels, names, and inventories all carry over. A few things change shape and are worth knowing about if you notice a file looks different after upgrading:

* **Pet ownership is now keyed by Mojang UUID.** MyPet 3 tracked players by an internal ID; 4.0 uses the same UUID Minecraft/Mojang uses. This is converted automatically for known players; pets whose owner identity can't be resolved are left untouched and logged rather than guessed at.
* **Color codes become MiniMessage.** Legacy `&`/`§` color codes — pet name prefixes/suffixes in `config.yml`, shop names and descriptions in `pet-shops.yml`, skilltree text, and your own locale overrides — are rewritten to MiniMessage format (e.g. `&a` → `<green>`), since 4.0 renders all of these through MiniMessage. The in-game result looks the same; the raw text in the file will look different if you go and edit it.
* **A few config keys were renamed.** For example, `CanGlide` in `pet-config.yml` is now `CanFly` for flying pet types — your existing value carries over under the new name.
* **`pet-shops.yml` option values switched from numbers to names.** Variant options that used to be an integer (e.g. `variant: 2`) are now a readable string (e.g. `variant: gold`) for pets like axolotls, parrots, rabbits, horses, cats, and others.
* **Pet backpack items are re-encoded** into the current item format. Enchantments, custom names, and other item data are preserved.

None of this requires action from you — it happens as part of the automatic migration.

## Before you upgrade

{% hint style="warning" %}
**Don't upgrade Paper/Minecraft at the same time as MyPet.** Do them as two separate steps. If something goes wrong after updating both at once, you won't know whether it was the MyPet data migration, the server version bump, or an interaction between the two — and you'll have two changes to roll back instead of one. Upgrade one, confirm the server is stable, then upgrade the other.
{% endhint %}

* **Take your own backup.** A full server backup is safest; at minimum, back up your `plugins/MyPet/` folder and your pet database.
* **Update to the latest MyPet 3 release first**, if you're not already on it. Migration doesn't check for a specific 3.x version number — it upgrades based on your database's structure — but it's only tested against the most recent 3.x data shape, not every historical one.
* **If you rely on the MyPet API** (a hook plugin, a custom integration), note that 4.0's API is a separate breaking change from this data migration — see [Migrating from v3.x](../../developer-guide/migrating-from-v3.md) if you or a plugin author you depend on maintains code against `mypet-api`.

## If the upgrade fails

If migration fails partway, MyPet disables itself for that server start rather than come up on partially-migrated data.

* Check the console log around startup for the error — it names which migration failed.
* Your pre-migration data is in `plugins/MyPet/backups/migration-<version>-<timestamp>/`, in addition to whatever backup you took yourself.
* Already-applied migrations from that run are **not** automatically rolled back. Fix the underlying issue (for example, free up disk space or resolve a database connection problem) and restart — MyPet resumes from where it left off rather than redoing completed steps.
* If the server crashed mid-migration, MyPet will detect a migration stuck "in progress" on the next start and refuse to proceed automatically, asking for manual intervention. At that point, restore from a backup rather than repeatedly restarting.

## FAQ

**Do I need to run a command to migrate?**\
No. It runs automatically the first time the 4.0 jar starts against 3.x data.

**Can I go back to MyPet 3 after upgrading?**\
Not through the plugin. Restore your own pre-upgrade backup if you need to revert.
