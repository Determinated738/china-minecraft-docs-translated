--- 
sidebarDepth: 1 
--- 
# Entity Type 

## GetEngineType 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.engineTypeCompServer.EngineTypeComponentServer 

- Description 

Get the entity type, mainly used to determine whether the entity belongs to a certain type of creature. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | See [EntityType enumeration](../../enumeration value/EntityType.md) for details | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
from mod_log import logger as logger 
comp = serverApi.GetEngineCompFactory().CreateEngineType(entityId) 
entityType = comp.GetEngineType() 
EntityTypeEnum = serverApi.GetMinecraftEnum().EntityType 
# Determine whether it is a creature (Mob) 
if entityType & EntityTypeEnum.Mob == EntityTypeEnum.Mob: 
logger.info("{} is Mob".format(comp.GetEngineTypeStr())) 
# Determine whether it is a projectile (Projectile) 
if entityType & EntityTypeEnum.Projectile == EntityTypeEnum.Projectile: 
logger.info("{} is Projectile".format(comp.GetEngineTypeStr())) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.engineTypeCompClient.EngineTypeComponentClient


- Description 

Get the entity type, mainly used to determine whether the entity belongs to a certain type of organism. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | See [EntityType enumeration](../../enumeration value/EntityType.md) for details | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
from mod_log import logger as logger 
comp = clientApi.GetEngineCompFactory().CreateEngineType(entityId) 
entityType = comp.GetEngineType() 
EntityTypeEnum = clientApi.GetMinecraftEnum().EntityType 
# Determine whether it is a creature (Mob) 
if entityType & EntityTypeEnum.Mob == EntityTypeEnum.Mob: 
logger.info("{} is Mob".format(comp.GetEngineTypeStr())) 
# Determine whether it is a projectile (Projectile) 
if entityType & EntityTypeEnum.Projectile == EntityTypeEnum.Projectile: 
logger.info("{} is Projectile".format(comp.GetEngineTypeStr())) 
``` 

## GetEngineTypeStr 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.engineTypeCompServer.EngineTypeComponentServer 

- Description 

Get the type name of the entity 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity type name, such as minecraft:husk | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateEngineType(entityId) 
comp.GetEngineTypeStr() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.engineTypeCompClient.EngineTypeComponentClient 

- Description 

Get the type name of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity type name, such as minecraft:husk | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateEngineType(entityId) 
strType = comp.GetEngineTypeStr() 
``` 

