# checkversion

## Syntax

```G1ANT
checkversion path ⟦text⟧ result ⟦text⟧ assembly ⟦bool⟧
```

## Description

The `checkversion` command allows to check product, file and assembly versions of the file.

| Name | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`path`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | |Specifies the path to a file|
|`result`| [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no | ♥result |Name of a variable, which will store the returned file information|
|`assembly`| [variable](../../G1ANT.Language/Structures/VariableStructure.md)  | no | ♥assembly | Name of a variable, which will store the assembly version information |
| `if`           | [bool](../../G1ANT.Language/Structures/VariableStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example


In this example a custom path to one of G1ANT .dll files is declared as the `♥dllPath` variable (you can provide the path to other .dll file here). Then, the `checkversion` command returns the product and file version (and some more info) to the default `♥result` variable. Finally, using the `dialog` command, this information is displayed in a message box.

```G1ANT
♥dllPath = ♥environment⟦windir⟧\system32\kernel32.dll
checkversion path ♥dllPath
dialog ♥result
```

 
