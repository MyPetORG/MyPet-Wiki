---
description: This page describes what you need to do in order to upgrade to MyPet 3.0
---

# Update to 3.0

### Step 1 - Put the new JAR file in place

If you are running [MyPet-NPC](../hooks/npc.md) too you can delete that now as it is included into MyPet itself.

### Step 2 - Convert the skilltrees

**If you never touched the skilltrees you can skip this step!**   


If you made your own skilltrees or edited the default ones you need to convert them to the new format using the following steps:

1. open up the new SkilltreeCreator
2. select the folder you want to save your new skilltrees in
3. Your browser will open and you will see the new [Skilltree Creator](../systems/skilltrees/skilltreecreator.md)
4. open the menu on the top left hand corner
5. select `Import Legacy Skilltree`
6. follow the 3 steps of the wizard
7. hit the save button
8. upload the new `.st.json` files to the **skilltrees** folder on your server

### Step 3 - Adjust your config files

MyPet doesn't support numeric item IDs anymore. All settings that requires an [config item](configurations/configitems.md) will require the 1.13 item ID even if you don't run a 1.13 server

