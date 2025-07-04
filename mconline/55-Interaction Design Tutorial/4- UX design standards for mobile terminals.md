# Mobile UX Design Standards 

## Positioning of Mobile Screen Areas 

![img](./images/4_1.png) 

Most mobile phones have rectangular screens, so I made a more intuitive area division diagram. Below I will explain some cases of UI design related to the area step by step based on this area division 

### Middle: High-frequency viewing, no interaction 

The middle area is generally used to display the game screen. Unless it is an expanded UI, such as the player's backpack UI, the long-term display UI is usually not placed in the center. When designing the UI in this area, try not to block the player's line of sight and not affect the player's operation. 

### Middle upper/lower: high-frequency viewing and low-frequency interaction 

Because of the existence of the quick inventory bar in the middle and lower area, players need to frequently search for the items in the inventory bar, so the frequency of viewing is high, and switching between items, so players are also more accustomed to clicking on the content in the middle and lower. Some low-frequency interactive UIs can be displayed near the inventory bar, which is convenient for players to view and click. 

### Left and right lower corners: high-frequency interaction 

The left and right lower corners are mainly movement buttons and jump buttons. According to the habits of mobile phone players, the left and right lower corners are relatively the most frequently used UI, especially the lower right corner, which only has a jump button. However, it should be noted that when players fly in creative mode, there will be additional lift buttons. If you do not take this into account, it may cause button overlap conflicts. 

### Left and right upper corners: high-frequency viewing and low interaction 

The upper left corner of the mobile game is the chat box, and the upper right corner currently only has a running and moving state switch, so the upper left and right corners are relatively free, and the upper left and right corners are also above the player's finger control, which will not be blocked by the finger, nor will it be blocked by other original UI, so it is very suitable for placing some high-frequency viewing but low-frequency interaction content, such as small maps, player status information display bar and other UI. 

## Common UI recommended placement positions 

### Level 1 menu button: upper right edge 

There are no buttons on the upper right side of the original version. Just be careful not to overlap with the switch sports mode button. In addition, since the player moves the button relatively, the jump button on the right is not clicked that frequently, so it is more convenient to perform more complex key operations. 

However, please note that the lower middle position on the right is still easy to touch by mistake, so it is better to place the level 1 menu button in the upper middle position. 

### Player attribute information: upper left/above the quick item bar 

The basic attribute values of the player need to be checked frequently, such as health and hunger values. This must be placed where the player can see it at any time. According to the player's habits, it is most reasonable to place it in the original blood position, but this area is only suitable for placing some simple small UIs such as blood bars. If the height of the UI is too high, it will block a large part of the game perspective. So if you need to make a large attribute display box, you can consider placing it in the upper left corner. While having a larger position, it will not block too many important game views. 

### Minimap: Upper right/upper left 

The minimap is a type of UI content that occupies a relatively large area, and players check it frequently, so it needs to be displayed in a convenient location. The upper left and right corners of the screen are very suitable for this type of UI display, without a lot of original UI blocking, and it will not be operated by mistake. 

However, for relatively large-occupying UI, it is best to provide a UI function that can be hidden and folded, and this UI can be hidden when the player clicks it. 

### Skill button: around the jump button 

Many components with RPG elements have skill settings. The most suitable place on the mobile phone screen is near the jump button. You can refer to moba games and make it next to the jump button, or it can be simpler and make it a little above the jump button. 

It is also a high-frequency interaction area. The jump button does not require a long click to control, while the move button requires a long click to control, so this type of skill that needs to be clicked is more recommended to be placed in the lower right corner of the jump button. 


### Settings button: middle and upper 

In most cases, players will not click the settings button at any time, so it can be placed in a more eye-catching place, but not easy to touch by mistake. The original settings button is also in the middle and upper, so that players will definitely notice the component settings button and click it to view it as long as they operate the original menu. 

## Common issues that need attention 

### Common mobile phone resolutions and adaptation methods 

First, we can test various resolutions in the Minecraft developer workbench, make good use of the preset resolutions and custom resolutions in it, and try to test several extreme screen ratios. 

### Adaptation of special-shaped screens 

Common special-shaped screens include bangs and rotating hole screens. 

### Allow players to dynamically adjust the position of buttons 

This can add a custom button position in the settings, which can facilitate players with various key habits to challenge the button position they need, and also facilitate players to add multiple component UI position adjustments to avoid conflicts. 

### Learn from popular mobile games (reduce players' learning costs) 

The mobile games recommended here must be popular enough so that players can adapt to their operating habits more quickly. If possible, try to find 3D mobile games to learn their button layouts. For example, the shooting chicken game that everyone played some time ago has a lot to learn from, including the button layout and button size distribution.