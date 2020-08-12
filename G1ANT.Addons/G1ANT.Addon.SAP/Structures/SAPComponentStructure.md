# SapComponent
This structure stores information about SAP objects (i.e. UI components), including their paths and is used by the `sap.`
family of commands.

The path and other component's information can be obtained from G1ANT.Addon.SAP’s SAP UI Objects Tree panel
(download addon G1ANT.Addon.SAP and select `SAP UI Objects Tree` from `View` menu): expand
the tree of a given application window, navigate to a desired element and double-click it.
Its path will be automatically inserted into the script. You can also copy any property from
detailed object data under the tree (select it and press Ctrl+C).

## Accessing components
You can access your desired SAP component in multiple ways.

The easiest is casting the component path to the structure:
```g1ant
♥component = ⟦sapcomponent⟧‴box[0]/btn‴
```

You can directly use path (without casting to `sapcomponent`) wherever component is required as argument of command:
```g1ant
sap.click ‴box[0]/btn‴
-or
sap.getchildren ‴box[0]/btn‴ result ♥children
```


Another way is using [sap.find](../Commands/Controls/SAPFindCommand.md) command:
```g1ant
sap.find ‴box[0]\btn‴ result ♥component
```

You can also search for component by its non-unique name with [sap.find](../Commands/Controls/SAPFindByNameCommand.md) command:
```g1ant
sap.findbyname ‴btn‴ type ‴GuiButton‴ result ♥componentList
♥component = ♥componentList⟦1⟧
```
Of course before accessing first element make sure that any component was found by checking number of elements of the list.


Remember to connect to SAP (see [sap.start](../Commands/Application/SAPStartCommand.md) and
[sap.connect](../Commands/Connections/SAPConnectCommand.md)) before referencing any component.


If component allows clicking, you can call in next line (after finding the component):
```g1ant
sap.click ♥component
```
or read component `text` property
```g1ant
dialog ♥component⟦text⟧
```


## Properties

The list of properties depends on the component contained by sapcomponent structure.
Shared (derived from GuiComponent) properties are:

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Name`          | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Non-unique name of the component, which in most cases is a last part of its id and path. |
| `Type`          | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Name of type of the component (i.e. GuiCheckBox, GuiToolbar, GuiApplication). |
| `TypeAsNumber` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Type of the component as numeric value. |
| `Path`          | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Unique path to the component. SAP uses path as unique identifier of components, but calls it the `Id`. Path is composed of non-unique names of parent components and current element name, separated by slashes i.e. `/app/con[0]/ses[0]/wnd[0]/box[0]` (absolute path), `/wnd[0]/box[0]` (session-relative path), `box[0]` (relative path). For clarity reasons this addon contains both `Id` and `Path`, which share exactly the same value. |
| `RelativePath` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Contains path shortened to window-relative path. If resulting path would be empty (i.e. for `/app` or `/wnd[0]`) then it becomes absolute path and starts from `/app`. |
| `Id`            | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Unique identifier of the component, consists from the path to component. Same as `Path`. |
| `Text`          | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Read/write `Text` property of components that are descendants of GuiVComponent. Some components do not implement writing to this property (writing to this property will raise an error), some do not implement reading it (mostly the non-visual ones like application, connection and session; in such case the field will contain an empty string). |
| `IsContainer`  | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if component contains children. |


Almost all visual components implement also following properties (derived from GuiVComponent):

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Tooltip`       | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Tooltip shown over the component when mouse hovers it. Read-only. |
| `IsChangeable` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if component is neither disabled nor read-only. Read-only. |
| `IsModified` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | An object is modified if its state has been changed by the user and this change has not yet been sent to the SAP system. Read-only. |
| `Position` | [rectangle](/G1ANT.Addons/G1ANT.Language/Structures/RectangleStructure.md) | The dimensions and left/top of the component in screen coordinates. Read-only. |
| `ScreenPosition` | [rectangle](/G1ANT.Addons/G1ANT.Language/Structures/RectangleStructure.md) | The dimensions and position of the component in screen coordinates. Read-only. |



### Addditional properties

