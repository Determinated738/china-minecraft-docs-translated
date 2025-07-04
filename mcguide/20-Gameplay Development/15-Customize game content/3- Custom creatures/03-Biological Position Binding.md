--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Entity Location Binding 

Developers can also add a location component to the entity json to add a rideable location. The component starts with `minecraft:rideable` and ends with **minecraft:boat**: 

```json 
"format_version": "1.13.0", 
"minecraft:entity": { 
"description": { 
"identifier": "minecraft:boat", 
"is_spawnable": false, 
"is_summonable": true, 
"is_experimental": false 
}, 

"components": { 
//Omit components that are not of interest 
"minecraft:rideable": { 
"seat_count": 2, 
"interact_text": "action.interact.ride.boat", 
"pull_in_entities": true, 
"seats": [ 
{ 
            "position": [ 0.0, -0.2, 0.0 ],
            "min_rider_count": 0,
            "max_rider_count": 1,

            "rotate_rider_by": -90,
            "lock_rider_rotation": 90
          },
          {
            "position": [ 0.2, -0.2, 0.0 ],
            "min_rider_count": 2,
            "max_rider_count": 2,

            "rotate_rider_by": -90,
            "lock_rider_rotation": 90
          },
          {
            "position": [ -0.6, -0.2, 0.0 ],
            "min_rider_count": 2,
            "max_rider_count": 2,
            "lock_rider_rotation": 90
          }

] 
}, 

} 
} 
} 
``` 

**minecraft:horse_wild**： 

``` 
"minecraft:rideable": { 
"seat_count": 1, 
"family_types": [ 
"player", 
"zombie" 
], 
"interact_text": "action.interact.mount", 
"seats": { 
"position": [ 0.0, 1.1, -0.2 ] 
} 

}, 
``` 

**Parameter explanation**： 

- seat_count: default value 1, change the number of riding positions the mob has 
- crouching_skip_interact: default value true, when true, if the entity interacting with this entity is crouching, it cannot be interacted with 
- interact_text: default value "", the text content displayed on the UI button when interacting with the player 
- family_types: default value "", the types of entities that can ride this entity 
- controlling_seat: default value 0, controls the position index of this entity 
- pull_in_entities: default value false, if true, this entity will pull entities of the correct family_type into any available seats 
- rider_can_interact: default value false, if true, this entity will be selected when viewed by a rider 
- seats: default value "", details of the position: 
- position: default value [0.0,0.0,0.0], the position of this seat relative to the position of this entity 
- min_rider_count: default value 0, defines the minimum number of passengers that must ride this entity before this seat can be used 
- max_rider_count: default value 0, defines the maximum number of passengers that must ride this entity before this seat can be used 
- rotate_rider_by: default value 0.0, the rider rotation angle 
- lock_rider_rotation: default value 181.0 The angle (in degrees) that the rider is allowed to rotate when rotating this entity. If this setting is ignored, there is no limit.