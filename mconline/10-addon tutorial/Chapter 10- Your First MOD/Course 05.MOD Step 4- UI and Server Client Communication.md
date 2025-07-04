--- 
front: 
hard: Advanced 
time: 10 minutes 
--- 

# MOD Step 4: UI and Server/Client Communication 

#### Author: Boundary 

#### What is UI 

UI is the interface for players to interact with the game. For example, there are many blocks with special functions in the world. When using these blocks, the game will pop up the UI interaction interface to guide the player to take the next step. Using MCSTUDIO's interface editor, you can quickly make the interface. The interface style file will also be saved in the resource package of the add-on package in json file format. 



#### Communicate with Client/Server 

The UI itself also runs on the client, so in general, the client interface can be used in the UI file. If you need to call the client system method, you can use the ClientApi.GetSystem interface to obtain the client system. At the same time, it will carry the NotifyToServer interface, so you can also directly transmit the UI data to the server. 

