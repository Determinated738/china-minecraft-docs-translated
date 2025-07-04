--- 
sidebarDepth: 1 
--- 
# Behavior 

## AddPlayerAroundEntityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add an entity around motion for the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eID | str | ID of an entity to be around | 
| angularVelocity | float | Angular velocity of circular motion (radians/second) | 
| axis | tuple(float,float,float) | The axis of the circular motion, which determines on which plane the circular motion is made, defaults to (0, 1, 0) | 
| lockDir | bool | Whether to lock the entity's orientation when the motion device is in effect. If not locked, the entity's orientation will change with the motion. The default is False. | 
| stopRad | float | The arc required to stop the motion device. When stopRad is 0, the motion device will continue to run. The default is 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Motion device ID. Returns -1 when adding fails | 

- Notes 
- This interface does not block player-controlled movement and gravity. When player control occurs, the final performance result may be different from the expected result. Since the player's head is related to the camera control, if you need to make the motion device control the player's head, please use [DepartCamera](./Camera.md#DepartCamera) to separate the player and the camera. 
- Multiple surround motion controllers can be stacked, and they can be stacked with speed motion controllers. 
- Due to the restrictions on the chunks loaded in the engine, it is recommended to control the player's motion range within ±100 of the current position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
axis=(-1, 1, 1) 
mID = motionComp.AddPlayerAroundEntityMotion(eID, 1.0, axis, lockDir=False, stopRad=0) 
``` 

## AddPlayerAroundPointMotion 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add a point-to-point orbit mover to the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| center | tuple(float,float,float) | Coordinates of the center point of the circle to orbit | 
| angularVelocity | float | Angular velocity of circular motion (radians/second) | 
| axis | tuple(float,float,float) | The axis of circular motion, which determines on which plane the circular motion is performed. The default is (0, 1, 0) | 
| lockDir | bool | Whether to lock the entity's orientation when the mover is in effect. If not locked, the player's orientation will change with the motion. The default is False. | 
| stopRad | float | The arc required to stop the mover. When stopRad is 0, the mover will keep running. The default value is 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Mover ID. Returns -1 when adding fails | 

- Notes 
- This interface does not block the movement and gravity controlled by the player. When there is player control, the final performance result may be different from the expected result. Since the player's head is related to the camera control, if you need to make the mover control the player's head, please use [DepartCamera](./Camera.md#DepartCamera) to separate the player and the camera. 
- Multiple surround movers can be superimposed, and they can be superimposed with speed movers. 
- Due to the block restrictions loaded in the engine, it is recommended to control the player's movement range within ±100 of the current position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
center = (0, 8, 0) 
axis=(-1, 1, 1) 
mID = motionComp.AddPlayerAroundPointMotion(center, 1.0, axis, lockDir=False, stopRad=0) 
``` 

## AddPlayerTrackMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add a track motion to the player 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetPos | tuple(float,float,float) | End point of the track | 
| duraTime | float | Time required to reach the end point | 
| startPos | tuple(float,float,float) | Start point of the track. The default value is None, which means that the position where [StartPlayerMotion](#StartPlayerMotion) is called is used as the starting point. | 
| relativeCoord | bool | Whether to use relative coordinates to set the start and end points. The default value is False. | 
| isLoop | bool | Whether to loop. If set to True, the player will move back and forth between the start and end points. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Movement device ID, returns -1 when adding fails | 

- Notes 
- This interface does not block the movement controlled by the player. When there is player control, the final performance result may be different from the expected. 
- Track movement devices cannot be superimposed, only one can be added. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
target = (5, 0, 0) 
mID = motionComp.AddPlayerTrackMotion(target, 3.0, startPos=None, relativeCoord=True, isLoop=False) 
``` 

## AddPlayerVelocityMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Add a velocity motion to the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| velocity | tuple(float,float,float) | velocity, including magnitude and direction | 
| accelerate | tuple(float,float,float) | acceleration, including magnitude and direction, the default is None, indicating no acceleration | 
| useVelocityDir | bool | Whether to use the current velocity direction as the direction of the entity at this moment, the default is True | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Motion device ID, returns -1 when adding fails | 

- Notes 
- This interface does not block the movement and gravity controlled by the player. When there is player control, the final performance result may be different from the expected. Since the player's head is related to the camera control, if you need to make the motion device control the player's head, please use [DepartCamera](./Camera.md#DepartCamera) to separate the player and the camera. 
- Multiple speed motion devices can be superimposed, and they can be superimposed with the surround motion device. 
- Due to the block restrictions loaded in the engine, it is recommended to control the player's movement range within ±100 of the current position. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
velocity = (0, 0, 1) 
accelerate = (0, 0, -1) 
mID = motionComp.AddPlayerVelocityMotion(velocity, accelerate, useVelocityDir=True) 
``` 

## BeginSprinting 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Makes the local player enter and maintain a forward sprinting state 

- Parameters 

None 

- Return Value 

None 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateActorMotion(localPlayerId)
comp.BeginSprinting()
```

## ChangePlayerDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Teleport player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimensionId | int | Dimension, 0-overWorld; 1-nether; 2-theEnd | 
| pos | tuple(int,int,int) | Coordinates of the teleport | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When the interface successfully switches the dimension, the pos position is the position of the player's head, which is 1.62 lower than the set position 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(playerId) 
comp.ChangePlayerDimension(0, (0,4,0)) 
``` 

## ChangePlayerFlyState 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.flyCompServer.FlyComponentServer 

- Description 

Grant/cancel the flying ability and enter the flying/non-flying state 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| isFly | bool | Flight status, True: flight mode, False: normal walking mode | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Yes False: No | 

- Notes 
- It is not recommended to NotifyToServer in the OnGroundClientEvent event callback, and then call the ChangePlayerFlyState interface after the server receives the data. 
If you still need to call it this way, it is recommended to use AddTimer to delay one frame after receiving the data on the server side before calling the ChangePlayerFlyState interface 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFly(playerId) 
comp.ChangePlayerFlyState(True) 
``` 

## EnableKeepInventory 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player to not drop items when they die 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to enable "Keep Inventory" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
succ = comp.EnableKeepInventory(True)

``` 

## EndSprinting 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Ends the local player's forward sprinting state 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorMotion(localPlayerId) 
comp.EndSprinting() 
``` 

## GetEntityRider 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Get the id of the entity the player is riding. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| str | The entity id of the object that the player is riding directly. If the player is not riding, "-1" is returned | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
riderId = comp.GetEntityRider() 
``` 

## GetIsBlocking 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's activated shield status 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is the player's shield status activated | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.GetIsBlocking() 
``` 

## GetPlayerExhaustionRatioByType 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 


Get the hunger consumption multiplier of a player's behavior 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type | int | Behavior enumeration [PlayerExhauseRatioType enumeration](../../enumeration value/PlayerExhauseRatioType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Hunger consumption multiplier value, -1 means failed to obtain | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
jumpType = serverApi.GetMinecraftEnum().PlayerExhauseRatioType.JUMP 
ratio = comp.GetPlayerExhaustionRatioByType(jumpType) 
``` 

## GetPlayerMotions 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Get all motion devices on the player 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Motion device collection, key value represents the motion device mID, value value represents the motion device type 0: track motion device, 1: speed motion device, 2: surround motion device | 

- Notes 
- The motion device will be removed after it stops without human intervention. 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
motions = motionComp.GetPlayerMotions() 
# motions = { 
# 0:1, 
# 1:2 
# } 
``` 

## GetPlayerRespawnPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's respawn point 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Respawn point information, including dimensions and coordinates | 

- Notes 
- After using the spawnpoint command to set the player's birth point, this interface can obtain the set birth point 
- When the spawn point position has not been set using the setworldspawn command, the y-axis of the returned coordinate is 32767 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
print comp.GetPlayerRespawnPos() 
#Result example {'dimensionId': 0, 'pos': (44, 32767, 4)} 
``` 

## GetRelevantPlayer 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get a list of nearby player IDs 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | exceptList | List of excluded player IDs, the default value is None, other players and the player itself are not excluded | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | List of nearby player IDs | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.GetRelevantPlayer(exceptId) 
``` 

## IsEntityRiding 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Check if the player is riding. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Riding or not | 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
isRiding = comp.IsEntityRiding() 
``` 

## IsPlayerFlying 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.flyCompServer.FlyComponentServer 

- Description 

Get whether the player is flying 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Yes False: No | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFly(playerId) 
comp.IsPlayerFlying() 
``` 
## PickUpItemEntity 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.gameCompServer.GameComponentServer 
- Description 
ItemEntity picked up by a player 
- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerEntityId | str | The playerEntityId of the picker | 
| itemEntityId | str | The itemEntityId of the item to be picked up | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the pickup was successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.PickUpItemEntity(playerEntityId, itemEntityId) 
``` 

## PlayerDestoryBlock 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Use the tool in hand to destroy the block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| particle | int | Whether to enable the destruction particle effect, the default is on | 
| sendInv | bool | Whether to synchronize the server backpack information, the default is not synchronized. Because destroying blocks may cause changes in information such as the durability of handheld items, not synchronizing information may cause some subsequent logical anomalies. If a large number of blocks are destroyed, each synchronization will have performance problems. It is recommended that the previous call can set sendInv to False, and pass in sendInv to True when calling this function for the last time. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- The enchantment effect of the tool in hand will take effect, and the durability will be deducted at the same time 
- The ServerPlayerTryDestroyBlockEvent event will be triggered and can be canceled by this event 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) # Here playerId is the destroyer of the block 
comp.PlayerDestoryBlock((0, 5, 0), 1, False) 
comp.PlayerDestoryBlock((0, 6, 0), 1, True) 

# Turn off the destruction particle effect 
comp.PlayerDestoryBlock((0, 6, 0),0) 
``` 

## PlayerUseItemToEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

The player uses the item in his hand to use on a creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Biological entityId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- 1. It will trigger the PlayerInteractServerEvent event and can be canceled by this event; 2. This interface ignores distance, but cannot be used across dimensions, and requires the target area to be loaded 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) # Here playerId is the player using the item 
suc = comp.PlayerUseItemToEntity("-123456")
```



## PlayerUseItemToPos


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

The player uses an item at a certain coordinate 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Coordinate | 
| posType | int | The location of the item [ItemPosType enumeration](../../enumeration value/ItemPosType.md) | 
| slotPos | int | Slot, need to be set when getting INVENTORY and ARMOR, write 0 in other cases | 
| facing | int | Direction, see [Facing Enumeration](../../Enumeration Value/Facing.md) | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | Set Result | 

- Notes 
- When using projectiles, it will only return True in non-creative mode; if you want to use items on entities such as "armor stands", please use the PlayerUseItemToEntity interface; it can only be used for coordinates within 200 blocks around the player 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) # Here playerId is the player using the item 
comp.PlayerUseItemToPos((0, 5, 0), serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0, 1) 
``` 

## RemovePlayerMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Remove the motion device on the player 

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
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
motionComp.RemovePlayerMotion(mID) 
``` 

## SetPickUpArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's pickup range. After setting, the player's pickup range will be changed based on the original pickup range. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| area | tuple(float,float,float) | Pickup range, when (0, 0, 0) is passed in, it is considered to be canceled | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
# The player's pickup range increases by 5 grids in the positive and negative directions of the X axis, and increases by 3 grids in the positive and negative directions of the Z axis, and remains unchanged in the Y axis 
succ = comp.SetPickUpArea((5, 0, 3))
```



## SetPlayerAttackSpeedAmplifier 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's attack speed multiplier, 1.0 means normal level, 1.2 means speed reduction of 20%, 0.8 means speed gain of 20% 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| amplifier | float | Attack speed multiplier, range [0.5,2.0] | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This interface affects the global attack CD set by the interface [SetHurtCD] (../world/game rules.md#sethurtcd) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.SetPlayerAttackSpeedAmplifier(1.1) 
``` 

## SetPlayerExhaustionRatioByType 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the hunger consumption multiplier of a certain behavior of the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| type | int | Behavior enumeration [PlayerExhauseRatioType enumeration] (../../enumeration value/PlayerExhauseRatioType.md) | 
| ratio | float | multiplier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
jumpType = serverApi.GetMinecraftEnum().PlayerExhauseRatioType.JUMP 
ratio = comp.SetPlayerExhaustionRatioByType(jumpType, 20) 
``` 

## SetPlayerJumpable 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set whether the player can jump 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isJumpable | bool | Whether it can jump, True allows jumping, False prohibits jumping | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId)
comp.SetPlayerJumpable(False)
```



