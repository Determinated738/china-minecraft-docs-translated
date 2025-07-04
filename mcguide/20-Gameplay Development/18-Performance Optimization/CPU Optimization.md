--- 
front: https://nie.res.netease.com/r/pic/20210728/2dc2a94f-71f6-4cc5-8700-3c3696f79a0c.jpg 
hard: Advanced 
time: 30 minutes 
--- 
# CPU optimization 

## Preface 

CPU is a representative of the computing power level of the device. The better the CPU performance, the more operations it can support in the same time. Whether it is the allocation and release of memory, the preparation of the rendering environment and the sending of instructions, etc., the CPU needs to participate. The optimization of the CPU can have a relatively large impact on the overall performance of the device. 

## Use of cache (memory for CPU) 

The repeated creation and destruction of objects will have a certain performance consumption. For data that needs to be used frequently, it is recommended to save it and use it directly from the memory next time. It is a common optimization method of exchanging space for time (memory for CPU), which has a good effect on reducing game lag. 

### Avoid using import in tick function 

The cost of importing modules is not small enough to be ignored. It is recommended to move the import to the top of the file. If this will cause a circular reference, you can cache the module as a member variable of the class 

- Wrong way to write: 

```python 
class DemoClientSystem(ClientSystem): 
def Update(self): 
# Import the module in the logic executed in each frame 
import mod.client.extraClientApi as clientApi 
clientApi.xxx 
``` 

- Correct way to write: 

```python 
# Import the module at the top of the file 
import mod.client.extraClientApi as clientApi 
class DemoClientSystem(ClientSystem): 
def Update(self): 
clientApi.xxx 
``` 

If two modules need to reference each other, then importing each other at the top of the file at the same time will cause a circular reference error. You can use the following method to handle it: 

```python 
class DemoClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
# Assume that the current module and another otherModule module need to reference each other 
import demoScripts.client.otherModule as otherModule 
self.otherModule = otherModule 


def Update(self): 
self.otherModule.xxx 
``` 

### Avoid initializing constants multiple times 

- Wrong way to write: 

Declare in a frequently called function, such as every Update 

```python 
class DemoClientSystem(ClientSystem): 
def Update(self): 
# Constants, created per frame, in practice there may be more data here 
bigDict = { 
(-1, -1): 1, 
(-1, 0): 2, 
(-1, 1): 3, 
(0, -1): 4, 
(0, 0): 5, 
(0, 1): 6, 
(1, -1): 7, 
(1, 0): 8, 
(1 1): 9, 
} 
# Read constants and do some logic 
do_something(bigDict) 
``` 

- Correct way to write: 

Constants with more data, especially those of List or Dict type, can be placed in the class's __init__ function 

```python 
class DemoClientSystem(ClientSystem): 
# Constructor 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
# Create during initialization 
self.bigDict = { 
(-1, -1): 1, 
(-1, 0): 2, 
(-1, 1): 3, 
(0, -1): 4, 
(0, 0): 5, 
(0, 1): 6, 
(1, -1): 7, 
(1, 0): 8, 
(1 1): 9, 
}


def Update(self): 
do_something(self.bigDict) 
``` 

### Cache intermediate data used multiple times 

Some methods return the same value when called multiple times. You can use temporary variables to cache them without repeated calls 

- Wrong way to write: 
```python 
class DemoServerSystem(ServerSystem): 
# Listening ServerItemUseOnEvent event callback 
def ServerItemUseOnEvent(self, args): 
# Set multiple blocks 
self.SetBlock(args['dimensionId'], (args['x']-1, args['y'], args['z']), 'minecraft:air') 
self.SetBlock(args['dimensionId'], (args['x']-1, args['y'], args['z']), 'minecraft:air') 
		self.SetBlock(args['dimensionId'], (args['x'], args['y'], args['z']), 'minecraft:air')
		self.SetBlock(args['dimensionId'], (args['x'], args['y'], args['z']-1), 'minecraft:air')
		self.SetBlock(args['dimensionId'], (args['x'], args['y'], args['z']+1), 'minecraft:air')

	def SetBlock(self, dimensionId, pos, blockName):
		serverApi.GetEngineCompFactory().CreateBlockInfo(levelId).SetBlockNew(pos, {'name': blockName}, 0, dimensionId)
```

- Correct way to write: 

```python 
# compFactory uses cache 
serverCompFactory = serverApi.GetEngineCompFactory() 
class DemoServerSystem(ServerSystem): 
# Listening ServerItemUseOnEvent event callback 
def ServerItemUseOnEvent(self, args): 
# Cache the values in the dictionary 
dimensionId = args['dimensionId'] 
x = args['x'] 
y = args['y'] 
z = args['z'] 
self.SetBlock(dimensionId, (x-1, y, z), 'minecraft:air') 
self.SetBlock(dimensionId, (x-1, y, z), 'minecraft:air') 
self.SetBlock(dimensionId, (x, y, z), 'minecraft:air') 
		self.SetBlock(dimensionId, (x, y, z-1), 'minecraft:air')
		self.SetBlock(dimensionId, (x, y, z+1), 'minecraft:air')

	def SetBlock(self, dimensionId, pos, blockName):
		serverCompFactory.CreateBlockInfo(levelId).SetBlockNew(pos, {'name': blockName}, 0, dimensionId)
```

