--- 
front: 
hard: Getting Started 
time: minutes 
sidebarDepth: 1 
--- 

# <span id="UI API"></span>UI API 

Below are some API interface documents for UI. For the use of UI, please refer to [UI Usage Document](30-UI Instructions.html). 

The following document is divided into two parts, one is in extraClientApi, and the other is the member function of the ScreenNode base class. 

<span id="extraClientApi"></span> 
## extraClientApi 

Some UI-related interfaces are distributed in <a href="../../mcdocs/1-ModAPI/Interface/Custom UI/General.html" rel="noopenner"> ExtraClientApi's General UI Interface </a>. 

<span id="ScreenNode"></span> 

## ScreenNode 

Some useful functions of ScreenNode and how to obtain the interface Node are described in detail in [UI Usage Document](30-UI Description Document.html). 

```python 
import mod.client.extraClientApi as clientApi 
uiNode = clientApi.GetUI("myModName", "myUIName") 
``` 

Assume that in the following function, uiNode is the inherited class of ScreenNode, and the called UI interface is organized according to the following node tree structure 

``` 
my_namespace 
| main 
| image 
| image_button 
| text1 
| panel 
| text2 
| panel2 
| text_edit_box 
``` 

<span id="ChangeBindAutoScale"></span> 
### ChangeBindAutoScale 

- Description 

