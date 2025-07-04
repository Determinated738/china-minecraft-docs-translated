--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Music 

## Introduction to MC Audio Management 

### Audio Engine 

MC's built-in audio management uses the industry-renowned audio engine [FMOD](https://www.fmod.com/). Audio management in MC is mainly done by encapsulating and calling FMOD's API through the **SoundSystemFMOD** class. 

### Game Audio 

#### Audio Definition 

In MC games, audio resource files are defined in *music_definitions.json* and *sound_definitions.json* in the `data\resource_packs\vanilla\sounds` directory. 

- *music_definitions.json*: defines the event name and delay information for triggering music 
- *sound_definitions.json*: defines the specific audio content, where the category field sets the category of the music 

#### *sound_definitions.json* single item introduction 

```json 
"record.13": { 
"max_distance": 64.0, 
"sounds": [ 
{ 
"name": "sounds/music/game/records/13", 
"stream": true, 
"volume": 0.5, 
"load_on_low_memory": true 
} 
] 
}, 
//... 
"music.game.endboss": { 
"category": "music", 
"sounds": [ 
{ 
"name": "sounds/music/game/end/boss", 
        "stream": true,
        "volume": 0.3,
        "load_on_low_memory": true
      }
    ]
  },
```


As shown in the code, each music item can be composed of multiple fields: 

- category: music classification, which can also be used as a folder directory for audio file classification 

- ui: whether it is a UI classification 

- music: whether it is a song classification 

- weather and other various classification values 

- min_distance: minimum distance, when choosing to play music at a certain location, the closest distance to trigger music playback 

- max_distance: maximum distance, same as above, the maximum distance to trigger music playback 

- sounds: music played, array definition 

- name: music file name 

- stream: whether it is a streaming file, when set to true, it can reduce memory usage, but only one audio file is allowed to be played at the same time, it is recommended to use larger BGM audio. 
- volume: volume 
- load_on_low_memory: whether to load in low memory usage 
#### *music_definitions.json* single item introduction 

```json 
{ 
"creative" : {//Scene of playing background music, creative here means playing in creative mode 
"event_name" : "music.game.creative",//Event name that triggers playing music 
"max_delay" : 180, 
"min_delay" : 60 
}, 
//...other definitions 
//...other definitions 
"endboss" : { 
"event_name" : "music.game.endboss", 
"max_delay" : 180, 
"min_delay" : 60 
}, 

``` 

As shown in the code, this json file is used to specify the game background music played in certain fixed scenes, including the following fields 
- event_name: the event name that triggers the corresponding music to be played, that is, the key name of each sound effect definition item in sound_definitions.json, such as music.game.endboss in the above text, and supports filling in custom key names 
- max_delay: the maximum delay when triggering the music playback event 
- min_delay: the minimum delay when triggering the music playback event 
- The key names supported by this json file (such as creative and endboss in the code) are fixed by the MC game and do not support customization. The key names supported by the current version are as follows: 

| Key name | Meaning | 
| --------------- | ---------- | 
| creative | Creative mode | 
| credits | Poem of the End | 
| crimson_forest | Crimson Forest | 
| dripstone_caves | Cave | 
| end | The End | 
| endboss | Ender Dragon | 
| frozen_peaks | Frozen Peaks | 
| game | Regular Game |

| grove | 
| hell | nether | 
| jagged_peaks | jagged_peaks | lush_caves ... Using items can also make sounds: 

