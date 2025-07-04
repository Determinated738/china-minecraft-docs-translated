--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Understanding Interface Controls 



#### Author: Boundary 



The UI interface is composed of a combination of interface controls. Common controls include buttons, text panels, grids, input boxes, etc. Currently, MCSTUDIO supports the use of interface editors to create UIs. At the same time, it can simulate the effects of UIs on mobile phones, PCs, and tablets according to different resolutions to adapt to the screens of different terminals to the greatest extent. Therefore, this chapter will use the interface editor to help developers understand interface controls and gain a basic understanding of commonly used controls. 



#### Canvas 

The canvas can be regarded as the entrance to the interface. A canvas contains multiple attributes. At the same time, the interface is placed in the canvas content, and it can also be directly adapted to special-shaped screens, so that the interface can be used normally on a variety of screens to the greatest extent. 

#### There are several canvas properties: 

① Always support keys, that is, when this interface is generated, if the player presses a key such as a move key, the character will also move in response to the key effect. 

② Run the game when creating, that is, when this interface is generated, whether the game world behind the interface is rendered on the screen as usual. 

③ Click penetration, that is, when this interface is generated, whether the input will also be responded to on the old interface below after clicking. For example, we generate another new interface on the HUD interface (an interface with a move key and a shortcut bar). When a finger clicks the screen, the new interface will be clicked first. If this property is checked, the HUD interface below will also respond, that is, it is possible to click the move key across an interface. 

④ Replace the pause interface, that is, after this interface is generated, if this property is checked while the pause interface is allowed to pop up, the pause interface cannot be popped up. 

⑤ Limit the cursor movement range, that is, after this interface is generated, the cursor on the PC will only appear within the interface range. After checking, it is very suitable for adapting the interface to the PC Bedrock Edition.

⑥ Force continuous rendering, that is, after this interface is generated, it will still render when the computer resources are too high. If it is not checked, it may not render when the computer computing pressure is too high. 

⑦ Inherit the base class canvas, that is, the interface uses the canvas properties used by most original interfaces. 



#### Drawing board 

The panel can be regarded as a divided block in the interface, which is a regional part. Imagine that in a canvas, we want to lay four buttons horizontally in the upper left corner so that they are close together. The more common method is to use the interface editor to create four new buttons under the canvas control and move them to the upper left corner one by one. Sometimes we want to hide buttons in the control structure to show other areas, or hide these buttons in the code, which may require a lot of extra code. By grouping the controls under the panel and moving the position of the panel, the controls contained in the panel will move together, and when the panel is hidden, they will disappear together. It is more like a folder in a computer file management system. Learning to use panels can separate the functions of an interface into several independent areas, and may also make the control structure and subsequent code writing more concise and convenient! 



#### Button 

Buttons can be clicked by players. In the interface editor, many rich styles can be made by setting the button size and the textures of different pressed states. At the same time, the editor also wraps a text in the button for the developer. If the developer chooses not to draw the text in the button texture, he can choose to use the custom button text function. By default, the button texture will point to none, that is, the original commonly used button texture is used. If the native texture is used, the original textures folder will be opened. After clicking the ui folder, you can see all the original textures, which is convenient for developers to choose their favorite original resources. If you choose to customize, the new texture imported by the developer will appear in the resource manager below. 


#### Note the following points: 

① There are three types of textures used for buttons, namely normal, suspended, and pressed. Normal means seeing the default state of the button, suspended means the state when the pointer is placed on the button, and pressed means clicking the button. 

② Nine-grid refers to the nine-grid stretching principle, which is an advanced method used to process textures in game interfaces to reduce resource usage. For more details, please [check the official tutorial](http://mc.163.com/mcstudio/mc-dev/MCDocs/2-ModSDK%E6%A8%A1%E7%BB%84%E5%BC%80%E5%8F%91/04-Mod%E5%BC%80%E5%8F%91%E8%A7%84%E8%8C%83/2-%E8%B4%B4%E5%9B%BE%E8%A7%84%E8%8C%83%E5%8F%8A%E4%B9%9D%E5%AE%AB%E6%A0%BC%E4%BD%BF%E7%94%A8.html). 



#### Picture 

The picture control will display a picture. You need to select the image type as native or custom to select the resource you want to use. The UV start point and UV size below, the former will determine which end point the image starts from, and the size determines the width from the UV start point, extending downwards, and the length to the right. When customizing particles in the previous chapter, we used the original particle map to see that the Bedrock Edition puts all common particles on a 128x128 size map. Using the UV start point and size is to determine a certain area to display it. 



#### Text 

As the name suggests, the text control is used to display text. Text supports text projection, text color, font size, line spacing, word alignment and other functions. All texts displayed in the original interface rely on it, including controls such as input boxes, which essentially present the content entered by the player in the form of text, and are very important controls. 



#### Text input box 

The text input box allows players to enter text into the box. At the same time, through code monitoring of bound input box interactions and bound input box contents, you can know how to get the content of the text input box in the script. It should be noted that if a new interface uses a text input box, it will block other inputs, such as the movement and jump buttons of the main interface. Therefore, for the interface using the text input box, we should treat it as a static game interface. Just like the original chat interface and backpack interface. 



#### Switch 

The switch control is often used to determine whether a function or state is turned on or off. It only has two states, true and false. The switch control is used extensively in the original setting interface. Therefore, when deciding whether a new interface needs to use such a control, you must know whether you need to set a function to turn on or off. By monitoring the binding switch interaction and button status through code, you can know the status of a switch. 



#### Paper Doll 

The paper doll control is used to render a physical model to the screen. Currently, only player models and FBX 3D models are supported in the editor. Using MODSDK, you can more conveniently set the model's scale, entity type, rotation angle along the Y axis, etc. It is very suitable for displaying physical creatures. 



#### Item Rendering 

The item rendering control is used to render an item on the interface. In the original interface, it is often used where items need to be displayed. Such as the backpack interface, enchantment table interface, anvil interface, etc. The inventory that allows players to put items in these interfaces is essentially an item rendering control mounted under a button. When the button is clicked, the button is pressed. If there is an item in it, the item rendering control mounted under it will display an item prop. 



#### Progress bar 

The progress bar control is often used to display the progress of a certain process. For example, the working progress of a certain machine, the degree of change of a certain state, and so on. The progress bar texture generally uses a complete long texture. Using modsdk, you can set the degree of cutting the picture for the progress bar control, with 1.0 as a complete length. If the cutting degree is set to 0.1 through the interface, only 10% of the progress bar will be displayed. 




#### Scroll List 

Scroll list is often used to slide a content area, which can be a text input box, picture, grid, etc. Imagine the original creation backpack bar, where the items are sorted from the beginning to the end, and the number of buttons displayed far exceeds the range that the screen can accommodate. Using a scroll list, you can only display an area in the middle of the backpack bar, and the rest of the area is slowly presented upward by scrolling the content area. 



#### Grid 

The grid control can help developers bind the control content of other canvases to the grid control. For example, the original big box interface has a built-in grid control, the grid size is 9 grids from left to right, 6 rows from top to bottom, and the content in the grid control points to the inventory button. This makes it convenient for developers to uniformly manage a series of repeated controls, without having to manually create multiple controls and calculate the spacing and arrangement between them in order to achieve similar functions.