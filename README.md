---
description: Quickly set up MyPet with default settings.
icon: bolt
---

# Quickstart

MyPet works out of the box on most servers. Install it, restart the server, and start capturing Pets.

{% stepper %}
{% step %}
### Confirm your server is compatible

Check [Supported Versions](getting-started/supported-versions/) to make sure your Minecraft version is supported. Use [Paper](https://papermc.io/) if you can. [Spigot](https://spigotmc.org/) is also supported.

{% hint style="warning" %}
The MyPet 3.14 series will be the **last MyPet version series to support base Spigot server software**. Paper is the superior and most widely used server software, with over 82% of Minecraft Java servers today running Paper or offshoots of Paper. Making the switch is as easy as swapping your server jar. Switch to Paper today: [https://papermc.io](https://papermc.io/)
{% endhint %}
{% endstep %}

{% step %}
### Download MyPet from an official source

There are five official sources:

* [**Modrinth**](https://modrinth.com/plugin/mypet) (**recommended;** stable + snapshot releases)
* [**Hangar**](https://hangar.papermc.io/MyPet/MyPet) (stable releases)
* [**Polymart**](https://polymart.org/product/8915/mypet) (stable releases)
* [**Spigot**](https://www.spigotmc.org/resources/mypet.12725/) (using the legacy MyPetDownloader)
* [GitHub](https://github.com/MyPetORG/MyPet/releases) (builds here only last for a certain period of time)
{% endstep %}

{% step %}
### Stop your server
{% endstep %}

{% step %}
### Put the jar in your `plugins/` folder

1. Download the `MyPet-*.jar`.
2. Copy it to `<server root>/plugins/`.

{% hint style="info" %}
It's a good idea to keep the name of the jar file the same, eg. `MyPet-3.14.1.jar`, as this can help you determine whether you are up to date when the server is offline.
{% endhint %}
{% endstep %}

{% step %}
### Start the server once to generate files

On first boot, MyPet will create `plugins/MyPet/`. This is where `config.yml` and other automatically-generated configuration files live.
{% endstep %}

{% step %}
### Verify the install

1. Check the server console for lines that says MyPet is enabled.
2. In-game, run `/plugins`.
3. Confirm you see `MyPet` in the plugin list.

{% hint style="warning" %}
If you don’t see `MyPet`, check the console for errors.
{% endhint %}
{% endstep %}
{% endstepper %}