### Use dict instead of multiple else if

When there are many branches in the conditional judgment, the performance of dict will be much higher than a series of else 

- Wrong writing: 

```python 
serverCompFactory = serverApi.GetEngineCompFactory() 
class DemoServerSystem(ServerSystem): 
def HandleBlocks(self, pos, dimensionId): 
# Get block information 
blockIdentifier = serverCompFactory.CreateBlockInfo(levelId).GetBlockNew(pos, dimensionId)[0] 
# Make different processing according to the block type 
if blockIdentifier == "minecraft:iron_ore": 
self.handleIronBlock() 
elif blockIdentifier == "minecraft:gold_ore": 
self.handleGoldBlock() 
elif blockIdentifier == "minecraft:diamond_ore": 
self.handleDiamondBlock() 
``` 

- Correct way to write:

```python
serverCompFactory = serverApi.GetEngineCompFactory()
class DemoServerSystem(ServerSystem):
	def __init__(self):
		# Register handler function
		self.blockHandlers = {
			"minecraft:iron_ore": self.handleIronBlock,
			"minecraft:gold_ore": self.handleGoldBlock,
			"minecraft:diamond_ore": self.handleDiamondBlock,
		}

	def HandleBlocks(self, data):
		blockIdentifier = serverCompFactory.CreateBlockInfo(levelId).GetBlockNew(pos, dimensionId)[0]
		# Select processing function from dict
		handler = self.blockHandlers.get(blockIdentifier)
		if handler:
			handler()
```

## Frame division (Real-time CPU replacement) 

Processing a large amount of logic at the same time can easily cause jamming. At this time, it is necessary to stagger the execution of the logic to multiple frames so that the workload of each frame is not too heavy. 

### Modify data in large quantities and process them in multiple frames 

Here is an example of blocks: 

- Wrong way of writing: 
(Processing all at the same time requires processing 100* 100 * 100, that is, one million blocks, which will inevitably jam)

```python 
# Modify a certain area 100 * 100 * 100 blocks to air 
def SetBlocksToAir(self, fromPos): 
blockcomp = serverApi.CreateComponent(id, "Minecraft", "blockInfo") 
for x in range(1, 100): 
for y in range(1, 100): 
for z in range(1, 100): 
blockcomp.SetBlockNew((fromPos[0] + x, fromPos[1] + y, fromPos[2] + z), {'name':'minecraft:air'}) 
``` 

- Correct way to write: 
(Only 5 blocks are processed separately per frame) 
```python 
# Modify a certain area 100 * 100 * 100 blocks to air 
def SetBlocksToAir(self, fromPos): 
# Command queue 
self.posList = [] 
self.posIndex = 0 
for x in range(1, 100): 
for y in range(1, 100): 
for z in range(1, 100): 
self.posList.append((fromPos[0] + x, fromPos[1] + y, fromPos[2] + z)) 
# Overridden function of the parent class directly executed by the engine. The engine will execute the Update callback, 30 frames per second 
def Update(self): 
if self.posList: 
posListLen = len(self.posList) 
blockcomp = serverApi.CreateComponent(id, "Minecraft", "blockInfo") 
#Process 5 per frame 
handleNum = 5 
while(handleNum > 0 and self.posIndex < posListLen): 
blockcomp.SetBlockNew(self.posList[self.posIndex], {'name':'minecraft:air'}) 
self.posIndex = self.posIndex + 1 
handleNum = handleNum - 1 
# All processing is completed 
if self.posIndex >= posListLen: 
self.posList = None 
``` 

### Non-important logic frame reduction processing 

Do not execute all logic updates every frame. Different logics are actually updated at intervals according to real-time requirements 

- Wrong writing method: 
(Execute all update logic every frame) 
```python 
def Update(self): 
self.do_something1()

self.do_something2() 
self.do_something3() 
``` 

- Correct way to write: 
(process only 5 per frame) 
```python 
class DemoClientSystem(ClientSystem): 
# Constructor 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
self.tick = 0 

def Update(self): 
self.tick = self.tick + 1 
# Important logic executed per frame 
self.do_something1() 

if self.tick % 5 == 0: 
# Minor logic executed at lower frame rate 
self.do_something2() 

if self.tick % 10 == 0: 
# More minor logic, executed at lower frame rate 
self.do_something3() 
``` 

### Use less polling logic 

Use events or some applicable interfaces instead of trying operations every frame. 

Imagine there is a requirement: I want to delete an entity, but the entity is not currently loaded 

- Wrong way to write: 

Try to delete the entity every frame until it succeeds 

- Recommended way to write: 

1. Listen to AddEntityServerEvent and delete it in the callback of the entity. 
2. If the entity is manually created, you can use the SetPersistence interface to set it to not save to disk, then you no longer need to deal with the situation where the entity is uninstalled and cannot be deleted.