#### GuiPasswordField, GuiTextField and GuiCTextField

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsNumeric` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | If this flag is set only numbers and special characters may be written into the text field. Read-only. |
| `IsHotspot` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Dynpro elements such as labels may be configured to cause a round trip when they are clicked. In that case the mouse cursor changes to the hand shape. This is called a hot spot. Read-only. |
| `MaxLength` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The maximum length of text that can be written in a text field. Read-only.|
| `IsRequired` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is True if the component is a required value for the screen. Read-only. |
| `IsHighlighted` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the Highlighted flag is set in the screen painter. Read-only. |
| `IsOField` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Marks that component is the Output Field. These fields can be set programmatically to a value at runtime. In this respect they differ from labels. However they cannot be used to enter data, so they are not input fields. Read-only. |
| `DisplayedText` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The text as it is displayed on the screen, including preceding or trailing blanks. Read-only. |



#### GuiRadioButton

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Selected` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if component is selected. Read-write. |
| `IsFlushing` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Some components such as radio buttons or checkboxes may cause a round trip when their value is changed. If this is the case, the Flushing property is True. Read-only. |
| `GroupCount` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The number of radio buttons in the same group the current object belongs to. Read-only. |
| `GroupPos` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Read-only. |
| `GroupMembers` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The collection of GuiRadioButton objects belonging to the same radio button group. Read-only. |



#### GuiCheckBox

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Selected` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if component is selected. Read-write. |
| `IsFlushing` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Some components such as radio buttons or checkboxes may cause a round trip when their value is changed. If this is the case, the Flushing property is True. Read-only. |
| `RowText` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Available only in ABAP list screens. Returns the text of the line containing the current component. Read-only. |



#### GuiTableColumn

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Selected` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is true if the column is selected. Read-write. |
| `IsFixed`  | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Some columns may be fixed, which means that they will not be scrolled with the rest of the columns. Read-write. |
| `Title`    | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | This is the caption of the column. Read-only. |
| `Width`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Width of the column. Read-only. |
| `Count`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the column. Read-only. |
| `Length`   | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the column. Read-only. |



#### GuiTableRow

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Selected`   | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is true if the row is selected. Read-write. |
| `Selectable` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is true if the row can be selected. Read-only. |
| `Count`      | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the row. Read-only. |
| `Length`     | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the row. Read-only. |


#### GuiTableControl

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `ColSelectMode` | GuiTableSelectionType | There are three different modes for selecting columns or rows: <table><thead><tr><th>Value</th><th>Description</th></tr></thead><tr><td>2</td><td>Several columns/rows can be selected.</td></tr><tr><td>0</td><td>No selection possible.</td></tr><tr><td>1</td><td>One column/row can be selected.</td></tr></table> Read-only. |
| `RowSelectMode` | GuiTableSelectionType | Same as `ColSelectMode`. |
| `CurrentColumnIndex` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Zero-based index of the current column. Read-only. |
| `CurrentRowIndex` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Zero-based index of the current row. Read-only. |
| `HorizontalScrollbar` | GuiScrollbarModel | The horizontal scrollbar of the table control. Read-only. |
| `VerticalScrollbar` | GuiScrollbarModel | The vertical scrollbar of the table control. Read-only. |
| `RowCount` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of rows in the table. This includes invisible rows. For the number of visible rows the property VisibleRowCount is available. Read-only. |
| `VisibleRowCount` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of visible rows in the table. Read-only. |




#### GuiTabStrip

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `SelectedTab` | GuiTab | The selected tab is the one whose descendants are currently visualized. The selected tab has exactly one child, which is a GuiScrollContainer. Read-only. |
| `LeftTab` | GuiTab | This is the left most tab whose caption is visible. Read-only. |



#### GuiLabel

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsListElement` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is True if the element is on an ABAP list, not a dynpro screen. Read-only. |
| `MaxLength` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The maximum text length of a label is counted in code units. On non-Unicode clients these are equivalent to bytes. Read-only. |
| `IsNumeric` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This flag is True if the label may only contain numbers. Read-only. |
| `CaretPosition` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Setting the caret position within a label is possible even though it is not visualized as a caret by SAP GUI. However, the position is transmitted to the server, so ABAP application logic may depend on this position. Read-write. |
| `DisplayedText` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Contains the text as it is displayed on the screen, including preceding or trailing blanks. Read-only. |
| `RowText` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Available only in ABAP list screens. Returns the text of the line containing the current component. Read-only. |



