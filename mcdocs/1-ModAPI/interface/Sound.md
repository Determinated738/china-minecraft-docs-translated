--- 
sidebarDepth: 1 
--- 
# Sound Effects 

# Index 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [DisableOriginMusic](sound effects.md#disableoriginmusic) | <span style="display:inline;color:#7575f9">Client</span> | Stop native background music | 
| [PlayCustomMusic](sound effects.md#playcustommusic) | <span style="display:inline;color:#7575f9">Client</span> | Play scene sound effects, including original sound effects and custom sound effects | 
| [PlayGlobalCustomMusic](sound effects.md#playglobalcustommusic) | <span style="display:inline;color:#7575f9">Client</span> | Play background music | 
| [SetCustomMusicLoop](sound.md#setcustommusicloop) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the specified music is played in a loop, including scene sound effects and background music | 
| [SetCustomMusicLoopById](sound.md#setcustommusicloopbyid) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the specified music is played in a loop | 
| [StopCustomMusic](sound.md#stopcustommusic) | <span style="display:inline;color:#7575f9">Client</span> | Stop sound effects, including scene sound effects and background music, and trigger OnMusicStopClientEvent event according to fadeOutTime | 
| [StopCustomMusicById](sound.md#stopcustommusicbyid) | <span style="display:inline;color:#7575f9">Client</span> | Stop scene sound effects | 

## DisableOriginMusic 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 

- Description 

Stop native background music 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| disable | bool | True means stop, False means resume | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
comp.DisableOriginMusic(True) 
``` 




## PlayCustomMusic 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 

- Description 

Play scene sound effects, including original sound effects and custom sound effects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Sound effect name | 
| pos | tuple(float,float,float) | Play position | 
| volume | float | Volume ratio, range 0-1, multiplied by the volume in json to get the actual volume played in the game | 
| pitch | float | Play speed, range 0-256, 1 means original speed, can be modified from the json file | 
| loop | bool | Whether to play in a loop | 
| entityId | str | Bound entity id, default is None, if there is a bound entity, the pos parameter is the coordinate relative to the entity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Music playback id, can be used to control the stop and loop of music | 

- Notes 
- When there is an error in playing music, the corresponding error id will be returned 
| Error | Error description | 
| -- | -- | 
| -1 | Unable to play sound effects on the server | 
| -2 | Play position error | 
| -3 | Background music with the same name is already playing | 
| -4 | Playback failed | 
| -5 | Bound entity does not exist | 
| -6 | **If the position is greater than 16 grids away from the local player, skip the sound effect playback** (the sound effects of the bound entity are not subject to this restriction) | 
- When background music is playing, please do not play scene sound effects with the same name. 
- For larger music, please set load_on_low_memory and stream to true. 
- This interface triggers [PlaySoundClientEvent](../event/soundeffect.md#playsoundclientevent) 
- The sound_definitions.json configuration corresponding to the example: 
```json 
{ 
"sound001": { 
"min_distance": 0, 
"max_distance": 20.0, 
"sounds": [ 
{ 
"name": "sounds/testaudio/largeBlast1",

"load_on_low_memory": true, 
"stream": true, 
"pitch": 1, 
"volume": 1 
} 
] 
} 
} 
``` 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
musicId = comp.PlayCustomMusic("music.global0", (1,1,1), 1, 1, False, None) 
``` 

## PlayGlobalCustomMusic 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 

- Description 

Play background music 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Music name | 
| volume | float | Volume, range 0-1, multiplied by volume in json to get the actual volume played in the game | 
| loop | bool | Whether to play in a loop | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the playback is successful | 

- Notes 
- Only one background music can be played at a time. When playing background music, the currently playing music will be stopped. This rule also includes the original background music, so in order to avoid the original background music overwriting the custom background music, it is recommended to use DisableOriginMusic to block the original background music first. 
- Background music has a higher priority than scene sound effects. When background music is playing, scene sound effects with the same name will fail to play. 
- The playback speed of background music needs to be modified in the configuration json. 
- For larger background music, please set load_on_low_memory and stream to true. 
- Background music needs to be defined as category music in json.

- This interface triggers [PlayMusicClientEvent](../event/soundeffect.md#playmusicclientevent) 
- The sound_definitions.json configuration corresponding to the example: 
```json 
{ 
"Gsound001": { 
"category": "music", 
"sounds": [ 
{ 
"name": "sounds/testaudio/Music001", 
"load_on_low_memory": true, 
"stream": true, 
"pitch": 1, 
"volume": 1 
} 
] 
} 
} 
``` 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
comp.PlayGlobalCustomMusic("Gsound001", 1, False) 
``` 
## SetCustomMusicLoop 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 
- Description 
Set whether the specified music is played in a loop, including scene sound effects and background music 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Music name | 
| loop | bool | True to loop, False to stop looping, and stopping will continue until the playback ends | 
- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the stop is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
comp.SetCustomMusicLoop("soundName", True) 
``` 

## SetCustomMusicLoopById 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 

- Description 

Set whether the specified music is played in a loop 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| musicId | str | Music id, play the specified music to get the music id | 
| loop | bool | True to loop, False to stop the loop, the stop will continue until the end of this playback | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the stop is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
musicId = comp.PlayCustomMusic("sound001", (1,1,1), 1, 1, False, False) 
comp.SetCustomMusicLoopById(musicId, True) 
``` 

## StopCustomMusic 

<span style="display:inline;color:#7575f9">Client</span> 


method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 

- Description 

Stops sound effects, including scene sound effects and background music, and triggers the OnMusicStopClientEvent event based on fadeOutTime 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| name | str | Music name | 
| fadeOutTime | float | Stop fade-out time, in seconds. If the remaining time is less than the fade-out time, the remaining time will prevail | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the stop is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
comp.StopCustomMusic("music.global0", 0) 
``` 
## StopCustomMusicById 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.audioCustomCompClient.AudioCustomComponentClient 
- Description 

Stop scene sound effects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| musicId | str | Music id, the music id obtained by playing the specified music | 
| fadeOutTime | float | Stop fade-out time, in seconds | 
- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the stop is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCustomAudio(levelId) 
musicId = comp.PlayCustomMusic("sound001", (1,1,1), 1, 1, False, False) 
comp.StopCustomMusicById(musicId, 0) 
``` 

