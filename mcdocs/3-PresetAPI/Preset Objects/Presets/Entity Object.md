--- 
sidebarDepth: 1 
--- 
# Entity Object 

## Overview 

- Inheritance Relationship 

```mermaid 
classDiagram 
SdkInterface <|-- EntityObject 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html" 
EntityObject: Entity Object 
SdkInterface: SDK Interface Encapsulation 
SdkInterface: (Click to Jump) 
``` 

- Description 

EntityObject is the base class that encapsulates entity objects and provides object-oriented usage for entities. 

- Member variables 

None 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetPos](#getpos) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity's position | 
| [GetFootPos](#getfootpos) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity's foot position | 
| [SetPos](#setpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's position | 
| [SetFootPos](#setfootpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's foot position | 
| [GetRot](#getrot) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity's angle | 
| [SetRot](#setrot) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the entity's head angle | 
| [GetEngineTypeStr](#getenginetypestr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity type name | 
| [GetEngineType](#getenginetype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity type | 
| [GetModelId](#getmodelid) | <span style="display:inline;color:#7575f9">Client</span> | Get the id of the skeleton model, mainly used for special effects binding skeleton model | 
| [PlayAnim](#playanim) | <span style="display:inline;color:#7575f9">Client</span> | Play skeleton animation | 
| [SetAnimSpeed](#setanimspeed) | <span style="display:inline;color:#7575f9">Client</span> | Set the playback speed of a skeleton animation | 
| [GetAnimLength](#getanimlength) | <span style="display:inline;color:#7575f9">Client</span> | Get the length of a skeleton animation in seconds | 
| [SetBrightness](#setbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Set the brightness of the entity | 
| [SetOpacity](#setopacity) | <span style="display:inline;color:#7575f9">Client</span> | Set the transparency of the creature model | 
| [GetHealth](#gethealth) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity's preset health value | 
| [SetHealth](#sethealth) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's preset health value |

| [GetMaxHealth](#getmaxhealth) | <span style="display:inline;color:#ff5555">Server</span> | Get the preset maximum health of the entity | 
| [SetMaxHealth](#setmaxhealth) | <span style="display:inline;color:#ff5555">Server</span> | Set the preset maximum health of the entity | 
| [GetSpeed](#getspeed) | <span style="display:inline;color:#ff5555">Server</span> | Get the preset speed of the entity | 
| [SetSpeed](#setspeed) | <span style="display:inline;color:#ff5555">Server</span> | Set the preset speed of the entity | 
| [GetMaxSpeed](#getmaxspeed) | <span style="display:inline;color:#ff5555">Server</span> | Get the preset maximum speed of the entity | 
| [SetMaxSpeed](#setmaxspeed) | <span style="display:inline;color:#ff5555">Server</span> | Sets the preset maximum speed of the entity | 
| [GetDamage](#getdamage) | <span style="display:inline;color:#ff5555">Server</span> | Gets the preset damage of the entity | 
| [SetDamage](#setdamage) | <span style="display:inline;color:#ff5555">Server</span> | Sets the preset damage of the entity | 
| [GetMaxDamage](#getmaxdamage) | <span style="display:inline;color:#ff5555">Server</span> | Gets the preset maximum damage of the entity | 
| [SetMaxDamage](#setmaxdamage) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum damage of the entity preset | 
| [ShowHealth](#showhealth) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to display the health bar, the default is to display | 
| [SetAttackTarget](#setattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Set the aggro target | 
| [ResetAttackTarget](#resetattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Clear the aggro target | 
| [GetAttackTarget](#getattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Get the aggro target | 
| [SetKnockback](#setknockback) | <span style="display:inline;color:#ff5555">Server</span> | Set the initial speed of the knockback, considering the influence of resistance | 
| [SetOwner](#setowner) | <span style="display:inline;color:#ff5555">Server</span> | Set the owner of the entity | 
| [GetOwner](#getowner) | <span style="display:inline;color:#ff5555">Server</span> | Get the owner of the entity | 
| [IsOnFire](#isonfire) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the entity is on fire | 
| [SetOnFire](#setonfire) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity on fire | 
| [GetAttrValue](#getattrvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get attribute values, including health, hunger, and speed | 
| [GetAttrMaxValue](#getattrmaxvalue) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the maximum value of the attribute, including health, hunger, and speed | 
| [SetAttrValue](#setattrvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set attribute values, including health, hunger, and speed | 
| [SetAttrMaxValue](#setattrmaxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum value of attributes, including health, hunger, and movement speed | 
| [IsInLava](#isinlava) | <span style="display:inline;color:#7575f9">Client</span> | Whether the entity is in lava | 
| [IsOnGround](#isonground) | <span style="display:inline;color:#7575f9">Client</span> | Whether the entity is touching the ground | 
| [GetAuxValue](#getauxvalue) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the additional value of the shot arrow or thrown potion | 
| [GetCurrentAirSupply](#getcurrentairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Current oxygen reserve value of organisms | 
| [GetMaxAirSupply](#getmaxairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum oxygen reserve value of organisms | 
| [SetCurrentAirSupply](#setcurrentairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Set the oxygen reserve value of organisms | 
| [SetMaxAirSupply](#setmaxairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum oxygen reserve value of organisms | 
| [IsConsumingAirSupply](#isconsumingairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the creature is currently consuming oxygen | 
| [SetRecoverTotalAirSupplyTime](#setrecovertotalairsupplytime) | <span style="display:inline;color:#ff5555">Server</span> | Set the time to restore the maximum amount of oxygen, in seconds | 
| [GetSourceId](#getsourceid) | <span style="display:inline;color:#ff5555">Server</span> | Get the projectile launcher entity id | 
| [SetCollisionBoxSize](#setcollisionboxsize) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's bounding box | 
| [GetCollisionBoxSize](#getcollisionboxsize) | style="display:inline;color:#ff5555">Server</span> | Get the bounding box of the entity | 
| [SetBlockControlAi](#setblockcontrolai) | <span style="display:inline;color:#ff5555">Server</span> | Set the native AI of the shielded creature | 
| [GetDimensionId](#getdimensionid) | <span style="display:inline;color:#ff5555">Server</span> | Get the dimension where the entity is located | 
| [ChangeDimension](#changedimension) | <span style="display:inline;color:#ff5555">Server</span> | Teleport the entity | 
| [RemoveEffect](#removeeffect) | <span style="display:inline;color:#ff5555">Server</span> | Remove the specified status effect for the entity | 
| [AddEffect](#addeffect) | <span style="display:inline;color:#ff5555">Server</span> | Adds a specified status effect to the entity. If the added status already exists, the following situations will occur: 1. If the level is greater than the existing one, update the status level and duration; 2. If the status levels are equal and the remaining duration is greater than the existing one, refresh the remaining time; 3. If the level is less than the existing one, do not modify it; 4. The particle effect is based on the new one. | 
| [GetEffects](#geteffects) | <span style="display:inline;color:#ff5555">Server</span> | Get all current status effects of the entity | 
| [TriggerCustomEvent](#triggercustomevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger a custom event for the creature | 
| [IsAlive](#isalive) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Determine whether a biological entity is alive or a non-biological entity exists | 
| [GetGravity](#getgravity) | <span style="display:inline;color:#ff5555">Server</span> | Get the gravity factor of the entity. When the gravity factor of the biological entity is 0, the gravity factor of the world is applied | 
| [SetGravity](#setgravity) | <span style="display:inline;color:#ff5555">Server</span> | Set the gravity factor of the entity. When the gravity factor of the biological entity is 0, the gravity factor of the world is applied | 
| [SetHurt](#sethurt) | <span style="display:inline;color:#ff5555">Server</span> | Cause damage to the entity | 
| [SetImmuneDamage](#setimmunedamage) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is immune to damage (this attribute is archived) | 
| [SetModAttr](#setmodattr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set attribute value | 
| [GetModAttr](#getmodattr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get attribute value | 
| [RegisterModAttrUpdateFunc](#registermodattrupdatefunc) | <span style="display:inline;color:#7575f9">Client</span> | Register the callback function when the attribute value changes. The function will be called when the attribute changes |

| [UnRegisterModAttrUpdateFunc](#unregistermodattrupdatefunc) | <span style="display:inline;color:#7575f9">Client</span> | Callback function when unregistering attribute value changes | 
| [GetName](#getname) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom name of the creature, that is, the name set by the name tag or SetName interface | 
| [SetName](#setname) | <span style="display:inline;color:#ff5555">Server</span> | Used to set the custom name of the creature, which has the same function as the original name tag. Players and new wandering traders do not support it yet | 
| [SetShowName](#setshowname) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the creature name is displayed according to the default game logic | 
| [SetAlwaysShowName](#setalwaysshowname) | <span style="display:inline;color:#7575f9">Client</span> | Sets whether the creature's name is always displayed, even when the aiming point is not pointing at the creature | 
| [SetPersistence](#setpersistence) | <span style="display:inline;color:#ff5555">Server</span> | Sets whether the entity is saved | 
| [SetMotion](#setmotion) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Sets the instantaneous movement direction vector of the creature. The server can only be used for non-players, and the client can only be used for local players | 
| [GetMotion](#getmotion) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the instantaneous moving direction vector of the creature (including the player) | 
| [SetItem](#setitem) | <span style="display:inline;color:#ff5555">Server</span> | Set the creature's item | 
| [SetCanOtherPlayerRide](#setcanotherplayerride) | <span style="display:inline;color:#ff5555">Server</span> | Set whether other players have the right to ride | 
| [SetControl](#setcontrol) | <span style="display:inline;color:#ff5555">Server</span> | Set the creature to be able to walk and jump without equipping a saddle | 
| [SetRidePos](#setridepos) | <span style="display:inline;color:#ff5555">Server</span> | Set the creature's riding position | 
| [SetNotRender](#setnotrender) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to turn off entity rendering | 
| [SetCollidable](#setcollidable) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the entity is collidable | 
| [SetHealthColor](#sethealthcolor) | <span style="display:inline;color:#7575f9">Client</span> | Set the color and background color of the health bar. The health bar can only be displayed when ShowHealthBar is set using the game component! ! | 
| [AddAnimation](#addanimation) | <span style="display:inline;color:#7575f9">Client</span> | Add creature rendering animation | 
| [AddAnimationController](#addanimationcontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add creature rendering animation controller | 
| [AddScriptAnimate](#addscriptanimate) | <span style="display:inline;color:#7575f9">Client</span> | Add animation/animation controller to the scripts/animate node in the creature's client entity definition (minecraft:client_entity) json | 
| [AddParticleEffect](#addparticleeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add creature special effect resources | 
| [AddRenderController](#addrendercontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add biological rendering controller | 
| [AddRenderMaterial](#addrendermaterial) | <span style="display:inline;color:#7575f9">Client</span> | Add materials required for biological rendering. After calling this interface, you need to call RebuildActorRender to take effect | 
| [AddSoundEffect](#addsoundeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add biological sound effect resources | 
| [SetPushable](#setpushable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity can be pushed | 
| [SetModel](#setmodel) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the skeleton model | 
| [GetLavaSpeed](#getlavaspeed) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity's preset movement speed in the lava | 
| [SetLavaSpeed](#setlavaspeed) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's preset movement speed in the lava | 
| [GetMaxLavaSpeed](#getmaxlavaspeed) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum movement speed in the entity's preset lava | 
| [SetMaxLavaSpeed](#setmaxlavaspeed) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum speed of the entity in the preset lava | 

## GetPos 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the entity position 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| tuple(float,float,float) | Position information | 

- Notes 
- For non-players, the position of the sole of the foot is obtained 
- For players, if they are walking, standing, swimming, sneaking, or gliding, the position obtained is 1.62 higher than the sole of the foot; if they are sleeping, the position obtained is 0.2 higher than the lowest position 

## GetFootPos 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the position of the entity's foot 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Position information | 

## SetPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the entity position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | xyz value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Set result | 

- Notes 
- The behavior is the same as using the tp command, the entity will teleport to the target point 
- For all types of entities, the foot position is set, which is equivalent to [SetFootPos](#setfootpos) 
- Calling this interface on the bed will return False 

- Example 

```python 
self.SetPos((1,2,3)) 
``` 

## SetFootPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the position of the entity's foot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | The location of the entity's feet | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The behavior is consistent with using the tp command, and the entity will teleport to the target point 
- Calling this interface while in bed will return False 

- Example 

```python 
self.SetFootPos((0, 4, 0)) 
``` 

## GetRot


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the entity angle 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | (upper and lower angles, left and right angles) The unit is angle instead of radians | 

## SetRot 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the angle of the entity's head 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| rot | tuple(float,float) | Pitch angle and angle around the vertical direction, the unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- It is recommended to only set local players. If other creatures are set, they will be overwritten by the creature's own behavior. 

- Example 

```python 
# Set to look up 45 degrees and face the positive direction of the world z axis

self.SetRot((-45, 0)) 
``` 

## GetEngineTypeStr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the type name of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity type name, such as minecraft:husk | 

- Example 

```python 
entity = self.GetEntityObject(entityId) 
engineType = entity.GetEngineTypeStr() 
``` 

## GetEngineType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get entity type 

- Parameters 

None 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | For details, see <a href="../../../1-ModAPI/Enumeration value/EntityType.html">EntityType enumeration</a> | 

- Example 

```python 
entity = self.GetEntityObject(entityId) 
# Take the example of judging whether it is a Mob. If you want to judge whether it is a projectile, find the corresponding type Projectile and modify it. 
if entity.GetEngineType() & self.GetMinecraftEnum().EntityType.Mob == self.GetMinecraftEnum().EntityType.Mob: 
logger.info("{} is Mod".format(self.GetEngineTypeStr(entityId))) 
``` 

## GetModelId 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the ID of the skeleton model, mainly used for binding the skeleton model with special effects 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The id of the current skeleton model instance | 

## PlayAnim 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Play skeleton animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| aniName | str | Animation name | 
| isLoop | bool | Whether to loop | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.PlayAnim("run", True) 
``` 

## SetAnimSpeed 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the playback speed of a skeletal animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| aniName | str | Skeletal animation name | 
| speed | float | Speed multiplier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# run action triple speed 
self.SetAnimSpeed("run", 3.0) 
``` 



## GetAnimLength 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the length of a skeletal animation in seconds 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| aniName | str | Skeletal animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Skeletal animation length | 

- Example 

```python 
# Get the length of the run animation 
animLength = self.GetAnimLength('run') 
``` 

## SetBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the brightness of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| brightness | float | 0: Pure black<br>1: Normal brightness<br>1-14: Brighter or even pure white<br>More than 14: Usually pure white, even if the value changes, there is no obvious change | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | True: Setting successful False: Setting failed | 

- Notes 
- Currently only supports modifying the brightness of entities that have replaced the skeleton model, and entities using the game's native model are not supported. 

- Example 

```python 
success = self.SetBrightness(0.5) 
``` 

## SetOpacity 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the transparency of the biological model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| opacity | float | Transparency value, the range is [0, 1], the smaller the value, the more transparent | 

- Return value 

None 

- Example 

```python 
self.SetOpacity(0.2) 
``` 

## GetHealth 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 


Get the preset health value of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Health value | 

## SetHealth 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the preset health value of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| hp | float | Health value | 

- Return value 

None 

## GetMaxHealth 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the maximum health value of the entity preset 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Health value | 

## SetMaxHealth 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the preset maximum health value of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| hp | float | Health value | 

- Return value 

None 

## GetSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the speed of the entity preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Speed | 




## SetSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the preset speed of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| speed | float | Speed | 

- Return value 

None 

## GetMaxSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the preset maximum speed of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Speed | 

## SetMaxSpeed 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the maximum speed of the entity preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| speed | float | Speed | 

- Return value 

None 

## GetDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the damage of the entity preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Damage | 

## SetDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the entity preset damage 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| hp | float | damage | 

- Return value 

None 

## GetMaxDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the maximum damage of the entity preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | damage | 

## SetMaxDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the maximum damage of the entity preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| damage | float | damage | 


- Return value 

None 

## ShowHealth 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether to display the health bar, the default is to display 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| show | bool | Set whether to display | 

- Return value 

None 

- Remarks 
- ShowHealthBar must be set first 

- Example 

```python 
# Set the entity not to display the health bar 
self.ShowHealth(False) 
``` 

## SetAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the target of hatred 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetId | str | Target entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetAttackTarget(targetId) 
``` 

## ResetAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Clear the target of hatred 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.ResetAttackTarget() 
``` 

## GetAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the target of aggro 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity id of the target of aggro | 

- Example 

```python 
self.GetAttackTarget() 
``` 

## SetKnockback 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the initial speed of the knockback, taking into account the influence of resistance 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| xd | float | x-axis direction, used to control the angle | 
| zd | float | z-axis direction, used to control the angle | 
| power | float | used to control the initial velocity in the horizontal direction | 
| height | float | initial velocity in the vertical direction | 
| heightCap | float | upward velocity threshold, this value needs to be considered when the entity itself already has an upward velocity, to ensure that the final upward velocity does not exceed heightCap | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None | No return value | 


- Example 

```python 
self.SetKnockback(0.1, 0.1, 1.0, 1.0, 1.0) 
``` 

## SetOwner 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the owner of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ownerId | str | Owner entity id, set the entity owner to null when None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True means the setting is successful | 

- Example 

```python 
result = self.SetOwner(ownerId) 
``` 

## GetOwner 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the owner of the entity 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity owner id | 

- Example 

```python 
ownerId = self.GetOwner() 
``` 

## IsOnFire 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get whether the entity is on fire 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is on fire | 

- Example

```python
isOnFire = self.IsEntityOnFire(entityId)
```



## SetOnFire

<span style="display:inline;color:#ff5555">Server</span>

method in Preset.Model.Entity.EntityObject.EntityObject

- Description 

Set the entity to catch fire 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| seconds | int | Ignition time (in seconds) | 
| burn_damage | int | HP lost per second when on fire. If not passed, the default value is 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting was successful | 

- Notes 
- Will not take effect in water or rain. Ignition time is affected by the creature's equipment and the creature's status. The value range of burn_damage is 0~1000. If it is less than 0, it will be 0, and if it is greater than 1000, it will be 1000. 

- Example 

```python 
self.SetEntityOnFire(entityId, 1, 2) 
``` 

## GetAttrValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get attribute values, including health, hunger, and movement speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration Value/AttrType.html">AttrType Enumeration</a> | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| float | Attribute Result | 


- Example 

```python 
self.GetAttrValue(self.GetMinecraftEnum().AttrType.HEALTH) 
``` 

## GetAttrMaxValue 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the maximum value of attributes, including health, hunger, and movement speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration Value/AttrType.html">AttrType Enumeration</a> | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| float | Attribute Value Result | 

- Example 

```python 
self.GetAttrMaxValue(self.GetMinecraftEnum().AttrType.HEALTH) 
``` 

## SetAttrValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set attribute values, including health, hunger, and movement speed 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration value/AttrType.html">AttrType enumeration</a> | 
| value | float | Attribute value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- Setting interface does not support ABSORPTION 

- Example 

```python 
self.SetAttrValue(self.GetMinecraftEnum().AttrType.HEALTH, 20) 
``` 

## SetAttrMaxValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the maximum value of attributes, including health, hunger, and speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration value/AttrType.html">AttrType enumeration</a> | 
| value | float | Attribute value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- The maximum saturation you set cannot exceed the current hunger value; after eating food, the maximum saturation will be modified by the original game mechanism 
- The setting interface does not currently support ABSORPTION 

- Example


```python 
self.SetAttrMaxValue(serverApi.GetMinecraftEnum().AttrType.SPEED, 0.2) 
``` 

## IsInLava 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Whether the entity is in lava 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it is in lava, True means it is in lava, False means it is not in lava | 

- Notes 
- Only the entity loaded by the local client can be obtained whether it is in the magma. If the entity is in other dimensions or not loaded (too far away from the local player), the acquisition will fail. 

## IsOnGround 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Whether the entity touches the ground 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether it touches the ground, True means it touches the ground, False means it does not touch the ground | 

- Notes 
- When the client entity is just created, the engine calculation is not completed. At this time, getting whether the entity touches the ground will return the default value True. You need to delay one frame to get the correct data 
- When the creature is in a riding state, such as a player riding a pig, it is also considered to be touching the ground 
- Only the entities loaded by the local client can be obtained. If the entity is in another dimension or not loaded (too far away from the local player), the acquisition will fail 

## GetAuxValue 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the additional value of the shot arrow or thrown potion 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | auxValue | 

- Example 

```python 
self.GetAuxValue() 
``` 

## GetCurrentAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Current oxygen reserve value of organism 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current oxygen reserve value of the organism | 

- Remarks 
- Note: This value returns the number of logical frames supported by the current oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

## GetMaxAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the maximum oxygen reserve value of the organism 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Maximum oxygen reserve value | 

- Notes 
- Note: This value returns the number of logical frames supported by the maximum oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

## SetCurrentAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the biological oxygen reserve value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| data | int | Set the current oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Note: This value sets the number of logical frames supported by the current oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
self.SetCurrentAirSupply(300) 
``` 

## SetMaxAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the maximum oxygen reserve value of the organism 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| data | int | Set the maximum oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Remarks 
- Note: This value sets the maximum number of logical frames supported by the oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
self.SetMaxAirSupply(400) 
```




## IsConsumingAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get whether the organism is currently consuming oxygen 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether oxygen is consumed | 

## SetRecoverTotalAirSupplyTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the time to restore the maximum oxygen amount, in seconds 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| timeSec | float | Restore the maximum oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note: When the set maximum oxygen value is less than (timeSec*10), the value of the oxygen restored by the organism per frame is 0 


- Example 

```python 
self.SetRecoverTotalAirSupplyTime(10) 
``` 

## GetSourceId 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the projectile launcher entity id 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Projectile launcher entity id | 

## SetCollisionBoxSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the bounding box of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| size | tuple(float,float) | The first digit indicates the width and length, and the second digit indicates the height | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Set result | 

- Notes 
- For newly generated entities, the bounding box size will take effect only after 5 frames have passed 

- Example 

```python 
self.SetCollisionBoxSize((2,3)) 
``` 

## GetCollisionBoxSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the bounding box of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Bounding box size | 

## SetBlockControlAi 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set to block the native AI of creatures 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isBlock | bool | Whether to keep AI, False means blocking |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- After AI is blocked, the creature cannot move, is not affected by gravity, and cannot be pushed. But it can be damaged and can be interacted with by players (for example, horses can be ridden or villagers can be traded) 

- Example 

```python 
self.SetBlockControlAi(False) 
``` 

## GetDimensionId 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the dimension where the entity is 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Dimension id, 0-Main world; 1-Nether; 2-The End; or other custom dimensions | 

- Example 

```python 
self.GetDimensionId() 
``` 

## ChangeDimension 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Teleport entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension id, 0-Main world; 1-Nether; 2-The End; or other custom dimensions | 
| pos | tuple(int,int,int) | Coordinates of the teleportation. If None is entered, the portal of the target dimension is selected as the destination first, and then the dimension coordinate mapping logic is used to determine the destination | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.ChangeDimension(0, (0,4,0)) 
``` 

## RemoveEffect 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Delete the specified status effect for the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| effectName | str | Status effect name string, including custom status effects and original status effects. The original status effects can be queried in the wiki | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the deletion is successful | 

- Example


```python 
res = self.RemoveEffect(entityId, "speed") 
``` 

## AddEffect 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add a specified state effect to the entity. If the added state already exists, the following situations will occur: 1. If the level is greater than the existing state, update the state level and duration; 2. If the state levels are equal and the remaining time duration is greater than the existing state, refresh the remaining time; 3. If the level is less than the existing state, do not modify it; 4. The particle effect is based on the new one 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effectName | str | Status effect name string, including custom status effects and vanilla status effects. Vanilla status effects can be found on the wiki | 
| duration | int | Duration of the status effect, in seconds | 
| amplifier | int | The additional level of the status effect. Must be between 0 and 255 (inclusive). If not specified, it defaults to 0. Note that the first level of a status effect (such as health regeneration I) corresponds to 0, so the second level of a status effect, such as health regeneration II, should be specified with a strength of 1. Some effects and custom status effects have no intensity difference, such as night vision | 
| showParticles | bool | Whether to display particle effects, True to display, False not to display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
res = self.AddEffect("speed", 30, 2, True) 
``` 

## GetEffects 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get all current status effects of the entity 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | List of status effect information dictionaries | 

- Notes 
- Status effect information dictionary effectDict 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| effectName | str | Status effect name | 
| duration | int | Status effect remaining duration, in seconds | 
| amplifier | int | Status effect additional level | 

- Example 

```python 
effectDictList = self.GetEffects() 
``` 

## TriggerCustomEvent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Trigger custom events for creatures 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Creature ID | 
| eventName | str | Event name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example


```python 
eventName = "netease:custom_exploading" 
self.TriggerCustomEvent(eventName) 
``` 

## IsAlive 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Determine whether a biological entity is alive or a non-biological entity exists 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | false means that the biological entity has died or the non-biological entity has been destroyed, true means that the biological entity is alive or the non-biological entity exists | 

- Notes 
- Note that if the block where the detected entity is located is unloaded, the interface returns False. Therefore, it is necessary to pay attention to whether the block where the entity is located is loaded. 
- Block unloading: The game will only load the blocks around the player. When the player moves to another area, the blocks in the original area will be unloaded. Refer to [Block Introduction](https://minecraft-zh.gamepedia.com/%E5%8C%BA%E5%9D%97) 

- Example 

```python 
alive = self.IsEntityAlive() 
``` 

## GetGravity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the gravity factor of the entity. When the gravity factor of the creature is 0, the gravity factor of the world is applied 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Gravity factor | 

## SetGravity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the gravity factor of the entity. When the gravity factor of the creature is 0, the gravity factor of the world is applied 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| gravity | float | Negative number, indicating the downward speed per frame | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetGravity(-0.08) 
``` 

## SetHurt 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 


Causes damage to an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| damage | int | Damage value | 
| cause | str | Damage source, see <a href="../../../1-ModAPI/Enumeration value/ActorDamageCause.html">ActorDamageCause enumeration</a> in the Minecraft enumeration value document for details | 
| attackerId | str | Entity id of the damage source, default is None | 
| childAttackerId | str | Child entity id of the damage source, default is None, for example, if the player uses a projectile to cause damage to the entity, the value should be the projectile id | 
| knocked | bool | Whether the entity was knocked back, the default value is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

## SetImmuneDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether the entity is immune to damage (this property is archived) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| immune | bool | Whether immune to damage | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetImmuneDamage(True) 
``` 



## SetModAttr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name. It is recommended to prefix str with mod to avoid conflicts between multiple mods | 
| paramValue | any | Attribute value, supports Python basic data | 

- Return value 

None 

- Remarks 
- Note: tuple and set will be converted to list during synchronization. It is recommended to use non-collection types such as numbers and strings. 

- Example 

```python 
self.SetModAttr('health', 1) 
self.SetModAttr('testDict', {'key':'value'}) 
``` 

## GetModAttr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name. It is recommended to prefix str with mod to avoid conflicts between multiple mods | 
| defaultValue | any | The default value of the attribute. When the attribute does not exist, the default value is returned. At this time, the attribute value is still not set | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | Return attribute value | 

- Notes 
- DefaultValue is None by default when not passed 

- Example 

```python 
# If you modify the collection type obtained by GetAttr directly, you need to call SetAttr again to ensure that it is updated 
testDict = self.GetModAttr('testDict') 
testDict['key'] = 'newValue' 
self.SetModAttr('testDict', testDict) 
``` 

## RegisterModAttrUpdateFunc 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Register the callback function when the attribute value changes. The function will be called when the attribute changes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name to be monitored | 
| func | function | Callback function to be monitored | 

- Return value 

None 

- Remarks 
- The callback function needs to accept a parameter, which is a dict. The specific data example is: {'oldValue': 0, 'newValue': 1, 'entityId': ’-433231231231‘} 

- Example 

```python 
# This entityId passes the ID of the object to be monitored 
self.RegisterModAttrUpdateFunc('health', self.jumpingText) 
# When the health attribute of the script layer changes, self.jumpingText will be called

def jumpingText(self, data): 
entityId = data['entityId'] 
oldValue = data['oldValue'] 
newValue = data['newValue'] 
``` 

## UnRegisterModAttrUpdateFunc 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Callback function when unregistering attribute value change 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name to monitor | 
| func | function | Callback function to monitor | 

- Return value 

None 

- Notes 
- The same function as the one used during registration needs to be passed as a parameter 

- Example 

```python 
self.UnRegisterModAttrUpdateFunc('health', self.jumpingText) 
``` 

## GetName 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the custom name of the creature, that is, the name set using the name tag or SetName interface 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Custom name of the creature | 

## SetName 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Used to set a custom name for the creature, which has the same function as the original name tag. Players and new wandering merchants do not support it yet 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetName("new Name") 
``` 

## SetShowName 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 


Set whether the creature's name is displayed according to the default game logic 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| show | bool | True means display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Return whether the setting is successful | 

- Notes 
- When set to True, the name display of the creature follows the default rendering logic of the game, that is, ordinary creatures need the center point to point to the creature to display the name, and the player will always display the name 

- Example 

```python 
# Do not display the name above the head 
self.SetShowName(False) 
``` 

## SetAlwaysShowName 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether the creature name is always displayed, and can be displayed even when the aiming point is not pointing at the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| show | bool | True is displayed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Return whether the setting is successful | 

- Notes 
- This interface is only effective for ordinary creatures and does not work for player settings


- Example 

```python 
# Do not display the name above the head 
self.SetAlwaysShowName(False) 
``` 

## SetPersistence 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether the entity is saved 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isPersistent | bool | True means save, False means do not save | 

- Return value 

None 

- Notes 
- Entities are saved by default. Entities set to not save will not be saved when the block is unloaded or the game is exited. 

- Example 

```python 
self.SetPersistence(True) 
``` 

## SetMotion 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the instantaneous moving direction vector of the creature. The server can only be used for non-players, and the client can only be used for local players.


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motion | tuple(float,float,float) | Vector in the world coordinate system. The direction is the vector in the world coordinate system. The positive direction of the x, z, and y axes is the positive value. The current direction of the player can be determined by the rot component of the current creature. You can open F3 in development mode to observe the value change. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Make the creature rush a certain distance in the direction of the crosshair 
rot = self.GetEntityRot(entityId) 
x, y, z = self.GetDirFromRot(rot) 
self.SetMotion((x * 5, y * 5, z * 5)) 
# Relationship between rot and world coordinate system 
# ^ x -90° 
# | 
# 180°/-180 ----------> z 0° 
# | 90° 
``` 

## GetMotion 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the instantaneous moving direction vector of the creature (including the player) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Instantaneous moving direction vector, returns None in case of exception | 




## SetItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set biological items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| posType | int | ItemPosType enumeration | 
| itemDict | dict | List of item information dictionaries at different positions on the creature. If None is passed in, the items/equipment at the current position will be cleared | 
| slotPos | int | Container slot | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if the setting is successful | 

- Example

```python
itemDict = {
    'itemName': 'minecraft:bow',
    'count': 1,
    'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),],
    'auxValue': 0,
    'customTips':'§c new item §r',
    'extraId': 'abc',
    'userData': {},
}
self.SetItem(serverApi.GetMinecraftEnum().ItemPosType.OFFHAND, None, 0)
```



## SetCanOtherPlayerRide

<span style="display:inline;color:#ff5555">Server</span>

method in Preset.Model.Entity.EntityObject.EntityObject

- describe


Set whether other players have the right to ride 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| canRide | bool | Control | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetCanOtherPlayerRide(entityId,False) 
``` 

## SetControl 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set this creature to be able to walk and jump without equipping a saddle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isControl | bool | Whether to control | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetControl(entityId,False) 
``` 




## SetRidePos 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the creature's riding position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | Attachment point when riding | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetRidePos(entityId,(1, 1, 1)) 
``` 

## SetNotRender 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether to turn off entity rendering 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| notRender | bool | True means not to render the entity | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether successful | 

- Example 

```python 
self.SetNotRender(True) # Stop rendering the entity 
``` 

## SetCollidable 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether the entity is collidable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isCollidable | bool | False: Non-collidable True: Collidable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
self.SetCollidable(True) # Set to collidable 
``` 

## SetHealthColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 


Set the color and background color of the health bar. The health bar can only be displayed when the game component is set to ShowHealthBar! ! 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| front | tuple(float,float,float,float) | RGBA value of health bar color, range 0-1 | 
| back | tuple(float,float,float,float) | RGBA value of background color, range 0-1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None | No return value | 

- Example 

```python 
self.SetHealthColor((0, 0, 0, 1), (1, 1, 1, 1)) 
``` 

## AddAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add biological rendering animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| animationKey | str | Animation key | 
| animationName | str | Animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
self.AddAnimation("custom_move", "animation.pig.custom_move")

``` 

## AddAnimationController 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add biological rendering animation controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| animationControllerKey | str | Animation controller key | 
| animationControllerName | str | Animation controller name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
self.AddAnimationController("controller__use_item_progress", "controller.animation.humanoid.use_item_progress") 
``` 

## AddScriptAnimate 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add animation/animation controller to the scripts/animate node in the client entity definition (minecraft:client_entity) json of the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| animateName | str | Animation/animation controller name, such as look_at_targe |

| condition | str | Animation/animation controller control expression, default is empty, such as query.mod.index > 0 | 
| autoReplace | bool | Whether to overwrite the existing animation/animation controller, the default value is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
self.AddScriptAnimate("animation_controller_short_name", "query.mod.index > 0") 
``` 

## AddParticleEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add biological special effects resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effectKey | str | Effect resource Key | 
| effectName | str | Effect resource name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
self.AddParticleEffect("nectar_dripping", "minecraft:nectar_drip_particle") 
``` 

## AddRenderController 


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add a biological rendering controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| renderControllerName | str | Rendering controller name | 
| condition | str | Rendering controller condition | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Add successfully | 

- Example 

```python 
self.AddRenderController('custom_render_controller_name', 'query.mod.condition') 
``` 

## AddRenderMaterial 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add the material required for biological rendering. After calling this interface, you need to call RebuildActorRender to take effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| materialKey | str | Material key | 
| materialName | str | Material name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the addition is successful | 

- Example 

```python 
self.AddRenderMaterial('custom_material_key', 'custom_material_name') 
``` 

## AddSoundEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Add biological sound effect resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| soundKey | str | Sound effect resource Key | 
| soundName | str | Sound effect resource name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
self.AddSoundEffect("sound_thunder", "ambient.weather.thunder") 
``` 

## SetPushable 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set whether the entity is pushable


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isPushable | bool | False: cannot be pushed True: can be pushed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
self.SetPushable(True) 
``` 

## SetModel 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the skeleton model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| modelName | str | Model name, reset the model when the value is "" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- To restore the original model, please use the ResetModel interface 
- Using the client component to replace the model will not synchronize and save, it is only a pure client performance. If synchronization and saving are required, please use the server's model component 

- Example 

```python

self.SetModel("xuenv") 
``` 

## GetLavaSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the entity preset movement speed in the lava 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Movement speed in the lava | 

## SetLavaSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the entity preset movement speed in the lava 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Movement speed in lava | 

- Return value 

None 

## GetMaxLavaSpeed


<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Get the maximum speed of the entity preset in the lava 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Maximum speed in the lava | 

## SetMaxLavaSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Entity.EntityObject.EntityObject 

- Description 

Set the maximum speed of the entity preset in the lava 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Maximum movement speed in lava | 

- Return value 

None 

