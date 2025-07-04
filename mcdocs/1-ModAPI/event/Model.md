--- 
sidebarDepth: 1 
--- 
# Model 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AttackAnimBeginClientEvent](Model.md#attackanimbeginclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired when the attack action starts | 
| [AttackAnimBeginServerEvent](Model.md#attackanimbeginserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when the attack action starts | 
| [AttackAnimEndClientEvent](Model.md#attackanimendclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired when the attack action ends | 
| [AttackAnimEndServerEvent](Model.md#attackanimendserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when the attack action ends | 
| [JumpAnimBeginServerEvent](Model.md#jumpanimbeginserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when the jump action starts | 
| [WalkAnimBeginClientEvent](Model.md#walkanimbeginclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired when the walk action starts | 
| [WalkAnimBeginServerEvent](Model.md#walkanimbeginserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when the walk action starts | 
| [WalkAnimEndClientEvent](Model.md#walkanimendclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired when the walk action ends | 
| [WalkAnimEndServerEvent](Model.md#walkanimendserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when the walk action ends | 
# Model 

## AttackAnimBeginClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the attack action starts 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AttackAnimBeginServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 


Triggered when the attack action starts 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AttackAnimEndClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the attack action ends 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AttackAnimEndServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the attack action ends 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## JumpAnimBeginServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the jump action starts 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## WalkAnimBeginClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the walking action starts 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## WalkAnimBeginServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the walking action starts 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## WalkAnimEndClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the walking action ends 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| id | str | entity id | 

- Return value 

None 

- Remarks 
- This event will take effect only after using SetModel to replace the skeleton model 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## WalkAnimEndServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the walking action ends 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | entity id | 

- Return value 

None 

- Notes 
- This event will take effect only after using SetModel to replace the skeleton model 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

