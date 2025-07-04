--- 
sidebarDepth: 1 
--- 
# Game Settings 

# Index 

Pause Menu->Settings Page Related Interfaces 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetToggleOption](Game Settings.md#gettoggleoption) | <span style="display:inline;color:#7575f9">Client</span> | Interface to get the setting value of a switch | 
| [GetUIProfile](Game Settings.md#getuiprofile) | <span style="display:inline;color:#7575f9">Client</span> | Get "UI Profile" mode | 
| [HighlightBoxSelection](Game Settings.md#highlightboxselection) | <span style="display:inline;color:#7575f9">Client</span> | Highlight the block pointed by the current view center when the camera moves | 
| [SetSplitControlCanChange](Game Settings.md#setsplitcontrolcanchange) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to allow the use of the crosshair aiming button | 
| [SetToggleOption](Game Settings.md#settoggleoption) | <span style="display:inline;color:#7575f9">Client</span> | Interface for modifying switch settings | 
| [SetUIProfile](Game Settings.md#setuiprofile) | <span style="display:inline;color:#7575f9">Client</span> | Set the "UI Profile" mode | 

## GetToggleOption 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Interface for obtaining the setting value of a switch 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| optionId | str | [OptionId enumeration](../enumeration value/OptionId.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | -1: Type not supported; 0: Switch off; 1: Switch on; | 

- Notes 
- When INPUT_MODE is selected, the return value is [InputMode Enumeration](../enumeration/InputMode.md) 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(levelId)

print(comp.GetToggleOption(clientApi.GetMinecraftEnum().OptionId.HIDE_PAPERDOLL)) 
``` 

## GetUIProfile 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Get the "UI Profile" mode 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0 for classic mode, 1 for pocket mode | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(levelId) 
profile = comp.GetUIProfile() 
``` 

## HighlightBoxSelection 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Highlight the block pointed by the center of the current view when the camera moves 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHighlight | bool | Whether to highlight, True is highlighted, False is not highlighted, the default is not highlighted |


- Return value 

None 

- Notes 
- The function implementation above is actually a layer of code encapsulation of Settings->Video->Contour, but it will not affect the original contour setting value. You can use this interface to turn on and off the highlight effect when the contour selection is turned on. If the contour selection is turned off in the game, the block will only be highlighted. 
- The setting will be invalid after restart 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(levelId) 
#Set to highlight 
comp.HighlightBoxSelection(True) 
``` 

## SetSplitControlCanChange 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Set whether to allow the use of the crosshair aiming button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| canChange | bool | Allowed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(levelId) 
print(comp.SetSplitControlCanChange(True)) 
``` 




## SetToggleOption 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Interface for modifying switch type settings 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| optionId | str | [OptionId enumeration](../enumeration value/OptionId.md) | 
| isOn | bool | Whether the switch is turned on, True is on, False is off | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- INPUT_MODE is the controller mode, which does not support setting 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(levelId) 
#Set the hidden paper doll option to on 
print(comp.SetToggleOption(clientApi.GetMinecraftEnum().OptionId.HIDE_PAPERDOLL, True)) 
``` 

## SetUIProfile 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Set the "UI Profile" mode 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| profileType | int | 0 for classic mode, 1 for Pocket mode | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(levelId) 
#Set to Pocket mode 
print(comp.SetUIProfile(1)) 
``` 

