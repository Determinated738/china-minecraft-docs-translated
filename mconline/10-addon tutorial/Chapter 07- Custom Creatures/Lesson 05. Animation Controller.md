--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Animation Controller 

#### Author: Boundary 

Animation controllers control when creatures play animations. A creature entity can load multiple animation resources at the same time, and can also load multiple animation controllers at the same time. An animation controller is actually a state controller, which is used to play animations on resource packs and to execute instructions, or "animation" on behavior packs. 

A brief understanding of the state controller is actually a special logic management mode, each state has two properties: 

1) What to do in the current state; 

2) How to transfer to other states; 

State machines are useful because they enable developers to naturally decompose animations into logical processes, with each state handling its own animations and logic. 

![](./images/5_1.jpg) 

For example, suppose a developer wants to set a rest-move animation for a custom creature squirrel, it contains two states: 

Rest state and move state, the visual flow chart is shown above.

```
{
    "format_version":"1.10.0",
    "animation_controllers":{
        "controller.animation.squirrel.general":{
            "initial_state":"default",
            "states":{
                "default":{
                    "blend_transition":0.1,
                    "blend_via_shortest_path":true,
                    "animations":[
                        "idle"
                    ],
                    "transitions":[
                        {
                            "move":"query.is_moving"
                        }
                    ]

}, 
"move":{ 
"animations":[ 
"move" 
], 
"transitions":[ 
{ 
"default":"!query.is_moving" 
} 
] 
} 
} 
} 
} 
} 
``` 

#### format_version 

format_version refers to the version number of the animation controller file. Currently, there are two format versions: 1.8.0 and 1.10.0. In version 1.10.0, Bedrock Edition has reorganized the animation controller writing format for custom creatures. In general, the latest 1.10.0 format is the general standard for custom creatures. 

#### controller.animation. 

Each controller must be prefixed with controller.animation. The following name can be separated by the name of the creature. 

#### initial_state 

initial_state refers to the initial state of the animation controller. If it is not written by default, the default value is default. 

#### states 

states is a collection of states, which includes animation collections and switch state collections. The animation collection can place multiple animations at the same time, and they will play immediately when switching to the state. For example: squirrel shaking head standby animation and squirrel shaking tail standby animation. In the switch state collection, there will be object data for other states, such as in the figure above: when switching to the moving state, the conditions for biological movement must be met. 

Finally, there are two special attributes, blend_transition and blend_via_shortest_path. 

blend_transition means to make the animation state switching smoother. Reasonable allocation of this value may make a smoother animation switching effect. Its value is between 0.0 and 1.0. 

#### blend_via_shortest_path 

blend_via_shortest_path means to switch to the next state immediately, depending on the developer's needs.