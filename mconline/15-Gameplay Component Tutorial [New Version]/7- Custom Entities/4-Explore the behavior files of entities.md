--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 30 minutes 
--- 
# Explore the behavior file of the entity 

In this section, we will explore the behavior file of the entity. For an entity, there is often only one server definition file in the behavior pack that defines it. Therefore, we focus on this **server definition file**. 

Let's take the complete server definition file of our custom teal entity as an example: 

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
        "avoid_damage_blocks": true
      },
      "minecraft:movement.basic": {},
      "minecraft:jump.static": {},      "minecraft:can_climb": {},
      "minecraft:despawn": {
        "despawn_from_distance": {}
      },
      "minecraft:behavior.float": {
        "priority": 0
      },
      "minecraft:behavior.panic": {
        "priority": 1,
        "speed_multiplier": 1.5
      },
      "minecraft:behavior.mount_pathing": {
        "priority": 2,
        "speed_multiplier": 1.5,
        "target_dist": 0,
        "track_target": true
      },
      "minecraft:behavior.tempt": {
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
    "component_groups": {
      "minecraft:teal_baby": {
        "minecraft:is_baby": {},
        "minecraft:scale": {
          "value": 0.5        },
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
            }
          },
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

- `format_version`: The entity's behavior definition file has undergone multiple iterations and currently has multiple format versions, namely `1.8.0`, `1.10.0`, `1.11.0`, `1.12.0`, `1.13.0`, `1.14.0`, `1.16.0` and `1.16.100`. We still recommend using the latest `1.16.0` or `1.16.100`. 
- `minecraft:entity`: The schema identifier of the server-side entity. This identifier must be used as the key name in the server-side entity definition file. It usually contains `description`, `components`, `component_groups` and `events` objects. 

## Understanding the description information of entity behavior 

The entity's **Description** (**Description**) is the entity's `description` object. Let's take a look at the properties in the description of the entity server definition file one by one. The following is an excerpt from the above file.

```json 
"description": { 
"identifier": "tutorial_demo:teal", 
"runtime_identifier": "minecraft:chicken", 
"is_spawnable": true, 
"is_summonable": true, 
"is_experimental": false 
} 
``` 

- `identifier`: string, the namespaced identifier of the entity, which must be consistent with the identifier in the client definition file. 
- `runtime_identifier`: optional, string, the **Runtime Identifier** (**Runtime Identifier**, abbreviated as **Runtime ID**) of the entity. The runtime identifier can only be filled with a vanilla entity. When this identifier exists, your custom entity will be created based on the vanilla entity. In other words, your entity will inherit from this vanilla entity. All entity members, flags, and hard-coded behaviors will be implemented on your custom entity. For example, undead mobs have behaviors such as losing health when using potions to heal, gaining health when taking damage, and taking more damage from the Smite spell. If you also want your entity to have this behavior, you can set the runtime identifier to `minecraft:zombie` or `minecraft:skeleton` to inherit this behavior. 
- `is_spawnable`: Optional, Boolean value, controls whether the entity can be spawned by a spawn egg or naturally spawned. 
- `is_summonable`: Optional, Boolean value, controls whether the entity can be summoned by the `/summon` command. 
- `is_experimental`: Optional, Boolean value, controls whether the entity is an experimental entity. Experimental entities will only be defined and appear in the world when experimental gameplay is turned on.

- `animations`: optional, object, server-side animation or animation controller of the entity. Server-side entities can also attach animations or animation controllers, and this is where the server attaches animations or animation controllers. The server-side animation or animation controller of the entity is mainly used to control "command animations" rather than the model animation of the entity. 
- `scripts`: optional, object, server-side Molang expression pseudo-script. Similarly, the `animate` array under it is used to conditionally control the playback of animations or animation controllers. 

## Understanding the three functions of entity behavior 

In addition to the description of the entity, we can see that there are three objects in the entity definition: `components`, `component_groups`, and `events`. They represent the three functions of entity behavior, namely **Component**, **Component Group**, and **Event**. 

### Components 

```json 
"components": { 
"minecraft:type_family": { // First component 
"family": ["chicken", "mob"] 
}, 
"minecraft:breathable": { // Second component 
"total_supply": 15, 
"suffocate_time": 0 
}, 
"minecraft:collision_box": { // Third component 
"width": 0.6, 
"height": 0.8 
}, 
"minecraft:nameable": {}, // Fourth component 
"minecraft:health": { // Fifth component 
"value": 4, 
"max": 4 
}, 
// ... 
} 
``` 

In the previous entity configuration section, we have already learned about entity components. Entity components are the direct definition of various behaviors of entities. Components defined in the entity's `components` object will take effect as soon as the entity appears in the world, performing their respective functions, such as features, navigation, and AI intentions. 

We can add and modify components through the editor of the Minecraft Development Workbench, or refer to the [add-on package entity documentation hosted on bedrock.dev](https://bedrock.dev/zh/b/Entities) to modify components by directly modifying the JSON file. These two solutions are equivalent. 

The components of an entity are the top priority for giving the entity a soul, and they are also the most comprehensive and content-rich functions. Developers need to study them carefully with the help of the editor or through the documentation. 

### Component groups 

```json 
"component_groups": { 
"minecraft:teal_baby": { // First group 
"minecraft:is_baby": {}, // First component in the first group 
"minecraft:scale": { // Second component in the first group 
"value": 0.5 
}, 
"minecraft:ageable": { // Third component in the first group 
"duration": 1200, 
"feed_items": ["wheat_seeds", "beetroot_seeds", "melon_seeds", "pumpkin_seeds"], 
"grow_up": {

"event": "minecraft:ageable_grow_up", 
"target": "self" 
} 
}, 
"minecraft:behavior.follow_parent": { // Fourth component in the first group 
"priority": 5, 
"speed_multiplier": 1.1 
} 
}, 
"minecraft:teal_adult": { // Second group 
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
        }
      },
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
      }    },
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
} 
``` 

A component group is a "package" of components. Each component group consists of an object. The key value of the component group is the identifier of the component group, and the content of the component group is composed of individual components. Component groups are created to dynamically and flexibly add and remove components from entities. For example, in the above example, we have two component groups, minecraft:teal_baby and minecraft:teal_adult. We can use the events to be introduced later to "package" the components in the minecraft:teal_baby component group into the entity's active component when the entity is in the baby state, and then when the entity is in the adult state, the components in the minecraft:teal_baby component group are "packaged" out, and the components in the minecraft:teal_adult component group are "packaged" into the active component. 

In other words, the components in the component group will not take effect instantly after the entity enters the game. These components will only take effect if the component group is added to the entity's active component list. When they are removed, they will become invalid again. This allows for dynamic addition and deletion of entity components. 

We can see the `minecraft:scale` component in the `minecraft:teal_baby` component group. This component represents the scale of the entire entity. You should remember that we saw the animation of the teal entity in its juvenile state in the previous section. The teal's head will double in size in its juvenile state. Here we can see that the entire teal will shrink to 0.5 times its original size. So the overall effect is that the teal's head size remains unchanged, while its body size shrinks by half. This is why all the young entities we see in Minecraft generally have a "big head and small body" appearance. And this "big head and small body" is actually in line with common sense. After all, the size of an animal's skull generally does not change with age. By using component groups flexibly and coordinating with other functions such as animation, our entities can be made more realistic or have other functions you envision. 

## event

```json
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
  },  "minecraft:ageable_grow_up": {
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
``` 

An entity's event is a property used to trigger specific functions in certain situations. Events can be triggered by components, animations or animation controllers, or by other events or even other events of other entities. Some events are built-in events that can be triggered by hard-coded parts. 

Events are generally used to add and remove component groups, and sometimes they can also be used to trigger other events. We can see that the following excerpts `from_egg` event and `minecraft:spawn_adult` event can each add a component group to the list of active components. 

```json 
"from_egg": { 
"add": { 
"component_groups": ["minecraft:teal_baby"] 
} 
} 
``` 

```json 
"minecraft:spawn_adult": { 
"add": { 
"component_groups": ["minecraft:teal_adult"] 
} 
} 
``` 

The following `minecraft:ageable_grow_up` can add and remove a component group at the same time. 

```json 
"minecraft:ageable_grow_up": { 
"remove": { 
"component_groups": ["minecraft:teal_baby"] 
}, 
"add": { 
"component_groups": ["minecraft:teal_adult"] 
} 
} 
``` 

Most events are triggered by a component. For example, we can find a `minecraft:ageable` component in the `minecraft:teal_baby` component group of an entity. It can be used to trigger the `minecraft:ageable_grow_up` event after the entity reaches a certain age, and the `minecraft:ageable_grow_up` event can remove the `minecraft:teal_baby` component group and add the `minecraft:teal_adult` component group. This means that the baby teal will grow into an adult teal. ```

```json
"minecraft:teal_baby": {
  // ...
  "minecraft:ageable": {
    "duration": 1200,
    "feed_items": ["wheat_seeds", "beetroot_seeds", "melon_seeds", "pumpkin_seeds"],

"grow_up": { 
"event": "minecraft:ageable_grow_up", 
"target": "self" 
} 
}, 
// ... 
} 
``` 

Some components can be triggered by entity animations and animation controllers. These animations and animation controllers must be defined in the behavior pack and need to be directly used in the format of `@s <namespace>:<event_identifier>` in `on_entry` or `on_exit`. 

Some components are triggered by other components, such as the `minecraft:entity_spawned` event has a 95% chance of triggering the `minecraft:spawn_adult` event, and a 5% chance of adding a `minecraft:teal_baby` component group. This is achieved using `randomize`. 

```json 
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
} 
``` 

Some are **Built-in Event**. Built-in events are triggered in game-specific internal code, and entities only need to define these events. These events do not need to be triggered manually by the player. For example, the above `minecraft:entity_spawned` and `minecraft:entity_born` are two internal events, which are triggered when the entity is spawned by a spawn egg/naturally spawned and when the entity is born by its parents. Of course, this does not mean that players cannot trigger them manually, and players can still add other triggers for these events according to their wishes. 

Of course, there are some special events, such as the `from_egg` event mentioned above. This event is a hard-coded event and will only take effect when the entity's runtime ID is `minecraft:chicken`. This will make it possible to spawn the entity when the thrown egg is broken. 

Reasonable use of events can make your entity more mobile, allowing you to better enrich and improve its functions. 
