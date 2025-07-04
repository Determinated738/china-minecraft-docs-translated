--- 
front: https://nie.res.netease.com/r/pic/20210727/82dd4b1e-04e1-4a90-a4c5-1a4d5cec462a.png 
hard: Getting Started 
time: 25 minutes 
--- 
# New version editor related questions 

1. What is the preset architecture? 

The preset architecture is an object-oriented Python code architecture. It provides objects such as presets, parts, and a complete set of preset APIs for developers to use. 

2. What is a preset? 

Preset means pre-setting, that is, developers can assemble blocks, materials, entities, special effects, and gameplay logic into a preset and save it as a file in the behavior package directory of the work. Currently there are empty presets, player presets, entity presets, special effect presets, block presets, and UI presets. 

3. What are parts? 

Parts can be bound to code files and hung under presets. The code file bound to the part must inherit from PartBase, which is similar to Mod Main and Server/Client System in MOD SDK. 

4. What is an instance? 

An instance is the content generated in the scene based on the preset file. Most presets can generate any number of instances in the scene, and the changes to the preset will be synchronized to the instance in real time. 

Developers can also modify each instance separately, and the instance modification has a higher priority than the preset modification. 

5. Will the writing method of Mod SDK be greatly changed? 

The preset architecture is another set of architectures and will not have any impact on Mod SDK. 

6. Is the writing method of Mod SDK compatible in the part? 

Compatible, you can normally get Server/Client System in the part, and use other Mod APIs. (Note that it is currently not possible to import in the file header, and can only be imported when in use) 

7. Can presets and parts be used in Mod SDK? 

Yes, you can get instances of presets or parts in Server/Client System. (Note that it is currently not possible to import in the file header, it can only be imported when used)



8. What are the advantages of the preset architecture? What are the recommended usage scenarios? 

The preset architecture is an object-oriented architecture, and its advantages also lie in this. 

If your logic has changes to existing entities (including creatures) or blocks, or new entities (including creatures) and blocks, or new complete buildings, using the preset architecture will significantly improve efficiency. 

If you are making a gameplay map, you can use the preset architecture to make the map, which can be adjusted quickly and will not affect the scene itself (preset buildings can even overlap). 

9. What are the advantages of parts? 

The preset architecture brings the characteristics of object assembly. Parts can be freely hung under the preset and plug and play. 

Experienced developers can use this feature of parts to decouple logic and disassemble a whole piece of logic into some relatively independent logic modules. 

When the code is reasonable, the parts do not care what specific preset they are hung under, and they can all take effect, so it is very convenient to reuse logic. 

Another advantage of parts is that they are deeply integrated with the editor, and the variables in the code can be exposed to the editor's property panel through the meta file of the parts. 

Under the preset architecture, the presets and parts will be saved in the preset archive, so the parts can partially replace the custom components of the Mod SDK. 

10. How to solve the white screen in the map editor of the new version of the editor? 

Delete the options file under this path: %appdata%\MinecraftPE_Netease_Editor\minecraftpe 