#### GuiComboBox

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `CurrentEntry` | GuiComboBoxEntryModel | The currently focused entry of the dropdown list. Read-only. |
| `Key` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | This is the key of the currently selected item. Read-write. |
| `Value` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | This is the value of the currently selected item. Read-write. |
| `IsShowKey` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is True if the combo box shows both keys and values. Read-only. |
| `IsFlushing` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Some components such as radio buttons, checkboxes or combo boxes may cause a round trip when their value is changed. If this is the case, the Flushing property is True. Read-only. |
| `IsHighlighted` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the Highlighted flag is set in the screen painter. Read-only. |
| `IsListBoxActive` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property is True if the list box of the combo box is currently open. Read-only. |



#### GuiOkCodeField

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsOpenedsShowKey` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | False if the GuiOkCodeField is collapsed. Read-only. |



#### GuiButton
Prefix is `btn`.

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `LeftLabel` | ISAPComponent | Left label of the GuiButton. Read-only. |
| `RightLabel` | ISAPComponent | Right label of the GuiButton. Read-only. |



#### GuiApplication
Represents SAP Logon app.
Prefix is `app`.

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `AllowSystemMessages` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | System messages are displayed when an administrator invokes them on the server to send a notification to users currently logged in. This may happen at any time and interfere with the recording or playback of a script. Setting this property to FALSE will prevent system messages from being displayed. Read-write. |
| `ToolbarVisible` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Visibility of system toolbar of the main window for newly opened connections. Read-write. |
| `StatusbarVisible` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Visibility of the status bar of the main window for newly opened connections. Read-write. |
| `ButtonbarVisible` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Visibility of the button bar of the main window for newly opened connections. Read-write. |
| `TitlebarVisible` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Visibility of the title bar of the main window for newly opened connections. Read-write. |
| `Inplace` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Turns inplace mode on or off. Read-write. |
| `Version` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Version of SAP. Read-only. |
| `NewVisualDesign` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True for New Visual Design, false for Classic mode used for the user interface. Read-only. |
| `HistoryEnabled` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The local history function can be enabled or disabled using this property. Disabling it will significantly improve the performance of SAP GUI, which may be crucial during load tests. Read-write. |
| `Utils` | GuiUtils | Returns GuiUtils object, which contains methods to write to files and show messages. Read-only. |
| `ConnectionErrorText` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | This property contains the text of a connection error message. If [sap.connect](../Commands/Connections/SAPConnectCommand.md) fails, you can retrieve information about the cause of the failure from this property. Read-only. |
| `ActiveSession` | GuiSession | Returns the Session that the user is currently working with, which will be the topmost window. Read-only. |

##### Example
Example application object serialized to json returned by `⟦sapcomponent⟧/app`
```json
{
  "AllowSystemMessages": true,
  "ToolbarVisible": true,
  "StatusbarVisible": true,
  "ButtonbarVisible": true,
  "TitlebarVisible": true,
  "Inplace": false,
  "Version": {
    "Major": 7500,
    "Minor": 257,
    "Build": 9,
    "Revision": 0,
    "MajorRevision": 0,
    "MinorRevision": 1
  },
  "NewVisualDesign": true,
  "Utils": {},
  "HistoryEnabled": true,
  "ConnectionErrorText": "",
  "ActiveSession": null,
  "Name": "app",
  "Type": "GuiApplication",
  "TypeAsNumber": 10,
  "Path": "/app",
  "RelativePath": "/app",
  "Id": "/app",
  "Text": "",
  "IsContainer": true
}
```


#### GuiConnection

Represents the connection between SAP GUI and an application server, so it might be understood
as a SAP window. Opening a connection (`/app/con[#]`) starts new session (`/app/con[#]/ses[#]`)
and opens a window (`/app/con[#]/ses[#]/wnd[#]`).
Prefix is `con`.

| Property name    | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Description` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | This description is only available if the connection was started either from SAP Logon or using `sap.connect`. The description can then be used when calling the `sap.connect` method. Read-only. |
| `IsDisabledByServer` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | Read-only. |
| `ConnectionString` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | Read-only. |


##### Example
Example connection object returned by `⟦sapcomponent⟧/app/con[0]` serialized to json:
```json
{
  "Description": "2. My form",
  "IsDisabledByServer": "false",
  "ConnectionString": "/SAP_CODEPAGE=1100 /FULLMENU SNC_PARTNERNAME="" SNC_QOP=-1 /H/172.16.64.17/S/3200",
  "Name": "con[0]",
  "Type": "GuiConnection",
  "TypeAsNumber": 11,
  "Path": "/app/con[0]",
  "RelativePath": "/app/con[0]",
  "Id": "/app/con[0]",
  "Text": "",
  "IsContainer": true
}
```



#### GuiSession
Prefix is `ses`.

| Property name    | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsActive`     | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the session window is active. Read-only. |
| `IsBusy`        | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | If this property is true, then a subsequent Scripting call will wait for the current job to be finished. Read-only. |
| `IsTestToolMode` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | If set to true then a special mode is applied: information (I) and abort (A) messages are no more displayed as pop-up windows; the update mode of the application server is changed to immediate mode for the connection; system messages are ignored so that they do not interrupt scripts. Read-only. See also `GuiApplication.AllowSystemMessages`. |
| `ProgressPercent` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/integerStructure.md) | The percentage displayed by the SAP GUI progress indicator. Read-only. |
| `ProgressText` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The text displayed by the progress indicator. Read-only. |
| `Info`          | `GuiSessionInfo` | Technical information about the current connection, the login data, the running SAP application and more. Read-only. See description below for details. |

