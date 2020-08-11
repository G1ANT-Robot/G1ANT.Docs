﻿# sap.switch

## Syntax

```G1ANT
sap.switch id ⟦integer⟧
```

## Description
Switches between open SAP connections.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `id`    | [integer](../../G1ANT.Language/Structures/IntegerStructure.md)             | **yes**  |                | Id of a SAP Manager that was returned by `sap.connect` command. |
| `if`            | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)  | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.
