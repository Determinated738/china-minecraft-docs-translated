--- 
front: https://nie.res.netease.com/r/pic/20210730/ee109f39-8987-46e0-9fe7-40ebb23060fa.png 
hard: Advanced 
time: 30 minutes 
--- 
# Customize NPC chat dialogue using MODSDK 

Novice guidance is a very critical "level" in the game. Whether the player can get started smoothly depends to the greatest extent on the novice guidance, so "Seaside Island" also needs to make a simple guidance level; we set up a family NPC on the island of birth, we can talk to it and complete the tasks he specifies: 

Get the id of the interactive NPC in advance as a condition and listen to the **PlayerAttackEntityEvent** event 

```python 
leveldatacomp = serverApi.GetEngineCompFactory().CreateExtraData(serverApi.GetLevelId()) 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
# Listen for PlayerAttackEntityEvent events 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), "PlayerAttackEntityEvent", 
self, self.PlayerAttack) 
# NPCid obtained in advance 
self.guide_id = "-481036336358" 
# Create a variable to control the dialogue stage 
self.guide_dialogue = {} 

# Event trigger function 
def PlayerAttack(self, args): 
# Player id obtained by the event 
self.playername = args["playerId"] 
# Create an interface for commands, blocks, and items 
commandcomp = serverApi.GetEngineCompFactory().CreateCommand(serverApi.GetLevelId()) 
blockcomp = serverApi.GetEngineCompFactory().CreateBlockInfo(serverApi.GetLevelId()) 
itemcomp = serverApi.GetEngineCompFactory().CreateItem(self.playername) 
# The creature id obtained by the event 
entityid = args["victimId"] 
# If the creature id obtained by the event is the same as the NPCid obtained in advance 
if entityid == self.guide_id: 
# Get player_guide data 
guide_data = leveldatacomp.GetExtraData('player_guide') 
# If there is no such data, set one 
if not guide_data: 
leveldatacomp.SetExtraData('player_guide', self.guide_dialogue) 
else: 
# If there is, pass guide_data to self.guide_dialogue 
self.guide_dialogue = guide_data 
# If self.guide_dialogue={} (it means this is the first time you click on this NPC) 
if self.guide_dialogue == {}: 
# Use the command interface to generate dialogue and sound effects 
commandcomp.SetCommand( 
"execute @a ~ ~ ~ tellraw @a {\"rawtext\":[{\"text\":\" §6§l【Family】 §r§fTata Village is a village located deep in the mountains, 'becoming a more independent person' is the long-standing heritage of the village. §6[1/6]\"}]}")

commandcomp.SetCommand("execute @a ~ ~ ~ /playsound random.orb @a ~ ~ ~ 3 1 3") 
# Give the variable a new parameter to control the next dialogue stage 
self.guide_dialogue["dialogue"] = 0 
# Store the new player_guide 
leveldatacomp.SetExtraData('player_guide', self.guide_dialogue) 
``` 

Now, when we click on this NPC, we can trigger the dialogue: 

![1](./images/1.png) 

Next, complete all the dialogues, and also use the reading and writing of variables and data to control the dialogue stage: 

```python 
leveldatacomp = serverApi.GetEngineCompFactory().CreateExtraData(serverApi.GetLevelId()) 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
#··· 

def PlayerAttack(self, args): 
#··· 
# If self.guide_dialogue={} (it means the first time clicking this NPC) 
if self.guide_dialogue == {}: 
# Use the command interface to generate dialogue and sound effects 
commandcomp.SetCommand("execute @a ~ ~ ~ tellraw @a {\"rawtext\":[{\"text\":\" §6§l【Family】 §r§fTata Village is a village located deep in the mountains, 'Becoming a more independent person' is the long-standing heritage of the village. §6[1/6]\"}]}") 
commandcomp.SetCommand("execute @a ~ ~ ~ /playsound random.orb @a ~ ~ ~ 3 1 3") 
# Give the variable a new parameter to control entering the next dialogue stage 
self.guide_dialogue["dialogue"] = 0 

elif self.guide_dialogue["dialogue"] == 0: 
commandcomp.SetCommand( 
"execute @a ~ ~ ~ tellraw @a {\"rawtext\":[{\"text\":\" §6§l【Family】 §r§fEvery year, the village holds a coming-of-age ceremony for young people who are about to reach adulthood. This year, the test left for you is §6[2/6]\"}]}") 
commandcomp.SetCommand("execute @a ~ ~ ~ /playsound random.orb @a ~ ~ ~ 3 1 3") 
self.guide_dialogue["dialogue"] = 1 

elif self.guide_dialogue["dialogue"] == 1: 
commandcomp.SetCommand( 
"execute @a ~ ~ ~ tellraw @a {\"rawtext\":[{\"text\":\" §6§l【Family】 §r§fBuild a seaside farm on Turtle Island for the village, as a tourist spot for the villagers to vacation in the future! §6[3/6]\"}]}") 
commandcomp.SetCommand("execute @a ~ ~ ~ /playsound random.orb @a ~ ~ ~ 3 1 3") 
self.guide_dialogue["dialogue"] = 2 

elif self.guide_dialogue["dialogue"] == 2: 
commandcomp.SetCommand( 
"execute @a ~ ~ ~ tellraw @a {\"rawtext\":[{\"text\":\" §6§l【Family】 §r§fIn order to help you adapt, I will first take you to get familiar with the life of the seaside farm and try to plant some plants.§6[4/6]\"}]}") 
commandcomp.SetCommand("execute @a ~ ~ ~ /playsound random.orb @a ~ ~ ~ 3 1 3") 
                self.guide_dialogue["dialogue"] = 3
            # Store new player_guide
            leveldatacomp.SetExtraData('player_guide', self.guide_dialogue)
```


<img src="./images/2.gif" alt="2" style="zoom:115%;" />