--- 
sidebarDepth: 1 
--- 
# Native UI 

# Index 

Including the original HUD interface related interfaces 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetScreenSize](Native UI.md#getscreensize) | <span style="display:inline;color:#7575f9">Client</span> | Get game resolution | 
| [GetScreenViewInfo](Native UI.md#getscreenviewinfo) | <span style="display:inline;color:#7575f9">Client</span> | Get game perspective information. First, get the UI magnification under the current resolution. The calculation method can refer to <a href="../../../mcguide/18-界面与互動/1-界面编辑使用说明.html#《我的世界》界面修改方法">《我的世界》界面修改方法</a>. Then the calculation method of the width of the current game perspective is: if the width of the current resolution can be divided by the magnification, it is equal to the current resolution. If not, it is equal to the current resolution plus the magnification and then subtracting the result of the current resolution modulo the magnification. The calculation method of the height of the current game perspective is similar. For example: For a mobile phone with a resolution of 1792, 828, the canvas is three times the resolution, so x = 1792 + 3 - 1 = 1794; y = 828, the result returned by this interface is (1794.0, 828.0, 0.0, 0.0) | 
| [HideAirSupplyGUI](Native UI.md#hideairsupplygui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the player oxygen value interface | 
| [HideArmorGui](Native UI.md#hidearmorgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the armor value display of the hud interface | 
| [HideChangePersonGui](Native UI.md#hidechangepersongui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the button for switching names. Clicking the corresponding position after hiding will not respond | 
| [HideChatGUI](Native UI.md#hidechatgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the chat button native UI. | 
| [HideEmoteGUI](Native UI.md#hideemotegui) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the emoticon function. By default, it is disabled on the PC and enabled on the mobile phone. This interface can only be used on the mobile phone. | 
| [HideExpGui](Native UI.md#hideexpgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the experience bar display in non-creator mode | 
| [HideFoldGUI](Native UI.md#hidefoldgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the native UI of the drop-down button. | 
| [HideHealthGui](Native UI.md#hidehealthgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the health display of the hud interface | 
| [HideHorseHealthGui](Native UI.md#hidehorsehealthgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the health display of the mount on the hud interface | 
| [HideHudGUI](Native UI.md#hidehudgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the game native UI of the HUD game interface. The effect is the same as the original F1 button, only the display is hidden, but clicking on the jump button and other positions will still respond | 
| [HideHungerGui](Native UI.md#hidehungergui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the hunger value display of the hud interface | 
| [HideInteractGui](Native UI.md#hideinteractgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the interactive button. Clicking the corresponding position after hiding will not respond | 
| [HideJumpGui](Native UI.md#hidejumpgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the jump button in the lower right corner of the game. After hiding, clicking the corresponding position will not respond | 
| [HideMoveGui](Native UI.md#hidemovegui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the move button in the lower left corner of the game. After hiding, clicking the corresponding position will not respond | 
| [HideNeteaseStoreGui](Native UI.md#hideneteasestoregui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the NetEase Store button in the game. After hiding, clicking the corresponding position will not respond | 
| [HidePauseGUI](Native UI.md#hidepausegui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the pause button native UI. | 
| [HideReportGUI](Native UI.md#hidereportgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the native UI of the report button. | 
| [HideSlotBarGui](Native UI.md#hideslotbargui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the inventory interface at the bottom center of the game | 
| [HideSneakGui](Native UI.md#hidesneakgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the sneak button at the center of the lower left arrow key in the game. After hiding, clicking the corresponding position will not respond | 
| [HideSwimGui](Native UI.md#hideswimgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the snorkeling button in the game. After hiding, clicking the corresponding position will not respond | 
| [HideVoiceGUI](Native UI.md#hidevoicegui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the voice button native UI. | 
| [HideWalkGui](Native UI.md#hidewalkgui) | <span style="display:inline;color:#7575f9">Client</span> | Hide the movement type button in the upper right corner of the game. After hiding, clicking the corresponding position will not respond | 
| [OpenChatGui](Native UI.md#openchatgui) | <span style="display:inline;color:#7575f9">Client</span> | Open the original chat bar | 
| [OpenEmoteGui](Native UI.md#openemotegui) | <span style="display:inline;color:#7575f9">Client</span> | Open the emoticon interface | 
| [OpenFoldGui](Native UI.md#openfoldgui) | <span style="display:inline;color:#7575f9">Client</span> | Open the original drop-down interface | 
| [OpenInventoryGui](Native UI.md#openinventorygui) | <span style="display:inline;color:#7575f9">Client</span> | Open the original backpack interface and support selecting a certain page (support custom page name) | 
| [OpenNeteaseStoreGui](Native UI.md#openneteasestoregui) | <span style="display:inline;color:#7575f9">Client</span> | Open the NetEase store purchase interface in the game | 
| [OpenPauseGui](Native UI.md#openpausegui) | <span style="display:inline;color:#7575f9">Client</span> | Open the original pause interface | 
| [OpenReportGui](Native UI.md#openreportgui) | <span style="display:inline;color:#7575f9">Client</span> | Open the original report interface | 
| [OpenVoiceGui](Native UI.md#openvoicegui) | <span style="display:inline;color:#7575f9">Client</span> | Open the original voice interface | 
| [PlayHudHeartBlinkAnim](Native UI.md#playhudheartblinkanim) | <span style="display:inline;color:#7575f9">Client</span> | Play the original version of the blood volume change animation when injured | 
| [SetCrossHair](Native UI.md#setcrosshair) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to use "crosshair aiming", that is, Settings->Touch Screen->Crosshair aiming | 
| [SetEmoteSwitch](Native UI.md#setemoteswitch) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the expression function. By default, it is disabled on PC and enabled on mobile phones. This interface can only be used on mobile phones. Call the setting before the native UI is initialized. | 
| [SetHudChatStackPosition](Native UI.md#sethudchatstackposition) | <span style="display:inline;color:#7575f9">Client</span> | Set the position of the small chat window in the upper left corner of the HUD interface | 
| [SetHudChatStackVisible](Native UI.md#sethudchatstackvisible) | <span style="display:inline;color:#7575f9">Client</span> | Set the visibility of the small chat window in the upper left corner of the HUD interface |

| [SetResponse](Native UI.md#setresponse) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the native UI responds | 

## GetScreenSize 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Get the game resolution 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Width and height (pixels) | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
width, height = comp.GetScreenSize() 
``` 

## GetScreenViewInfo 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Get the game perspective information. First, get the UI magnification at the current resolution. The calculation method can refer to <a href="../../../mcguide/18-Interface and Interaction/1-Interface Editor Instructions.html#《My World》Interface Adaptation Method">《My World》Interface Adaptation Method</a>. The width of the current game perspective is calculated as follows: if the width of the current resolution can be divided by the magnification factor, it is equal to the current resolution; if not, it is equal to the current resolution plus the magnification factor minus the modulo of the current resolution and the magnification factor. The height of the current game perspective is calculated similarly. Example: For a mobile phone with a resolution of 1792,828, the canvas is 3 times the resolution, so x = 1792 + 3 - 1 = 1794; y = 828, the result returned by the interface is (1794.0, 828.0, 0.0, 0.0) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| tuple(float,float,float,float) | width, height, x offset, y offset | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
width, height, offsetX, offsetY= comp.GetScreenViewInfo() 
``` 

## HideAirSupplyGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the player oxygen value interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True for hiding, False for displaying | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideAirSupplyGUI(True) 
``` 

## HideArmorGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description


Hide the armor value display of the hud interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideArmorGui(True) 
``` 

## HideChangePersonGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the button for switching names. Clicking the corresponding position after hiding will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideChangePersonGui(True) 
```



## HideChatGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the chat button native UI. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | True to hide the native HUD, False to restore the display | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideChatGUI(True) 
``` 

## HideEmoteGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Set whether to enable the emoticon function. By default, it is disabled on the PC side and enabled on the mobile side. This interface can only be used on the mobile side. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | True means hiding the native HUD, False means restoring the display | 

- Return value 


None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideEmoteGUI(True) 
``` 

## HideExpGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the experience bar display in non-creator mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideExpGui(True) 
``` 

## HideFoldGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the drop-down button native UI. 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | True to hide the native HUD, False to restore the display | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideFoldGUI(True) 
``` 

## HideHealthGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the health display of the hud interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True for hiding, False for showing | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideHealthGui(True) 
``` 



## HideHorseHealthGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the health display of the mount in the hud interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideHorseHealthGui(True) 
``` 

## HideHudGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the game native UI of the HUD game interface. The effect is the same as the original F1 button, only hiding the display, but clicking the jump key and other positions will still respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | True to hide the native HUD, False to restore the display | 

- Return value 

None


- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideHudGUI(True) 
``` 

## HideHungerGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the hunger value display of the hud interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideHungerGui(True) 
``` 

## HideInteractGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the interactive button. Clicking the corresponding position will not respond after hiding.


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideInteractGui(True) 
``` 

## HideJumpGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the jump button in the lower right corner of the game. After hiding, clicking the corresponding position will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether hidden, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideJumpGui(True) 
``` 

## HideMoveGui


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the move button in the lower left corner of the game. After hiding, clicking the corresponding position will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideMoveGui(True) 
``` 

## HideNeteaseStoreGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the NetEase Store button in the game. After hiding, clicking the corresponding position will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether hidden, True is hidden, False is displayed | 

- Return value 

None 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideNeteaseStoreGui(True) 
``` 

## HidePauseGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the pause button native UI. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | True to hide the native HUD, False to restore the display | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HidePauseGUI(True) 
``` 

## HideReportGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the native UI of the report button. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| isHide | bool | True to hide the native HUD, False to restore display | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideReportGUI(True) 
``` 

## HideSlotBarGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the inventory interface in the middle of the bottom of the game 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True to hide, False to show | 

- Return value 

None 

- Notes 
- Limited by the MC main interface structure control, it is not possible to hide the slotbar while retaining the experience bar 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideSlotBarGui(True) 
``` 

## HideSneakGui 

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.extraClientApi 

- Description 

Hides the sneak button in the center of the lower left directional pad in the game. After hiding, clicking the corresponding position will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideSneakGui(True) 
``` 

## HideSwimGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the snorkeling button in the game. After hiding, clicking the corresponding position will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether hidden, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi

clientApi.HideSwimGui(True) 
``` 

## HideVoiceGUI 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide the native UI of the voice button. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | True to hide the native HUD, False to restore the display | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideVoiceGUI(True) 
``` 

## HideWalkGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hides the movement type button in the upper right corner of the game. After hiding, clicking the corresponding position will not respond 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 


- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideWalkGui(True) 
``` 

## OpenChatGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the original chat bar 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
#Please do not execute this interface in the callback function that listens to the PlayerChatButtonClickClientEvent event, which will cause the chat interface to fail to close 
clientApi.OpenChatGui() 
``` 

## OpenEmoteGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the emoticon interface


- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenEmoteGui() 
``` 

## OpenFoldGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the original drop-down interface 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenFoldGui() 
``` 

## OpenInventoryGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi


- Description 

Open the original backpack interface and support selecting a certain page (support custom page name) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| categoryName | str | Page name ([Original page name enumeration] (../enumeration value/InventoryType.md)) | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenInventoryGui(clientApi.GetMinecraftEnum().InventoryType.NATURE) 
``` 

## OpenNeteaseStoreGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the NetEase store in the game to purchase goods interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| categoryName | str | Product category name | 
| itemName | str | Product name | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenNeteaseStoreGui("Goods", "Test Goods 1")

``` 

## OpenPauseGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the original pause interface 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenPauseGui() 
``` 

## OpenReportGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the original report interface 

- Parameters 

None 

- Return value 

None 

- Example


```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenReportGui() 
``` 

## OpenVoiceGui 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Open the original voice interface 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenVoiceGui() 
``` 

## PlayHudHeartBlinkAnim 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Play the original version of the blood volume change animation when injured 

- Parameters 

None 

- Return value


    None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.PlayHudHeartBlinkAnim() 
``` 

## SetCrossHair 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Set whether to use "crosshair aiming", that is, Settings->Touchscreen->Crosshair aiming 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| visible | bool | True to turn on "crosshair aiming", False to turn off | 

- Return value 

None 

- Example 

```python 
# we want to hide cross hair 
import mod.client.extraClientApi as clientApi
clientApi.SetCrossHair(False)
```



## SetEmoteSwitch

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.gameCompClient.GameComponentClient

- describe


Set whether to enable the emoticon function. By default, it is disabled on PC and enabled on mobile phones. This interface can only be used on mobile phones. Call the setting before the native UI is initialized. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| flag | bool | Whether to enable emoticons | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns true if the setting is successful, and false if the setting fails | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
res = comp.SetEmoteSwitch(False) 
``` 

## SetHudChatStackPosition 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Set the position of the small chat window in the upper left corner of the HUD interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float) | The target coordinates of the interface. The first item is the horizontal axis and the second item is the vertical axis. The (0,0) point is in the upper left corner of the HUD interface, below the player image | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.SetHudChatStackPosition((100, 0)) 
```



## SetHudChatStackVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Set the visibility of the small chat window in the upper left corner of the HUD interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| visible | bool | Visible | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.SetHudChatStackVisible(True) 
``` 

## SetResponse 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Set whether the native UI responds 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| response | bool | Whether to block the lower layer from knocking blocks/attacking entities when clicking the UI | 

- Return value 


None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.SetResponse(False) 
``` 

