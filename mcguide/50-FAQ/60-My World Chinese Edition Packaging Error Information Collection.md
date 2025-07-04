--- 
front: https://nie.res.netease.com/r/pic/20210730/ee109f39-8987-46e0-9fe7-40ebb23060fa.png 
hard: Getting Started 
time: 15 minutes 
selection: true 
--- 
# Summary of error messages for packaging Chinese version of Minecraft 

For manual packaging of work resources, please click to view [Rules for uploading resources of Chinese version of Minecraft](../35-Listing and Settlement/Course 11-Rules for uploading resources of Chinese version of Minecraft.html). 

For the method of packaging work resources in one click in the Minecraft Development Workbench, please click to view <a href="../../mconline/10-addon tutorial/Chapter 18: Package and export your work/Course 01. Package structure and import.html" rel="noopenner">[Minecraft Development Workbench package import] </a> and <a href="../../mconline/10-addon tutorial/Chapter 18: Package and export your work/Course 02. Package export.html" rel="noopenner">[Minecraft Development Workbench package export]</a> 

## Summary of machine review packaging error codes 

### Packaging error code 6 [DirError] 

Indicates a directory error. The component is not organized according to the directory requirements, resulting in the packaging system being unable to parse. Among the known information, the reasons that trigger the above errors are: 

> Map component: 
> 
> - level.dat_old, levelname.txt, etc. are not carried. You can try to use the Minecraft Development Workbench (MC Studio) to import the map, which will automatically regenerate these two files for the map. 

### Packaging error code 7 [UnZipError] 

Indicates an error in decompressing the zip file. The zip file itself has a problem and cannot be decompressed. 

### Packaging error code 8 [PackMcpError] 

Indicates that there is a problem in the process of packaging the python script, which is likely to be a problem with the script syntax. 

### Packaging error code 10 [NoManifestError] 

According to the known information, the reasons that trigger the above errors are: 

> - Indicates that during the packaging process, it was found that there was no manifest.json file in behavior_packs. 
> - Indicates that there is an entities folder in the resource pack. Currently, the machine review needs to use the entities folder to judge the behavior pack. The duplicate folder name will cause a machine review error. 
> 
> - Indicates that the map component is nested with more than one layer of folders.



### Packaging error code 12 [NoLevelError] 

Indicates that when packaging NetGame and Lobby, no Level map data was found. 

### Packaging error code 13 [HasLevelError] 

Indicates that when packaging the product Mod, Level map data was found, which means that the file content that should not be there was included. 

### Packaging error code 16 [FileOrPathNameError] 

Indicates that when the packaging system decompressed the uploaded zip file, it found that the file name contained unresolvable characters, which may be Chinese or unresolvable symbols. 

### Packaging error code 18 [CodeReviewError] 

Indicates that when checking the code of the entire package, it was found that unopened APIs or syntax errors or prohibited methods were used. 

### Packaging error code 20 [FindBehaviorAndResourceError] 

Indicates that an error occurred when searching for resource packs or behavior packs. If there is no behavior pack, please check whether there is a folder named resource_pack at the same level as manifest.json. If so, please rename it. 

### Packaging error code 21 [EncryptError] 

Indicates that there was a problem when the platform encrypted the component. Please do not resubmit the component source files that have been released in the Chinese version. Now the platform has encrypted all uploaded components. Please do not upload encrypted component resources. 

### Packaging error code 24 [ResourcePackUnvalid] 

The folder structure is wrong. Please make sure that there is a textures or shader folder in the resource pack folder, an entities folder in the behavior pack folder, and no other irrelevant files in the root directory. 





### Packaging error code 25 [TexturesListLoadError] 

Indicates that the reading of the json file failed, which may be due to a problem with the corresponding json file. Among the known information, the reasons that trigger the above errors are: 

> - Indicates that the encoding of the json file is incorrect and should be utf-8. 
> - Indicates that the format of the json file is incorrect. You can use the json formatting tool to check it. 

### Packaging error code 26 [TexturesSizeError] 

Indicates that the error is caused by the size of the texture file. You can check whether there is an oversized texture file. 

### Packaging error code 27 [NameOverSizeError] 

Indicates that there is a file with a file name that is too long in the zip file. Please check whether the corresponding file name is too long. 

### Packaging error code 29 [PlayerEntityJsonReviewError] 

Indicates that the render_controllers definition in the customized player.entity.json under the resource_packs/entity/ path does not meet the specifications. Please make sure to keep at least the following 4 render_controllers: 

