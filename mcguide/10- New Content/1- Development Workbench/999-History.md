# Historical update information 

## 2021.7.29 Version 0.16.14 

1. Apollo: 
- Optimize the display mode of hot update failure 
2. Preset Editor: 
- Add Steve's preview to player presets 
3. Preset Architecture: 
- Add some commonly used Mod APIs to the parts API, see <a href="../../../mcdocs/3-PresetAPI/Preset Object/General/SDK Interface Package SdkInterface.html" rel="noopenner"> Preset API Document </a> for details 
- Drop configuration 
- Trading configuration 
4. Special Effect Editor: 
- Timeline supports interval playback and frame jump 

## 2021.7.19 Version 0.16.13 

* Fix several problems and optimize platform experience. 

## 2021.7.15 Version 0.16.12 

1. Major version update! 
- Brand new editor version! Support for gameplay programming has been incorporated into the editor 
- For detailed update information, please check the following document links: 
- Teaching Center - Editor Basics: [Instructions for using each module of the new editor](../../20-Gameplay Development/11-Assembling Simple Gameplay/7-Preset Editor.md) 
- Teaching Center - Using Presets for Development: [Instructions for using the preset architecture from examples to in-depth understanding](../../20-Gameplay Development/14-Preset Gameplay Programming/0-The First Preset Mod/0-Create a New Version of Works.md) 
- Technical Manual - Preset API: <a href="../../../mcdocs/3-PresetAPI/Preset Management/PresetApi.html" rel="noopenner"> Preset Architecture API Manual </a> 
2. Preset Architecture: 
- A new code framework consisting of presets, parts, and instances 
- A complete set of preset APIs (please reinstall the completion library after updating Studio) 
- Complete object-oriented architecture! 
- Assembled logic integration method, plug and play, easy to reuse and modularize logic 
- Modify code properties in the editor, automatically distribute some system events, automatically synchronize client/server properties and other advanced features 
3. New version of the editor: 
- Preset editor: for previewing, editing and assembling presets 
- Level editor: completely redone, now the main scene editor, you can place the assembled presets here and adjust them 
- Resource manager: Add a new file wizard for guided file creation, and automatically create supporting files and supplement necessary code 
- Configuration: Use the editor to directly edit the additional package Json, supporting almost all fields of the entity behavior package component 
4. Launcher: 
- Added support for the new version of the editor/editor dual version, now you can upgrade the old version of the work to the new version 
- Added new version of the entry script template, simple shooting template, preset sample template 
- Added news page 
5. Editor: 
- Special effects editor 
- The timeline can now drag the handle 
- The number of bones in the skeleton model has been increased to 70 

## 2021.6.23 Version 0.16.11 

- Fixed issues with the entry script template and the simple design template


## 2021.6.17 Version 0.16.10 

1. Apollo: 
- Optimize the efficiency of the deployment process 
- The official plug-in interface supports search 
2. General: 
- Other problem fixes and experience optimization 

## 2021.6.4 Version 0.16.9 

1. Special Effects Editor: 
- Scrolling the wheel will advance/pull the camera forward instead of changing the camera's FOV 
- The hanging point information supports undo operations 
2. Interface Editor: 
- Added a new grid adjustment method to the grid control - horizontal mode 
3. Apollo: 
- Added verification and automatic repair functions to the pack_id under the worlds folder 
- Optimized the deployment operation in the test phase 
- Supports one-click adjustment of large and small versions of all server types 
4. General: 
- Other problem fixes and experience optimization 

## 2021.5.20 Version 0.16.8 

1. Apollo: 
- Network service mod supports automatic deployment 
- After automatic deployment is turned on, the mod directory is checked regularly, and if changes occur, it is automatically deployed 
- The automatic deployment function can be used for sub-account collaborative development. 
- The hot update function is divided into server hot update and client hot update 
- Support map copy 
2. General: 
- Other problem fixes and experience optimization 

## 2021.5.7 Version 0.16.7 

- Fix several problems and optimize the platform experience. 

