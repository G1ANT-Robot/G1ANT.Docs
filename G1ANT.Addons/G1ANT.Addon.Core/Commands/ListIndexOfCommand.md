# list.indexof

## Syntax

```G1ANT
list.indexof list ⟦list⟧ value ⟦undefined⟧
```

## Description

This command returns an index of a specified value in the provided list.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`list`| [list](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ListStructure.md)) | yes | | A list variable to be searched |
|`value`|    | yes |  | Value or a variable to be searched for in a list |
|`alloccurances`| [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no | false | If set to `true`, the command will return all indexes of the specified value; if set to false, the command will return only the first occurrence |
| `result`       | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md)) | no       | [♥timeoutcommand](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md)) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md)) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md)) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

## Example 1

```G1ANT
♥nameList = John❚Samantha❚Adam❚Eve❚Michael
♥name = Samantha
list.indexof list ♥nameList value ♥name result ♥index
dialog ♥index
```

In the script above, the robot looks for the name *Samantha* (stored in the `♥name` variable) in the list of names stored in the `♥nameList` variable. The search result is saved in the `♥index` variable and then displayed in a dialog box. In this case, the result will be 2, since *Samantha* is the second element in the list.

## Example 2

Here the robot will display `2❚4`, because the word *Apples* is the second and the fourth element in the list. If you set the `alloccurances` argument to `false` (or omit it altogether as it’s a default value), the robot will return only the first occurrence of the searched value.

```G1ANT
♥foodList = Carrots❚Apples❚Oranges❚Apples❚Avocados
list.indexof list ♥foodList value Apples alloccurances true result ♥index
dialog ♥index
```


