# process.kill

## Syntax

```G1ANT
process.kill name ⟦text⟧
```

## Description

This command kills all processes of a specified name running on your computer.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`name`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Name of a process(es) to kill |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

The following script starts four processes and then kills them instantly all one by one, even if they were not originally launched by the robot. In other words, the `process.kill` command in this example will close **ALL** Firefox windows and tabs, as well as Notepad, Excel and Internet Explorer windows. **Be sure to save all your work in these applications before running this script, otherwise your data will be lost!**

>**Note:** The `process.kill` command will not kill processes specified as filenames with extensions, e.g. `iexplore.exe`.

> **Note:** The `excel.open`, `ie.open` and `selenium.open` commands require the MSOffice, IExplorer and Selenium addons enabled, respectively. You can do that in the Addons [panel](../../../g1ant.robot-window/panels.md).

```G1ANT
program notepad
excel.open
ie.open
selenium.open firefox url google.com
process.kill notepad
process.kill excel
process.kill iexplorer
process.kill firefox
```
