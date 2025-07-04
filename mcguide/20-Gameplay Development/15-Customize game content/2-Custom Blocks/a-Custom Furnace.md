--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Furnace Demo 

### Overview 

[CustomFurnaceMod](../../13-Module SDK Programming/60-Demo Example.md#CustomFurnaceMod) replicates the UI and logic of the original furnace using custom blocks and ModSDK related events and interfaces. 

**Note: The demo uses the PE size. Changing the window size on PC may cause a certain display error in the backpack interface** 

### Supported functions 

- A custom block 
- Clicking this block will open the furnace interface 
- The interface includes the following functions: 
- The interface is consistent with the original furnace 
- The backpack in the interface can normally display the items in the player's backpack 
- Click the backpack grid, then click the input grid, you can exchange the items in the two grids 
- Click the backpack grid, then click the fuel grid, you can exchange the items in the two grids 
- When there are items in the fuel grid and the input grid, and the item combination exists in the configuration, consume the fuel and input after a certain period of time, and generate 1 item in the output grid 
- There is a flying animation when exchanging items 
- There is a corresponding flame burning animation and progress animation when burning 
- When the output grid items reach the stacking limit, stop generating 
- Items in the input grid, fuel grid, and output grid will be stored in the blockentity, and will continue to be smelted even if the furnace is not turned on. 

### New features in 1.18 

- Long press to split the stack 
- Double-click to merge the stack 
- Click the item grid to display tips 
- Equipment durability display 
- Item enchantment status display 
- Correctly display disaster flags and various flags woven by looms 
- After clicking the item grid, click somewhere else to discard the item 
- The items in the block will fall after the block is destroyed 
- The UI is closed correctly after the block is destroyed and the player dies 
- The UI can be correctly updated when obtaining items with the UI open 
- When generating items, the developer no longer needs to control the maximum number of stacks generated, and can directly obtain them through the corresponding interface 

### Introduction to the main files of Demo


- recipeMgrBase.py 
- Implement the management of the smelting recipe base class. One type of custom furnace block corresponds to a furnace recipe class. The furnace recipe class inherits from this base class and needs to implement the following basic interfaces: 
- `GetFurnaceResult(self, inputItem)`: Return the product based on the raw material 
- `GetBurnDuration(self, fuelItem)`: Return the fuel burning time based on the fuel 
- `IsFuelItem(self, item)`: Determine whether the incoming item is fuel 
- The smelting recipe and combustion list are configured when each subclass is initialized. If the fuel is not in the smelting list, it cannot be placed in the fuel slot 
- furnaceMgrBase.py 
- The furnace management base class implements the smelting logic of the furnace. It is necessary to tick the custom furnace block in the ServerBlockEntityTickEvent event. The main smelting judgment is performed in the Tick function. If the UI or data changes after the Tick ends, the client UI and the server blockEntityData need to be updated 
- A type of custom furnace block corresponds to a furnace management class. The furnace management class inherits from this class and needs to implement the following interfaces: 
- `CanBurn(self)`: Determine whether smelting is possible 
- `Burn(self)`: Smelting process, consuming raw materials to generate burning materials 
- `CanSet(self, slotName, item)`: Pass in the slot name and item, and return whether it can be placed 
- customFurnaceServer.py 
- Custom furnace server, inherited from CustomContainerServerSystem, the base class implements the functions of opening containers, destroying containers, and basic exchange and discarding items. The following interfaces need to be implemented in the subclass 
- `GetCustomContainerItems(self, dimension, blockName, blockPos)` Pass in the data of the custom container block and return all item information in the container 
- `OnCustomContainerItemSwap(self, playerId, fromSlot, fromItem, toSlot, toItem)` is called when the exchanged items involve a custom container. Return True to allow exchange, return False to prohibit exchange. When the exchange is successful, the blockEntityData of the corresponding container block needs to be updated. 
- `ResetCustomContainer(self, dimension, blockName, blockPos)` is called when the custom furnace is destroyed. The corresponding furnaceManager needs to be deleted under this function. 
- `OnCustomContainerItemDrop(self, playerId, slot)` is called when the custom container item is dropped. Return True to allow drop, return False to prohibit drop. When the drop is successful, the blockEntityData of the corresponding container block needs to be updated. 
- OnBlockEntityTick: Implement the tick logic of the custom furnace under this event. 
- customFurnaceClient.py 
- OnCustomFurnaceChanged handles the smelting state change event sent by the server, including the burning state change and the furnace data change, and updates the UI display. 
- OpenCustomFurnace handles the UI opening event sent by the server. 
- OnItemSwap handles the item exchange event sent by the server. 
- customFurnaceUI.py 
- Manage the furnace interface, inherited from CustomContainerUIScreenBase, and need to implement the following interfaces 
- `InitCustomContainerUI(self, args)`: Initialize the UI of the custom container. In the demo, the UI of the three slots of input, fuel and generation in the custom furnace is initialized 
- `UpdateCustomContainerUI(self, args)`: Update the UI of the custom container. In the demo, the combustion status, fuel data and UI of the custom slot are updated 
- `Update(self)`: This function is called every frame. You need to execute the parent class's Update first, and then implement your own Update logic. The parent class Update implements the flight animation when exchanging items. 
- modConfig.py 
- The following data needs to be configured in this file 
- BURN_INTERVAL: burning time interval, int, unit seconds, each time this interval passes, items can be smelted and generated. Currently, it is unified for all furnaces. Developers can modify it if necessary. 
- FLY_ANIMATION_DURATION: flight animation time interval, int, unit frame, developers can configure the number of frames according to the desired form of expression 
- CUSTOM_CONTAINER_LIST: list, stores the identifier of all custom furnace blocks 
- FURNACE_SLOT_NUM_DICT: dict, stores the number of custom slots corresponding to all custom furnace blocks, at least 3 (one each for raw material slot, fuel slot and generation slot). The current architecture only supports 1 generation slot + 1 fuel slot + n raw material slots (greater than or equal to 1) 
- FURNACE_SLOT_PREFIX: Custom furnace slot prefix, used for naming in UI files, must strictly meet the "prefix + number" format, such as `furnaceSlot0`. In this demo, serial number 0 is the generation slot, 1 is the fuel slot, and greater than 1 is the raw material slot. 
- UI_DEFS: The UI correspondence of the custom container, which is a dictionary type. The key is the identifier of the custom block corresponding to the custom container, and the value is its configuration, including the following fields. 
- `uiName`, corresponding to the json file name of the ui (excluding .json) 
- `uiClassPath`, corresponding to the ui management class of the container 
- `uiScreenDef`, corresponding to the root node of the UI 
- furnaceManagerFactory.py 
- Furnace management factory class, create different furnace management classes according to the block name. If the developer needs to create different custom furnaces, the corresponding factory generation method needs to be added here 

### UI implementation details 

- neteaseCommonUI.json 
- This file provides some template controls, such as itemBtn, which can be used as backpack grids or furnace grids. 
- These controls can be used through inheritance, refer to `furnaceSlot0` in customFurnaceUI.json

- Backpack interface 
- ScrollView sliding window 
- Window content is arranged in Grid 
- Grid template component is mainly divided into 4 parts, the control template can be reused, refer to custom furnace slot 
- ImageButton is responsible for corresponding click 
- Image is responsible for displaying click status 
- Label is responsible for displaying stacking number 
- ItemRenderer is responsible for displaying item rendering 
- Tips of item information when clicking use alpha attribute to control transparency, and control the alpha attribute through binding to achieve fading effect 
- Furnace interface 
- Furnace slot is implemented with Grid template component 
- Flame and smelting progress call SetSpriteClipRatio new image clipping interface to realize burning animation 
- Flying animation 
- Use an imagePool to manage the flying ItemRenderer, display it when exchanging items and hide it at other times, and call SetPosition in Update to update its position to achieve flying animation effect 
- Others 
- Background image uses Image native nine-square clipping 

### Based on Demo extension development process (reference) 

Suppose our requirement is to develop a custom furnace with different recipes 

1. Create a custom block and add its identifier to CUSTOM_FURNACE_LIST and FURNACE_SLOT_NUM_DICT of modConfig.py. Since the UI has not been changed, the corresponding number of slots in FURNACE_SLOT_NUM_DICT is also 3 
2. Create a newFurnaceRecipeMgr.py, inherit from the RecipeManagerBase recipe management base class, and implement the three interfaces of GetFurnaceResult, GetBurnDuration, and IsFuelItem. Configure the corresponding recipe list and fuel list in the initialization function. Please refer to furnaceRecipeManager.py 
3. Create a newFurnaceManagerGas.py, inherit from the FurnaceManagerBase furnace management base class, initialize the corresponding recipe management class in the initialization function, and use the recipe management class created in the second step `self.recipeMgr = NewFurnaceRecipeManager()`, and implement the three interfaces of CanBurn, Burn, and CanSet. Please refer to furnaceManagerGas.py 
4. Add the factory creation method corresponding to the custom block name in furnaceManagerFactory.py 

Note: Currently all custom furnaces use the same UI. If you need to add a raw material slot, in addition to changing the above places, you also need to modify the customFurnaceUI.json file to add the UI of the corresponding slot. The naming method must strictly meet the "prefix + number" format, such as `furnaceSlot3` (0, 1, 2 are the generation slot, fuel slot and default raw material slot respectively, and the new slot numbers are added one by one starting from 3). The slot UI can directly inherit `neteaseCommonUI.itemBtn` and place the control node under `rightPanel`. The code is as follows: 

```json 
"furnaceSlot0@neteaseCommonUI.itemBtn" : { 
"$item_button_layer" : 14, 
"$item_button_offset" : [ 42, -16 ], 
"$item_button_size" : [ 32.0, 32.0 ], 
"$item_button_anchor_from" : "center", 
"$item_button_anchor_to" : "center" 
} 
``` 

The data in each field are explained as follows: 

| Field name | Description | Default value | 
| :----------------------: | :---------------------: | :------: | 
| $item_button_layer | Display level | 1 | 
| $item_button_offset | Offset | [0, 0] | 
| $item_button_size | Size | [28, 28] | 
| $item_button_anchor_from | Position of the parent node anchor | "center" | 
| $item_button_anchor_to | The location of the anchor point itself | "center" | 


### Extended development process based on Demo (new) 

Now our custom furnace demo can be used for any container that needs to be implemented by a backpack. For example, we now create a custom box with no other logic, which is only used to store items. The reference development process is as follows: 

1. Create a custom block and add its identifier to CUSTOM_CONTAINER_LIST in modConfig.py 

2. Refer to the customFurnaceUI.json file and modify the controls under its rightPanel to implement the UI of a box 

3. To implement the corresponding UI controller, you need to inherit the CustomContainerUIScreenBase class. You can refer to CustomFurnaceUIScreen.py. The following two functions must be implemented: 

1. `InitCustomContainerUI()` is used to initialize the UI of the custom container. You need to save the information of all item grids to two variables. After storing the information, the key listening events of the corresponding slots will be automatically registered. The UI of the item grid needs to inherit from itemBtn in neteaseCommonUI. You can refer to the implementation of furnaceSlot0 in customFurnaceUI.json 
1. `self.mBagInfo` stores the information of all item grids in the form of a dictionary, where the key is `slotPath`, which is the path of the UI control, and there are two values, one is the slot name "slot", which is int for backpack slot names and str for custom furnace slot names, **must be strictly followed**; the other is "itme" which stores the itemDict of the item in the item grid. 
2. `self.mSlotToPath` stores the mapping from slot name to ui control path in dictionary form, key is slot name, value is ui control path 
2. `UpdateCustomContainerUI()` is used to update the UI in the custom container, which needs to be implemented in conjunction with the corresponding server event 

4. To implement the corresponding server system, you need to inherit CustomContainerServerSystem, refer to CustomFurnaceServerSystem.py, where the following points must be implemented 

1. In the initialization function, you need to initialize the list of containers that can be opened by right-clicking. Here, CUSTOM_CONTAINER_LIST in modConfig is used for initialization 

```python 
self.mCustomContainer = modConfig.CUSTOM_CONTAINER_LIST 
``` 

2. `GetCustomContainerItems()`, this function will be called in the parent class. It is necessary to implement here to get the information of all items of the custom container from blockEntityData and return a dict, where the key is the slot name (the convention is str in point 3 above), and the value is the item information of the slot, that is, its itemDict 

3. `ResetCustomContainer(self, dimension, blockName, blockPos)`, this function will be called when the placed custom container is destroyed. It needs to handle some reset operations, such as the custom furnace needs to delete the corresponding furnace manager at this time 

4. `UpdateCustomContainer()`, this function will be called when the custom container is opened by right-clicking and when related item exchange operations occur. It is used to update other status information of the custom container except the item slot. For example, the custom furnace updates the burning status and burning animation through this function, and notifies the client to call `UpdateCustomContainerUI()` to update the UI of the custom container through the modConfig.OnCustomContainerChangedEvent event. The parameters passed can be customized by the developer 

5. `OnCustomContainerItemSwap()`, this function will be called when an item is swapped between a custom container and a backpack. The previous slot name convention is used to distinguish which container the item belongs to. You need to return False in this function to prohibit the swap. If you return True to allow the swap, you need to call `SpawnItemToPlayerInv()` or `SetInvItemNum()` to update the item in the corresponding backpack slot and update the data in blockEntityData at the same time. If there are other logic-related, such as a custom furnace that requires a furnace manager to tick the generation and consumption of items, you also need to update the data of the corresponding manager in this function. 

6. `OnCustomContainerItemDrop()`, this function will be triggered when the item in the custom container is discarded. Returning False means that the discard is prohibited. Returning True allows the discard and needs to update the data in blockEntityData before allowing it. If there are other logic-related, such as a custom furnace that requires a furnace manager to tick the generation and consumption of items, you also need to update the data of the corresponding manager in this function. 

