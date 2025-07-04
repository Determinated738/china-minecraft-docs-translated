--- 
sidebarDepth: 1 
--- 
# Properties 

## ChangeEntityDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Teleport entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension id, 0-Main world; 1-Nether; 2-The End; or other custom dimensions | 
| pos | tuple(int,int,int) | Coordinates of the teleportation. If None is entered, the portal of the target dimension is selected as the destination first, and the destination is determined by the dimension coordinate mapping logic | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This interface cannot be used for players. Players should use ChangePlayerDimension 
- This interface can only be used to transfer to another dimension. If the entity is already in this dimension, it will return False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(entityId) 
comp.ChangeEntityDimension(0, (0,4,0)) 
``` 

## GetAttrMaxValue 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span>
method in mod.server.component.attrCompServer.AttrCompServer


- Description 

Get the maximum value of the engine attribute of an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| type | int | [AttrType enumeration](../../enumeration value/AttrType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Attribute value result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.GetAttrMaxValue(serverApi.GetMinecraftEnum().AttrType.HEALTH) 
``` 
### Client interface 
<span id="c0"></span> 
method in mod.client.component.attrCompClient.AttrCompClient 

- Description 

Get the maximum value of attributes, including health, hunger, movement speed, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| type | int | [AttrType enumeration](../../enumeration value/AttrType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | property value result | 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.GetAttrMaxValue(clientApi.GetMinecraftEnum().AttrType.HEALTH) 
``` 

## GetAttrValue 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Get the engine attributes of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| attrType | int | [AttrType enumeration](../../enumeration value/AttrType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Attribute result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.GetAttrValue(serverApi.GetMinecraftEnum().AttrType.HEALTH) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.attrCompClient.AttrCompClient

- describe


Get attribute values, including health, hunger, and movement speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| attrType | int | [AttrType enumeration](../../enumeration value/AttrType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Attribute result | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.GetAttrValue(clientApi.GetMinecraftEnum().AttrType.HEALTH) 
``` 

## GetBodyRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.rotCompClient.RotComponentClient 

- Description 

Get the body angle of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | The body's angle around the vertical direction, in degrees. If there is no body, it returns 0 | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateRot(entityId)
y = comp.GetBodyRot()

``` 

## GetCurrentAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.breathCompServer.BreathCompServer 

- Description 

Current oxygen reserve value of organism 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current oxygen reserve value of organism | 

- Remarks 
- Note: This value returns the number of logical frames supported by the current oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(entityId) 
comp.GetCurrentAirSupply() 
``` 
## GetEntityDimensionId 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.dimensionCompServer.DimensionCompServer 
- Description 
Get the dimension of the entity 
- Parameters 
None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Dimension id, 0-Main world; 1-Nether; 2-The End; or other custom dimensions | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(entityId) 
comp.GetEntityDimensionId() 
``` 

## GetEntityOwner 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorOwnerCompServer.ActorOwnerComponentServer 

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
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateActorOwner(entityId) 
ownerId = comp.GetEntityOwner() 
``` 

## GetFootPos 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span>


### Server Interface 

<span id="s0"></span> 
method in mod.server.component.posCompServer.PosComponentServer 

- Description 

Get the location of the entity's foot 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Location Information | 

- Notes 
- Get the location of the entity's foot (except when sleeping) 
- For similar interfaces, see [Get Entity Position](#getpos) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePos(entityId) 
entityFootPos = comp.GetFootPos() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.posCompClient.PosComponentClient 

- Description 

Get the location of the entity's foot 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| tuple(float,float,float) | Position information | 

- Notes 
- Get the position of the entity's feet (except when sleeping) 
- For similar interfaces, see [Get entity position](#getpos) 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePos(entityId) 
#Get position: 
entityFootPos = comp.GetFootPos() 
``` 

## GetGravity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gravityCompServer.GravityComponentServer 

- Description 

Get the entity's gravity factor. When the creature's gravity factor is 0, the world's gravity factor is applied. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Gravity factor | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGravity(entityId) 
comp.GetGravity() 
``` 

## GetMaxAirSupply 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.breathCompServer.BreathCompServer 

- Description 

Get the maximum oxygen reserve value of the organism 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Maximum oxygen reserve value | 

- Remarks 
- Note: This value returns the maximum oxygen reserve supported logical frame number = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(entityId) 
comp.GetMaxAirSupply() 
``` 
## GetName 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.nameCompServer.NameComponentServer 
- Description 
Get the custom name of the creature, that is, the name set by the name tag or SetName interface 
- Parameters 

None 
- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Custom name of the creature |


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateName(entityId) 
comp.GetName() 
``` 

## GetPos 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.posCompServer.PosComponentServer 

- Description 

Get the entity position 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Position information | 

- Notes 
- For non-players, the position of the sole of the foot is obtained 
- For players, if they are walking, standing, swimming, sneaking, or gliding, the position obtained is 1.62 higher than the sole of the foot; if they are sleeping, the position obtained is 0.2 higher than the lowest position 
- Similar interfaces include [GetFootPos](#getfootpos), which obtains the position of the sole of the foot for any entity 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePos(entityId) 
comp.GetPos() 
``` 

### Client interface


<span id="c0"></span> 
method in mod.client.component.posCompClient.PosComponentClient 

- Description 

Get the entity position 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Entity coordinates | 

- Notes 
- For non-players, the position of the sole of the foot is obtained 
- For players, if they are walking, standing, swimming, sneaking, or gliding, the position obtained is 1.62 higher than the sole of the foot. If they are sleeping, the position obtained is 0.2 higher than the lowest position 
- Similar interfaces include [GetFootPos](#getfootpos), which obtains the position of the sole of the foot for any entity 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePos(entityId) 
#Get position: 
entityPos = comp.GetPos() 
``` 

## GetRot 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.rotCompServer.RotComponentServer 

- Description 

Get the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction. After obtaining the angle, the GetDirFromRot interface can be used to convert it into a unit vector of the direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | (up and down angle, left and right angle) The unit is angle instead of radian | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRot(entityId) 
comp.GetRot() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.rotCompClient.RotComponentClient 

- Description 

Get the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction. After obtaining the angle, the GetDirFromRot interface can be used to convert it into a unit vector of the direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Pitch angle and rotation angle around the vertical direction, the unit is degree | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateRot(entityId) 
x, y = comp.GetRot() 
``` 

## GetSize 

<span style="display:inline;color:#ff5555">Server</span> 


method in mod.server.component.collisionBoxCompServer.CollisionBoxComponentServer 

- Description 

Get the bounding box of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Bounding box size | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCollisionBox(entityId) 
comp.GetSize() 
``` 

## GetTypeFamily 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Get the creature behavior package field type_family 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | type_family list, for example ['cow', 'mob'] | 

- Example 

```python 
import mod.server.extraServerApi as serverApi

comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.GetTypeFamily() 
``` 
## GetUnitBubbleAirSupply 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.breathCompServer.BreathCompServer 
- Description 

Oxygen reserve value corresponding to the number of bubbles per unit 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Oxygen reserve value corresponding to the number of bubbles per unit | 

- Example 
```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(levelId) 
comp.GetUnitBubbleAirSupply() 
``` 
## IsConsumingAirSupply 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.breathCompServer.BreathCompServer 
- Description 
Get whether the organism is currently consuming oxygen 
- Parameters 
None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether oxygen is consumed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(entityId) 
comp.IsConsumingAirSupply() 
``` 

## LockLocalPlayerRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.rotCompClient.RotComponentClient 

- Description 

Lock the head angle of the local player when detaching the camera 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| lock | bool | Pass True to lock the local player's head angle<br> Pass False to unlock the local player's head angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Setting successful<br>False: Setting failed | 

- Notes 
- Only localplayer can be set 
- The head angle will be reset when the player respawns or switches dimensions 
- When the local player's head angle is locked, the camera can be rotated in the first-person perspective, but the player's head angle will not change. The next time you switch to the first-person perspective, the camera angle will still be the locked angle 
- After locking the local player's head angle, the player's head angle will try to get close to the locked angle when rowing. If it cannot turn to that angle, it will look left or right (depending on which side is closer to the target angle) 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Detach camera 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId)

comp.DepartCamera() 
# Lock the head angle of the local player 
comp = clientApi.GetEngineCompFactory().CreateRot(entityId) 
comp.LockLocalPlayerRot(True) 
``` 

## SetAttrMaxValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Set the maximum value of the engine attribute of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| type | int | [AttrType enumeration](../../enumeration value/AttrType.md) | 
| value | float | Attribute value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- The setting interface does not support ABSORPTION 
- When setting properties, you need to pay attention to whether it exceeds the original value range. If the set value exceeds the original value range, False is returned. 
- The maximum saturation set cannot exceed the current hunger value; after eating food, the maximum saturation will be modified by the original game mechanism 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.SetAttrMaxValue(serverApi.GetMinecraftEnum().AttrType.SPEED,0.2) 
``` 

## SetAttrValue 

<span style="display:inline;color:#ff5555">Server</span> 


method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Set the engine attribute of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| attrType | int | [AttrType enumeration](../../enumeration value/AttrType.md) | 
| value | float | Attribute value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- The setting interface does not support ABSORPTION 
- When setting attributes, you need to pay attention to whether it exceeds the value range of the original version or the value range of the current attribute. If the set value exceeds the range of the original value, False is returned. 
- If it exceeds the current maximum value of the attribute, you need to call the SetAttrMaxValue interface to expand the maximum value of the attribute first. Otherwise, if the set value is too large, it will be truncated to the maximum value because it exceeds the maximum value of the attribute. If the set value is lower than the current minimum value of the attribute, it will be set to the original minimum value. 
- For the original maximum or minimum value limits of basic attributes, see [AttrType Enumeration](../../Enumeration Value/AttrType.md) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
# If the set value exceeds the current maximum value of the attribute, you need to expand the maximum value of the attribute first, otherwise it will not take effect. 
comp.SetAttrMaxValue(serverApi.GetMinecraftEnum().AttrType.HEALTH, 30) 
comp.SetAttrValue(serverApi.GetMinecraftEnum().AttrType.HEALTH, 30) 
``` 
## SetCurrentAirSupply 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.breathCompServer.BreathCompServer 
- Description 
Set the oxygen reserve value of organisms 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| data | int | Set the current oxygen value of the creature | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Note: This value sets the logical frame number supported by the current oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(entityId) 
comp.SetCurrentAirSupply(300) 
``` 

## SetEntityLookAtPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rotCompServer.RotComponentServer 

- Description 

Set non-player entities to look at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetPos | tuple(float,float,float) | Target position to look at | 
| minTime | float | Minimum duration of gaze behavior, in seconds | 
| maxTime | float | Maximum duration of gaze behavior, in seconds, with a maximum value of 60<br>The actual duration of the behavior will be a random value between minTime and maxTime | 
| reject | bool | When performing the gaze behavior, is it forbidden to trigger other behaviors? True means to prohibit other behaviors. False means to allow other behaviors (the gaze behavior may not be obvious at this time) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True means success, False means failure | 

- Notes 
- Calling this interface will interrupt the ongoing behavior of the creature, and the creature will not look at the target position immediately, but will gradually look at the target position 
- Calling this interface for some entities that will not turn may return failure or success but no actual performance


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRot(entityId) 
# Set the entity to look at the position (0,78,0). The gaze behavior lasts for at least 2 seconds and at most 3 seconds. Other behaviors are prohibited during the gaze process. 
comp.SetEntityLookAtPos((0,78,0), 2, 3, True) 
``` 

## SetEntityOwner 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorOwnerCompServer.ActorOwnerComponentServer 

- Description 

Set the owner of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetId | str | Owner entity id, when None, set the entity owner to null | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True means the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateActorOwner(entityId) 
result = comp.SetEntityOwner(targetId) 
``` 

## SetFootPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.posCompServer.PosComponentServer

- Description 

Set the position of the entity's foot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| footPos | tuple(float,float,float) | The position of the entity's foot | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The behavior is the same as using the tp command, the entity will teleport to the target point 
- Calling this interface while in bed will return False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePos(entityId) 
comp.SetFootPos((0, 4, 0)) 
``` 
## SetGravity 
<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gravityCompServer.GravityComponentServer 

- Description 

Set the entity's gravity factor. When the creature's gravity factor is 0, the world's gravity factor is applied 

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
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGravity(entityId) 
comp.SetGravity(-0.08) 
``` 

## SetMaxAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.breathCompServer.BreathCompServer 

- Description 

Set the maximum oxygen reserve value of the organism 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| data | int | Set the maximum oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Remarks 
- Note: This value sets the maximum oxygen reserve supported logical frames = oxygen reserve value * logical frames (20 frames per second) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(entityId) 
comp.SetMaxAirSupply(400) 
``` 

## SetName 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.nameCompServer.NameComponentServer 

- Description 

Used to set a custom name for a creature, which has the same function as the original name tag. It is not supported by players and new wandering traders 

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
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateName(entityId) 
comp.SetName("new Name") 
``` 

## SetPersistent 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.attrCompServer.AttrCompServer 

- Description 

Sets the entity to not be [cleared](https://minecraft.fandom.com/zh/wiki/%E7%94%9F%E6%88%90#.E5.9F.BA.E5.B2.A9.E7.89.88_2) because it is too far away from the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| persistent | bool | When set to True, the entity will not be cleared | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | whether successful |


- Notes 
- When using CreateEngineEntityByTypeStr to create an entity with isNpc set to True, it will not be cleared by default 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAttr(entityId) 
comp.SetPersistent(True) 
``` 

## SetPlayerLookAtPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.rotCompClient.RotComponentClient 

- Description 

Set the local player to look at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetPos | tuple(float,float,float) | Target position to look at | 
| pitchStep | float | Angular velocity of rotation in pitch direction (per frame), minimum 0.2 | 
| yawStep | float | Angular velocity of rotation in yaw direction (per frame), minimum 0.2 | 
| blockInput | bool | Whether to block player operation when turning to target angle, default is True<br>True: Block player operation, the player cannot turn or move at this time<br>False: Do not block player operation, if the player moves or the camera turns at this time, the turn set by this interface will be interrupted | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True is successful, False is failed | 

- Notes 
- When the local player is not separated from the camera, calling this interface will cause the camera to look at the specified position together<br>When the local player is separated from the camera, calling this interface will only change the direction of the local player model 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateRot(localPlayerId) 
# Set the local player to look at the position (0,78,0) at a pitch velocity of 0.2 degrees per frame and a yaw velocity of 1 degree per frame, and shield the player's operation during the turning process 
comp.SetPlayerLookAtPos((0,78,0), 0.2, 1, True) 
```



## SetPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.posCompServer.PosComponentServer 

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
- For all types of entities, it sets the foot position, which is equivalent to [SetFootPos](#setfootpos) 
- Calling this interface when in bed will return False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePos(entityId) 
comp.SetPos((1,2,3)) 
``` 

## SetRecoverTotalAirSupplyTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.breathCompServer.BreathCompServer 

- Description 

Set the time to restore the maximum oxygen, in seconds 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| timeSec | float | Restore the maximum oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note: When the set maximum oxygen value is less than (timeSec*10), the value of the oxygen amount restored by the organism per frame is 0 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBreath(entityId) 
comp.SetRecoverTotalAirSupplyTime(10) 
``` 

## SetRot 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.rotCompServer.RotComponentServer 

- Description 

Set the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float) | (upper and lower angles, left and right angles) units are degrees instead of radians | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRot(entityId) 
comp.SetRot((30,0)) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.rotCompClient.RotComponentClient 

- Description 

Set the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction <a href="../../../../mcguide/20-玩法开发/10-基本概念/10-Vector3.html">MC Coordinate System Description</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float) | Pitch angle and rotation angle around the vertical direction, the unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- It is recommended to only use it to set local players. If you set other creatures, it will be overwritten by the creature's own behavior. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateRot(entityId) 
# Set to look up 45 degrees and face the positive direction of the world z axis 
comp.SetRot((-45, 0)) 
``` 

## SetSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.collisionBoxCompServer.CollisionBoxComponentServer


- Description 

Set the bounding box of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| size | tuple(float,float) | The first digit indicates the width and length, the second digit indicates the height | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- For newly generated entities, it takes 5 frames before the bounding box size is set to take effect 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCollisionBox(entityId) 
comp.SetSize((2,3)) 
``` 

## isEntityInLava 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.attrCompClient.AttrCompClient 

- Description 

Whether the entity is in lava 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it is in lava, True means it is in lava, False means it is not in lava | 


- Notes 
- Only the entities loaded by the local client can be obtained whether they are in lava. If the entity is in other dimensions or not loaded (too far from the local player), the acquisition will fail. 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreateAttr(entityId) 
isInLava = comp.isEntityInLava() 
``` 

## isEntityOnGround 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.attrCompClient.AttrCompClient 

- Description 

Whether the entity is touching the ground 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it touches the ground, True means it touches the ground, False means it does not touch the ground | 

- Notes 
- When the client entity is just created, the engine calculation has not been completed. At this time, getting whether the entity is on the ground will return the default value True. You need to delay one frame to get the correct data 
- When the creature is in a riding state, such as a player riding a pig, it is also considered to be touching the ground 
- Only the entities loaded by the local client can be obtained. If the entity is in other dimensions or not loaded (too far away from the local player), the acquisition will fail 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreateAttr(entityId) 
isOnGound = comp.isEntityOnGround() 
``` 

