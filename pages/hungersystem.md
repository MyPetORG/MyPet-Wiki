# Hunger-System

With the Hunger-System was a new value added. The *Hunger-Points*.
This value is always between **1** and **100**, where **100** is the best and **1** is the worst value.
After a periodic amount of time (can be set with the <font color="Coral">MyPet.HungerSystem.Time</font> setting) this value decreases and affects other stats of your pet.

## What is affected by the Hunger-Points?

### Hitpoints on respawn
When a pet respawns it doesn't has full hitpoints when the *Hunger-Points* is below **90**.
This tables shows how much the Hunger-Points affect the hitpoints on a respawn:

 | Hunger-Points | Hitpoints on respawn      |
 | ------------- | --------------------      |
 | 100-91        | **full** Hitpoints        |
 | 90-81         | **90%** of max. Hitpoints |
 | 80-71         | **80%** of max. Hitpoints |
 | 70-61         | **70%** of max. Hitpoints |
 | 60-51         | **60%** of max. Hitpoints |
 | 50-41         | **50%** of max. Hitpoints |
 | 40-31         | **40%** of max. Hitpoints |
 | 30-21         | **30%** of max. Hitpoints |
 | 20-11         | **20%** of max. Hitpoints |
 | 10-2          | **10%** of max. Hitpoints |
 | 1             | **1** Hitpoint            |

----

### Beacon range

The lower the Hunger-Points the less is the range of the beacon effect.
