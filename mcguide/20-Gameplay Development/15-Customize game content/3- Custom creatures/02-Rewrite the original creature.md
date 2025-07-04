--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Rewrite the original creature 

We can rewrite the behavior and appearance of the original creature by customizing the same identifier as the original creature. 

Please read this document in conjunction with the example [CustomEntityMod](../../13-Module SDK Programming/60-Demo Example.md#CustomEntityMod). 

## 1. Rewrite the behavior of the creature 

As in the example [CustomEntityMod](../../13-Module SDK Programming/60-Demo Example.md#CustomEntityMod), add custom_pig.json under behavior_pack/entities, the identifier is still minecraft:pig, and then add the **creeper** attack components minecraft:nearest_attackable_target and minecraft:target_nearby_sensor, as well as the explosion event, so that it will attack the player and explode and disappear.

## 2. Rewrite the appearance of creatures 

There are two ways to rewrite the appearance of creatures: 

* **Rewrite the definition of the client entity (under resource_pack/entity) and change the method to pure json configuration** 

Just like rewriting the behavior of creatures, we can rewrite the appearance of creatures by rewriting the entity definition, texture, animation, model, rendering controller and other json files under the resource pack. For example, in the example [CustomEntityMod](../../13-Module SDK Programming/60-Demo Example.md#CustomEntityMod), the pig wears the butcher's texture. 

```json
  {
    "format_version": "1.10.0",
    "minecraft:client_entity": {
      "description": {
        "identifier": "minecraft:pig",
        "materials": { "default": "custom_entity" },
        "textures": {
          "default": "textures/entity/custom_pig", # Modify this texture
          "saddled": "textures/entity/custom_pig_saddle" # Modify this texture
        },
        "geometry": {
          "default": "geometry.pig"
        },
        "animations": {
          "setup": "animation.pig.setup.v1.0",
          "walk": "animation.quadruped.walk",
          "look_at_target": "animation.common.look_at_target",
          "baby_transform": "animation.pig.baby_transform"
        },
        "scripts": {
          "animate": [

            "setup",
            { "walk": "query.modified_move_speed" },
            "look_at_target",
            { "baby_transform": "query.is_baby" }
          ]
        },
        "render_controllers": [ "controller.render.custom_pig" ],
        "spawn_egg": {
          "texture": "spawn_egg",
          "texture_index": 2
        }
      }
    }
  }
  
  ```

  And add textures custom_pig.png and custom_pig_saddle.png in the textures/entity directory
  
  

## 3. About rewriting the player's client entity definition 

**Modifications to the player's client definition should be based on `data\resource_packs\vanilla_netease\entity\player.entity.json`, not vanilla or other original resource packs. ** 

When the engine supports player skins, the player's render_controllers will be hard-coded: 

1. Depending on whether the player uses a member skin with self-luminescence, remove controller.render.player.first_person_bloom and controller.render.player.third_person_bloom, or controller.render.player.first_person and controller.render.player.third_person. Because in order to be compatible with self-luminescence, please keep the above 4 render controllers at the same time. 

2. If the player uses a personalized combination, controller.render.persona_animated_face.third_person will be added. 

This can lead to situations when a developer wants to completely override the player's appearance, for example: 

```json 
{ 
"format_version": "1.10.0", 
"minecraft:client_entity": { 
"description": { 
"identifier": "minecraft:player", 
"materials": { 
"MC_default": "entity" 
}, 
"textures": { 
"MC_default": "textures/entity/penguin/penguin" 
}, 
"geometry": { 
"MC_default": "geometry.penguin" 
}, 
"animations": { 
...

}, 
"scripts": { 
... 
}, 
"render_controllers": [ "controller.render.penguin" ] 
} 
} 
} 
``` 

Then when the player uses a personalized match, there will be an extra render controller. 

To solve this problem, you can add the netease_override_persona attribute to the description. When this attribute is true, the engine will not make any changes to the player's render_controllers. For example:

   ```json
   {
     "format_version": "1.10.0",
     "minecraft:client_entity": {
       "description": {
         "identifier": "minecraft:player",
         "netease_override_persona": true,
         ...
         "render_controllers": [ "controller.render.penguin" ]
       }
     }
   }
   ```

   



