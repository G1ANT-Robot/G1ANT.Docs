﻿# sap.getparentwindow

## Syntax

```G1ANT
sap.getparentwindow parent ⟦sapcomponent⟧
```

## Description
Get parent window of `component`. All components have parent window except window itself
(`GuiMainWindow`, `GuiFrameWindow`, `GuiModalWindow`), session (`GuiSession`),
connection (`GuiSession`) and application (`GuiApplication`).

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `component`    | [sapcomponent](../../../Structures/SapComponentStructure.md)       | **yes**  |                | The component placed inside SAP window. |
| `result`        | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([sapcomponent](../../Structures/SapComponentStructure.md) structure with component being parent) |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)  | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.

## Result
Returned window contains `Handle` property that contains WinAPI window handle which can be used 
to perform WinaAPI-level operations, i.e. to send input.

You can also send VKeys to the window via [`sap.sendvkey`](../Windows/SAPSendVKeyCommand.md) command (i.e. `0` to simulate
`Enter`).