```json 
{ 
// player.entity.json 
"render_controllers":[ 
{ 
"controller.render.player.first_person":"variable.is_first_person" 
}, 
{ 
"controller.render.player.third_person":"!variable.is_first_person && !variable.map_face_icon" 
}, 
{ 
"controller.render.player.first_person_bloom":"variable.is_first_person" 
}, 
{ 
"controller.render.player.third_person_bloom":"!variable.is_first_person && !variable.map_face_icon"
        }
    ]
}
```



### Packaging error code 30 [ReadLevelDataError] 

Indicates that the level.dat file failed to be read. Please check whether the file in the resource package is damaged, missing fields or does not exist. 

### Packaging error code 31 [MapItemVersionError] 

Indicates that the game version of the map component is greater than the highest game version supported by the current Chinese version of "Minecraft". 

### Packaging error code 33 [AudioReviewError] 

Indicates that the sound effect format carried in the component is not in .ogg format, or the sound effect bit rate in .ogg format is greater than 128. The developer platform's internal email will inform you of the path of the corresponding sound effect. Please convert the sound effect format to .ogg format and set the bit rate to no more than 128. 

### Packaging error code 34 [GlyphReviewError] 

Indicates that the custom bitmap font does not meet the requirements of Chinese version 2.2 (Bedrock Edition 1.18) and above. The bitmap font needs to meet the following conditions: 

- The texture size is 256*256. 
- The length and width of each font are 16 pixels. 

### Packaging error code 35 [CodeExceptionError] 

Indicates that in the detected file, there are more than 5 consecutive identical characters in the variable name, file name, and function name. For the sake of script security, please modify the characters that have more than 5 consecutive identical characters. 

## Other packaging error information summary 

### Packaging error: Skin image must contain alpha channel 

Indicates that the skin image lacks alpha channel. Please import the skin source image file into image processing software such as Photoshop, check the color channel, and export it as a png image. Or use MCSkin3D or Skinseed to import the skin source file and export it again, and then upload it. 

### Packaging error, failed to call the listing interface 

Please check whether there are Chinese characters or special symbols in the name of the packaged folder, and whether there are some special symbols (such as Emoji**) that cannot be parsed in the author profile and work introduction of the developer platform. If the above situation exists, it needs to be readjusted before review. If the problem still exists, under **[Developer FAQ]** of **[Developer Platform]**, click **[Feedback Other Issues]** to submit the problem, and the feedback result will be sent to the developer platform mailbox via developer email. 





### Packaging error UUID [UUID conflict, please regenerate] 

![](./images/1_1.jpg) 

![](./images/1_2.jpg) 

1. The uuid under the behavior pack or resource pack manifest of the resource add-on pack is repeated with the UUID of the existing resources on the platform. If the error resource is a mobile game resource and is an Add-on, please open the manifest file in the behavior pack (behavior_packs) and resource pack (resource_packs) folders, regenerate the uuid with the online tool, and replace the uuid value in the file. If the error resource is a mobile game map component with Add-on, please rename the netease_world_behavior_packs and netease_world_resource_packs files in the map root directory to world_behavior_packs and world_resource_packs **(overwrite if they exist)**, and modify the relevant information. The example is as follows: 

```json 
[// world_resource_packs.json 

{ 
"pack_id" : "c04c0b42-fed4-4b7d-a34d-9ea5280a0e05", //Please use the UUID generation tool to replace this value! ! ! 
"type": "Addon", 
"version" : [ 0, 0, 1 ] //Please make sure that the array value corresponds to the version information in the resource pack carrying the relevant UUID! ! 
} 
] 
``` 

```json 
[// world_behavior_packs.json 

{ 
"pack_id" : "c04c0b42-fed4-4b7d-a34d-9ea5280a0e05", //Please use the UUID generator to replace this value! ! ! 
"type": "Addon", 
"version" : [ 0, 0, 1 ] //Please make sure that the array value corresponds to the version information in the behavior pack that carries the relevant UUID! ! 
} 
] 
``` 

The generator tool [can be viewed at this link](https://www.uuidgenerator.net/). 

2. If the error is about a gameplay map or map overview without Add-on resources, please directly clear the files in the behavior pack (behavior_packs) and resource pack (resource_packs) folders, and delete files such as netease_world_behavior_packs, netease_world_resource_packs, world_behavior_packs, and world_resource_packs. 
