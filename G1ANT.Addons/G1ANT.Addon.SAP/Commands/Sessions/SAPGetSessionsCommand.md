# sap.getchildren

## Syntax

```G1ANT
sap.getsessions
```

## Description
Gets list of all sessions from the current connection.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `result`        | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) structure of [`sapcomponent`](../../../Structures/SapComponentStructure.md) structure with sessions) |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)   | no      | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.


## Result
Gets the list of all sessions from current connection in a form of a [list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) 
structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structures containing `GuiSession` components.
If nothing is found returned list will be empty.

##### Example
One of elements of returned list (session object serialized to json):
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


##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can see all the details
of all sessions on the `SAP UI object tree`.
Also, you can view details of specific session on `Variables` panel if you assign
a session from the session list to a variable.