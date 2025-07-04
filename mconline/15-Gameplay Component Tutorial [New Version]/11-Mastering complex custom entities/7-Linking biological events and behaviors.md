--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 25 minutes 
--- 
# Linking creature events and behaviors 

Finally, let's explore the trigger component of the creature. In this section, we want to use **Trigger** to achieve a "refuge" mechanism for a squirrel. 

## Events and Triggers 

Through the previous chapters, we have learned that **Event** is a very important mechanism in the entity definition file. We can trigger different effects, add or remove component groups by defining different events. The trigger mechanism of events is also diverse. However, in addition to the hard-coded trigger of the built-in event, the most triggering means should be the **Trigger** component. 

The trigger component is also a kind of entity behavior package component. Unlike other types of components, trigger components are mainly used to trigger an event. In other words, trigger components are born for events. The principle of triggers is similar to event monitoring in the module SDK, which is to monitor certain system events and then execute specified content at a specific time. However, in data-driven files such as entity definition files, the content of event response execution is often limited. Here, triggers can only be used to trigger another event defined in the entity behavior package definition file. 

There are also many types of entity trigger components. Here we want to make a mechanism that squirrels will run away after being injured, so we need to use triggers related to injuries. In the component definition of the predator, we can find similar triggers. 

```json 
"minecraft:on_hurt": { 
"event": "minecraft:ranged_mode", 
"target": "self" 
}, 
"minecraft:on_hurt_by_player": { 
"event": "minecraft:ranged_mode", 
"target": "self" 
}, 
"minecraft:on_target_escape": { 
"event": "minecraft:calm", 
"target": "self" 
} 
``` 

Here, `minecraft:on_hurt` is triggered when the entity is damaged, `minecraft:on_hurt_by_player` is triggered when the entity is damaged by the player, and `minecraft:on_target_escape` is triggered when the target of the entity disappears (that is, when the entity is no longer considered as a target). 

We can use `minecraft:on_hurt` and `minecraft:on_target_escape` to design an escape mechanism. 

## Design an escape mechanism for squirrels 

We know that in order to make squirrels escape, we should use an AI intention that can be used to avoid creatures. Through the understanding of the original mechanism, we know that creepers will avoid "cat" creatures. We use this to look for relevant AI intentions in the behavior file of creepers. As expected, we found the AI intention `minecraft:behavior.avoid_mob_type` that avoids specific creatures. This is his expression in the creeper file: 

```json 
"minecraft:behavior.avoid_mob_type": { 
"priority": 3, 
"entity_types": [ 
{ 
"filters": { 
"any_of": [ 
{ "test" : "is_family", "subject" : "other", "value" : "ocelot"}, 
{ "test" : "is_family", "subject" : "other", "value" : "cat"}

] 
}, 
"max_dist": 6, 
"walk_speed_multiplier": 1, 
"sprint_speed_multiplier": 1.2 
} 
] 
} 
``` 

We can use this AI intent as the intention for the squirrel to avoid creatures that harm it. In order to modify it to the function we need, we need to first understand a minecraft mechanism used in this AI intent - **Filter**. 

The `filters` field in the above code is the field used to specify the filter. We can see that the vanilla creeper specifies two filters and uses the `any_of` logic, which means that as long as one of the two is satisfied, the AI intent can be triggered. Here the vanilla uses the `is_family` filter. The filter is a string test. Here the vanilla tests whether the opposing entity is an ocelot or a cat respectively, and once it is satisfied, the avoidance AI intent is executed. 

We want our entity to avoid the entity that harms it. We know we already have the `minecraft:behavior.hurt_by_target` AI intent, and any entity that hurts it will be marked as a target by it. So we only need the `has_target` filter, which is a boolean test. We just need to test whether the opposing entity is the target of our entity. 

Our modified components are as follows: 

```json 
"minecraft:behavior.avoid_mob_type": { 
"priority": 3, 
"entity_types": [ 
{ 
"filters": { 
"test": "is_target", 
"subject": "other", 
"value": true 
}, 
"max_dist": 6, 
"walk_speed_multiplier": 1, 
"sprint_speed_multiplier": 1.2 
} 
] 
} 
``` 

