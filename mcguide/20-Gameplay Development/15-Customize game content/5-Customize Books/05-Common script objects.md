--- 
front: 
hard: Getting Started 
time: minutes 
sidebarDepth: 4 
--- 

# Common Script Objects 

## 1. Book Page Jump Mechanism 

### 1. Overview <span id="Page Jump Mechanism"></span> 

The so-called page jump is similar to the browser page jump effect. For example, from the homepage of the book, click the directory icon to jump to the homepage of the directory. From the homepage of the directory, click the chapter title to jump to the chapter homepage. These are common jump operations. 

<img src="../picture/customBook/API/objs/Common Jump Demonstration.gif" alt="Common Jump Demonstration" style="zoom: 100%;" /> 

<center>Jump from the directory to a certain page in the chapter</center> 

In addition to this regular jump, it also supports link address jump. In order to explain how the link address is used, it is necessary to explain the related objects and their relationship. 

### 2. Object analysis <span id="Object Analysis"></span> 

The constituent elements of a book are actually pages one by one, but their relationship is not independent. Some pages belong to the same chapter, and some pages are used as the homepage of a directory. For this reason, we group all pages and use the **PageGroup** object to manage the pages under it. The layout and sorting of the pages in the group are the responsibility of **PageGroup**. 

<img src="../picture/customBook/API/objs/页面组概念.png" alt="页面组概念" style="zoom: 100%;" /> 

As shown in the example above, this book has 8 pages (page numbers start from 0) and is managed by 3 PageGroups. When you need to request page 4, you only need to request its first page from PageGroup3. <br>The format of the requested address is **PageGroup3 name + "/0**", 0 means page 0. 

Although there is group management, it is still not like a book with a directory, chapter and other hierarchical structures. PageGroup is still at the same level, so there are three objects: **Book**, **Category**, **Entry**. They all inherit from **PageGroup**. In addition to pointing to the page, they can also point to its sub-page group. For details, see "**behavior_pack/customBooks/Book1**" in the example [CustomBookMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBookMod). The corresponding Chinese name of the item is "**Link Test Book"**. 

<img src="../picture/customBook/API/objs/Hierarchical Jump Demonstration.gif" alt="Hierarchical Jump Demonstration" style="zoom: 45%;" /> 

<img src="../picture/customBook/API/objs/Hierarchical Concept.png" alt="Hierarchical Concept" style="zoom: 100%;" /> 

As shown in the figure above, pages 0 and 1 are the first page of the book (the first page includes the introduction of the first page and the directory list display page), which is managed by the Book object Book1, and it also points to its sub-page group Category1. 

Pages 2 and 3 are the first page of the directory 1 (the first page includes the chapter list display page in addition to the introduction of the first page), which is managed by the Category object Category1, and it also points to its sub-page group Entry1. 

Pages 4, 5, 6, and 7 are the actual pages of **Chapter 1**, which are managed by the **Entry** object **Entry1**, which has no child page groups. 

- <span id="absolute path">Absolute path (starting with "**/**")</span> 

The custom book system will set the path values of these three page groups according to the hierarchical relationship as follows: 