## 2021.4.22 Version 0.16.6 

1. Interface Editor: 
- Added more resolution options 
- You can see the actual resolution of the preview window after conversion 
2. Special Effects Editor: 
- The height attribute of the ring sequence frame is adjusted to a floating point value 
3. Apollo: 
- Added prompts for deploying operational data plug-ins during the review and launch stages 
- Support client hot updates 
- Added a toolbox button to the launcher's network service development page 


## 2021.4.15 Version 0.16.5 

1. Map Editor: 
- Added NetEase version optimized structure when saving structure 
- Added built-in materials Shipwreck, Undersea Temple, Forest Mansion 
2. Special Effects Editor: 
- Initial rotation of particles, rotation speed supports y direction 
- Texture and sequence frame properties of particle special effects, modification of texture properties of sequence frame special effects can display results in real time 
- Added delayed start playback properties for particles and sequence frames 
- Scene special effects color modification takes effect in real time 
- Particle emitter supports cone 
- Special effects can choose not to destroy emitted particles when stopped 
- Sequence frames support Add mixed mode 
3. Launcher: 
- Added java forge 1.16 version 
4. General: 
- Added mobile debugging function to view logs of PC and mobile terminals (currently only including Android) and manage mods loaded by the game and adjust the file data in the application. For details, please refer to the debugging tool description in the document. 
- Added a "custom dimension" template to the Bedrock Edition component 
- Added a mini-game template to the network server template 
- Disabled the function of switching the drop-down box options when the mouse is on the drop-down box 
- Other issues fixed 

## 2021.3.25 Version 0.16.3 

1. Map Editor: 
- The camera component no longer affects the game mode of the map editor 
- Text prompts will appear when visibility is too low 
2. UI Editor: 
- The position and size of general features support new writing methods, support new features such as transparency 
- Text and image controls support new features 
- The appearance of the zoom function is optimized 
3. General: 
- Optimize the undo operation of the slider in the property panel 
- When closing the editor, you can choose not to save changes to the map 
- When importing some resources, a resource import progress pop-up window will appear 
- When the embedded game crashes, a crash feedback pop-up window will pop up (you will be able to give us direct feedback on the crash here) 
- Optimized the stretching logic of the property window 
- You can choose the beta version code base 
- Added custom scene examples to the 1.22beta version offline documentation 

## 2021.3.16 Version 0.16.2 

1. The modpc package and the beta launcher support the 1.22beta version 

## 2021.3.11 Version 0.16.1 

1. Map Editor: 
- Added the option to copy/paste air in the clipboard 
2. UI Editor: 
- Added import prompts when the paper doll model is missing

3. Special Effects Editor: 
- Supports exporting parameters of special effects attached to models 
- Particles/sequence frames support being more transparent the closer to the camera 
- Hanging points and special effects list support deleting special effects with the del key 
- When particles expand emitter properties, the shape of the emitter is displayed 
4. Launcher: 
- After the 1.22beta version is released (expected on March 15), developers can download the 1.22beta version of the ModPC development package and the beta version launcher 
5. General: 
- During the Apollo launch phase, the server supports the option to deploy the approved version without re-review 
- Tutorials will be enabled when new users log in 
- In the settings, select whether to display the Mod UI in the special effects editor and map editor 
- In the resource manager, you can right-click the file to open the directory where it is located 
- The drop-down box in the property panel supports switching entries by using the up and down keys on the keyboard 
- You can enable the beautiful images of the embedded game in the settings 
- "Assertion interrupts in the debugger" is not checked by default for development and testing 
6. Fix the following issues: 
- The special effects editor opens the wrong folder where the texture is located 
- The anvil problem of the mod pc development package 
- The editor startup failure problem in some cases 
7. Performance: 
- Improve the startup speed of development and testing 
- Optimize the time-consuming large-scale undo and redo 
- Optimize the jamming of the first input command in the embedded game 
- Optimize the jamming of large creature placement 
- Optimize the performance of the statistics block 

