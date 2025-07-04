--- 
sidebarDepth: 1 
--- 
# Index 

--- 

- [General](#General) 
- [Custom Book](#Custom Book) 
- [Custom Achievement System](#Custom Achievement System) 

### General 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CheckCanBindUI](General.md#checkcanbindui) | <span style="display:inline;color:#7575f9">Client</span> | Check whether the entity can bind the overhead UI. For details on how to bind the UI to the entity, see [CreateUI](General.md#CreateUI) Interface | 
| [CreateUI](General.md#createui) | <span style="display:inline;color:#7575f9">Client</span> | Create UI, see <a href="../../../../mcguide/18-Interface and Interaction/30-UI Instructions.html#Interface Creation Process and Life Cycle">Interface Creation Process and Life Cycle</a> | 
| [GetCustomUIControlProxyCls](General.md#getcustomuicontrolproxycls) | <span style="display:inline;color:#7575f9">Client</span> | Get the native interface custom UI proxy base class | 
| [GetMiniMapScreenNodeCls](General.md#getminimapscreennodecls) | <span style="display:inline;color:#7575f9">Client</span> | Get the small map ScreenNode base class | 
| [GetNativeScreenManagerCls](General.md#getnativescreenmanagercls) | <span style="display:inline;color:#7575f9">Client</span> | Get the NativeScreenManager class | 
| [GetScreenNodeCls](General.md#getscreennodecls) | <span style="display:inline;color:#7575f9">Client</span> | Get the ScreenNode class | 
| [GetTopScreen](General.md#gettopscreen) | <span style="display:inline;color:#7575f9">Client</span> | Get the UI node at the top of the UI stack | 
| [GetTopUI](General.md#gettopui) | <span style="display:inline;color:#7575f9">Client</span> | Get the UI name at the top of the UI stack | 
| [GetUI](General.md#getui) | <span style="display:inline;color:#7575f9">Client</span> | Get the UI node, see <a href="../../../../mcguide/18-Interface and Interaction/30-UI Instructions.html#Interface Creation Process and Life Cycle">Interface Creation Process and Life Cycle</a> | 
| [GetViewBinderCls](General.md#getviewbindercls) | <span style="display:inline;color:#7575f9">Client</span> | Get ViewBinder Class | 
| [GetViewViewRequestCls](General.md#getviewviewrequestcls) | <span style="display:inline;color:#7575f9">Client</span> | Get ViewRequest Class | 
| [PopScreen](General.md#popscreen) | <span style="display:inline;color:#7575f9">Client</span> | Close UI using stack management | 
| [PopTopUI](General.md#poptopui) | <span style="display:inline;color:#7575f9">Client</span> | Pop up the UI on the top of the UI stack | 
| [PushScreen](Common.md#pushscreen) | <span style="display:inline;color:#7575f9">Client</span> | Create a UI using stack management | 
| [RegisterUI](Common.md#registerui) | <span style="display:inline;color:#7575f9">Client</span> | Register the UI. Before creating the UI, you need to register the UI first. The same UI only needs to be registered once. For details, see <a href="../../../../mcguide/18-Interface and Interaction/30-UI Instructions.html#Interface Creation Process and Life Cycle">Interface Creation Process and Life Cycle</a> | 

### Custom Book 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetBookManager](Custom Book.md#getbookmanager) | <span style="display:inline;color:#7575f9">Client</span> | Get Book Management Object | 

### Custom Achievement System 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddNodeProgress](Custom Achievement System.md#addnodeprogress) | <span style="display:inline;color:#ff5555">Server</span> | Increase the achievement progress of the corresponding achievement node of the corresponding player | 
| [GetChildrenNode](Custom Achievement System.md#getchildrennode) | <span style="display:inline;color:#ff5555">Server</span> | Get the list of all child nodes of the next level of the achievement node | 
| [GetNodeDetailInfo](Custom Achievement System.md#getnodedetailinfo) | <span style="display:inline;color:#ff5555">Server</span> | Get the corresponding node information of the corresponding player | 
| [SetNodeFinish](Custom Achievement System.md#setnodefinish) | <span style="display:inline;color:#ff5555">Server</span> | Set the corresponding achievement node of the corresponding player to complete | 

