# Is MyPet EULA compliant?

MyPet was not designed with the EULA in mind but with some changes to the configuration, MyPet should be EULA compliant. This depends mainly on the MyPet features you want to use on your server.

{% hint style="info" %}
In this article players that paid for anything on a server with real money are referred as Donators.
{% endhint %}

## What do I have to change?

1. You can not have skilltrees that are available just for donators or players that paid for a pet. That means that every skilltree must be available for everyone at the same point.
2. Disable special abilities of the pets like cows giving milk or sheep shearing. Just go throuh the pet-config.yml and disable them all.
3. All base stats must be the same for all pets or at least not higher than pets that are freely available.
4. ![$](../.gitbook/assets/exclaim.gif) Pets that can be bought on the shop are not allowed to have higher EXP or skilltrees that are not publicly available.
5. [Custom EXP scripts](https://wiki.mypet-plugin.de/experience) must treat everyone \(donators and non donatos\) equal

## Disclaimer

I can not be held responsible for the things written on this page. Everything was written with best intentions in mind but may contain flaws. If you think there are things missing or not correct please contact me on the [Spigot Forums](https://www.spigotmc.org/conversations/add?to=Keyle&title=EULA).

