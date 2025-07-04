--- 
front: 
hard: Getting Started 
time: 5 minutes 
selection: true 
--- 

# The concept of plugins 

The essence of plugins is actually very similar to the Chinese version of Addon. 

But it is slightly different from Addon. 

For example, the following is the directory structure of a plugin, which can be compared with Addon. The structure will be introduced in detail in the following chapters, and it is only for reference here. 

``` 
tutorialApolloMod 
behavior_packs 
tutorialBehavior 
developer_mods 
tutorialDev 
tutorialScripts 
resource_packs 
tutorialResource 
worlds 
level 
world_behavior_packs.json 
world_resource_packs.json 
``` 

The plugin will run the code in developer_mods on the server, send the content in behavior_packs to the client, and communicate with the server in both directions. 

Doing so can prevent the code from being reverse engineered, thereby protecting the server-side plug-in code. 

And plug-ins can also call each other and depend on each other, splitting the server gameplay into modules. 

## Why use plug-ins 

The purpose of doing this is - **efficiency**. 

Make small functions needed by the server into plug-ins. For example, make the territory protection function, permission management function, box lock function... into small plug-ins. Although these functions cannot bring core gameplay to the server, they are the cornerstone of a Minecraft network server. By writing plug-ins, these basic functions can be installed and managed on every server, reducing repeated development. 

At the same time, small plug-ins correspond to the concept of modular design. 

If there is a problem with a module and it needs to be improved, it can be easily located and repaired. It greatly improves development efficiency. 

