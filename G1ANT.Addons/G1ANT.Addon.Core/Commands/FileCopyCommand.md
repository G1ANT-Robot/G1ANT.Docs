# file.copy

## Syntax

```G1ANT
file.copy path ⟦text⟧ destinationpath ⟦text⟧
```

## Description

This command copies the specified file to the location specified with the `destinationpath` argument.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`path`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Source path to the file to be copied |
|`destinationpath`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Relative or absolute destination filepath |
|`overwrite`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | true | Executes the command even if a file of the same name exists in the destination location |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../../appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example 1

This example copies the specified file using absolute destination path:

```G1ANT
file.copy path ‴D:\New folder\test.txt‴ destinationpath ‴D:\New folder\copied_file.txt‴
```

The same results can be achieved with relative destination path (when the destination path is the same as the source one):

```G1ANT
file.copy path ‴D:\New folder\test.txt‴ destinationpath copied_file.txt
```

or, if you want the file to be copied to `D:\Test Folder`, leaving the filename unchanged:

```G1ANT
file.copy path ‴D:\New folder\test.txt‴ destinationpath ‴..\Test Folder‴
```

## Example 2

In the script below the robot checks whether a `TestLogo.png` file exists in the specified location, and if so, a copy of the file is created in the same location. If there’s no source file, an appropriate dialog box is displayed.

```G1ANT
file.exists C:\Tests\TestLogo.png timeout 1000 errorjump noFile
file.copy C:\Tests\TestLogo.png destinationpath C:\Tests\TestLogo2.png overwrite true

label noFile
    dialog ‴File not found‴
end
```
