--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 20 minutes 
--- 
# Understanding particle events 

We have learned before that data-driven entities have the function of defining events and triggering events. In fact, our particles can also define and trigger events. In this section, let's learn how to define and trigger particle events. 

## Define events 

Currently, Snowstorm does not support the definition and triggering of events, so we need to manually edit the JSON file. Events and components are at the same level and are defined under the pattern identifier. 

```json 
{ 
"format_version": "1.10.0", 
"particle_effect": { 
"description": { 
"identifier": "tutorial_demo:some_particle", 
"basic_render_parameters": { 
"material": "particles_alpha", 
"texture": "textures/particle/particles" 
} 
}, 
"events": { 
// Events 
}, 
"curves": { 
// Curves 
}, 
"components": { 
// Components 
} 
} 
} 
``` 

In the `events` field, we can manually define some particle events. Similar to entities, each particle event is also composed of an object, and the key name of the object is the event name of the particle. Particle events can also use `sequence` to trigger multiple events, or use `randomize` to trigger an event with weighted randomness. For example, we can analyze the following fictitious example: 

```json 
"events": { 
"<event_name_1>": { 
"sequence": [ 
{ 
"particle_effect": { 
"effect": "tutorial_demo:particle_1", 
"type": "emitter" 
}, 
"sound_effect": {

"event_name": "some.level.sound.event.name" 
} 
}, 
{ 
"particle_effect": { 
"effect": "tutorial_demo:particle_2", 
"type": "emitter" 
}, 
"expression": "/* Some Molang Expression */" 
}, 
{ 
"sequence": [ 
// Can be nested infinitely 
] 
}, 
{ 
"randomize": [ 
// Weighted random trigger 
] 
} 
] // You can write an event trigger sequence 
}, 
"<event_name_2>": { 
"randomize": [ 
{ 
"weight": 1, 
"particle_effect": { 
"effect": "tutorial_demo:particle_2", 
"type": "particle" 
}, 
"expression": "/* Another Molang Expression */" 
}, 
{ 
"weight": 1, 
"particle_effect": { 
"effect": "tutorial_demo:particle_4", 
"type": "particle_with_velocity" 
} 
} 
] // You can write a weighted random trigger 
}, 
"<event_name_3>": { 
"particle_effect": { 
"effect": "tutorial_demo:particle_5", 
"type": "emitter_bound" 
} // You can also directly write an event trigger response 
} 
} 
``` 


As you can see, the structure of this event is almost the same as that in the entity, except that the content that the event can respond to is different. `particle_effect` is used to generate another particle at the initial coordinates of its own emitter, where `effect` fills in the particle's namespace identifier, and `type` fills in the generated type. You can fill in `emitter`, `emitter_bound`, `particle` or `particle_with_velocity`, which respectively represent the emitter that generates particles, the emitter that binds the generated particles (that is, if the current particle is bound to an entity or locator, the new particle will inherit this binding relationship), the generation of a particle instance, and the generation of a particle instance that inherits the current emitter's velocity. 

`expression` is used to execute a Molang expression when the event is triggered, which is generally used to change the value of a variable. 

`sound_effect` is used to trigger a system sound, or an archived sound event. Archived sound events are sounds defined in the resource package `sounds.json`. However, for particles, only system sounds defined in the `individual_event_sounds` field, that is, independent archived sound events, can be triggered. For example, let's look at the vanilla honey drip particle example: 

```json 
{ 
"format_version": "1.10.0", 
"particle_effect": { 
"description": { 
"identifier": "minecraft:honey_drip_particle", 
"basic_render_parameters": { 
"material": "particles_alpha", 
"texture": "textures/particle/particles" 
} 
}, 
"events": { 
"hit_ground": { 
"sound_effect": { 
"event_name": "block.beehive.drip" 
} 
} 
}, 
"components": { 
// ... 
"minecraft:particle_motion_collision": { 
"coefficient_of_restitution": 0.1, 
"collision_drag": 10.0, 
"collision_radius": 0.01, 
"events": [ 
{ 
"event": "hit_ground", 
"min_speed": 0.5 
} 
] 
} 
// ... 
} 
} 
} 

``` 

And the corresponding `sounds.json` file: 

```json 
{ 
"individual_event_sounds": { 
"events": {

      "block.beehive.enter": {
        "sound": "block.beehive.enter",
        "volume": 0.75,
        "pitch": [ 0.7, 0.8 ]
      },
      "block.beehive.exit": {
        "sound": "block.beehive.exit",
        "volume": 0.75,
        "pitch": [0.9, 1.1]
      },
      "block.beehive.shear": {
        "sound": "block.beehive.shear",
        "volume": 0.8,
        "pitch": [0.8, 1.0]
      },
      "block.beehive.work": {
        "sound": "block.beehive.work",
        "volume": 0.6,
        "pitch": 1.0
      }, "block.beehive.drip": { 
"sound": "block.beehive.drip", 
"volume": 0.3, 
"pitch": [0.7, 0.9] 
} // block.beehive.drip system sound is defined here 
} 
}, 
"entity_sounds": { 
// ... 
} 
// ... 
} 
``` 

## Triggering events 

Particles can trigger events in multiple components, the most important of which are the two lifecycle event components `minecraft:emitter_lifetime_events` and `minecraft:particle_lifetime_events`. 

The `minecraft:emitter_lifetime_events` component is the **lifecycle event of the emitter**. It has five fields: `creation_event`, `expiration_event`, `timeline`, `travel_distance_events` and `looping_travel_distance_events`. Each field can trigger the component in a specific way. 

```json 
"minecraft:emitter_lifetime_events": { 
"creation_event": [ "<event_name>", ...], 
// "creation_event": "<event_name>", 
"expiration_event": [ "<event_name>", ...], 
// "expiration_event": "<event_name>", 
"timeline": { 
"some_time": [ "<event_name>", ... ], 
"another_time": "<event_name>" 
},

"travel_distance_events": { 
"some_distance": [ "<event_name>", ... ], 
"another_distance": "<event_name>" 
}, 
"looping_travel_distance_events": [ 
{ 
"distance": 1.0, 
"effects": [ "<effect_event_one>" ] 
}, 
{ 
"distance": 2.0, 
"effects": [ "<effect_event_two>" ] 
} 
] 

} 
``` 

We can see that both the creation event `creation_event` and the expiration event `expiration_event` can specify an event name or multiple event names in the form of an array. The timeline `timeline` and the travel distance event `travel_distance_events` represent the triggering of one or more events after the emitter has passed a specific time or traveled a specific distance. Among them, `some_time`, `another_time`, `some_distance`, and `another_distance` can all be filled with a number like the keyframes of an animation. The looping travel distance event `looping_travel_distance_events` is used to define the event that is triggered every time a certain distance is traveled. Such an event must be an event that generates a new particle effect, that is, the event triggered here must have the definition of the `particle_effect` field. 

`minecraft:particle_lifetime_events` is the **particle life cycle event**, but it can only define the creation event `creation_event`, the expiration event `expiration_event`, and the timeline `timeline`. All the syntax is the same. 

So far, we have basically learned most of the content of particles. In the next section, let's challenge to create a firework particle to complete our study of this chapter!