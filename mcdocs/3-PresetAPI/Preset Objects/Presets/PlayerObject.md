--- 
sidebarDepth: 1 
--- 
# PlayerObject 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
EntityObject <|-- PlayerObject 
link EntityObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E5%AE%9E%E4%BD%93%E5%AF%B9%E8%B1%A1EntityObject.html" 
SdkInterface <|-- EntityObject 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html" 
PlayerObject: Player object 
SdkInterface: SDK interface encapsulation 
SdkInterface: (click to jump) 
EntityObject: Entity object 
EntityObject: (click to jump) 
``` 

- Description 

PlayerObject (player object) is the base class for player object encapsulation, which provides object-oriented usage for entities. 

- Member variables 

None 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetPlayerId](#getplayerid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the player's preset player ID | 
| [IsLocalPlayer](#islocalplayer) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Determine whether the current player object is a local player | 
| [IsSneaking](#issneaking) | <span style="display:inline;color:#ff5555">Server</span> | Stealth or not | 
| [GetHunger](#gethunger) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's hunger and display it on the UI hunger progress bar. The initial value is 20, that is, each chicken leg represents 2 hunger points. **Saturation**: The player's current saturation, the initial value is 5, and the maximum value is always the player's current hunger. This value directly affects the player's **hunger**. <br>1) Increase method: Eat food. <br>2) Decrease method: Every time a **consumption event** is triggered, the value decreases by 1. If the value is not greater than 0, directly reduce the player's **hunger** by 1. | 
| [SetHunger](#sethunger) | <span style="display:inline;color:#ff5555">Server</span> | Sets the player's hunger level. | 
| [SetStepHeight](#setstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum step height that the player can climb when moving forward without jumping. The default value is 0.5625. 1 means that the player can climb one step. | 
| [GetStepHeight](#getstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Returns the maximum step height that the player can climb when moving forward without jumping. | 
| [ResetStepHeight](#resetstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Restore the engine default maximum step height that the player can climb when moving forward without jumping. | 
| [GetExp](#getexp) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's experience value at the current level | 
| [AddExp](#addexp) | <span style="display:inline;color:#ff5555">Server</span> | Add player experience points | 
| [GetTotalExp](#gettotalexp) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's total experience points | 
| [SetTotalExp](#settotalexp) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's total experience points |

| [IsFlying](#isflying) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the player is flying | 
| [ChangeFlyState](#changeflystate) | <span style="display:inline;color:#ff5555">Server</span> | Grant/cancel flying ability and enter flying/non-flying state | 
| [GetLevel](#getlevel) | <span style="display:inline;color:#ff5555">Server</span> | Get player level | 
| [AddLevel](#addlevel) | <span style="display:inline;color:#ff5555">Server</span> | Modify player level | 
| [SetPrefixAndSuffixName](#setprefixandsuffixname) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's prefix and suffix name | 
| [EnableKeepInventory](#enablekeepinventory) | <span style="display:inline;color:#ff5555">Server</span> | Set the player to not drop items when he dies | 
| [AddAnimation](#addanimation) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering animation | 
| [SetHealthLevel](#sethealthlevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's health threshold. When the hunger value is greater than or equal to the health threshold, the blood volume will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value of the original version is 18 | 
| [SetStarveLevel](#setstarvelevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's hunger threshold. When the hunger value is less than the hunger threshold, health will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value of the original version is 1 | 
| [SetNaturalStarve](#setnaturalstarve) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to enable the player's hunger blood loss. When the hunger value is less than the hunger critical value, the blood will be automatically deducted. It is effective when the hunger value is turned on and the hunger blood loss is turned on. The original version is enabled by default | 
| [SetStarveTick](#setstarvetick) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's hunger blood loss speed. When the hunger value is less than the hunger critical value, the blood will be automatically deducted. It is effective when the hunger value is turned on and the hunger blood loss is turned on | 
| [SetNaturalRegen](#setnaturalregen) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to enable the player's natural recovery | 
| [SetHealthTick](#sethealthtick) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's natural recovery speed | 
| [SetMaxExhaustionValue](#setmaxexhaustionvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's maximum exhaustion (maxExhaustion) | 
| [SetPickUpArea](#setpickuparea) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's pickup area | 
| [SetJumpable](#setjumpable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the player can jump | 
| [SetMovable](#setmovable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the player can move | 
| [AddAnimationController](#addanimationcontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering animation controller | 
| [AddAnimationIntoState](#addanimationintostate) | <span style="display:inline;color:#7575f9">Client</span> | Add animation in the state of the player's animation controller | 
| [AddGeometry](#addgeometry) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering geometry | 
| [AddParticleEffect](#addparticleeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add player special effect resources | 
| [AddRenderController](#addrendercontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering controller | 
| [AddRenderMaterial](#addrendermaterial) | <span style="display:inline;color:#7575f9">Client</span> | Add materials required for player rendering | 
| [AddSoundEffect](#addsoundeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add player sound effect resources | 
| [AddTexture](#addtexture) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering texture | 
| [SetSkin](#setskin) | <span style="display:inline;color:#7575f9">Client</span> | Replace the original custom skin | 
## GetPlayerId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Get the preset player ID of the player 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Player ID | 




## IsLocalPlayer 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Determine whether the current player object is a local player 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if it is a local player, otherwise returns False, and the server also returns False | 

## IsSneaking 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Is it sneaking 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it sneaking | 

- Example 

```python 
self.IsSneaking() 
``` 




## GetHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Get the player's hunger and display it on the UI hunger progress bar. The initial value is 20, that is, each chicken leg represents 2 hungers. **Saturation**: The player's current saturation, the initial value is 5, and the maximum value is always the player's current hunger. This value directly affects the player's **hunger**. <br>1) Increase method: Eat food. <br>2) Decrease method: Every time a **consumption event** is triggered, the value decreases by 1. If the value is not greater than 0, directly reduce the player's **hunger** by 1. 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| float | Player Hunger | 

- Example 

```python 
self.GetPlayerHunger(playerId) 
``` 

## SetHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's hunger. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Hunger level | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Example 

```python 
self.SetPlayerHunger(playerId, 10) 
``` 

## SetStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the maximum step height that the player can climb when moving forward without jumping. The default value is 0.5625. If it is 1, it means that the player can climb one step 

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
#If there is a two-block high block in front, the player can go up directly by pressing forward without jumping 
self.SetPlayerStepHeight(playerId, 2.0625) 
``` 

## GetStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Returns the maximum step height that the player can climb when moving forward without jumping 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Step height | 

## ResetStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Restore the engine default maximum step height that the player can climb when moving forward without jumping 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is the setting successful? | 

## GetExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Get the player's experience value at the current level 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isPercent | bool | Is it a percentage? | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Player experience value | 

- Notes 
- If the return percentage is set to False, the absolute value of the player's experience at the current level (not the current player's total experience value) is returned. 

- Example 

```python 
print(self.GetExp(False)) 
``` 

## AddExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Increase player experience 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| exp | int | Player experience, can be set to negative | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the set exp value is a negative number and exceeds the existing experience value of the current level, after calling the interface, the player's level will not decrease but the experience value will be set to the minimum value 

- Example 


```python 
self.AddExp(25) 
``` 

## GetTotalExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Get the total experience of the player 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Total experience, a positive integer. Returns -1 if the acquisition fails. | 

- Example 

```python 
print(self.GetTotalExp()) 
``` 

## SetTotalExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's total experience value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| exp | int | Total experience value, positive integer | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The level will be recalculated according to the total experience value. This interface can cause the level to change 
- Internal calculations use floating point numbers, and errors will occur when the value is large 

- Example 

```python 
self.SetTotalExp(25) 
``` 

## IsFlying 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Get whether the player is flying 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Yes False: No | 

## ChangeFlyState 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Grant/cancel the flying ability and enter the flying/non-flying state 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isFly | bool | Flight status, True: flight mode, False: normal walking mode | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: yes False: no | 

- Example 

```python 
self.ChangeFlyState(True) 
``` 

## GetLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Get the player level 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Player level | 

## AddLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 


Modify player level 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| level | int | Player level, can be set to negative | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.AddLevel(2) 
``` 

## SetPrefixAndSuffixName 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player prefix and suffix name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| prefix | str | Prefix content | 
| prefixColor | str | Prefix content color description, such as 'RED' | 
| suffix | str | Suffix content | 
| suffixColor | str | Suffix content color description, such as 'RED' | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python

self.SetPrefixAndSuffixName(playerId, "Red Team", 'RED', 'Tanshield', 'RED') 
``` 

## EnableKeepInventory 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player to not drop items when they die 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | bool | Whether to enable "keep inventory" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set successfully | 

- Example 

```python 
self.EnableKeepInventory(True) 
``` 

## AddAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Add player rendering animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| animationKey | str | Animation key |

| animationName | str | Animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.AddAnimation("move.arms", "animation.player.move.arms_custom") 
``` 

## SetHealthLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's health threshold. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The original default value is 18 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| healthLevel | int | Health threshold | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetHealthLevel(16) 
``` 

## SetStarveLevel 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's hunger threshold. When the hunger value is less than the hunger threshold, the health will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value of the original version is 1 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| starveLevel | int | Hunger threshold | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetStarveLevel(2)# If the hunger value is less than or equal to 2, it will enter the hungry blood loss state. By default, 1 blood point will be lost every 4 seconds 
``` 

## SetNaturalStarve 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set whether to enable the player's blood loss due to hunger. When the hunger value is less than the critical value of hunger, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are enabled. The original version is enabled by default. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | bool | True to enable, False to disable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
self.SetNaturalStarve(False)# # Turn off hunger blood loss. Even if the hunger value is less than the hunger threshold, the blood will not be deducted. 
``` 

## SetStarveTick 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's hunger blood loss speed. When the hunger value is less than the hunger threshold, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| starveTick | int | Hunger blood loss speed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetStarveTick(40) # Deduct 1 health point every 2 (40/20) seconds when hungry and losing blood 
``` 

## SetNaturalRegen 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set whether to enable natural recovery of the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| value | bool | True to enable, False to disable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetNaturalRegen(False) # Disable natural recovery. Even if the hunger value is greater than the health threshold, the health will not be restored. 
``` 

## SetHealthTick 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's natural recovery speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| healthTick | int | natural recovery speed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetHealthTick(40) # Recover 1 health point every 2 (40/20) seconds in natural recovery state 
``` 

## SetMaxExhaustionValue 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's maximum consumption (maxExhaustion) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Maximum consumption (maxExhaustion) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetMaxExhaustionValue(10.0) 
``` 

## SetPickUpArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set the player's pickup range 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| area | tuple(float,float,float) | Pickup range, passing in (0, 0, 0) is considered to cancel the setting | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
self.SetPickUpArea((5, 0, 3)) 
``` 

## SetJumpable 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

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
self.SetJumpable(False) 
``` 

## SetMovable 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Set whether the player is movable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| isMovable | bool | Whether it is movable, True allows movement, False prohibits movement | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetMovable(False) 
``` 

## AddAnimationController 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

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
| bool | Whether the setting is successful | 

- Example 

```python 
self.AddAnimationController("root", "controller.animation.player.root_custom") 
``` 

## AddAnimationIntoState 

<span style="display:inline;color:#7575f9">Client</span>


method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Add animation to the state of the player's animation controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| animationControllerName | str | Animation controller name | 
| stateName | str | Animation controller name | 
| animationName | str | Added animation name or animation controller name | 
| condition | str | Animation control expression | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
self.AddAnimationIntoState("root", "first_person", "first_person_attack_controller_new", "query.mod.index > 0") 
``` 

## AddGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Add player rendering geometry 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryKey | str | Rendering geometry key | 
| geometryName | str | Rendering geometry name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Success | 

- Example 

```python 
self.AddGeometry("default", "geometry.player.custom") 
``` 

## AddParticleEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Add player special effect resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effectKey | str | Special effect resource Key | 
| effectName | str | Special effect resource name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
self.AddParticleEffect("nectar_dripping", "minecraft:nectar_drip_particle") 
``` 

## AddRenderController 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 


Add player rendering controller 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| renderControllerName | str | Rendering controller name | 
| condition | str | Rendering controller condition | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
self.AddRenderController('custom_render_controller_name', 'query.mod.condition') 
``` 

## AddRenderMaterial 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Add materials required for player rendering 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| materialKey | str | Material key | 
| materialName | str | Material name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
self.AddRenderMaterial('custom_material_key', 'custom_material_name')

``` 

## AddSoundEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

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

- Example 

```python 
self.AddSoundEffect("sound_thunder", "ambient.weather.thunder") 
``` 

## AddTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Add player rendering texture 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryKey | str | Texture key |

| geometryName | str | Texture path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- RebuildPlayerRender needs to be called after calling this interface to take effect 

- Example 

```python 
self.AddTexture("default", "textures/misc/missing_texture") 
``` 

## SetSkin 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Player.PlayerObject.PlayerObject 

- Description 

Replace the original custom skin 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| skin | str | Texture path, relative to the current path of textures\models | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetSkin("kagura") 
``` 

