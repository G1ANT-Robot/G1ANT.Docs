# text.write

## Syntax

```G1ANT
text.write text ⟦text⟧ filename ⟦text⟧ encodingculture ⟦text⟧ writemode ⟦text⟧
```

## Description

This command writes the specified text directly to a file.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`text`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes|  | Text or a variable with the content to be written |
|`filename`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Path to a file where the text should be written to |
|`encodingculture`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Specifies the file's coding page. If not specified, UTF8 Encoding will be used |
|`writemode`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Specifies writing mode: `append`, `createonly`, `override` |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

The simple script below writes “Lorem Ipsum” in a new line (using C# snippet: `⊂"\r\n"⊃`) of an existing file (the `writemode append` argument). If you wanted to replace the file with new content, you should use the  `writemode override` argument.

```G1ANT
text.write ‴⊂"\r\n"⊃Lorem Ipsum‴ filename C:\tests\test.txt writemode append
```
