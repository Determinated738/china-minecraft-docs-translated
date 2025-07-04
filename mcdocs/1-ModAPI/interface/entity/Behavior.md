--- 
sidebarDepth: 1 
--- 
# Behavior 

## AddEntityAroundEntityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add an entity around motion motion for an entity (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eID | str | ID of an entity to be around | 
| angularVelocity | float | Angular velocity of circular motion (radians/second) | 
| axis | tuple(float,float,float) | The axis of circular motion determines on which plane the circular motion is performed. The default value is (0, 1, 0) | 
| lockDir | bool | Whether to lock the entity's orientation when the motion device is in effect. If not locked, the entity's orientation will change with the motion. The default value is False. | 
| stopRad | float | The arc required to stop the motion device. When stopRad is 0, the motion device will continue to run. The default value is 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Motion device ID. Returns -1 when adding fails | 

- Notes 
- This interface does not block the AI motion and gravity of the creature itself. When AI motion occurs, the final performance result may be different from the expected result. 
- Multiple orbital motion devices can be superimposed, and they can be superimposed with speed motion devices. 
- Since the engine will stop all activities when loading entities outside the chunk, it is recommended to control the entity's motion range within ±100 of the player's position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
axis=(-1, 1, 1) 
mID = motionComp.AddEntityAroundEntityMotion(eID, 1.0, axis, lockDir=False, stopRad=0) 
``` 

## AddEntityAroundPointMotion 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add a point-to-point orbit mover to an entity (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| center | tuple(float,float,float) | Coordinates of the center point of the circle to orbit | 
| angularVelocity | float | Angular velocity of circular motion (radians/second) | 
| axis | tuple(float,float,float) | The axis of circular motion, which determines on which plane the circular motion is made. The default is (0, 1, 0) | 
| lockDir | bool | Whether to lock the entity's orientation when the mover is in effect. If not locked, the entity's orientation will change with the motion. The default is False. | 
| stopRad | float | The arc required to stop the mover. When stopRad is 0, the mover will keep running. The default value is 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Mover ID. Returns -1 when adding fails | 

- Notes 
- This interface does not block the AI movement and gravity of the creature itself. When AI movement occurs, the final performance may be different from the expected result. 
- Multiple orbital movers can be superimposed, and they can be superimposed with speed movers. 
- Since the engine stops all activities when an entity is outside the loaded block, it is recommended to control the movement range of the entity within ±100 of the player position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
center = (0, 8, 0) 
axis=(-1, 1, 1) 
mID = motionComp.AddEntityAroundPointMotion(center, 1.0, axis, lockDir=False, stopRad=0) 
``` 

## AddEntityTrackMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add a track motioner to an entity (excluding the player) 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetPos | tuple(float,float,float) | End point of the track | 
| duraTime | float | Time required to reach the end point | 
| startPos | tuple(float,float,float) | Start point of the track. The default value is None, which means that the position where [StartEntityMotion](#StartEntityMotion) is called is used as the starting point. | 
| relativeCoord | bool | Whether to use relative coordinates to set the start and end points. The default value is False. | 
| isLoop | bool | Whether to loop. If set to True, the entity will move back and forth between the start and end points. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Motion device ID, returns -1 when adding fails | 

- Notes 
- This interface does not block the AI movement of the creature itself, and the creature will be damaged by falling when in the air. When AI movement occurs, the final performance result may be different from the expected result. It is recommended to set the creature as NPC. 
- Track motion devices cannot be superimposed, only one can be added. 
- Since the engine will stop all activities when loading entities outside the block, it is recommended to control the movement range within ±100 of the player position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
target = (5, 0, 0) 
mID = motionComp.AddEntityTrackMotion(target, 3.0, startPos=None, relativeCoord=True, isLoop=False) 
``` 

## AddEntityVelocityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add a velocity motion to an entity (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| velocity | tuple(float,float,float) | Velocity, including magnitude and direction | 
| accelerate | tuple(float,float,float) | Acceleration, including magnitude and direction. The default value is None, indicating no acceleration | 
| useVelocityDir | bool | Whether to use the current velocity direction as the direction of the entity at this moment. The default value is True | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Motion device ID, returns -1 when adding fails | 

- Notes 
- This interface does not block the AI movement and gravity of the creature itself. When AI movement occurs, the final performance result may be different from the expected. 
- Multiple speed motion devices can be superimposed, and can be superimposed with the surrounding motion device. 
- Since the engine will stop all activities when loading entities outside the block, it is recommended to control the movement range of the entity within ±100 of the player position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
velocity = (0, 0, 1) 
accelerate = (0, 0, -1) 
mID = motionComp.AddEntityVelocityMotion(velocity, accelerate, useVelocityDir=True) 
``` 

## GetAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actionCompServer.ActionCompServer 

- Description 

Get the target of aggro 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Returns the entity id of the target of aggro. If the entity corresponding to the passed entity id has no aggro target, it returns -1. If the entity corresponding to the passed entity id does not exist, it returns None. | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAction(entityId) 
comp.GetAttackTarget() 
```



## GetBlockControlAi 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.controlAiCompServer.ControlAiCompServer 

- Description 

Get whether the creature's native AI is blocked 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether AI is retained. False means AI is blocked. | 

- Notes 
- After AI is blocked, the creature cannot move, is not affected by gravity, and cannot be pushed. But it can be damaged and can be interacted with by players (for example, a horse can be ridden or a villager can be traded) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateControlAi(entityId) 
comp.GetBlockControlAi() 
``` 

## GetCustomGoalCls 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 

- Description 

Base class for getting custom behavior nodes on the server. When implementing a new behavior node, you need to inherit the class returned by this interface 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(CustomGoal) | Server-side custom behavior node class | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
CustomGoal = serverApi.GetCustomGoalCls() 
class CustomGoalDemo(CustomGoal): 
def __init__(self, entityId, argsJson): 
CustomGoalCls.__init__(self, entityId, argsJson) 
``` 

## GetEntityMotions 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Get all motion devices on an entity (excluding players) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Motion device collection, key value represents the motion device mID, value value represents the motion device type 0: track motion device, 1: speed motion device, 2: orbit motion device | 

- Notes 
- Motion devices will be removed after non-human stop. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motions = motionComp.GetEntityMotions() 
# motions = { 
# 0:1, 
# 1:2

# } 
``` 

## GetMotion 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Get the instantaneous moving direction vector of the creature (including the player) 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Instantaneous moving direction vector, returns None in case of exception | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.GetMotion() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Get the instantaneous moving direction vector of the creature 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Instantaneous moving direction vector, returns None in case of exception | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.GetMotion() 
``` 

## GetOwnerId 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.tameCompServer.TameComponentServer 

- Description 

Get the owner id of the tamed creature 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Owner id, returns None if it does not exist | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTame(entityId) 
oid = comp.GetOwnerId() 
``` 

## GetStepHeight 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Returns the maximum step height that the player can climb when moving forward without jumping 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Step height | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
print(comp.GetStepHeight()) 
``` 

## Hurt 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.hurtCompServer.HurtCompServer 

- Description 

Set entity damage 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| damage | int | Damage value | 
| cause | str | Damage source, see the [ActorDamageCause enumeration](../../enumeration value/ActorDamageCause.md) in the Minecraft enumeration value document for details | 
| attackerId | str | Entity id of the damage source, default is None | 
| childAttackerId | str | Child entity id of the damage source, default is None, for example, if the player uses a projectile to cause damage to the entity, the value should be the projectile ID | 
| knocked | bool | Whether the entity is knocked back, the default value is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHurt(playerId) 
comp.Hurt(10, serverApi.GetMinecraftEnum().ActorDamageCause.EntityAttack, attackerId, None, False) 
``` 

## ImmuneDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.hurtCompServer.HurtCompServer 

- Description 

Set whether the entity is immune to damage (this property is archived) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| immune | bool | Immune to damage | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHurt(entityId) 
comp.ImmuneDamage(True) 
``` 

## IsEntityOnFire 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer


- Description 

Get whether the entity is on fire 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it on fire | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
isOnFire = comp.IsEntityOnFire() 
``` 

## RemoveEntityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Remove the motion device on the entity (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motionId | int | The ID of a motion device to be removed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal was successful | 

- Example 

```python

import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.RemoveEntityMotion(mID) 
``` 

## ResetAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actionCompServer.ActionCompServer 

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
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAction(entityId) 
comp.ResetAttackTarget() 
``` 
## ResetMotion 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 
- Description 
Reset the instantaneous movement direction vector of the creature (excluding the player) 
- Parameters 
None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This interface can only reset the instantaneous moving direction vector set by SetMotion, and cannot affect the movement generated by the creature's own AI. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.ResetMotion() 
``` 

## ResetStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Restore the engine default maximum step height that the player can climb when moving forward without jumping 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId)
comp.ResetStepHeight()
```

## SetActorCollidable 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorCollidableCompClient.ActorCollidableCompClient 

- Description 

Set whether the entity is collidable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isCollidable | int | 0: Non-collidable 1: Collidable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorCollidable(entityId) 
success = comp.SetActorCollidable(1) 
``` 

## SetActorPushable 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorPushableCompServer.ActorPushableCompServer 

- Description 

Set whether the entity is pushable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isPushable | int | 0: Not pushable 1: Pushable | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateActorPushable(entityId) 
success = comp.SetActorPushable(1) 
``` 

## SetAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actionCompServer.ActionCompServer 

- Description 

Set the target of hatred 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetId | str | target entity id | 

- return value 

| <div style="width: 4em">data type</div> | description | 
| :--- | :--- | 
| bool | set result | 

- example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAction(entityId) 
comp.SetAttackTarget(targetId) 
``` 

## SetBlockControlAi 

<span style="display:inline;color:#ff5555">server</span> 


method in mod.server.component.controlAiCompServer.ControlAiCompServer 

- Description 

Set to block the native AI of creatures 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isBlock | bool | Whether to keep AI, False means blocking | 
| freezeAnim | bool | Whether to freeze the action when blocking AI, the default is False, only effective when isBlock is False. Re-entering the world will restore the initial action | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- After AI is blocked, the creature cannot move, is not affected by gravity and cannot be pushed, but can be damaged and can be interacted with by players (such as horses being ridden or villagers being traded) 
- Invalid for players 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateControlAi(entityId) 
comp.SetBlockControlAi(False, True) 
``` 

## SetCanOtherPlayerRide 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Set whether other players have the right to ride. True means every player can ride, False means only the tamer can ride 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| tamedEntityId | str | Rideable creature id | 
| canRide | bool | Whether to control | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
# Tame creature 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetCanOtherPlayerRide(entityId,False) 
``` 

## SetControl 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Set the creature to control walking and jumping without equipping a saddle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| tamedEntityId | str | Rideable creature id | 
| isControl | bool | Control or not | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- This interface is only effective for tamed rideable creatures. If you use the SetEntityRide interface to tame a creature, you need to call this interface after a certain number of frames. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetControl(entityId,True) 
```



## SetEntityInteractFilter 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.interactCompServer.InteractComponentServer 

- Description 

Set the conditions for interacting with creatures 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| index | int | Interaction list index | 
| interactFilter | str | Interaction conditions | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- This interface modifies the definition of filters in minecraft:interact->on_interact 
- This interface can only be called when the creature has a minecraft:interact component, such as cows, alpacas, piglins, etc. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
import json 
comp = serverApi.GetEngineCompFactory().CreateInteract(entityId) 
filterDict = { 
"filters": { 
"all_of": [ 
{ "test": "is_family", "subject" : "other", "value" : "player"}, 
{ "test": "has_equipment", "domain": "hand", "subject": "other", "value": "bucket:0"} 
] 
} 
} 
filterStr = json.dumps(filterDict) 
comp.SetEntityInteractFilter(0, filterStr) 
``` 



## SetEntityOnFire 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Set the entity on fire 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| seconds | int | Time on fire (unit: seconds) | 
| burn_damage | int | HP deducted per second when on fire. If not passed, the default value is 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- It will not take effect in water or rain, and the ignition time is affected by the creature's equipment and the creature's status. The value range of burn_damage is 0~1000. If it is less than 0, it will be 0, and if it is greater than 1000, it will be 1000. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.SetEntityOnFire(1, 2) 
``` 

## SetEntityRide 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Tame a rideable creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| playerId | str | player id | 
| tamedEntityId | str | id of the rideable creature to be tamed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Taming information will be saved 

- Example 

```python 
# Taming creature 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetEntityRide(playerId,entityId) 
``` 

## SetEntityShareablesItems 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.shareableCompServer.ShareableComponentServer 

- Description 

Set the list of items that can be shared/picked up by the mob 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| items | list(itemdict) | List of items that can be shared/picked up | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- This interface modifies the items definition of minecraft:shareables 
- This interface can only be called when the mob has a minecraft:shareables component, such as foxes, husks, piglins, etc. If admire is True, the mob also needs to have a minecraft:admire_item component. If barter is True, the mob must also have the minecraft:behavior.barter behavior. 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateShareables(entityId) 
shareableItems = [] 
shareableItems.append({ 
"item": "minecraft:golden_sword", 
"auxValue": 0, 
"priority": 1, 
"pickupLimit": 1, 
"barter": True, 
"admire": True, 
}) 
comp.SetEntityShareablesItems(shareableItems) 
``` 

## SetEntityTamed 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.tameCompServer.TameComponentServer 

- Description 

Sets the creature taming, which needs to be used with the entityEvent component. This type of taming does not include the riding function. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Tamed player ID | 
| tamedId | str | Tamed creature ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- To tame a creature, follow these steps: 
1. Modify the creature json file to make it tamable: 
- Add minecraft:tameable component 
- Add a component group to put the tamed behavior in it 
- Add an event, add the component group just added, and remove the unnecessary component group 
2. Use SetEntityTamed to tame the target creature 
3. Use TriggerCustomEvent to trigger the taming event 
If it is used for the original tamable creature, there is no need to modify the json according to the first step, but find the existing event and trigger it in the third step

- If you want to make creepers tamable, modify json as follows: 
```json 
{ 
"format_version": "1.8.0", 
"minecraft:entity": { 
"description": { 
"identifier": "minecraft:creeper", 
"is_spawnable": true, 
"is_summonable": true, 
"is_experimental": false 
}, 
"component_groups": { 
... 
//Add tamed state 
"netease:creeper_tame":{ 
"minecraft:is_tamed": { 
}, 
//Follow owner 
"minecraft:behavior.follow_owner": { 
"priority": 4, //Priority is higher than other movement behaviors 
"speed_multiplier": 1.0, 
"start_distance": 10, 
"stop_distance": 2 
} 
} 
}, 

"components": { 
... 
//Add taming components, use bones to tame 
"minecraft:tameable": { 
"probability": 0.33, 
"tameItems": "bone", 
"tame_event": { 
"event": "netease:on_tame", 
"target": "self" 
} 
} 
}, 

"events": { 
... 
//Add taming events 
"netease:on_tame": { 
//Remove all logic related to explosion 
"remove": { 
"component_groups": [ 
"minecraft:exploding", 
"minecraft:charged_exploding", 
"minecraft:forced_exploding",

"minecraft:forced_charged_exploding", 
"minecraft:charged_creeper" 
] 
}, 
//Add netease:creeper_tame 
"add": { 
"component_groups": [ 
"netease:creeper_tame" 
] 
} 
} 
} 
} 
} 
``` 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Make tamedId tamed by playerId 
tameComp = serverApi.GetEngineCompFactory().CreateTame(tamedId) 
tameComp.SetEntityTamed(playerId,tamedId) 
# Trigger netease:on_tame custom event of tamedId 
envComp = serverApi.GetEngineCompFactory().CreateEntityEvent(tamedId) 
envComp.TriggerCustomEvent(tamedId,'netease:on_tame') 
``` 

## SetJumpPower 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gravityCompServer.GravityComponentServer 

- Description 

Set the creature's jump power, 0.42 represents the normal level 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| jumpPower | float | Jump power, normal is 0.42 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Notes 
- The jumping power of creatures affects the height of creature jumps; this interface needs to be loaded by the client. For example, in AddServerPlayer, the client has not been loaded yet, and the execution must be delayed to take effect. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGravity(entityId) 
comp.SetJumpPower(0.84) 
``` 

## SetMobKnockback 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actionCompServer.ActionCompServer 

- Description 

Set the initial speed of the knockback, and consider the influence of resistance 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| xd | float | x-axis direction, used to control the angle | 
| zd | float | z-axis direction, used to control the angle | 
| power | float | used to control the initial horizontal velocity | 
| height | float | initial vertical velocity | 
| heightCap | float | upward velocity threshold, this value needs to be considered when the entity itself already has an upward velocity, to ensure that the final upward velocity does not exceed heightCap | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None | No return value | 

- Notes 
- When using this interface in the damageEvent event, the knock parameter of the damageEvent event callback needs to be set to False 
- This interface will trigger the OnKnockBackServerEvent event, so when you need to use it in this event, please write logic to avoid circular calls 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAction(entityId)

comp.SetMobKnockback(0.1, 0.1, 1.0, 1.0, 1.0) 
``` 

## SetMotion 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Sets the instantaneous moving direction vector of the creature (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motion | tuple(float,float,float) | The direction is the vector in the world coordinate system. The positive direction of the x, z, and y axes is the positive value. The rot component of the current creature can be used to determine the direction the player is currently facing. In development mode, press F3 to observe the value change. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When using this interface in the damageEvent event, the knock parameter of the damageEvent event callback needs to be set to False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Make the creature rush a certain distance in the direction of the crosshair 
rotComp = serverApi.GetEngineCompFactory().CreateRot(entityId) 
rot = rotComp.GetRot() 
x, y, z = serverApi.GetDirFromRot(rot) 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.SetMotion((x * 5, y * 5, z * 5)) 
# Relationship between rot and world coordinate system 
# ^ x -90° 
# | 
# 180°/-180 ----------> z 0° 
# | 90° 
``` 




### Client interface 

<span id="c0"></span> 
method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Set the instantaneous moving direction vector for local players 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motion | tuple(float,float,float) | Vector in the world coordinate system. The direction is the vector in the world coordinate system. The positive direction of the three axes x, z, and y is the positive value. The current player's rot component can be used to determine the direction the current player is facing. You can open F3 in development mode to observe the value changes. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the local player's instantaneous movement vector is frequently and quickly modified, the engine server's anti-cheating mechanism (such as fall damage) may be triggered. If frequent and rapid modifications are required, it is best to synchronize the modification with the server-side SetMotion 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Make the player rush a certain distance in the direction of the crosshair 
localPlayerId = clientApi.GetLocalPlayerId() 
rotComp = clientApi.GetEngineCompFactory().CreateRot(localPlayerId) 
rot = rotComp.GetRot() 
x, y, z = clientApi.GetDirFromRot(rot) 
motionComp = clientApi.GetEngineCompFactory().CreateActorMotion(localPlayerId) 
motionComp.SetMotion((x * 5, y * 5, z * 5)) 
# Relationship between rot and world coordinate system 
# ^ x -90° 
# | 
# 180°/-180 ----------> z 0° 
# | 90° 
``` 

## SetMoveSetting 

<span style="display:inline;color:#ff5555">Server</span> 


method in mod.server.component.moveToCompServer.MoveToComponentServer 

- Description 

Pathfinding component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Pathfinding target position | 
| speed | float | Movement speed, which refers to the multiple of normal movement speed. For example, 1.0 means normal speed, and 2.0 means twice the speed | 
| maxIteration | int | Maximum number of iterations of the pathfinding algorithm. Default is 200 | 
| callback | function | Pathfinding end callback function | 

- Return value 

None 

- Notes 
- When using this interface, you need to configure the pathfinding json component in the creature. After configuring the pathfinding json component, the interface will automatically select the corresponding type of pathfinding 
Currently supported pathfinding json components include: 
- minecraft:navigation.walk 
Land pathfinding, the same as the original zombie pathfinding 
- minecraft:navigation.generic 
Aquatic pathfinding, supports land and water, the same as the original drowned pathfinding 
- minecraft:navigation.climb 
Land pathfinding, but supports climbing walls, the same as the original spider pathfinding. This kind of pathfinding may be blocked by overhead blocks and cannot reach the destination. 
- minecraft:navigation.fly 
Aerial pathfinding, the same as the original parrot pathfinding 
The above pathfinding needs to be used with some other json components (such as movement). For details, please refer to the example of NavigationMod 
The navigation types not mentioned above are not supported, such as minecraft:navigation.float (such as the original ghast), minecraft:navigation.hover (such as the original bee) 
- Different creatures have different default maximum follow distances. If the distance to the target point to be pathfinded is greater than this value, the engine will refuse to pathfind. To modify this distance, you can configure it in the entity's json. 
```json 
{ 
"format_version": "1.8.0", 
"minecraft:entity": { 
"components": { 
"minecraft:follow_range": { 
"value": 48, 
"max": 48 
} 
} 
} 
} 
``` 
- About the maxIteration parameter 
This parameter will affect the actual length of the path found. If the pathfinding algorithm fails to find the target point after a certain number of iterations, it will return to the local optimal solution, that is, the creature will only go halfway. 
In the absence of large obstacles, the reference pathfinding distance corresponding to the parameter is as follows: The default value of this parameter is 200 and the maximum value is 2000. Developers are requested to choose according to actual conditions. 
| maxIteration | Straight-line distance to the target point |

| ------------ | ---------------- | 
| 200 | 13 | 
| 500 | 20 | 
| 1000 | 30 | 
| 2000 | 43 | 
- About callback function 
This function needs to accept two parameters, the first parameter is the pathfinding entityId, type str, the second parameter is the pathfinding result, type int 
(The position obtained by the player will be 1.62 grids higher than the ground. If the player's position is used as the target point, the y axis needs to be subtracted by 1.62 first, otherwise the callback will always return 1) 
| Result | Description | 
| ---- | ------------------------------------------------------------ | 
| -3 | Pathfinding failed, greater than the follow distance, or there is no walkable position around the creature, or it is used for a flying creature that is pathfinding | 
| -2 | Pathfinding failed, the creature has no pathfinding component (referring to minecraft:navigation) | 
| -1 | Pathfinding failed, parameter error, or the creature does not exist | 
| 0 | Pathfinding completed. Reached the set target point | 
| 1 | Pathfinding completed, but did not reach the target point (maybe because the maxIteration parameter is too small) | 
| 2 | Pathfinding interrupted. Obstacle encountered midway | 
| 3 | Pathfinding interrupted. Overwritten by the original biological pathfinding behavior, or the moveTo component is called repeatedly before the pathfinding is completed. <br>If the creature's movement speed is too low (the actual speed is less than 0.3 grids per second), it will also be regarded as pathing stuck and return this error code | 
- For various types of pathing creatures, the following initial conditions must be met: 
1. Land pathing, water pathing and wall pathing: One of the following conditions must be met: 
- The creature is on the ground 
- The creature is riding and the ride is on the ground 
- The creature is in liquid 
- The creature is withering 
2. Flying pathing: One of the following conditions must be met: 
- Not in the riding state 
- In liquid 
- The creature is on the ground 
- The can_path_from_air attribute in the json configuration is true 
- Demo introduction: 
Entering walk/generic/climb/fly in the chat bar will generate a creature using the corresponding navigation json component on the spot, then run to another location, and then enter go, which will navigate the creature just generated to the player's current location. 
The behavior json of these 4 example creatures can be viewed in the NavigationMod_behavior/entities directory. 
The maximum pathfinding distance of the 4 example creatures is set to 48 blocks. 

- Example

```python
from mod_log import logger as logger
def myCallback(entityId, result):
    if result in (-1,-2,-3):
        logger.info('[error] [SetMoveSetting] failed')
    elif result==0:
        logger.info('[info] [SetMoveSetting] success')
    elif result in (1,2,3):
        logger.info('[warn] [SetMoveSetting] terminated')

import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateMoveTo(entityId)
comp.SetMoveSetting((x,y,z),2.0,200,myCallback)
```



## SetPersistence 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.persistenceCompServer.PersistenceCompServer 

- Description 

Set whether the entity is persistent. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isPersistent | bool | True means the entity is persistent, False means the entity is not persistent. | 

- Return value 

None 

- Notes 
- In the game, entities are persistent by default. If they are not persistent, the entity will be deleted when the block is unloaded and the save is exited, and will not be saved. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePersistence(entityId) 
comp.SetPersistence(True) 
``` 

## SetRidePos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Set the creature's riding position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| tamedEntityId | str | Rideable creature id |

| pos | tuple(float,float,float) | Attachment point when riding | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetRidePos(entityId,(1,1,1)) 
``` 

## SetRiderRideEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Set the entity to ride (or boat or minecart) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| riderId | str | The id of the ridden creature | 
| riddenEntityId | str | The id of the ridden creature. Requires the definition of the ridden creature to have a minecraft:rideable component, and the family_types in the component contains a type declaration for the rider | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Usually needs to be used with SetEntityRide and SetControl, and the riding component in the ridden creature json needs to support the rider's creature type 
When the controlled entity has multiple locations and the developer wants to add multiple players, the first player added will be set as the controller by default by the engine 

- Example 

```python 
# Ride the mount 
import mod.server.extraServerApi as serverApi

comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetRiderRideEntity(playerId,rideEntityId) 
``` 

## SetStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Set the maximum step height that the player can climb when moving forward without jumping. The default value is 0.5625. If it is 1, it means that the player can climb one step. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| stepHeight | float | Maximum height, needs to be greater than 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- To avoid errors caused by floating point errors, the setting usually increases by 1/16 of the block size, that is, 0.0625. So here we set 2.0625. The default value in the game is 0.5625, which is half a grid height. 
- Only applies to players, and this attribute cannot be modified for other entities 
- The modification does not affect the jump logic and jump height, and it will not jump higher. Therefore, in some specific cases, you can walk on the block but cannot jump up. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
#If there is a two-block high block in front, the player can go up directly by pressing forward without jumping 
comp.SetStepHeight(2.0625) 
``` 

## StartEntityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 


- Description 

Start a motion device on an entity (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motionId | int | ID of a motion device to start | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the motion was started successfully | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.StartEntityMotion(mID) 
``` 

## StopEntityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Stop a motion device on an entity (excluding the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| motionId | int | ID of a motion device to be stopped | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the motion is stopped successfully | 

- Notes 
- Calling this interface will not trigger the event [EntityMotionStopServerEvent] (../../Event/Entity.md#EntityMotionStopServerEvent).


- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(entityId) 
motionComp.StopEntityMotion(mID) 
``` 

## TriggerCustomEvent 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.entityEventCompServer.EntityEventComponentServer 

- Description 

Trigger creature custom event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Creature ID | 
| eventName | str | Event name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Trigger creeper explosion 
Add the following event under the `events` field in the creeper's entity json file, and then run the sample code in the mod: 
```json 
"netease:custom_exploading":{ 
"sequence": [ 
{ 
"filters": { 
"test": "has_component", 
"operator": "!=", 
"value": "minecraft:is_charged" 
}, 
"add": { 
"component_groups": [ 
"minecraft:forced_exploding" 
]

} 
}, 
{ 
"filters": { 
"test": "has_component", 
"value": "minecraft:is_charged" 
}, 
"add": { 
"component_groups": [ 
"minecraft:forced_charged_exploding" 
] 
} 
} 
] 
} 
``` 
- The component_groups added or removed by the trigger event will not take effect until the next frame. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
#Trigger entity custom event 
eventName = "netease:custom_exploading" 
comp = serverApi.GetEngineCompFactory().CreateEntityEvent(entityId) 
comp.TriggerCustomEvent(entityId,eventName) 
``` 