## SetPlayerMovable 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set whether the player is movable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isMovable | bool | Whether movable, True allows movement, False prohibits movement | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.SetPlayerMovable(False) 
``` 
## SetPlayerRespawnPos 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.playerCompServer.PlayerCompServer 
- Description 
Set the position and dimension of the player's resurrection 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of the resurrection point |

| dimensionId | int | The dimension of the respawn point. The default value is 0 (main world). Note 1: Dimension 21 is not available; Note 2: The respawn point cannot be set after the player dies (PlayerDieEvent). | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
suc = comp.SetPlayerRespawnPos((0, 4, 0), 0) 
``` 

## SetPlayerRideEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Set the player to ride a creature (or a boat or minecart) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str | Player id | 
| rideEntityId | str | RideEntity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Usually needs to be used with SetEntityRide and SetControl 
When the controlled entity has multiple positions and the developer wants to add multiple players, the first player added will be set as the controller by the engine by default 

- Example 

```python 
# Mount your mount 
import mod.server.extraServerApi as serverApi

comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetPlayerRideEntity(playerId,rideEntityId) 
``` 

## StartPlayerMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Start a motion device on the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| motionId | int | ID of a motion device to start | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to start successfully | 

- Notes 
- Since the player's motion device needs to be synchronized between the client and the server, please use the triggering of the [EntityMotionStartServerEvent](../../Event/Entity.md#EntityMotionStartServerEvent) event as the real start time. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
motionComp.StartPlayerMotion(mID) 
``` 

## StopEntityRiding 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Force the player to get off the mount.


- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if the player is currently riding and successfully dismounts, otherwise returns False | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
success = comp.StopEntityRiding() 
``` 

