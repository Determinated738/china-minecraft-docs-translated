--- 
sidebarDepth: 1 
--- 
# Animation 

## PlayTpAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerAnimCompClient.PlayerAnimCompClient 

- Description 

Plays common player actions from a third-person perspective 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| anim | str | Action name, such as sneaking | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- Supported actions include: sneaking, sneaking_inverted, swimming, sleeping, holding_left, holding_right, crossbow_hold, crossbow_equipped, bow_equipped, upside_down, tp_attack 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerAnim(playerId) 
comp.PlayTpAnimation("sneaking") 
``` 

## StopAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerAnimCompClient.PlayerAnimCompClient 

- Description 

Stop playing common player actions 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| anim | str | Action name, such as sneaking | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerAnim(playerId) 
comp.StopAnimation("sneaking") 
``` 

