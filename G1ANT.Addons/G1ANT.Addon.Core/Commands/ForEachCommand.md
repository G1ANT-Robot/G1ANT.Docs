# foreach

## Syntax

```G1ANT
foreach element ⟦variable⟧ in ⟦list⟧
end
```

## Description

The `foreach` command creates a loop, which repeats the inner block a specified number of times. The loop ends with the `end` command.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`element`| [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | yes |  | Name of a variable, which will store one element at a time from the specified list |
|`in`| [list](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ListStructure.md)) | yes |  | Name of a list, from which all elements will be processed one by one with every execution of a loop |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md)) | no       | [♥timeoutcommand](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md)) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md)) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

## Example

In this example a `♥list` with three elements is declared. The `♥element` variable is initially set to the first element of the list, then to the second and finally to the third. The script will display all values from the `♥list` in consecutive dialog boxes.

```G1ANT
♥list = one❚two❚three
foreach ♥element in ♥list
   dialog ♥element
end
```
