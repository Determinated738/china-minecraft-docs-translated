--- 
sidebarDepth: 1 
--- 
# Sound Effects 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [OnMusicStopClientEvent](sound effect.md#onmusicstopclientevent) | <span style="display:inline;color:#7575f9">Client</span> | When the music stops, when the player calls StopCustomMusic to stop the custom background music, this event will be triggered | 
| [PlayMusicClientEvent](sound effect.md#playmusicclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when playing background music | 
| [PlaySoundClientEvent](sound effect.md#playsoundclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when playing scene sound effects or UI sound effects | 
# Sound effects 

## OnMusicStopClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

When the music stops, when the player calls StopCustomMusic to stop the custom background music, this event will be triggered 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| musicName | str | Music name | 

- Return value 

None 

## PlayMusicClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when background music is played 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | That is, event_name in sounds/music_definitions.json in the resource package, and corresponds to the key in sounds/sound_definitions.json | 
| cancel | bool | Set to True to block the sound effect playback | 

- Return value


None 

## PlaySoundClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when playing scene sound effects or UI sound effects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | The key in sounds/sound_definitions.json in the resource pack | 
| pos | tuple(float,float,float) | The position where the sound effect is played. UI sound effect is (0,0,0) | 
| volume | float | volume, range is 0-1 | 
| pitch | float | playback speed, normal speed is 1 | 
| cancel | bool | Set to True to block the playback of this sound effect | 

- Return value 

None 

