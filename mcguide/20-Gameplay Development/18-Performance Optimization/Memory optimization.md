--- 
front: https://nie.res.netease.com/r/pic/20210727/82dd4b1e-04e1-4a90-a4c5-1a4d5cec462a.png 
hard: Advanced 
time: 20 minutes 
--- 

# Memory Optimization 

## Preface 

Memory optimization is extremely sensitive and meaningful to mid- and low-end models. With the growth of MC content and the increasing number of MODs released by developers, players may load more and more MODs in the game and experience more and more content. The bottleneck of memory on mid- and low-end devices is becoming more and more obvious. Therefore, it is necessary to optimize memory. 

## Resource Size Optimization 

### Texture Resolution 

#### Significance 

The resolution control of textures is very important. First of all, it will directly determine the speed of texture loading and the memory occupied. Secondly, because the internal implementation will combine multiple textures of blocks and items into one atlas, a single texture with a high resolution will also cause the overall atlas resolution to be too large, and the performance will also be reduced when using the atlas. So don’t think that if I have an item with a very high-definition texture, but as long as I don’t use this item, it will not affect the game performance. 

#### Two principles 

1. The texture should be as small as possible while being clear: 
For example, if a 500 * 500 texture is reduced to 100 * 100, the effect is not much different, so it is recommended to directly reduce it to 100 * 100 

2. The texture should be a power of 2 as much as possible. Textures with a power of 2 size are more friendly when loading and rendering: 
For example: a 1200 * 1200 texture is recommended to be reduced to 1024 * 1024; 
A 20 * 20 texture is recommended to be reduced to 16 * 16. 

#### PNG texture compression 

When using PNG textures, you can use the pngquant tool to compress them first, which is close to lossless compression 

### Audio 

For sound effect resources, use ogg format files as much as possible, and wav format files have a lower compression rate 

## Dynamic loading 

If the resource is not frequently used, try not to preload it, and load it when it is used 

Skeleton model system (uncommon skeleton models should declare the dy_load field to be true) 

netease_models.json: 
```json 
{ 
"datiangou" : { 
"skeleton" : "skeleton/datiangou_skeleton.json", 
"mesh" : "mesh/datiangou_mesh.json", 
"animation":{ 
"fengxi":"animation/datiangou_animation_fengxi.json",

"run": "animation/datiangou_animation_run.json" 
}, 
"dy_load": true 
} 
} 
``` 

Audio system (uncommon audio should be declared in dy_load_list) 
sound_definitions.json: 
```json 
{ 
"dy_load_list":[ 
"sounds/testaudio/test", 
"sounds/music/game/test/test1", 
] 
} 
```