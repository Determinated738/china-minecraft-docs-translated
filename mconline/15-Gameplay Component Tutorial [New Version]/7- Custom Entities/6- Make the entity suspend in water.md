--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 25 minutes 
--- 

# Make the entity suspended in water 

As we know, ducks like to swim on the water surface. When ducks swim, although their feet are flapping in the water, they are extremely stable on the water surface. The idiom "a duck paddles in the water" means to make an effort secretly, which is not visible on the surface. However, when our current water duck floats in the water, it just goes up and down like other creatures. In this section, we will change the behavior of our duck to continuously float on the water surface. 

## Find the corresponding component in the original entity 

We recall which entity in the original entity has the behavior of floating on the surface of the liquid. It is not difficult to find that the barefoot beast is an entity that can float on the surface of lava. Therefore, there must be a component that can be used for suspension in the barefoot beast's behavior file. Let's open the barefoot beast's behavior file to find out. Since floating on the water surface should be an AI intention, we focus on the components with the prefix `behavior.`. 

```json
"minecraft:behavior.rise_to_liquid_level": {
  "priority": 0,
  "liquid_y_offset": 0.25,
  "rise_delta": 0.01,
  "sink_delta": 0.01
},
"minecraft:behavior.move_to_lava": {
  "priority": 7,
  "search_range": 16,
  "search_height": 10,
  "goal_radius": 0.9,
  "search_count": 30
},
"minecraft:behavior.random_stroll": {
  "priority": 8,
  "speed_multiplier": 0.8
},
"minecraft:behavior.look_at_player": {
  "priority": 9,  "look_distance": 6.0,
  "probability": 0.02
},
"minecraft:behavior.random_look_around": {
  "priority": 10
},
"minecraft:behavior.panic": {
  "priority": 3,
  "speed_multiplier": 1.1,
  "panic_sound": "panic",
  "sound_interval": {
    "range_min": 1.0,
    "range_max": 3.0
  }
},
"minecraft:behavior.tempt": {

"priority": 5, 
"speed_multiplier": 1.2, 
"items": [ 
"warped_fungus", 
"warped_fungus_on_a_stick" 
], 
"tempt_sound": "tempt", 
"sound_interval": { 
"range_min": 2.0, 
"range_max": 5.0 
} 
} 
``` 

Quickly, we can locate the component `minecraft:behavior.rise_to_liquid_level` with a `priority` of 0 by its literal meaning of its component name. In fact, this is indeed the AI intention that can make the barefoot float. We copy it to the duck. 

## Implement the behavior of the water teal 

We make a slight modification and then copy it to the behavior definition file of the water teal. 

```json 
"minecraft:behavior.rise_to_liquid_level": { 
"priority": 0, 
"liquid_y_offset": -0.5, 
"rise_delta": 0.01, 
"sink_delta": 0.01 
} 
``` 

This is not the end. Because we know that the reason why the teal floats up and down on the water is because another AI intention is also in effect, that is, `minecraft:behavior.float`. Let's delete this AI intention. 

Finally, we change the navigation component of the teal. Because we deleted `minecraft:behavior.float`, the teal's AI no longer requires the teal to stay on the water, so we add `can_sink` to the teal's navigation component `minecraft:navigation.walk` and set it to `false`. In this way, the teal will not sink in the water. 

```json 
"minecraft:navigation.walk": { 
"can_path_over_water": true, 
"can_sink": false, 
"avoid_damage_blocks": true 
} 
``` 

So far, we have theoretically implemented the behavior replacement of the teal. 

