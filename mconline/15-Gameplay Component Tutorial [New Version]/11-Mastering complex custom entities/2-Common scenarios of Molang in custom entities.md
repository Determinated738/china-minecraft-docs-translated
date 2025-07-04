--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 10 minutes 
--- 
# Common scenarios for Molang in custom entities 

Molang is used everywhere in the add-on pack, but if you want to talk about the most frequently used scenario, it is custom entities. In this section, let's learn about the application of Molang in custom entities. 

## Control entity rendering 

In Chapter 8, we learned about the rendering controller of the entity. In the rendering controller of the entity, we can use Molang to control the geometry, material, and texture selection of the entity. Generally speaking, there are two common control methods. The first is to use an array, and the second is to use the ternary conditional operator `?:`. 

```json 
"geometry": "array.crossbow_geo_frames[query.get_animation_frame]", 
"materials": [ 
{ "*": "variable.is_enchanted ? material.enchanted : material.default" } 
], 
"textures": [ 
"array.crossbow_texture_frames[query.get_animation_frame]", 
"texture.enchanted" 
] 
``` 

In the above example, we can see that both geometry and texture use arrays, and the corresponding geometry and texture are obtained by using the value of the query.get_animation_frame as the array index. The material uses a ternary conditional operator, and the value of the variable variable.is_enchanted is used to determine whether to use the enchanted material or the default material. 

## Participate in animation expressiveness 

We have learned before that Molang expressions can also be used in animation to control the value of a channel of a bone. For example, the moving animation of the teal we previously showed. 

```json 
"animation.teal.move": { 
"loop": true, 
"anim_time_update": "query.modified_distance_moved", 
"bones": { 
"leg0": { 
"rotation": ["math.cos(query.anim_time*38.17)*80.0", 0, 0] 
}, 
"leg1": { 
"rotation": ["math.cos(query.anim_time*38.17)*-80.0", 0, 0] 
} 
} 
} 
``` 

We can see that $\mathrm{cos}(query.anim\_time \times38.17)\times80.0$ and $\mathrm{cos}(query.anim\_time\times38.17)\times-80.0$ respectively control the rotation angles of `leg0` and `leg1` in the $yOz$ plane. `query.anim_time` is the playback time of the current animation, and the default unit is seconds (s). However, we use the `anim_time_update` field here to change the animation time flow speed, so the movement speed is used to control the animation flow rate. And it should be noted that trigonometric mathematical functions such as `math.cos` only accept angle values as input and output the corresponding trigonometric function values. 

## Combining behavior with animation 


We can combine animations and behaviors by calling some Molang variables in animations. When an entity's behavior pack component defines the AI intention of attack, we can access a correct `variable.attack_time` variable in its animation, which represents its attack time for non-player entities. When the entity does not attack, it returns `0.0`. For players, it returns a percentage of the attack animation completed, ranging from `0.0` to `1.0`. 

Let's take the zombie's bare-hand attack animation as an example: 

```json 
"animation.zombie.attack_bare_hand" : { 
"loop" : true, 
"bones" : { 
"leftarm" : { 
"rotation" : [ "-90.0 - ((math.sin(variable.attack_time * 180.0) * 57.3) * 1.2 - (math.sin((1.0 - (1.0 - variable.attack_time) * (1.0 - variable.attack_time)) * 180.0) * 57.3) * 0.4) - (math.sin(query.life_time * 76.776372) * 2.865) - this", "5.73 - ((math.sin(variable.attack_time * 180.0) * 57.3) * 0.6) - this", "math.cos(query.life_time * 103.13244) * -2.865 - 2.865 - this" ]
    },
    "rightarm" : {
      "rotation" : [ "90.0 * (variable.is_brandishing_spear - 1.0) - ((math.sin(variable.attack_time * 180.0) * 57.3) * 1.2 - (math.sin((1.0 - (1.0 - variable.attack_time) * (1.0 - variable.attack_time)) * 180.0) * 57.3) * 0.4) + (math.sin(query.life_time * 76.776372) * 2.865) - this", "(math.sin(variable.attack_time * 180.0) * 57.3) * 0.6 - 5.73 - this", "math.cos(query.life_time * 103.13244) * 2.865 + 2.865 - this" ] 
} 
} 
}, 
``` 

You can see that `variable.attack_time` is passed into the components of the rotation channel as a variable similar to the query function. 

## Behavior Pack Entity Components and Events 

Some components and events are often defined in the behavior pack definition file of the entity. Molang can be used to control the calculation of related variables in the component and the triggering of events. For example, almost all entities define an experience reward component to calculate the dropped experience value. 

```json 
"minecraft:experience_reward": { 
"on_bred": "Math.Random(1,7)", 
"on_death": "query.last_hit_by_player?Math.Random(1,3):0" 
} 
``` 

## Linking with Module SDK 

In the module SDK, you can use the `queryVariable` engine component to register a custom query function. For example, the following code can register a `query.mod.is_custom_material` query in the client. 

```python 
import mod.client.extraClientApi as clientApi 
compFactory = clientApi.GetEngineCompFactory() 
# Register a custom material switching query function 
comp = compFactory.CreateQueryVariable(clientApi.GetLevelId()) 
result = comp.Register('query.mod.is_custom_material', 0.0) 
# Change the value of the query function 
comp.Set('query.mod.is_custom_material', 1.0) 
``` 

After that, we can use `query.mod.is_custom_material` in the animation controller to control the material of the entity, and the value of `query.mod.is_custom_material` can be controlled by the Python script, so as to achieve script-enabled resource control.