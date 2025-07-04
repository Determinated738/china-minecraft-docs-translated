--- 
front: 
hard: Advanced 
time: 15 minutes 
--- 

# Creature definition file 

#### Author: Boundary 

Creature resource definition is done in the client. In this type of file, developers can define the texture, animation, model, sound effect, particle short name of the creature, and control the animation playback timing when necessary. This type of file is called a mob definition file. It is located in RP/entity and has a .json suffix. 

``` 
{ 
"format_version":"1.10.0", 
"minecraft:client_entity":{ 
"description":{ 
"identifier":"minecraft:pig", 
"materials":{ 
"default":"pig" 
}, 
"textures":{ 
"default":"textures/entity/pig/pig", 
"saddled":"textures/entity/pig/pig_saddle" 
}, 
"geometry":{ 
"default":"geometry.pig" 
}, 
"animations":{ 
"setup":"animation.pig.setup.v1.0", 
"walk":"animation.quadruped.walk", 
                "look_at_target":"animation.common.look_at_target",
                "baby_transform":"animation.pig.baby_transform"
            },
            "scripts":{
                "animate":[
                    "setup",
                    {
                        "walk":"query.modified_move_speed"
                    },
                    "look_at_target",
                    {
                        "baby_transform":"query.is_baby"
                    }
                ]
            },

"render_controllers":[ 
"controller.render.pig" 
], 
"spawn_egg":{ 
"texture":"spawn_egg", 
"texture_index":2 
} 
} 
} 
} 
``` 

#### format_version 

format_version refers to the version number of the definition content. Currently, there are two options: 1.8.0 and 1.10.0. 1.8.0 and 1.10.0 are two major changes in the implementation of the custom creature function. The custom creature function was first implemented in Bedrock Edition 1.8.0, and in the 1.10.0 version, Bedrock Edition once again reorganized the writing format of custom creatures. In general, the latest 1.10.0 format is used, which is the general standard for custom creatures now. 

#### identifier 

identifier means the identifier of the creature. It consists of a namespace and a name. When using the /summon command in the game to summon entities, the original creatures that start with minecraft: can be directly summoned by their names. Custom creatures need to add a namespace before their names to help the game distinguish, for example: two components have added a duck creature named duck, and distinguishing which component they come from is the job of the namespace. 

#### material 

Material means material, which controls the presentation of entities. Some creatures in the game have luminous and transparent texture parts, and the material of the map texture needs to be specified to work properly. 

#### texture 

Texture means map texture, which controls the texture of the entity. For example, the wood texture of wood, the feathers on a chicken, etc. 

#### geometry 

Geometry means model geometry. It controls what the entity looks like. 

#### animations 

Animations means animations, and a series of animation resources and animation controllers that control the timing of animation playback will be placed here. 



#### scripts/animate 

scripts/animate means playing the root animation. Animation or animation controller will be placed here. 

#### render_controller 

render_controller means rendering controller. It is a method for developers to define how to render creatures. Through the rendering controller, you can set the geometry, material, texture, and part hiding and display of the creature. Note: The words such as geometry, material, and texture here represent the key information needed to render the creature. For example, the original pig needs to show two forms, and display the texture with or without saddle according to the state of saddle or unsaddle. You can switch in the rendering controller, and define the entry by the developer, and then point to the complete resource path in the creature definition file. 

#### particle_effects 

particle_effects means particle effects. A series of particle resources that need to be used will be placed here. Developers can use original particles or custom particles. 

#### sound_effects 

sound_effects means sound effects. A series of sound effect resources that need to be used will be placed here. Developers can use original sound effects or custom sound effects. 

#### spawn_egg 

spawn_egg means creature egg, which is a way to summon creatures in my world. Developers can define the texture resources referenced by creature eggs. 

#### enable_attachable 

enable_attachable means to display the wearable items on the body. This attribute is available on players and some wither creatures.