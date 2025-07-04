--- 
front: https://nie.res.netease.com/r/pic/20220408/0c3f2c46-fb70-4102-820b-3ed513469dc5.png 
hard: Advanced 
time: 60 minutes 
selection: true 
--- 
# Use custom data to record data 

"Seaside Island" has three data that determine the progress of the game: the amount of money, the number of furniture, and the number of game days; we need to monitor and store these three data, so we need to use specific interfaces to store and obtain these three data, and use UI to visualize the data so that players can see the changes in the data in real time. 

After the novice guide is over, store the data uniformly: 

```python 
leveldatacomp = serverApi.GetEngineCompFactory().CreateExtraData(serverApi.GetLevelId()) 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 

#Function triggered when the novice guide is over and the game starts 
def start_game_data(self,playerid): 
#Store the initial number of coins 
player_data_coin = leveldatacomp.SetExtraData("player_coin",0) 
#Store the initial number of furniture 
player_data_furniture = leveldatacomp.SetExtraData("player_furniture",0) 
#Store the initial number of game days 
player_data_day = leveldatacomp.SetExtraData("player_day",0) 
#Store player id 
player_data_id = leveldatacomp.SetExtraData("player_id",playerid) 
``` 

## Write a function to track player trading behavior 

We need to change the data in real time according to the two situations of "getting money" and "spending money", so add communication events to modify the data when the player trades with the NPC: 

The tutorial content related to NPC trading is in [Chapter 5](../Chapter 05: Setting the Basic Status and Trading Table of NPC/Course 01. Customizing the Basic Behavior of NPC.md) 

```python 
leveldatacomp = serverApi.GetEngineCompFactory().CreateExtraData(serverApi.GetLevelId()) 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
# Listen for the event PlayerAttackEntityEvent 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), "PlayerAttackEntityEvent", 
self,self.PlayerAttack) 
# Listen for events sent by the client (players purchase goods) 
self.ListenForEvent("FarmMod", "ClientSystem", "buy_item", 
self,self.PlayerBuyItem) 

# Merchant id obtained in advance

self.animal_shop_id = "-120259084268" 

# Triggered when clicking on NPC 
def PlayerAttack(self,args): 
# Player id 
self.playername = args["playerId"] 
# Clicked NPCid 
entityid = args["victimId"] 
# If the clicked NPC is consistent with the stored merchant id 
if entityid == self.animal_shop_id: 
# Store the parameters to be transmitted: player id, merchant id, amount of money 
event = {"playerid":args["playerId"] , "entityid" : entityid, 
"player_coin": leveldatacomp.GetExtraData("player_coin")} 
# Send event to client 
self.NotifyToClient(self.playername,"create_shop_ui", event) 

# Function triggered after the player clicks the buy button in the transaction table and successfully purchases 
def PlayerBuyItem(self, args): 
# Save the remaining money after the transaction through the passed parameters 
leveldatacomp.SetExtraData("player_coin",args["coin"]) 
#The passed player id 
player_id = args['playerid'] 
#The actual name of the item passed 
item_name = args['buy_item'] 
# Issue items 
serverApi.GetEngineCompFactory().CreateItem(player_id).SpawnItemToPlayerInv( 
{ 
'newItemName': item_name, 
'count': 1 
}, 
player_id 
) 
``` 

```python 
class FarmClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
super(FarmClientSystem, self).__init__(namespace, systemName) 
# Listen for events sent by ServerSystem 
self.ListenForEvent("FarmMod", "ServerSystem", "create_shop_ui",self, self.Create_Shop_UI) 
# Merchant id obtained in advance 
self.animal_shop_id = "-120259084268" 

def Create_Shop_UI(self,event): 
if event["entityid"] == self.animal_shop_id: 
# Create transaction table UI 
self.ui = clientApi.PushScreen("Farm","new_shop") 
# Modify variables (products) through UI instance 
self.ui.item_button_text = self.animal_shop_item_button_text 
# Set the amount of money of the player transmitted by the event to the ui

self.ui.coin = event["player_coin"] 
``` 

