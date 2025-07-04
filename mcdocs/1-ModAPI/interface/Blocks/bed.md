--- 
sidebarDepth: 1 
--- 
# Bed 

## GetBedColor 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the color of the bed (block) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | The position coordinates of the bed (the bed occupies two grids, any grid is fine) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | [ItemColor Enumeration](../../Enumeration Value/ItemColor.md) | 

- Notes 
- When the block at the input coordinate position is not a bed, -1 is returned 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) 
pos = (-1, 4, 34) 
color = comp.GetBedColor(pos) 
print "GetBedColor color={}".format(color) 
``` 

## SetBedColor 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 


Set the color of the bed (block) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | The location coordinates of the bed (the bed occupies two grids, any grid is fine) | 
| color | int | [ItemColor enumeration](../../enumeration value/ItemColor.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) 
pos = (-1, 4, 34)
suc = comp.SetBedColor(pos, serverApi.GetMinecraftEnum().ItemColor.Blue)
print "SetBedColor suc={}".format(suc)
```