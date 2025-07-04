--- 
sidebarDepth: 1 
--- 
# Rendering 

## AddPlayerAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add player rendering animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| animationKey | str | Animation key | 
| animationName | str | Animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerAnimation("move.arms", "animation.player.move.arms_custom") 
``` 

## AddPlayerAnimationController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add player rendering animation controller 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| animationControllerKey | str | Animation controller key | 
| animationControllerName | str | Animation controller name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerAnimationController("root", "controller.animation.player.root_custom") 
``` 

## AddPlayerAnimationIntoState 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add animation to the state in the player's animation controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| animationControllerName | str | Animation controller name, such as root (controller.animation.player.root) | 
| stateName | str | Animation state name, such as first_person | 
| animationName | str | Added animation name or animation controller name, such as first_person_attack_controller_new | 
| condition | str | Animation control expression, default is empty, such as query.mod.index > 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerAnimationIntoState("root", "first_person", "first_person_attack_controller_new", "query.mod.index > 0") 
``` 

## AddPlayerGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add player render geometry 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryKey | str | Render geometry key, such as player default geometry default | 
| geometryName | str | Rendering geometry name, such as the player's default geometry geometry.humanoid.custom | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- After calling this interface, you need to call RebuildPlayerRender to take effect 
Animation and textures are closely related to geometry. Changing geometry also requires changing animation and textures 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerGeometry("default", "geometry.player.custom") 
``` 

## AddPlayerParticleEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description


    Add player special effect resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effectKey | str | Special effect resource key, such as nectar_dripping in bee.entity.json | 
| effectName | str | Special effect resource name, such as minecraft:nectar_drip_particle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerParticleEffect("nectar_dripping", "minecraft:nectar_drip_particle") 
``` 

## AddPlayerRenderController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add player <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller">Rendering Controller</a> 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| renderControllerName | str | Rendering Controller Name | 
| condition | str | Rendering Controller Condition | 

- Return Value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Notes

- After calling this interface, you need to call RebuildPlayerRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerRenderController('custom_render_controller_name', 'query.mod.condition') 
``` 

## AddPlayerRenderMaterial 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add the <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_3-Custom Materials">Material</a> 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| materialKey | str | Material Key | 
| materialName | str | Material Name | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | Add Success | 

- Notes 
- RebuildPlayerRender needs to be called after calling this interface to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId)
comp.AddPlayerRenderMaterial('custom_material_key', 'custom_material_name')
```



## AddPlayerSoundEffect

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add player sound effect resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| soundKey | str | Sound effect resource Key | 
| soundName | str | Sound effect resource name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- Sound effects are defined in RP/entities/player.entity.json # minecraft:client_entity / description as follows: 
"sound_effects": { 
"sound_thunder": "ambient.weather.thunder" # ambient.weather.thunder is defined in sound_definitions 
} 
If you want to play audio synchronously with the action, you can define it in RP/animations/player.animation_controllers.json # animation_controllers / controller.animation.player.root as follows: 
"dripping": { 
"sound_effects": [ 
{ 
"effect": "sound_thunder" 
} 
], 
"transitions": [ 
{ 
"third_person": "!query.mod.is_powered" 
} 
] 
}, 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId)
comp.AddPlayerSoundEffect("sound_thunder", "ambient.weather.thunder")
```

## AddPlayerTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add player rendering texture 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| geometryKey | str | Texture key | 
| geometryName | str | Texture path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- After calling this interface, you need to call RebuildPlayerRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddPlayerTexture("default", "textures/misc/missing_texture") 
``` 

## RebuildPlayerRender 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Rebuild the player's data renderer 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the rebuild is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.RebuildPlayerRender() 
``` 

## RemovePlayerAnimationController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Remove the player rendering animation controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| animationControllKey | str | animation controller key | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.RemovePlayerAnimationController("root") 
``` 

## RemovePlayerGeometry 


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Delete player rendering geometry 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| geometryKey | str | Rendering geometry name key, such as player default geometry default | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- After calling this interface, you need to call RebuildPlayerRender to take effect 
Animation and textures are closely related to geometry. Changing geometry also requires changing animation and textures. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# geometry definition in player.entity.json 
"geometry": { 
"default": "geometry.humanoid.custom", 
"cape": "geometry.cape" 
} 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.RemovePlayerGeometry("default") 
``` 

## RemovePlayerRenderController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Delete player<a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller">Rendering Controller</a> 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| renderControllerName | str | Rendering controller name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- After calling this interface, you need to call RebuildPlayerRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.RemovePlayerRenderController('custom_render_controller_name') 
``` 

## SetPlayerItemInHandVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Set whether to hide the player's handheld item model display 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| visible | bool | Set whether to display or hide, True means display, False means hide | 
| mode | int | Sets the perspective mode in which hiding handheld items takes effect. When mode=0, it means that handheld items are hidden in both first-person and third-person perspectives; when mode=1, it means that only handheld items in third-person perspective are hidden; when mode=2, it means that only handheld items in first-person perspective are hidden. The default value is 0. Filling in values other than 0, 1, and 2 will be forced to 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether the setting is successful. Return True if successful, and False if failed. | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
# Hide the handheld item model display of the specified player 
print actorRenderComp.SetPlayerItemInHandVisible(False, 0) 
``` 

## SetSkin 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Replace the original custom skin 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| skin | str | Texture path, with textures\models as the relative path of the current path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Will overwrite the original skin (including 4d skin). But it will be overwritten by the skeleton model 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetSkin("kagura") 
``` 

