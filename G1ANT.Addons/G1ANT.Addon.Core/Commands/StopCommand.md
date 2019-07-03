# stop

## Syntax

```G1ANT
stop silentmode ⟦bool⟧
```

## Description

The `stop` command stops the process and displays a dialog box message.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`silentmode`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | false | If set to `true`, the command silently stops the script without showing errors; `false` value enables displaying errors |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

This simple loop iterates twice, displaying a dialog box with the current value of the `♥i` variable. But when the variable reaches 3, the process is stopped and an appropriate message is displayed (if you don’t want this message to appear, just use the  `silentmode true` argument for the `stop` command):

```G1ANT
for ♥i from 1 to 5
  stop if ⊂♥i==3⊃
  dialog ♥i
end
```