##### Example
Example session object returned by `⟦sapcomponent⟧/app/con[0]/ses[0]` serialized to json:
```json
{
  "IsBusy": false,
  "IsActive": false,
  "IsTestToolMode": false,
  "ProgressPercent": 0,
  "ProgressText": "",
  "Info": {
    "ApplicationServer": "XXXXXXXXXX06",
    "Client": "100",
    "MessageServer": "",
    "Program": "SAPMV45A",
    "SessionNumber": 1,
    "SystemSessionId": "0050529251611E7AB84544E7FF7C3101",
    "Transaction": "VX01",
    "User": "xxxx",
    "Group": "",
    "Codepage": 4110,
    "GuiCodepage": 4110,
    "IsI18NMode": false,
    "Language": "PL",
    "InterpretationTimeMilliseconds": 594,
    "ResponseTimeMilliseconds": 812,
    "RoundTrips": 3,
    "ScriptingModeReadOnly": false,
    "ScriptingModeRecordingDisabled": false,
    "DoesFlush": true,
    "IsLowSpeedConnection": false,
    "ScreenNumber": 9999,
    "SystemName": "XXX",
    "SystemNumber": 10
  },
  "Name": "ses[0]",
  "Type": "GuiSession",
  "TypeAsNumber": 12,
  "Path": "/app/con[0]/ses[0]",
  "RelativePath": "/app/con[0]/ses[0]",
  "Id": "/app/con[0]/ses[0]",
  "Text": "",
  "IsContainer": true
}
```

#### GuiSessionInfo

