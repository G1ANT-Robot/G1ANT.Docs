# ocrabbyy.plaintext

## Syntax

```G1ANT
ocrabbyy.plaintext documentid ⟦integer⟧ method ⟦text⟧
```

## Description

This command extracts text from a processed document.

> **Note:** The OCR ABBYY addon is in the beta phase and was not tested with ABBYY FineReader Engine 12.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`documentid`| [integer](../../G1ANT.Language/Structures/IntegerStructure.md) | no |  | ID of a processed document. If not specified, the last processed document is used |
|`method`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no | structured | Method of text recognition to use: `linebyline` or `structured` |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In order to use the `ocrabbyy.plaintext` command, it’s necessary to process the file first with the [`ocrabbyy.processfile`](OcrAbbyyProcessFileCommand.md) command. In the example below, a sample file located on user’s Desktop is processed and then the robot assigns the content of a document to a variable and displays it in a dialog box:

```
ocrabbyy.processfile ♥environment⟦USERPROFILE⟧\Desktop\document.jpg result ♥fileId
ocrabbyy.plaintext ♥fileId result ♥text
dialog ♥text
```



