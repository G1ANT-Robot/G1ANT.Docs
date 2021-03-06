# excel.insertcolumn

## Syntax

```G1ANT
excel.insertcolumn colindex ⟦integer⟧ where ⟦text⟧
```

or

```G1ANT
excel.insertcolumn colname ⟦text⟧ where ⟦text⟧
```

## Description

This command inserts an empty column in a specified place.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`colindex` or `colname`| [integer](../../G1ANT.Language/Structures/IntegerStructure.md)  or [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | `colindex`: cell's column number; `colname`: cell's column name |
| `where`                 | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       | after                                                        | Specifies where to insert a column: `before` or `after` a specified column |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

This example opens an empty Excel instance, enters “*something*” and “*something else*” into first two cells of the first row and inserts a column after the column A, between the already filled cells:

```G1ANT
excel.open
window ✱Excel
excel.setvalue something row 1 colindex 1
excel.setvalue ‴something else‴ row 1 colindex 2
excel.insertcolumn colname A where after
```

