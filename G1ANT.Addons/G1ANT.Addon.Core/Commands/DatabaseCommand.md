# database

## Syntax

```G1ANT
database connection ⟦text⟧ type ⟦text⟧
```

## Description

This command allows to establish a connection to an SQL database. If the command succeeds, all `sql` commands will be executed on the established database connection. See also [sql.query](SqlQueryCommand.md) command.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`connection`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | yes |  | Connection string necessary to establish a database connection (see the strings description below) |
|`type`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no | | Type of data provider: `mssql`, `oledb` or `odbc` |
| `if` | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutdb](G1ANT.Manual/appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for a connection |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

```G1ANT
database ‴Server=myServerAddress;Database=myDataBase;User Id=myUsername;
Password=myPassword;‴ type mssql
```

### Connection strings description

_Standard Security_

```G1ANT
Server=myServerAddress;Database=myDataBase;User Id=myUsername;
Password=myPassword;
```

_Trusted Connection_

```G1ANT
Server=myServerAddress;Database=myDataBase;Trusted_Connection=True;
```

_Connection to a SQL Server instance_

```G1ANT
Server=myServerName\myInstanceName;Database=myDataBase;User Id=myUsername;
Password=myPassword;
```

_Trusted Connection from a CE device_

```G1ANT
Data Source=myServerAddress;Initial Catalog=myDataBase;Integrated Security=SSPI;
User ID=myDomain\myUsername;Password=myPassword;
```

_Connect via an IP address_

```G1ANT
Data Source=190.190.200.100,1433;Network Library=DBMSSOCN;
Initial Catalog=myDataBase;User ID=myUsername;Password=myPassword;
```

_Enable MARS_

```G1ANT
Server=myServerAddress;Database=myDataBase;Trusted_Connection=True;
MultipleActiveResultSets=true;
```

_Attach a database file on connect to a local SQL Server Express instance_

```G1ANT
Server=.\SQLExpress;AttachDbFilename=C:\MyFolder\MyDataFile.mdf;Database=dbname;
Trusted_Connection=Yes;
```

_Attach a database file, located in the data directory, on connect to a local SQL Server Express instance_

```G1ANT
Server=.\SQLExpress;AttachDbFilename=C:\MyFolder\MyDataFile.mdf;Database=dbname;
Trusted_Connection=Yes;
```

_Attach a database file, located in the data directory, on connect to a local SQL Server Express instance_

```G1ANT
Server=.\SQLExpress;AttachDbFilename=|DataDirectory|mydbfile.mdf;Database=dbname;
Trusted_Connection=Yes;
```

_LocalDB automatic instance_

```G1ANT
Server=(localdb)\v11.0;Integrated Security=true;
```

_LocalDB automatic instance with specific data file_

```G1ANT
Server=(localdb)\v11.0;Integrated Security=true;
AttachDbFileName=C:\MyFolder\MyData.mdf;
```

_LocalDB named instance_

```G1ANT
Server=(localdb)\MyInstance;Integrated Security=true;
```

_LocalDB named instance via the named pipes pipe name_

```G1ANT
Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query;
```

_LocalDB shared instance_

```G1ANT
Server=(localdb)\.\MyInstanceShare;Integrated Security=true;
```

_Database mirroring_

```G1ANT
Data Source=myServerAddress;Failover Partner=myMirrorServerAddress;
Initial Catalog=myDataBase;Integrated Security=True;
```

_Asynchronous processing_

```G1ANT
Server=myServerAddress;Database=myDataBase;Integrated Security=True;
Asynchronous Processing=True;
```

_Using an User Instance on a local SQL Server Express instance_

```G1ANT
Data Source=.\SQLExpress;Integrated Security=true;
AttachDbFilename=C:\MyFolder\MyDataFile.mdf;User Instance=true;
```

_Specifying packet size_

```G1ANT
Server=myServerAddress;Database=myDataBase;User ID=myUsername;
Password=myPassword;Trusted_Connection=False;Packet Size=4096;
```
