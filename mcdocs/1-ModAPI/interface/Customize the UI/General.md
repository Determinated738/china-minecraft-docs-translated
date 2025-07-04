--- 
sidebarDepth: 1 
--- 
# General 

## CheckCanBindUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Check whether the entity can bind the overhead UI. For details on how to bind the UI to the entity, see the [CreateUI](#CreateUI) interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the overhead UI can be bound True: Can be bound False: Cannot be bound | 

- Notes 
- Failure to bind the overhead UI usually means that the entity has died or has just been created. If the newly created entity cannot bind the overhead UI, wait for 1-3 frames and try to bind again. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
canBind = clientApi.CheckCanBindUI(entityId) 
``` 

## CreateUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Create UI, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#界面创建流程及人生系統">界面创建过程及人生系統</a> 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name is recommended | 
| uiKey | str | UI unique identifier | 
| createParams | dict | Parameters for creating UI, which will be passed to the _init_ function of the UI class | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScreenNode | UI node | 

- Notes 
- The createParams parameter is explained as follows: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| isHud | int | The value is (0 / 1), which means whether it is a HUD UI. In general, the shooting button does not block the game, and the native operation interface should have isHud of 1; the isHud of the interface that is not operated in the game, such as the mall interface, should be 0, and the default value is 0. When isHud is 0, the created UI will be generated from a level 1000 higher than the current UI by default, which may cause the control to be blocked; when isHud is 1, the created UI will be generated from a level 0. | 
| inputMode | int | The value is (0 / 1), which belongs to the old version writing method. It has the same meaning as isHud but the value is opposite, that is, isHud is 0 is equal to inputMode is 1, and if both exist at the same time, isHud is judged first. | 
| bindEntityId | str | means the id of the bound entity. If this key-value pair is not passed in or the value is None, the UI interface will be processed with isHud = 0. | 
| bindOffset | tuple | means the offset between the UI and the bound entity, and the default value is (0, 1, 0). | 
| autoScale | int | The value is (0 / 1), which means whether the bound entity UI will automatically scale dynamically according to the distance between the entity and the local player. The default value is 1, which means that the size of the overhead UI will be dynamically scaled. | 
| mini_map_root_path | str | Minimap control root path | 
- Note: 
The scaling of the bound entity UI only applies to the child nodes under the root node (such as the "main" node). 

It is recommended to mount a panel type node under the root node, and then set all UI nodes that need to be scaled to percentage attributes and mount them under this panel node. 
- Note: 
If there are too many bound entity UIs on the same screen or a large number of bound entity UIs are created or deleted at one time, it may cause performance problems such as lag. 

It is recommended to use a resource pool to manage the bound entity UI. When the distance between the entity and the local player exceeds a certain range, hide/remove its bound UI, or change its bound UI to bind other entities in need. 

When you need to create bound entity UIs in large batches, it is recommended to divide the task of creating UIs into small batches and execute them multiple times, with at least one frame between each batch. For example, if you need to create 100 bound entity UIs, spread the task across 5 frames, creating 20 bound entity UIs per frame. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
from mod_log import logger as logger 
# Listen for the engine initialization completion event and create our battle UI after this event 
def OnUIInitFinished(self, args): 
logger.info("OnUIInitFinished : %s" % args) 
# Register UI For detailed explanation, refer to "UI API" 
clientApi.RegisterUI(modConfig.ModName, modConfig.FpsBattleUIName, modConfig.FpsBattleUIPyClsPath, modConfig.FpsBattleUIScreenDef) 
# Create a normal UI interface 
clientApi.CreateUI(modConfig.ModName, modConfig.FpsBattleUIName, {"isHud" : 1}) 
# Get the created UI interface 
self.mFpsBattleUINode = clientApi.GetUI(modConfig.ModName, modConfig.FpsBattleUIName)
    if self.mFpsBattleUINode:
        self.mFpsBattleUINode.Init()


# Different from the above example, here is how to create a UI interface for binding entities 
def OnUIInitFinished(self, args): 
logger.info("OnUIInitFinished : %s" % args) 
# Also register the UI first 
clientApi.RegisterUI(modConfig.ModName, modConfig.FpsBattleUIName, modConfig.FpsBattleUIPyClsPath, modConfig.FpsBattleUIScreenDef) 
# Create a UI for the entity with binding id entityId 
clientApi.CreateUI( 
modConfig.ModName, 
modConfig.FpsBattleUIName, 
{ 
"bindEntityId": entityId, 
"bindOffset": (0, 2, 0), 
"autoScale": 1 
} 
) 
self.mFpsBattleUINode = clientApi.GetUI(modConfig.ModName, modConfig.FpsBattleUIName) 
if self.mFpsBattleUINode: 
self.mFpsBattleUINode.Init() 
``` 

## GetCustomUIControlProxyCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the native interface custom UI proxy base class 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(CustomUIControlProxy) | Native interface custom UI proxy base class | 

- Example 

```python 
import client.extraClientApi as clientApi 
CustomUIControlProxy = clientApi.GetCustomUIControlProxyCls()
```



## GetMiniMapScreenNodeCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the base class of the minimap ScreenNode 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(MiniMapBaseScreen) | Base class of the minimap ScreenNode | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
MiniMapBaseScreen = clientApi.GetMiniMapScreenNodeCls() 
``` 

## GetNativeScreenManagerCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the NativeScreenManager class 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(NativeScreenManager) | NativeScreenManager class |


- Example 

```python 
import client.extraClientApi as clientApi 
NativeScreenManager = clientApi.GetNativeScreenManagerCls() 
``` 

## GetScreenNodeCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the ScreenNode class 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(ScreenNode) | ScreenNode class | 

- Example 

```python 
import client.extraClientApi as clientApi 
ScreenNode = clientApi.GetScreenNodeCls() 
``` 

## GetTopScreen 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the UI node at the top of the UI stack 

- Parameters


    None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScreenNode | UI node, returns None when the stack is empty | 

- Notes 
- This interface gets the interface created by the last PushScreen. Different from the GetTopUI interface, GetTopScreen can only get the UI created by PushScreen, while GetTopUI can get the native UI or the UI created by PushScreen 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
node = clientApi.GetTopScreen() 
``` 

## GetTopUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the UI name at the top of the UI stack 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The top-level UI name. If the pop-up is a native UI, the name is ([Native UI Enumeration](../../Enumeration Value/UICategory.md)) | 

- Notes 
- Get the UI name at the top of the UI stack. Different from the GetTopScreen interface, GetTopUI can get native UI and UI generated by PushScreen, while GetTopScreen can only get UI created by PushScreen. 
- Get the UI generated by PushScreen and return it as main. If the main name is modified in the json file of the UI, the return value obtained here will also correspond to it. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
TopUIName = clientApi.GetTopUI()

``` 

## GetUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get UI node, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#界面创建流程及人生系統">界面创建流程及人生系統</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name recommended | 
| uiKey | str | UI unique identifier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScreenNode | UI Node | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
uiNode = clientApi.GetUI(modConfig.ModName, modConfig.FpsBattleUIName) 
``` 

## GetViewBinderCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the ViewBinder class 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(ViewBinder) | ViewBinder class | 

- Example 

```python 
import client.extraClientApi as clientApi 
ViewBinder = clientApi.GetViewBinderCls() 
``` 

## GetViewViewRequestCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the ViewRequest class 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(ViewRequest) | ViewRequest class |

- Example

```python
import client.extraClientApi as clientApi
ViewRequest = clientApi.GetViewViewRequestCls()
```



## PopScreen

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.extraClientApi

- Description 

Close the UI using stack management 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the closure is successful | 

- Notes 
- This interface closes the interface created by PushScreen. Different from the PopTopUI interface, PopScreen can only pop up the UI created by PushScreen, while PopTopUI can pop up the game's native UI and the UI created by PushScreen 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.PopScreen() 
``` 

## PopTopUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Pop up the UI at the top of the UI stack 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- Pop up the UI at the top of the UI stack. Different from the PopScreen interface, PopTopUI can pop up native UI and UI generated by PushScreen, while PopScreen can only pop up UI created by PushScreen. 
- Multiple operations are not allowed in the same frame. Only one UI is allowed to pop up in one frame 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
MyBool = clientApi.PopTopUI() 
``` 

## PushScreen 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Create UI using stack management 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| namespace | str | Namespace, mod name recommended | 
| uiname | str | UI unique identifier | 
| createParams | dict | Custom parameters for creating UI, which will be passed to the _init_ function of the UI class, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScreenNode | UI node, returns None when creation fails | 

- Notes 
- Use PopScreen to close the interface created by this interface 
- createParams is a custom parameter, which is different from createParams in the CreateUI method and does not support all the parameters listed in CreateUI. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Listen for the engine initialization completion event and create our battle UI after this event 
# Since the UI will not be created immediately after PushScreen is called, please do not operate the controls in the Init function. After the creation is completed, the Create function of screenNode will be called 
def OnUIInitFinished(self, args): 
clientApi.RegisterUI(modConfig.ModName, modConfig.FpsBattleUIName, modConfig.FpsBattleUIPyClsPath, modConfig.FpsBattleUIScreenDef) 
self.mFpsBattleUINode = clientApi.PushScreen(modConfig.ModName, modConfig.FpsBattleUIName) 
if self.mFpsBattleUINode: 
self.mFpsBattleUINode.Init() 
``` 




## RegisterUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Register UI. Before creating UI, you need to register UI first. The same UI only needs to be registered once. For details, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#界面创建流程与人生系統">界面创建流程与人生系統</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name is recommended | 
| uiKey | str | UI unique identifier | 
| clsPath | str | UI class path | 
| uiScreenDef | str | UI canvas path, in the format of "namespace.screenName". namespace corresponds to the value corresponding to "namespace" in the uiJson file. The value of the uiJson file generated by the UI editor is equal to the file name. screenName corresponds to the name of the canvas you want to open. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
from mod_log import logger as logger 
# Listen for engine initialization completion events, and create our battle UI after this event 
def OnUIInitFinished(self, args): 
logger.info("OnUIInitFinished : %s" % args) 
# Register UI For detailed explanation, refer to "UI API" 
clientApi.RegisterUI(modConfig.ModName, modConfig.FpsBattleUIName, modConfig.FpsBattleUIPyClsPath, modConfig.FpsBattleUIScreenDef) 
# Create UI For detailed explanation, refer to "UI API" 
    clientApi.CreateUI(modConfig.ModName, modConfig.FpsBattleUIName, {"isHud" : 1})
    self.mFpsBattleUINode = clientApi.GetUI(modConfig.ModName, modConfig.FpsBattleUIName)
    if self.mFpsBattleUINode:
        self.mFpsBattleUINode.Init()
```