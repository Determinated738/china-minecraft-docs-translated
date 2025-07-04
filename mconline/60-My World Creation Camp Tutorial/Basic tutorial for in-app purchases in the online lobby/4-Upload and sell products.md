--- 
front: 
hard: Advanced 
time: 10 minutes 
--- 

# Upload and sell goods 

<iframe src="https://cc.163.com/act/m/daily/iframeplayer/?id=63468187c6dfd1bb76f2bfb4" width="800" height="600" allow="fullscreen"/> 

## Upload maps and goods in Kaiping and implement the design of instructions 

When creating resources, select **Online Hall** as the resource category and check the commercial in-app purchase function. 

<img src="./image/1_41.png" alt="image-20220901182339201" style="zoom:50%;" /> 

After creation, the resource will appear in the **Online Hall Product Column**. 

![image-20220901182537714](./image/1_42.png) 

Click **Add product**. 

![image-20220901182801120](./image/1_43.png) 

Optional: Edit product category information. 

<img src="./image/1_44.png" alt="image-20220912015916334" style="zoom:50%;" /> 

Edit basic information. 

<img src="./image/1_45.png" alt="image-20220912020216785" style="zoom:50%;" /> 

Regarding the implementation instructions, the original intention is to pass the content to the logic system as an identifier to let the code know which product it is. For example, let's write a few characters in the simplest way: 

<img src="./image/1_46.png" alt="image-20220901184950487" style="zoom:50%;" /> 

Then when coding: 

```python 
def PlayerBuySometing(self, playerId, buyCommand): 
if buyCommand == 'vip1': 
self.GivePlayerVip(playerId, level=1) 
... 
``` 

The implementation command format supports `str` or `json`. Either one can be used. It is recommended to use `json`. The reason is that if `str` is used, then the product with the modified implementation command cannot be put on the shelf without updating the package body. Modifying a character will cause the service to be unavailable. Although it will not happen under normal circumstances, it is better to have a backup plan. 

<img src="./image/1_47.png" alt="image-20220901183906907" style="zoom:50%;" />


Using the `json` format, even if some changes need to occur, as long as the core content does not change, **it will not affect the recognition function itself**. 

<img src="./image/1_48.png" alt="image-20220901184403182" style="zoom:50%;" /> 

`json` can contain any fields as long as they serve as identification. It can be code or name or any form, depending on the developer's preference. 

<img src="./image/1_49.png" alt="image-20220901184454109" style="zoom:50%;" /> 

Before actually filling in the implementation instructions, in order to ensure that there is no error that cannot be deserialized, it is recommended to verify and compress json in the formatting tool. 

<img src="./image/1_50.png" alt="image-20220912020926106" style="zoom:50%;" /> 

<img src="./image/1_51.png" alt="image-20220912020955017" style="zoom:50%;" /> 

Add the remaining product information and save the product. 

![image-20220912021147595](./image/1_52.png) 

Submit the product for self-testing**, and the online lobby resource itself for self-testing**, and you can see this product appear in the showcase. 

Of course, this is only the showcase of the beta client, and the official version will not put this product on the shelves. If the product is to be put into the production environment, it needs to be submitted for review and then updated to the showcase. For more information about product upload, please refer to <a href="../../../mcguide/26-在线大厅/5-在线大厅作品与商品加载文档.html">Product upload document</a>. 

![image-20220912021729008](./image/1_53.png) 

<img src="./image/1_54.png" alt="image-20220901190523718" style="zoom: 42%;" /> 

<img src="./image/1_55.png" alt="image-20220912021836175" style="zoom: 25%;" /> 

<img src="./image/1_56.png" alt="image-20220912021910666" style="zoom:25%;" /> 

Add the remaining two products as shown above. 

![image-20220912022753488](./image/1_57.png) 

<img src="./image/1_58.png" alt="image-20220912023500454" style="zoom:25%;" /> 

## Selling goods in the game through neteaseStore 

Speaking of which, do you still remember the `neteaseStore` we mentioned in the last chapter? 

<img src="./image/1_59.png" alt="image-20220901191433701" style="zoom:50%;" /> 

After uploading the goods, we hope that players can not only buy them in the window, but also buy them in the game and take effect immediately. At this time, we need to use the neteaseStore frequently mentioned in the previous article, **It is an important medium for selling goods to players in the game**. 

![buy](./image/buy1.gif) 

neteaseStore can be seen as a UI. There are two ways to open it: 

- By default, it comes with a button in the upper left corner. Click it to open it.


<img src="./image/1_60.png" alt="image-20220901195719468" style="zoom: 100%;" /> 

- Do not display the built-in button, stimulate the player's purchasing demand through gameplay, and use the <a href="../../../mcdocs/1-ModAPI/界面/原创UI.html#openneteasestoregui">interface</a> to pull up the UI at the right time to guide the player to purchase 

| Parameter name | Data type | Description | 
| :----------- | :------- | :----------- | 
| categoryName | str | Product category name | 
| itemName | str | Product name | 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.OpenNeteaseStoreGui("Product", "Test Product 1") 
``` 

In order to reduce the workload, we use the first method here, but the built-in button of neteaseStore is not displayed at the beginning. After all, not all gameplays require it, so it is necessary to call an interface to display this button when the player enters the game. 

Create a new part, name it ShowStorePart, and write a line of code: 

```python 
def InitClient(self): 
PartBase.InitClient(self) 
self.GetApi().HideNeteaseStoreGui(False) 
``` 

Mount it under **Player preset** or **GM class preset**: 

**GM class** preset refers to GameMananger, which is usually an empty preset with always loaded and preloaded checked 

<img src="./image/1_61.png" alt="image-20220912030545679" style="zoom:50%;" /> 

<img src="./image/1_62.png" alt="image-20220912133837819" style="zoom: 50%;" /> 

It's that simple, enter the game and you can see the built-in store button displayed. 

<img src="./image/1_60.png" alt="image-20220901195719468" />