## 2021.1.28 Version 0.16.0 

1. Map Editor: 
- The material list supports more blocks. 
- Material expansion. 
2. UI Editor: 
- The window supports zooming and dragging. 
- Add text line spacing properties. 
- UI images support configuration as native images. 
3. Special Effects Editor: 
- The first-person model preview supports left-click events. 
- Particle survival time supports two decimal places. 
- The native model supports setting the location and coordinates of hanging points in the world. 
- Property changes can now be undone. 
- When using shapes to emit particles, the shapes will be rendered using wireframes. 
4. Launcher: 
- Works that have been developed and tested will be displayed in the recent list. 
5. General: 
- Added cloud switches in the settings. 
- Optimized fbx file import and export. 
- Multiple actions can be exported in one fbx file. 
- When creating a new work, the birth point coordinates support negative numbers. 
- Added a reminder to back up the work. 
6. Fixed the following issues:

- Model size cache problem. 
7. Other optimizations: 
- Resource manager performance when copying a large number of files. 
- Rendering block generation. 
- Map editor edit mode interface optimization. 
- Resource manager text color adjustment. 
- Emitter property names and prompts in the special effect editor. 
- Test log and server log search optimization. 

## 2021.1.22 Version 0.15.9 

1. General: 
- ModPC development kit upgraded to version 1.21. 

## 2021.1.7 Version 0.15.8 
1. Special Effect Editor: 
- Removed redundant protagonist model configuration, unified use of the attachment model option in the attachment point properties. 
- When importing bbmodel models, block item textures are now optional. If not set, the textures provided by the model file are used. 
2. Interface Editor: 
- Control property names can be fully displayed by default.
3. Map Editor: 
- In edit mode, three mirror flip operations are supported. 
4. General: 
- Optimize log search, add case matching, regular matching, and full word matching functions. 
- The input box in the editor interface now selects all by default when clicked. 
- The editor interface supports Tab key control focus. 
- In the launcher settings, increase the frame rate limit of the editor game window. It is recommended to turn it on on low-configuration computers. 
5. Others: 
- Optimize the default visibility in the editor under different circumstances. 
- Several stability and detail optimizations. 

## 2020.12.24 Version 0.15.7 
1. Special Effects Editor: 
- The timeline supports forward and backward frame-by-frame playback. 
2. Interface Editor: 
- Added item rendering controls to support displaying items on the interface. 
3. General: 
- You can now click on the coordinate axis to rotate the view. 
- Optimize the performance of the built-in resource manager when operating a large number of files. 
- Optimize the performance of the drop-down list in the special effect editor. 
4. Others: 
- Fixed the editor freezing in some cases. 
- Fixed the game window not being displayed in the editor in some cases. 
- Fixed several issues that caused the editor to crash. 

## 2020.12.10 Version 0.15.6 

1. Special Effect Editor: 
- You can now use the scroll wheel to control the distance of the view. 
- Particle orientation supports horizontal speed direction.

2. Launcher: 
- Added recent tab. 
- Interface adjustment. 
- When editing/running a work, you can restore the default game settings. 
- The editor type when each work is exited will now be recorded. 
- Mail content supports links. 
3. General: 
- Paste attribute optimization. 
- The map editor material import model supports FBX texture parsing. 
4. Fixed the following issues: 
- The editor freezes in some cases. 
- The embedded game cannot be started in some cases. 
- Several issues that cause the editor to crash. 

## 2020.11.26 Version 0.15.5 

