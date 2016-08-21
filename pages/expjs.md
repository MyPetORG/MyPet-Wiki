# Experience-Script

With the **Experience-Script** ''exp.js'' it's possible to customize when a *MyPet* will level up.\\
As you can see at the file ending, the used language is **JavaScript**.\\
## Script

### Result Methods
To make a fully functional exp-script that can be used by *MyPet* you have to implement the following methods:

*  ''function getLevel(exp, mypet)''-> return the actual level in this method. 

*  ''function getRequiredExp(exp, mypet)'' -> return the exp that are needed to levelup in this method

*  ''function getCurrentExp(exp, mypet)''  -> return the actual exp of the current level in this method.

*  ''function getExpByLevel(level, mypet)''  -> return the exp needed for this level in this method.
### Usable Methods

You can use the following methods to react individually on some pets:

*  ''MyPet.getType()'' -> pet-type of the *MyPet*.

*  ''MyPet.getOwnerName()'' -> name of the owner.

*  ''MyPet.getSkilltree()'' -> selected skilltree.

*  ''MyPet.getUUID()'' -> internal UUID of the *MyPet*.

*  ''MyPet.getWorldGroup()'' -> worldgroup the *MyPet* is in.

----
`<box red>`If you have any questions related to this topic please send me a [private message](http://dev.bukkit.org/home/send-private-message/?to=xXKeyleXx) on BukkitDev or on the Spigot forums`</box>`
## Examples

You can find a working example [here](https///github.com/xXKeyleXx/MyPet/blob/master/experience-scripts/exp.js) (it calculates it the same way as it was calculated for players in [Minecraft 1.3.1](http://www.minecraftwiki.net/wiki/Experience#Leveling_Up)).
