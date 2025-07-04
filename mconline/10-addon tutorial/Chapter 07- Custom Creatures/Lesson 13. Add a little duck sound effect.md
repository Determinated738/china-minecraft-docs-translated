--- 
front: 
hard: Advanced 
time: 15 minutes 
--- 

# Add a little duck sound effect 

#### Author: Realm 

Sound effects are located in the RP/sounds folder, so custom sound effects also need to be placed here. Developers can use folders to separate them. Custom sound effect files use .ogg and .wav formats. In pursuit of quality, .wav has better sound quality than .ogg, but .ogg saves more space than .wav. It is up to the developer's own consideration to decide which format to use. 

``` 
{ 
"mob.green_head_duck.ambient": { 
"category": "neutral", 
"sounds": [ 
{ 
"name": "sounds/mob/green_head_duck/ambient", 
"volume": 0.7 
} 
] 
} 
} 
``` 

Developers need to put a sound_definitions.json file in the sounds folder. We define a resource path "mob.green_head_duck.ambient", and we set the sound effect category (category) to neutral. Before 1.16.200, setting the sound effect category has little effect on whether the sound effect plays normally. After version 1.16.200, developers can adjust the corresponding volume according to the sound effect category in the settings. 

The sounds array will store the resource address, volume, playback distance, etc. of each sound effect. Generally, if the volume is not set, the default is the normal volume of the sound effect. 

``` 
{ 
"entity_sounds": { 
"entities": { 
"design:green_head_duck": { 
"volume": 1.0, 
"pitch": [0.8, 1.2], 
"events": { 
"ambient": "mob.green_head_duck.ambient" 
} 
} 
} 
} 
}

``` 

Go back to the sounds.json file in the main directory of the texture pack. This file also needs to be created manually. After entering the file, define the structure format as follows: 

``` 
{ 
"entity_sounds": { 
"entities": {} 
} 
} 
``` 

Entities contains the corresponding biological name domain. Our teal name domain is design:green_head_duck, so the object name is based on "design:green_head_duck". Its properties include volume, pitch, and sound effect playback events. After modifying the audio, the volume and pitch of the sound effect itself, you can revise it here again. The event contains many sound effects that will be played by the creature in different states. 

Commonly used parameter options are generally the following: 

ambient natural sound effects, that is, the sound effects played when in standby. 

hurt injury sound effects, that is, the sound effects played when injured. 

death death sound effects, the sound effects played when dying. 

step walking sound effect, the sound effect played when walking. 

attack attack sound effect, the sound effect when attacking. 

shoot shooting sound effect, the sound effect played when designing.