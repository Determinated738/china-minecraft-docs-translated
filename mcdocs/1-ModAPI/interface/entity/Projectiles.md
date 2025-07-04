--- 
sidebarDepth: 1 
--- 
# Projectile 

## GetSourceEntityId 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.bulletAttributesCompServer.BulletAttributesComponentServer 

- Description 

Get the projectile launcher entity id 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Projectile launcher entity id | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBulletAttributes(entityId)
comp.GetSourceEntityId()
```