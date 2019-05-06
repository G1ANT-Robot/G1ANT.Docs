# waitfor.directory

## Syntax

```G1ANT
waitfor.directory path ⟦text⟧
```

## Description

This command waits for a directory to appear at a specified location.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`path`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | yes |  |Path to the expected directory|
| `if`           | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutfileexists](G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutFileExistsVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

The following script waits 10 seconds for the *Test* directory to appear on the user’s Desktop. If the directory is found within the given timespan, a dialog box is displayed. If it isn’t, an error message pops up:

```G1ANT
waitfor.directory path ♥environment⟦USERPROFILE⟧\Desktop\Test timeout 10000 errormessage ‴No such directory!‴
dialog ‴Directory found!‴
```