- The name of **Book1** is its [identifier](01-custom basic book.md#book identifier), and its **absolute path** is "**/Book1 name**", that is, "**/Book1**". 
- The name of **Category1** is its [identifier](01-custom basic book.md#catalog identifier), and its **absolute path** is "**Category1's parent page group absolute path/Category1 name**", that is, "**/Book1/Category1**". 
- The name of **Entry1** is its [identifier](01-Custom Basic Book.md#Chapter identifier), and its **absolute path** is "**Entry1's parent page group's absolute path/Entry1's name**", that is, "**/Book1/Category1/Entry1**". 


If you do not add a **page number** after the path, it will jump to **page 0** by default. **Return** is an operation relative to the jump, and you can only return after the jump. 

- Relative path 

A relative path does not start with "**/**". When the path is parsed, the current page group is taken as the beginning of the path to form an absolute path. For example, if the current page group is **Entry1**, if you call the [To](#To) function and pass in the parameter "**2**", it will be spliced into the global path "**Entry1's absolute path/2**", that is, "**/Book1/Category1/Entry1/2**", which jumps to **page 6**. 

- For path jumps, you can refer to the two **buttons** in the **homepage** of Chapter 1 in the example to click and jump. 

The custom book system supports page jumps within the same chapter, across chapters, within the same directory, and across directories, but does not support jumps between different books. You can only jump to pages in the currently opened book. 

## 2.BookConfig<span id="book configuration"></span> 

The configuration object of **system default value** is a static object. Please do not modify the properties of this object during program operation. 

| Property name | Description | Enumeration value | 
| --------------- | -------------------- | ------------------------------------------------------------ | 
| TextSize | Text font size (integer) | infotext: font size of component annotation text, value is 6px<br>footprint: font size of page footer text, value is 8px<br>content: font size of content text, value is 10px<br>smallTitle: small title, value is 12px<br>middleTitle: middle title, value is 14px<br>title: large title, value is 16px | 
| Colors | Color (three-dimensional floating point number) | TextDefault: default font color, value is (48, 3, 3, 255) normalized value<br/>BookTitle: font color of the book homepage title, value is (249, 221, 166, 255) normalized value<br/>SubTitle: font color of page title, value is (72.0, 30, 23, 255) normalized value<br/> | 
| TextAlign | Text alignment | Left: The text box size is fixed, and the text is aligned to the left<br/>Center: The text box size is fixed, and the text is aligned to the center<br/>Right: The text box size is fixed, and the text is aligned to the right<br/>Fit_Left: The text box size is adaptive, and the text is aligned to the left<br/>Fit_Center: The text box size is adaptive, and the text is aligned to the center<br/>Fit_Right: The text box size is adaptive, and the text is aligned to the right | 
| ImageReszieRule | Image scaling | Ninesliced: Nine-grid scaling, with 0px left and right margins<br>Fit: The image ratio is fixed, and the image will try to fill the given space | 
| Images | Preset image path | blank: A completely transparent blank image<br>categoryDefaultIcon: Default directory icon<br/> <img src="../picture/customBook/API/config/categoryDefaultIcon.png" style="zoom: 150%;"></img><br>lockBtn_dark: The default lock icon for the directory<br/><img src="../picture/customBook/API/config/lockBtn_dark.png" style="zoom: 250%;"></img><br>sqrtPanel_light: The default background image for entity display<br><img src="../picture/customBook/API/config/sqrtPanel_light.png" style="zoom: 250%;"></img><br/>progressBar_light: The default foreground image of the progress bar<br><img src="../picture/customBook/API/config/progressBar_light.png" style="zoom: 100%;"></img><br/>progressBar_dark: The default background image of the progress bar<br><img src="../picture/customBook/API/config/progressBar_dark.png" style="zoom: 100%;"></img><br/> | 

Get method: 

```python 
import mod.client.extraClientApi as clientApi 
# Get the book management object, how to use the visible BookManager API 
bookManager = clientApi.GetBookManager() 
# Get the book configuration constant 
bcf = bookManager.GetBookConfig() 
``` 

## 3.BookManager<span id="BookManager"></span> 

This object manages **all book objects**, it will save the [browsing history](01-Custom Basic Book.md#Browsing History) and [link address](#absolute path) of all books, and provide public methods for all books. Through this object, you can get the currently opened book object, call the global message display, register a custom page, and jump to the book page. 

This object is a global singleton object and can be obtained through the API. 

```python 
import mod.client.extraClientApi as clientApi 
bookManager = clientApi.GetBookManager() 
``` 

### GetBookConfig 

- Description 

Get book configuration constants 

- Parameters


None 

- Return value 

| Data type | Description | 
| ----------------------- | ------------ | 
| [BookConfig](#BookConfig) | Book configuration constants | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Get the book management object 
bookManager = clientApi.GetBookManager() 
# Get the book configuration constants 
bcf = bookManager.GetBookConfig() 
print bcf.TextSize.content # Output the font size value of normal text 10 
``` 

### GetBookInstance 

- Description 

Get the object that manages the book according to the book name 

- Parameters 

| Parameter name | Data type | Description | 
| -------- | -------- | ------------------------------------------------------------ | 
| bookName | str | The name of the book, that is, the [identifier] of the book (01-Custom Basic Book.md#Book identifier) | 

- Return value 

| Data type | Description | 
| ------------------------- | ---------------- | 
| [NormalBook](#NormalBook) | The object that manages the book | 

- Notes 
- If the book is not created successfully, None will be returned. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
print bookInstance.bookName # Output the name of the book 
``` 


### GetOpeningBookInstance 

- Description 

Get the management object of the currently open book 

- Parameters 

None 

- Return value 

| Data type | Description | 
| ------------------------- | ---------------------------- | 
| [NormalBook](#NormalBook) | Management object of the book in the open state | 

- Notes 

- If there is no currently open book, None will be returned. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetOpeningBookInstance() # Get the management object of the book currently being opened 
if bookInstance: 
print bookInstance.bookName # Output the name of the book 
``` 

### ShowMsg<span id="Show message text"></span> 

- Description 

Global display message text 

- Parameters 

| Parameter name | Data type | Description | 
| -------- | --------------- | ------------------------------------------------------------ | 
| position | tuple(int, int) | Position of message display ([Global coordinate system](01-Custom basic book.md#Page writing)) | 
| msg | str | Text content of the message<br>The default value is "**Click without any description, please fill in data**" | 

- Return value 

None 

- Example 

You can see the code of the custom page **behavior_pack/tutorialScripts/pages/buttonPage.py** in [CustomBookMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBookMod). The function implemented here is to display text information in the center of the button after clicking the button. 


```python 
def ShowMsg(self, msg): 
# Get all book management objects 
bookManager = clientApi.GetBookManager() 
# Get the root node of the UI control encapsulated by the button1 component 
buttonNode = self.button1.GetRootUINode() 
# Use GetNodeCenterGlobal to get the global coordinates of the center of the root node 
position = self.button1.GetNodeCenterGlobal(buttonNode) 
# Display prompt message 
bookManager.ShowMsg(position, msg) 
``` 

- Notes 
- The text is displayed for **2 seconds** and will be automatically hidden after 2 seconds. 

### HideMsg 

- Description 

Hide the global message text 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookManager = clientApi.GetBookManager() 
bookManager.HideMsg() 
``` 

- Notes 
- Even if the current global message is displayed for less than 2 seconds, calling this method can directly hide it. 

### AddPageType 

- Description 

Register a custom page 

- Parameters 

| Parameter name | Data type | Description | 
| -------- | -------- | -------------------- |

| pageName | str | Name of the custom page | 
| pageCls | classobj | Class corresponding to the custom page | 

- Return value 

None 

- Example 

See the code **behavior_pack/tutorialScripts/tutorialClientSystem.py** in [CustomBookMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBookMod). Here, several custom page classes are written and the page names are registered for them. This name will be used when writing the book json page. For details, see [json usage page](01-Custom Basic Book.md#Page Writing). 

**TutorialClientSystem.py** 

```python 
# MyNoTitlePage is a custom page class 
from tutorialScripts.pages.myNoTitlePage import MyNoTitlePage 
# Register the name "CustomMod:MyNoTitlePage" for MyNoTitlePage, which will be used as the key value in the page json 
bookManager.AddPageType("CustomMod:MyNoTitlePage", MyNoTitlePage) 
``` 

**behavior_pack/customBooks/customBook/entry/myNoTitlePage.json** The corresponding code, the **type** attribute corresponds to the page name registered above. 

```json 
{ 
"type": "CustomMod:MyNoTitlePage", 
"testTitle": "Title text", 
"image": "textures/ui/myCustomBook/testImage", 
"content1": "First paragraph of text", 
"content2": "Second paragraph of text" 
} 
``` 

- Notes 

- This function can only be called when **ClientSystem** is initialized, otherwise it will not take effect. 
- In order to avoid the page having the same name as other Mod pages or system preset pages, it is recommended that developers use the format of Mod name + ":" + page name to name your page. If a duplicate name occurs, the registration will not be successful and the system will report a corresponding error message. 
- If the naming rules are met, the customized page can be used by other Mod developers, not limited to one book. 

### UpdateScreen 

- Description 

Refresh the book interface 

- Parameters 

None 

- Return value 


None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookManager = clientApi.GetBookManager() 
bookManager.UpdateScreen() 
``` 

- Note 

- This function essentially calls the **UpdateScreen** method of the ScreenNode of the book interface. 

### To<span id="To"></span> 

- Description 

Jump to the book page according to the provided book page address 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | -------- | ------------------------------------------------------------ | 
| addr | str | Book page address. The page jump mechanism of the custom book is similar to the address navigation of the browser. For details, see [Page Jump Mechanism](#Page Jump Mechanism) | 

- Return value 

| Data type | Description | 
| ----------------------- | ------------ | 
| [PageGroup](#PageGroup) | Page group to jump to | 

- Example 

As can be seen in the code of the custom page **behavior_pack/tutorialScripts/pages/addrPage.py** in [CustomBookMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBookMod), the function implemented here is to jump to the specified page of the specified chapter after clicking the button. 

```python 
def GoToPage(self, addr): 
# Get the management object of all books 
bookManager = clientApi.GetBookManager() 
# Jump to address 
bookManager.To(addr) 
``` 

Notes 

- You can only jump in the open book. You cannot jump from a page in one book to a page in another book. Other jumps are allowed, such as jumping within the same chapter, jumping from a chapter to the directory, etc. 
- Only when a jump occurs (when the function is called), you can click the "**Back"** button to return (which is similar to the back function in the browser). Common operations from the home page of the book to the home page of the catalog, and from the home page of the catalog to the chapter are all jumps, so when you return, you will return to the state before the jump, and the **"Previous Page" button** and the **"Next Page" button** are not jump operations. For details, please refer to [Page Jump Mechanism](#Page Jump Mechanism). 

### Get component class <span id="Get component class"></span>


- Description 

This type of method is used to obtain the basic component and the component class of the class preset. The format is "Get" + component class name + "Cls", and there are no parameters. 

- Interface 

| Function name | Return value | Description | 
| --------------------- | --------------------- | -------------------------------- | 
| GetBaseCompCls | type(BaseComp) | Get the base class of the component class | 
| GetButtonCompCls | type(ButtonComp) | Get the preset component ButtonComp class | 
| GetEntityCompCls | type(EntityComp) | Get the preset component Entity class | 
| GetHighlightCompCls | type(HighlightComp) | Get the preset component HighlightComp class | 
| GetImageCompCls | type(ImageComp) | Get the preset component ImageComp class | 
| GetTextCompCls | type(TextComp) | Get the preset component TextComp class | 
| GetProgressBarCompCls | type(ProgressBarComp) | Get the preset component ProgressBarComp class | 

- Example 

Because the usage is the same, here is just an example. For more specific usage, please refer to the custom page section of [CustomBookMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBookMod) 

```python 
import mod.client.extraClientApi as clientApi 
# Get the book management object, see "05-Common Script Objects" for detailed usage 
bookManager = clientApi.GetBookManager() 
# Get the book configuration constants, see "05-Common Script Objects" for detailed API 
bcf = bookManager.GetBookConfig() 
# Get the preset page class TitlePage 
TitlePage = bookManager.GetTitlePageCls() 
# Get the preset component class TextComp 
TextComp = bookManager.GetTextCompCls() 
# Get the preset component class ImageComp 
ImageComp = bookManager.GetImageCompCls() 

# A custom Page 
class MyTitlePage(TitlePage): 
def __init__(self, size = None, position = None): 
# Call the method of the same name in the parent class, TitlePage will automatically add the title component and provide methods for injecting data into the title component and the layout method. 
TitlePage.__init__(self, size, position) 
self.content1 = TextComp(bcf.TextAlign.Left) 
self.image = ImageComp() 
self.content2 = TextComp(bcf.TextAlign.Left) 
self.AddComps(self.content1, self.image, self.content2) 
``` 

### Get the page class <span id="Get the page class"></span> 

- Description 

This type of method is to get the basic page and the preset page class, the format is "Get" + page class name + "Cls", all without parameters


- Interface 

| Function Name | Return Value | Description | 
| -------------- | --------------- | -------------------------- | 
| GetBasePageCls | type(BasePage) | Get the base class of the page class | 
| GetTitlePageCls | type(TitlePage) | Get the preset page TitlePage class | 

- Example 

For examples, see [Get Component Class](#Get Component Class) 

## 4.NormalBook<span id="NormalBook"></span> 

This object manages **books that have been successfully created**. This object is a global singleton object and can be obtained through the API. 

```python 
import mod.client.extraClientApi as clientApi 
bookManager = clientApi.GetBookManager() 
# There are two ways to get it. One is to get it through the book being opened, call GetOpeningBookInstance, and the other is to get it through the book name, call GetBookInstance 
bookInstance = bookManager.GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
``` 

### GetOriginJsonData 

- Description 

Get the **unprocessed** data passed from the book **json** file. If you want to get the **currently modified** data, you can call **GetCurrentJsonData** 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | -------------------------- | 
| dict | Data passed from the book json file | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
originData = bookInstance.GetOriginJsonData() # Get the original json data 
``` 

- Notes


- The book system will preprocess the data when passing it to the page and components (such as configuring default values, etc.), so the data passed in is not consistent with the data defined in the original json. If you want to get the current preprocessed data, you can call **GetCurrentJsonData**. 

### GetCurrentJsonData 

- Description 

Get the modified data from the book's **json** file. If you want to get **unmodified** data, you can call **GetOriginJsonData** 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | -------------------------- | 
| dict | Data from the book's json file | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
currentData = bookInstance.GetCurrentJsonData() # Get the current json data 
``` 

- Notes 

- The book system will preprocess the data when passing it to the page and component (such as configuring default values, etc.), so the data passed in is not consistent with the data defined in the original json. If you want to get **unmodified** data, you can call **GetOriginJsonData** 

### GetBook 

- Description 

Get the page group object where the book homepage is located 

- Return value 

| Data type | Description | 
| ------------- | -------- | 
| [Book](#Book) | Book instance | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance:

bookObj = bookInstance.GetBook() # Get the book page group object of the book 
``` 

### GetCategory 

- Description 

Get the object according to the **identitfier** of the catalog 

- Parameters 

| Parameter name | Data type | Description | 
| ------------------------------------------------- | -------- | ---------------- | 
| [identifier](01-Custom basic book.md#Catalog identifier) | str | Unique identifier of the catalog. | 

- Return value 

| Data type | Description | 
| --------------------- | -------- | 
| [Category](#Category) | Directory instance | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") # For example, get a directory object with an identifier of "pages" 
``` 

### GetEntry 

- Description 

Get the object according to the **identitfier** of the chapter 

- Parameters 

| Parameter name | Data type | Description | 
| ------------------------------------------------- | -------- | ---------------- | 
| [identifier](01-Custom Basic Book.md#Chapter identifier) | str | The unique identifier of the chapter. | 

- Return value 

| Data type | Description | 
| --------------- | -------- | 
| [Entry](#Entry) | Chapter instance | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
entryObj = bookInstance.GetEntry("entityEntry") # For example, get a directory object with an identifier of "entityEntry" 
``` 

### LockCategory 

- Description 

Lock the corresponding directory according to the directory's **identitfier** 

- Parameters 

| Parameter name | Data type | Description | 
| ------------------------------------------------- | -------- | ---------------- | 
| [identifier](01-Custom basic book.md#Directory identifier) | str | Unique identifier of the directory. | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
bookInstance.LockCategory("pages") # For example, lock a directory with an identifier of "pages" 
``` 

### UnlockCategory 

- Description 

Unlock the corresponding directory according to the directory's **identitfier** 

- Parameters 

| Parameter name | Data type | Description | 
| ------------------------------------------------- | -------- | ---------------- | 
| [identifier](01-Custom basic book.md#Directory identifier) | str | The unique identifier of the directory. | 

- Return value 

None 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
bookInstance.UnlockCategory("pages") # For example, unlock a directory with identifier "pages" 
``` 

### LockEntry 

- Description 

Lock the corresponding chapter according to the chapter's **identitfier** 

- Parameters 

| Parameter name | Data type | Description | 
| ------------------------------------------------- | -------- | ---------------- | 
| [identifier](01-Custom basic book.md#Chapter identifier) | str | The unique identifier of the chapter. | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
bookInstance.LockEntry("entityEntry") # For example, lock a chapter with identifier "entityEntry" 
``` 

### UnlockEntry 

- Description 

Unlock the corresponding chapter according to the **identitfier** of the chapter 

- Parameters 

| Parameter name | Data type | Description | 
| ------------------------------------------------- | -------- | ---------------- | 
| [identifier](01-Custom basic book.md#Chapter identifier) | str | The unique identifier of the chapter. | 

- Return value 

None


- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
bookInstance.UnlockEntry("entityEntry") # For example, unlock a chapter with the identifier "entityEntry" 
``` 

## 5.PageGroup<span id="PageGroup"></span> 

This object manages a group of pages, see [Object Analysis](#Object Analysis) for details. Generally, developers will not use this class directly, but use the three inherited classes of this class: **Book, Category, Entry**, so the API here is actually the public API of these three classes. 

### GetAddr 

- Description 

Get the [absolute path](#absolute path) of the page group 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | ------------------ | 
| str | The absolute path corresponding to the page group | 

- Example 

Because **Book**, **Category**, **Entry** all inherit **PageGroup**, here we will take **Category** as an example. 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") # For example, get a directory object with an identifier of "pages" 
if categoryObj: 
print categoryObj.GetAddr() # Output "/customBook/pages" 
``` 

### GetPages 

- Description 

Get all page objects of the page group 

- Parameters


None 

- Return value 

| Data type | Description | 
| -------------- | ---------------- | 
| List[BasePage] | All pages in the page group | 

- Example 

Because **Book**, **Category**, **Entry** all inherit **PageGroup**, here we take **Category** as an example. 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") # For example, get a directory object with an identifier of "pages" 
if categoryObj: 
print categoryObj.GetPages() # Output the page object, you can use the page API method to verify 
``` 

### GetPagesCount 

- Description 

Get the number of pages in the page group 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | ---------------- | 
| int | Number of pages in the page group | 

- Example 

Because **Book**, **Category** and **Entry** both inherit **PageGroup**. Here we take **Category** as an example. 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") # For example, get a directory object with an identifier of "pages" 
if categoryObj: 
print categoryObj.GetPagesCount() # Output "2" 
```


## 6.Book<span id="Book"></span> 

This object inherits **PageGroup**, is a page group that contains the first page of a book, and represents an object of a book. For details, see [Object Analysis](#Object Analysis). 

### GetSons 

- Description 

Get subpage groups (the subpage groups are Category objects) 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------------- | -------------- | 
| list(Category) | First-level directory of books | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
bookObj = bookInstance.GetBook() 
# Get the identifiers of all subpage groups 
print [son.name for son in bookObj.GetSons()] 
``` 

### GetProgressValue 

- Description 

Get the progress of unlocking the sub-page group, commonly used for progress bar display 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | ------------------------------------------------------------ | 
| float | The progress of unlocking the current sub-page group, the range is [**0, 1**], **0** means **0%**, **1** means **100%** | 

- Example 


```python 
# For example, get the current unlock progress of the book. If there are two unlocked first-level subdirectories under the book, the unlock progress is 100%. If one is unlocked and the other is not unlocked, it is 50%. 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
bookObj = bookInstance.GetBook() 
# Get progress 
progressValue = bookObj.GetProgressValue() 
print progressValue 
``` 

## 7.Category<span id="Category"></span> 

This object inherits **PageGroup**, is a page group containing the homepage of the directory, and represents an object of a directory. For details, see [Object Analysis](#Object Analysis). 

### GetSons 

- Description 

Get subpage groups (the subpage groups can be Category objects or Entry objects, because directories can be nested, see [Directory Nesting](01-Custom Basic Books.md#Directory Nesting).) 

- Parameters 

None 

- Return value 

| Data type | Description | 
| --------- | ---------------------------- | 
| PageGroup | Subdirectory or chapter object under this directory | 

- Notes 

- **Category** supports nesting, and its subpage group objects can be **Category** or **Entry** 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") # For example, get a directory object with identifier "pages" 
if categoryObj: 
# Get the identifiers of all child page groups (either all Category objects or all Entry objects) 
print [son.name for son in categoryObj.GetSons()] 
``` 

### GetParent 

- Description


  Get its parent page group (its parent page group can be a Category object or a Book object, because directories are allowed to be nested, see [Directory Nesting](01-Custom Basic Books.md#Directory Nesting).) 

- Parameters 

None 

- Return value 

| Data type | Description | 
| --------- | ---------- | 
| PageGroup | Parent page group object | 

- Notes 

- **Category** supports nesting, its parent page group object can be **Category** or **Book** 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
# For example, get a directory object with an identifier of "pages", and its parent page group is the Book object "customBook" 
categoryObj_1 = bookInstance.GetCategory("pages") 
# For example, get a directory object with identifier "subcategory1", whose parent page group is the Category object "subcategoryTest", this is a nested example 
categoryObj_2 = bookInstance.GetCategory("subcategory1") 
if categoryObj_1: 
print categoryObj_1.GetParent().name # Output "customBook" 
if categoryObj_2: 
print categoryObj_2.GetParent().name # Output "subcategory" 
``` 

### isLocked 

- Description 

Returns the unlock status of the directory 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | --------------------------------- | 
| bool | True means unlocked, False means unlocked | 

- Example


  ```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") # For example, get a directory object with an identifier of "pages" 
if categoryObj: 
print categoryObj.isLocked() 
``` 

### Lock 

- Description 

Lock the directory 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") 
if categoryObj: 
# Lock the directory with identifier "pages" 
categoryObj.Lock() 
``` 

### Unlock 

- Description 

Unlock the directory 

- Parameters 

None 

- Return value 

None 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") 
if categoryObj: 
# Unlock the directory with identifier "pages" 
categoryObj.Unlock() 
``` 

### GetProgressValue 

- Description 

Get the progress of sub-page group unlocking, commonly used for progress bar display 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | ------------------------------------------------------------ | 
| float | The progress of the current sub-page group unlocking, the range is [**0, 1**], **0** means **0%**, **1** means **100%** | 

- Example 

```python 
# For example, get the current unlock progress of the book. If there are two unlocked first-level subdirectories under the book, then the unlock progress is 100%. If one is unlocked and the other is not unlocked, it is 50%. 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
categoryObj = bookInstance.GetCategory("pages") 
if categoryObj: 
# Get the unlock progress of the directory with identifier "pages" 
progressValue = categoryObj.GetProgressValue() 
print progressValue 
``` 

## 8.Entry<span id="Entry"></span> 

This object inherits the page group of **PageGroup** and represents an object of a chapter. For details, see [Object Analysis](#Object Analysis). 

### GetParent 

- Description 


Get its parent page group (its parent page group is Category object) 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | -------------------- | 
| Category | The directory object to which this chapter belongs | 

- Notes 

- **Entry** cannot be nested, its parent page group object can only be **Category** 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
entryObj = bookInstance.GetEntry("entityEntry") # For example, get a directory object with an identifier of "entityEntry" 
if entryObj: 
print entryObj.GetParent().name # Its parent page group is "pages" 
``` 

### isLocked 

- Description 

Returns the unlock status of the chapter 

- Parameters 

None 

- Return value 

| Data type | Description | 
| -------- | --------------------------------- | 
| bool | True means unlocked, False means unlocked | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
entryObj = bookInstance.GetEntry("entityEntry") # For example, get a directory object with an identifier of "entityEntry"

if entryObj: 
print entryObj.isLocked() 
``` 

### Lock 

- Description 

Lock this chapter 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance: 
entryObj = bookInstance.GetEntry("entityEntry") 
if entryObj: 
# Lock the directory with identifier "entityEntry" 
entryObj.Lock() 
``` 

### Unlock 

- Description 

Unlock this chapter 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
bookInstance = clientApi.GetBookManager().GetBookInstance("customBook") # Get the book management object with the book name "customBook" 
if bookInstance:

entryObj = bookInstance.GetEntry("entityEntry") 
if entryObj: 
# Unlock the directory with identifier "entityEntry" 
entryObj.Unlock() 
``` 

