﻿# sap.gettext

## Syntax

```G1ANT
sap.settext component ⟦sapcomponent⟧ text ⟦text⟧
```

## Description
Set value of `Text` property of component. Same as `♥component⟦text⟧ = ‴newTextValue‴`, where `♥component` contains `sapcomponent` structure.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `component`    | [sapcomponent](../../../Structures/SapComponentStructure.md)       | **yes**  |                | The component which `Text` property will be set. |
| `text`          | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | Value to be set as `Text` property of component. If component does not handle `Text` setter it will raise an error (all components that derive only from `GuiComponent` (i.e. `GuiApplication`, `GuiConnection`, `GuiSessionModel`), `GuiScrollbar`, `GuiTableRow`, `GuiTreeNode`). |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)  | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.