```python 
class FarmUIScreen(ScreenNode): 
def __init__(self, namespace, name, param): 
ScreenNode.__init__(self, namespace, name, param) 
self.coin = 0 # variable for player's money 

# button binding 
@ViewBinder.binding(ViewBinder.BF_ButtonClickUp) 
def buy_button_clicked(self,args): 
if self.clicked_button_index == -1: 
print "The player has not selected an item yet" 
return 
# Get the price of the item 
price = self.item_button_text[self.clicked_button_index]['coin'] 
# If the player's money is greater than or equal to the price of the item → subtract → send the event to the server 
if self.coin >= price: 
self.coin -= price 
#Communicate to the server, passing the player ID, remaining money, and actual items purchased as parameters 
self.clientsystem.NotifyToServer("buy_item",{"playerid":clientApi.GetLocalPlayerId(),"coin":self.coin,"buy_item" 
:self.item_button_text[self.clicked_button_index]["itemname"]}) 
else: 
print "You can't afford it" 
``` 

Most of the functional logic has been introduced in Chapter 5 when making the transaction table. You only need to add some interfaces for obtaining and storing data on this basis; of course, it is not enough to only enter but not exit. We also need to make a function that can obtain money **"The recycling merchant will recycle the items in the box in the evening and get money"**: 

```json 
{ 
"format_version": "1.13.0", 
"minecraft:entity": { 
"description": { 
"identifier": "farm:acquirer", //Recycling merchant 
			"is_spawnable": true,
			"is_summonable": true,
			"is_experimental": false,
			"runtime_identifier": "minecraft:villager"
		},
		"components": {
			"minecraft:scheduler": { //Trigger events at a specific time
				"min_delay_secs": 0,
				"max_delay_secs": 10,
				"scheduled_events" : [
				  {
					"filters": {
					  "all_of": [
						{ "test": "hourly_clock_time", "operator": ">=", "value": 12000 },
						{ "test": "hourly_clock_time", "operator": "<", "value": 13000 }

] 
}, 
"event": "minecraft:work" // Triggered event 
} 
] 
} 
}, 
"component_groups": { 
}, 
"events": { 
"minecraft:work":{ 


} 
} 
} 
} 
``` 

Add a component that triggers an event at a specific time to the merchant's behavior file, and use MODSDK to listen to the merchant to execute the function logic when the event is triggered: 

```python 
leveldatacomp = serverApi.GetEngineCompFactory().CreateExtraData(serverApi.GetLevelId()) 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
# Listen for events EntityDefinitionsEventServerEvent 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(),'EntityDefinitionsEventServerEvent', 
self, self.Player_Event) 
# The recycling merchant id obtained in advance 
self.acquirer_id = "-983547510779" 

def Player_Event(self,args): 
# If the creature id that triggers the event is a recycling merchant 
if args["entityId"] == self.acquirer_id: 
# Use the pathfinding interface to let the recycling merchant walk to the box 
movecomp = serverApi.GetEngineCompFactory().CreateMoveTo(self.acquirer_id) 
movecomp.SetMoveSetting((72,66,82), 1.5, 2000, self.acquirer_callback) 

# Callback function for the end of pathfinding 
def acquirer_callback(self,entityid ,result): 
# If the recycling merchant arrives at the location 
if result == 0: 
# The names and prices of all recyclable goods 
goods_list = {"farm:spinach_item":8,"farm:whiteradish_item":4,"farm:peas_item":3, 
"farm:lemon_item":6,"farm:eggplant_item":4,"farm:crown_dasiy_item":4, 
"farm:corn_item":6,"farm:banana_item":6,"farm:bambooshoot_item":6, 
"minecraft:log":2,"minecraft:cobblestone":2,"minecraft:egg":8, 
"minecraft:wool":15,"minecraft:leather":15} 
# Create an interface

chestitemcomp = serverApi.GetEngineCompFactory().CreateItem(serverApi.GetLevelId()) 
chestslotcomp = serverApi.GetEngineCompFactory().CreateChestBlock(serverApi.GetLevelId()) 
# Create variables (number of slots in the box and the final settlement price) 
count = 0 
add_price = 0 
# Loop 0-26, corresponding to the number of slots in the small box 
for item in range(0,27): 
# Get the item information dictionary of the current slot 
itemdict = chestitemcomp.GetContainerItem((72,66,81), count, 0) 
# If there is something 
if itemdict: 
# If the item name of the slot is in the goods list 
if itemdict["newItemName"] in goods_list: 
# Item quantity * item price += to the variable 
add_price += itemdict["count"] * goods_list.get(itemdict["newItemName"]) 
# Set the number of items in this slot to 0 
chestslotcomp.SetChestBoxItemNum(None, (72,66,81), count, 0, 0) 
# Number of slots in the box += 1 
count += 1 
# Get the current player's money 
now_coin = leveldatacomp.GetExtraData("player_coin") 
# Add the current money to the final money settled above and store it 
leveldatacomp.SetExtraData("player_coin",now_coin + add_price) 
# Use the pathfinding interface to let the recycling merchant return home 
movecomp = serverApi.GetEngineCompFactory().CreateMoveTo(self.acquirer_id) 
movecomp.SetMoveSetting((132,71,96), 1.5, 2000, self.acquirer_callback_home) 

def acquirer_callback_home(self,entityid,result): 
print result 
``` 