| Property name    | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `ApplicationServer` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The name of the application server is set only if the session belongs to a connection that was started without load balancing, by specifying an application server. Read-only. |
| `Client` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The client selected on the login screen. Read-only. |
| `MessageServer` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The message server information is available only if the session belongs to a connection which was started using load balancing. Read-only. |
| `Program` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The name of the source program that is currently being executed. Read-only. |
| `SessionNumber` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The number of the session is also displayed in SAP GUI on the status bar. Read-only. |
| `SystemSessionId` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | All SAP GUI sessions of the same connection are represented on the server with the same SystemSessionId. Using SystemSessionId and SessionNumber to match SAP GUI session. Read-only. |
| `Transaction` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The transaction that is currently being executed. Read-only. |
| `User` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The SAP name of the user logged into the system. Read-only. |
| `Group` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The login group information (available only if the session belongs to a connection which was started using load balancing). Read-only. |
| `Codepage` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The codepage specified in SAP Logon in the properties of the connection. Read-only. |
| `GuiCodepage` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | A list of codepages is available in table TCP00A of the SAP system. I.e. for codepage 1252 (Latin I) the property guiCodepage is 1160. Read-only. |
| `IsI18NMode` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The I18N mode of SAP GUI is required for multi-byte character sets. Read-only. |
| `Language` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The language specified on the login screen. Read-only. |
| `InterpretationTimeMilliseconds` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The interpretation time begins after the data have arrived from the server. It comprises the parsing of the data and distribution to the SAP GUI elements. Read-only. |
| `ResponseTimeMilliseconds` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | This is the time that is spent on network communication from the moment data are sent to the server to the moment the server response arrives. Read-only. |
| `RoundTrips` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Before SAP GUI sends data to the server it locks the user interface. In many cases it will not unlock the interface once data arrive from the server, but instead will send a new request to the server immediately. Controls in particular use this technology to load the data they need for visualization. This property contains count of these token switches between SAP GUI and the server. Read-only. |
| `ScriptingModeReadOnly` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The read only mode can be enabled using an application server profile parameter. In this mode the state of SAP applications cannot be changed through the Scripting API, which means:<ul><li>Properties can only be read, but not set</li><li>Functions can only be called if they do not change the control’s state.</li><li>Scripts can be recorded and information about the application can be read from SAP GUI. However a transaction cannot be run from a script.</li></ul> Read-only. |
| `ScriptingModeRecordingDisabled` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The recording disabled mode can be enabled using an application server profile parameter. In this mode SAP GUI Scripting does not fire any events. This implies that user interaction cannot be recorded. However data can be read from SAP GUI and scripts can be used to run transactions. Read-only. |
| `DoesFlush` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | The property flushes counts the number of flushes in the automation queue during server communication. Read-only. |
| `IsLowSpeedConnection` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the connection to which the session belongs runs with the low speed connection flag. This flag can be set on the advanced connection properties page of the SAPLogon dialog. **The SAP GUI Scripting support is very limited for low speed connections**, because information required to identify SAP GUI objects is not being sent. Read-only. |
| `ScreenNumber` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The number of the screen currently displayed. Read-only. |
| `SystemName` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | This is the name of the SAP system. Read-only. |
| `SystemNumber` | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | The system number is set only if the session belongs to a connection that was started without load balancing, by specifying an application server. Read-only. |

##### Note
Please check if you read description of `IsTestToolMode` property; enabling it and disabling 
GuiApplication.AllowSystemMessages might be very useful for automation purposes.



#### GuiFrameWindow, GuiMainWindow, GuiModalWindow
Prefix is `wnd`.

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Handle`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | A handle of the window. Read-only. |

#### GuiModalWindow


| Property name       | Type                                                         | Description                                                  |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsPopupDialog`   | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True for modal window popup dialogs. Read-write. |
| `PopupDialogText` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | The text of the input field of the popup dialog in a concatenated form. Read-write. |



#### GuiShell
`GuiShell` is a tree. Addon API exposes its nodes as children.
Prefix is `shell`.

| Property name     | Type                                                         | Description                                                  |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `SelectionMode` | SelectionMode                                                | Selection mode. Possible values:<table><thead><tr>    <td>Name</td>    <td>Value</td></tr></thead><tr>    <td>SingleNode</td>    <td>0</td></tr><tr>    <td>MultipleNodes</td>    <td>1</td></tr><tr>    <td>SingleItem</td>    <td>2</td></tr><tr>    <td>MultipleItems</td>    <td>3</td></tr></table> Read-only. |
| `TreeType`       | GuiTreeType                                                  | Possible values:<table><thead><tr>    <td>Name</td>    <td>Value</td></tr></thead><tr>    <td>Simple</td>    <td>0</td></tr><tr>    <td>ListTree</td>    <td>1</td></tr><tr>    <td>ColumnTree</td>    <td>2</td></tr></table> Read-only. |
| `Handle`         | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | A handle of the tree. Read-only. |
| `SubType`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Additional type information to identify the control represented by the shell, for example Picture, TextEdit, GridView and so on. Read-only. |
| `NodeKeys`       | TreeNodeKeyModelCollection                                   | Collection of unique keys of tree nodes. Unlike components, which use unique Path (Id), nodes use Keys which are not in a form of a path, but are basically a string containing their absolute position within the tree, i.e. "00000003". Read-only. |

