# file.download

## Syntax

```G1ANT
file.download url ⟦text⟧ filename ⟦text⟧
```

## Description

This command downloads a file from a web of FTP server and saves it to the specified location.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`url`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | | Direct link to the file to be downloaded |
|`filename`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Destination path and filename for the downloaded file |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../../appendices/common-arguments.md) | Maximal time for downloading a file from a server; a negative value indicates infinite timeout |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In the example below the script downloads the TeamViewer application installer file and saves it to a specified directory under a slightly changed filename:

```G1ANT
file.download url http://download.teamviewer.com/download/TeamViewer_Setup_en.exe filename ‴C:\G1ANT\TeamViewer Setup (EN).exe‴
```

