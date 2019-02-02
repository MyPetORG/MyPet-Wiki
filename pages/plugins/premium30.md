# MyPet-Premium 3.0

## Breaking changes

### Skilltree format

* MyPet now uses the JSON format for all skilltree files
* A new and better editor is also included \(doubleclick the jar file\)
  * after selecting the skilltree folder \(of your choice\) it will open a new tab in your default webbrowser
* The skilltree system got completely rewritten so old skilltrees can not be loaded with the new version
  * If you never changes the skilltrees you don't have to do anything
  * You can convert your old skilltrees with the new SkilltreeCreator
    1. open the new SkilltreeCreator
    2. select the folder you want to save your new skilltrees in
    3. open the menu on the top left hand corner
    4. select `Import Legacy Skilltree`
    5. follow the 3 steps of the wizard
    6. hit the save button
    7. upload the new `.st.json` files to the skilltree folder on your server

## Other changes

* Fixed Ender Dragon interactions
* improved EXP calculation system
  * JS files just need the `getExpByLevel(level, info)` function now
    * you don't have to do anything if you use a exp.js file
* pets can level down if they die \(can be enabled via the `Allow-Level-Drowngrade` setting\)
* some other longstanding bugs got fixed

### Overhaul of the LeashFlag system

* they work like before but there are more and some of them can be configured
* also there are flags that require other plugins
* New flags:
  * `World` flag
    * `World:<world name>:...`
    * Examples:
      * `World:default`
      * `World:default:nether`
  * `Size` flag
    * works only for slimes and magma cubes
    * `Size:min=<min size>:max=<max size>`
      * `min` is an optional parameter
      * `max` is an optional parameter
    * `Size:<exact size>`
    * Examples:
      * `Size:min=2`
      * `Size:min=2:max=4`
      * `Size:max=2`
      * `Size:3`
  * `BelowHP` flag
    * checks if a mob is below a certain health threshold
    * `BelowHP:<health>[%]`
      * `%` is optional
    * Examples:
      * `BelowHP:2`
      * `BelowHP:2.5`
      * `BelowHP:10%`
  * `Chance` flag
    * with this flag you can add a random factor to the leashing
    * `Chance:<chance>`
      * `<chance>` is the chance in percent \(%\)
    * Examples:
      * `Chance:2`
      * `Chance:50`
  * `mcMMO` flag
    * checks if a player has a skill above a certain level
    * `mcMMO:<job>=<level>:...`
    * if multiple jobs are specified all requirements must be fullfilled
    * Examples:
      * `mcMMO:Mining=10`
      * `mcMMO:Mining=2:Taming=25`
  * `MythicMobs` flag
    * checks if a mob is from a specific MythicMob type
    * `MythicMobs:<type name>:...`
    * Examples:
      * `MythicMobs:SkeletalKnight`
      * `MythicMobs:StaticallyChargedSheep:SkeletonKing`

