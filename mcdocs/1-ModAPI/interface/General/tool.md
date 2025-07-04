--- 
sidebarDepth: 1 
--- 
# Tools 

## AddRepeatedTimer 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Add a server-triggered timer for repeated execution 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | function | Timer trigger function | 
| *args | any | Variable length parameter, can be left blank | 
| **kwargs | any | Dictionary variable length parameter, can be left blank | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CallLater | Returns the triggered timer instance | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddRepeatedTimer(3.0,func,args,kwargs) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 


Add a client-triggered timer and execute it repeatedly 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | function | Timer trigger function | 
| *args | any | Variable length parameter, optional | 
| **kwargs | any | Dictionary variable length parameter, optional | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CallLater | Return the triggered timer instance | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddRepeatedTimer(3.0,func,args,kwargs) 
``` 

## AddTimer 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Add a server-triggered timer, non-repeating 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | function | Timer trigger function | 
| *args | any | Variable length parameter, can be left blank | 
| **kwargs | any | Dictionary variable length parameter, can be left blank | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CallLater | Returns a single-trigger timer instance | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddTimer(3.0,func,args,kwargs) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Add a client-triggered timer, non-repeating 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | function | Timer trigger function | 
| *args | any | Variable length parameter, optional | 
| **kwargs | any | Dictionary variable length parameter, optional | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CallLater | Returns a single-trigger timer instance | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.AddTimer(3.0,func,args,kwargs) 
``` 

## CancelTimer


<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Cancel the timer 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| timer | CallLater | Timer instance returned by AddTimer and AddRepeatedTimer | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.CancelTimer(timer) 
``` 
### Client interface 
<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Cancel the timer 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| timer | CallLater | Timer instance returned by AddOnceTimer and AddRepeatedTimer | 

- Return value 

None


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.CancelTimer(timer) 
``` 

## CheckNameValid 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Check if the nickname is legal, i.e. does not contain sensitive words 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | nickname | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Nickname is legal False: Nickname is illegal | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
isValid = comp.CheckNameValid("Steve") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient


- Description 

Check if the nickname is legal, i.e. does not contain sensitive words 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Nickname | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Nickname is legal False: Nickname is illegal | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
isValid = comp.CheckNameValid("Steve") 
``` 

## CheckWordsValid 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Check whether the statement is legal, that is, it does not contain sensitive words 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| words | str | Statement | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | True: the statement is legal<br>False: the statement is illegal | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
isValid = comp.CheckWordsValid("creeper? Aww man") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Check whether the statement is legal, that is, it does not contain sensitive words 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| words | str | Statement | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: The statement is legal<br>False: The statement is illegal | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
isValid = comp.CheckWordsValid("creeper? Aww man") 
``` 

## GetChinese 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span>

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the Chinese corresponding to langStr. Please refer to \handheld\localization\handheld\data\resource_packs\vanilla\texts\zh_CN.lang in the PC development package 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| langStr | str | The passed langStr | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The Chinese corresponding to langStr. If the corresponding Chinese is not found, langStr itself will be returned | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
# Get the Chinese corresponding to "entity.wolf.name" ("狼") 
Chinese = comp.GetChinese("entity.wolf.name") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Get the Chinese corresponding to langStr, refer to \handheld\localization\handheld\data\resource_packs\vanilla\texts\zh_CN.lang in the PC development kit 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| langStr | str | Incoming langStr | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The Chinese character corresponding to langStr. If the corresponding Chinese character cannot be found, langStr itself will be returned | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
# Get the Chinese corresponding to "entity.wolf.name" ("狼") 
Chinese = comp.GetChinese("entity.wolf.name") 
``` 

## GetFps 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Get fps 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Current fps value | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
fps = comp.GetFps() 
``` 

## GetMinecraftEnum 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 


- Description 

