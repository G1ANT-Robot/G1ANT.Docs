# text.read

## Syntax

```G1ANT
text.read filename ⟦text⟧ result ⟦variable⟧ encodingculture ⟦text⟧
```

## Description

This command reads the content of a file and assigns it to a variable.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`filename`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | The path to a file with the source content |
| `result`          | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                    | Name of a variable where the file content will be stored     |
|`encodingculture`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Specifies the file's coding page. If not specified, UTF8 Encoding will be used |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In this simple script below the content of the `test.txt` file is read and stored in the `♥read` variable. Then, this content is displayed in a dialog box:

```G1ANT
text.read C:\tests\test.txt result ♥read
dialog ♥read
```

