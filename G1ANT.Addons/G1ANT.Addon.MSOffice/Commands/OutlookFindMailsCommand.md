# outlook.findmails

## Syntax

```G1ANT
outlook.findmails search ⟦text⟧ showmail ⟦bool⟧
```

## Description

This command searches subjects of Inbox messages and returns all emails that contain a required keyword.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`search`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | | Word to be searched for in a message subject |
|`showmail`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | false | If set to `true`, G1ANT.Robot will show all emails meeting the criteria |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

```G1ANT
outlook.open
outlook.findmails search G1ANT showmail false result ♥result
dialog ♥result
```

In this example *true* will be displayed in a dialog box if the robot finds an email with the word *G1ANT* in its subject. If it doesn’t, *false* will be displayed.

