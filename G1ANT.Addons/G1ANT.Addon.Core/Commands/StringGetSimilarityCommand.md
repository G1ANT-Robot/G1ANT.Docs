# string.getsimilarity

## Syntax

```G1ANT
string.getsimilarity phrase1 ⟦text⟧ phrase2 ⟦text⟧ ignorecase ⟦bool⟧ normalize ⟦bool⟧
```

## Description

This command calculates a percentage similarity of two words based on the [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance).

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`phrase1`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | First phrase to be compared |
|`phrase2`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Second phrase to be compared |
|`ignorecase`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | true | Determines whether to ignore case |
|`normalize`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | true | Normalizes phrases before comparison by replacing diacritic characters with their Latin equivalents |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

The example below shows the results of two comparisons: two identical phrases give 100 percent of similarity, so *100* is displayed in the first dialog box, whereas in the second case the similarity drops to 62 percent:

```G1ANT
string.getsimilarity phrase1 robot phrase2 robot
dialog ♥result
string.getsimilarity phrase1 robot phrase2 robotize
dialog ♥result
```
