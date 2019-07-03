# sql

## Syntax

```G1ANT
sql query ⟦text⟧
```

## Description

This command executes an SQL query while user is connected to their database. Please use the [`database`](DatabaseCommand.md) command first to establish a connection to a database. The query results are returned as a list of dictionaries, from which you can fetch individual records.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`query`| [string](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/master/G1ANT-Language/Structures/string.md) | yes | | SQL query to execute on the active database connection |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In this example, after a connection to a database is established with the `database` command (remember to provide real information in the connection string), an sql query for `name` and `surname` columns in the `users` table is performed and the resulting dictionary is stored in the default `♥result` variable. Then, the first row in the dictionary is assigned to the `♥row` variable and the values from its `name` and `surname` indexes are assigned to the `♥name` and `♥surname` variables, respectively. Finally, the information from the first record is displayed in a dialog box:

```G1ANT
database ‴Server=myServerAddress;Database=myDataBase;User Id=myUsername;
Password=myPassword;‴
sql ‴select name, surname from users‴
♥row = ♥result⟦1⟧
♥name = ♥row⟦name⟧
♥surname = ♥row⟦surname⟧
dialog ‴Name: ♥name, Surname: ♥surname‴
```
