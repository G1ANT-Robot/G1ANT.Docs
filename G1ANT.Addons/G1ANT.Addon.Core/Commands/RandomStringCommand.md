# random.string

## Syntax

```G1ANT
random.string length ⟦integer⟧ useletters ⟦bool⟧ usenumbers ⟦bool⟧ usechars ⟦bool⟧ casesensitivity ⟦bool⟧
```

## Description

This command generates a random string of a specified length. The string can be generated using letters (lower- and uppercase), numbers or various characters, and these attributes can be specified by a user.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`length`| [integer](../../G1ANT.Language/Structures/IntegerStructure.md) | yes | | Length of the random generated string |
|`useletters`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no| true | Allows to generate string using letters |
|`usenumbers`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no| true | Allows to generate string using numbers |
|`usechars`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no| false | Allows to generate string using all non-control UTF characters |
|`casesensitivity`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no| false | Allows to generate string using uppercase letters |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the random string will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

This example generates a random string, which is 23 characters long and case sensitive (uses uppercase letters). The result is displayed in a dialog box:

```G1ANT
random.string length 23 casesensitivity true
dialog ♥result
```
