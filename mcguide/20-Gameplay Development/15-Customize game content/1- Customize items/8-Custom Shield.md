--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Shield 

## Overview 

This is a special custom item. In addition to supporting all the features of custom items, it also has shield-related functions and supports custom shield animations and models. 

## Registration 

1. Same as steps 1-6 of registering a custom basic item 

**The item name (the part after the colon in identifier) cannot be called shield, otherwise it will conflict with the original shield!! ** 

1. If the icon in resource is empty, the item form of the shield will be rendered as a model (using the default model and default texture rendering, no action will be played) 

If the texture icon is configured, the item form is rendered as a texture 

```python 
{ 
"minecraft:item": { 
"description": { 
"identifier": "customshield:test_shield" 
}, 
"components": { 
"minecraft:icon": "" 
} 
}, 
"format_version": "1.10" 
} 
``` 

1. Add weapon/tool related definitions to the json of behavior/netease_items_beh, including: 

custom_item_type is shield 

A netease:shield component, required. For component parameters, see [json component](#json component) 

```python 
{ 
"minecraft:item": { 
"description": { 
"category": "Custom", 
"identifier": "customshield:test_shield",

"custom_item_type": "shield", 
"register_to_create_menu": true 
}, 
"components": { 
"netease:shield":{ 
"defence_damage_source_list":["drowning"],//Defense damage type, if not configured or empty, use native blocking damage logic 
"undefence_damage_source_list":["entity_attack"],//Undefended damage type, cannot have the same elements as the above, if there are the same, prioritize defense of this damage type 
"is_consume_damage":false//Whether to consume durability, false does not consume 
} 
} 
}, 
"format_version": "1.10" 
} 
``` 

1. Add a json file in resource/netease_item_res, such as: 

```python 
{ 
"minecraft:item": { 
"description": { 
"identifier": "customshield:test_shield" 
}, 
"components": { 
"minecraft:icon": "shield" 
} 
}, 
"format_version": "1.10" 
} 
``` 

1. Add a json file to resource/attachables, such as: 

```python 
{ 
"format_version": "1.10.0", 
"minecraft:attachable": { 
"description": { 
"identifier": "customshield:test_shield", 
"materials": { 
"default": "entity_alphatest", 
"enchanted": "entity_alphatest_glint" 
}, 
"textures": { 
"default": "textures/entity/test_shield", //Model surface texture 
"enchanted": "textures/misc/enchanted_item_glint"
            },
            "geometry": {
              "default": "geometry.test_shield" //Model
            },

"animations": { 
//We provide a general animation controller, which is located in vanilla_netease/animation_controllers/shield.animation_controllers.json 
"wield": "controller.animation.default_custom_shield.wield", 
//The normal shield holding state uses custom actions 
//You can also reuse the original actions animation.shield.xxx 
"wield_main_hand_first_person": "animation.test_shield.wield_main_hand_first_person", 
"wield_off_hand_first_person": "animation.test_shield.wield_off_hand_first_person", 
"wield_third_person": "animation.test_shield.wield_third_person", 

// If the defense state action reuses the original action, the shield animation part will be invalid when the shield is raised 
// "wield_main_hand_first_person_block": "animation.shield.wield_main_hand_first_person_blocking", 
// "wield_off_hand_first_person_block": "animation.shield.wield_off_hand_first_person_blocking" 

// In order to make the shield animation work properly when the shield is raised, the defense state action uses a custom action 
"wield_main_hand_first_person_block": "animation.test_shield.wield_main_hand_first_person_blocking", 
"wield_off_hand_first_person_block": "animation.test_shield.wield_off_hand_first_person_blocking" 

}, 
"scripts": { 
"animate": [ 
"wield" 
], 
// If you reuse the original action, you need to have the following value definition 
"initialize": [ 
"variable.main_hand_first_person_pos_x = 5.3;", 
"variable.main_hand_first_person_pos_y = 26.0;", 
"variable.main_hand_first_person_pos_z = 0.4;", 
"variable.main_hand_first_person_rot_x = 91.0;", 
"variable.main_hand_first_person_rot_y = 65.0;", 
"variable.main_hand_first_person_rot_z = -43.0;", 
"variable.off_hand_first_person_pos_x = -13.5;", 
"variable.off_hand_first_person_pos_y = -5.8;", 
"variable.off_hand_first_person_pos_z = 5.1;", 
                "variable.off_hand_first_person_with_bow_pos_z = -25.0;",
                "variable.off_hand_first_person_rot_x = 1.0;",
                "variable.off_hand_first_person_rot_y = 176.0;",
                "variable.off_hand_first_person_rot_z = -2.5;"
              ],
               // Movement correction when using bow
              "pre_animation": [
                "variable.is_using_bow = (query.get_equipped_item_name == 'bow') && (query.main_hand_item_use_duration > 0.0f);"
              ]
            },
            "render_controllers": [ "controller.render.item_default" ]
          }
        }
    }
    ```

1. Customize your own shield model in resource/models/entity

1. Place custom actions and action controllers in resource/animations and resource/animation_controllers (if any) 

1. Bind the player's animation controller in python. At the same time, the operation of binding the animation controller to the player is completed in the callback function of a new event. 
The event name is <a href="../../../../mcdocs/1-ModAPI/事件/世界.html#addplayercreatedclientevent">"AddPlayerCreatedClientEvent"</a>. When this event is triggered, a playerId parameter will be passed. This event triggering indicates that the player's rendering related resources have been loaded. 

```python 
animaComp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
# Add the player's action when the shield is activated 
# animationKey needs to be unique 
# animationName reuses the original 
# If you need to use custom actions, you can also refer to player.animation.json to write new actions 
animaComp.AddPlayerAnimation("shield_block_main_hand_test", "animation.player.shield_block_main_hand") 
animaComp.AddPlayerAnimation("shield_block_off_hand_test", "animation.player.shield_block_off_hand") 
# blocking state, and the left hand is not the original shield and the custom shield, and the main hand is our custom shield 
animaComp.AddPlayerAnimationIntoState("root", "third_person", "shield_block_main_hand_test", "query.blocking && query.get_equipped_item_name('off_hand') != 'shield' && !query.get_equipped_item_is_netease_shield('off_hand') && query.get_equipped_item_full_name == 'customshield:test_shield'") 
# blocking state, and the left hand is our custom shield 
animaComp.AddPlayerAnimationIntoState("root", "third_person", "shield_block_off_hand_test", "query.blocking && query.get_equipped_item_full_name('off_hand') == 'customshield:test_shield'") 
``` 

## Molang expression 

### Add molang expression 
- query.get_equipped_item_is_netease_shield 

* Description 

Get whether the main hand/off-hand has a custom shield (the original shield does not count) 

* Parameters: 

| key | type | default value | explanation | 
| -------- | ---- | --------- | ---------------------------------------------- | 
| hand | str | 'main_hand' | Get whether the main hand (main_hand)/off-hand ('off_hand') is a shield | 

* Return value: 

| description | 
| ---- | 
| Whether the main hand (main_hand)/off-hand ('off_hand') is a NetEase custom shield | 

- query.get_equipped_item_full_name 

* Description 

Get the identifier of the main hand/off-hand item, only used for custom items, please use query.get_equipped_item_name for original items. 

* Parameters: 


| Key | Type | Default | Explanation | 
| -------- | ---- | --------- | ---------------------------------------------- | 
| hand | str | 'main_hand' | Get whether the main hand (main_hand)/off hand ('off_hand') is a shield | 

* Return value: 

| Description | 
| ---- | 
| The identifier of the main hand/off hand item | 



### Original molang expression 

* c.item_slot 
The location of this item 
**Return value:** 
| Description | 
| ---- | 
| "main_hand": main hand; "off_hand": off hand; "head": head; "torso": torso | 

* q.item_slot_to_bone_name 
**Return value:** 
| Description | 
| ---- | 
| "rightitem": main hand; "leftitem": off-hand; | 

## JSON component 

### NetEase components 

* netease:shield 

| Key | Type | Default value | Explanation | 
| -------- | ---- | --------- | ---------------------------------------------- | 
| defence_damage_source_list | list | [] | Defense damage type. If not configured or empty, the original blocking damage logic will be used. Temporarily does not support defense against fire (fire_tick), suicide (suicide), wither (wither) damage | 
| undefence_damage_source_list | list | [] | Undefended damage type, cannot have the same elements as the above, if there is a same, prioritize defense against that damage type | 
| is_consume_damage | bool | true | Whether to consume durability, false does not consume | 

### Original components 

* minecraft:icon 

Texture name 

* minecraft:attachable 

The main key of minecraft:attachable is description, the value of description is introduced below


| key | type | default | explanation | 
| ---------- | ---- | ------ | ---------------------------------------------------- | 
| identifier | str | | shield id | 
| textures | dict | | "default": default surface texture; "enchanted": enchanted surface texture | 
| geometry | dict | | "default": item model | 
| animations | dict | | item animation controller and animation related, reference example explanation | 
| scripts | dict | | "animate": [item animation controller name], reference example | 
| materials | dict | | "default": default surface texture; "enchanted": enchanted surface texture, reference example | 
| render_controllers | list | | reference example | 

## New events and interfaces 

### Events 
* <a href="../../../../mcdocs/1-ModAPI/Event/Item.html#onplayerblockedbyshieldbeforeserverevent">OnPlayerBlockedByShieldBeforeServerEvent</a> 

Triggered before the player uses a shield to block damage 

* <a href="../../../../mcdocs/1-ModAPI/Event/Item.html#onplayerblockedbyshieldafterserverevent">OnPlayerBlockedByShieldAfterServerEvent</a> 

Triggered after the player uses a shield to block damage 

* <a href="../../../../mcdocs/1-ModAPI/Event/Item.html#onplayeractiveshieldserverevent">OnPlayerActiveShieldServerEvent</a> 

Event triggered by the player activating/deactivating the shield 

### Interface 

* <a href="../../../../mcdocs/1-ModAPI/接口/件.html#getitemdefenceangle">GetItemDefenceAngle</a> 

Server-side interface. Get the defense angle range of the shield item 

* <a href="../../../../mcdocs/1-ModAPI/接口/件.html#setitemdefenceangle">SetItemDefenceAngle</a> 

Server-side interface. Set the defense angle range of the shield item, refer to the explanation of the defense angle range below 

* <a href="../../../../mcdocs/1-ModAPI/接口/玩家/行为.html#setusingshield">setUsingShield</a> 

Client-side interface. Set whether to activate the shield 

* <a href="../../../../mcdocs/1-ModAPI/接口/玩家/行为.html#getisblocking">GetIsBlocking</a> 

Server-side interface. Get whether the player is in a blocking state, that is, whether the shield is activated 





## Add item dictionary parameters 

**Defense range** 
| Key | Type | Default value | Explanation | 
| -------- | ---- | ------ | ---------------------- | 
| shieldDefenceAngleLeft | float | -90 | The left range, the default is -90, the value range is [-180,180] | 
| shieldDefenceAngleRight | float | 90 | The right range, the default is 90, the value range is [-180,180], and shieldDefenceAngleLeft<shieldDefenceAngleRight | 

```python 
itemDict1 = { 
'itemName': 'customshield:test_shield', 
'count': 1, 
'shieldDefenceAngleLeft':-45, 
'shieldDefenceAngleRight':30 
} 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SpawnItemToPlayerInv(itemDict1, playerId) 
``` 
### Explanation of the defense range 

As shown in the diagram, if a shield has a defense range of [-45°, 30°], i.e. shieldDefenceAngleLeft=-45, shieldDefenceAngleRight=30, then when the player raises the shield, if the source of damage is an entity, then the damage within the range of -45° to 30° in front of the player can be blocked, otherwise it cannot be blocked. Note: The original shield range is [-90°, 90°] 

![Schematic diagram](./picture/customitem/shield1.png) 

## demo explanation 

[CustomShieldItemMod](../../13-Module SDK Programming/60-Demo Example.md#CustomShieldItemMod) defines a custom shield: 

* customshield:test_shield 

Custom shield 
