--- 
front: 
hard: Advanced 
time: 10 minutes 
--- 

# Original particles and special effect particles 



#### Author: Boundary 



Original particles refer to the particle special effects that come with the Bedrock Edition of Minecraft, or particles created by developers through the custom particle method provided by the Bedrock Edition particle system. Special effect particles are a set of particle systems maintained by the official Chinese version. Developers can study them through the official Demo or MODSDK documents, and use MCStudio's special effect editor for visual creation. In general, the rules followed by the two in making particles are roughly the same, but the individual and detailed functions of the services are slightly different. The following table explains these differences. 

| | Original particles | Special effect particles | 
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | 
| Functional differences | 1) Original particles can have collision detection. Particle detection includes executing events after particles collide with blocks (such as honey particles of bee blocks, which will play the sound effect of honey falling after falling to the ground); and generating real physical collisions after colliding with blocks (such as staying or rebounding after touching blocks). 2) Original particles can be set whether they are affected by light. When set to true, the color of particles will darken as the light darkens (such as the sky getting darker in the MC world). 3) Particles have no concept of hierarchy, that is, they support the effects of the front and back levels of particles, for example: the larger the level, the later the rendering, and the closer the particles are displayed. | 1) Special effect particles have no collision detection. 2) Special effect particles are not affected by light and always maintain their original color. 3) Particles have a concept of hierarchy, that is, they support the effects of the front and back levels of particles, for example: the larger the level, the later the rendering, and the closer the particles are displayed. | 
| Performance Difference | 1) Original particles will be recycled by the game after the particles disappear, and resources will be dynamically allocated. 2) The original particle map and sequence frame map will print a warning in the game log when the size is above 2048x2048. | 1) Special effect particles will stay in the game after the particles disappear, occupying resources. 2) According to the official document specifications, a single particle map does not exceed 32x32, and a sequence frame map does not exceed 512x512. | 
| Usage difference | 1) Original particles can be generated in the world through instructions, or bound to the original model, but it cannot be bound to the bones of the skeleton model. 2) There is no official editor for original particles, but there is a special effects editor snowstorm maintained by foreign private developers. 3) The original particles have high requirements on the level of developers in terms of dynamic changes and effect levels. For example, particle gradient color and particle scaling require Molang syntax expressions. | 1) Special effect particles can be generated in the world through MODSDK, or bound to the skeleton model, but it cannot be bound to the bones of the original model. 2) Special effect particles can be edited and produced by MCSTUDIO special effect editor, which is developed and maintained by the official Chinese version. 3) Special effect particles are easy to make, and it is easy to make good-looking special effects. There is a direct input panel to control the gradient color and scaling. |