## Write a function to track the number of days a player survives 

When the player finishes the novice guide and officially starts the game, you can reset the game time in the function: 

```python 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 

# Function triggered when the novice guide ends and the game starts 
def start_game_data(self,playerid): 
# Create time interface 
timecomp = serverApi.GetEngineCompFactory().CreateTime(serverApi.GetLevelId()) 
# Set the world time to 0 
timecomp.SetTime(0) 
``` 

To get the time of the current world, you can directly get Molang or use related interfaces: 


```python 
# Get the current world day through query.day 
clientApi.GetEngineCompFactory().CreateQueryVariable(clientApi.GetLocalPlayerId()).GetMolangValue('query.day') 

#or 

# Create time interface 
comp = serverApi.GetEngineCompFactory().CreateTime(levelId) 
# Get the current time 
passedTime = comp.GetTime() 
# Get the current day 
day = passedTime / 24000 
``` 

## Write a function to track the number of furniture held by the player 

All furniture is made of custom blocks, so we only need to listen to the two events of player placement and destruction of blocks to complete the tracking of the number of furniture: 

```python 
class FarmServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
# Listen for EntityPlaceBlockAfterServerEvent 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 
'EntityPlaceBlockAfterServerEvent', 
self, self.Place_Furniture) 
# Listen for ServerPlayerTryDestroyBlockEvent 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 
'ServerPlayerTryDestroyBlockEvent', 
self, self.Destroy_Furniture) 
# List of furniture made using the Chinese version of the custom block method 
self.netease_block_list = ["farm:connect_table", "farm:sofa_black", "farm:sofa_blue", "farm:sofa_brown", 
"farm:sofa_cyan", "farm:sofa_gray", 
"farm:sofa_light_blue", "farm:sofa_light_cyan", "farm:sofa_light_green", 
"farm:sofa_light_gray", "farm:sofa_orange", "farm:sofa_pink_red", 
"farm:sofa_purple", "farm:sofa_red", "farm:sofa_white", "farm:sofa_yellow"] 
# Triggered when placing a block 
def Place_Furniture(self, args): 
# Block coordinates and names obtained through events 
x = args['x'] 
y = args['y'] 
z = args['z'] 
blockname = args['fullName'] 
# Create a block state interface 
blockstatecomp = serverApi.GetEngineCompFactory().CreateBlockState(serverApi.GetLevelId()) 
# Get the state of the placed block 
blockstate = blockstatecomp.GetBlockStates((x, y, z), 0) 
# If farm:rotation is not in blockstate and the block name is not in the list, return (all furniture has farm:rotation attribute, so this can be used to determine whether it is furniture) 
# However, furniture made by the Chinese version of custom blocks does not have attributes, so it is necessary to create an additional list for these furniture for judgment conditions 
# Of course, you can also put all the furniture in a list for judgment

if "farm:rotation" not in blockstate and blockname not in self.netease_block_list: 
return 
# If it is furniture, it will continue to execute, and then set the furniture data += 1 
leveldatacomp.SetExtraData("player_furniture", leveldatacomp.GetExtraData("player_furniture") + 1) 

# Triggered when the block is destroyed 
def Destroy_Furniture(self, args): 
# Block coordinates and names obtained through events 
x = args['x'] 
y = args['y'] 
z = args['z'] 
blockname = args['fullName'] 
player_id = args['playerId'] 
# Create block state interface 
blockstatecomp = serverApi.GetEngineCompFactory().CreateBlockState(serverApi.GetLevelId()) 
# Get the state of the placed block 
blockstate = blockstatecomp.GetBlockStates((x, y, z), 0) 
# The logic below is the same as when placing furniture, but the data is changed from +=1 to -+1 
if "farm:rotation" not in blockstate and blockname not in self.netease_block_list: 
return 
leveldatacomp.SetExtraData("player_furniture", leveldatacomp.GetExtraData("player_furniture") - 1) 
event = {"player_data_furniture": leveldatacomp.GetExtraData("player_furniture")} 
self.NotifyToClient(leveldatacomp.GetExtraData("player_id"), "re_dataui", event) 
``` 

