# text.replace

## Syntax

```G1ANT
text.replace text ⟦text⟧ search ⟦text⟧ regex ⟦text⟧ replace ⟦text⟧
```

## Description

This command replaces text with other value and assigns the result to another variable.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`text`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | yes|  | Source text or a variable |
|`search`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no |   | Specifies text to be replaced in the source text |
|`regex`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no|   | Specifies regular expression to be applied for the search in the source text |
|`replace`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | yes|   | Text to be used as a replacement |
| `result`       | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md)) | no       | [♥timeoutcommand](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md)) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md)) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md)) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

## Example 1

This simple script replaces “John” with “Tom” in the source text stored in a variable:

```G1ANT
♥source = Name: John Surname: Smith
text.replace ♥source search John replace Tom result ♥name
dialog ♥name
```

## Example 2

In this example G1ANT.Robot searches for all 3-letter words using regex expression (`\b\w{3}\b`) and then replaces them with the word “fox”.

```G1ANT
♥loremIpsum = It's a fez. I wear a fez now. Fezes are cool. You hit me with a cricket bat. Saving the world with meals on wheels. I hate yogurt. It's just stuff with bits in.
text.replace ♥loremIpsum regex \b\w{3}\b replace fox result ♥new
dialog ♥new
```

