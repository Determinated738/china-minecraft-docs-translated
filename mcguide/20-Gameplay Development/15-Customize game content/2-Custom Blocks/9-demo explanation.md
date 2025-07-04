--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# demo explanation 

[CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod) defines the following custom blocks: 

- customblocks:customblocks_test0 

The block with the top surface different from the other surfaces. 

In `resource/blocks.json`, set isotropic up to true so that the upper surface will rotate randomly when placed, which can achieve the effect of no obvious texture duplication visually. This is the function of Microsoft custom blocks. 

Demonstrated the functions of forming custom biomes, villager trading, custom recipes, and block combinations 

- customblocks:customblocks_test_ore 

Custom blocks with properties similar to minerals 

Demonstrated the functions of mining and dropping objects 

- customblocks:customblocks_test_face4 

Blocks with 4 faces 

Demonstrated the function of four faces in multi-faceted 

- customblocks:customblocks_test_face6 

Blocks with 6 faces 

Demonstrated the function of six faces in multi-faceted 

- customblocks:customblocks_test_mobspawner 

Custom spawner block - protozoa 

Demonstrated the function of generating protozoa in "Special Block - Custom Spawner" 

- customblocks:customblocks_test_mobspawner1 

Custom spawner block - Microsoft custom creatures 

Demonstrates the function of generating Microsoft custom creatures in "Special Block - Custom Spawner" 

- customblocks:customblocks_test_portal_blue 


Custom portal block to dimension 3 

Demonstrates the function of "Special Block - Custom Portal Block" 

- customblocks:customblocks_test_block_entity<span id="demo说明_block_entity"></span> 

Custom blocks with custom block entities 

Demonstrates the functions related to custom block entities. For detailed explanation, see the [Custom Block Entity](./4-Custom Block Entity.md#demo) document 

- customblocks:customblocks_model_flower 

Custom blocks in the shape of flowers 

Demonstrates the functions of custom block models, brightness, collision boxes, rendering materials, solidity, and pathfinding 

- customblocks:customblocks_flower_extend 

In addition to covering the basic functions of customblocks_model_flower (custom blocks in the shape of flowers), it also extends the functions of slowing down entities when passing through and destroying gravity blocks when falling. 

- customblocks:customblocks_model_decoration 

Four-sided blocks with custom models 

- customblocks:customblocks_model_wire 

A custom block in the shape of a wire that can be connected to other wires, furnaces or grass blocks next to it 

Demonstrates variable models and variable collision boxes 

- customblocks:customblocks_test_heavy 


Demonstrates custom gravity blocks 

- customblocks:customblocks_slime 

Uses the netease:block_properties component and python events to replicate the original slime block feature 

Demonstrates the custom entity block appearance function 

- customblocks:custom_block_squirrel 

Includes the entity model configuration of the custom entity block, the NetEase version of particles, sequence frame effects, the Microsoft original particle effects and sound effect configuration.