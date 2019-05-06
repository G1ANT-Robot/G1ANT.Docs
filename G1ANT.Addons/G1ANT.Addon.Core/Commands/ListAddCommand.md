# list.add

## Syntax

```G1ANT
list.add list ⟦list⟧ toadd ⟦undefined⟧
```

## Description

This command creates a new list by adding an element or a list to the existing one.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`list`| [list](G1ANT.Language/G1ANT.Language/Structures/ListStructure.md) | yes | | First list to be added |
|`toadd`|  | yes |  | An element or a list to be added |
| `result`       | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

This example adds two lists using the `list.add` command. First, two lists are created, and then, with the `list.add` command, they are added together. The resulting list is displayed with the `dialog` command.

>**Note:** As a result of the `list.add` command, the original list (`♥list1`) is modified as well, and becomes equal to the variable specified by the `result` argument (which is the default `♥result` variable in case of this example).

```G1ANT
♥list1 = foo1❚foo2❚foo3❚123❚45
♥list2 = a❚b❚c
list.add list ♥list1 toadd ♥list2
dialog ♥result
```

