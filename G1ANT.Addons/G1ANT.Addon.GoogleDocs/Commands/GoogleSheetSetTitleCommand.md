# googlesheet.settitle

## Syntax

```G1ANT
googlesheet.settitle title ⟦text⟧
```

## Description

This command sets the title of a Google Sheets document.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`title`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | New spreadsheet title |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In this example a Google Sheets document is opened, its title is retrieved and displayed in a dialog box. The title is then changed and retrieved and displayed again to confirm the change succeeded. Finally, the original title is restored and the document is closed:

```G1ANT
googlesheet.open 1gKFnrtZ-kzijNeIpYxln6PZS0z5btyHjoW1vZhCZ58c
googlesheet.gettitle ♥originalTitle
dialog ♥originalTitle
googlesheet.settitle ‴Test title‴
googlesheet.gettitle ♥newTitle
dialog ♥NewTitle
googlesheet.settitle ♥originalTitle
googlesheet.close
```



