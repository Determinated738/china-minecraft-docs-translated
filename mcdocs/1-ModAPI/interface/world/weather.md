--- 
sidebarDepth: 1 
--- 
# Weather 

## GetDimensionLocalWeatherInfo 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Get independent dimension weather information (must first use SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Independent dimension weather information (rain intensity, rain time, thunder intensity, thunder time, whether to open the weather cycle) | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.GetDimensionLocalWeatherInfo(0) 
``` 

## GetDimensionUseLocalWeather 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Get whether a dimension has its own weather rules 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| dimension | int | dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether independent weather rules are used | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.GetDimensionUseLocalWeather(0) 
``` 

## IsRaining 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Get whether it is raining 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it raining? | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.IsRaining() 
``` 

## IsThunder


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Get whether there is thunder 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether there is thunder | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.IsThunder() 
``` 

## SetDimensionLocalDoWeatherCycle 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Set whether to enable weather cycle for a dimension (must first use SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 
| value | bool | Whether to enable weather cycle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.SetDimensionLocalDoWeatherCycle(0, True) 
``` 

## SetDimensionLocalRain 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Set a dimension to rain (must first use the SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | dimension id | 
| rainLevel | float | rain intensity, range 0-1 | 
| rainTime | int | duration of rain, in frames, 20 frames per second. It will automatically switch to the opposite weather after the duration ends | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.SetDimensionLocalRain(0, 0.5, 180) 
``` 

## SetDimensionLocalThunder 

<span style="display:inline;color:#ff5555">Server</span> 


method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Set a dimension to have thunder (you must first use the SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| thunderLevel | float | Thunder intensity, range 0-1 | 
| thunderTime | int | Thunder duration, in frames, 20 frames per second. After the duration ends, it will automatically switch to the opposite weather | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.SetDimensionLocalThunder(0, 0.5, 180) 
``` 

## SetDimensionUseLocalWeather 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Set a dimension to have its own weather rules. After it is turned on, the dimension can have different weather and weather change rules from other dimensions. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| value | bool | Whether to turn on independent weather | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | success | 

- Notes 
- We have added the concept of "local weather" to the main world and custom dimensions. Before this, all dimensions shared a "global weather", that is, when setting weather or weather cycle rules, they would apply to all dimensions. 
Now, we can use local weather rules for a dimension and set its rain intensity, rain time, thunder intensity, thunder time, and whether to open the weather cycle (see [SetDimensionLocalRain](#setdimensionlocalrain), [SetDimensionLocalThunder](#setdimensionlocalthunder), [SetDimensionLocalDoWeatherCycle](#setdimensionlocaldoweathercycle)). 
In the following, we will refer to dimensions that use local weather rules as "local dimensions" and dimensions that use global weather as "global dimensions". By default, all dimensions are global dimensions. 
The original weather command, interface [SetRaining](#setraining) and [SetThunder](#setthunder) will not affect the local dimension. 
- When the local weather rule is enabled, the global weather intensity and time are inherited by default, and the local dimension weather cycle is enabled by default. 
- Weather rules are invalid for the original Nether and the End, and these two dimensions do not have a weather system. 
- It is recommended to call them uniformly when the game starts. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.SetDimensionUseLocalWeather(0, True) 
``` 

## SetRaining 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Set whether it rains 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| level | float | Rain intensity, ranging from 0-1 | 
| time | int | Duration of the weather, in frames, 20 frames per second. It will automatically switch to the opposite weather after the duration ends. Note that this parameter will only take effect after the weather change is turned on in the game settings. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId)

comp.SetRaining(0.5,1000) 
``` 

## SetThunder 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.weatherCompServer.WeatherComponentServer 

- Description 

Set whether to thunder 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| level | float | Thunder intensity, range is 0-1 | 
| time | int | Thunder duration, unit is frame, 20 frames per second. Note that this parameter will only take effect after the weather change is enabled in the game settings. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateWeather(levelId) 
comp.SetThunder(0.5,1000)set_lightning 
``` 

