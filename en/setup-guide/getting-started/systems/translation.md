---
icon: earth-europe
---

# Translation

{% hint style="info" %}
**MyPet uses the language the player has selected!**

Players playing Minecraft in German will get German messages and English players English messages.
{% endhint %}

If you want to help translate MyPet you can do so on the [MyPet Translation Site](https://crowdin.com/project/mypet-translations). MyPet is already translated into several languages so please check the site for existing translations before you do your own.

### Custom Translation

You can create your own translation by modifying an [existing translation](https://github.com/MyPetORG/MyPet-Translations) or creating a completely new one. Either way you have to put the file into the `locale` folder and name it in this schema: `MyPet_XX.properties`. `XX` has to be replaced by the [locale code](https://minecraft.wiki/w/Language) of the language you want to change/create.

### Overriding the Language

If you don't want the default behavior where the plugin will send messages in the language of the player or you did your own messages then you can force the plugin to use only that one language. You can do so by setting `OverwriteLanguages` in the [config.yml](../configuration/config.yml.md) to the [locale code](https://minecraft.wiki/w/Language) you want to use.