In this way, as long as the opposing entity is its target, our squirrel will automatically avoid it to a distance of 6 meters. 

Of course, here we intend to do this through triggers. Although due to the existence of filters, it is not necessary to use triggers, but we still design a squirrel that uses triggers. The designed entity definition file is as follows: 

```json 
{ 
"format_version": "1.12.0", 
"minecraft:entity": { 
"description": { 
"identifier": "tutorial_demo:squirrel", 
"is_experimental": false, 
"is_spawnable": true, 
"is_summonable": true 
},

    "component_groups": {
      "tutorial_demo:color_red": {
        "minecraft:variant": {
          "value": 0
        }
      },
      "tutorial_demo:color_gray": {
        "minecraft:variant": {
          "value": 1
        }
      },
      "tutorial_demo:escaping": {
        "minecraft:behavior.avoid_mob_type": {
          "priority": 3,
          "entity_types": [
            {
              "filters": {
                "test": "is_target",
                "subject": "other",
                "value": true
              },
              "max_dist": 6,
              "walk_speed_multiplier": 1,
              "sprint_speed_multiplier": 1.2
            }
          ]
        }
      }    },
    "components": {
      // ...
      "minecraft:behavior.hurt_by_target": {
        "priority": 1
      },
      "minecraft:behavior.delayed_attack": {
        "priority": 4,
        "reach_multiplier": 1.5,
        "attack_duration": 0.75,
        "hit_delay_pct": 0.25,
        "track_target": true,
        "sound_event": "attack.strong"
      },
      "minecraft:behavior.random_stroll": {
        "priority": 6,
        "xz_dist": 2,
        "y_dist": 1,
        "speed_multiplier": 0.8
      },
      "minecraft:behavior.random_look_around": { "priority": 9

      },
      "minecraft:behavior.look_at_player": {
        "priority": 11
      },
      // ...
      "minecraft:movement": {
        "value": 0.3
      },
      "minecraft:health": {
        "value": 30,
        "max": 30
      },
      "minecraft:on_hurt": {
        "event": "tutorial_demo:escape_started",
        "target": "self"
      },
      "minecraft:on_hurt_by_player": {
        "event": "tutorial_demo:escape_started",
        "target": "self"
      },
      "minecraft:on_target_escape": {
        "event": "tutorial_demo:escape_ended",
        "target": "self"
      }
    },
    "events": { "minecraft:entity_spawned": { 
// ... 
}, 
"tutorial_demo:escape_started": { 
"add": { 
"component_groups": [ 
"tutorial_demo:escaping" 
] 
} 
}, 
"tutorial_demo:escape_ended": { 
"remove": { 
"component_groups": [ 
"tutorial_demo:escaping" 
] 
} 
} 
} 
} 
} 
``` 

Here we add a `tutorial_demo:escaping` component group for the dynamic addition and subtraction of the `minecraft:behavior.avoid_mob_type` AI intent. Then we use the `tutorial_demo:escape_started` and `tutorial_demo:escape_ended` events to add and subtract component groups. Finally, we use `minecraft:on_hurt`, `minecraft:on_hurt_by_player` and `minecraft:on_target_escape` to trigger two events. In this way, the implementation of a dynamic addition and deletion function (here is to add and delete the AI intention of avoiding creatures) is completed. 


Of course, if we have a strong "brain-filling" ability, we can find that such a design has an obvious disadvantage. That is, due to the existence of `minecraft:behavior.delayed_attack`, although its priority is 4, which is lower than `minecraft:behavior.avoid_mob_type` with a priority of 3, `minecraft:behavior.avoid_mob_type` will only make the entity avoid to 6 meters away. When the entity walks to 6 meters away, `minecraft:behavior.avoid_mob_type` will be temporarily deactivated. At this time, `minecraft:behavior.delayed_attack` will be activated because the high-priority AI intention is deactivated, and the entity will re-approach the target that attacked it before. When it approaches a certain distance, it will reactivate `minecraft:behavior.avoid_mob_type` because it is too close, and `minecraft:behavior.delayed_attack` will be deactivated again. The entity will be in a cycle of avoiding and approaching. We can also see this intuitively through ImGui in the PC development version. 

