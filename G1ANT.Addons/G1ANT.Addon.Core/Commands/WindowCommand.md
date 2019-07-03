# window

## Syntax

```G1ANT
window title ⟦text⟧ style ⟦text⟧
```

## Description

This command brings the specified window to the front and activates it.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`title`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no|  | Title of a window to activate. It can be obtained from `Tools/Windows` menu or with **Ctrl+W** keyboard shortcut |
|`style`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no| normal | Action to perform on the style of a window: `maximize`, `minimize` or `normal` (restore from minimized or maximized state) |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutwindow](../Variables/TimeoutWindowVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

In order to see titles of all opened windows, use [All Windows](../../../g1ant.robot-window/auxiliary-windows/all-windows.md) tool.

## Example

In this example Notepad is launched and then Calculator. In order to bring Notepad to the foreground again, you can use different variations of “Notepad” word inclusion with the [search place](../../../appendices/special-characters/search-place.md) character (`✱`), because the window title of this application always includes its name, as it’s the case with many other apps.

> **Note:** Windows titles may differ depending on your system’s language version.

```G1ANT
program notepad
program calc
window ✱Notepad style maximized
```


