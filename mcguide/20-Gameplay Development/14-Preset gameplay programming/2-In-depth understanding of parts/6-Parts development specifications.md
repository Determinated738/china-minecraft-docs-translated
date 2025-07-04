# Parts Development Specifications 

## Directory and Naming 

When using the editor to create a part, a folder with the same name as the .part file will be created in the Parts folder under the behavior pack directory (if there is no folder, it will be created automatically. Hereinafter referred to as the behavior pack Parts directory). The three files related to the part are all in this folder, see [0-Parts Development](0-Parts Development.md). Once the folder is determined, it is not recommended to rename it, otherwise the part will become invalid. 

Since the normal operation of the mod's script files depends on the script directory where modmain is located, the parts folder will be linked to the Parts folder under the first script directory in the currently edited mod (hereinafter referred to as the script Parts directory) as a shortcut to ensure the normal operation of the part code. When the mod is exported in the studio, the shortcut will be cut off, and the parts folder under the behavior pack Parts directory will be completely copied to the script Parts directory. At the same time, the parts folder under the behavior pack Parts directory only retains the .part file, and the parts folder under the script Parts directory retains two python files. 

## Reserved fields 

The following fields are member variables used by the part base class. Developers overwriting these reserved fields may lead to unknown consequences. Please avoid using them. 

- id 

- classType 

- isClient 

- filterKeys 

- _parent 

- entityId 

- boxId 

- name 

- transform 

- isRemoved 

- loaded 

- needUpdate 

- directoryPath 

- tickEnable 

- data 

- dataKeys 

- eventMap 

- replicated 

## Import and development specifications 


- Only support modification in the function of the main class of the part, and cannot be imported in the header of the main class 

- Since the part class will also execute initialization logic in the editor, but the editor and engine operating environments are different, in order to avoid errors affecting developers, try to avoid writing logic in the initialization function of the part. 

- Although there is only one part code, it is divided into two instances, client and server, when the game is running. Therefore, developers need to always pay attention to the separation of client part code and server part code to avoid the problem of client part code calling service point SDK interface. 

- Since the part needs to run in the game code and editor code, the part code needs to be compatible with python2 and python3 environments. 