![](./images/12.7_in-game_1.gif) 

We need to optimize this. 

### Optimize data 

We intend to solve this problem by changing the existence of `minecraft:behavior.delayed_attack`. We expect the behavior of the two variants of squirrels to be inconsistent. The red squirrel is more "brave" and will fight back as long as someone hits it, while the gray squirrel is more "weak" and will run away when someone hits it. So, how do we implement this mechanism? In fact, triggers such as `minecraft:on_hurt` can also use filters for conditional triggering. We can write a filter like this: 

```json 
"minecraft:on_hurt": { 
"event": "tutorial_demo:escape_started", 
"filters":{ 
"test": "is_variant", 
"value": 1 
}, 
"target": "self" 
}, 
"minecraft:on_hurt_by_player": { 
"event": "tutorial_demo:escape_started", 
"filters":{ 
"test": "is_variant", 
"value": 1 
}, 
"target": "self" 
}, 
"minecraft:on_target_escape": { 
"event": "tutorial_demo:escape_ended", 
"target": "self" 
} 
``` 

Where the `is_variant` filter is the filter used to detect the value of the variant. The variant value of the gray squirrel is 1, so we only trigger the event of adding the corresponding AI intention when the variant value is detected to be 1. The red squirrel also adds the delayed attack component in the form of a component group when it is generated, so that the gray squirrel will not have this component. We moved the `minecraft:behavior.delayed_attack` component to the red squirrel variant component group, like this: 

```json 
{ 
"format_version": "1.12.0", 
"minecraft:entity": { 
"description": { 
"identifier": "tutorial_demo:squirrel", 
"is_experimental": false, 
"is_spawnable": true, 
"is_summonable": true 
}, 
"component_groups": { 
"tutorial_demo:color_red": { 
"minecraft:behavior.delayed_attack": { 
"priority": 4, 
"reach_multiplier": 1.5,

          "attack_duration": 0.75,
          "hit_delay_pct": 0.25,
          "track_target": true,
          "sound_event": "attack.strong"
        },
        "minecraft:variant": {
          "value": 0
        }
      },
      "tutorial_demo:color_gray": {
        "minecraft:variant": {
          "value": 1
        }
      },
      "tutorial_demo:escaping": {
        "minecraft:behavior.avoid_mob_type": {
          "priority": 3,
          "entity_types": [
            {
              "filters": {
                "test": "is_target",
                "subject": "other",
                "value": true
              },
              "max_dist": 6,
              "walk_speed_multiplier": 1,
              "sprint_speed_multiplier": 1.2
            }
          ]
        }
      }
    },
    "components": {
      // ...
      "minecraft:behavior.hurt_by_target": {
        "priority": 1
      },
      "minecraft:behavior.random_stroll": {
        "priority": 6,
        "xz_dist": 2,
        "y_dist": 1,
        "speed_multiplier": 0.8
      },
      "minecraft:behavior.random_look_around": {
        "priority": 9
      },
      "minecraft:behavior.look_at_player": {
        "priority": 11
      },
      // ...

      "minecraft:on_hurt": {
        "event": "tutorial_demo:escape_started",
        "filters":{
          "test": "is_variant",
          "value": 1
        },
        "target": "self"
      },
      "minecraft:on_hurt_by_player": {
        "event": "tutorial_demo:escape_started",
        "filters":{
          "test": "is_variant",
          "value": 1
        },
        "target": "self"
      },
      "minecraft:on_target_escape": {
        "event": "tutorial_demo:escape_ended",
        "target": "self"
      }
    },
    "events": {
      "minecraft:entity_spawned": {
        // ...
      },
      "tutorial_demo:escape_started": { 
// ... 
}, 
"tutorial_demo:escape_ended": { 
// ... 
} 
} 
} 
} 
``` 

In this way, we have achieved the behavior specialization of the red and gray squirrels. Let's enter the game to test our content. We can intuitively see the addition and deletion of component groups and the activation and deactivation of AI intentions through the computer development version of ImGui. 

![](./images/12.7_in-game_2.gif) 

In this way, we have fixed our anomaly. Below, we release all the contents of our behavior pack definition files so far for the reference of all developers: 