Used to get the enumeration value in the [enumeration value document](../../enumeration value/index.md) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| minecraftEnum | Enumeration collection class | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
# Use enumeration values as parameters of other interfaces 
comp.SetPlayerGameType(serverApi.GetMinecraftEnum().GameType.Survival) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Used to get the enumeration value in the [enumeration value document](../../enumeration value/index.md) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| minecraftEnum | Enumeration collection class | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Compare enumeration values with event parameters 
class BattleUI(ScreenNode):

def OnButtonTouch(self, args): 
touchEventEnum = clientApi.GetMinecraftEnum().TouchEvent 
if touchEvent == touchEventEnum.TouchUp: 
pass 

def Create(self): 
self.AddTouchEventHandler("/panel/test_btn", self.OnButtonTouch, {"isSwallow":True}) 
``` 

## GetModConfigJson 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Returns the contents of the json-formatted configuration file at the specified path in the form of a dictionary. The file must be placed in the /modconfigs directory of the resource pack 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | json file of the specified path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Dictionary of configuration content. An empty dictionary is returned when reading the file fails | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
data = clientApi.GetModConfigJson("modconfigs/monster.json") 
``` 

## StartCoroutine 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi


- Description 

Enable server-side coroutines to implement segmented function execution, which can be used to alleviate game lag caused by complex logic calculations 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| iterOrFunc | generator or callable([],generator) | Pass in a yield function or a generator. If a generator is passed in, it will start from the interrupt position of the generator. If a function is passed in, it will start from the beginning. | 
| callback | function | The callback function after the coroutine is executed. The default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| generator | Function generator | 

- Example 

```python 
#Execute coroutine through generator 
import server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(serverApi.GetLevelId()) 

def callback(): 
print "callback" 

def coroutineTest(): 
for i in xrange(1000): 
print i 
yield 

generator = serverApi.StartCoroutine(coroutineTest, callback) 
#Stop the coroutine after 1 second 
comp.AddTimer(1.0, serverApi.StopCoroutine, generator) 
#After 5 seconds, pass in the generator returned by StartCoroutine, and the function will continue to execute from the stop position 
comp.AddTimer(5.0, serverApi.StartCoroutine, generator, callback) 

#---------------------------------------------------------------- 

#Execute the coroutine through a function 
import server.extraServerApi as serverApi 
def callback(): 
print "callback" 

def coroutineTest(): 
for i in xrange(1000): 
print i 
yield

# Pass in a function, and the function will be executed from the beginning 
serverApi.StartCoroutine(coroutineTest, callback) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Start the client coroutine and implement segmented function execution, which can be used to alleviate the problem of game lag caused by complex logic calculations 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| iterOrFunc | generator or callable([],generator) | Pass in a function with yield or a generator. If a generator is passed in, it will start from the interrupt position of the generator. If a function is passed in, it will start from the beginning. | 
| callback | function | The callback function after the coroutine is executed. The default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| generator | Function generator | 

- Example 

```python 
#Execute coroutine through generator 
import client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(clientApi.GetLevelId()) 

def callback(): 
print "callback" 

def coroutineTest(): 
for i in xrange(1000): 
print i 
yield 

generator = clientApi.StartCoroutine(coroutineTest, callback) 
#Stop the coroutine after 1 second of execution 
comp.AddTimer(1.0, clientApi.StopCoroutine, generator) 
#After 5 seconds of execution, pass in the generator returned by StartCoroutine, and the function will continue to execute from the stop position 
comp.AddTimer(5.0, clientApi.StartCoroutine, generator, callback) 

#----------------------------------------------------------------


#Execute coroutines through functions 
import client.extraClientApi as clientApi 
def callback(): 
print "callback" 

def coroutineTest(): 
for i in xrange(1000): 
print i 
yield 
#Pass in a function, and the function will start from the beginning 
clientApi.StartCoroutine(coroutineTest, callback) 
``` 

## StopCoroutine 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Stop coroutine 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| iter | generator | The generator object to be stopped, the return value of StartCoroutine | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
serverApi.StopCoroutine(generator) 
``` 



### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Stop client coroutine 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| iter | generator | Generator object to be stopped, return value of StartCoroutine | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.StopCoroutine(generator) 
``` 

