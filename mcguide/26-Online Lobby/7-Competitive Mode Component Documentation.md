--- 
front: https://nie.res.netease.com/r/pic/20220408/06a1fb24-d76a-4d82-816c-96489966196c.png 
hard: Getting Started 
time: 15 minutes 
selection: true 
--- 
# Competitive Mode Component Documentation 
The competitive mode component provides MOD developers with unified competitive mode start and settlement notification events. By calling relevant APIs and listening to fixed events, the necessary parameters can be notified to the webhttpserver through the competitive component for score settlement. In addition, the escape penalty during the game is also notified to the webhttpserver by the competitive mode component. 

## MOD client access 

### API 
- SetArenaGamePlayerReady 

- Description 

Set the current player to be called when ready 

- Parameters 

No parameters 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.SetArenaGamePlayerReady() 
``` 

- Notes 

MOD developers must call this function 

- CancelArenaGamePlayerReady 

- Description 

Set the player to be called when canceling preparation 

- Parameters 

No parameters 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.CancelArenaGamePlayerReady()

``` 

- Notes 

This interface is optional 

### Events 
- ClientArenaGameAllPlayerReadyEvent 

- Description 
The event sent by the competitive component to the client after all players of the current game are ready 

- Parameters 

No parameters 

- Notes 

MOD developers can choose to listen to this event to switch the game state, or ignore the game state switch controlled by the custom MOD server logic 

- ClientArenaGameFinishEvent 

- Description 

After the MOD developer calls the end API, the competitive component sends the end event to the client 

- Parameters 

Game results 

```python 
[ 
{ 
"camp_id": 1, 
"result": 1, 
"score": 100, 
"uid": [ 
uid1 
] 
		},
		{
			"camp_id": 2,
			"result": 2,
			"score": 50,
			"uid": [
				uid2
			]
		}
	]
	```


| Keywords | Data Type | Description | 
| --- | --- | --- | 
| camp_id | int | Camp, default is 0 if not distinguished, distinguish up to three camps 1, 2, 3 | 
| result | int | Game outcome: 0: draw, 1: win, 2: lose | 
| score | int | Score, pass null if not needed | 
| uid | list string array | Player id list | 

- Notes 

MOD developers can choose to listen to this event to obtain game results, or obtain results from the MOD server through custom events. After receiving this event, the competitive component server will automatically make a remote call to close the current game after 5 seconds. 

## MOD server access 

### API 

- SetArenaGameResult 

- Description 

Called when the current game ends, the developer passes in the final result 

- Parameters 

| Keywords | Data type | Description | 
| --- | --- | ---| 
| camp_id | int | Camp, default is 0 if not distinguished, distinguish up to three camps 1, 2, 3 | 
| result | int | Game win or loss: 0: draw, 1: win, 2: lose | 
| score | int | Score, pass null if not needed | 
| uid | list string array | Player id list | 

- Example 

```python 
resList = [ 
{ 
"camp_id": 1, 
"result": 1, 
"score": 100, 
"uid": [ 
uid1 
] 
			},
			{
				"camp_id": 2,
				"result": 2,
				"score": 50,
				"uid": [
					uid2
				]

} 
] 
serverApi.SetArenaGameResult(resList) 
``` 

- Notes 

- Score settings: 

- If you specify a custom score, you need to set the score for each item. 
- If you use the default score of the ranking system, the value of each item `score` needs to be set to None. 
- If `result` is set to 2, that is, it is set to lose, the time-sharing needs to pass the score minus the score `score` positive number instead of a negative number 
- MOD developers must call this function to set the game result. 

### Event 

- ServerArenaGameAllPlayerReadyEvent 

- Description 

The event sent by the competitive component to the server after all players in the current game are ready 

- Parameters 

No parameters 

- Notes 

MOD developers can choose to listen to this event to switch the game state, or ignore the game state switch controlled by the custom MOD server logic 

- ServerArenaGamePlayerReconnectSuccessEvent 

- Description 

When a player reconnects after being disconnected, this event is triggered if there is no timeout 

- Parameters 

| Keywords | Data Type | Description | 
| --- | --- | --- | 
| playerId | str | player's entityId | 
| uid | str | player's uid | 

- Notes 
MOD developers can choose to listen to this event to determine the player's reconnection status. 

- ServerArenaGamePlayerReconnectFailedEvent 

- Description 

When a player reconnects after being disconnected, this event is triggered if the timeout occurs.


- Parameters 

| Keywords | Data Type | Description | 
| --- | --- | --- | 
| playerId | str | player's entityId | 
| uid | str | player's uid | 

- Notes 

MOD developers can choose to listen to this event. If a player reconnects after a timeout, the competitive component will send a message to force the player to quit the game. 

- ServerSetGameResultFailed 

- Description 

This event is triggered when the developer sets a result failure 

- Parameters 

| Keywords | Data Type | Description | 
| :--- | :--- | :--- | 
| rcode | int | Error Code | 
| msg | str | Error Message | 
| detail | str | Cause of Error | 

- Notes 

The meaning of the error code and the corresponding detailed information are as follows: 

> **4**: The parameter is empty, a parameter is missing 
> 
> **12**: Parameter error, see details for details 
> teams must be an array 
> 
> ​ team parameter is missing 
> 
> ​ result is out of range {sent result value} (0: draw, 1: win, 2: fail) 
> 
> ​ camp_id is out of range camp_id:{sent camp_id} camp_num:{number of camps} (The number of camps is 0, camp_id can only be 0, the number of camps is greater than 0, it is num, camp_id range [1,num]) 
> 
> ​ uid must be an array 
> 
> ​ uid is not a room member room_id:{room id} user_id:{player id} 
> 
> **13**: Operation failed, see details 
> 
> The room cannot find {room id} 
> 
> The room member {room id} cannot be found

> 
> Component information {component id} not found 
> 
> Matching status error room_id:{room id} user_id:{player id} state:{matching status} (to prevent duplicate settlement) 
> 
> Settlement failed 
> 
> **12028**: Room key calculation error 
