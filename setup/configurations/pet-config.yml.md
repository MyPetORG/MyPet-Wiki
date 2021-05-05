---
description: Pet Configuration
---

# pet-config.yml

The _`pet-config.yml`_ file contains all MyPet-Type specific settings. All other settings can be found in the main config \([config.yml](config.yml.md)\).

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
      <td style="text-align:left">&#xA0;&#xA0;<b>Pets:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;<b>&lt;MyPet-Type-Name&gt;:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:right"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;HP:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">The maximum HP the pet (type) has by default.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Speed:</td>
      <td style="text-align:center">double</td>
      <td style="text-align:right">
        <p>The running speed the pet-type has by default.</p>
        <p>&#x2757; Small changes have a massive impact on the speed &#x2757;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Food:</td>
      <td style="text-align:center">list</td>
      <td style="text-align:right">The food this pet-type eats. This setting must be a list of valid <a href="configitems.md">config items</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;LeashItem:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:right">The item this pet-type can be leashed with. This setting must be a valid
        <a
        href="configitems.md">config item</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;LeashRequirements:</td>
      <td style="text-align:center">list</td>
      <td style="text-align:right">A list of valid <a href="../../systems/leashflag.md">Leash Requirements</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;CustomRespawnTimeFactor:</td>
      <td style="text-align:center">int</td>
      <td style="text-align:right">This setting allows to change the respawn times pet-type. This value will
        be added on top of the value from the main config.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;CustomRespawnTimeFixed:</td>
      <td style="text-align:center">int</td>
      <td style="text-align:right">This setting allows to change the respawn times pet-type. This value will
        be added on top of the value from the main config.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;ReleaseOnDeath:</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:right">Whether or not the pet is released on death.</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;RemoveAfterRelease:</td>
      <td style="text-align:center">bool</td>
      <td style="text-align:right">Whether or not the Mob is deleted after the pet is released.</td>
    </tr>
  </tbody>
</table>

