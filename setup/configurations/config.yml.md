---
description: Main Configuration
---

# config.yml

The _config.yml_ file is the main configfile of _MyPet_. All pet type related options can be found in the [pet-config.yml](pet-config.yml.md).

<table>
  <thead>
    <tr>
      <th style="text-align:left">Setting</th>
      <th style="text-align:center">Type</th>
      <th style="text-align:right">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>MyPet:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">Disable-All-Actionbar-Messages</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true, no actionbar messages will be used.</td>
    </tr>
    <tr>
      <td style="text-align:left">OwnerCanAttackPet:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable to allow the owner to hit his own pet.</td>
    </tr>
    <tr>
      <td style="text-align:left">DisablePetVersusPlayer:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Prevents combat between players and pets.</td>
    </tr>
    <tr>
      <td style="text-align:left">RemovePetsAfterRelease:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable to remove pets when they get released. Prevents players from griefing
        other players by releasing monsters in their vicinity.</td>
    </tr>
    <tr>
      <td style="text-align:left">ReleasePetsOnDeath:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable to release the pet when it dies. Player that have the <em>MyPet.admin</em> permission
        are excluded from this</td>
    </tr>
    <tr>
      <td style="text-align:left">Make-Pet-Invisible-When-Owner-Is-Invisible:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Makes the pet invisible when the owner has the <code>Invisible</code> effect.
        Does not affect vanished players.</td>
    </tr>
    <tr>
      <td style="text-align:left">RetainEquipmentOnTame:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Allows mobs to keep their equipment after leashed (based on the default
        MC drop chance).</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;FollowStartDistance:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">Sets the distance from the player where the pet starts to follow him.</td>
    </tr>
    <tr>
      <td style="text-align:left">Max-Stored-Pet-Count:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">Sets the maximum amount of inactive (stored) pets a player can have.</td>
    </tr>
    <tr>
      <td style="text-align:left">Throw-PlayerMoveEvent-While-Riding:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Disable this when other plugins cause bugs because of the thrown events.</td>
    </tr>
    <tr>
      <td style="text-align:left">OverwriteLanguages:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">If you don&apos;t want per player language detection you can use this
        to overwrite the language for all players. Available languages can be found
        <a
        href="https://github.com/xXKeyleXx/MyPet-Translations">here</a>. Example: <code>pt_br</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Right-Click-Command</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">
        <p>a command that will be executed when a player rightclicks his own pet.
          Supports the following placeholders:</p>
        <p><code>%pet_owner%</code>
        </p>
        <p><code>%pet_level%</code>
        </p>
        <p><code>%pet_status%</code>
        </p>
        <p><code>%pet_type%</code>
        </p>
        <p><code>%pet_uuid%</code>
        </p>
        <p><code>%pet_world_group%</code>
        </p>
        <p><code>%pet_skilltree_name%</code>
        </p>
        <p><code>%pet_name%</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"> <b>Leash:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Consume:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable to consume the leash item when a new pet is leashed.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;AllowRanged</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable to allow players to catch pets with projectiles when the leash
        item is a bow</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Log:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Level:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">Set the level at which the messages will be logged to the file. All possible
        log levels can be found <a href="https://docs.oracle.com/javase/7/docs/api/java/util/logging/Level.html#field_summary">here</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Report-Errors</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If enabled all errors that occur are reported automatically</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Unique-ID</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">
        <p>This is used to identify different users for the error reporter. This
          will allow the devs to see how many servers have the same problem.</p>
        <p><b>DO NOT CHANGE!</b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Info:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Wiki-URL:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">This can be changed if the server has it&apos;s own Wiki for MyPet.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Update:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;Check:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Sets if the plugin will check for updates when it is loaded. This will
        not download the new version.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;Download:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Sets if the plugin will download the update.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;ReplaceOld:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Sets if the plugin will load the update on the next server start.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;In-Background</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true the plugin will not wait until the updated is downloaded on start.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;OP-Notification</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true, the plugin will notify OPs if a new version is available.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Repository:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Type:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The storage type where the plugin will save the pets into. Options: <code>SQLite</code> ,<code>MySQL</code> ,<code>MongoDB</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;ConvertFrom:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">This options allows to migrate from one storage type to another. For example
        from <code>SQLite</code> to <code>MySQL</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>MySQL:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Database:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The name of the MySQL database.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;TablePrefix:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The table prefix if the database is shared with other applications.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Host:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The address of the MySQL server.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Port:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">The port of the MySQL server.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Password:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The password of the MySQL user.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;User:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The username of the MySQL user.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;MaxConnections:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">The amount of simultaneous connections the plugin will create to the MySQL
        server. You can find more about the best pool size <a href="https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing">here</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">CharacterEncoding</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The encoding used by the database.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>MongoDB:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Database:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The name of the MongoDB database.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;CollectionPrefix:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The collection prefix if the database is shared with other applications.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Host:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The address of the MongoDB server.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Port:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">The port of the MongoDB server.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Password:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The password of the MongoDB user.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;User:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The username of the MongoDB user.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Respawn:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>Time:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;<b>Default:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Factor:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">Determines how long the owner has to wait until the pet respawns when
        it <b>wasn&apos;t</b> killed by a player.
        <br /> <code>Respawntime = Factor * (Level of MyPet) + Fixed</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Fixed:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">See <code>Factor</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;<b>Player:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Factor:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">Determines how long the owner has to wait until the pet respawns when
        it was killed by a <b>player</b>.
        <br /> <code>Respawntime = Factor * (Level of MyPet) + Fixed</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Fixed:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">See <code>Factor</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;<b>EconomyCost:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Factor:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">Determines how much it will cost if you want to revive a dead MyPet.
        <br
        /> <code>Costs = Factor * (Respawn Time in sec.) + Fixed</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Fixed:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">See <code>Factor</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Permissions:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Enabled:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Disable the use of <a href="../permissions.md">permissions</a> and fall
        back to the OP permission system.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Extended:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable if you want to use some addition permissions that can be found
        <a
        href="../permissions.md#extended-mypet-permissions">here</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>LevelSystem:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;CalculationMode:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">Set this to <code>JS</code> or <code>JavaScript</code> if you want use a custom
        <a
        href="../../systems/experience/expjs.md">exp.js</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>HungerSystem:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Active:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Disable the <a href="../../systems/hungersystem.md">hungersystem</a> if
        you don&apos;t want your pets need food to survive.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Time:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">Sets the interval (in seconds) in which the hunger counter will be reduced
        by <code>1</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;SaturationPerFeed:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">Sets the value the hunger counter will be increased by if the pet is fed.</td>
    </tr>
    <tr>
      <td style="text-align:left">Affect-Ride-Speed:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true the saturation affects the ride speed.</td>
    </tr>
    <tr>
      <td style="text-align:left">Affect-Beacon-Range:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true the saturation affects the beacon range.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Skilltree:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;AutomaticAssignment:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable to automatically assign a skilltree to a pet when it is leashed.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;RandomAssignment:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Like <code>AutomaticAssignment</code> but the skilltree is selected randomly.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;ChooseOnce:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enable this if players shouldn&apos;t be able to pick another skilltree
        once the pet has a skilltree.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;PreventLevellingWithout:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Pets without a skilltree will not gain XP if it is set to <code>true</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>SwitchFee:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Admin:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Set this to <code>true</code> if admins should pay the same skilltree switch
        penalty like normal players.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Percent:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">The percentage of XP a players has to pay if he switches to another skilltree.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Fixed:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">The amount of XP a players has to pay if he switches to another skilltree.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Name:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;Filter:</td>
      <td style="text-align:center">list</td>
      <td style="text-align:right">Every pet name is checked against this list of filters (string/regular
        expression).</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;MaxLength:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">The maximum length a petname can have.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>Tag:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Show:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Set this to <code>false</code> if you don&apos;t want nametags for MyPets.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Prefix:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">This text will be added in front of the name. You can use color codes
        and these placeholders:
        <br /> <code>&lt;owner&gt;</code> &#x21D2; name of the owner
        <br /> <code>&lt;level&gt;</code> &#x21D2; level of the pet</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Suffix:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">This text will be added the end of the name. You can use color codes and
        these placeholders:
        <br /> <code>&lt;owner&gt;</code> &#x21D2; name of the owner
        <br /> <code>&lt;level&gt;</code> &#x21D2; level of the pet</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Exp:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;DamageWeightedExperienceDistribution:</td>
      <td
      style="text-align:center">boolean</td>
        <td style="text-align:right">This setting allows pets to gain XP even if they did not kill the enemy.
          Every bit of damage is counted and when the enemy dies the XP will be split
          up to reflect the damage given to that enemy. So if a pet does 50% of the
          damage it will gain 50% of the total XP.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>Passive:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Always-Grant-Passive-XP:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">This setting allows the pet to always gain XP when the owner kills a monster,
        even if it has a damage skill (<a href="../../skills/damage.md">Damage</a> or
        <a
        href="../../skills/ranged.md">Ranged</a>).</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;PercentPerMonster:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">Sets the percentage of XP a pet will get when the owner kills an enemy.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>Loss:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Drop:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If this setting is set to <code>true</code> the lost XP is dropped on the
        ground and can be picked up by others.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Percent:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">Sets the percentage of XP a pet will lose when it dies.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Fixed:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">Sets the XP a pet will lose when it dies.</td>
    </tr>
    <tr>
      <td style="text-align:left">Allow-Level-Downgrade:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true pets can lose levels if they die.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>Gain:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;PreventFromSpawnReason:</td>
      <td style="text-align:center">list</td>
      <td style="text-align:right">This setting is a list of spawn reasons. Every mob that is spawned by
        any of these spawn reasons will not grant any XP. All spawn reasons can
        be found <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html#enum_constant_summary">here</a>. <b>This resets on every server reload/restart so it will not prevent it after a restart!</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;LevelCap:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">A pet can not gain any XP and level up if that level is reached.</td>
    </tr>
    <tr>
      <td style="text-align:left">Disabled-Worlds:</td>
      <td style="text-align:center">list</td>
      <td style="text-align:right">A list of worlds where pets can&apos;t gain any XP</td>
    </tr>
    <tr>
      <td style="text-align:left"> <b>Modifier:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">Global:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">
        <p>The global XP modifier.</p>
        <p>1.0 equals 100% XP / 2.0 equals 200% XP</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Use-Permissions:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">If true, the modifier can be changed via permissions too. See <a href="../permissions.md">permissions</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>Skill:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<a href="../../skills/control.md"><b>Control</b></a><b>:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Item:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">Sets the item that allows the player to use the <a href="../../skills/control.md">Control</a> skill
        the pet. This setting follows the <a href="configitems.md">config item</a> guidelines</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<a href="../../skills/ride.md"><b>Ride</b></a><b>:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Item:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">Sets the item that allows the player to mount the pet. This setting follows
        the <a href="configitems.md">config item</a> guidelines</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;HungerPerMeter:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">If the <a href="../../systems/hungersystem.md">Hunger-System</a> is active,
        this setting set the value the hunger value is decreased by for every ridden
        meter.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<a href="../../skills/backpack.md"><b>Backpack</b></a>:</td>
      <td
      style="text-align:center"></td>
        <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Creative:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Allows players to open the inventory of their pet when they are in creative
        mode.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;DropWhenOwnerDies:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">When this is set to <code>true</code> the pet will drop the content in it&apos;s
        inventory when the owner dies.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<a href="../../skills/beacon.md"><b>Beacon</b></a><b>:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;HungerDecreaseTime:</td>
      <td style="text-align:center">integer</td>
      <td style="text-align:right">If the <a href="../../systems/hungersystem.md">Hunger-System</a> is active,
        this setting sets the interval in which the value the hunger value is decreased
        by 1.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Party-Support:</td>
      <td style="text-align:center">boolean</td>
      <td style="text-align:right">Enables the support for parties from these plugins: <a href="https://www.spigotmc.org/resources/mcmmo.2445/">MCMMO</a>,
        <a
        href="https://www.spigotmc.org/resources/heroes.305/">Heroes</a>, <a href="http://dev.bukkit.org/bukkit-plugins/ancient-rpg/">Ancient</a>
          <br
          />If you have any party plugins MyPet should support please request them
          on GitHub or Discord.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
  </tbody>
</table>