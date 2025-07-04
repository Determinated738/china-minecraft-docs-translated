--- 
front: 
hard: Advanced 
time: 10 minutes 
--- 

# Duration of retractable particles 



#### Author: Boundary 



#### Setting duration 

1) Above the Texture panel is the lifetime panel. The default mode is Time, which is equivalent to the lifetime of the special effects editor after setting Max Age. Each particle emitted by the emitter will disappear after reaching the maximum lifetime. The Snowstorm editor has two additional parameters. Kill in blocks can add the name field of the original block, that is, when the particle enters a certain block, it will be destroyed by the game and disappear. Only in blocks is the opposite. The particle will only be displayed when it is active in this block, otherwise it will disappear. A classic example of using this parameter is bubbles in the water. In the previous tutorial on binding the particle effect of the mallard, developers can find that bubbles will only be generated in the water, which is exactly what this function is used for. 

2) Emitter lifetime means the life cycle of the emitter. Active time means the time during which the emitter will continuously emit particles, which is equivalent to the emission cycle length of the special effect editor. Sleep time means how long the emitter will rest after the active time ends. It is only valid when the mode of the emitter life cycle is changed to loop, which is equivalent to the emission cycle interval of the special effect editor.