1. Map Editor: 
- In the editing environment, the Enter key can be used to confirm the generation. 
- The length of the unified material name is 10 characters. 
- The fill tool pop-up window supports the Esc key to close. 
- The material library will no longer display the button such as Confirm Generation when the material is not placed. 
- Fixed some incorrect material names. 
- Blocks such as podiums, campfires, bells, portals, etc. can now be rendered normally in the editing state. 
- Adjusted the transparency of the selection area when selecting, and now you can see the selection content more clearly. 
2. Special Effects Editor: 
- The perspective button can display the selected state normally when entering for the first time. 
- Added a depth test switch. 
3. Interface Editor: 
- When a control cannot add sub-controls, the add button is grayed out. 
- Controls in the control list now support F2 key renaming. 
- Resource management will now refresh automatically. 
- After right-clicking the control, click the Copy Path button to copy the control path. 
4. General: 
- Adjusted the rules for generating thumbnails for works. 
- Optimized the process and prompts for creating new works. 
- Now when the focus is in the game, you can also press Ctrl+S to save. 
- Now there is a clearer prompt when the SDK installation fails. 
- Now you can see more work information when modifying the work configuration. 
- Optimize the prompts of several interfaces. 
- The Apollo application entrance is now more obvious. 
- Add a toolbox entrance to the network service page. 
5. Fix the following problems: 
- In some cases, the editor automatically becomes the foreground application. 
- The mortgaged items in the trading component can be zero or negative. 
- In some cases, mount scaling does not take effect. 
- In some cases, the material library exports Obj files, causing the editor to be unresponsive. 
- The material library does not support Chinese paths when importing model files. 
- Several editor interface problems. 
- In some cases, the editor or engine crashes. 
- When editing large interface files, adding components is stuck.


## 2020.11.12 Version 0.15.4 

1. Map Editor: 
- You can choose the direction when placing redstone, rails, and beds. 
- Optimize the preset interface of materials. 
- When pasting from the clipboard, the most recently copied content will now be selected. 
- You can now start the game test directly from the map editor. 
2. Special Effects Editor: 
- Optimize the timeline performance. 
3. Interface Editor: 
- When the mouse hovers over the texture properties, the image path is displayed. 
- Support setting the game resolution (aspect ratio). 
- You can also start the game test without a canvas. 
4. General: 
- The resource manager supports shortcut renaming and deletion. 
- The import button of the resource manager is merged. 
- Improve the game startup speed in the editor. 
5. Fix the following issues: 
- In some cases, Studio cannot be started (disappears after double-clicking the icon). 
- Fixed some template errors. 

## 2020.10.29 Version 0.15.3 

