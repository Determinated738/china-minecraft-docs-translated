--- 
front: 
hard: Advanced 
time: 15 minutes 
--- 

# Animation format 

#### Author: Boundary 

The animation format refers to the data structure developed by the Bedrock Edition team for biological entities. It is written into a JSON file and presented in JSON syntax. If the developer uses software such as Blockbench to create art resources, it is not necessary to specifically understand these structures. This chapter of the tutorial is more for individual developers who are both artists and developers to sort out and summarize some knowledge. Some non-critical information may be folded in the display diagram. 

#### format_version 

format_version refers to the version number that defines the animation file. Currently, there is only one format version number, 1.8.0. 

#### Animation. 

Each animation resource must be prefixed with animation. The name behind it can be a combination of the biological name and the animation name. 

#### loop 

loop means the loop format of animation playback. If it is played only once, the loop attribute can be left blank; if it is played in a loop, the loop value is true. If the animation stays on the last frame after it ends, the value is "hold_on_last_frame". 

#### animation_length 

animation_length means the duration of the animation. 

#### bones 

bones means a collection of animation information for each bone. It stores the displacement information, rotation information, and scaling information of all biological bones. Each attribute key corresponds to the name of the bone of the biological geometry. The corresponding values contain three animation forms: rotation, position, and scale, and each form contains the corresponding animation information. 

``` 
{

	"format_version": "1.8.0",
	"animations": {
		"animation.fallout_cow.dying": {
			"animation_length": 0.52,
			"bones": {
				"body": {
					"rotation": {
						"0.0": [0, 0, 0],
						"0.52": [0, 0, -5]
					},
					"position": {
						"0.0": [0, 0, 0],
						"0.52": [-2, -11, 0]
					}
				}
			}
		} } 
} 
``` 

As shown in the code above: 

In the time period "0.0"->"0.52", the body bone rotates -5 degrees around the Z axis, and the position is offset 2 units to the left of the X axis and 11 units downward to the Y axis, and finally enlarged by 1.5 times. 



The current Chinese version of the animation effect is a linear animation effect, that is, the animation is expressed in a uniform speed. The curve change animation effect is still in the experimental gameplay. Developers can see the effect in single-player mode, but the component cannot be used for online. Please wait for the subsequent development plan of the Bedrock Edition team. 