Set whether the UI of the bound entity is dynamically scaled according to the distance between the bound entity and the local player. **Only effective for the UI interface of the bound entity. For details on how to bind the UI to the entity, see [Create UI interface](30-UI instruction document.html#Create ui interface)** 


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| autoScale | int | 1: Dynamic scaling 0: No dynamic scaling | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful True: Success False: Failure | 

- Example 

```python 
succ = uiNode.ChangeBindAutoScale(1) 
``` 

<span id="ChangeBindEntityId"></span> 
### ChangeBindEntityId 

- Description 

Modify the bound entity id, **only effective for the UI interface of the bound entity, how to bind the UI to the entity, see [Create UI interface](30-UI description document.html#Create ui interface)** 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| entityId | str | Bound entity id | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful True: Success False: Failure | 

- Example 

```python 
succ = uiNode.ChangeBindEntityId(entityId) 
``` 

<span id="ChangeBindOffset"></span> 
### ChangeBindOffset 

- Description 

Modify the offset between the bound entity, **only effective for the UI interface of the bound entity, how to bind the UI to the entity, see [Create UI interface](30-UI description document.html#Create ui interface)** 


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | offset | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful True: Success False: Failure | 

- Notes 
- It is not recommended to set the offset of the local player binding UI to (0, 0, 0) in the first-person perspective 

- Example 

```python 
succ = uiNode.ChangeBindOffset((0, 3, 0)) 
``` 

<span id="Clone"></span> 
### Clone 

- Description 

Clone an existing control, modify its name, and attach it to the specified parent node. Currently, cloned controls of text, image, and button controls perform normally, but cloned controls of other complex controls may have operational problems. It is recommended to manually copy a copy of the corresponding control for use during json writing. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Control path starting from the main node | 
| parentPath | str | Control path of the parent node starting from the main node | 
| newName | str | Name of the new control created after successful cloning, the path of the new control is parentPath/newName | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the cloning is successful | 

- Example 

```python 
# we want to clone text2 named text3 on panel 
parentPath = "/panel" 
text2Path = "/panel/text2" 
text3Name = "text3" 
uiNode.Clone(text2Path, parentPath, text3Name)

``` 

<span id="GetAllChildrenPath"></span> 
### GetAllChildrenPath 

- Description 

Get the path list of all child nodes 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| parentPath | str | The control path of the parent node starting from the main node | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(str) | Returns the path of the child nodes under the parent node, and will recursively return all child nodes. If the node has no child nodes, an empty list is returned | 

- Example 

```python 
# get panel's all children path 
node.GetAllChildrenPath("/panel") 
``` 

<span id="GetBaseUIControl"></span> 
### GetBaseUIControl 

- Description 

Get the BaseUIControl instance based on the path 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| path | str | Path of the current control | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| BaseUIControl | BaseUIControl instance corresponding to the path | 

- Example 

```python

# Get the BaseUIControl instance according to the path 
text2Path = "/panel/text2" 
text2UIControl = uiNode.GetBaseUIControl(text2Path) 
``` 

<span id="GetBindAutoScale"></span> 
### GetBindAutoScale 

- Description 

Get whether the UI of the bound entity is dynamically scaled. The unbound UI will return the default value 1 

- Parameters 

None 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | 1: Dynamic scaling 0: No dynamic scaling | 

- Example 

```python 
autoScale = uiNode.GetBindAutoScale() 
``` 

<span id="GetBindEntityId"></span> 
### GetBindEntityId 

- Description 

Get the entity id bound to the UI. Unbound UI will return the default value None 

- Parameters 

None 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | Bound entity id | 

- Example 

```python 
entityId = uiNode.GetBindEntityId() 
```


<span id="GetBindOffset"></span> 
### GetBindOffset 

- Description 

Get the offset of the UI bound entity. Unbound UI will return the default value (0, 0, 0) 

- Parameters 

None 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Offset | 

- Example 

```python 
offset = uiNode.GetBindOffset() 
``` 

<span id="GetChildrenName"></span> 
### GetChildrenName 

- Description 

Get the name list of child nodes 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| parentPath | str | is the control path of the parent node starting from the main node | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(str) | Returns the name of the child node under the parent node. It will not recursively return all child nodes. If the node has no child nodes, it returns an empty list | 

- Example 

```python 
# get panel's children name 
node.GetChildrenName("/panel") 
``` 


<span id="GetIsHud"></span> 
### GetIsHud 

- Description 

Get the input mode of this interface 

- Parameters 

None 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Return 1 means that the interface does not block game operations, and return 0 means it blocks. | 

- Example 

```python 
# We need to get the input mode of this interface 
isHud = uiNode.GetIsHud() 
``` 

<span id="GetRichTextItem"></span> 
### GetRichTextItem 

- Description 

Return a rich text control instance 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Starting from the main node, the path inherited from the rich_text.RichTextPanel control | 

- Return value 

None 

- Example 

```python 
# we want get a rich-text-item 
richTextPath = "/RichTextPanel" 
richTextItem = uiNode.GetRichTextItem(richTextPath) 
``` 

<span id="RemoveComponent"></span>

### RemoveComponent 

- Description 

Dynamically delete a control 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Path of the control to be deleted starting from the main node | 
| parentPath | str | Path of the parent node's control starting from the main node | 

- Return value 

None 

- Example 

```python 
# we want to remove text2 
text2Path = "/panel/text2" 
parentPath = "/panel" 
uiNode.RemoveComponent(text2Path, parentPath) 
``` 

<span id="SetIsHud"></span> 
### SetIsHud 

- Description 

Set the input mode of this interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| isHud | int | Setting 1 means that the interface does not block game operations, and setting 0 means blocking. | 

- Return value 

None 

- Example 

```python 
# We need to set this interface to HUD operation mode 
uiNode.SetIsHud(1) 
``` 


<span id="SetRemove"></span> 
### SetRemove 

- Description 

Delete this interface node 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
# we want to remove this screen 
uiNode.SetRemove() 
``` 

<span id="SetScreenVisible"></span> 
### SetScreenVisible 

- Description 

Set whether to display this interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| visible | bool | False means hiding this interface, True means showing this interface | 

- Return value 

None 

- Example 

```python 
# We hide the current UI interface 
uiNode.SetScreenVisible(False) 
``` 

<span id="SetSelectControl"></span> 
### SetSelectControl 

- Description


Set the control where the focus is located this year 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The path of the control to be selected starting from the main node | 
| enable | bool | True selects the control represented by componentPath, false deselects it | 

- Return value 

None 

- Example 

```python 
path = "/text_edit_box0" 
uiNode.SetSelectControl(path, True) 
``` 

<span id="SetStackGridCount"></span> 
### SetStackGridCount 

- Description 

Set the size of the StackGrid control 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Starting from the main node, the path of the Grid control | 
| count | int | Set the number of contents of the StackGrid | 

- Return value 

None 

- Example 

```python 
# we want change stackgrid count 
stackgridPath = "/stack_grid1" 
uiNode.SetStackGridCount(stackgridPath, 3) 
``` 

<span id="SetUiEntity"></span> 
### SetUiEntity 


- Description 

Set the biological model that the PaperDoll control needs to display. For details on how to configure the PaperDoll control, see [Control Introduction PaperDoll](30-UI Description Document.html#paperdoll) 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The control path starting from the main node | 
| entityIdentifier | str | The identifier set in the biological definition (squid, horse, donkey, mule, zombie_horse, skeleton_horse, drowned, elder_guardian, ender_dragon are not supported yet, and will be supported in subsequent versions) | 

- Return value 

None 

- Example 

```python 
# we want to show an entity model 
imagePath = "/paper_doll0" 
uiNode.SetUiEntity(imagePath, 'minecraft:cat') # According to the parameter description, if 'minecraft:squid' is passed in, no model will be displayed 
``` 

<span id="SetUiItem"></span> 
### SetUiItem 

- Description 

Set the item displayed by the ItemRenderer control. For details on how to configure the ItemRenderer control, see [Control Introduction ItemRenderer](30-UI Description Document.html#itemrenderer) 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The path of the control that needs to be modified starting from the main node | 
| itemName | str | Item identifier | 
| auxValue | int | Item additional value | 
| isEnchanted | bool | Optional parameter, whether to display the enchantment effect, the default is False and not displayed | 
| userData | dict | Optional parameter. If it is a disaster banner or firework star with userData, this parameter needs to be passed in to display correctly. Currently, only disaster banners and firework stars need to be passed. | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether to set the result, True means success | 

- Example 

```python 
#Set the display to wooden board block

itemRenderPath = "/panel/item_renderer" 
itemName = "minecraft:wool" 
auxValue = 0 
uiNode.SetUiItem(itemRenderPath, itemName, auxValue) 
``` 

<span id="SetUiModel"></span> 
### SetUiModel 

- Description 

Set the model that the PaperDoll control needs to display. For details on how to configure the PaperDoll control, see [Control Introduction PaperDoll](30-UI Description Document.html#paperdoll) 

- Parameters 

| Parameter Name | Data Type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Control path starting from the main node | 
| modelName | str | Name of the skeleton model | 
| animateName | str | Animation name, default is 'idle' | 
| looped | bool | Whether to loop the animation, the default is True | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to change model 
imagePath = "/paper_doll0" 
uiNode.SetUiModel(imagePath, 'saber', 'idle', True) 
``` 

<span id="SetUiModelScale"></span> 
### SetUiModelScale 

- Description 

Set the scale of the PaperDoll control model 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Starting from the main node, the control path to be deleted | 
| scale | float | PaperDoll's zoom ratio, default is 1.0 | 


- Return value 

None 

- Notes 
- When set to the original creature model, it will cause offset. It is recommended that developers adjust the position by themselves 

- Example 

```python 
imagePath = "/paper_doll0" 
uiNode.SetUiModelScale(imagePath, 1.2) 
``` 

<span id="MiniMapBaseScreen"></span> 
## MiniMapBaseScreen 

MiniMapBaseScreen inherits from ScreenNode, implements the basic functions of the minimap, and encapsulates some interfaces for operating the minimap. 
Note: This function belongs to [experimental function] (../20-Gameplay Development/13-Module SDK Programming/10-Experimental Function.md). Currently, there may be performance issues on low-end machines. It is recommended that developers use this function reasonably. 
Notes: 
1) It is not recommended to open the minimap in flight mode or running mode; 
2) If the Create interface is overridden, please call super(MiniMapBaseScreen, self).Create() first; 
3) If the Destroy interface is overridden, please call super(MiniMapBaseScreen, self).Destroy() first; 

