---
icon: terminal
description: Build plugins that integrate with MyPet.
---

# Developer Guide

MyPet ships a public API that lets your Bukkit/Paper plugin react to and modify pet behavior. This guide covers how to depend on the API jar, how to listen for the 23 events MyPet publishes, and a handful of copy-paste recipes for the most common integrations.

{% hint style="info" %}
**Migrating from MyPet 3.x?** The 4.0 API renamed every event class (`MyPet*Event` → `Pet*Event`), changed several method signatures, and removed a few classes outright. See [Migrating from v3.x](migrating-from-v3.md) for the full porting guide.
{% endhint %}

## Requirements

* **Java 21**
* **Paper** (or a Paper fork — Folia is supported). Bukkit and Spigot are not supported in 4.0.
* **Minecraft 1.20.6** or newer
* **MyPet 4.0.0** or newer installed on the server

## Add the repository

MyPet publishes its API jar to two Reposilite-hosted Maven repositories:

* `https://repo.userderezzed.dev/snapshots` — alpha/beta builds; updates frequently.
* `https://repo.userderezzed.dev/releases` — stable cuts.

Pick the URL that matches the MyPet jar installed on your server.

{% hint style="info" %}
**Gradle (Kotlin DSL) is the recommended build tool** — it's what MyPet itself uses and gives you type-safe build scripts.
{% endhint %}

{% tabs %}
{% tab title="Gradle (Kotlin DSL)" %}
```kotlin
repositories {
    maven("https://repo.userderezzed.dev/snapshots")
    // maven("https://repo.userderezzed.dev/releases")
}
```
{% endtab %}

{% tab title="Gradle (Groovy)" %}
```groovy
repositories {
    maven { url 'https://repo.userderezzed.dev/snapshots' }
    // maven { url 'https://repo.userderezzed.dev/releases' }
}
```
{% endtab %}

{% tab title="Maven" %}
```xml
<repositories>
    <repository>
        <id>userderezzed-snapshots</id>
        <url>https://repo.userderezzed.dev/snapshots</url>
    </repository>
    <!--
    <repository>
        <id>userderezzed-releases</id>
        <url>https://repo.userderezzed.dev/releases</url>
    </repository>
    -->
</repositories>
```
{% endtab %}
{% endtabs %}

## Add the dependency

The API jar is provided by the MyPet plugin at runtime, so it must be declared as `compileOnly` (Gradle) or `provided` (Maven). Bundling it would create a duplicate `MyPetApi` on the server classpath.

{% tabs %}
{% tab title="Gradle (Kotlin DSL)" %}
```kotlin
dependencies {
    // Provided by the MyPet plugin at runtime — do not shade.
    compileOnly("de.keyle:mypet-api:4.0.1-SNAPSHOT")
}
```
{% endtab %}

{% tab title="Gradle (Groovy)" %}
```groovy
dependencies {
    // Provided by the MyPet plugin at runtime — do not shade.
    compileOnly 'de.keyle:mypet-api:4.0.1-SNAPSHOT'
}
```
{% endtab %}

{% tab title="Maven" %}
```xml
<dependencies>
    <!-- Provided by the MyPet plugin at runtime — do not shade. -->
    <dependency>
        <groupId>de.keyle</groupId>
        <artifactId>mypet-api</artifactId>
        <version>4.0.1-SNAPSHOT</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
{% endtab %}
{% endtabs %}

## Declare MyPet as a dependency in `plugin.yml`

```yaml
depend: [MyPet]
# Or, if your plugin only optionally integrates with MyPet:
# softdepend: [MyPet]
```

## Verify the install

{% stepper %}
{% step %}
### Build your plugin
Run your usual build command (`./gradlew build`, `mvn package`, etc.) and confirm the jar is produced.
{% endstep %}

{% step %}
### Drop both jars into `plugins/`
Place your plugin jar **and** `MyPet-*.jar` in the server's `plugins/` directory.
{% endstep %}

{% step %}
### Confirm the API is reachable
In your plugin's `onEnable()`, log a check:

```java
if (MyPetApi.getPlugin() != null) {
    getLogger().info("MyPet API ready.");
}
```

Start the server and look for the line in the console.
{% endstep %}
{% endstepper %}

## Where next

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><h4><i class="fa-bell">:bell:</i></h4></td><td><strong>Events</strong></td><td>React to and modify pet behavior using the 23 published event classes.</td><td><a href="events.md">events.md</a></td></tr><tr><td><h4><i class="fa-lightbulb">:lightbulb:</i></h4></td><td><strong>Examples</strong></td><td>Copy-paste recipes for common MyPet integrations.</td><td><a href="examples.md">examples.md</a></td></tr><tr><td><h4><i class="fa-code-branch">:code-branch:</i></h4></td><td><strong>Example Plugin</strong></td><td>A complete, runnable plugin that registers a custom skill end-to-end.</td><td><a href="example-plugin.md">example-plugin.md</a></td></tr><tr><td><h4><i class="fa-arrows-rotate">:arrows_counterclockwise:</i></h4></td><td><strong>Migrating from v3.x</strong></td><td>Porting guide for plugins moving from the 3.x API to 4.0.</td><td><a href="migrating-from-v3.md">migrating-from-v3.md</a></td></tr></tbody></table>
