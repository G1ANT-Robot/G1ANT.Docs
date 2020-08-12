# sap.isrunning

## Syntax

```G1ANT
sap.isrunning
```

## Description

This command checks if SAP instance (Logon app) is running.

| Argument       | Type                                                         | Required | Default Value                                                | Description                                                  |
| -------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `result`       | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                    | Name of a variable where the command's result will be stored ([bool](/G1ANT.Addons/G1ANT.Language/Structures/BoolStructure.md) structure) |
| `if`           | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                         | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                              | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                              | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | no       |                                                              | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                              | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.

## Example

In the following script will open message window with value returned by this command.

```G1ANT
sap.isrunning result ♥isRunning
dialog ♥isRunning
```

> **Note:** returs true only if instance of SAP Logon app is running, otherwise (SAP Logon not running, not installed or incorrectly installed (i.e. missing SAP Scripting API)) returns false.


