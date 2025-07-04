--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Getting Started 
time: 10 minutes 
--- 
# Understanding the structure of add-on packages 

Next in this section, we will focus on and formally introduce the concept of **Add-on**, which has appeared many times in the previous article. 

## Concept of add-on packages 

The concept of add-on packages was introduced by Microsoft into the development of Minecraft. In the Chinese version of Minecraft, NetEase also used this concept as a synonym for the Chinese version of the work. In essence, the nature of add-on packages in the international version and the Chinese version is the same. **Add-on pack** is a **Mod** that can modify Minecraft through **Bedrock Engine** with a **Manifest File**. It usually appears as a folder, a compressed package or an encrypted file in a special format. 

Bedrock Engine is a set of interfaces and programs for Minecraft game to read and apply add-on packs. As long as we write the add-on pack in the specified format, the engine will not report an error. The manifest file is a file called `pack_manifest.json` or `manifest.json`, which is used to guide the content of the entire add-on pack, and at the same time facilitates the Bedrock Engine to understand the type of add-on pack, so that it can know which interface to choose to connect to the add-on pack. 

From the above definition, it can be seen that add-on packs can be divided into different types according to the provisions in the manifest file. In the Chinese version, we mainly use two types of add-on packs: **Resource Pack** and **Behavior Pack**. 

- **Resource pack**: A resource pack is an add-on pack used to store client resources, most of which are used for client display, rendering, and calculation. For example, resource packs often contain textures of blocks, items, entities, and other objects, and some resource packs also contain custom materials and shaders for rendering. For some resource packs that are made with behavior packs for specific gameplay, client definition files for various blocks, items, entities, and other elements are also stored. 
- **Behavior pack**: As the name suggests, behavior packs are mainly used to store the behaviors of various elements and objects. At the same time, behavior packs also store various tables and scripts for logical calculations, which determine how the game server operates. For example, behavior packs are generally used to store server definition files for gameplay blocks, items, entities, and other elements, as well as transaction tables, loot tables, dimensions, biomes, and terrain features for game servers. Scripts written by the module API also exist in behavior packs. 

The formats of add-on packs for the international version and the Chinese version have similarities and differences. Here we focus on the format of add-on packs for the Chinese version. 

## Resource Pack Structure 

```shell 
RESOURCE_PACK 
│ biomes_client.json # Client biome color definition file 
│ blocks.json # Client block property definition file, including texture, anisotropy and block shape, etc. 
│ pack_icon.jpg # Resource pack icon, can also be in .png or .tag format 
│ pack_manifest.json # Resource pack manifest file, can also be simply manifest.json 
│ sounds.json # Sound definition file, linking sound events to corresponding system sound effect types 
│ 
├─animations # Client animation definition 
├─animation_controllers # Client animation controller definition, mainly used for entity skeleton animation 
├─attachables # Attachment definition 
├─effects # Chinese version special effect definition 
├─entity # International version client entity definition 
├─fogs # Fog definition 
├─font # font image and its definition 
├─items # international client item definition 
├─materials # material definition 
├─models # model definition, including geometry, skeleton and mesh, etc. 
├─netease_items_res # Chinese client item definition 
├─particles # international version particle definition 
├─render_controllers # rendering controller definition 
├─shaders # shader 
├─sounds # sound, including sound files and sound event definition files 
├─texts # localization 
├─textures # texture (the folder where the resource pack must exist)

└─ui # JSON UI definition 
``` 

## Behavior Pack Structure 

```shell 
BEHAVIOR_PACK 
│ pack_icon.jpg # Behavior Pack Icon, can also be in .png or .tag format 
│ pack_manifest.json # Behavior Pack Manifest File, can also be simply manifest.json 
│ 
├─animations # Server-side animation definition 
├─animation_controllers # Server-side animation controller definition, mainly used for entity command animation 
├─biomes # International version server-side biome definition 
├─BoxData # Chinese version material 
├─config # Chinese version module configuration file 
├─customBook # Chinese version custom book 
├─blocks # International version server-side block definition 
├─entities # International version server-side entity definition (a folder that must exist for behavior packs) 
├─features # International version feature definition 
├─feature_rules # International version feature rule definition 
├─functions # Function 
├─Galaxy # Chinese version logic editor macros and templates 
├─items # International version server-side item definition 
├─loot_tables # Loot table definition 
├─netease_biomes # Chinese version server-side biome definition 
├─netease_blocks # Chinese version server-side block definition 
├─netease_dimension # Chinese version dimension definition 
├─netease_effects # Chinese version status effect definition 
├─netease_enchants # Chinese version enchantment definition 
├─netease_features # Chinese version feature definition 
├─netease_feature_rules # Chinese version feature rule definition 
├─netease_group # Chinese version item grouping definition 
├─netease_items_beh # Chinese version server-side item definition 
├─netease_micro_blocks # Chinese version microblock definition 
├─netease_recipes # Chinese version recipe definition 
├─netease_tab # Chinese version item classification/item column paging definition 
├─Parts # Chinese version part definition and its script 
├─Presets # Chinese version preset definition 
├─recipes # International version recipe definition 
├─Script_xxx # Various Python scripts in Chinese version 
├─spawn_rules # Generation rule definition 
├─storyline # Chinese version logic editor logic file 
├─structures # Structure 
├─texts # Localization 
└─trading # Trading definition 
``` 

The above is a complete folder template framework for resource packs and behavior packs. Most resource packs and behavior packs do not need to have all of the above folders. You only need to create corresponding folders and related files when needed. Among all the above files, only the **manifest file** (`pack_manifest.json` or `manifest.json`) must exist correctly, which is related to whether an additional pack can be recognized normally by the game. 

## The difference between resource packs, texture packs and light and shadow packs


In order to avoid confusion among various concepts, here we emphasize the differences between **resource packs**, **texture packs** (**Texture Pack**, formerly translated as **material pack**) and **shader pack** (**Shader Pack**). 

As we have introduced before, resource packs are a type of additional package, which generally contains all or part of texture files, sound files, shader files, various client entities, items, and block definition files. We call this kind of package resource pack. 

Texture packs (formerly translated as material packs) refer to resource packs that basically only have **texture** (**Texture**) map files. General texture packs are mainly used to modify the original textures, change the appearance of the original game, and make the game style look brand new. 

Shader packs refer to resource packs that mainly contain **shader** (**Shader**) files. Some shader packs also contain some custom materials (Material), or expose some texture (Texture) interfaces for other texture packs to use (such as the four-in-one PBR mapping rule interface that is very popular recently). The shading package is mainly used to change the rendering effect of the game. The same texture will appear different under different rendering effects. Shadow effects, water reflections, and volumetric fog are all special effects that the shading package can achieve.