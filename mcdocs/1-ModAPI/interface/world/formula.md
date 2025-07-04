--- 
sidebarDepth: 1 
--- 
# Recipes 

## AddBrewingRecipes 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.recipeCompServer.RecipeCompServer 

- Description 

Interface for adding brewing stand recipes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| brewType | str | recipe_brewing_mix or recipe_brewing_container, recipe_brewing_mix represents mixed brewing recipes, recipe_brewing_container represents container-changing brewing recipes | 
| inputName | str | Items accepted by the recipe | 
| reagentName | str | Additional items required for brewing | 
| outputName | str | The item output by this recipe | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The output item cannot be stacked with the original item 
- For an existing recipe, it will return False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRecipe(serverApi.GetLevelId()) 
print(comp.AddBrewingRecipes("recipe_brewing_container", "minecraft:potion", "minecraft:gunpowder", "minecraft:splash_potion")) 
``` 

## GetRecipeResult 

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.component.recipeCompServer.RecipeCompServer

- Description 

Get recipe results based on recipe id. Only supports synthesis recipes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recipeId | str | Recipe id, corresponding to the identifier field in the recipe json file | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | See the notes for the resultDict dictionary of the list elements | 

- Notes 
- The resultDict dictionary content is as follows 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| itemName | str | Item name id | 
|auxValue| int | Item additional value | 
|num| int | Item number | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRecipe(serverApi.GetLevelId()) 
comp.GetRecipeResult(recipe1) 
comp.GetRecipeResult(recipe2) 
``` 

## GetRecipesByInput 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.recipeCompServer.RecipeCompServer 

- Description 

Query recipes by inputting items 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| inputIdentifier | str | Input item identifier | 
| tag | str | Corresponding value in the tags field in the recipe json | 
| aux | int | Output item additional value, defaults to 0 if no parameter is passed | 
| maxResultNum | int | Maximum number of output items. If it is greater than or equal to 0, and the result exceeds maxResultNum, only maxResultNum items will be returned. Default is -1, indicating that all are returned | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | Returns a list of recipes that meet the conditions | 

- Notes 
- When obtaining a furnace recipe, if the number of output items is 1, the output uses a string to represent the item identifier and additional value; if the number of output items is greater than 1, the output is a dict 
- When obtaining a brewing stand recipe, the tag label and aux value are not matched, and the identifier of the potion needs to be entered in full, for example: minecraft:potion_type:long_turtle_master, otherwise the correct recipe cannot be obtained. 
- Need to traverse more data, frequent calls are not recommended 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRecipe(serverApi.GetLevelId()) 
print(comp.GetRecipesByInput("minecraft:log", "crafting_table", 0, -1)) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.recipeCompClient.RecipeCompClient 

- Description 

Query recipes by inputting items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| inputIdentifier | str | Identifier of input item | 
| tag | str | The value in the tags field in the corresponding recipe json | 
| aux | int | The additional value of the output item. If no parameter is passed, the default value is 0 | 
| maxResultNum | int | The maximum number of output items. If it is greater than or equal to 0, and the result exceeds maxResultNum, only maxResultNum items will be returned. The default value is -1, which means returning all | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| list(dict) | Returns a list of recipes that meet the conditions | 

- Notes 
- When getting a furnace recipe, if the number of output items is 1, the output uses a string to represent the item identifier and additional value; if the number of output items is greater than 1, the output is a dict 
- When getting a brewing stand recipe, the tag label and aux value are not matched, and the identifier of the potion needs to be entered in full, for example: minecraft:potion_type:long_turtle_master, otherwise the correct recipe cannot be obtained. 
- Need to traverse more data, frequent calls are not recommended 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateRecipe(clientApi.GetLevelId()) 
print(comp.GetRecipesByInput("minecraft:log", "crafting_table", 0, -1)) 
``` 

## GetRecipesByResult 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.recipeCompServer.RecipeCompServer 

- Description 

Query the input materials required for the recipe through the output item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| resultIdentifier | str | Output item identifier | 
| tag | str | Corresponding value in the tags field in the recipe json | 
| aux | int | Additional value of the output item, defaults to 0 if no parameter is passed | 
| maxResultNum | int | Maximum number of output items. If it is greater than or equal to 0, and the result exceeds maxResultNum, only maxResultNum items will be returned. Default is -1, indicating to return all | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | Returns a list of recipes that meet the conditions | 

- Notes 
- When getting the furnace recipe, if the number of output items is 1, the output uses a string to represent the item identifier and additional value; if the number of output items is greater than 1, the output is a dict 
- When getting the brewing stand recipe, the tag label and aux value are not matched. The identifier of the potion needs to be entered in full, for example: minecraft:potion_type:long_turtle_master, otherwise the correct recipe cannot be obtained. 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRecipe(serverApi.GetLevelId()) 
print(comp.GetRecipesByResult("minecraft:boat", "crafting_table", 4, -1)) 
``` 

### Client Interface 

<span id="c0"></span> 
method in mod.client.component.recipeCompClient.RecipeCompClient 

- Description 

Query the input materials required for a recipe through the output items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| resultIdentifier | str | Output item identifier | 
| tag | str | Corresponding to the value in the tags field in the recipe json | 
| aux | int | Output item's additional value, defaults to 0 if no parameter is passed | 
| maxResultNum | int | Maximum number of output items, if greater than or equal to 0, and the result exceeds maxResultNum, only maxResultNum items are returned. Default is -1, indicating that all items are returned | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | Returns a list of recipes that meet the conditions | 

- Notes 
- When getting a furnace recipe, if the number of output items is 1, output uses a string to represent the item identifier and additional value; if the number of output items is greater than 1, output is a dict 
- When getting a brewing stand recipe, the tag tag and aux value are not matched, and the potion identifier needs to be entered in full, for example: minecraft:potion_type:long_turtle_master, otherwise the correct recipe cannot be obtained. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateRecipe(clientApi.GetLevelId())
print(comp.GetRecipesByResult("minecraft:boat", "crafting_table", 4, -1))
```