#### GuiTreeNode
Represents a node of `GuiShell`. Its child nodes are represented like any other 
component's children, so you can get the nodes of a tree in a tree structure using
[`sap.getchildren`](../Commands/Controls/SAPGetChildrenCommand.md) command.

| Property name     | Type                                                         | Description                                                  |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Id`            | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | `Id` (`Path`) of parent tree. Read-only. |
| `Key`            | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Unique (within parent tree) key of the node, which is string containing absolute index of a node filled with zeros to the length of 8. Read-only. |
| `RelativePath`  | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Same as `Path`, used only for compatibility with Addon internals. Read-only. |
| `Path`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Backslash-separated path inside the tree built from relative indexes of nodes within their parent nodes. For example `2\1`, which means first child of second root node. Read-only. |
| `Name`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Same as `Key`, used only for compatibility with Addon internals. Read-only. |
| `Text`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Display caption of a node. Read-only. |
| `Level`        | [integer](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Nesting level. Root nodes have `Level` equal to 0. Read-only. |
| `Position` | [rectangle](/G1ANT.Addons/G1ANT.Language/Structures/RectangleStructure.md) | The dimensions and left/top of the component in screen coordinates. Read-only. |
| `ScreenPosition` | [rectangle](/G1ANT.Addons/G1ANT.Language/Structures/RectangleStructure.md) | The dimensions and position of the component in screen coordinates. Read-only. |


> ###### Example
Example tree node object serialized to json returned by [`sap.findtreenode`](../Commands/Controls/Trees/SAPFindTreeNodeCommand.md)
```json
{
  "Key": "00000003",
  "Position": "21, 45, 32, 20",
  "ScreenPosition": "33, 538, 32, 20",
  "Name": "00000003",
  "Type": "GuiTreeNode",
  "TypeAsNumber": -1,
  "Path": "1\2",
  "RelativePath": "1\2",
  "Id": "/app/con[0]/ses[0]/wnd[0]/shell",
  "IsContainer": true
}
```


#### GuiDialogShell

| Property name    | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Title`         | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Title of the dialog. Read-only. |



#### GuiContextMenu
`GuiContextMenu` items can be accessed as children, which are also of type `GuiContextMenu`.
Root-level context menu is just a container, with children being a set of `GuiContextMenu`s.

Component name prefix is `mnu`.

##### Example
If you need to click on an item of context menu:
* get it's child by name or index (i.e. `sap.getchild index 0 parent ♥contextMenu result ♥item`)
* click on it (`sap.click ♥item`).

| Property name    | Type                       | Description                                                  |
| ---------------- | -------------------------- | ------------------------------------------------------------ |
| `Items`         | ContextMenuItemCollection  | Items of context menu. You can access them via `sap.getchild` or `sap.getchildren` commands. Read-only. |



#### GuiMessageWindow

| Property name           | Type                                                         | Description                                                  |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `FocusedButton`       | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Zero-based index of the button that currently has the focus. Read-write. |
| `OKButtonText`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Caption of "OK" button. Read-write. |
| `HelpButtonText`      | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Caption of "Help" button. Read-write. |
| `OKButtonHelpText`   | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | "OK" button help text. Read-write. |
| `HelpButtonHelpText` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | "Help" button help text. Read-write. |
| `MessageType`         | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) |  Type of message. Read-write. |
| `MessageText`         | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Text of message displayed by this window. Read-write. |
| `IsVisible`           | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | True if window is visible. Read-write. |



#### GuiSimpleContainer