<span id="AddEntityMarker"></span> 
### AddEntityMarker 

- Description 

Add entity position marker 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity Id | 
| texturePath | str | Overhead ICON texture, such as textures/blocks/border | 
| size | tuple(float,float) | Texture size, default is (4,4) | 
| enableRotation | bool | Whether to enable entity orientation, the default is False | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.AddEntityMarker(entityId, "textures/ui/custom_head") 
``` 

<span id="AddStaticMarker"></span> 
### AddStaticMarker 

- Description 

Add a marker for a static location on the map 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | str | Marker ID | 
| vec2 | tuple(float,float) | Map location 2D coordinates (x,z) | 
| texturePath | str | Texture path | 
| size | tuple(float,float) | Texture size, default is (4,4) | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.AddStaticMarker("this_is_marker_key", (10,2), "textures/blocks/border", (3,3)) 
``` 

<span id="RemoveEntityMarker"></span> 
### RemoveEntityMarker 

- Description 

Delete entity position marker 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| entityId | str | entityId | 

- Return value 

| data type | description |

| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.RemoveEntityMarker(entityId) 
``` 

<span id="RemoveStaticMarker"></span> 
### RemoveStaticMarker 

- Description 

Delete static location marker 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | str | Marker ID | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.RemoveStaticMarker(entityId) 
``` 

<span id="ZoomIn"></span> 
### ZoomIn 

- Description 

Zoom in the map (up to double the zoom) 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| value | float | The incremental value based on the original value can control the zoom speed. The default value is 0.1 |


- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.ZoomIn(0.2) 
``` 

<span id="ZoomOut"></span> 
### ZoomOut 

- Description 

Zoom out the map (up to double the size) 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| value | float | The reduction value on the original basis can control the zoom speed. The default value is 0.1 | 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.ZoomOut(0.2) 
``` 

