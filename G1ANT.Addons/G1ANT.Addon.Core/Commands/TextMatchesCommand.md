# text.matches

## Syntax

```G1ANT
text.matches text ⟦text⟧ regexes ⟦text⟧
```

## Description

This command gives you a percentage value (0-100) of how much a given text complies with a provided [regex](../../../appendices/regex.md).

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`text`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Text or a variable with the content to be matched against regex |
|`regexes`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Regex to be matched against text input |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

This simple script checks the input text against `\wn.mE` regex, which searches for whole words starting with “n” (case insensitive), then having any character, then “m” and finally “E” (again, case insensitive). Since “Name” matches this regex, it’s a 100 percent match and this value is displayed in a dialog box:

```G1ANT
text.matches ‴Name: John Surname: Smith‴ regexes \wn.mE
dialog ♥result
```

