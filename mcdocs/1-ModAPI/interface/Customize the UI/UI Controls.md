--- 
sidebarDepth: 1 
--- 
# UI Controls 

### BaseUIControl 

| Function | Description | 
| --- | --- | 
| [SetPosition](UI Control.md#setposition) | Set the coordinates of the control relative to the parent node | 
| [SetFullSize](UI Control.md#setfullsize) | Set the size of the control, supporting proportional form and absolute value | 
| [GetFullSize](UI Control.md#getfullsize) | Get the size of the control, supporting percentage and absolute value | 
| [SetFullPosition](UI Control.md#setfullposition) | Set the anchor point coordinates (global coordinates) of the control, supporting proportional value and absolute value | 
| [GetFullPosition](UI Control.md#getfullposition) | Get the anchor point coordinates of the control, supporting proportional value and absolute value | 
| [SetAnchorFrom](UI control.md#setanchorfrom) | Set the control's anchor point relative to the parent node | 
| [GetAnchorFrom](UI control.md#getanchorfrom) | Determine which anchor point of the control relative to the parent node to calculate the position and size | 
| [SetAnchorTo](UI control.md#setanchorto) | Set the control's own anchor point position | 
| [GetAnchorTo](UI control.md#getanchorto) | Get the control's own anchor point position information | 
| [SetClipOffset](UI control.md#setclipoffset) | Set the control's clipping offset information | 
| [GetClipOffset](UI control.md#getclipoffset) | Get the control's clipping offset information | 
| [SetClipsChildren](UI control.md#setclipschildren) | Set whether the control enables clipping content | 
| [GetClipsChildren](UI control.md#getclipschildren) | Returns whether a control enables clipping based on the control path | 
| [SetMaxSize](UI control.md#setmaxsize) | Sets the maximum size allowed by the control | 
| [GetMaxSize](UI control.md#getmaxsize) | Gets the maximum size allowed by the control | 
| [SetMinSize](UI control.md#setminsize) | Sets the minimum size allowed by the control | 
| [GetMinSize](UI control.md#getminsize) | Gets the minimum size allowed by the control | 
| [GetPosition](UI control.md#getposition) | Gets the coordinates of the control relative to the parent node | 
| [SetSize](UI control.md#setsize) | Sets the size of the control | 
| [GetSize](UI control.md#getsize) | Gets the size of the control | 
| [SetVisible](UI control.md#setvisible) | Choose whether to display a control based on the control path. You can adjust the display/hide of the entire JSON by passing in an empty string (""). | 
| [GetVisible](UI control.md#getvisible) | Return whether a control is displayed based on the control path | 
| [SetTouchEnable](UI control.md#settouchenable) | Set whether the control is clickable and interactive | 
| [SetAlpha](UI control.md#setalpha) | Set the transparency of the node, which is only effective for image and label controls | 
| [SetLayer](UI control.md#setlayer) | Set the level of the control node. You can adjust the base level of the entire JSON by passing in an empty string (""). | 
| [GetChildByName](UI control.md#getchildbyname) | Get the BaseUIControl instance based on the name of the child control | 
| [GetChildByPath](UI control.md#getchildbypath) | Get the BaseUIControl instance based on the relative path | 
| [resetAnimation](UI control.md#resetanimation) | Reset the animation of the control | 
| [asLabel](UI control.md#aslabel) | Convert the current BaseUIControl to a LabelUIControl instance. If the current control is not of the Label type, it returns None | 
| [asButton](UI control.md#asbutton) | Convert the current BaseUIControl to a ButtonUIControl instance. If the current control is not of the button type, it returns None | 
| [asImage](UI control.md#asimage) | Convert the current BaseUIControl to an ImageUIControl instance. If the current control is not of the image type, it returns None | 
| [asGrid](UI control.md#asgrid) | Convert the current BaseUIControl to a GridUIControl instance. If the current control is not of the grid type, it returns None | 
| [asScrollView](UI control.md#asscrollview) | Convert the current BaseUIControl to a ScrollViewUIControl instance. If the current control is not of the scrollview type, it returns None | 
| [asSwitchToggle](UI control.md#asswitchtoggle) | Convert the current BaseUIControl to a SwitchToggleUIControl instance. If the current control is not a panel type or not a toggle, it returns None. | 
| [asTextEditBox](UI control.md#astexteditbox) | Convert the current BaseUIControl to a TextEditBoxUIControl instance. If the current control is not an editbox type, it returns None. | 
| [asProgressBar](UI control.md#asprogressbar) | Convert the current BaseUIControl to a ProgressBarUIControl instance. If the current control is not a panel type, it returns None. | 
| [asNeteasePaperDoll](UI control.md#asneteasepaperdoll) | Convert the current BaseUIControl to a NeteasePaperDollUIControl instance. If the current control is not a custom type, it returns None. | 
| [asMiniMap](UI control.md#asminimap) | Convert the current BaseUIControl to a MiniMapUIControl instance. If the current control is not a minimap type, it returns None. | 
| [asSlider](UI control.md#asslider) | Convert the current BaseUIControl to a SliderUIControl instance. If the current control is not a slider type, it returns None. | 
| [asItemRenderer](UI control.md#asitemrenderer) | Convert the current BaseUIControl to an ItemRenderer instance. If the current control is not a custom type, it returns None. | 
| [asNeteaseComboBox](UI control.md#asneteasecombobox) | Convert the current BaseUIControl to a NeteaseComboBoxUIControl instance. If the current control is not a panel type, it returns None. |

| [asStackPanel](UI control.md#asstackpanel) | Convert the current BaseUIControl to a StackPanelUIControl instance. If the current control is not of the stackPanel type, it returns None | 
| [asInputPanel](UI control.md#asinputpanel) | Convert the current BaseUIControl to an InputPanelUIControl instance. If the current control is not of the inputPanel type, it returns None | 

### ButtonUIControl 

| Function | Description | 
| --- | --- | 
| [AddTouchEventParams](UI control.md#addtoucheventparams) | Enable the button callback function. If this function is not called, the button will have no callback | 
| [SetButtonTouchDownCallback](UI control.md#setbuttontouchdowncallback) | Set the callback function triggered when the button is pressed | 
| [SetButtonTouchUpCallback](UI control.md#setbuttontouchupcallback) | Set the callback function when the touch is released within the button range | 
| [SetButtonTouchCancelCallback](UI control.md#setbuttontouchcancelcallback) | Set the callback function triggered when the touch is released outside the button range | 
| [SetButtonTouchMoveCallback](UI control.md#setbuttontouchmovecallback) | Set the callback function triggered when the touch moves after pressing | 
| [SetButtonTouchMoveInCallback](UI control.md#setbuttontouchmoveincallback) | Set the callback function triggered when entering the control after pressing the button | 
| [SetButtonTouchMoveOutCallback](UI control.md#setbuttontouchmoveoutcallback) | Set the callback function triggered when exiting the control after pressing the button | 
| [SetButtonScreenExitCallback](UI control.md#setbuttonscreenexitcallback) | Set the callback function to be triggered when the mouse is not lifted when the canvas where the button is located is exited | 

### GridUIControl 

| Function | Description | 
| --- | --- | 
| [SetGridDimension](UI control.md#setgriddimension) | Set the size of the Grid control | 

### ImageUIControl 

| Function | Description | 
| --- | --- | 
| [SetSprite](UI control.md#setsprite) | Change the specified texture for the image control | 
| [SetSpriteColor](UI control.md#setspritecolor) | Set the image color | 
| [SetSpriteGray](UI control.md#setspritegray) | Graying the image control is more efficient than directly SetSprite a gray image | 
| [SetSpriteUV](UI control.md#setspriteuv) | Set the starting uv of the image, which is consistent with the "uv" attribute in json | 
| [SetSpriteUVSize](UI control.md#setspriteuvsize) | Set the image's uv size, which is the same as the "uv_size" property in json | 
| [SetSpriteClipRatio](UI control.md#setspriteclipratio) | Set the image's clipping area ratio (without changing the control size). You can use the image control's clip_ratio property to control the direction. | 
| [SetSpritePlatformHead](UI control.md#setspriteplatformhead) | Set the image to the avatar of the current account in the Minecraft mobile launcher | 
| [SetSpritePlatformFrame](UI control.md#setspriteplatformframe) | Set the image to the avatar frame of the current account in the Minecraft mobile launcher | 
| [SetClipDirection](UI control.md#setclipdirection) | Set the clipping direction of the image control | 
| [GetClipDirection](UI control.md#getclipdirection) | Get the clipping direction of the image control | 
| [SetImageAdaptionType](UI control.md#setimageadaptiontype) | Set the image adaptation method and information of the image control | 

### InputPanelUIControl 

| Function | Description | 
| --- | --- | 
| [SetIsModal](UI control.md#setismodal) | Set whether the current panel is a modal box | 
| [GetIsModal](UI control.md#getismodal) | Determine whether the current panel is a modal box | 
| [SetOffsetDelta](UI control.md#setoffsetdelta) | Set the drag offset of the clicked panel | 
| [GetOffsetDelta](UI control.md#getoffsetdelta) | Get the drag offset of the clicked panel | 

### ItemRendererUIControl 

| Function | Description |

| --- | --- | 
| [SetUiItem](UI control.md#setuiitem) | Set the item displayed by the ItemRenderer control. For details on how to configure the ItemRenderer control, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#itemrenderer">Control Introduction ItemRenderer</a> | 

### LabelUIControl 

| Function | Description | 
| --- | --- | 
| [SetText](UI control.md#settext) | Set the text information of the Label | 
| [GetText](UI control.md#gettext) | Get the text information of the Label. If the acquisition fails, None will be returned | 
| [SetTextColor](UI control.md#settextcolor) | Set the color of the Label text | 
| [GetTextColor](UI control.md#gettextcolor) | Get the color of the Label text | 
| [SetTextFontSize](UI control.md#settextfontsize) | Set the font size of the text in the Label | 
| [SetTextAlignment](UI control.md#settextalignment) | Set the text alignment of the text control | 
| [GetTextAlignment](UI control.md#gettextalignment) | Get the text alignment of the text control | 
| [SetTextLinePadding](UI control.md#settextlinepadding) | Set the line spacing of the text control | 
| [GetTextLinePadding](UI control.md#gettextlinepadding) | Get the line spacing of the text control | 
| [EnableTextShadow](UI control.md#enabletextshadow) | Enable the text control to display a shadow | 
| [DisableTextShadow](UI control.md#disabletextshadow) | Disable the text control from displaying a shadow | 
| [IsTextShadowEnabled](UI control.md#istextshadowenabled) | Determine whether the text control displays a shadow | 

### MiniMapUIControl 

| Function | Description | 
| --- | --- | 
| [ZoomIn](UI control.md#zoomin) | Zoom in the map | 
| [ZoomOut](UI control.md#zoomout) | Zoom out the map | 
| [ZoomReset](UI control.md#zoomreset) | Restore the map zoom size to the default value | 
| [SetHighestY](UI control.md#sethighesty) | Set the maximum height of the map | 

### NeteaseComboBoxUIControl 

| Function | Description | 
| --- | --- | 
| [AddOption](UI control.md#addoption) | Add a drop-down box item, return True if the addition is successful, otherwise return False | 
| [ClearOptions](UI control.md#clearoptions) | Clear the drop-down box | 
| [ClearSelection](UI control.md#clearselection) | Clear the current selection and restore the drop-down box to the unselected state | 
| [GetOptionIndexByShowName](UI control.md#getoptionindexbyshowname) | Find the index position of the corresponding drop-down box item according to the display text. If it is not found, return -1 | 
| [GetOptionShowNameByIndex](UI control.md#getoptionshownamebyindex) | Find the current stack text according to the index position. If it is not found, return None | 
| [GetOptionCount](UI control.md#getoptioncount) | Get the number of options | 
| [GetSelectOptionIndex](UI control.md#getselectoptionindex) | Get the index of the currently selected item. If there is no selected item, return -1 | 
| [GetSelectOptionShowName](UI control.md#getselectoptionshowname) | Get the display text of the currently selected item. If there is no selected item, return None | 
| [RemoveOptionByShowName](UI control.md#removeoptionbyshowname) | Remove the corresponding drop-down box item according to the provided display text. Return True if the removal is successful, otherwise return False | 
| [RemoveOptionByIndex](UI control.md#removeoptionbyindex) | Remove the corresponding drop-down box item according to the provided index. Return True if the removal is successful, otherwise return False | 
| [SetSelectOptionByIndex](UI control.md#setselectoptionbyindex) | Select the corresponding drop-down box item according to the provided index | 
| [SetSelectOptionByShowName](UI control.md#setselectoptionbyshowname) | Select the corresponding drop-down box item according to the provided display text | 
| [RegisterOpenComboBoxCallback](UI control.md#registeropencomboboxcallback) | Register the callback for the event of expanding the drop-down box | 
| [RegisterCloseComboBoxCallback](UI control.md#registerclosecomboboxcallback) | Register close drop-down box event callback | 
| [RegisterSelectItemCallback](UI control.md#registerselectitemcallback) | Register select drop-down box content event callback | 

### NeteasePaperDollUIControl


| Function | Description | 
| --- | --- | 
| [GetModelId](UI control.md#getmodelid) | Get the rendered skeleton model Id | 
| [RenderEntity](UI control.md#renderentity) | Render entity | 
| [RenderSkeletonModel](UI control.md#renderskeletonmodel) | Render skeleton model (not dependent on entity) | 
| [RenderBlockGeometryModel](UI control.md#renderblockgeometrymodel) | Render mesh model | 

### ProgressBarUIControl 

| Function | Description | 
| --- | --- | 
| [SetValue](UI control.md#setvalue) | Set the progress of the progress bar | 

### ScrollViewUIControl 

| Function | Description | 
| --- | --- | 
| [SetScrollViewPos](UI control.md#setscrollviewpos) | Set the position of the current scroll_view content | 
| [GetScrollViewPos](UI control.md#getscrollviewpos) | Get the position of the top content of the current scroll_view | 
| [SetScrollViewPercentValue](UI control.md#setscrollviewpercentvalue) | Set the percentage position of the current scroll_view content | 
| [GetScrollViewContentPath](UI control.md#getscrollviewcontentpath) | Return the path of the scroll_view content | 
| [GetScrollViewContentControl](UI control.md#getscrollviewcontentcontrol) | Return the BaseUIControl instance of the scroll_view content | 

### SliderUIControl 

| Function | Description | 
| --- | --- | 
| [GetSliderValue](UI control.md#getslidervalue) | Get the value of the slider, return 0 if failed | 
| [SetSliderValue](UI control.md#setslidervalue) | Set the value of the slider | 

### StackPanelUIControl 

| Function | Description | 
| --- | --- | 
| [SetOrientation](UI control.md#setorientation) | Set the arrangement direction of stackPanel | 
| [GetOrientation](UI control.md#getorientation) | Get the arrangement direction of stackPanel | 

### SwitchToggleUIControl 

| Function | Description | 
| --- | --- | 
| [SetToggleState](UI control.md#settogglestate) | Set the value of the Toggle switch control | 

### TextEditBoxUIControl 

| Function | Description | 
| --- | --- | 
| [GetEditText](UI control.md#getedittext) | Get the text information of the edit_box input box. If the acquisition fails, None will be returned | 
| [SetEditText](UI control.md#setedittext) | Set the text information of the edit_box input box |

| [SetEditTextMaxLength](UI control.md#setedittextmaxlength) | Set the maximum input length of the input box | 

# BaseUIControl 

class in mod.client.ui.controls.baseUIControl 

Base class of each control class, including the basic functional interface of the control 

<span id="SetPosition"></span> 
## SetPosition 

- Description 

Set the coordinates of the control relative to the parent node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float) | The coordinate information of the control relative to the parent node, the first item is the horizontal axis, the second item is the vertical axis | 

- Return value 

None 

- Example 

```python 
# we want to set text2 position 
text2Path = "/panel/text2" 
pos = (10, 10) 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
baseUIControl.SetPosition(pos) 
``` 

<span id="SetFullSize"></span> 
## SetFullSize 

- Description 

Set the size of the control, supporting proportional form and absolute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| axis | str | The axis to be set. The optional values are ["x","y"], "x" means setting the width of the control, and "y" means setting the height of the control | 
| paramDict | dict | The parameters to be set, see the notes for details |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Key value of paramDict 
| Parameter name | Parameter type | Explanation | 
| ----------------| --------------|---------------------------------------------- | 
| "fit"| bool | Whether to adapt to the parent control, the default value is False, you can not write this key value | 
| "followType"| str | Follow type, the default value is "none", you can not write this key value | 
| "relativeValue"| float | The proportional value relative to the follow control, the default value is 0, you can not write this key value | 
| "absoluteValue"| float | The absolute value of the setting, the default value is 0, you can not write this key value | 
- The size of the control supports complex calculations to achieve adaptive layout, in the form of "absoluteValue + relativeValue * follow value".
The follow value is determined by the control being followed and the currently set property. For example, if the width of the control is currently set, and the follow control is the parent control, the follow value is the width of the parent control. 
The control being followed is specific and has a certain relationship with the control itself, such as the parent control, child control, etc. of the control, which can be specified by setting the value of followType. 
- Optional values of followType 
| Value | Explanation | 
| ----------------| ------------------------------------------------------------ | 
| "none" | No follow, only absoluteValue is considered in actual calculation | 
| "parent" | The follow control is the parent control | 
| "maxChildren" | The follow control is the largest child control (the width is the maximum width when setting, and the height is the maximum height when setting), relativeValue is 1.0 no matter how it is set | 
| "maxSibling" | The follow control is the largest sibling control (the width is the maximum width when setting, and the height is the maximum height when setting), relativeValue is 1.0 no matter how it is set | 
| "children" | The follow value is equal to the sum of all child nodes | 
| "x" | The follow value is equal to the width of the control itself, which is only valid when axis == "y" | 
| "y" | The follow value is equal to the height of the control itself, which is only valid when axis == "x" | 
- The fit parameter is used to specify whether to adapt to the parent control. If it is an adaptive parent control, the absoluteValue, followType, and relativeValue parameters will be invalid, and the value of the control will be directly taken from the value of the parent control. 
- Be careful when setting the follow type, and do not cause a dependency cycle, such as the width of the parent control depends on the width of the child control, and the width of the child control depends on the parent control. In this way, even if the setting is successful, the result is unknown. 

- Example 

```python 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
# Set the width of image1 to half of the parent node, 
ret = baseUIControl.SetFullSize(axis="x", paramDict={"followType":"parent", "relativeValue":0.5}) 
# Set the height of image1 to twice the height of all child nodes and 20 pixels more 
ret = baseUIControl.SetFullSize(axis="y", paramDict={"absoluteValue":20, "followType":"children", "relativeValue":2}) 
# Set the width and height of image1 to the width and height of the parent node 
ret = baseUIControl.SetFullSize(axis="x", {"fit":True}) 
ret = baseUIControl.SetFullSize(axis="y", {"fit":True}) 
``` 

<span id="GetFullSize"></span> 
## GetFullSize 


- Description 

Get the size of the control, support percentage and absolute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| axis | str | The axis to be obtained, the optional values are ["x","y"], "x" means to get the width of the control, "y" means to get the height of the control | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | The size information of the control, see the notes for details | 

- Notes 
- Refer to the SetFullSize interface, the size information of the control can be described by the four attributes absoluteValue, followType, relativeValue, fit 
Therefore, the structure of the return value is as follows: 
| Key value | Type | 
| ----------------| -------------| 
| "absoluteValue" | float | 
| "followType" | str | 
| "relativeValue" | float | 
| "fit" | bool | 

- Example 

```python 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
# Get the width information of image1 
ret = baseUIControl.GetFullSize(axis="x") 
``` 

<span id="SetFullPosition"></span> 
## SetFullPosition 

- Description 

Set the control's anchor coordinates (global coordinates), supporting proportional and absolute values 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| axis | str | The set axis, the optional values are ["x", "y"], "x" means setting the x coordinate of the control anchor point, "y" means setting the y coordinate of the control anchor point | 
| paramDict | dict | Set parameters, see notes for details |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Key value of paramDict 
| Parameter name | Parameter type | Explanation | 
| ----------------| --------------|---------------------------------------------- | 
| "followType"| str | Follow type, the default value is "none", you can not write this key value | 
| "relativeValue"| float | The proportional value relative to the follow control, the default value is 0, you can not write this key value | 
| "absoluteValue"| float | The absolute value of the setting, the default value is 0, you can not write this key value | 
- The size of the control supports complex calculations to achieve adaptive layout, in the form of "absoluteValue + relativeValue * follow value". 
The follow value is determined by the follow control and the currently set properties. For example, the current setting is the x coordinate of the control, and the follow control is the parent control, and the follow value is the width of the parent control. 
The follow control is specific and has a certain relationship with the control itself, such as the parent control, child control, etc. of the control, which can be specified by setting the value of followType. 
- optional value of followType 
| Value | Explanation | 
| ----------------| ------------------------------------------------------------ | 
| "none" | No follow, only absoluteValue is considered in actual calculation | 
| "parent" | The follow control is the parent control | 
| "maxChildren" | The follow control is the largest child control (set x to the maximum width, set y to the maximum height), relativeValue is 1.0 no matter how it is set | 
| "maxSibling" | The follow control is the largest sibling control (set x to the maximum width, set y to the maximum height), relativeValue is 1.0 no matter how it is set | 
| "children" | The follow value is equal to the sum of all child nodes (if it is x, the sum of the widths of the child nodes is calculated, if it is y, the sum of the heights of the child nodes is calculated) | 
| "x" | The follow value is equal to the width of the control itself, this value is only valid when axis == "y" | 
| "y" | The follow value is equal to the height of the control itself, this value is only valid when axis == "x" will take effect | 
- Be careful when setting the follow type, do not cause a dependency cycle, such as the x coordinate of the parent control depends on the width of the child control, and the width of the child control depends on the parent control. In this way, even if the setting is successful, the result is unknown. 

- Example 

```python 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
# Set the position of image1 in the middle of the parent control 
ret = baseUIControl.SetFullPosition(axis="x", paramDict={"followType":"parent", "relativeValue":0.5}) 
ret = baseUIControl.SetFullPosition(axis="y", paramDict={"followType":"parent", "relativeValue":0.5}) 
``` 

<span id="GetFullPosition"></span> 
## GetFullPosition 

- Description 

Get the anchor coordinates of the control, supporting proportional and absolute values 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| axis | str | The axis to be obtained. The optional values are ["x","y"], "x" means obtaining the x coordinate of the control, and "y" means obtaining the y coordinate of the control | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | The size information of the control, see the remarks for details | 

- Remarks 
- Refer to the SetFullPosition interface. The size information of the control can be described by the three attributes of absoluteValue, followType, and relativeValue. 
Therefore, the structure of the return value is as follows: 
| Key value | Type | 
| ----------------| -------------| 
| "absoluteValue" | float | 
| "followType" | str | 
| "relativeValue" | float | 

- Example 

```python 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
# Get the x coordinate of the anchor point of image1 
ret = baseUIControl.GetFullPosition(axis="x") 
``` 

<span id="SetAnchorFrom"></span> 
## SetAnchorFrom 

- Description 

Set the anchor point of the control relative to the parent node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| anchorFrom | str | Anchor point relative to the parent node, optional values are detailed in the remarks | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes

- anchorFrom optional value 
| Value | Explanation | 
| ----------------| ------------------------------------------------------------ | 
| "top_left" | relative to the top left corner of the parent node | 
| "top_middle" | relative to the top middle of the parent node | 
| "top_right" | relative to the top right corner of the parent node | 
| "left_middle" | relative to the left middle of the parent node | 
| "center" | relative to the middle of the parent node | 
| "right_middle" | relative to the right middle of the parent node | 
| "bottom_left" | relative to the bottom left of the parent node | 
| "bottom_middle" | relative to the bottom middle of the parent node | 
| "bottom_right" | relative to the bottom right of the parent node | 

- Example 

```python 
# Set the top left corner of the image1 control relative to the parent node 
imagePath = "/panel/image1" 
anchorFrom = "top_left" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
ret = baseUIControl.SetAnchorFrom(anchorFrom) 
``` 

<span id="GetAnchorFrom"></span> 
## GetAnchorFrom 

- Description 

Determine which anchor point of the control relative to the parent node to calculate the position and size 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The parent node anchor point position information that the control relies on to calculate the position and size. For the specific meaning of the return value, please refer to the remarks of the SetAnchorFrom interface | 

- Example 

```python 
# we want to get image1 anchorFrom 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
anchorFrom = baseUIControl.GetAnchorFrom()
```




<span id="SetAnchorTo"></span> 
## SetAnchorTo 

- Description 

Set the control's own anchor position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| anchorTo | str | Control's own anchor position, optional values see notes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Optional values of anchorTo 
| Value | Explanation | 
| ----------------| ------------------------------------------------------------ | 
| "top_left" | The own anchor is located in the top left corner | 
| "top_middle" | The own anchor is located in the middle of the top | 
| "top_right" | The anchor point is located at the top right corner | 
| "left_middle" | The anchor point is located at the middle of the left | 
| "center" | The anchor point is located at the middle | 
| "right_middle" | The anchor point is located at the middle of the right | 
| "bottom_left" | The anchor point is located at the bottom left | 
| "bottom_middle" | The anchor point is located at the bottom middle | 
| "bottom_right" | The anchor point is located at the bottom right | 

- Example 

```python 
# Set the anchor point of the image1 control to the middle of itself 
imagePath = "/panel/image1" 
anchorTo = "center" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
ret = baseUIControl.SetAnchorTo(anchorTo) 
``` 

<span id="GetAnchorTo"></span> 
## GetAnchorTo


- Description 

Get the control's own anchor position information 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The control's own anchor position information. For the specific meaning of the return value, please refer to the remarks of the SetAnchorTo interface | 

- Example 

```python 
# we want to get image1 anchorTo 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
anchorTo = baseUIControl.GetAnchorTo() 
``` 

<span id="SetClipOffset"></span> 
## SetClipOffset 

- Description 

Set the control's clipping offset information 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| clipOffset | tuple(float,float) | The clipping offset information of this control, the first item is the horizontal axis, the second item is the vertical axis | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to set image1 maxSize 
imagePath = "/panel/image1"

clipOffset = (20, 20) 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
ret = baseUIControl.SetClipOffset(clipOffset) 
``` 

<span id="GetClipOffset"></span> 
## GetClipOffset 

- Description 

Get the clipping offset information of the control 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Clipping offset information of the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Example 

```python 
# we want to get image1 clipOffset 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
clipOffset = baseUIControl.GetClipOffset() 
``` 

<span id="SetClipsChildren"></span> 
## SetClipsChildren 

- Description 

Set whether the control enables clipping 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| clipsChildren | bool | True means enabled, False means disabled | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting success | 

- Example 

```python 
# we want to enable image1 clipsChildren 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
ret = baseUIControl.SetClipsChildren(True) 
``` 

<span id="GetClipsChildren"></span> 
## GetClipsChildren 

- Description 

Returns whether a control enables clipping based on the control path 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the control has enabled clipping content | 

- Example 

```python 
# we want to know whether image1 enables clipsChildren 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
clipsChildrenEnabled = baseUIControl.GetClipsChildren() 
``` 

<span id="SetMaxSize"></span> 
## SetMaxSize 

- Description 

Set the maximum size value allowed by the control 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| maxSize | tuple(float,float) | The maximum size allowed by the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- maxSize = (0, 0) means no limit 

- Example 

```python 
# we want to set image1 maxSize 
imagePath = "/panel/image1" 
imageMaxSize = (10, 10) 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
ret = baseUIControl.SetMaxSize(imageMaxSize) 
``` 

<span id="GetMaxSize"></span> 
## GetMaxSize 

- Description 

Get the maximum size allowed by the control 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | The maximum size allowed by the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Notes 
- A return value of (0, 0) means no limit 

- Example 

```python

# we want to get image1 maxSize 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
imageMaxSize = baseUIControl.GetMaxSize() 
``` 

<span id="SetMinSize"></span> 
## SetMinSize 

- Description 

Set the minimum size allowed by the control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| minSize | tuple(float,float) | The size allowed by the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- minSize = (0, 0) means no limit 

- Example 

```python 
# we want to set image1 minSize 
imagePath = "/panel/image1" 
imageMinSize = (10, 10) 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
ret = baseUIControl.SetMinSize(imageMinSize) 
``` 

<span id="GetMinSize"></span> 
## GetMinSize 

- Description 

Get the minimum size value allowed by the control 

- Parameters


    None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | The minimum size allowed by the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Notes 
- A return value of (0, 0) means no limit 

- Example 

```python 
# we want to get image1 minSize 
imagePath = "/panel/image1" 
baseUIControl = uiNode.GetBaseUIControl(imagePath) 
imageMinSize = baseUIControl.GetMinSize() 
``` 

<span id="GetPosition"></span> 
## GetPosition 

- Description 

Get the coordinates of the control relative to the parent node 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | The coordinate information of the control relative to the parent node, the first item is the horizontal axis, the second item is the vertical axis | 

- Example 

```python 
# we want to get text2 position 
text2Path = "/panel/text2" 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
textPosition = baseUIControl.GetPosition() 
``` 




<span id="SetSize"></span> 
## SetSize 

- Description 

Set the size of the control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| size | tuple(float,float) | The size information of the control, the first item is the horizontal axis, the second item is the vertical axis | 
| resizeChildren | bool | Whether to adjust the size of the child controls at the same time, the default is False | 

- Return value 

None 

- Example 

```python 
# we want to set text2 size 
text2Path = "/panel/text2" 
text2Size = (10, 10) 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
baseUIControl.SetSize(text2Size) 
``` 

<span id="GetSize"></span> 
## GetSize 

- Description 

Get the size of the control 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Size information of the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Example 


```python 
# we want to get text2 size 
text2Path = "/panel/text2" 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
text2Size = baseUIControl.GetSize() 
``` 

<span id="SetVisible"></span> 
## SetVisible 

- Description 

Choose whether to display a control based on the control path. You can adjust the display/hide of the entire JSON by passing in an empty string (""). 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| visible | bool | False means hiding the control, True means showing the control | 
| forceUpdtae | bool | Whether to force refresh, the default value is True. If set to True, refresh immediately and the new visible state will take effect. If it is set to False, you need to call UpdateScreen again to make the new state take effect. If there are a large number of SetVisible operations and they are not executed in the same frame, it is recommended to set it to False. When an update is required, call the UpdateScreen interface to refresh the interface and related control data | 

- Return value 

None 

- Remarks 
- Special case description: 
When the call of this interface comes from the button callback in the scroll list content control, and the purpose of the call is to hide the scroll list control or its parent node control, setting the forceUpdate parameter to True will cause scroll list data abnormality. If there is no need to refresh the interface, please set the forceUpdate parameter to False. If necessary, use a timer to delay the execution of the manual UpdateScreen interface. 

- Example 

```python 
# Hide the sub-control text2 of panel 
text2Path = "/panel/text2" 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
baseUIControl.SetVisible(False) 
# Hide the sub-controls text1, text2, text3 of panel in different frames 
parentPath = "/panel" 
textPrefabPath = "/panel/text_prefab" 
def _tickSetVisible(pathName): 
baseUIControl = uiNode.GetBaseUIControl(pathName) 
baseUIControl.SetVisible(False, False) 
def _tickUpdateScreen(): 
uiNode.UpdateScreen(True) 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddTimer(100, _tickSetVisible, "/panel/text1")
comp.AddTimer(200, _tickSetVisible, "/panel/text2")
comp.AddTimer(300, _tickSetVisible, "/panel/text3")

comp.AddTimer(300, _tickUpdateScreen) 
``` 

<span id="GetVisible"></span> 
## GetVisible 

- Description 

Returns whether a control is displayed based on the control path 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the control is displayed | 

- Example 

```python 
# We get whether text2 under panel is displayed 
text2Path = "/panel/text2" 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
textVisible = baseUIControl.GetVisible() 
``` 

<span id="SetTouchEnable"></span> 
## SetTouchEnable 

- Description 

Set whether the control is clickable and interactive 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | False means no response, True means resume response | 

- Return value 

None 


- Example 

```python 
# we want to set image_button unable 
imageButtonPath = "/image_button" 
baseUIControl = uiNode.GetBaseUIControl(imageButtonPath) 
baseUIControl.SetTouchEnable(False) 
``` 

<span id="SetAlpha"></span> 
## SetAlpha 

- Description 

Set the transparency of the node, only valid for image and label controls 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| alpha | float | Transparency, value between 0-1, 0 means completely transparent, 1 means completely opaque | 

- Return value 

None 

- Example 

```python 
# Set the transparency of text2 to semi-transparent 
text2Path = "/panel/text2" 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
baseUIControl.SetAlpha(0.5) 
``` 

<span id="SetLayer"></span> 
## SetLayer 

- Description 

Set the level of the control node. You can adjust the base level of the entire JSON by passing in an empty string (""). 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| layer | int | Set layer | 
| syncRefresh | bool | Whether synchronous refresh is required, the default value is True. Set True to allow the game to perform relevant calculations based on the layer of the control in the same frame, and set False to perform calculations in the next frame. If there are a large number of SetLayer operations in the same frame, it is recommended to set it to False. After the operation is completed, call the ScreenNode.UpdateScreen interface once to refresh the interface and related control data. | 
| forceUpdtae | bool | Whether forced refresh is required, the default value is True. Set True to synchronize or refresh the next frame according to the syncRefresh logic, and set False to not refresh the current frame and the next frame, and you need to manually call UpdateScreen to refresh. If there are a large number of SetLayer operations and they are not executed in the same frame, it is recommended to set it to False. When an update is required, call the UpdateScreen interface to refresh the interface and related control data | 

- Return value 

None 

- Example 

```python 
# Set the level of the text2 control 
text2Path = "/panel/text2" 
baseUIControl = uiNode.GetBaseUIControl(text2Path) 
baseUIControl.SetLayer(2) 
# Set the level of several controls in the same frame 
text1Path = "/panel/text1" 
uiNode.GetBaseUIControl(text1Path).SetLayer(1,False) 
text2Path = "/panel/text2" 
uiNode.GetBaseUIControl(text2Path).SetLayer(2,False) 
text3Path = "/panel/text3" 
uiNode.GetBaseUIControl(text3Path).SetLayer(3,False) 
# Set the level of several controls in different frames 
def _setLyerText1(path, layer): 
uiNode.GetBaseUIControl(text1Path).SetLayer(1,False,False) 
def _updateScreen(): 
uiNode.UpdateScreen(True) 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddTimer(100, _setLyerText1, "/panel/text1", 1) 
comp.AddTimer(200, _setLyerText1, "/panel/text2", 2) 
comp.AddTimer(300, _setLyerText1, "/panel/text3", 3) 
comp.AddTimer(300, _updateScreen) 
``` 

<span id="GetChildByName"></span> 
## GetChildByName 

- Description 

Get the BaseUIControl instance based on the name of the child control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| childName | str | Child node name | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseUIControl | BaseUIControl instance of child control | 

- Example 

```python 
# BaseUIControl instance of text1 gets BaseUIControl instance of text2 
text1Path = "/text1" 
text1Control = uiNode.GetBaseUIControl(text1Path) 
text2Control = text1Control.GetChildByName("text2") 
``` 

<span id="GetChildByPath"></span> 
## GetChildByPath 

- Description 

Get BaseUIControl instance based on relative path 

- Parameter 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| childPath | str | Path relative to the current BaseUIControl path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseUIControl | BaseUIControl instance of child control | 

- Example 

```python 
# Get the BaseUIControl instance with path "/text1/text2/text3" according to the BaseUIControl instance with path "/text1" 
text1Path = "/text1" 
text1Control = uiNode.GetBaseUIControl(text1Path) 
text3Control = text1Control.GetChildByPath("/text2/text3") 
``` 

<span id="resetAnimation"></span> 
## resetAnimation 

- Description


    Reset the animation of this control 

- Parameters 

None 

- Return value 

None 

- Notes 
- For UI property animation, see <a href="../../../../mcguide/18-界面与互動/19-控制属性动漫.html">属性动漫</a> 

- Example 

```python 
# Reset the property animation on the /text1 control 
text1Path = "/text1" 
text1Control = uiNode.GetBaseUIControl(text1Path) 
text1Control.resetAnimation() 
``` 

<span id="asLabel"></span> 
## asLabel 

- Description 

Convert the current BaseUIControl to a LabelUIControl instance. If the current control is not of the Label type, None is returned 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| LabelUIControl | LabelUIControl Instance | 

- Example 

```python 
text1Path = "/text1" 
text1BaseControl = uiNode.GetBaseUIControl(text1Path) 
text1LabelControl = text1BaseControl.asLabel() 
``` 




<span id="asButton"></span> 
## asButton 

- Description 

Convert the current BaseUIControl to a ButtonUIControl instance. If the current control is not of the button type, it returns None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ButtonUIControl | ButtonUIControl instance | 

- Example 

```python 
buttonPath = "/button" 
buttonBaseControl = uiNode.GetBaseUIControl(buttonPath) 
buttonControl = buttonBaseControl.asButton() 
``` 

<span id="asImage"></span> 
## asImage 

- Description 

Convert the current BaseUIControl to an ImageUIControl instance. If the current control is not of the image type, it returns None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ImageUIControl | ImageUIControl instance | 

- Example 

```python 
imagePath = "/image"

imageBaseControl = uiNode.GetBaseUIControl(imagePath) 
imageControl = imageBaseControl.asImage() 
``` 

<span id="asGrid"></span> 
## asGrid 

- Description 

Convert the current BaseUIControl to a GridUIControl instance. If the current control is not a grid type, return None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GridUIControl | GridUIControl instance | 

- Example 

```python 
gridPath = "/grid" 
gridBaseControl = uiNode.GetBaseUIControl(gridPath) 
gridControl = gridBaseControl.asGrid() 
``` 

<span id="asScrollView"></span> 
## asScrollView 

- Description 

Convert the current BaseUIControl to a ScrollViewUIControl instance. If the current control is not of scrollview type, return None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScrollViewUIControl | ScrollViewUIControl instance | 


- Example 

```python 
scrollViewPath = "/scroll_view" 
scrollViewBaseControl = uiNode.GetBaseUIControl(scrollViewPath) 
scrollViewControl = scrollviewBaseControl.asScrollView() 
``` 

<span id="asSwitchToggle"></span> 
## asSwitchToggle 

- Description 

Convert the current BaseUIControl to a SwitchToggleUIControl instance. If the current control is not a panel type or a toggle, it returns None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| SwitchToggleUIControl | SwitchToggleUIControl instance | 

- Example 

```python 
switchTogglePath = "/switch_toggle" 
switchToggleBaseControl = uiNode.GetBaseUIControl(switchTogglePath) 
switchToggleControl = switchToggleBaseControl.asSwitchToggle() 
``` 

<span id="asTextEditBox"></span> 
## asTextEditBox 

- Description 

Convert the current BaseUIControl to a TextEditBoxUIControl instance. If the current control is not an editbox type, return None 

- Parameters 

None 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TextEditBoxUIControl | TextEditBoxUIControl instance | 

- Example 

```python 
textEditBoxPath = "/text_edit_box" 
textEditBoxBaseControl = uiNode.GetBaseUIControl(textEditBoxPath) 
textEditBoxControl = textEditBoxBaseControl.asTextEditBox() 
``` 

<span id="asProgressBar"></span> 
## asProgressBar 

- Description 

Convert the current BaseUIControl to a ProgressBarUIControl instance. If the current control is not a panel type, None is returned 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fillImagePath | str | The path of the progress bar filling image, the default is "/filled_progress_bar", this parameter affects the effect of the control API | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ProgressBarUIControl | ProgressBarUIControl instance | 

- Example 

```python 
progressBarPath = "/progress_bar" 
progressBarBaseControl = uiNode.GetBaseUIControl(progressBarPath) 
progressBarControl = progressBarBaseControl.asProgressBar() 
``` 

<span id="asNeteasePaperDoll"></span> 
## asNeteasePaperDoll 

- Description 

Convert the current BaseUIControl to a NeteasePaperDollUIControl instance. If the current control is not a custom type, None is returned 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| NeteasePaperDollUIControl | NeteasePaperDollUIControl instance | 

- Example 

```python 
paperDollPath = "/paper_doll" 
paperDollBaseControl = uiNode.GetBaseUIControl(paperDollPath) 
paperDollControl = paperDollBaseControl.asNeteasePaperDoll() 
``` 

<span id="asMiniMap"></span> 
## asMiniMap 

- Description 

Convert the current BaseUIControl to a MiniMapUIControl instance. If the current control is not a minimap type, None is returned 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| MiniMapUIControl | MiniMapUIControl Example | 

- Example 

```python 
path = "/mini_map" 
miniMapBaseControl = uiNode.GetBaseUIControl(path) 
miniMapControl = miniMapBaseControl.asMiniMap() 
``` 

<span id="asSlider"></span> 
## asSlider 


- Description 

Convert the current BaseUIControl to a SliderUIControl instance. If the current control is not a slider type, it returns None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| SliderUIControl | SliderUIControl | 

- Example 

```python 
path = "/slider0" 
sliderBaseControl = uiNode.GetBaseUIControl(path) 
sliderControl = sliderBaseControl.asSlider() 
``` 

<span id="asItemRenderer"></span> 
## asItemRenderer 

- Description 

Convert the current BaseUIControl to an ItemRenderer instance. If the current control is not a custom type, it returns None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ItemRendererUIControl | ItemRendererUIControl instance | 

- Example 

```python 
itemRendererPath = "/item_renderer" 
itemRendererBaseControl = uiNode.GetBaseUIControl(itemRendererPath) 
itemRendererControl = itemRendererBaseControl.asItemRenderer() 
``` 




<span id="asNeteaseComboBox"></span> 
## asNeteaseComboBox 

- Description 

Convert the current BaseUIControl to a NeteaseComboBoxUIControl instance. If the current control is not a panel type, it returns None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| NeteaseComboBoxUIControl | NeteaseComboBoxUIControl instance | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
``` 

<span id="asStackPanel"></span> 
## asStackPanel 

- Description 

Convert the current BaseUIControl to a StackPanelUIControl instance. If the current control is not of stackPanel type, return None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| StackPanelUIControl | StackPanelUIControl instance | 

- Example 

```python 
stackPanelPath = "/stackPanel" 
stackPanelUIControl = uiNode.GetBaseUIControl(stackPanelPath).asStackPanel() 
```



<span id="asInputPanel"></span> 
## asInputPanel 

- Description 

Convert the current BaseUIControl to an InputPanelUIControl instance. If the current control is not of inputPanel type, return None 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| InputPanelUIControl | InputPanelUIControl instance | 

- Example 

```python 
inputPanelPath = "/inputPanel" 
inputPanelUIControl = uiNode.GetBaseUIControl(inputPanelPath).asInputPanel() 
``` 

# ButtonUIControl 

class in mod.client.ui.controls.buttonUIControl 

Button control class, inherited from BaseUIControl, contains button-related function interfaces in addition to basic function interfaces 

<span id="AddTouchEventParams"></span> 
## AddTouchEventParams 

- Description 

Enable the button callback function. If this function is not called, the button will have no callback 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| args | dict | The default is None. For detailed description, please see the notes. | 

- Return value 


None 

- Notes 
- AddTouchEventParams parameter args description: 
| Keyword | Data type | Description | 
| ----------| --------------------- | ---------| 
| isSwallow | bool | Defaults to True, whether the button swallows the event; or True, when the button is clicked, the click event will not penetrate into the world. For example, destroying blocks and turning the camera will not be responded to | 

- Example 

```python 
buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
``` 

<span id="SetButtonTouchDownCallback"></span> 
## SetButtonTouchDownCallback 

- Description 

Set the callback function triggered when the button is pressed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value 

None 

- Notes 
- onButtonTouchDownCallback parameter args description: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| #collection_name | str | Collection name to which the button belongs | 
| #collection_index | int | Collection index to which the button belongs | 
| ButtonState | int | Button state: Up is 0, Down is 1, the default is -1, it is recommended to use New | 
| TouchEvent | int | New version of button state: Up is 0, Down is 1, Cancel is 3, Move is 4, the default is -1 | 
| PrevButtonDownID | str | ID of the last button that was clicked Down, if not set to "-1" | 
| TouchPosX | float | UI coordinate X value on the screen when the button is clicked | 
| TouchPosY | float | UI coordinate Y value on the screen when the button is clicked | 
| ButtonPath | str | ComponentPath of the clicked button | 
| AddTouchEventParams| dict | Parameter dictionary passed in when calling the AddTouchEventParams interface | 

The relationship between events is shown in the figure below:

![Event description](../../picture/touch_event.png) 

- Example 

```python 
def onButtonTouchDownCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonTouchDownCallback(onButtonTouchDownCallback) 
``` 

<span id="SetButtonTouchUpCallback"></span> 
## SetButtonTouchUpCallback 

- Description 

Set the callback function when the touch is bounced within the button range 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value 

None 

- Remarks 
- For other related instructions, see the SetButtonTouchDownCallback interface: 

- Example 

```python 
def onButtonTouchUpCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonTouchUpCallback(onButtonTouchUpCallback) 
``` 



<span id="SetButtonTouchCancelCallback"></span> 
## SetButtonTouchCancelCallback 

- Description 

Set the callback function triggered when the touch is outside the button range 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value 

None 

- Remarks 
- For other related instructions, see the SetButtonTouchDownCallback interface: 

- Example 

```python 
def onButtonTouchCancelCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonTouchCancelCallback(onButtonTouchCancelCallback) 
``` 

<span id="SetButtonTouchMoveCallback"></span> 
## SetButtonTouchMoveCallback 

- Description 

Set the callback function triggered when the touch moves after pressing 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value 

None


- Notes 
- For other related instructions, see SetButtonTouchDownCallback interface: 

- Example 

```python 
def onButtonTouchMoveCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonTouchMoveCallback(onButtonTouchMoveCallback) 
``` 

<span id="SetButtonTouchMoveInCallback"></span> 
## SetButtonTouchMoveInCallback 

- Description 

Set the callback function triggered when entering the control after pressing the button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value 

None 

- Remarks 
- For other related instructions, see the SetButtonTouchDownCallback interface: 

- Example 

```python 
def onButtonTouchMoveInCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonTouchMoveInCallback(onButtonTouchMoveInCallback) 
``` 




<span id="SetButtonTouchMoveOutCallback"></span> 
## SetButtonTouchMoveOutCallback 

- Description 

Set the callback function triggered when the control is exited after pressing the button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value 

None 

- Remarks 
- For other related instructions, see the SetButtonTouchDownCallback interface: 

- Example 

```python 
def onButtonTouchMoveOutCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonTouchMoveOutCallback(onButtonTouchMoveOutCallback) 
``` 

<span id="SetButtonScreenExitCallback"></span> 
## SetButtonScreenExitCallback 

- Description 

Set the callback function to be triggered when the mouse is not lifted when the canvas where the button is located exits 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callbackFunc | function | Callback function, must be a UI class function | 

- Return value


None 

- Notes 
- For other related instructions, see SetButtonTouchDownCallback interface: 

- Example 

```python 
def onButtonScreenExitCallback(args): 
pass 

buttonPath = "/panel/test_btn" 
buttonUIControl = uiNode.GetBaseUIControl("/panel/test_btn").asButton() 
buttonUIControl.AddTouchEventParams({"isSwallow":True}) 
buttonUIControl.SetButtonScreenExitCallback(onButtonScreenExitCallback) 
``` 

# GridUIControl 

class in mod.client.ui.controls.gridUIControl 

Grid control class, inherited from BaseUIControl, contains grid-related function interfaces in addition to basic function interfaces 

<span id="SetGridDimension"></span> 
## SetGridDimension 

- Description 

Set the size of the Grid control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | tuple(int,int) | Set the horizontal and vertical size of the grid | 

- Return value 

None 

- Example 

```python 
# we want change grid dimension 
gridPath = "/grid1" 
gridUIControl = uiNode.GetBaseUIControl(gridPath).asGrid() 
gridUIControl.SetGridDimension((2, 2))

``` 

# ImageUIControl 

class in mod.client.ui.controls.imageUIControl 

Image control class, inherited from BaseUIControl, contains image-related function interfaces in addition to basic function interfaces 

<span id="SetSprite"></span> 
## SetSprite 

- Description 

Change the specified texture for the image control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| texturePath | str | Texture path, needs to start from the textures directory under resource_pack | 

- Return value 

None 

- Remarks 
- When changing the texture for ImageButton, pay attention to using the child control path (default / hover / pressed) to obtain ImageUIControl 

- Example 

```python 
# we want to set image_button textures
imageButtonPath = "/image_button"
buttonUIControl = uiNode.GetBaseUIControl(imageButtonPath).asButton()
buttonDefaultUIControl = buttonUIControl.GetChildByName("default").asImage()
buttonHoverUIControl = buttonUIControl.GetChildByName("hover").asImage()
buttonPressedUIControl = buttonUIControl.GetChildByName("pressed").asImage()
buttonDefaultUIControl.SetSprite("textures/button01_default")
buttonHoverUIControl.SetSprite("textures/button01_hover")
buttonPressedUIControl.SetSprite("textures/button01_pressed")
```



<span id="SetSpriteColor"></span>
## SetSpriteColor

- describe


    Set the image color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| color | tuple(float,float,float) | Image color rgb, value [0, 1] | 

- Return value 

None 

- Example 

```python 
# We want the durability bar to change color with the durability, green when full and red when empty, where barPath is the durability bar path 
durabilityRatio = 0.8 # Durability ratio, 1 is full durability 
barPath = "/image_bar" 
imageUIControl = uiNode.GetBaseUIControl(barPath).asImage() 
imageUIControl.SetSpriteColor((1 - durabilityRatio, durabilityRatio, 0)) 
``` 

<span id="SetSpriteGray"></span> 
## SetSpriteGray 

- Description 

Setting the image control to gray is more efficient than directly setting a gray image to SetSprite 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| gray | bool | True sets the image to gray, False restores the original color | 

- Return value 

None 

- Example 

```python 
# we want set image gray 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.SetSpriteGray(True) 
```




<span id="SetSpriteUV"></span> 
## SetSpriteUV 

- Description 

Set the starting uv of the image, which is consistent with the "uv" attribute in json 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| uv | tuple(float,float) | The upper left corner of the image is (0,0), the right is the x-axis, and the bottom is the y-axis | 

- Return value 

None 

- Example 

```python 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.SetSpriteUV((10, 0)) 
``` 

<span id="SetSpriteUVSize"></span> 
## SetSpriteUVSize 

- Description 

Set the uv size of the image, which is consistent with the "uv_size" attribute in json 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| uvSize | tuple(float,float) | The x-axis is to the right of the image, and the y-axis is to the bottom | 

- Return value 

None 

- Example 

```python

imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.SetSpriteUVSize((40, 30)) 
``` 

<span id="SetSpriteClipRatio"></span> 
## SetSpriteClipRatio 

- Description 

Set the image clipping area ratio (without changing the control size). You can use the clip_ratio property of the image control to control the direction. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| clipRatio | float | The cropping ratio of the image (range 0 to 1), the cropping accuracy is related to the image resolution | 

- Return value 

None 

- Example 

```python 
# We want to set the progress of the progress bar created by the UI editor 
# The editor progress bar contains two image controls (named empty_progress_bar and filled_progress_bar) 
progress = 0.8 # When used to simulate progress, the following cropping ratio needs to be set to (1-progress) to get the correct visual effect 
imagePath = "/progress_bar0/filled_progress_bar" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.SetSpriteClipRatio(1.0 - progress) 
``` 

<span id="SetSpritePlatformHead"></span> 
## SetSpritePlatformHead 

- Description 

Set the image to the avatar of the current account in the Minecraft mobile launcher 

- Parameters 

None 

- Return value 


None 

- Notes 
- This interface only supports mobile calls, and is invalid on other platforms: 

- Example 

```python 
# We want to set the current image control to the avatar of the current account of the Minecraft mobile launcher 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.SetSpritePlatformHead() 
``` 

<span id="SetSpritePlatformFrame"></span> 
## SetSpritePlatformFrame 

- Description 

Set the image to the avatar frame of the current account of the Minecraft mobile launcher 

- Parameters 

None 

- Return value 

None 

- Notes 
- This interface only supports mobile calls, and is invalid on other platforms: 
- When the avatar frame of the Minecraft mobile launcher account is a dynamic avatar frame, the avatar frame image will not be loaded. This problem will be fixed in the next version: 

- Example 

```python 
# We want to set the current image control to the avatar frame of the current account of the Minecraft mobile launcher 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.SetSpritePlatformFrame() 
``` 

<span id="SetClipDirection"></span> 
## SetClipDirection 

- Description


    Set the clipping direction of the image control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| clipDirection | str | Clipping direction of the image control, see the notes for optional values | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Optional values of clipDirection 
| Value | Explanation | 
| ------------------------| --------------------------------------------- | 
| "fromLeftToRight" | From left to right | 
| "fromRightToLeft" | From right to left | 
| "fromOutsideToInside" | From outside to inside | 
| "fromTopToBottom" | From top to bottom | 
| "fromBottomToTop" | From bottom to top | 

- Example 

```python 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
clipDirection = "fromOutsideToInside" 
ret = imageUIControl.SetClipDirection(clipDirection) 
``` 

<span id="GetClipDirection"></span> 
## GetClipDirection 

- Description 

Get the clipping direction of the image control 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| str | The clipping direction of the image control. For the meaning of the return value, see the remarks of the SetClipDirection interface. | 

- Example 

```python 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
imageUIControl.GetClipDirection() 
``` 

<span id="SetImageAdaptionType"></span> 
## SetImageAdaptionType 

- Description 

Set the image adaptation method and information of the image control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| imageAdaptionType | str | The image adaptation method of the image control. For optional values, see the remarks. | 
| imageAdaptionData | tuple(float,float,float,float) | If the image is not in Nine-grid adaptation mode, this value does not need to be passed. Otherwise, it needs to be set. Each value in the tuple represents the four parameters of Nine-grid cutting: left, right, top, and bottom | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The optional values of imageAdaptionType are as follows 
| Value | Explanation | 
| ------------------------| --------------------------------------------- | 
| "normal" | Normal adaptation, do not open Nine-grid and keep the aspect ratio | 
| "filled" | Filled adaptation, do not open Nine-grid and keep the aspect ratio | 
| "oldNineSlice" | Old version Nine-grid adaptation | 
| "originNineSlice" | Original Nine-grid adaptation | 

- Example 

```python 
imagePath = "/image" 
imageUIControl = uiNode.GetBaseUIControl(imagePath).asImage() 
# Normal adaptation 
ret = imageUIControl.SetImageAdaptionType("normal") 
# Adapt to the original nine-grid and set the margins

ret = imageUIControl.SetImageAdaptionType("originNineSlice", (0, 0, 0, 0)) 
``` 

# InputPanelUIControl 

class in mod.client.ui.controls.inputPanelUIControl 

Layout panel control class, inherited from BaseUIControl, contains text-related functional interfaces in addition to basic functional interfaces 

<span id="SetIsModal"></span> 
## SetIsModal 

- Description 

Sets whether the current panel is a modal box 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isModal | bool | Whether the current panel is a modal box | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to set inputPanel1 isModal 
inputPanelPath = "/inputPanel1" 
inputPanel = uiNode.GetBaseUIControl(inputPanelPath).asInputPanel() 
ret = inputPanel.SetIsModal(True) 
``` 

<span id="GetIsModal"></span> 
## GetIsModal 

- Description 

Determine whether the current panel is a modal box 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the current panel is a modal box | 

- Example 

```python 
# we want to know whether inputPanel1 isModal 
inputPanelPath = "/inputPanel1" 
inputPanel = uiNode.GetBaseUIControl(inputPanelPath).asInputPanel() 
inputPanel.GetIsModal() 
``` 

<span id="SetOffsetDelta"></span> 
## SetOffsetDelta 

- Description 

Set the drag offset of the click panel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset_delta | tuple(float,float) | The drag offset of the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Click the panel to drag the function and the drag offset, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#InputPanel">InputPanel</a> 

- Example 

```python 
# we want to set inputPanel's offset_delta 
inputPanelPath = "/inputPanel1" 
inputPanel = uiNode.GetBaseUIControl(inputPanelPath).asInputPanel()
success = inputPanel.SetOffsetDelta((100, 100))
```



<span id="GetOffsetDelta"></span> 
## GetOffsetDelta 

- Description 

Get the drag offset of the click panel 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | The drag offset of the control, the first item is the horizontal axis, the second item is the vertical axis | 

- Notes 
- Click the panel drag function and drag offset, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#InputPanel">InputPanel</a> 

- Example 

```python 
# we want to get inputPanel1's offset_delta 
inputPanelPath = "/inputPanel1" 
inputPanel = uiNode.GetBaseUIControl(inputPanelPath).asInputPanel() 
offset_delta = inputPanel.GetOffsetDelta() 
``` 

# ItemRendererUIControl 

class in mod.client.ui.controls.itemRendererUIControl 

Item rendering control class, inherited from BaseUIControl, contains item rendering control related function interfaces in addition to basic function interfaces 

<span id="SetUiItem"></span> 
## SetUiItem 

- Description 

Set the items displayed by the ItemRenderer control. For details on the configuration of the ItemRenderer control, see <a href="../../../../mcguide/18-界面与互動/30-UI说明文档.html#itemrenderer">Control Introduction ItemRenderer</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| itemName | str | item identifier | 
| auxValue | int | item additional value | 
| isEnchanted | bool | optional parameter, whether to display the enchantment effect, the default is False and not displayed | 
| userData | dict | optional parameter, if it is a disaster banner or firework star with userData, you need to pass this parameter to display correctly. Currently, only disaster banners and firework stars need to be passed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set the result, True means success | 

- Example 

```python 
#Set the display to wooden board block 
itemRenderPath = "/panel/item_renderer" 
itemName = "minecraft:wool" 
auxValue = 0 
itemRendererBaseControl = uiNode.GetBaseUIControl(itemRenderPath) 
itemRendererControl = itemRendererBaseControl.asItemRenderer() 
itemRendererControl.SetUiItem(itemName, auxValue) 
``` 

# LabelUIControl 

class in mod.client.ui.controls.labelUIControl 

Text control class, inherited from BaseUIControl, contains text-related functional interfaces in addition to basic functional interfaces 

<span id="SetText"></span> 
## SetText 

- Description 

Set the text information of the Label 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| text | str | The content of the text can support [style code](https://minecraft-zh.gamepedia.com/%E6%A0%B7%E5%BC%8F%E4%BB%A3%E7%A0%81) (§You can set the color and format of the text, etc. This usage is more flexible and changeable) | 
| syncSize | bool | Whether to update the text box size synchronously when setting the text, the default value is False | 

- Return value 

None 

- Example


```python 
# we want to set text2 content 
text2Path = "/panel/text2" 
text = "Hello World!" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.SetText(text) 
``` 

<span id="GetText"></span> 
## GetText 

- Description 

Get the text information of the Label. If the acquisition fails, None will be returned 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Text information | 

- Notes 
- Failure to obtain is usually due to an incorrect path or the control is not of Label type 

- Example 

```python 
# we want to get text2 content 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.GetText() 
``` 

<span id="SetTextColor"></span> 
## SetTextColor 

- Description 

Set the color of the Label text 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| color | tuple(float,float,float) | Text color information (r, g, b), value [0, 1] | 

- Return value 

None 

- Remarks 
- This interface does not support the alpha channel to change the transparency, it is recommended to use the SetAlpha interface 

- Example 

```python 
# we want to set text2 green 
text2Path = "/panel/text2" 
color = (0, 1, 0) 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.SetTextColor(color) 
``` 

<span id="GetTextColor"></span> 
## GetTextColor 

- Description 

Get Label text color 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float,float) | Get text color information (r, g, b, a), value [0, 1] | 

- Example 

```python 
# we want to get text2 color 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.GetTextColor() 
``` 




<span id="SetTextFontSize"></span> 
## SetTextFontSize 

- Description 

Set the font size of the text in the Label 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| componentPath | str | The control path starting from the main node | 
| scale | float | The font_size of label is the default font size in the Label. The value is limited to [small normal large]. This scale is based on the default font to scale the font size. The default font size is 1.0 | 

- Return value 

None 

- Example 

```python 
# set text font size 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.SetTextFontSize(0.8) 
``` 

<span id="SetTextAlignment"></span> 
## SetTextAlignment 

- Description 

Set the text alignment of the text control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| textAlignment | str | Text alignment of the text control, see the notes for optional values | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Notes 
- Optional values for textAlignment 
| Value | Explanation | 
| ----------------| ------------------------------------------------------------ | 
| "left" | Text aligned to the left (horizontally) | 
| "right" | Text aligned to the right (horizontally) | 
| "center" | Text aligned to the center (horizontally) | 

- Example 

```python 
# we want to align text2 to center 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
textAlignment = "center" 
ret = labelUIControl.SetTextAlignment(textAlignment) 
``` 

<span id="GetTextAlignment"></span> 
## GetTextAlignment 

- Description 

Get the text alignment of the text control 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Text alignment of the text control. For the specific meaning of the return value, please refer to the remarks of the SetTextAlignment interface | 

- Example 

```python 
# we want to get text2 textAlignment 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.GetTextAlignment() 
``` 

<span id="SetTextLinePadding"></span> 
## SetTextLinePadding


- Description 

Set the line spacing of the text control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| textLinePadding | float | Line spacing of the text control, in pixels | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to set text2 textLinePadding 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
textLinePadding = 20 
ret = labelUIControl.SetTextLinePadding(textLinePadding) 
``` 

<span id="GetTextLinePadding"></span> 
## GetTextLinePadding 

- Description 

Get the line spacing of the text control 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | The line spacing of the text control, in pixels | 

- Example 

```python 
# we want to get text2 textLinePadding

text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.GetTextLinePadding() 
``` 

<span id="EnableTextShadow"></span> 
## EnableTextShadow 

- Description 

Enable the text control to display a shadow 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to enable text2 textShadow 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
ret = labelUIControl.EnableTextShadow() 
``` 

<span id="DisableTextShadow"></span> 
## DisableTextShadow 

- Description 

Disable the text control to display shadow 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Example 

```python 
# we want to disable text2 textShadow 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
ret = labelUIControl.DisableTextShadow() 
``` 

<span id="IsTextShadowEnabled"></span> 
## IsTextShadowEnabled 

- Description 

Determine whether the text control displays a shadow 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the text control displays a shadow | 

- Example 

```python 
# we want to know whether text2 has shadow 
text2Path = "/panel/text2" 
labelUIControl = uiNode.GetBaseUIControl(text2Path).asLabel() 
labelUIControl.IsTextShadowEnabled() 
``` 

# MiniMapUIControl 

class in mod.client.ui.controls.minimapUIControl 

UI object-oriented minimap control class 
Used to render real-time map on UI 

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
path = "/demoPanel/netease_mini_map" 
doll = uiNode.GetBaseUIControl(path).asMiniMap() 
doll.ZoomIn(0.2) 
``` 

<span id="ZoomOut"></span> 
## ZoomOut 

- Description 

Zoom out map 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | The reduction value based on the original value can control the zoom speed. The default value is 0.05 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- The client has limited map block loading. If the map UI interface is too large or the map zoom factor is too large, the small map will not be able to display the unloaded blocks. 

- Example


```python 
path = "/demoPanel/netease_mini_map" 
doll = uiNode.GetBaseUIControl(path).asMiniMap() 
doll.ZoomOut(0.2) 
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
path = "/demoPanel/netease_mini_map" 
doll = uiNode.GetBaseUIControl(path).asMiniMap() 
doll.ZoomReset(0.2) 
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
path = "/demoPanel/netease_mini_map" 
doll = uiNode.GetBaseUIControl(path).asMiniMap() 
doll.SetHighestY(255) 
``` 

# NeteaseComboBoxUIControl 

class in mod.client.ui.controls.neteaseComboBoxUIControl 

Netease version single-select drop-down box control class, inherited from BaseUIControl, contains single-select drop-down box related function interfaces in addition to basic function interfaces 

<span id="AddOption"></span> 
## AddOption 

- Description 

Add a drop-down box item, return True if added successfully, otherwise return False 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| showName | str | Display text, required parameter | 
| icon | str | Texture path, if filled in, the icon will be displayed at the front of the drop-down box item, the default is None | 
| userData | any | Custom data, when the drop-down box item is selected, it will be returned with the callback function, the default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it is added successfully | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox()

success = comboBoxUIControl.AddOption("Test item", "textures/ui/test_icon", {"mydata": "netease"}) 
``` 

<span id="ClearOptions"></span> 
## ClearOptions 

- Description 

Clear the drop-down box 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
comboBoxUIControl.ClearOptions() 
``` 

<span id="ClearSelection"></span> 
## ClearSelection 

- Description 

Clear the current selection and restore the drop-down box to the unselected state 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox()

comboBoxUIControl.ClearSelection() 
``` 

<span id="GetOptionIndexByShowName"></span> 
## GetOptionIndexByShowName 

- Description 

Find the index position of the corresponding drop-down box item according to the display text. If not found, return -1 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Display text | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Index position | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
index = comboBoxUIControl.GetOptionIndexByShowName("Test item") 
``` 

<span id="GetOptionShowNameByIndex"></span> 
## GetOptionShowNameByIndex 

- Description 

Search for the current stack text according to the index position. If not found, return None 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| index | int | Index position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| str | Display text | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
text = comboBoxUIControl.GetOptionShowNameByIndex(0) 
``` 

<span id="GetOptionCount"></span> 
## GetOptionCount 

- Description 

Get the number of options 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The number of current drop-down box options | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
totalNum = comboBoxUIControl.GetOptionCount() 
``` 

<span id="GetSelectOptionIndex"></span> 
## GetSelectOptionIndex 

- Description 

Get the index of the currently selected item. If there is no selected item, return -1 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Index of the currently selected item in the drop-down box | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
currentIndex = comboBoxUIControl.GetSelectOptionIndex() 
``` 

<span id="GetSelectOptionShowName"></span> 
## GetSelectOptionShowName 

- Description 

Get the display text of the currently selected item. If there is no selected item, None is returned 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Display text of currently selected item | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
currentText = comboBoxUIControl.GetSelectOptionShowName() 
``` 

<span id="RemoveOptionByShowName"></span> 
## RemoveOptionByShowName 

- Description 

Remove the corresponding drop-down box item according to the provided display text. Return True if the removal is successful, otherwise return False


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| showName | str | Display text | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
success = comboBoxUIControl.RemoveOptionByShowName("Test item") 
``` 

<span id="RemoveOptionByIndex"></span> 
## RemoveOptionByIndex 

- Description 

Remove the corresponding drop-down box item according to the provided index. Return True if the removal is successful, otherwise return False 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| index | int | Index | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
success = comboBoxUIControl.RemoveOptionByIndex(0)
```



<span id="SetSelectOptionByIndex"></span> 
## SetSelectOptionByIndex 

- Description 

Select the corresponding drop-down box item according to the provided index 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| index | int | Index | 

- Return value 

None 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
comboBoxUIControl.SetSelectOptionByIndex(0) 
``` 

<span id="SetSelectOptionByShowName"></span> 
## SetSelectOptionByShowName 

- Description 

Select the corresponding drop-down box item according to the provided display text 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Index | 

- Return value 

None 

- Example 

```python 
comboBoxPath = "/panel/comboBoxPanel"

comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
comboBoxUIControl.SetSelectOptionByShowName("Test item") 
``` 

<span id="RegisterOpenComboBoxCallback"></span> 
## RegisterOpenComboBoxCallback 

- Description 

Register the callback for the event of expanding the drop-down box 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Callback function, must be a class function of UI | 

- Return value 

None 

- Example 

```python 
# Register the callback for the event of expanding the drop-down box. The registered callback function will be called when clicking the expanded drop-down box 
def onOpenComboBoxCallback(args): 
pass 

comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
comboBoxUIControl.RegisterOpenComboBoxCallback(onOpenComboBoxCallback) 
``` 

<span id="RegisterCloseComboBoxCallback"></span> 
## RegisterCloseComboBoxCallback 

- Description 

Register close drop-down box event callback 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Callback function, must be a UI class function | 


- Return value 

None 

- Example 

```python 
# Register the callback function for closing the drop-down box event. The registered callback function will be called when clicking to close the drop-down box 
def onCloseComboBoxCallback(args): 
pass 

comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
comboBoxUIControl.RegisterCloseComboBoxCallback(onCloseComboBoxCallback) 
``` 

<span id="RegisterSelectItemCallback"></span> 
## RegisterSelectItemCallback 

- Description 

Register the callback function for selecting the content of the drop-down box 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | callback function, must be a UI class function | 

- Return value 

None 

- Remarks 
- onSelectItemCallback parameter description: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| index | int | Index of the currently selected item | 
| showName | str | Display text of the currently selected item | 
| userData | Unknown | Custom data of the currently selected item. If no custom data is passed in when adding a drop-down box item, this is None | 

- Example 

```python 
# Register the callback for the selected drop-down box content event. The registered callback function will be called when the drop-down box is closed 
def onSelectItemCallback(index, showName, userData): 
pass 


comboBoxPath = "/panel/comboBoxPanel" 
comboBoxUIControl = uiNode.GetBaseUIControl(comboBoxPath).asNeteaseComboBox() 
comboBoxUIControl.RegisterSelectItemCallback(onSelectItemCallback) 
``` 

# NeteasePaperDollUIControl 

class in mod.client.ui.controls.neteasePaperDollUIControl 

Paper doll control class, inherited from BaseUIControl, contains paper doll related functional interfaces in addition to basic functional interfaces 
Used to render entities/skeleton models/special effects on UI 

<span id="GetModelId"></span> 
## GetModelId 

- Description 

Get the rendered skeleton model Id 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Skeleton model Id, returns -1 if failed or does not exist | 

- Notes 
- Note: Please do not execute immediately after calling RenderEntity/RenderSkeletonModel. 
The bone model Id can be used in the following situations: 
1. Bind another bone model; 
2. Bind sequence frame animation; 
3. Bind special effect particle animation 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
path = '/demoPanel/paper_doll' 
doll = uiNode.GetBaseUIControl(path).asNeteasePaperDoll() 
modelId = doll.GetModelId() 
if modelId == -1: 
return 
#Purpose 1: Bind another bone model 
modelComp = clientApi.GetEngineCompFactory().CreateModel(modelId) 
newModelId = modelComp.BindModelToModel("rightHand", "gun") # Attach the bone model named gun to the rightHand bone

#Purpose 2: Bind sequence frame animation 
sfxId = clientSystem.CreateEngineSfxFromEditor("effects/example_sfx.json") # Create special effects 
comp = clientApi.GetEngineCompFactory().CreateFrameAniSkeletonBind(sfxId) 
comp.Bind(modelId, "root", (0, 1, 0), (0, 0, 0)) # Bind the special effect to the bone node of the skeleton model 
frameComp = clientApi.GetEngineCompFactory().CreateFrameAniControl(sfxId) 
frameComp.Play() # Play animation 
clientSystem.DestroyEntity(sfxId) # Destroy animation 
#Purpose 3: Bind special effect particle animation 
particleEntityId = clientSystem.CreateEngineParticle("effects/example_particle.json", (0,0,0)) # Create special effects 
comp = clientApi.GetEngineCompFactory().CreateParticleSkeletonBind(particleEntityId) 
comp.Bind(modelId, "root", (0, 1, 0), (0, 0, 0)) # Bind special effects to the skeleton model's bone node 
particleComp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
particleComp.Play() # Play animation 
clientSystem.DestroyEntity(particleEntityId) # Destroy animation 
``` 

<span id="RenderEntity"></span> 
## RenderEntity 

- Description 

Rendering entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| params | dict | Rendering parameters, see the notes for detailed description | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- RenderEntity parameter params description: 
The params parameter is explained as follows: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| entity_id | str | Entity ID of the rendered creature | 
| scale | float | Rendering scale, default is 1.0 | 
| render_depth | int | Rendering depth, default is -50 for players, -15 for ordinary creatures, this parameter can solve the UI occlusion culling problem | 
| init_rot_y | float | Initial Y direction | 
| molang_dict | dict | molang expression dictionary, where key is str and value is float | 

- Example 


```python 
path = '/demoPanel/paper_doll' 
param = { 
"entity_id": "-8589934591", 
"scale": 0.5, 
"render_depth": -50, 
"init_rot_y": 60, 
"molang_dict": {"variable.liedownamount": 1} 
} 
doll = uiNode.GetBaseUIControl(path).asNeteasePaperDoll() 
doll.RenderEntity(param) 
``` 

<span id="RenderSkeletonModel"></span> 
## RenderSkeletonModel 

- Description 

Rendering skeleton model (not dependent on entity) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| params | dict | Rendering parameters, see the notes for detailed description | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- RenderSkeletonModel parameter params description: 
The params parameter is explained as follows: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| skeleton_model_name | str | Skeleton model name | 
| animation | str | Skeleton action name, default is idle | 
| animation_looped | bool | Skeleton action looping, default is True | 
| scale | float | Rendering scale, default is 1.0 | 
| render_depth | int | Rendering depth, the default is -50 for players and -15 for ordinary creatures. This parameter can solve the UI occlusion culling problem | 
| init_rot_y | float | Initial Y direction | 
| molang_dict | dict | molang expression dictionary, where key is str and value is float | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
path = '/demoPanel/paper_doll' 
param = { 
"skeleton_model_name": "ty_yuanshenghuli_0_0", 
"animation": "idle_stand", 
"scale": 0.5, 
"render_depth": -50, 
"init_rot_y": 60, 
"molang_dict": {"variable.liedownamount": 1} 
} 
doll = uiNode.GetBaseUIControl(path).asNeteasePaperDoll() 
doll.RenderSkeletonModel(param) 
``` 

<span id="RenderBlockGeometryModel"></span> 
## RenderBlockGeometryModel 

- Description 

Rendering mesh model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| params | dict | Rendering parameters, see the notes for details | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- The mesh model is generated using [CombineBlockPaletteToGeometry](../Block/Block Geometry Model.md#combineblockpalettetogeometry) 
- Each time you enter the game, you need to call this interface again to render the mesh model. You can use [SerializeBlockPalette](../Block/Block Palette.md#serializeblockpalette) and [DeserializeBlockPalette](../Block/Block Palette.md#deserializeblockpalette) to save and reload the palette, and regenerate the mesh model for rendering. 
- RenderBlockGeometryModel parameter params description: 
The params parameter is explained as follows: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| block_geometry_model_name | str | Mesh model name, can be used CombineBlockPaletteToGeometry return value | | 
| scale | float | Rendering scale, default is 1.0 | | 
| init_rot_y | float | Initial Y direction | 
| molang_dict | dict | molang expression dictionary, where key is str and value is float | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
path = '/demoPanel/paper_doll' 
param = { 
"block_geometry_model_name": "my_geometry_model", 
"scale": 0.5, 
"init_rot_y": 60, 
"molang_dict": {"variable.liedownamount": 1} 
} 
doll = uiNode.GetBaseUIControl(path).asNeteasePaperDoll() 
doll.RenderBlockGeometryModel(param) 
``` 

# ProgressBarUIControl 

class in mod.client.ui.controls.progressBarUIControl 

Progress bar control class, inherited from BaseUIControl, contains progress bar related function interfaces in addition to basic function interfaces 

<span id="SetValue"></span> 
## SetValue 

- Description 

Set the progress of the progress bar 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| progress | float | Progress, value [0, 1] | 

- Return value 

None 

- Example 

```python 
# we want to set progress 
progressBarPath = "/panel/progress_bar" 
progressBarUIControl = uiNode.GetBaseUIControl(progressBarPath).asProgressBar() 
progressBarUIControl.SetValue(0.8) 
``` 

# ScrollViewUIControl 


class in mod.client.ui.controls.scrollViewUIControl 

Scroll list control class, inherited from BaseUIControl, contains scroll list related function interfaces in addition to basic function interfaces 

<span id="SetScrollViewPos"></span> 
## SetScrollViewPos 

- Description 

Set the position of the current scroll_view content 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | float | The position to jump to, generally the set position will appear at the top of the scroll_view. | 

- Return value 

None 

- Example 

```python 
# we want set scroll_view pos 
scrollViewPath = "/scroll_view0" 
scrollViewUIControl = uiNode.GetBaseUIControl(scrollViewPath).asScrollView() 
scrollViewUIControl.SetScrollViewPos(100) 
``` 

<span id="GetScrollViewPos"></span> 
## GetScrollViewPos 

- Description 

Get the position of the top content of the current scroll_view 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | The position of the top content of the current scroll_view | 

- Example


```python 
# we want get scroll_view pos 
scrollViewPath = "/scroll_view0" 
scrollViewUIControl = uiNode.GetBaseUIControl(scrollViewPath).asScrollView() 
scrollViewUIControl.GetScrollViewPos() 
``` 

<span id="SetScrollViewPercentValue"></span> 
## SetScrollViewPercentValue 

- Description 

Set the percentage position of the current scroll_view content 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| percent_value | int | The percentage position to jump to. Generally, the set position will appear at the top of the scroll_view. The value range is 0-100 | 

- Return value 

None 

- Example 

```python 
# we want set scroll_view percent pos 
scrollViewPath = "/scroll_view0" 
scrollViewUIControl = uiNode.GetBaseUIControl(scrollViewPath).asScrollView() 
scrollViewUIControl.SetScrollViewPercentValue(20) 
``` 

<span id="GetScrollViewContentPath"></span> 
## GetScrollViewContentPath 

- Description 

Returns the path of the scroll_view content 

- Parameters 

None 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The path of the scroll_view content | 

- Example 

```python 
# we want get scroll_view content path 
scrollViewPath = "/scroll_view0" 
scrollViewUIControl = uiNode.GetBaseUIControl(scrollViewPath).asScrollView() 
path = scrollViewUIControl.GetScrollViewContentPath() 
``` 

<span id="GetScrollViewContentControl"></span> 
## GetScrollViewContentControl 

- Description 

Returns the BaseUIControl instance of the scroll_view content 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseUIControl | BaseUIControl instance of the scroll_view content | 

- Example 

```python 
# we want get scroll_view content 
scrollViewPath = "/scroll_view0" 
scrollViewUIControl = uiNode.GetBaseUIControl(scrollViewPath).asScrollView() 
contentUIControl = scrollViewUIControl.GetScrollViewContentControl() 
``` 

# SliderUIControl 

class in mod.client.ui.controls.sliderUIControl 

Text input box control class, inherited from BaseUIControl, contains text input box related function interfaces in addition to basic function interfaces 


<span id="GetSliderValue"></span> 
## GetSliderValue 

- Description 

Get the value of the slider, return 0 if failed 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Slider value | 

- Example 

```python 
# we want to get slider value 
sliderPath = "/panel/slider0" 
sliderUIControl = uiNode.GetBaseUIControl(sliderPath).asSlider() 
value = sliderUIControl.GetSliderValue() 
``` 

<span id="SetSliderValue"></span> 
## SetSliderValue 

- Description 

Set the value of the slider 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Slider value | 

- Return value 

None 

- Example 

```python 
# we want to set slider value 
sliderPath = "/panel/slider0"

sliderUIControl = uiNode.GetBaseUIControl(sliderPath).asSlider() 
sliderUIControl.SetSliderValue(0.5) # Percentage slider 
# sliderUIControl.SetSliderValue(5) # Fixed grid slider 
``` 
# StackPanelUIControl 
class in mod.client.ui.controls.stackPanelUIControl 
Layout panel control class, inherited from BaseUIControl, contains text-related functional interfaces in addition to basic functional interfaces 
<span id="SetOrientation"></span> 
## SetOrientation 
- Description 
Set the arrangement direction of stackPanel 
- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| orientation | str | The arrangement direction of stackPanel, the value is limited to ["vertical", "horizontal"], indicating vertical direction and horizontal direction respectively | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# we want to set stackPanel1 orientation 
stackPanelPath = "/stackPanel1" 
stackPanel = uiNode.GetBaseUIControl(stackPanelPath).asStackPanel() 
orientation = "vertical" 
stackPanel.SetOrientation(orientation) 
``` 

<span id="GetOrientation"></span> 
## GetOrientation 

- Description 

Get the arrangement direction of stackPanel


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The arrangement direction of stackPanel, the value is limited to ["vertical", "horizontal"], representing the vertical direction and horizontal direction respectively | 

- Example 

```python 
# we want to get stackPanel1 orientation 
stackPanelPath = "/stackPanel1" 
stackPanel = uiNode.GetBaseUIControl(stackPanelPath).asStackPanel() 
stackPanel.GetOrientation() 
``` 

# SwitchToggleUIControl 

class in mod.client.ui.controls.switchToggleUIControl 

Switch control class, inherited from BaseUIControl, contains switch-related function interfaces in addition to basic function interfaces 

<span id="SetToggleState"></span> 
## SetToggleState 

- Description 

Set the value of the Toggle switch control 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| is_on | bool | Sets whether the Toggle switch control is on or off | 
| toggle_path | bool | The relative path of the actual toggle control. The switch control generated by the UI editor has the default value "/this_toggle" for this parameter | 

- Return value 

None 

- Example 

```python 
togglePath = "/toggle1"

switchToggleUIControl = uiNode.GetBaseUIControl(togglePath).asSwitchToggle() 
switchToggleUIControl.SetToggleState(True) 
``` 

# TextEditBoxUIControl 

class in mod.client.ui.controls.textEditBoxUIControl 

Text input box control class, inherited from BaseUIControl, contains text input box related function interfaces in addition to basic function interfaces 

<span id="GetEditText"></span> 
## GetEditText 

- Description 

Get the text information of the edit_box input box. If the acquisition fails, None will be returned 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Text information | 

- Notes 
- Failure to obtain is usually due to an error in filling in the path or the control is not of the edit_box type 

- Example 

```python 
# we want to get edit2 content 
editBoxPath = "/panel/edit2" 
textEditBoxUIControl = uiNode.GetBaseUIControl(editBoxPath).asTextEditBox() 
text = textEditBoxUIControl.GetEditText() 
``` 

<span id="SetEditText"></span> 
## SetEditText 

- Description 

Set the text information of the edit_box input box 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| text | str | Text content | 

- Return value 

None 

- Example 

```python 
# we want to clear edit2 content 
editBoxPath = "/panel/edit2" 
text = "" 
textEditBoxUIControl = uiNode.GetBaseUIControl(editBoxPath).asTextEditBox() 
textEditBoxUIControl.SetEditText(text) 
``` 

<span id="SetEditTextMaxLength"></span> 
## SetEditTextMaxLength 

- Description 

Set the maximum input length of the input box 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| maxLength | int | The maximum length that can be entered in the input box, the value is [0, +∞) | 

- Return value 

None 

- Example 

```python 
# we want to set text_edit_box max input length 10 
editTextPath = "/panel2/text_edit_box" 
textEditBoxUIControl = uiNode.GetBaseUIControl(editBoxPath).asTextEditBox() 
textEditBoxUIControl.SetEditTextMaxLength(10) 
``` 

