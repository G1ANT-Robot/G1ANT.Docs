# sap.getconnections

## Syntax

```G1ANT
sap.getconnections
```

## Description

This command returns a list of open connections to SAP.


| Argument       | Type                                                         | Required | Default Value                                                | Description                                                  |
| -------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `result`       | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                    | Name of a variable where the command's result will be stored (a [list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structures containing connection components) |
| `if`           | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                         | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                              | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                              | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | no       |                                                              | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                              | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.

> **Note:** One of parameters `description`, `connectionstring` or `index` must be set.

> **See also:** [sap.settesttool](../Sessions/SAPSetTestToolModeCommand.md) to turn off modal messages from SAP.

##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can see all the details
of your connections on the `SAP UI object tree`.
You can view details of specific connection on `Variables` panel if you assign
connection from connection list to a variable.