| Property name           | Type                                                         | Description                                                  |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsListElement`   | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the element is on an ABAP list, not a dynpro screen. Read-only. |
| `IsStepLoop`       | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the container is a step loop container. Read-only. |
| `LoopColCount`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | If the container is a step loop container, then this property contains the number of columns in the step loop. Read-only. |
| `LoopRowCount`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | If the container is a step loop container, then this property contains the number of rows in the step loop. Read-only. |
| `LoopCurrentCol`  | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | If the container is a step loop container, then this property contains the current row number in the step loop. Read-only. |
| `LoopCurrentRow`  | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | If the container is a step loop container, then this property contains the current column number in the step loop. Read-only. |



#### GuiSplitterContainer

| Property name           | Type                                                         | Description                                                  |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `IsVertical`       | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the splitter cells of the GuiSplitterContainer are vertically aligned, otherwise false. Read-only. |
| `SashPosition`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Contains the position of the splitter sash in characters. Read-write. |



#### GuiUserArea:
 
 Property name             | Type                                                         | Description                                                  |
| ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `VerticalScrollbar`   | GuiScrollbar | Vertical scroll bar. Read-only. |
| `HorizontalScrollbar` | GuiScrollbar | Horizontal scroll bar. Read-only. |
| `CurrentContextMenu`  | GuiContextMenu | Context menu. Read-only. |



#### GuiTableRow
It is not a visual component, so in addition to the properties below it derives only the properties from `GuiComponent`.

| Property name           | Type                                                         | Description                                                  |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Count`       | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the row. Read-only. |
| `Length`      | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the row. Yes. Exactly the same as `Count`. Read-only. |
| `Selected`    | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the row is selected. Read-only. |
| `Selectable` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) | True if the row can be selected. Read-only. |



#### TableCell
Derives all properties from `GuiComponent` and `GuiVComponent`.
Value of cell is stored in `Text` property.
Last position of `Path` (and `Id`) differs from `Name`: it contains prefix related with `Type` property
(i.e. "txt" for "GuiTextField") and suffix with cell coordinates, for example "txtVBAP-POSNR[0,0]".

> ###### Example
Example table cell object serialized to json returned by [sap.gettablecell](../Commands/Controls/Tables/SAPGetTableCellCommand.md)
```json
{
  "Text": "Value",
  "Tooltip": "",
  "IsChangeable": false,
  "IsModified": false,
  "Position": "21, 45, 32, 20",
  "ScreenPosition": "33, 538, 32, 20",
  "Name": "VBAP-POSNR",
  "Type": "GuiTextField",
  "TypeAsNumber": 31,
  "Path": "/app/con[0]/ses[0]/wnd[0]/usr/tabpT\\01/txtVBAP-POSNR[0,0]",
  "RelativePath": "usr/tabpT\\01/txtVBAP-POSNR[0,0]",
  "Id": "/app/con[0]/ses[0]/wnd[0]/usr/tabpT\\01/txtVBAP-POSNR[0,0]",
  "IsContainer": false
}
```



> ## Notes
Materialize you component once, then use it multiple times. COM communication used for exchanging
information with SAP is pretty slow and you don't want to download the same data multiple times.
So instead of
```g1ant
sap.connect index 0
♥sapTablePath = ‴usr/tbl‴
sap.gettablerowcount ♥sapTablePath result ♥tableRowCount
sap.gettablerow ♥sapTablePath index 0 result ♥row
sap.gettablerows ♥sapTablePath result ♥rows
sap.gettablecolumn ♥sapTablePath index 0 result ♥col
sap.gettablecolumns ♥sapTablePath result ♥cols
sap.gettablecell ♥sapTablePath row 0 column 0 result ♥cell
```

use

```g1ant
sap.connect index 0
♥sapTable = ⟦sapcomponent⟧‴usr/tbl‴
sap.gettablerowcount ♥sapTable result ♥tableRowCount
sap.gettablerow ♥sapTable index 0 result ♥row
sap.gettablerows ♥sapTable result ♥rows
sap.gettablecolumn ♥sapTable index 0 result ♥col
sap.gettablecolumns ♥sapTable result ♥cols
sap.gettablecell ♥sapTable row 0 column 0 result ♥cell
```