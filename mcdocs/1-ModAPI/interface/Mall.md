--- 
sidebarDepth: 1 
--- 
# Mall 

# Index 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CloseShopWindow](Mall.md#closeshopwindow) | <span style="display:inline;color:#7575f9">Client</span> | Close NetEase Mall window | 
| [HideShopGate](Mall.md#hideshopgate) | <span style="display:inline;color:#7575f9">Client</span> | Hide NetEase Mall entrance | 
| [OpenItemDetailWindow](Mall.md#openitemdetailwindow) | <span style="display:inline;color:#7575f9">Client</span> | Open the details interface of a specific product | 
| [OpenShopWindow](商城.md#openshopwindow) | <span style="display:inline;color:#7575f9">Client</span> | Open NetEase Mall window | 
| [ShowShopGate](商城.md#showshopgate) | <span style="display:inline;color:#7575f9">Client</span> | Show NetEase Mall entrance | 

## CloseShopWindow 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.neteaseShopCompClient.NeteaseShopCompClient 

- Description 

Close the NetEase Mall window 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateNeteaseShop(levelId)
comp.CloseShopWindow()
```



## HideShopGate

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.neteaseShopCompClient.NeteaseShopCompClient


- Description 

Hide the entrance to NetEase Mall 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateNeteaseShop(levelId) 
comp.HideShopGate() 
``` 

## OpenItemDetailWindow 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.neteaseShopCompClient.NeteaseShopCompClient 

- Description 

Open the details interface of a specific product 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| categoryName | str | Product category name | 
| itemName | str | Product name | 

- Return value 

None 

- Example 

```python 
import client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateNeteaseShop(levelId) 
comp.OpenItemDetailWindow("Product", "Test Product 1")

``` 

## OpenShopWindow 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.neteaseShopCompClient.NeteaseShopCompClient 

- Description 

Open the Netease Mall window 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateNeteaseShop(levelId) 
comp.OpenShopWindow() 
``` 

## ShowShopGate 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.neteaseShopCompClient.NeteaseShopCompClient 

- Description 

Display the entrance to NetEase Mall 

- Parameters 

None 

- Return value 

None 


- Example

```python
import client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateNeteaseShop(levelId)
comp.ShowShopGate()
```