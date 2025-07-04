--- 
sidebarDepth: 1 
--- 
# Rendering 

## AddActorAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add creature rendering animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Entity identifier | 
| animationKey | str | Animation key | 
| animationName | str | Animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.AddActorAnimation("minecraft:pig", "custom_move", "animation.pig.custom_move") 
``` 

## AddActorAnimationController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add creature rendering animation controller 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actorIdentifier | str | Mob identifier | 
| animationControllerKey | str | Animation controller key | 
| animationControllerName | str | Animation controller name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(entityId) 
comp.AddActorAnimationController("minecraft:skeleton", "controller__use_item_progress", "controller.animation.humanoid.use_item_progress") 
``` 

## AddActorBlockGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add a block geometry model to the entity. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 
| offset | tuple(float,float,float) | The position offset value of the block geometry model relative to the entity, optional parameter, default is (0, 0, 0). | 
| rotation | tuple(float,float,float) | The rotation angle of the block geometry model relative to the entity, optional parameter, default is (0, 0, 0), representing the rotation angle around the x, y, and z axes respectively, and the rotation order is z, x, y. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful, True is returned if successful, and False is returned if failed. If the entity already has a model with the same name, True is also returned | 

- Notes 
- Please make sure that the world has been initialized (for example, listen to the UiInitFinished event) before calling this interface, otherwise calling it too early will cause the interface execution to fail. 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId) 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
# Combine blocks and convert to a block geometry model named "my_block_geometry" 
geometryName = blockGeometryComp.CombineBlockFromPosListToGeometry([(200,64,200),(201,65,202)],"my_block_geometry") 
# Add to entity with entity id -4294967295 
print actorRenderComp.AddActorBlockGeometry(geometryName) 
``` 

## AddActorGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add creature rendering geometry 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Creature entity identifier | 
| geometryKey | str | Rendering geometry key, such as default | 
| geometryName | str | Rendering geometry name, such as panda geometry geometry.panda | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- After calling this interface, you need to call RebuildActorRender to take effect. 
Animation and texture are closely related to geometry. Changing geometry also requires changing animation and texture. It is recommended to modify the creature's animation and animation controller before modifying the creature's geometry. 
- Some creatures are affected by the initial animation, and the geometry will have an initial offset, which will cause abnormal performance after modifying the geometry. If the modified geometry does not have the bones required by the current animation, an error will be triggered. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.AddActorGeometry("minecraft:sheep", "default", "geometry.panda") 
```




## AddActorParticleEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add creature special effect resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actorIdentifier | str | Entity identifier | 
| effectKey | str | Special effect resource key, such as nectar_dripping in bee.entity.json | 
| effectName | str | Special effect resource name, such as minecraft:nectar_drip_particle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.AddActorParticleEffect("minecraft:villager", "nectar_dripping", "minecraft:nectar_drip_particle") 
``` 

## AddActorRenderController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add creature [rendering controller](/mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| actorIdentifier | str | creature identifier | 
| renderControllerName | str | render controller name | 
| condition | str | render controller condition. When this condition is met, the render controller pointed to by renderControllerName will take effect | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Notes 
- After calling this interface, you need to call RebuildActorRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.AddActorRenderController('minecraft:villager', 'custom_render_controller_name', 'query.mod.condition') 
``` 

## AddActorRenderControllerArray 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add dictionary arrays elements to the list of creature render controllers 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actorIdentifier | str | Entity identifier | 
| renderControllerName | str | Entity creature render controller name | 
| arrayType | int | Render controller arrays type ([render controller arrays type enumeration](../../enumeration value/RenderControllerArrayType.md)) | 
| arrayName | str | Array name | 
| expression | str | Expression of element to be added | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 


- Notes 
- This interface adds elements in render_controller->arrays—>materials/textures/geometries->array.*** 
- After calling this interface, you need to call RebuildActorRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(entityId) 
comp.AddActorRenderControllerArray("minecraft:pig", "controller.render.pig", clientApi.GetMinecraftEnum().RenderControllerArrayType.Texture, "Array.skins", "Texture.test") 
``` 

## AddActorRenderMaterial 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Adds [materials] required for creature rendering (/mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_3-Custom Materials) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Creature identifier | 
| materialKey | str | Material key | 
| materialName | str | Material name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Add successfully | 

- Notes 
- After calling this interface, you need to call RebuildActorRender to make it take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(playerId) 
comp.AddActorRenderMaterial('minecraft:villager', 'custom_material_key', 'custom_material_name') 
``` 




