--- 
sidebarDepth: 1 
--- 
# Index 

--- 

- [Component](#component) 
- [System](#system) 
- [Events](#events) 
- [Local Devices](#localdevices) 
- [Local Storage](#localstorage) 
- [Math](#math) 
- [Tools](#tools) 
- [Debug](#debug) 

### Component 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateComponent](Component.md#createcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a server component for the entity | 
| [CreateComponent](Component.md#createcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create a client component for the entity | 
| [DestroyComponent](Component.md#destroycomponent) | <span style="display:inline;color:#ff5555">Server</span> | Delete the server component of the entity | 
| [DestroyComponent](Component.md#destroycomponent) | <span style="display:inline;color:#7575f9">Client</span> | Delete the client component of the entity | 
| [GetComponent](Component.md#getcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Get the server component of the entity. Generally used to determine whether a component has been created. In other cases, please use CreateComponent | 
| [GetComponent](Component.md#getcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Get the client component of the entity. Generally used to determine whether a component has been created. In other cases, please use CreateComponent | 
| [GetComponentCls](Component.md#getcomponentcls) | <span style="display:inline;color:#ff5555">Server</span> | Used to obtain the server component base class. When implementing a new component, you need to inherit the class returned by this interface | 
| [GetComponentCls](Component.md#getcomponentcls) | <span style="display:inline;color:#7575f9">Client</span> | Used to obtain the client component base class. When implementing a new component, you need to inherit the class returned by this interface | 
| [GetEngineCompFactory](Component.md#getenginecompfactory) | <span style="display:inline;color:#ff5555">Server</span> | Get the factory of the engine component, through which you can create the engine component of the server | 
| [GetEngineCompFactory](Component.md#getenginecompfactory) | <span style="display:inline;color:#7575f9">Client</span> | Get the factory of the engine component, through which you can create the engine component of the client | 
| [RegisterComponent](Component.md#registercomponent) | <span style="display:inline;color:#ff5555">Server</span> | Used to register components in the engine | 
| [RegisterComponent](Component.md#registercomponent) | <span style="display:inline;color:#7575f9">Client</span> | Used to register components to the engine | 

### System 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetClientSystemCls](System.md#getclientsystemcls) | <span style="display:inline;color:#7575f9">Client</span> | Used to obtain the client system base class. When implementing a new system, you need to inherit the class returned by this interface | 
| [GetServerSystemCls](System.md#getserversystemcls) | <span style="display:inline;color:#ff5555">Server</span> | Used to obtain the server system base class. When implementing a new system, you need to inherit the class returned by this interface | 
| [GetSystem](System.md#getsystem) | <span style="display:inline;color:#ff5555">Server</span> | Get the registered system | 
| [GetSystem](System.md#getsystem) | <span style="display:inline;color:#7575f9">Client</span> | Used to get other system instances | 
| [RegisterSystem](System.md#registersystem) | <span style="display:inline;color:#ff5555">Server</span> | Used to register the system with the engine. The engine will create an instance of the system and recycle it when exiting the game. The system can execute the basic logic given by our engine, such as listening to events, executing Tick functions, communicating with clients, etc. | 
| [RegisterSystem](System.md#registersystem) | <span style="display:inline;color:#7575f9">Client</span> | Used to register the system to the engine. The engine will create an instance of the system and recycle it when exiting the game. The system can execute the basic logic given by our engine, such as listening to events, executing Tick functions, communicating with the server, etc. | 

### Event 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [BroadcastEvent](Event.md#broadcastevent) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Local broadcast events. Events broadcast by the client system can only be listened to by the client system, and events broadcast by the server system can only be listened to by the server system. | 
| [BroadcastToAllClient](event.md#broadcasttoallclient) | <span style="display:inline;color:#ff5555">Server</span> | The server broadcasts events to all clients |

| [CreateEventData](event.md#createeventdata) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Create custom event data, eventData is used to send events. The created eventData can be understood as a dict, which can be nested with dict, list and basic data types, but does not support tuple | 
| [GetEngineNamespace](event.md#getenginenamespace) | <span style="display:inline;color:#ff5555">Server</span> | Get the namespace of the engine event. When monitoring engine events, namespace passes the namespace returned by this interface | 
| [GetEngineNamespace](event.md#getenginenamespace) | <span style="display:inline;color:#7575f9">Client</span> | Get the namespace of the engine event. When listening to engine events, namespace passes the namespace returned by this interface | 
| [GetEngineSystemName](event.md#getenginesystemname) | <span style="display:inline;color:#ff5555">Server</span> | Get the engine system name. When listening to engine events, systemName passes the systemName returned by this interface | 
| [GetEngineSystemName](event.md#getenginesystemname) | <span style="display:inline;color:#7575f9">Client</span> | Get the engine system name. When listening to engine events, systemName passes the systemName returned by this interface | 
| [ListenForEvent](event.md#listenforevent) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Register to listen to events thrown by a certain system. When monitoring engine events, namespace and systemName are GetEngineNamespace() and GetEngineSystemName() respectively. For detailed event data of each event, please refer to the content under the "Event" category | 
| [NotifyToClient](event.md#notifytoclient) | <span style="display:inline;color:#ff5555">Server</span> | The server sends events to the specified client | 
| [NotifyToMultiClients](event.md#notifytomulticlients) | <span style="display:inline;color:#ff5555">Server</span> | Version 2.0 is only available in Apollo, and the server sends events to a specified batch of clients | 
| [NotifyToServer](event.md#notifytoserver) | <span style="display:inline;color:#7575f9">Client</span> | The client sends events to the server | 
| [UnListenAllEvents](event.md#unlistenallevents) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Unregister to listen to all events thrown by a certain system, that is, no longer listen. | 
| [UnListenForEvent](event.md#unlistenforevent) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Unregister to listen to events thrown by a certain system, that is, no longer listen. If it is an engine event, namespace and systemName are [GetEngineNamespace](event.md#getenginenamespace) and [GetEngineSystemName](event.md#getenginesystemname) respectively. Corresponds to ListenForEvent. | 

### Local device 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetIP](Local device.md#getip) | <span style="display:inline;color:#7575f9">Client</span> | Get the local player's IP address | 
| [GetPlatform](Local device.md#getplatform) | <span style="display:inline;color:#ff5555">Server</span> | Get the platform where the script runs | 
| [GetPlatform](Local device.md#getplatform) | <span style="display:inline;color:#7575f9">Client</span> | Get the platform where the script runs | 
| [IsInApollo](Local device.md#isinapollo) | <span style="display:inline;color:#ff5555">Server</span> | Returns whether the current game mod is running in the Apollo network server | 
| [IsInServer](Local Device.md#isinserver) | <span style="display:inline;color:#ff5555">Server</span> | Gets whether the current game is running in a server environment | 

### Local Storage 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetConfigData](Local Storage.md#getconfigdata) | <span style="display:inline;color:#7575f9">Client</span> | Gets the data stored in the local configuration file | 
| [SetConfigData](Local Storage.md#setconfigdata) | <span style="display:inline;color:#7575f9">Client</span> | Store data in local configuration files | 

### Mathematics 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetDirFromRot](数学.md#getdirfromrot) | <span style="display:inline;color:#ff5555">Server</span> | Get orientation by rotation angle | 
| [GetDirFromRot](数学.md#getdirfromrot) | <span style="display:inline;color:#7575f9">Client</span> | Get orientation by rotation angle | 
| [GetRotFromDir](数学.md#getrotfromdir) | <span style="display:inline;color:#ff5555">Server</span> | Get rotation angle by orientation | 
| [GetRotFromDir](数学.md#getrotfromdir) | <span style="display:inline;color:#ff5555">Server</span> | style="display:inline;color:#7575f9">Client</span> | Get the rotation angle by orientation | 

### Tools 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddRepeatedTimer](Tools.md#addrepeatedtimer) | <span style="display:inline;color:#ff5555">Server</span> | Add a timer triggered by the server and execute repeatedly | 
| [AddRepeatedTimer](Tools.md#addrepeatedtimer) | <span style="display:inline;color:#7575f9">Client</span> | Add a timer triggered by the client and execute repeatedly | 
| [AddTimer](Tools.md#addtimer) | <span style="display:inline;color:#ff5555">Server</span> | Add a timer triggered by the server, non-repeating | 
| [AddTimer](Tool.md#addtimer) | <span style="display:inline;color:#7575f9">Client</span> | Add a timer triggered by the client, non-repeating | 
| [CancelTimer](Tool.md#canceltimer) | <span style="display:inline;color:#ff5555">Server</span> | Cancel the timer | 
| [CancelTimer](Tool.md#canceltimer) | <span style="display:inline;color:#7575f9">Client</span> | Cancel the timer | 
| [CheckNameValid](Tool.md#checknamevalid) | <span style="display:inline;color:#ff5555">Server</span> | Check whether the nickname is legal, that is, it does not contain sensitive words | 
| [CheckNameValid](Tool.md#checknamevalid) | <span style="display:inline;color:#7575f9">Client</span> | Check whether the nickname is legal, that is, it does not contain sensitive words |

| [CheckWordsValid](Tool.md#checkwordsvalid) | <span style="display:inline;color:#ff5555">Server</span> | Check if the statement is legal, that is, it does not contain sensitive words | 
| [CheckWordsValid](Tool.md#checkwordsvalid) | <span style="display:inline;color:#7575f9">Client</span> | Check if the statement is legal, that is, it does not contain sensitive words | 
| [GetChinese](Tool.md#getchinese) | <span style="display:inline;color:#ff5555">Server</span> | Get the Chinese corresponding to langStr, refer to \handheld\localization\handheld\data\resource_packs\vanilla\texts\zh_CN.lang in the PC development package | 
| [GetChinese](Tool.md#getchinese) | <span style="display:inline;color:#7575f9">Client</span> | Get the Chinese corresponding to langStr, refer to \handheld\localization\handheld\data\resource_packs\vanilla\texts\zh_CN.lang in the PC development kit | 
| [GetFps](Tool.md#getfps) | <span style="display:inline;color:#7575f9">Client</span> | Get fps | 
| [GetMinecraftEnum](Tool.md#getminecraftenum) | <span style="display:inline;color:#ff5555">Server</span> | Used to get the enumeration value in the [Enumeration Value Document](../../Enumeration Value/Index.md) | 
| [GetMinecraftEnum](Tool.md#getminecraftenum) | <span style="display:inline;color:#7575f9">Client</span> | Used to get the enumeration value in the [enumeration value document](../../enumeration value/index.md) | 
| [GetModConfigJson](tool.md#getmodconfigjson) | <span style="display:inline;color:#7575f9">Client</span> | Returns the contents of the json format configuration file of the specified path in the form of a dictionary. The file must be placed in the /modconfigs directory of the resource pack | 
| [StartCoroutine](tool.md#startcoroutine) | <span style="display:inline;color:#ff5555">Server</span> | Start the server-side coroutine to implement segmented function execution, which can be used to alleviate the problem of game lag caused by complex logic calculations | 
| [StartCoroutine](tool.md#startcoroutine) | <span style="display:inline;color:#7575f9">Client</span> | Enable client coroutine to implement segmented function execution, which can be used to alleviate game lag caused by complex logic calculations | 
| [StopCoroutine](Tools.md#stopcoroutine) | <span style="display:inline;color:#ff5555">Server</span> | Stop coroutine | 
| [StopCoroutine](Tools.md#stopcoroutine) | <span style="display:inline;color:#7575f9">Client</span> | Stop client coroutine | 

### Debug 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetEnableReconnectNetgame](Debug.md#getenablereconnectnetgame) | <span style="display:inline;color:#7575f9">Client</span> | Get whether disconnection and reconnection are allowed | 
| [GetKeepResourceWhenTransfer](debug.md#getkeepresourcewhentransfer) | <span style="display:inline;color:#7575f9">Client</span> | Get fast server switching settings | 
| [GetResourceFastload](debug.md#getresourcefastload) | <span style="display:inline;color:#7575f9">Client</span> | Get resource fast loading settings | 
| [ReloadAllMaterials](debug.md#reloadallmaterials) | <span style="display:inline;color:#7575f9">Client</span> | Reload all material files | 
| [ReloadAllShaders](debug.md#reloadallshaders) | <span style="display:inline;color:#7575f9">Client</span> | Reload all Shader files | 
| [ReloadOneShader](debug.md#reloadoneshader) | <span style="display:inline;color:#7575f9">Client</span> | Reload a Shader file | 
| [SetEnableReconnectNetgame](debug.md#setenablereconnectnetgame) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to allow disconnection and reconnection | 
| [SetKeepResourceWhenTransfer](debug.md#setkeepresourcewhentransfer) | <span style="display:inline;color:#7575f9">Client</span> | Set fast server switching | 
| [SetResourceFastload](debug.md#setresourcefastload) | <span style="display:inline;color:#7575f9">Client</span> | Set fast resource loading | 
| [StartMemProfile](debug.md#startmemprofile) | <span style="display:inline;color:#ff5555">Server</span> | Start the server script memory analysis. After starting, call [StopMemProfile](debug.md#stopMemProfile) to generate the function memory flame graph in the path fileName. This interface only supports PC. The generated flame graph can be opened with a browser. Chrome browser is recommended. | 
| [StartMemProfile](debug.md#startmemprofile) | <span style="display:inline;color:#7575f9">Client</span> | Start the client script memory analysis. After starting, call [StopMemProfile](debug.md#stopMemProfile) to generate the function memory flame graph in the path fileName. This interface only supports PC. The generated flame graph can be opened with a browser. Chrome browser is recommended. | 
| [StartMultiProfile](debug.md#startmultiprofile) | <span style="display:inline;color:#ff5555">Server</span> | Start the server-side and client-side script performance analysis. After starting, call [StopMultiProfile](debug.md#stopmultiprofile) to generate the function performance flame graph in the path fileName. The data error is large during dual-end collection. It is recommended to use the single-end version of [StartProfile](debug.md#startprofile) first. This interface only supports PC. | 
| [StartMultiProfile](debug.md#startmultiprofile) | <span style="display:inline;color:#7575f9">Client</span> | Start the server-side and client-side script performance analysis. After starting, call [StopMultiProfile](debug.md#stopmultiprofile) to generate the function performance flame graph in the path fileName. The data error is large when collecting data from both ends. It is recommended to use the single-end version of [StartProfile](debug.md#startprofile) first. This interface only supports PC end. | 
| [StartProfile](debug.md#startprofile) | <span style="display:inline;color:#ff5555">Server</span> | Start the server script performance analysis. After starting, call [StopProfile](debug.md#stopprofile) to generate the function performance flame graph in the path fileName. This interface only supports PC end. The generated flame graph can be opened with a browser. Chrome browser is recommended. | 
| [StartProfile](debug.md#startprofile) | <span style="display:inline;color:#7575f9">Client</span> | Start the client script performance analysis. After starting, call [StopProfile](debug.md#stopprofile) to generate the function performance flame graph in the path fileName. This interface only supports PC end. The generated flame graph can be opened with a browser. Chrome browser is recommended. | 
| [StartRecordEvent](debug.md#startrecordevent) | <span style="display:inline;color:#ff5555">Apollo</span> | Start the statistics of script event reception and transmission between the server and the client. After starting, call [StopRecordEvent](debug.md#stoprecordevent) to obtain the statistics of script event reception and transmission between the two function calls. Only supports rental service and Apollo network service environment (does not support stand-alone environment) | 
| [StartRecordPacket](debug.md#startrecordpacket) | <span style="display:inline;color:#ff5555">Apollo</span> | Start the statistics of engine packet reception and transmission between the server and the client. After starting, call [StopRecordPacket](debug.md#stoprecordpacket) to obtain the statistics of engine packet reception and transmission between the two function calls. Only supports rental service and Apollo network service environment (does not support stand-alone environment) | 
| [StopMemProfile](debug.md#stopmemprofile) | <span style="display:inline;color:#ff5555">Server</span> | Stop server script memory analysis and generate flame graph, used with [StartMemProfile](debug.md#startMemProfile), this interface only supports PC | 
| [StopMemProfile](debug.md#stopmemprofile) | <span style="display:inline;color:#7575f9">Client</span> | Stop client script memory analysis and generate flame graph, used with [StartMemProfile](debug.md#startMemProfile), this interface only supports PC | 
| [StopMultiProfile](debug.md#stopmultiprofile) | <span style="display:inline;color:#ff5555">Server</span> | Stop dual-end script performance analysis and generate flame graph, used with [StartMultiProfile](debug.md#startmultiprofile), this interface only supports PC side | 
| [StopMultiProfile](debug.md#stopmultiprofile) | <span style="display:inline;color:#7575f9">Client</span> | Stop dual-end script performance analysis and generate flame graph, used with [StartMultiProfile](debug.md#startmultiprofile), this interface only supports PC side | 
| [StopProfile](debug.md#stopprofile) | <span style="display:inline;color:#ff5555">Server</span> | Stop server-side script performance analysis and generate flame graph, used with [StartProfile](debug.md#startprofile), this interface only supports PC side | 
| [StopProfile](debug.md#stopprofile) | <span style="display:inline;color:#7575f9">Client</span> | Stop client script performance analysis and generate flame graph, used with [StartProfile](debug.md#startprofile), this interface only supports PC side | 
| [StopRecordEvent](debug.md#stoprecordevent) | <span style="display:inline;color:#ff5555">Apollo</span> | Stop the script event sending and receiving statistics between the server and the client and output the results, used with [StartRecordEvent](debug.md#startrecordevent), the output result is a dictionary, the key is the network package name, and the value dictionary records the sending and receiving information. For details, see the example, only supports rental service and Apollo network service environment (not supported in stand-alone environment) | 
| [StopRecordPacket](debug.md#stoprecordpacket) | <span style="display:inline;color:#ff5555">Apollo</span> | Stop the engine packet statistics between the server and the client and output the results. Used in conjunction with [StartRecordPacket](debug.md#startrecordpacket), the output result is a dictionary, the key is the network packet name, and the value dictionary records the sending and receiving information. See the example for details. Only supports rental services and Apollo network service environments (not stand-alone environments) | 

