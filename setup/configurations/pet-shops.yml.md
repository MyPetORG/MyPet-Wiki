---
description: Pet Shop Configuration
---

# pet-shops.yml

The _`pet-shops.yml`_ file contains the shops where players can buy pets.

You can create as many shops as you want, but all of them need different IDs \(`<shop-id>`\). Each shop can be opened by this it with the `/petshop <shop-id>` command. Every item in the shop needs a unique ID too \(`<id>`\).

<table>
  <thead>
    <tr>
      <th style="text-align:left">Setting</th>
      <th style="text-align:center">Type</th>
      <th style="text-align:center">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Shops:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:center"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;<b>&lt;shop-id&gt;:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:center">
        <p><code>&lt;shop-id&gt;</code> can be chosen freely but needs to be unique
          for every shop</p>
        <p><em>(This is <code>&lt;shop-name&gt;</code> in the shop permission node)</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Name:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:center">The name that will be shown in the shop overview</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;<b>Balance</b>:</td>
      <td style="text-align:center"></td>
      <td style="text-align:center"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Type:</td>
      <td style="text-align:center">string</td>
      <td style="text-align:center">TODO</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;<b>Pets</b>:</td>
      <td style="text-align:center"></td>
      <td style="text-align:center"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;<b>&lt;id&gt;:</b>
      </td>
      <td style="text-align:center"></td>
      <td style="text-align:center"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Name:</td>
      <td
      style="text-align:center">string</td>
        <td style="text-align:center">The name the pet will have</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Description:</td>
      <td
      style="text-align:center">list of strings</td>
        <td style="text-align:center">The description that will be shown when hovering the shop item</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Position:</td>
      <td
      style="text-align:center">integer</td>
        <td style="text-align:center">The slot in the inventory the pet item will have in the shop</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Exp:</td>
      <td
      style="text-align:center">double</td>
        <td style="text-align:center">The XP the pet will have</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Price:</td>
      <td
      style="text-align:center">double</td>
        <td style="text-align:center">The price the player has to pay in order to get the pet</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Skilltree:</td>
      <td
      style="text-align:center">string</td>
        <td style="text-align:center">The skilltree the pet will have</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;PetType:</td>
      <td
      style="text-align:center">string</td>
        <td style="text-align:center">The mob type of the pet</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;&#xA0;Options:</td>
      <td
      style="text-align:center">list of strings</td>
        <td style="text-align:center">These work exaclty like the parameters for the pet create admin command.</td>
    </tr>
  </tbody>
</table>

