--- 
sidebarDepth: 1 
--- 
# UI interface 

### ScreenNode 

| Function | Description | 
| --- | --- | 
| [Update](UI interface.md#update) | Called by the client every frame, 1 second has 30 frames | 
| [Destroy](UI interface.md#destroy) | UI life cycle function, called when the UI is destroyed. | 
| [Create](UI interface.md#create) | UI life cycle function, called when the UI is created successfully. | 
| [OnDeactive](UI interface.md#ondeactive) | UI life cycle function, called when the top UI of the stack has other UIs pushed into the stack. | 
| [OnActive](UI interface.md#onactive) | UI life cycle function, called when the UI returns to the top of the stack. | 
| [SetScreenVisible](UI界面.md#setscreenvisible) | Set whether to display this interface | 
| [ChangeBindEntityId](UI界面.md#changebindentityid) | Modify the bound entity id, **only effective for the UI interface of the bound entity, how to bind the UI to the entity, see [CreateUI](General.md#CreateUI) interface** | 
| [BindVirtualWorldModel](UI界面.md#bindvirtualworldmodel) | Bind the model in the virtual world | 
| [ChangeBindOffset](UI界面.md#changebindoffset) | Modify the offset between the bound entity and the bound entity, **only effective for the UI interface of the bound entity, how to bind the UI to the entity, see [CreateUI](General.md#CreateUI) interface** | 
| [ChangeBindAutoScale](UI界面.md#changebindautoscale) | Set whether the bound entity's UI is dynamically scaled according to the distance between the bound entity and the local player. **Only effective for the bound entity's UI interface. For details on how to bind the UI to the entity, see the [CreateUI](General.md#CreateUI) interface** | 
| [GetBindEntityId](UI interface.md#getbindentityid) | Get the entity id bound to the UI. The unbound UI will return the default value None | 
| [GetBindOffset](UI interface.md#getbindoffset) | Get the offset of the bound entity of the UI. The unbound UI will return the default value (0, 0, 0) | 
| [GetBindAutoScale](UI interface.md#getbindautoscale) | Get whether the bound entity's UI is dynamically scaled. The unbound UI will return the default value 1 | 
| [Clone](UI interface.md#clone) | Clone an existing control, modify its name, and attach it to the specified parent node. Currently, the cloned controls of text, image, and button controls perform normally, but cloned controls of other complex controls may have operation problems. It is recommended to manually copy a corresponding control for use during the JSON writing process. | 
| [GetChildrenName](UI界面.md#getchildrenname) | Get the name list of child nodes | 
| [GetAllChildrenPath](UI界面.md#getallchildrenpath) | Get the path list of all child nodes | 
| [RemoveComponent](UI界面.md#removecomponent) | Dynamically delete a control | 
| [SetRemove](UI界面.md#setremove) | Delete this interface node | 
| [SetUiModel](UI界面.md#setuimodel) | Set the model that the PaperDoll control needs to display. For details on how to configure the PaperDoll control, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#paperdoll">Control Introduction PaperDoll</a> | 
| [SetUiEntity](UI界面.md#setuientity) | Set the biological model that the PaperDoll control needs to display. For details on how to configure the PaperDoll control, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#paperdoll">Control Introduction PaperDoll</a> | 
| [SetUiModelScale](UI界面.md#setuimodelscale) | Set the scale of the PaperDoll control model | 
| [UpdateScreen](UI界面.md#updatescreen) | Refresh the interface and recalculate the relevant data of each control | 
| [SetStackGridCount](UI界面.md#setstackgridcount) | Set the size of the StackGrid control | 
| [SetSelectControl](UI界面.md#setselectcontrol) | Set the control where the current focus is. When the control is set to a text input box, the system keypad will pop up | 
| [GetRichTextItem](UI界面.md#getrichtextitem) | Return a rich text control instance | 
| [SetIsHud](UI界面.md#setishud) | Set the input mode of this interface | 
| [GetIsHud](UI界面.md#getishud) | Get the input mode of this interface | 
| [GetScreenName](UI界面.md#getscreenname) | Get the name of this interface | 
| [GetSelf](UI界面.md#getself) | Get the part interface itself | 
| [GetBaseUIControl](UI界面.md#getbaseuicontrol) | Get the BaseUIControl instance according to the path | 

### MiniMapBaseScreen 

| Function | Description | 
| --- | --- | 
| [AddEntityMarker](UI界面.md#addentitymarker) | Add entity position marker | 
| [RemoveEntityMarker](UI界面.md#removeentitymarker) | Delete entity position marker | 
| [AddStaticMarker](UI interface.md#addstaticmarker) | Add a marker for a static location on the map | 
| [RemoveStaticMarker](UI interface.md#removestaticmarker) | Delete a static location marker | 
| [ZoomIn](UI interface.md#zoomin) | Zoom in the map | 
| [ZoomOut](UI interface.md#zoomout) | Zoom out the map |

| [ZoomReset](UI界面.md#zoomreset) | Restore the map zoom size to the default value | 
| [SetHighestY](UI界面.md#sethighesty) | Set the maximum height of the map | 

# ScreenNode 

class in mod.client.ui.screenNode 

Some useful functions of ScreenNode and how to obtain the interface Node node are described in detail in <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html">UI用文档</a>. 

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

<span id="Update"></span> 
## Update 

- Description 

The client calls every frame, and there are 30 frames in 1 second 

- Parameters 

None 

- Return value 

None 

<span id="Destroy"></span> 
## Destroy 

- Description 


UI lifecycle function, called when the UI is destroyed. 

- Parameters 

None 

- Return value 

None 

<span id="Create"></span> 
## Create 

- Description 

UI lifecycle function, called when the UI is successfully created. 

- Parameters 

None 

- Return value 

None 

<span id="OnDeactive"></span> 
## OnDeactive 

- Description 

UI lifecycle function, called when the top UI on the stack has other UIs pushed into the stack. 

- Parameters 

None 

- Return value 

None 

- Remarks 
- It is not recommended to call SetScreenVisible(False) in the OnDeactive function and SetScreenVisible(True) in the OnActive function to hide the original interface when opening a new interface and automatically display the original interface when closing the new interface. Since hiding the interface will not change the UI stack, multiple Mods are prone to conflicts. It is recommended to use the PushScreen and PopScreen interfaces. 

<span id="OnActive"></span>

## OnActive 

- Description 

UI lifecycle function, called when the UI returns to the top of the stack. 

- Parameters 

None 

- Return value 

None 

- Remarks 
- It is not recommended to use the method of calling SetScreenVisible(False) in the OnDeactive function and calling SetScreenVisible(True) in the OnActive function to hide the original interface when opening a new interface and automatically display the original interface when the new interface is closed. Since hiding the interface will not change the UI stack, multiple mods are prone to conflicts. It is recommended to use the PushScreen and PopScreen interfaces. 

<span id="SetScreenVisible"></span> 
## SetScreenVisible 

- Description 

Set whether to display this interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| visible | bool | False means hiding the interface, True means showing the interface | 

- Return value 

None 

- Example 

```python 
# We hide the interface of the current UI 
uiNode.SetScreenVisible(False) 
``` 

<span id="ChangeBindEntityId"></span> 
## ChangeBindEntityId 

- Description 


Modify the bound entity id. **Only effective for the UI interface of the bound entity. For details on how to bind the UI to the entity, please refer to the [CreateUI](General.md#CreateUI) interface** 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Bound entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful True: Success False: Failure | 

- Example 

```python 
succ = uiNode.ChangeBindEntityId(entityId) 
``` 

<span id="BindVirtualWorldModel"></span> 
## BindVirtualWorldModel 

- Description 

Binds the model in the virtual world 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bindToObjId | int | The id of the bound model object | 
| offset | tuple(float,float,float) | The offset between the UI and the bound entity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful True: Success False: Failure | 

- Notes 
- When the bound object is destroyed, the UI will not be destroyed, but will be hidden. It is recommended to reuse or destroy it 

- Example 

```python 
# If the bound UI needs to create multiple copies, you need to use this method to create it: 
uiNode=clientApi.CreateUI("modNamespace","testUI", {

"bindEntityId": clientApi.GetLocalPlayerId() 
}) 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.VirtualWorldCreate() 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
succ = uiNode.BindVirtualWorldModel(objId, (0.0, 0.0, 0.0)) 
``` 

<span id="ChangeBindOffset"></span> 
## ChangeBindOffset 

- Description 

Modify the offset between the bound entity, **only effective for the UI interface of the bound entity, how to bind the UI to the entity, see [CreateUI](General.md#CreateUI) interface** 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | offset | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful True: Success False: Failure | 

- Notes 
- It is not recommended to set the offset of the local player binding UI to (0, 0, 0) in the first-person perspective 

- Example 

```python 
succ = uiNode.ChangeBindOffset((0, 3, 0)) 
``` 

<span id="ChangeBindAutoScale"></span> 
## ChangeBindAutoScale 

- Description 

Set whether the bound entity's UI is dynamically scaled based on the distance between the bound entity and the local player. **Only effective for the bound entity's UI interface. For details on how to bind the UI to the entity, see the [CreateUI](General.md#CreateUI) interface** 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| autoScale | int | 1: Dynamic scaling 0: No dynamic scaling | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful True: Success False: Failure | 

- Notes 
- Note: 
The UI scaling of the bound entity only works on the child nodes under the root node (such as the "main" node). 

It is recommended to mount a panel type node under the root node, and then set all UI nodes that need to be scaled to percentage attributes and mount them under this panel node. 

- Example 

```python 
succ = uiNode.ChangeBindAutoScale(1) 
``` 

<span id="GetBindEntityId"></span> 
## GetBindEntityId 

- Description 

Get the entity id bound to the UI. The default value None will be returned for unbound UI 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Bound entity id | 

- Example 

```python 
entityId = uiNode.GetBindEntityId() 
``` 

<span id="GetBindOffset"></span> 
## GetBindOffset


- Description 

Get the offset of the UI bound to the entity. If the UI is not bound, the default value (0, 0, 0) will be returned. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Offset | 

- Example 

```python 
offset = uiNode.GetBindOffset() 
``` 

<span id="GetBindAutoScale"></span> 
## GetBindAutoScale 

- Description 

Get whether the UI of the bound entity is dynamically scaled. If the UI is not bound, the default value 1 will be returned. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 1: dynamic scaling 0: no dynamic scaling | 

- Example 

```python 
autoScale = uiNode.GetBindAutoScale() 
``` 

<span id="Clone"></span> 
## Clone


- Description 

Clone an existing control, modify its name, and attach it to the specified parent node. Currently, the cloned controls of text, image, and button controls perform normally. The cloned controls of other complex controls may have operation problems. It is recommended to manually copy a copy of the corresponding control for use during the json writing process. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The control path starting from the main node | 
| parentPath | str | The control path of the parent node starting from the main node | 
| newName | str | The name of the new control created after successful cloning. The path of the new control is parentPath/newName | 
| syncRefresh | bool | Whether to need synchronous refresh. The default value is True. Set True to calculate the size and other related data of the control in the same frame. Set False to calculate in the next frame. **If there are a lot of clone operations in the same frame, it is recommended to set it to False. After the operation is completed, call the UpdateScreen interface once to refresh the interface and related control data** | 
| forceUpdtae | bool | Whether to force refresh. The default value is True. If set to True, the same frame or the next frame will be refreshed according to the syncRefresh logic. If set to False, neither the current frame nor the next frame will be refreshed. You need to manually call UpdateScreen to refresh. If there are a large number of Clone operations and they are not executed in the same frame, it is recommended to set it to False. When an update is needed, call the UpdateScreen interface to refresh the interface and related control data. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the cloning is successful | 

- Example 

```python 
# Clone the text2 control, rename it to text3 and use panel as the parent control 
parentPath = "/panel" 
text2Path = "/panel/text2" 
text3Name = "text3" 
uiNode.Clone(text2Path, parentPath, text3Name) 
# Clone several controls with panel as the parent control and text_prefab as the template 
parentPath = "/panel" 
textPrefabPath = "/panel/text_prefab" 
for i in range(0, 10): 
uiNode.Clone(textPrefabPath, parentPath, "text" + str(i), False) 
uiNode.UpdateScreen(True) 
# In different frames, use panel as parent control and text_prefab as template to clone several controls 
parentPath = "/panel" 
textPrefabPath = "/panel/text_prefab" 
def _tickClone(newName): 
uiNode.Clone(textPrefabPath, parentPath, newName , False, False) 
def _tickUpdateScreen(): 
uiNode.UpdateScreen(True) 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddTimer(100, _tickClone, "text1") 
comp.AddTimer(200, _tickClone, "text2") 
comp.AddTimer(300, _tickUpdateScreen)
```

<span id="GetChildrenName"></span> 
## GetChildrenName 

- Description 

Get the name list of child nodes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| parentPath | str | The control path of the parent node starting from the main node | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns the name of the child node under the parent node. It will not recursively return all child nodes. If the node has no child nodes, it returns an empty list | 

- Example 

```python 
# get panel's children name 
node.GetChildrenName("/panel") 
``` 

<span id="GetAllChildrenPath"></span> 
## GetAllChildrenPath 

- Description 

Get the path list of all child nodes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| parentPath | str | The control path of the parent node starting from the main node | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns the path of the child nodes under the parent node, and will recursively return all child nodes. If the node has no child nodes, an empty list is returned | 

- Example 

```python

# get panel's all children path 
node.GetAllChildrenPath("/panel") 
``` 

<span id="RemoveComponent"></span> 
## RemoveComponent 

- Description 

Dynamically remove a control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Path of the control to be deleted starting from the main node | 
| parentPath | str | Path of the control of the parent node starting from the main node | 

- Return value 

None 

- Example 

```python 
# we want to remove text2 
text2Path = "/panel/text2" 
parentPath = "/panel" 
uiNode.RemoveComponent(text2Path, parentPath) 
``` 

<span id="SetRemove"></span> 
## SetRemove 

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

<span id="SetUiModel"></span> 
## SetUiModel 

- Description 

Set the model that the PaperDoll control needs to display. For details on how to configure the PaperDoll control, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#paperdoll">Control Introduction PaperDoll</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Control path starting from the main node | 
| modelName | str | Name of the skeleton model | 
| animateName | str | Animation name, default is 'idle' | 
| looped | bool | Whether to loop the animation, default is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to change model 
imagePath = "/paper_doll0" 
uiNode.SetUiModel(imagePath, 'saber', 'idle', True) 
``` 

<span id="SetUiEntity"></span> 
## SetUiEntity 

- Description 

Set the biological model that the PaperDoll control needs to display. For details on how to configure the PaperDoll control, see <a href="../../../../mcguide/18-Interface and Interaction/30-UI Instructions.html#paperdoll">Control Introduction PaperDoll</a> 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The control path starting from the main node | 
| entityIdentifier | str | The identifier set in the biological definition | 

- Return value 

None 

- Notes 
- Microsoft original models not currently supported: horse, donkey, mule, skeleton_horse, zombie_horse, llama, tropicalfish, slime, magma_cube, ghast, shulker, ender_dragon, thrown_trident, ender_crystal, boat, tnt 

- Example 

```python 
# we want to show an entity model 
imagePath = "/paper_doll0" 
uiNode.SetUiEntity(imagePath, 'minecraft:cat') 
``` 

<span id="SetUiModelScale"></span> 
## SetUiModelScale 

- Description 

Set the scale of the PaperDoll control model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | PaperDoll control path starting from the main node | 
| scale | float | PaperDoll scale, default is 1.0 | 

- Return value 

None 

- Remarks 
- When set to the original creature model, it will cause offset, it is recommended that developers adjust the position by themselves 

- Example 

```python 
imagePath = "/paper_doll0" 
uiNode.SetUiModelScale(imagePath, 1.2) 
``` 




<span id="UpdateScreen"></span> 
## UpdateScreen 

- Description 

Refresh the interface and recalculate the relevant data of each control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| syncRefresh | bool | Whether to refresh synchronously, the default value is True. Set True for the game to calculate the relevant data of each control in the same frame, and set False to calculate in the next frame. If set to True, it is not recommended to call multiple times in the same frame | 

- Return value 

None 

- Example 

```python 
# Current frame refresh interface 
uiNode.UpdateScreen(True) 
# Next frame refresh interface 
uiNode.UpdateScreen(False) 
``` 

<span id="SetStackGridCount"></span> 
## SetStackGridCount 

- Description 

Set the size of the StackGrid control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The path of the Grid control starting from the main node | 
| count | int | Set the number of contents in the StackGrid | 

- Return value 

None 

- Example 


```python 
# we want change stackgrid count 
stackgridPath = "/stack_grid1" 
uiNode.SetStackGridCount(stackgridPath, 3) 
``` 

<span id="SetSelectControl"></span> 
## SetSelectControl 

- Description 

Set the control where the current focus is. When the control is set to a text input box, the system keypad will pop up 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The path of the control to be selected starting from the main node | 
| enable | bool | True selects the control represented by componentPath, False deselects | 

- Return value 

None 

- Example 

```python 
path = "/text_edit_box0" 
uiNode.SetSelectControl(path, True) 
``` 

<span id="GetRichTextItem"></span> 
## GetRichTextItem 

- Description 

Returns a rich text control instance 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | Starting from the main node, the path inherited from the rich_text.RichTextPanel control | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| RichTextItem | Returns a rich text control instance | 

- Example 

```python 
# we want get a rich-text-item 
richTextPath = "/RichTextPanel" 
richTextItem = uiNode.GetRichTextItem(richTextPath) 
``` 

<span id="SetIsHud"></span> 
## SetIsHud 

- Description 

Set the input mode of this interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHud | int | Setting 1 means that the interface does not block game operations, and setting 0 means blocking. | 

- Return value 

None 

- Example 

```python 
# We need to set this interface to HUD operation mode 
uiNode.SetIsHud(1) 
``` 

<span id="GetIsHud"></span> 
## GetIsHud 

- Description 

Get the input mode of this interface 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Return 1 means that the interface does not block game operations, and return 0 means it blocks. | 

- Example 

```python 
# We need to get the input mode of this interface 
isHud = uiNode.GetIsHud() 
``` 

<span id="GetScreenName"></span> 
## GetScreenName 

- Description 

Get the name of this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Return the name of this interface. The return value is only when the interface is generated by calling the PushScreen method. The return value is the parameter uiScreenDef used when registering the UI (calling RegisterUI), otherwise it is None | 

- Example 

```python 
# We need to get the name of this interface 
screenName = uiNode.GetScreenName() 
``` 

<span id="GetSelf"></span> 
## GetSelf 

- Description 

Get the part interface itself 

- Parameters


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScreenNode | Part interface itself | 

<span id="GetBaseUIControl"></span> 
## GetBaseUIControl 

- Description 

Get the BaseUIControl instance according to the path 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | Path of the current control | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseUIControl | BaseUIControl instance corresponding to the path control | 

- Example 

```python 
# Get the BaseUIControl instance according to the path 
text2Path = "/panel/text2" 
text2UIControl = uiNode.GetBaseUIControl(text2Path) 
``` 

# MiniMapBaseScreen 

class in mod.client.ui.miniMapBaseScreen 

MiniMapBaseScreen inherits from ScreenNode, implements the basic functions of the minimap, and encapsulates some interfaces for operating the minimap. 
Note: This function belongs to <a href="../../../../mcguide/20-Gameplay Development/13-Module SDK Programming/10-Experimental Functions.html">experimental functions</a>, and may have performance issues on low-end machines. It is recommended that developers use this function reasonably. 
Notes: 
1) It is not recommended to open the minimap in flight mode or running map mode; 
2) If the Create interface is overridden, please call super(MiniMapBaseScreen, self).Create() first; 
3) If the Destroy interface is overridden, please call super(MiniMapBaseScreen, self).Destroy() first;


<span id="AddEntityMarker"></span> 
## AddEntityMarker 

- Description 

Add entity position marker 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity ID | 
| texturePath | str | Top ICON texture, such as textures/blocks/border | 
| size | tuple(float,float) | Texture size, default is (4,4) | 
| enableRotation | bool | Whether to enable entity orientation, default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to add successfully | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.AddEntityMarker(entityId, "textures/ui/custom_head") 
``` 

<span id="RemoveEntityMarker"></span> 
## RemoveEntityMarker 

- Description 

Remove entity position marker 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity Id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the deletion is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.RemoveEntityMarker(entityId) 
``` 

<span id="AddStaticMarker"></span> 
## AddStaticMarker 

- Description 

Add a marker for a static location on the map 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Marker ID | 
| vec2 | tuple(float,float) | Map location 2D coordinates (x,z) | 
| texturePath | str | Texture path | 
| size | tuple(float,float) | Texture size, default is (4,4) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the increase was successful | 

- Notes 
- If you use this interface, please do not set the map zoom factor too large (it is recommended that the map zoom factor after ZoomOut is set to no less than 0.5 times the original map size) to avoid problems such as invalid static marker position after the map is zoomed out. 

- Example

```python
import mod.client.extraClientApi as clientApi
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"})
node.AddStaticMarker("this_is_marker_key", (10,2), "textures/blocks/border", (3,3))
```



<span id="RemoveStaticMarker"></span>
## RemoveStaticMarker

- Description 

Delete static position marker 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Marker ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.RemoveStaticMarker(entityId) 
``` 

<span id="ZoomIn"></span> 
## ZoomIn 

- Description 

Zoom in the map 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Incremental value based on the original value, which can control the zoom speed. The default value is 0.05 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"})

node.ZoomIn(0.2) 
``` 

<span id="ZoomOut"></span> 
## ZoomOut 

- Description 

Zoom out 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | The reduction value based on the original basis can control the zoom speed. The default is 0.05 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- The client has limited map block loading. If the map UI interface is too large or the map zoom factor is too large, the small map will not be able to display the unloaded blocks. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.ZoomOut(0.2) 
``` 

<span id="ZoomReset"></span> 
## ZoomReset 

- Description 

Restore the map zoom size to the default value 

- Parameters 

None 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.ZoomReset() 
``` 

<span id="SetHighestY"></span> 
## SetHighestY 

- Description 

Set the maximum height of the map 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| highestY | int | Drawing height value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- After dynamically adjusting the height value, the blocks that have been drawn will not be refreshed to the new height value. Only the blocks that have not been drawn will be drawn with the new height value. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.CreateUI(modConfig.ModName, modConfig.UIName, {"mini_map_root_path": "/mainPanel"}) 
node.SetHighestY(250) 
``` 

