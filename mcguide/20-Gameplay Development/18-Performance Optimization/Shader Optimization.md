--- 
front: https://nie.res.netease.com/r/pic/20210728/5a263f49-e1f3-4a9a-96b3-307b11848590.png 
hard: Advanced 
time: 30 minutes 
--- 
# Shader Optimization 
## Preface 

In order to create cooler effects, we often customize materials and then define our own Shaders, or directly rewrite and replace the original Shaders. In particular, many current light and shadow MODs basically require Shader modifications. Shaders are closely related to GPU performance. A well-written Shader can allow players with low configurations to experience cool effects smoothly. If it is not well written, it may cause high-end machines to be stuck. 

## Try to use as few if else conditional statements as possible 

GPUs process logic in parallel and use SIMD (single instruction multiple data) structure. The same code will be processed by multiple GPU processing units at the same time. The execution time of this code depends on the code that takes the longest time to execute. In order to give full play to the parallelism of GPUs, we try to use as few conditional branch logic as possible so that all GPU processing units execute the same code. 

If the if else statement does not contain much logic and most of it can be merged, the step() function can often be used for optimization. 

The function of step(a,b) is: 
```glsl 
If b >= a, return 1, otherwise return 0 
``` 

So if there is such a statement: 
```glsl 
if(r >= 0.5) 
{ 
r = 0.6; 
}else{ 
r = 0.4; 
} 
``` 

Then it should be written as: 
```glsl 
r = 0.4 + step(0.5, r) * (0.6 - 0.4); 
``` 

Logically equivalent to if r >= 0.5, then: 
```glsl 
r = 0.4 + 1 * 0.2 = 0.6; 
``` 
Otherwise r < 0.5, then: 
```glsl 
r = 0.4 + 0 * 0.2 = 0.4; 
``` 
Thus, the if else statement can be eliminated. 

- Wrong way of writing:

(if else is used extensively) 
```python 
// Simple cartoon shading example, mapping continuous color values to several special discrete values 
// Get a new color value based on the passed color value. Here, for simplicity, we use only one channel as an example 
void main() 
{ 
color.r = getNewRedColor(color.r); 
...(unrelated code omitted) 
} 
float getNewRedColor(float r) 
{ 
float newR; 
if(r >= 0.6) 
{ 
newR = 0.8; 
}else if(r >= 0.3) 
{ 
newR = 0.5; 
}else{ 
newR = 0.1; 
} 
return newR; 
} 
``` 

- Correct way to write: 
(separately process only 5 per frame) 
```python 
// A simple cartoon shading example, mapping continuous color values to several special discrete values 
//Get a new color value based on the color value passed in. Here, for simplicity, we use only one channel as an example 
void main() 
{ 
color.r = getNewRedColor(color.r); 
...(unrelated code omitted) 
} 
float getNewRedColor(float r) 
{ 
float newR = 0.0; 
newR = newR + step(0.6, r) * 0.8; 
newR = newR + step(0.3, r) * step(r, 0.6) * 0.5; 
newR = newR + step(r, 0.3) * 0.1; 
return newR; 
} 
``` 

## Loop statement 

The internal implementation of loop statements such as for and while actually also has conditional judgment if The else statement has low parallelism, so try not to use it if you can. But this does not mean that you should copy and paste the code many times, which is meaningless. Instead, try to avoid the appearance of loop logic logically. If you really need to use it, it is recommended not to do too many performance-consuming operations in the loop body. 
In addition, remember to initialize the loop variable! The initial value of the variable is sometimes different on different devices. For example, the initial value of int is not necessarily 0 on all devices. 


- Wrong way to write: 
(loop variable i is not initialized) 
```python 
for(int i; i < 5; i ++) 
{ 
func(); 
} 
``` 
On some devices, the value of i will be initialized to 0, and there is no problem with looping 5 times. But on some devices, the default value of i may be a meaningless number, or even a negative number! For example, if it is −2147483648, the above loop will loop super many times, and the player will be stuck and unable to move. 

