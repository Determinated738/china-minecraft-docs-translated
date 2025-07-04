--- 
front: https://nie.res.netease.com/r/pic/20210730/ee109f39-8987-46e0-9fe7-40ebb23060fa.png 
hard: Getting Started 
time: 20 minutes 
--- 
# Set up a work area for NPCs 
When all NPCs are ready, they need to return to their jobs and not run around. To meet this condition, there are the following solutions: 
- Directly delete the movement behavior below so that it can only stay in place. This method is the simplest and crudest. The NPC will always stay in the same place wherever it is placed, which is very safe; but our NPC will lose its "vitality", which is very rigid. This method is not recommended. 

```json 
"minecraft:movement": { 
"value": 0.25 
}, 
"minecraft:navigation.walk": { 
"can_path_over_water": true, 
"can_pass_doors": true, 
"can_open_doors": true, 
"avoid_water": true 
}, 
"minecraft:movement.basic": { 
}, 
``` 

- Remove the NPC's wandering behavior, so that it can only walk to sleep, but it will stay where it wakes up during the day 

```json 
"minecraft:behavior.random_stroll": { 
"priority": 7, 
"speed_multiplier": 1 
}, 
``` 

- The best and simplest way is to use blocks to seal it in a fixed area, allowing it to wander around the area 

![4](./images/7.gif) 

In addition to the above methods, there are definitely better solutions waiting to be discovered. This tutorial stops here and provides a simple solution for everyone. 