- [Jukebox](https://minecraft-zh.gamepedia.com/index.php?title=%E5%94%B1%E7%89%87%E6%9C%BA&variant=zh): Plays all available music records in the game 
- [Music Box](https://minecraft-zh.gamepedia.com/index.php?title=%E9%9F%B3%E7%AC%A6%E7%9B%92&variant=zh): Makes sounds after receiving redstone signals. The sound produced by the music box depends on the material of the block below the music box. Each time a note box is used, the pitch of the next note it plays will be raised by half a step. According to the twelve-tone equal temperament, each instrument has a range of two octaves (24 semitones) to choose from. 

## MOD Custom Audio Settings 

There are three ways to use custom audio in a mod: addon data driver, Mod SDK interface and music command. All three methods require adding corresponding custom sound resource configurations in the Mod. 

### Audio resource settings 

1. Create a `sounds` folder in the `resource` directory 

2. Add `sound_definitions.json` 

- Modify/add a sound resource 
Refer to the settings of the file with the same name in the built-in resource directory of the MC game to set the audio file content in the corresponding situation. For example: 

```json 
{ 
"music.game.creative": { 
"category": "music", 
"sounds": [ 
{ 
"name": "sounds/music/game/creative/1", 
"stream": true, 
"volume": 0.1, 
"load_on_low_memory": true 
} 
]

} 
} 
``` 

> The above code sets the BGM content in the creative mode. This method is suitable for developers who want to inherit the original game music playback timing and want to change the music content, without additional code settings. 

- Dynamic loading settings: 

When developers use the ModSDK interface to play music (see <a href="../../../mcdocs/1-ModAPI/接口/音效.html##playcustommusic" rel="noopenner"> PlayCustomMusic interface </a> for details), we recommend using the `dy_load_list` field to set the music to be played (see [Audio dynamic loading settings](#Audio dynamic loading settings) below for details), because in this case, only the music will be loaded and played when it is used, reducing memory pressure. 

3. Add the corresponding music resource file to the directory in the new definition in the previous step json. 

For example: add 1.ogg file to `sounds\music\game\` 

**Note**: The current version of music files supports three formats: `.fsb`, `.ogg`, and `.wav`. The commonly used mp3 format is not supported. 

### Playback settings 

1. Playback via Mod SDK interface: Use the Mod SDK interface to control the playback of music. A brief introduction is given below. For details, see the detailed introduction of the customAudio component interface in the MOD SDK 

> DisableOriginMusic to block native music 
> PlayGlobalCustomMusic to play global custom background music, with the highest priority 
> PlayCustomMusic to play music at a specified location 

2. Playback via Music command: Sound effects can be called via the native music command of MC: see [Music Command Wiki](https://minecraft.fandom.com/zh/wiki/%E5%91%BD%E4%BB%A4/music) for details. The music command supports all sound effects defined in sound_definitions.json, including native sound effect keys and custom sound effect keys, such as music.game.custom1. 

### Audio dynamic loading settings 

By default, all audio is loaded at startup. When there are many audio resources in the mod, it is recommended to control the number of audios loaded at startup. 

The control method is as shown in `sound_definitions.json` introduced in this article. Add the key value *dy_load_list* in the json file, and the corresponding value is list. The sounds recorded in this list are not loaded by default when the game starts, and will only be loaded when they are used. It can effectively suppress the crash at startup caused by excessive memory occupation by audio resources. 

```json 
{ 
"dy_load_list":[ 
"sounds/music/game/creative/1", 
"sounds/customSound/2", 
"sounds/customSound/3", 
"sounds/customSound/4", 
"sounds/customSound/5" 
], 
# other code 
``` 

The current engine already supports **LRU management** (a memory management algorithm) of audio, so when there are many audio resources, the engine will dynamically control the memory resources occupied by audio. 

## Sample DEMO Introduction 

The sample demo is [customMusicDemo](../13-Module SDK Programming/60-Demo Example.md#customMusicDemo), which mainly shows the two settings of the current custom music: data-driven addon form and mod sdk interface call form. There are two methods of interface call, one is the playback of the globally unique BGM, and the other is the playback of the sound effect at a specified position.


### Replace BGM 

In ``sound_definitions.json`, the mod replaces the BGM in the original creative mode 

```json 
"music.game.creative": { 
"category": "music", 
"sounds": [ 
{ 
"name": "sounds/music/game/creative/1", 
"stream": true, 
"volume": 0.1, 
"load_on_low_memory": true 
} 

] 
}, 
``` 

### Switch BGM according to position changes 

In DEMO, if the player enters 

> ​ self.global0Area =[(0,0), (5,5)] # That is, the x and z coordinates of the smallest point are (0,0) and the largest point is (5,5) 
>​ self.global1Area =[(-5,-5), (0,0)] 

In the two areas, `PlayGlobalCustomMusic` will be called to play the corresponding BGM. Before calling this function, `DisableOriginMusic` needs to be called to stop playing the built-in BGM. 

### Play music at a specified location 

When the player approaches the circular area shown below 

> ​ self.campPoint = (20,4,20) 
> 
> ​ self.campRadius = 5 

`PlayCustomMusic` will be called to play the corresponding music in the camp. The definition of the music is as follows 

```json 
"music.custom": { 
"min_distance": 0.0, 
"max_distance": 5.0, 
"sounds": [ 
{ 
"name": "sounds/customSound/4", 
"pitch": 1, 
"volume": 1,

"load_on_low_memory": true, 
"stream": true 
} 
] 
} 
``` 

You can specify the minimum and maximum playback range. The music at this time has a 3D effect, and the volume changes according to the distance. 