1. Map Editor: 
- Optimized large-size selection operations. 
- Added time setting function. 
2. Level Editor: 
- Component and creature lists support multiple selections and shortcut key operations. 
- Optimized performance when there are many components. 
3. Special Effect Editor: 
- Hanging points can be used in all actions. 
- Optimized rotation operations. 
4. Interface Editor: 
- Batch operations now support undo. 
- Optimized the reading speed of large interfaces. 
5. General: 
- Support Python code hot update, see [Debug Information] (../../20-Gameplay Development/13-Module SDK Programming/2-Python Script Development/0-Script Development Introduction.md#How to Debug). 
- Optimized interactive feedback. 
- Fixed the problem of editor freezing in some cases. 
- The resource manager supports image preview. 
- Overall performance optimization. 

## 2020.10.26 Version 0.15.2 

1. Fixed the following issues: 
- In some cases, the startup program is unresponsive. 

## 2020.10.15 Version 0.15.1


1. Launcher: 
- The component versions in each template have been updated to the latest version. <!--by leiyaoyao--> 
2. Map Editor: 
- Optimize memory and performance of large-size operations. <!--by liukun--> 
3. Level Editor: 
- Support modifying the id, resources and other properties of custom creatures at any time. <!--by leiyaoyao--> 
- Enriched the resource options of biological components. <!--by leiyaoyao--> 
4. Special Effects Editor: 
- Added first-person model modification, which is used to modify the first-person display model of the character. For details, please refer to [First-person Model Modification](../../16-Art/9-Special Effects/5-First-person Model Modification.md). <!--by guoxun--> 
- Standardized Steve's name to Steve. <!--by guoxun--> 
5. Interface Editor: 
- Optimize the efficiency of creating controls. <!--by panlei--> 
- Support copying, pasting, and dragging of controls across canvases. <!--by panlei--> 
- Standardize the name of PaperDoll to PaperDoll. <!--by panlei--> 

## 2020.09.24 Version 0.15.0 

1. Launcher: 
- Add export settings. 
2. Map Editor: 
- Fine-tune some interfaces. 
3. Level Editor: 
- Newly created biological components use zombie models by default. 
- The recipe output quantity setting takes effect. 
4. Special Effects Editor: 
- Support dragging special effects Json from the file manager to the hanging point. 
- Support dragging pictures from the file manager to particle properties. 
- Support previewing custom sequence frames. 
5. Interface Editor: 
- Optimize the dragging performance of controls and support dragging multiple controls at the same time. 
- Optimize control properties. 
- Support control duplication and inheritance. 
- Performance optimization 
6. Improve the download speed of PC development kit. 
7. Fix the following issues: 
- In some cases, the editor cannot be awakened normally. 
- In some cases, the UI editor is stuck. 
- In some cases, the editor has a white screen. 
- The special effect editor cannot process some Json files correctly. 

## 2020.09.10 Version 0.14.7 

1. Map Editor: 
- Extended brush tools, added single point, cylinder, and hemisphere brushes, see [Brush Function](../../14-Map Making/2-Map Editor Instructions.md#Brush Function) for details. 
- Added terrain tools, including 5 types of terrain such as fill, ridge, and plant, see [Terrain Function](../../14-Map Making/2-Map Editor Instructions.md#Terrain Function) for details. 
2. Level Editor: 
- Add "Add Component" button in the toolbar. 
3. Special Effects Editor:

- The perspective of the game area is adjusted to right-click operation. 
- Added random playback settings for particle effects, see [Sequence frame random playback shuffle](../../16-Art/9-Special Effects/10-Detailed Property Description.md#Sequence frame random playback shuffle). 
4. The editor has added a feedback function, the entry is located in the menu "Help" -> "Feedback". 
5. Fixed several bugs. 

## 2020.08.27 Version 0.14.6 

1. Launcher: 
- Supports quick release of components to the platform, the entry is located in the "More" menu on the work page, see [Publish Works](../../12-Getting Started Tutorial/20-MC%20Studio Instructions.md#Publish Works). 
- Updated the simple interface logic template, demonstrating the use of various interface controls (such as buttons, text input boxes, etc.). 
3. Level Editor: 
- Added portal component, which can quickly configure functions similar to nether portal. The entrance is located in level editor component->dimension->custom portal. 
4. Added "weather" setting item in the editor, the entrance is located in editor work menu->settings->embedded game->weather 
- After turning on the weather, you can modify the weather of the editor embedded game through instructions. 
5. Added editor usage instructions: 
- Click the "?" button in the upper right corner of the editor to open the corresponding web page of the editor. 
- Move the mouse to the "?" button in the upper right corner of the editor window to display the introduction of the corresponding function. 
6. Fixed the following bugs: 
- When the editor is not started, it still prompts that the process already exists. 
- The copy all log function in the script test log window is invalid. 
- Modifying the Json file requires starting the game multiple times to take effect. 
- In the map editor game mode, the mouse pointer is not displayed when the backpack interface is opened. 

## 2020.08.13 Version 0.14.5 

1. Launcher: 
- Support Minecraft Java Edition 1.15. 
- The Bedrock Edition network server displays the proxy server and control server addresses. 
2. Map Editor 
- Optimize the block model import function. 
3. Level Editor: 
- Components involving items support richer item types. 
- Optimize the operation of component midpoints and area coordinates. 
- Support preview of custom blocks. 
4. Special Effects Editor: 
- Optimize the group preview effect. 
- Support batch import of FBX models. 
5. Interface Editor: 
- The Nine-square grid supports both the old version and the original version. 
- Add configurable properties to the text input box. 
6. The configuration items are placed in a unified settings interface. 
7. Fix the following bugs: 
- The map editor number keys cannot quickly select materials.
- Some feature generation timings of custom feature components in the level editor are invalid.