- Correct way to write: 
(separately process only 5 per frame) 
```python 
//Here i must give a default value 
for(int i = 0; i < 5; i ++) 
{ 
func(); 
} 
``` 

## Beautiful Texture Switch 

Location of the switch in the game: Settings->Video->Beautiful Texture 
Developers can execute different shader logic based on whether the player turns on beautiful texture. Two files need to be declared here, materials/sad.json and materials/fancy.json. Let's first look at the contents of the two files in the original version: 
```python 
sad.json: 
[ 
{"path":"materials/sad.material"}, 
{"path":"materials/entity.material"}, 
{"path":"materials/terrain.material"}, 
{"path":"materials/portal.material"}, 
{"path":"materials/barrier.material"}, 
{"path":"materials/wireframe.material"} 
] 

fancy.json: 
[ 
{"path":"materials/fancy.material", "+defines":["FANCY"]}, 
{"path":"materials/entity.material", "+defines":["FANCY"]}, 
{"path":"materials/terrain.material", "+defines":["FANCY"]}, 
{"path":"materials/hologram.material"}, 
{"path":"materials/portal.material", "+defines":["FANCY"]}, 
{"path":"materials/barrier.material"}, 
{"path":"materials/wireframe.material"} 
] 
``` 

When the fancy texture is turned on, the material below will be loaded. If it is not turned on, the material above will be loaded. Let's take a material as an example, such as the terrain.material material in both sad and fancy. The difference in fancy is that the FANCY field is additionally defined. In the Shader, it can be written like this: 
```python 
void main()

{ 
#ifdef FANCY 
//You can do more logic here to render better effects 
renderBeautiful(); 
#else 
// This is to turn off the beautiful textures. You should not execute too much logic here. You only need to provide a simple display effect 
renderSimple(); 
#endif 
} 
``` 

## Reduce precision 

Generally speaking, we don't need to pay too much attention to the precision of the shader we write, because in most cases the performance bottleneck is not here, but some MODs that are too complex and most players say are stuck are recommended to consider some optimization in terms of precision. 

The lower the variable precision in the shader, the faster the GPU operation. The precision is divided into 3 levels, and the keywords are: 
```glsl 
Low: lowp 
Medium: mediump 
High: highp 
``` 

int (integer): It is recommended to use lowp for integers within 256, mediump for integers within 1024, and highp for other cases 
float (floating point): It is recommended to use lowp for floating point numbers within 256, mediump for floating point numbers within 16384, and highp for other cases 

Default precision: 
```glsl 
In the vertex shader, float and int are both highp 
In the pixel shader, int is mediump, and float has no default precision depending on the device 
``` 
Declaration method example (directly add the precision keyword in front of the variable type): 
```glsl 
lowp float color 
``` 

## Remove useless variables and logic 

Some developers may be lazy when writing Shaders and copy and paste from their own previously written code, but this part of the code may have a lot of logic or variables that are not used, resulting in a lot of meaningless calculations that waste performance and need to be removed. 

- Wrong way to write: 
(Contains a lot of useless logic) 
```python 
void main() 
{ 
//Multiple variables are declared here, or perhaps copied from other places, the specific values are omitted first 
A = ...; 
B = ...; 
C = ...; 
//Only variable A is used here; B and C are not used

DoSomeThingWithA(A); 
return; 
} 
``` 

- Correct way to write: 
(delete useless logic) 
```python 
void main() 
{ 
//Leave only A, delete all other unused ones 
A = ...; 

//Only variable A is used here; neither B nor C is used 
DoSomeThingWithA(A); 
return; 
} 
``` 

## Make multiple MOD versions by level 

Developers can list different versions according to the complexity of the shader. For example, there can be "NetEase Light and Shadow Low-profile Edition" and "NetEase Light and Shadow High-profile Edition". Players can roughly know the different performance requirements by looking at the names, so that players can choose when downloading.