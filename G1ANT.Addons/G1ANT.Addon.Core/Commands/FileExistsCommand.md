# file.exists

## Syntax

```G1ANT
file.exists filename ⟦text⟧ 
```

## Description

This command determines whether a specified file exists.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`filename`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | yes |  | Path and a name of the expected file |
| `if`           | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](G1ANT.Manual/appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

Using the `timeout`,  `errorcall` and ` errorjump` arguments, you can make the robot wait for a file to appear and in case the file doesn’t show up, other commands can be executed:

```G1ANT
file.exists ♥environment⟦USERPROFILE⟧\Documents\test.txt timeout 1000 errorjump notFound
dialog ‴File exists‴

procedure notFound
    dialog ‴File not found‴
end
```

The robot can also display a simple message, if it can’t find the specified file:

```G1ANT
file.exists C:\\test.txt errormessage ‴Sorry, I could not find file‴
```
