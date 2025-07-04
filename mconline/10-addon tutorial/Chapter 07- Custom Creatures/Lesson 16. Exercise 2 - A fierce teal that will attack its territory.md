--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Exercise 2: The fierce duck that will attack the territory 

#### Author: Realm 

Download the fierce duck sample package: Download [sample package](https://g79.gdl.netease.com/guidedemo-case7v2.zip). 

```
{
  "format_version": "1.16.0",
  "minecraft:entity": {
    "description": {
      "identifier": "design:green_head_duck",
      "is_spawnable": true,
      "is_summonable": true,
      "is_experimental": false,
      "runtime_identifier": "design:green_head_duck"
    },
    "component_groups": {
    },

    "components": {
      "minecraft:breathable": {
        "total_supply": 15,
        "suffocate_time": 0
      },
      "minecraft:collision_box": {
        "width": 0.6,
        "height": 1.0
      },
      "minecraft:nameable": {
      },
      "minecraft:health": {
        "value": 4,
        "max": 4
      },
      "minecraft:hurt_on_condition": {
        "damage_conditions": [
          {
            "filters": { "test": "in_lava", "subject": "self", "operator": "==", "value": true },
            "cause": "lava",

            "damage_per_tick": 4
          }
        ]
      },
      "minecraft:movement": {
        "value": 0.25
      },
      "minecraft:damage_sensor": {
        "triggers": {
          "cause": "fall",
          "deals_damage": false
        }
      },
      "minecraft:behavior.rise_to_liquid_level": {
        "priority": 0,
        "liquid_y_offset": -0.5,
        "rise_delta": 0.01,
        "sink_delta": 0.01
      },
      "minecraft:leashable": {
        "soft_distance": 4.0,
        "hard_distance": 6.0,
        "max_distance": 10.0
      },
      "minecraft:balloonable": {        "mass": 0.5
      },
      "minecraft:navigation.walk": {
        "can_path_over_water": true,
        "can_sink": false,
        "avoid_damage_blocks": true
      },
      "minecraft:movement.basic": {
      },
      "minecraft:jump.static": {
      },
      "minecraft:can_climb": {
      },
      "minecraft:despawn": {
        "despawn_from_distance": {}
      },
      "minecraft:behavior.panic": {
        "priority": 1,
        "speed_multiplier": 1.5
      },
      "minecraft:behavior.tempt": {
        "priority": 4,
        "speed_multiplier": 1.0,
        "items": [
          "wheat_seeds",

          "beetroot_seeds",
          "melon_seeds",
          "pumpkin_seeds"
        ]
      },
      "minecraft:type_family": {
        "family": [ "duck", "mob" ]
      },
	  "minecraft:behavior.melee_attack": {
        "priority": 3,
        "speed_multiplier": 1,
        "track_target": false
      },
	  "minecraft:behavior.nearest_attackable_target": {
        "priority": 2,
        "reselect_targets": true,
		"must_see": false,
        "entity_types": [
          {
            "filters": {
              "all_of": [
                { "test": "is_family", "subject": "other", "value": "mob" },
				{ "test": "is_family", "subject": "other", "operator": "not", "value": "duck"}
              ]
            },
            "max_dist": 5
          }
        ]
      },
	  "minecraft:attack": {
		"damage": 1
	  },
      "minecraft:behavior.random_stroll": {
        "priority": 6,
        "speed_multiplier": 1.0
      },
      "minecraft:behavior.look_at_player": {
        "priority": 7,
        "look_distance": 6.0,
        "probability": 0.02
      },
      "minecraft:behavior.random_look_around": {
        "priority": 8
      },
      "minecraft:physics": {
      },
      "minecraft:pushable": {        "is_pushable": true,
        "is_pushable_by_piston": true
      }

}, 

"events": { 
} 
} 
} 
``` 

The behavior of attacking a territorial intruder can be imagined as how close you are to a teal to cause it to attack. Therefore, when setting a creature with melee ability, you need to combine three behaviors: 

1) minecraft:attack, its damage value can accept an array or an integer value. In the case of an array, you can let the damage take a random damage from the array from large to small, while a fixed value represents fixed damage. 

2) minecraft:behavior.nearest_attackable_target, its entity_types accepts a series of biological targets. In the target selector, we set the target to mob but not duck at the same time, that is, all creatures with mob tags but not duck tags. max_dist represents how far away it will be regarded as a target, must_see means whether it must be seen to be regarded as a target, and reselect_targets will continuously select the target closest to itself from a group of targets. 

3) minecraft:behavior.melee_attack, its speed_multiplier receives a floating point value, that is, when maintaining the attack state, how much speed will be given a bonus, 1 is 100%, then maintain the original speed, 1.5 is 150%. track_target receives a Boolean value, if set to true, it will keep following the target, even if it walks out of the attack range, false will stop the behavior after the target leaves the attack range. 



Special note: Since the minecraft:type_family component is used to mark the family type of the creature, the family tags carried by the original chicken are "mob" and "chicken". In theory, all the creatures in the original version have this mob tag. We keep the mob tag for the teal, and also allow other original creatures to include the teal in the target range when dealing with some behaviors that require judging the creature tag, such as when looking for a target, so as to be closer to the original ecology. In addition, we changed chicken to duck, one to emphasize that the entity carries the duck tag, and the other to exclude entities with the duck tag from the target range when searching for targets. If we keep the original chicken, it will become an entity that needs to remove the chicken tag, which will include creatures such as chickens, which does not meet actual needs.