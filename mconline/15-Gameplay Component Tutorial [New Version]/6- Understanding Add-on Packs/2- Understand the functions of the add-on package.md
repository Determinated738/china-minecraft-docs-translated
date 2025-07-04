--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Getting Started 
time: 10 minutes 
--- 
# Understanding the functions of add-ons 

Through add-ons, we can modify various functions of Minecraft. As we know, the editor in the Minecraft development workbench can also visually support us to modify Minecraft with one click. So, what is the difference between the two? In fact, the essence of the process of operating various function modifications in the "AddOn component" of the editor is a process of making and modifying add-ons, thereby further modifying the Minecraft game. It's just that the modifications in the editor are more visual and simpler. But at the same time, relatively speaking, the scalability, flexibility and complexity of the results of modifications in the editor are much lower than those of directly operating files for modification. Therefore, if we want to make some large, complex, and comprehensive add-on packs, we still need to learn how to modify the content and functions by directly manipulating the files. 

## Definition File 

We introduce a type of file that you need to frequently use in add-on packs, that is, the **Definition File**. A definition file is a type of file that can define various contents in the game through the data contained in it. It is usually a JSON file, which is the file with the `.json` extension we see. 

These JSON-formatted definition files all use a JSON format that can be annotated. So if you want to understand and write definition files correctly, you need to first understand the format of **JSON** (**JavaScript Object Notation**, **JavaScript Object Notation**). Developers can learn about this knowledge on the Internet. 

In fact, in the challenge section of the previous chapter, we came into contact with the original `Vanilla_Resource_Pack/entity/slime.entity.json` and `Vanilla_Behavior_Pack/entities/slime.json` at the beginning of the section, which are the two definition files of entities. `slime.entity.json` defines the rendering, model, texture and other properties of the client entity, while `slime.json` defines the server-side components, events and other contents of the same entity. 

The definition file determines the "initial state" of most gameplay and a small amount of "pseudo-logic" (such as entity animation). For this reason, the content in the definition file is often just called a static **data**, and the content added or changed by this data, the interface and components provided for this data are called **data-driven**. 

## Script File 

The **Script File** is the most important file type after the definition file. Script files refer to scripts that can be loaded by the Minecraft Bedrock Engine. In the international version of Minecraft, developers usually use JavaScript scripts, but in the Chinese version of Minecraft, we can use another script exclusive to the Chinese version and with powerful interface functions - **Python** script. The interface of Python scripts in the Chinese version of Minecraft is also called **Mod API**. This is a Minecraft module interface carefully built by the Chinese version development team. It is very powerful and closely integrated with the data-driven interface. While giving full play to the functions of the data-driven interface, it adds "real" logic to it, and achieves more powerful gameplay through the "real" event system and component factory. 

The content of the script file is generally called **Script**, and the content added or changed by the script, the interface and components provided for the script are all called **Script-Enabled**. 

The close integration of data-driven content and script-enabled content can make the add-on package have a very high functional ceiling as a game module. 

## Functions that depend on behavior packages 

Let's take a look at which functions are mainly dependent on behavior packages. 

### Server-side content of entities, items, and blocks 

Entities, items, and blocks are defined by two definition files, one in the resource pack, responsible for client content, and one in the behavior pack, responsible for server content. Among them, the definition files located on the server are often more important, because the server definition files occupy the main game manifestations of entities, items and blocks. Most of the various functions, behaviors, and gameplay we see in the game actually come from their server-side behaviors. 

At the same time, if we want to add script logic to them, then these scripts are all located on the server. Therefore, entities, items and blocks are particularly important in the behavior pack. 

### Dimensions, biomes and features 

The definitions of dimensions, biomes and features are also all located in the behavior pack, because they determine the world generation, and the world generation is all done on the server. **Dimension** (**Dimension**) is a world concept similar to the main world, the netherworld and the end; **Biome** (**Biome**) is a world concept that determines where grasslands, forests, oceans, various creatures, and various features are generated; and **Feature** (**Feature**, also translated as **Feature**) is a physical object scattered in the world, ranging from large ruins to small ore veins. 

### Presets and Parts 

A **Preset** is a pre-set abstract structure that can be a block, entity, player or world, but can be instantiated into a real thing or logic in the world. A **Part** is a logic script that can be attached to a preset and can function according to the preset. Both types of files should be stored in the behavior pack. 

### Module API Script 

Previously, we introduced a script exclusive to the Chinese version - the Python script of the module API. All module API scripts should be located in the behavior pack. 


### Other content 

Recipes, trades, loot tables, macros in the logic editor, and logic blueprints are all defined and stored by behavior packs. 

## Resource pack-dependent functions 

Let's take a look at the main functions that depend on resource packs. 

### Texture maps 

All texture maps, whether they are texture files that cover the original textures or files added to customize new gameplay, should be stored in the folder corresponding to the resource pack. Only in this way can the client find the corresponding texture and render it. 

### Shaders (Light and Shadow) 

All **Shaders** (**Shader**, commonly known as **Light and Shadow**) are defined and implemented in resource packs. This is because shaders are used to provide rendering to the renderer, and the rendering of the renderer is content that only occurs on the client. 

### UI 

Although Microsoft is developing a new UI for Minecraft, the JSON-driven UI format that has been used for many years is still widely used in the game. We usually call it **JSON UI**. All JSON UI definition files are located in the resource pack and are parsed by the Bedrock Engine to work. 

However, the UI defined in the resource pack actually has almost no logic. Most of the original JSON UI space needs to bind hard-coded functions to implement logic, but we can use the module API to add logic to our custom UI. However, due to the use of the module API, all script files related to UI logic should be located in the behavior pack, so please keep this in mind. 

### Client content of entities, items, and blocks 

This part of content is often used by entities, items, and blocks to bind textures, models, and materials, and materials will further associate them with shaders for in-game rendering. 

Of course, there are also some components in items that are exclusive to the client, which are written in the client definition file of the item. 

### Models 

Obviously, models are used for rendering. The actual collision boxes of entities and blocks in the game are often different from the models. Most of the time, they are simpler than the models, mostly a combination of large or small cubes, which can facilitate the calculation of the server. The more sophisticated models are used to output on the player's screen, and the server does not need to know such sophisticated information. Therefore, the models are also placed in the resource pack. 

### Other content 

Particle and special effect definitions, font files and their definitions, sound files (sound effects and music), etc. are all used for calculation and output on the client, and they should all be located in the resource pack.