## AddActorScriptAnimate 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Adds an animation/animation controller to the scripts/animate node in the client entity definition (minecraft:client_entity) json of the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actorIdentifier | str | Entity identifier | 
| animateName | str | Animation/animation controller name, such as look_at_target | 
| condition | str | Animation/animation controller control expression, default is empty, such as query.mod.index > 0 | 
| autoReplace | bool | Whether to overwrite an existing animation/animation controller, default value is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- For existing creatures, you need to pass the creature ID when calling CreateActorRender to make it take effect immediately. For non-existent creatures, just pass the levelId. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateActorRender(entityId)
comp.AddActorAnimationController("minecraft:pig", "animation_controller_short_name", "controller.animation.pig.custom_animation_controller")
comp.AddActorScriptAnimate("minecraft:pig", "animation_controller_short_name", "query.mod.index > 0")
```



## AddActorSoundEffect

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient

- describe

    Added biological sound effects resources

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Entity identifier | 
| soundKey | str | Sound resource key | 
| soundName | str | Sound resource name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- Currently, only sound effects can be played in animations, not in animation controllers. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.AddActorSoundEffect("minecraft:villager", "sound_thunder", "ambient.weather.thunder") 
``` 

## AddActorTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Add creature rendering texture 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actorIdentifier | str | Creature entity identifier | 
| textureKey | str | texture key | 
| texturePath | str | texture path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not |


- Notes 
- After calling this interface, you need to call RebuildActorRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.AddActorTexture("minecraft:sheep", "default", "textures/entity/panda/panda") 
``` 

## BindEntityToEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Bind the skeletal model to follow other entities, and the camera also follows other entities 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| bindEntityId | str | Bind to follow entity ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | False means failure, True means success | 

- Notes 
- This interface only implements visual effects. In essence, the entity is still in place, so you need to call the interface to set the entity's position to the position of other entities, otherwise it will not be rendered when the entity itself is not within the camera range. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Bind the entity of entityId to the entity of bindEntityId 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.BindEntityToEntity(bindEntityId) 
``` 



## ClearActorBlockGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Delete all block geometry models in the entity. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful, return True if successful, return False if failed. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId) 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
# Combine blocks and convert to a block geometry model named "my_block_geometry" 
geometryName = blockGeometryComp.CombineBlockFromPosListToGeometry([(200,64,200),(201,65,202)],"my_block_geometry") 
# Add to entity with id -4294967295 
print actorRenderComp.AddActorBlockGeometry(geometryName) 
# Clear all block geometries in the entity 
print actorRenderComp.ClearActorBlockGeometry() 
``` 

## DeleteActorBlockGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Delete the specified block geometry model in the entity. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful, True is returned if successful, False is returned if failed. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId) 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
# Combine blocks and convert to a block geometry model named "my_block_geometry" 
geometryName = blockGeometryComp.CombineBlockFromPosListToGeometry([(200,64,200),(201,65,202)],"my_block_geometry") 
# Add to entity with id -4294967295 
print actorRenderComp.AddActorBlockGeometry(geometryName) 
# Delete the block geometry just added 
print actorRenderComp.DeleteActorBlockGeometry(geometryName) 
``` 

## GetNotRenderAtAll 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Get whether the entity is not rendered 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means not rendered | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(entityId) 
notRender = comp.GetNotRenderAtAll()

``` 

## RebuildActorRender 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Rebuild the creature's data renderer (this interface does not support players, players should use RebuildPlayerRender) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Entity identifier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the reconstruction is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.RebuildActorRender('minecraft:villager') 
``` 

## RemoveActorAnimationController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Remove the creature rendering animation controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| actorIdentifier | str | The identifier of the creature | 
| animationControllKey | str | The animation controller key. Note that this value needs to be prefixed with "controller__" in the animation controller key in json | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(entityId) 
comp.RemoveActorAnimationController("minecraft:villager", "controller__use_item_progress") 
``` 

## RemoveActorGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Delete creature rendering geometry 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Creature entity identifier | 
| geometryKey | str | Rendering geometry name, such as panda geometry.panda | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- After calling this interface, you need to call RebuildActorRender to take effect 
Animation and textures are closely related to geometry. Changing geometry also requires changing animation and textures 

- Example 

```python 
import mod.client.extraClientApi as clientApi

# geometry definition in panda.entity.json 
# "geometry": { 
# "default": "geometry.panda" 
# }, 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.RemoveActorGeometry("minecraft:panda", "default") 
``` 

## RemoveActorRenderController 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Remove creature [rendering controller](/mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller) 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| actorIdentifier | str | creature identifier | 
| renderControllerName | str | rendering controller name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- After calling this interface, you need to call RebuildActorRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
comp.RemoveActorRenderController('minecraft:villager', 'custom_render_controller_name') 
``` 

## RemoveActorTexture 

<span style="display:inline;color:#7575f9">Client</span> 


method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Deletes the creature rendering texture 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| actorIdentifier | str | Creature entity identifier | 
| textureKey | str | Texture key, such as default | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- After calling this interface, you need to call RebuildActorRender to take effect 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# texture definition in panda.entity.json 
# "textures": {
# "default": "textures/entity/panda/panda",
# "lazy": "textures/entity/panda/panda_lazy",
# "worried": "textures/entity/panda/panda_worried",
# "playful": "textures/entity/panda/panda_playful",
# "brown": "textures/entity/panda/panda_brown",
# "weak": "textures/entity/panda/panda_sneezy",
# "aggressive": "textures/entity/panda/panda_aggressive"
# }
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId)
comp.RemoveActorTexture("minecraft:panda", "default")
```



## ResetBindEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 


Cancel the binding entity of the target entity. After cancellation, no other entities will follow. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | False means failure, True means success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ResetBindEntity() 
``` 

## SetActorAllBlockGeometryVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Sets whether all the cube geometry models in the entity are displayed. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| visible | bool | Sets whether to display or hide, True means display, False means hide | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Sets whether to succeed, returns True if successful, returns False if failed. |

- Example

```python
import mod.client.extraClientApi as clientApi
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId)
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295")

# Combine blocks and convert them to a block geometry model named "my_block_geometry" 
geometryName = blockGeometryComp.CombineBlockFromPosListToGeometry([(200,64,200),(201,65,202)],"my_block_geometry") 
# Add to entity with id -4294967295 
print actorRenderComp.AddActorBlockGeometry(geometryName) 
# Hide all block geometry 
print actorRenderComp.SetActorAllBlockGeometryVisible(False) 
``` 

## SetActorBlockGeometryVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Sets whether the specified block geometry model in the entity is displayed. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 
| visible | bool | Sets whether to display or hide, True means display, False means hide | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Sets whether to succeed, returns True if successful, and returns False if failed. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId) 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
# Combine blocks and convert to a block geometry model named "my_block_geometry" 
geometryName = blockGeometryComp.CombineBlockFromPosListToGeometry([(200,64,200),(201,65,202)],"my_block_geometry") 
# Add to entity with id -4294967295 
print actorRenderComp.AddActorBlockGeometry(geometryName) 
# Hide the block geometry just added 
print actorRenderComp.SetActorBlockGeometryVisible(geometryName, False) 
``` 

## SetAlwaysShowName


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.nameCompClient.NameComponentClient 

- Description 

Sets whether the creature's name is always displayed, even when the aiming point is not pointing at the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| show | bool | True for display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Notes 
- This interface is only valid for ordinary creatures and does not work for player settings 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateName(entityId) 
# Do not display the name above the head 
comp.SetAlwaysShowName(False) 
``` 
## SetColor 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.healthCompClient.HealthComponentClient 

- Description 

Set the color and background color of the health bar 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| front | tuple(float,float,float,float) | RGBA value of the health bar color, range 0-1 |

| back | tuple(float,float,float,float) | RGBA value of background color, range 0-1 | 

- Return value 

None 

- Notes 
- Health bar can only be displayed when ShowHealthBar is set with game component! ! 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateHealth(entityId) 
comp.SetColor((0, 0, 0, 1), (1, 1, 1, 1)) 
``` 

## SetHealthBarDeviation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.healthCompClient.HealthComponentClient 

- Description 

Set the relative height of an entity's health bar 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| health_bar_deviation | float | Relative height of health bar | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The health bar can only be displayed when ShowHealthBar is set with the game component; the health bar is 1.5 meters above the creature AABB by default 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateHealth(entityId) 
# Set the relative height of the health bar

comp.SetHealthBarDeviation(1.0) 
``` 

## SetNameDeeptest 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Set whether the name is perspective 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| deeptest | bool | True means no perspective. Perspective by default | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
# Set to non-perspective 
comp.SetNameDeeptest(True) 
``` 

## SetNotRenderAtAll 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Set whether to turn off entity rendering 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| notRender | bool | True means not to render the entity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Do not render a single entity entityId 
comp = clientApi.GetEngineCompFactory().CreateActorRender(entityId) 
comp.SetNotRenderAtAll(True) 
# Restart rendering the entity 
comp.SetNotRenderAtAll(False) 
``` 

## SetRenderLocalPlayer 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Set whether the local player is rendered 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| render | bool | True is rendering | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId)

# Do not render local players 
comp.SetRenderLocalPlayer(False) 
``` 
## SetShowName 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.nameCompClient.NameComponentClient 
- Description 
Set whether the creature name is displayed according to the default game logic 
- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| show | bool | True for display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Return whether the setting is successful | 

- Notes 
- When set to True, the name display of the creature follows the default rendering logic of the game, that is, the name of ordinary creatures needs to be pointed to by the center point, while the name of the player will always be displayed. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateName(entityId) 
# Do not display the name above the head 
comp.SetShowName(False) 
``` 

## ShowHealth 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.healthCompClient.HealthComponentClient 

- Description 


Set whether to display the health bar of an entity. The default is to display. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| show | bool | Set whether to display | 

- Return value 

None 

- Notes 
- The health bar can only be displayed when the game component is set to ShowHealthBar! ! 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateHealth(entityId) 
# Set this entity not to display the health bar 
comp.ShowHealth(False) 
``` 

## ShowHealthBar 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Set whether to display the health bar 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| show | bool | True means display. After enabling, you can use the health component to set the color of an entity's health bar and whether to display it | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateGame(levelId)
comp.ShowHealthBar(True)
```