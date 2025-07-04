--- 
sidebarDepth: 1 
--- 
# Time 

## GetLocalDoDayNightCycle 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Gets whether the dimension has day and night cycles turned on 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to turn on day and night cycles | 

- Notes 
- When the dimension uses the local time rule, it returns the dimension's own day and night change rule; when it is not used, it returns the global day and night change rule 
- For "local time rule", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.GetLocalDoDayNightCycle(3) 
``` 

## GetLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Get the time of the dimension


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Time, in frames, indicating the time since the archive was created, not the time in the current game day. One game day in mc is equivalent to 20 minutes in reality, that is, 24000 frames | 

- Notes 
- When the dimension uses the local time rule, the local time is returned; when it is not used, the global time is returned 
- For "local time rule", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
# Total number of frames passed since the start of the game 
passedTime = comp.GetLocalTime(3) 
# Number of frames in the current game day 
timeOfDay = passedTime % 24000 
# Number of game days passed since the start of the game 
day = passedTime / 24000 
``` 

## GetTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.timeCompServer.TimeComponentServer 

- Description 

Get the current world time 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| int | The current time, in frames, represents the time since the save was created, not the time in the current game day. One game day in mc is equivalent to 20 minutes in reality, that is, 24000 frames | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTime(levelId) 
# Total number of frames since the start of the game 
passedTime = comp.GetTime() 
# Number of frames in the current game day 
timeOfDay = passedTime % 24000 
# Number of game days since the start of the game 
day = passedTime / 24000 
``` 

## GetUseLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Get whether a dimension is set to use the local time rule 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to use local time rules | 

- Remarks 
- For "local time rules", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.GetUseLocalTime(3) 
``` 




## SetLocalDoDayNightCycle 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Sets whether the dimension using local time rules turns on the day and night cycle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 
| value | bool | Turn on the day and night cycle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Can only be set for dimensions using local time rules 
- For "local time rules", see [SetUseLocalTime](#setuselocaltime) 
- In the PC development kit, you can type `dmtime cycle on` or `dmtime cycle off` in the chat bar to test turning on and off the day and night cycle of the current dimension 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.SetLocalDoDayNightCycle(3, False) 
``` 

## SetLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Set the time of the dimension using the local time rule 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| time | int | Time, in frames. Indicates the time since the archive was created, not the time in the current game day. One game day in MC is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The game has the concept of days, which needs to be considered when using it. You can also use [SetLocalTimeOfDay](#setlocaltimeofday) to set the time of day without calculating the number of days. 
- Can only be set if the dimension uses local time rules 
- For "local time rules", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
# Get the current time 
passedTime = comp.GetLocalTime(3) 
# Get the current day 
day = passedTime / 24000 
# Set to noon of the day 
comp.SetLocalTime(3, day * 24000 + 6000) 
# Set to sunrise of the next day 
comp.SetLocalTime(3, (day + 1) * 24000 + 0) 
``` 

## SetLocalTimeOfDay 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Set the time of day for the dimension using the local time rule 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | dimension id |

| timeOfDay | int | Time, in frames, representing the time of day in the game, ranging from 0 to 24000. One game day in MC is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The specific logic is the same as the time instruction. If timeOfDay is later than the current time, it is set to the timeOfDay of the current day; if timeOfDay is earlier than the current time, it is set to the timeOfDay of the next day. 
- In the PC development kit, you can type `dmtime time <int: frame number>` in the chat bar to test setting the local time of the current dimension. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
# Set to noon 
comp.SetLocalTimeOfDay(3, 6000) 
``` 

## SetTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.timeCompServer.TimeComponentServer 

- Description 

Set the current world time 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| time | int | Time, in frames, indicating the time since the archive was created, not the time in the current game day. One game day in mc is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The game has the concept of days, which needs to be considered when using it. You can also directly use [SetTimeOfDay](#settimeofday) to set the time of day without calculating the number of days. 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTime(levelId) 
# Get the current time 
passedTime = comp.GetTime() 
# Get the current day 
day = passedTime / 24000 
# Set to noon of the day 
comp.SetTime(day * 24000 + 6000) 
# Set to sunrise of the next day 
comp.SetTime((day + 1) * 24000 + 0) 
``` 

## SetTimeOfDay 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.timeCompServer.TimeComponentServer 

- Description 

Set the time of the day in the current world 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| timeOfDay | int | Time, in frames, represents the time in a game day, ranging from 0 to 24000. One game day in mc is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The specific logic is the same as the time instruction. If timeOfDay is later than the current time, it is set to the timeOfDay of the current day; if timeOfDay is earlier than the current time, it is set to the timeOfDay of the next day 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTime(levelId) 
# Set to noon 
comp.SetTimeOfDay(6000) 
``` 




## SetUseLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Let a dimension have its own local time rules. After turning it on, the dimension can have different time and day and night rules from other dimensions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 
| value | bool | Whether to enable local time rules | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set successfully | 

- Notes 
- We've added the concept of "local time rules" to the Overworld and custom dimensions. Previously, all dimensions shared a "global time", meaning that when you set the time or dodaynightcycle rules, it would apply to all dimensions. 
Now, you can set a dimension to use local time rules, and set its time (see [SetLocalTime](#setlocaltime)) and dodaynightcycle rules (see [SetLocalDoDayNightCycle](#setlocaldodaynightcycle)) separately. 
In the following, we'll refer to dimensions that use local time rules as "local dimensions", and dimensions that use global time rules as "global dimensions". By default, all dimensions are global dimensions. 
The vanilla time command, the gamerule dodaylightcycle command and the setting to turn on the day-night cycle, and the daylock command and the setting to turn on daylight cycle, will not apply to local dimensions. 
When there are both local and global dimensions in the world, there are only two situations where you can sleep to skip the night: 
1. All players are sleeping in the global dimension. This will jump the global time to the next morning. 
2. All players sleep in the same local dimension. At this time, the time of the local dimension will jump to the next morning. 
- When the local time rule is enabled, the global time and day and night change rules are inherited by default 
- The time rule is invalid for the original Nether and the End. These two dimensions are always dark and there is no day and night change 
- It is recommended to call it uniformly when the game starts 
- In the PC development kit, you can type `dmtime on` or `dmtime off` in the chat bar to test turning on and off the local time of the current dimension 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.SetUseLocalTime(3, True) 
``` 