```json 
{ 
"format_version": "1.16.0", 
"minecraft:entity": { 
"description": { 
"identifier": "tutorial_demo:teal", 
"runtime_identifier": "minecraft:chicken",

      "is_spawnable": true,
      "is_summonable": true,
      "is_experimental": false
    },
    "component_groups": {
      "minecraft:teal_baby": {
        "minecraft:is_baby": {},
        "minecraft:scale": {
          "value": 0.5
        },
        "minecraft:ageable": {
          "duration": 1200,
          "feed_items": ["wheat_seeds", "beetroot_seeds", "melon_seeds", "pumpkin_seeds"],
          "grow_up": {
            "event": "minecraft:ageable_grow_up",
            "target": "self"
          }
        },
        "minecraft:behavior.follow_parent": {
          "priority": 5,
          "speed_multiplier": 1.1
        }
      },
      "minecraft:teal_adult": {
        "minecraft:experience_reward": {
          "on_bred": "Math.Random(1,7)",
          "on_death": "query.last_hit_by_player?Math.Random(1,3):0"
        },
        "minecraft:loot": {
          "table": "loot_tables/entities/chicken.json"
        },
        "minecraft:breedable": {
          "require_tame": false,
          "breeds_with": {
            "mate_type": "tutorial_demo:teal",
            "baby_type": "tutorial_demo:teal",
            "breed_event": {
              "event": "minecraft:entity_born",
              "target": "baby"
            }          },
          "breed_items": ["wheat_seeds", "beetroot_seeds", "melon_seeds", "pumpkin_seeds"]
        },
        "minecraft:behavior.breed": {
          "priority": 3,
          "speed_multiplier": 1
        },
        "minecraft:rideable": {
          "seat_count": 1,
          "family_types": ["zombie"],

          "seats": {
            "position": [0, 0.4, 0]
          }
        },
        "minecraft:spawn_entity": {
          "entities": {
            "min_wait_time": 300,
            "max_wait_time": 600,
            "spawn_sound": "plop",
            "spawn_item": "egg",
            "filters": {
              "test": "rider_count",
              "subject": "self",
              "operator": "==",
              "value": 0
            }
          }
        }
      }
    },
    "components": {
      "minecraft:type_family": {
        "family": ["chicken", "mob"]
      },
      "minecraft:breathable": {
        "total_supply": 15,
        "suffocate_time": 0
      },
      "minecraft:collision_box": {
        "width": 0.6,
        "height": 0.8
      },
      "minecraft:nameable": {},
      "minecraft:health": {
        "value": 4,
        "max": 4
      },
      "minecraft:hurt_on_condition": {
        "damage_conditions": [
          {
            "filters": {
              "test": "in_lava",
              "subject": "self",
              "operator": "==",
              "value": true
            },
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
      "minecraft:leashable": {
        "soft_distance": 4,
        "hard_distance": 6,
        "max_distance": 10
      },
      "minecraft:balloonable": {
        "mass": 0.5
      },
      "minecraft:navigation.walk": {
        "can_path_over_water": true,
        "can_sink": false, // Adding will not sink
        "avoid_damage_blocks": true
      },
      "minecraft:movement.basic": {},
      "minecraft:jump.static": {},      "minecraft:can_climb": {},
      "minecraft:despawn": {
        "despawn_from_distance": {}
      },
      "minecraft:behavior.rise_to_liquid_level": {
        "priority": 0,
        "liquid_y_offset": -0.5,
        "rise_delta": 0.01,
        "sink_delta": 0.01
      }, // Add the floating behavior of the barefoot beast
      "minecraft:behavior.panic": {
        "priority": 1,
        "speed_multiplier": 1.5
      },
      "minecraft:behavior.mount_pathing": {
        "priority": 2,
        "speed_multiplier": 1.5,
        "target_dist": 0,
        "track_target": true
      },      "minecraft:behavior.tempt": {
        "priority": 4,
        "speed_multiplier": 1,
        "items": ["wheat_seeds", "beetroot_seeds", "melon_seeds", "pumpkin_seeds"]
      },

      "minecraft:behavior.random_stroll": {
        "priority": 6,
        "speed_multiplier": 1
      },
      "minecraft:behavior.look_at_player": {
        "priority": 7,
        "look_distance": 6,
        "probability": 0.02
      },
      "minecraft:behavior.random_look_around": {
        "priority": 8
      },
      "minecraft:physics": {},
      "minecraft:pushable": {
        "is_pushable": true,
        "is_pushable_by_piston": true
      },
      "minecraft:conditional_bandwidth_optimization": {}
    },
    "events": {
      "from_egg": {
        "add": {
          "component_groups": ["minecraft:teal_baby"]
        }
      },
      "minecraft:entity_spawned": {
        "randomize": [
          {
            "weight": 95,
            "trigger": "minecraft:spawn_adult"
          },
          {
            "weight": 5,
            "add": {
              "component_groups": ["minecraft:teal_baby"]
            }
          }
        ]
      },
      "minecraft:entity_born": {
        "remove": {},
        "add": {
          "component_groups": ["minecraft:teal_baby"]
        }
      },
      "minecraft:ageable_grow_up": {
        "remove": {
          "component_groups": ["minecraft:teal_baby"]
        },
        "add": {

"component_groups": ["minecraft:teal_adult"] 
} 
}, 
"minecraft:spawn_adult": { 
"add": { 
"component_groups": ["minecraft:teal_adult"] 
} 
} 
} 
} 
} 
``` 

But in fact, due to some defects, our current Teal will still ignore the `minecraft:behavior.rise_to_liquid_level` behavior in the actual game and add a `minecraft:behavior.float` behavior to itself. This will cause our behavior replacement to fail. This is because our Teal package is generated by Blockbench and uses the latest Microsoft manifest file format version. We need to change the format version in the manifest file from 2 to 1 to eliminate this hidden danger. 

Similarly, we also need to replace the format version of the manifest file from 2 to 1 in the resource package, otherwise the Teal texture will not be loaded due to the mismatch of the format version. Due to the change in the format version, this will affect the minimum engine version, so we delete the minimum engine version in the resource pack, otherwise it will cause loading failure. 

```json
{
  "format_version": "1.10.0",
  "minecraft:client_entity": {
    "description": {
      "identifier": "tutorial_demo:teal",
      //"min_engine_version": "1.12.0",
      "materials": {
        "default": "chicken",
        "legs": "chicken_legs"
      },
      "textures": {
        "default": "textures/entity/teal"
      },
      "geometry": {
        "default": "geometry.teal"
      },
      "animations": {
        "move": "animation.teal.move",
        //"general": "animation.teal.general",
        "look_at_target": "animation.common.look_at_target",
        "baby_transform": "animation.teal.baby_transform"
      },
      "scripts": {
        "animate": [
          //"general",
          {
            "move": "query.modified_move_speed"
          },
          "look_at_target",
          {
            "baby_transform": "query.is_baby"
          }

] 
}, 
"render_controllers": ["controller.render.chicken"], 
"spawn_egg": { 
"base_color": "#62c287", 
"overlay_color": "#87692b" 
} 
} 
} 
} 
``` 

At the same time, we delete the `general` animation. The `general` animation is a hard-coded wing flapping animation, which will be played when the duck is in water or air. However, as we all know, ducks do not flap their wings when swimming, so we delete this animation directly. 

![](./images/8.6_in-game.gif) 

We enter the game and can see that our duck does have the AI intention of floating!