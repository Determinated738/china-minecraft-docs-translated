--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Status Effects 

### Overview 

This feature does not require experimental gameplay. 

Developers can add a netease_effects folder to the behavior_pack directory of the addon, and then configure a json file to add custom status effects. For details, please refer to the example [CustomEffectsMod](../13-Module SDK Programming/60-Demo Example.md#CustomEffectsMod) 

### Custom state effect Json 

First, add a netease_effects folder in the behavior pack behavior_pack directory, and add the Json configuration file of the custom state. The file name is not required. The Json file format is as follows: 

```json 
{ 
"format_version": "1.10", 
"minecraft:effect": { 
"description": { 
"identifier": "custom_effect:weightless" 
}, 
"components": { 
"minecraft:particle_color": [255, 255, 255], 
"minecraft:icon": "weightless" 
} 
} 
} 
``` 

The following is a description of some nodes: 

- `"minecraft:effect"`: This node is the outermost node of the custom state configuration table 
- `"description"`: This node is the description information of the custom state 
- `"identifier"`: This node is the name of the custom state, which is divided into namespace and state name. The namespace is recommended to be consistent with the mod name, and the identifier must be globally unique. This identifier is used to correspond to this custom state in other places in the mod. Note: The identifier must be **all lowercase**. If there are uppercase letters, it will be invalid when added to custom food 
- `"components"`: This node is a component related to the custom state 
- `"minecraft:particle_color"`: This node is the color of the particle effect on the player after adding the state. It uses RGB color mode, the data type is [int, int, int], and the value range of each int type is 0-255 
- `"minecraft:icon"`: This node is the name of the custom state icon, the data type is string 

Next, add the icon of the custom state under the resource pack resource_pack/textures/ui. Taking this Json configuration file as an example, the value of the `"minecraft:icon"` field is `"weightless"`, so the icon should be named `weightless_effect.png`. Note that the **icon path** and **name** here must be strictly followed, otherwise it will not take effect. 

Finally, add the following settings in the localization file texts/zh_CN.lang to localize the custom state name: 

``` 
minecraft:custom_effect=custom state 
``` 




### Add custom status to custom food 

Custom status can be added through the interface (see the effect component in the ModSDK document for details), or by configuring the Json file of the custom food. When the custom food is eaten, the corresponding custom status is obtained. The Json file format of a custom food is as follows: 

```Json 
{ 
"format_version": "1.10", 
"minecraft:item": { 
"description": { 
"identifier": "itemMod:testFood", 
"register_to_create_menu":true, 
"category":"Nature" 
}, 

"components": { 
"minecraft:use_duration": 32, 
"minecraft:max_stack_size": 64, 
"minecraft:food": { 
"nutrition": 100, 
"saturation_modifier": "supernatural", 
"can_always_eat":true, 
"effects": [ 
{ 
"name": "custom_effect:weightless", 
"chance": 1.0, 
"duration": 30, 
"amplifier": 4 
} 
] 
} 
} 
} 
} 
``` 

You only need to add the corresponding status information under the `"effects"` field. The meaning of each field is as follows: 

- `"name"`: Status name. If it is a custom status, it corresponds to the `"identifier"` of the custom status 

- `"chance"`: The probability of obtaining this status, with a value between 0 and 1 
- `"duration"`: Status effect duration, in seconds 
- `"amplifier"`: Status amplification factor. This value plus 1 is the status effect level 

For other related definitions of custom food, please refer to 3-9 Custom Item Document 

### Demo Explanation 


In 6-1DemoMod, we provide a DemoMod [CustomEffectsMod](../13-Module SDK Programming/60-Demo Example.md#CustomEffectsMod) for custom status effects. This mod mainly implements the following functions: 

- Defines a custom state - weightless: 
- custom_effect:weightless 
- Customizes the icon of this state (weightless_effect.png) and the example effect color (white) 
- Defines a custom food: 
- itemMod:testFood 
- Customizes the icon of this food 
- Eating this food can get a custom weightless state 
- Listens for events when adding and removing states in customEffectServer.py 
- If the added state is weightless, set the player's gravity to -0.03 
- If the removed state is weightless, reset the player's gravity to the default value 

In addition to customizing food to add custom states, we also provide the AddEffectToEntity interface to add a specified state to a specified entity, and the RemoveEffectFromEntity interface to remove a specified state from a specified entity. For detailed interface usage, please refer to <a href="../../../mcdocs/1-ModAPI/接口/对象/STATEFFECT.html" rel="noopenner"> Status Effect Interface </a>. 

When an entity obtains a status or a status is removed (whether it is removed actively by calling the RemoveEffectFromEntity interface or after the duration ends), the corresponding event will be triggered. Developers need to listen to the corresponding event to add or remove effect logic for the corresponding custom status. For details, please refer to: 

- <a href="../../../mcdocs/1-ModAPI/Event/Entity.html#addeffectserverevent" rel="noopenner"> Add Status Event-AddEffectServerEvent </a> 
- <a href="../../../mcdocs/1-ModAPI/Event/Entity.html#removeeffectserverevent" rel="noopenner"> Delete Status Event-RemoveEffectServerEvent </a> 
- <a href="../../../mcdocs/1-ModAPI/Event/Entity.html#refresheffectserverevent" rel="noopenner"> Update Status Event-RefreshEffectServerEvent </a> 

Note: Custom status cannot be obtained through the /effect command 

