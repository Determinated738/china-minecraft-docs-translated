--- 
front: https://nie.res.netease.com/r/pic/20220408/e24733db-2cc1-49ee-bacb-c1913b2e6c82.png 
hard: Getting Started 
time: 10 minutes 
selection: true 
--- 
# Specifications 

Making plug-ins that meet the specifications can not only increase readability, but also reduce conflicts between plug-ins, and make them easier to use and facilitate secondary development. 

This section will introduce the relevant specifications for plug-in development. 

## Design document specifications 

When designing a plug-in, use documents to record the design plan. On the one hand, it is easy to convert the plug-in function into the instruction document required by the developer, and on the other hand, it is easy to develop in the future. 

The document needs to include the following aspects: 

- Plugin function description (if the function flow is more complicated, it is best to include a flowchart) 

- UI diagram 
- Configuration instructions 
- API 
- Events and operation instructions 
- Functional description 

[Click me](./Design document example.html) to view the design document example of the portable warehouse plug-in. 

## Plugin specification 

Plugin directory and naming specifications can be found [here](https://g.126.fm/02YRPPK) 

## Introduction document specifications 

The introduction document is the readme.txt in the plugin directory. In order to make others better understand and use your plugin, you need to write readme.txt according to the specifications. 

For specific specifications, please refer to [here](https://g.126.fm/02AskEc) 

For example, the readme.txt of neteaseMenus below 

``` 
Plugin introduction: 
This server mod belongs to the "Main Menu" plug-in. 
The "Main Menu" plug-in implements the main menu function: 
- Main menu: defines and takes effect on the main menu in the game (configured in mod.json under lobby/game) 

Plugin composition: 
Currently, the "Main Menu" plug-in contains the following Mods: 
- neteaseMenus: deployed in lobby server or game server 


Usage steps: 
(1) In the deployment configuration, add neteaseMenus to the mods list of the required lobby server or game server 

Plugin API: 
(1) Set the main menu button status 
Applicable scope: client 
Function: UpdateMenus(data) 
Parameters: 
data: dict, dictionary for setting button status, refer to the following example for the format 
Return: 
bool, whether the setting is successful. Note that if the setting fails, the menu status may have been changed 
Example: 
import client.extraClientApi as clientApi 
data = { # key corresponds to the button number, starting from 0, value is a number in (0, 1), [0] means disabling the button, [1] means enabling the button 
1: 0, 
4: 1, 
16: -1, 
} 
menusSystem = clientApi.GetSystem("neteaseMenus", "neteaseMenusBeh") 
flag = menusSystem.UpdateMenus(data) 

(2) Get all the button configurations of the main menu 
Scope of application: client 
Function: GetMenus() 
Parameters: 
None 
Return: 
menus:dict Main menu button configuration, the structure corresponds to the configuration in mod.json, see mod.json for details 
Example: 
import client.extraClientApi as clientApi 
menusSystem = clientApi.GetSystem("neteaseMenus", "neteaseMenusBeh") 
menus = menusSystem.GetMenus() # The structure corresponds to the configuration in mod.json, see mod.json for details 

Plugin event: 
(1)MenusNavigateEvent 
Scope of application: client 
Namespace: namespace = 'neteaseMenus', systemname = 'neteaseMenusBeh' 
Description: Player clicks a button event 
Parameters: 
playerId: str, playerId of the player who clicked the button 
order: int, The serial number of the clicked button, starting from 0 
Example: 
def __init__(self, namespace, systemName): 
self.ListenForEvent('neteaseMenus', 'neteaseMenusBeh', 'MenusNavigateEvent', self, self.OnMenusNavigate) 

def OnMenusNavigate(self, data): 
print 'OnMenusNavigate', data 
playerId = data["playerId"] 
order = data["order"] 
print 'Player {} clicked button {} in the main menu'.format(playerId, order)


Update list: 
Version 1.0.0: 
Initial version 
Version 1.0.1: 
Adjusted UI resources and added code comments 
Version 1.0.2: 
Adjusted UI and code according to new specifications 
Version 1.0.3: 
Iterated new UI and code 
Version 1.0.4: 
Refactored UI and code, and the configuration method has also changed 
Version 1.0.5: 
Optimized plugin readme document description 
``` 

Contains the following: 

- Plugin introduction 
- Plugin composition 
- Usage steps 
- Plugin api 
- Plugin event 
- Update list 

In the plugin in the example above, there is no introduction to **operation instructions** and **pre-plugins**. If there is a need for operation instructions and pre-plugins in the plugin you wrote, you also need to write them all. 

For example, the following is an introduction to the operation instructions of the economic plugin. 

``` 
Supported operation commands: 
Operation commands: 
(1) Query the remaining amount of currency on a player (the player must be online) 
post url: http:masterip:masterport/query-player-doughs 
post body:{ 
"uid": 996 # Player's uid 
} 
response: 
{ 
"code": 1, # Return code, [1] represents success, other represents failure 
"message": "Request successful", # Specific description of the failure reason 
"entity": { # Returns the remaining amount of currency on the player, an empty dictionary if the query fails 
"RMB": 996, 
"USD": -996 
} 
} 
(2) Add/reduce currency for a player (parameters: player id, currency type, currency amount, currency amount can be negative) 
post url: http:masterip:masterport/update-player-doughs 
post body:{ 
"uid": 996, # player's uid

"mod": { # Modify the dictionary of currency data 
"RMB": 996, 
"USD": -996 
} 
} 
response: 
{ 
"code": 1, # Return code, [1] represents success, others represent failure 
"message": "Request successful", # Specific description of the reason for failure 
"entity": { # Return the remaining amount of currency on the player, an empty dictionary if the operation fails 
"RMB": 1992, 
"USD": -1992 
} 
} 
(3) Query the total number of stalls currently available (new in 2.0.0) 
post url: http:masterip:masterport/count-stalls 
post body:{} 
response: 
{ 
"code": 1, # Return code, [1] represents success, others represent failure 
"message": "Request successful", # Specific description of the reason for failure 
"entity": { 
"stalls": { 
"996": { 
"duration": 12, # Total duration of stall 
"deadline": 1590462263, # Automatic closing timestamp of stall 
"ver": 0, # Useless 
"label": "Good goods are not cheap", # Stall name 
"deals": [...] # Sales record of this stall 
} 
} 
} 
} 
``` 

For prerequisites, please refer to the face-to-face transaction plug-in below 

``` 
Plugin introduction: 
This server mod belongs to the "Face-to-face transaction" plug-in. 
The "Transaction" plug-in implements 2 main functions, 1 is transaction currency, and 1 is transaction items: 
- Transaction currency: weakly dependent on the economic plug-in, the corresponding currency type and currency map need to be configured. You can also manage it yourself. Just search for "Economy Plugin" in transactionServerSystem.py and replace the corresponding places for obtaining and updating currency with your own interface management. 
- Trading items: Players can trade by selecting the items and quantities in their backpacks. 
``` 

