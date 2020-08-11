# sap.connect

## Syntax

```G1ANT
sap.connect index ⟦text⟧ description ⟦text⟧ connectionstring ⟦text⟧
```

## Description

This command connects to an existing connection or opens a connection with your app (`/app/con[#]`). 
In the second case it also opens a session (`/app/con[#]/ses[#]`) and a (login) window 
(`/app/con[#]/ses[#]/wnd[#]`) which will become your form after login (if neccessary). 
Equivalent of double-click on  your form at the forms list inside SAP Logon.

This command must be executed before most of other SAP commands. Exceptions are the commands 
related with app ([app.start](../Application/SAPStartCommand.md), [app.isrunning](../Application/SAPIsRunningCommand.md))
and [sap.getconnections](SAPGetConnectionsCommand.md).

It will raise an error if SAP or SAP Scripting API are not installed (this component is installed 
by default SAP installation) or SAP Logon application is not running or is not registered
in the Running Object Table table.

It sets current (default) connection (and current session and current window if available) for
created SAP Manager instance, which id is returned and might be used to switch between 
connections/sessions/windows. Default connection/session/window is used if path to SAP component
if relative. Defaults are also used by specific commands like [sap.getactivewindow](../Windows/SAPGetActiveWindowCommand.md).

| Argument              | Type                                                              | Required | Default Value                                                | Description                                                  |
| --------------------- | ----------------------------------------------------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `description`       | [text](../../G1ANT.Language/Structures/TextStructure.md)          | no       |               | Description of active connection to connect to. You can get the list of all active connections with `sap.getconnections` command and take the description from `Description field`. Either `Description`, `ConnectionString` or `Index` has to be set. |
| `connectionstring` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |              | Connection string to open new connection. Either `Description`, `ConnectionString` or `Index` has to be set. |
| `index`              | [integer](../../G1ANT.Language/Structures/IntegerStructure.md)    | no       |               | The index of connection to connect to (starting from 0). You can get the list of all available connections with `sap.getconnections` command. Will raise an error if non-existent index will be used (use `name` parameter if no connection is open to connect a new one). Either `Description`, `ConnectionString` or `Index` has to be set. |
| `result`             | [variable](../../G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`   | Name of a variable where the command's result will be stored ([integer](../../G1ANT.Language/Structures/IntegerStructure.md) structure with instance id for managing/swapping SAP Manager instances) |
| `if`                 | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true         | Executes the command only if a specified condition is true   |
| `timeout`           | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`         | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |              | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`         | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |              | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage`      | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |              | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |              | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

Following script will open start SAP Logon app and try to open form with description TestForm.
Variable ♥managerId will contain id of SAP Manager which can be used with command
[sap.switch](../SAPSwitchCommand.md).

```G1ANT
sap.start
sap.connect description TestForm result ♥managerId
```

> **Note:** One of parameters `description`, `connectionstring` or `index` must be set.

> **See also:** [sap.settesttool](../Sessions/SAPSetTestToolModeCommand.md) to turn off modal messages from SAP.