## StopPlayerMotion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorMotionCompServer.ActorMotionComponentServer 

- Description 

Stop a motion device on the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motionId | int | The ID of a motion device to be stopped | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the stop is successful | 

- Notes 
- Calling this interface will not trigger the event [EntityMotionStopServerEvent] (../../Event/Entity.md#EntityMotionStopServerEvent). 

- Example 

```python 
import mod.server.extraServerApi as serverApi

motionComp = serverApi.GetEngineCompFactory().CreateActorMotion(playerId) 
motionComp.StopPlayerMotion(mID) 
``` 

## isGliding 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Whether to fly with elytra 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to fly with elytra | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.isGliding() 
``` 
## isInWater 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.playerCompClient.PlayerCompClient 
- Description 
Whether in water 
- Parameters 

None 
- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it in water? | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.isInWater() 
``` 

## isMoving 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Is it walking? 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it walking? | 

- Example

```python
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId)
comp.isMoving()
```



## isRiding

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.playerCompClient.PlayerCompClient

- describe


Is it riding? 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it riding? | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.isRiding() 
``` 

## isSneaking 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get whether the player is in stealth state 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the current player is in stealth state | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId)

is_sneaking = comp.isSneaking() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Whether sneaking 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether sneaking | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.isSneaking() 
``` 

## isSprinting 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Is sprinting 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Is sprinting? | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.isSprinting() 
``` 

## isSwimming 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get whether the player is swimming. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the current player is in swimming state | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
is_swiming = comp.isSwimming() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.playerCompClient.PlayerCompClient 


- Description 

Swimming or not 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Swimming or not | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.isSwimming() 
``` 

## setMoving 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Set whether to walk, can only set local players (only applicable to mobile terminals) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.setMoving() 
``` 




## setSneaking 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Set whether to sneak, can only be set for local players (only applicable to mobile terminals) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.setSneaking() 
``` 

## setSprinting 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Set whether to sprint, can only be set for local players (only applicable to mobile devices) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful |


- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.setSprinting() 
``` 

## setUsingShield 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Activate shield state 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| flag | bool | True to use shield, False to cancel the use of shield | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 1 setting success, 0 setting failure, -1 player does not hold a shield | 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.setUsingShield(True) 
``` 

