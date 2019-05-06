# for

## Syntax

```G1ANT
for counter ⟦variable⟧ from ⟦integer⟧ to ⟦integer⟧
end
```

## Description

The `for` command allows to create a loop, which repeats the inner block a specified number of times. The loop ends with the `end` command.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`counter`| [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | yes |  | Name of a variable, which will store a number that changes with every execution of a loop (if it's not an infinite one) |
|`from`| [integer](G1ANT.Language/G1ANT.Language/Structures/IntegerStructure.md) | yes |  | Initial value of the counter variable |
|`to`| [integer](G1ANT.Language/G1ANT.Language/Structures/IntegerStructure.md) | yes |  | End value of the counter (the loop will end when the counter variable exceeds this value) |
|`step`| [integer](G1ANT.Language/G1ANT.Language/Structures/IntegerStructure.md) | no | 1 | Number that is added to the counter variable with every execution of a loop (can be negative to decrease the counter variable) |
| `if`           | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](G1ANT.Manual/appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

In this example the `♥idx` counter variable starts with the value of 1 in the first execution of a loop, then it’s increased to 4, then to 7 and finally reaches 10. All these values are displayed in a dialog box:

```G1ANT
for counter ♥idx from 1 to 10 step 3
   dialog ♥idx
end
```
