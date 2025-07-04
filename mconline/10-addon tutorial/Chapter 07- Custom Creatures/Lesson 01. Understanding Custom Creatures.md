--- 
front: 
hard: Getting Started 
time: 15 minutes 
--- 

# Understanding Custom Creatures 

#### Author: Realm 

#### What are Custom Creatures 

The Custom Creatures feature provides developers with a new way of thinking to enrich the creature types in the Bedrock Edition of Minecraft. In the past, modifying the behavior and image of creature AI was an extremely complicated task for MC novice developers. It not only requires developers to have a high level of mastery and understanding of programming languages, but may also have additional requirements for some programming algorithm knowledge. Now, developers only need to learn to master a text editor and have a certain understanding of the JSON language, and then they can cooperate with artists or even create a new creature alone. 

### Add-on function allocation for custom creatures 

#### Resource Pack 

In the Bedrock Edition of Minecraft, the resource pack is responsible for rendering creatures in the game, and will also generate corresponding visual feedback based on the changes in the behavior of the creatures. 

#### Behavior Pack 

Behavior packs control the behavior of creatures in the game, and remind resource packs what kind of animations and special effects to play at the right time. 

#### How to define custom creatures in resource packs 

The resource pack runs in the client and is the entry point for the game to render creature materials, animations, models, etc. The main directory of the material pack is abbreviated as RP below. 

The definition file of the custom creature will be placed in the RP/entity folder. 

![](./images/1_1.png) 

The animation file of the custom creature will be placed in the RP/animations folder. 

![](./images/1_2.png) 



The model files of custom creatures will be placed in the RP/models/entity folder. 

![](./images/1_3.png) 

The rendering controller files of custom creatures will be placed in the RP/render_controllers folder. 

![](./images/1_4.png) 

The animation controller files of custom creatures will be placed in the RP/animation_controllers folder. 

![](./images/1_5.png) 

The sound effect files of custom creatures will be placed in the RP/sounds folder. 

![](./images/1_6.png) 