```json 
{ 
"format_version": "1.12.0", 
"minecraft:entity": { 
"description": { 
"identifier": "tutorial_demo:squirrel", 
"is_experimental": false, 
"is_spawnable": true,

      "is_summonable": true
    },
    "component_groups": {
      "tutorial_demo:color_red": {
        "minecraft:behavior.delayed_attack": {
          "priority": 4,
          "reach_multiplier": 1.5,
          "attack_duration": 0.75,
          "hit_delay_pct": 0.25,
          "track_target": true,
          "sound_event": "attack.strong"
        },
        "minecraft:variant": {
          "value": 0
        }
      },
      "tutorial_demo:color_gray": {
        "minecraft:variant": {
          "value": 1
        }
      },
      "tutorial_demo:escaping": {
        "minecraft:behavior.avoid_mob_type": {          "priority": 3,
          "entity_types": [
            {
              "filters": {
                "test": "is_target",
                "subject": "other",
                "value": true
              },
              "max_dist": 6,
              "walk_speed_multiplier": 1,
              "sprint_speed_multiplier": 1.2
            }
          ]
        }
      }
    },
    "components": {
      "minecraft:hurt_on_condition": {
        "damage_conditions": [{
          "filters": {
            "test": "in_lava",
            "subject": "self",
            "operator": "==",
            "value": true
          },
          "cause": "lava",
          "damage_per_tick": 4

        }]
      },
      "minecraft:pushable": {
        "is_pushable": true,
        "is_pushable_by_piston": true
      },
      "minecraft:experience_reward": {
        "on_death": "query.last_hit_by_player ? Math.Random(0,1) : 0"
      },
      "minecraft:breathable": {
        "total_supply": 15,
        "suffocate_time": 0
      },
      "minecraft:physics": {},
      "minecraft:navigation.walk": {
        "can_path_over_water": true,
        "avoid_water": true
      },
      "minecraft:movement.skip": {},
      "minecraft:jump.static": {},
      "minecraft:behavior.float": {        "priority": 0
      },
      "minecraft:behavior.hurt_by_target": {
        "priority": 1
      },
      "minecraft:behavior.random_stroll": {
        "priority": 6,
        "xz_dist": 2,
        "y_dist": 1,
        "speed_multiplier": 0.8
      },
      "minecraft:behavior.random_look_around": {
        "priority": 9
      },
      "minecraft:behavior.look_at_player": {
        "priority": 11
      },
      "minecraft:equipment": {
        "table": "loot_tables/entities/squirrel_equipment.json"
      },
      "minecraft:type_family": {
        "family":["squirrel", "mob"]
      },
      "minecraft:can_climb": {},
      "minecraft:collision_box": {
        "width": 0.7,
        "height": 0.7
      },
      "minecraft:attack": {

        "damage": 1.0
      },
      "minecraft:movement": {
        "value": 0.3
      },
      "minecraft:health": {
        "value": 30,
        "max": 30
      },
      "minecraft:on_hurt": {
        "event": "tutorial_demo:escape_started",
        "filters":{
          "test": "is_variant",
          "value": 1
        },
        "target": "self"
      },
      "minecraft:on_hurt_by_player": {
        "event": "tutorial_demo:escape_started",
        "filters":{
          "test": "is_variant",
          "value": 1
        },
        "target": "self"
      },
      "minecraft:on_target_escape": {
        "event": "tutorial_demo:escape_ended",
        "target": "self"
      }
    },
    "events": {
      "minecraft:entity_spawned": {
        "sequence": [
          {
            "randomize": [
              {
                "weight": 1,
                "add": {
                  "component_groups": [
                    "tutorial_demo:color_red"
                  ]
                }
              },
              {
                "weight": 1,
                "add": {
                  "component_groups": [
                    "tutorial_demo:color_gray"
                  ]
                }

              }
            ]
          }
        ]
      },
      "tutorial_demo:escape_started": {
        "add": {
          "component_groups": [
            "tutorial_demo:escaping"
          ]
        }
      },
      "tutorial_demo:escape_ended": {
        "remove": {
          "component_groups": [
            "tutorial_demo:escaping"
          ]
        }
      }
    }
  }
}
```