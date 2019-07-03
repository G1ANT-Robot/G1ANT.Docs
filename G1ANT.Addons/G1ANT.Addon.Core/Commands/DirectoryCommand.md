# directory

## Syntax

```G1ANT
directory path ⟦text⟧
```

## Description

This command allows to retrieve directory content and assign it to a variable. 

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`path`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Directory path |
|`pattern`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Allows to filter results, e.g. file extensions, file names etc. Type “directory” to get directories only |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored as [list](../../G1ANT.Language/Structures/ListStructure.md) elements. To calculate the number of list elements, use the `⟦count⟧` index |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../../appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example 1

This example shows how to easily list the contents of a specified directory.  The script searches for robot’s log files starting with *“2019-01”* (the [`♥environment⟦USERPROFILE⟧`](../../../appendices/environment.md) variable reads the path to the current Windows user profile). After the process is finished, a dialog box will pop up showing the results: a list with its elements separated with the [list separator](../../../appendices/special-characters/array-separator.md) character (❚).

```G1ANT
directory path ♥environment⟦USERPROFILE⟧\Documents\G1ANT.Robot\logs pattern 2019-01**
dialog ♥result
```

## Example 2

Here, G1ANT.Robot calculates the number of filtered items in the specified directory, using `♥files⟦count⟧` index.

```G1ANT
directory path ♥environment⟦USERPROFILE⟧\Desktop pattern *.txt result ♥files
dialog ♥files⟦count⟧
```
