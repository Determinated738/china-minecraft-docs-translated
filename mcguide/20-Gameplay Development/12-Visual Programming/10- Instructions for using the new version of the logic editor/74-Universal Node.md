# Universal node 

## Get/set properties 

These two nodes can be used to get and set properties of almost any object 

- Object: get from "who" 

- Key: which property to get 

- Value: the value to get 

![image-20211110221804343](./images/image-20211110221804343.png) 

For example, you can use this node to get the value corresponding to a key in the dictionary 

![image-20211110222644905](./images/image-20211110222644905.png) 

You can also use this node to get an element of a list. As shown in the figure below, fill in 1 in the key to get the second element of the list (the sequence number of the elements in the list starts from 0). 

![image-20211126145506399](./images/image-20211126145506399.png) 

## Calling the Part Interface 

Currently, we have supported almost all the part interfaces. If you still encounter the situation that the part interface is not correct, or the parameters/return values are missing, etc., then you can directly use "Calling the Part Interface" and set it in its property interface. 

- Input parameters: You can add input parameters. The name of the parameter is arbitrary, but the type needs to match the type in the official document as much as possible (if not, you can set it to any) 
- Output port: Similar to the input, the output of the corresponding document 
- Call interface: Fill in the name of the interface 

![image-20211110223110612](./images/image-20211110223110612.png) 

Calling part interface can only be found in the interface of <a href="../../../../mcdocs/3-PresetAPI/Preset object/Part/PartBase.html" rel="noopenner"> PartBase </a>. 

As shown in the figure, you can use partbase and its inherited interfaces. 

![image-20211110223749837](./images/image-20211110223749837.png) 

For example, the following interface. 

![image-20211110224142679](./images/image-20211110224142679.png) 

You can use it directly after making the following simple settings. 

![image-20211110224407274](./images/image-20211110224407274.png) 

## Calling the preset object interface 

It is very similar to calling the part interface. 

![image-20211110224447563](./images/image-20211110224447563.png)

Applicable to all interfaces in the following categories. 

![image-20211110224633204](./images/image-20211110224633204.png) 

![image-20211110224701846](./images/image-20211110224701846.png) 

Note that these interfaces are often not called by the parts themselves, and the calling object cannot be left blank, for example. 

This is the interface of the player object, which can only be called by the player preset (inherited from the player object). 

![image-20211110224828594](./images/image-20211110224828594.png) 

## Calling the preset management interface 

Similar to the above node, it is suitable for direct calling of <a href="../../../../mcdocs/3-PresetAPI/Preset Management/PresetApi.html" rel="noopenner"> PresetApi (Preset Management Interface) </a>. 

![image-20211110224928639](./images/image-20211110224928639.png) 

## SDK component interface 

Similar to the above node, it is divided into two different interfaces: server-side and client-side. 

![image-20211110225234874](./images/image-20211110225234874.png) 

Applicable to the call of the interface of Mod API. 

![image-20211110225314449](./images/image-20211110225314449.png) 

