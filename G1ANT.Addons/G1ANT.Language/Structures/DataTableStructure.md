# datatable

The datetable structure stores information about the excel sheets, sql queries, etc.:

| Field                         | Type    | Description           |
| ----------------------------- | ------- | --------------------- |
| 'colcount'                    | integer | number of columns     |
| `count`                       | integer | number of rows        |
| `columns`                     | list    | list of column names  |
| row-index                     | list    | row values            |
| column-name                   | list    | column values         |
| column-name,row-index         |         | cell value            |
| column-index,row-index        | integer | Year value            |
| filter ...                    | string  | any filter expression |

Filter can contains the following operators: And, Between, In, Is, Like, Not, Null, Or, <, <=, >, >=, <>, =, +, -, *, /, % (modulo)

See also: [filter expression has been described in the Microsoft manual](https://docs.microsoft.com/en-us/dotnet/api/system.data.datacolumn.expression?view=netcore-3.1#System_Data_DataColumn_Expression)

# Example

```G1ANT
database ‴Server=...;Database=...;User ID=...;Password=...‴
sql ‴select * from machines‴ resultas datatable
dialog ‴List of column names: ‴♥result⟦columns⟧
dialog ‴First row from datatable: ‴♥result⟦1⟧
dialog ‴Field value from row 1, column 1: ‴♥result⟦1,1⟧
dialog ‴Field value from row 1, column Id: ‴♥result⟦Id,1⟧
dialog ‴List of field values from column Id: ‴♥result⟦Id⟧
dialog ‴Row count: ‴♥result⟦count⟧
dialog ‴Column count: ‴♥result⟦colcount⟧
dialog ‴Filtered data: ‴♥result⟦filter Id = 'chris'⟧
dialog ‴Filtered data: ‴♥result⟦filter LIKE 'chr* and Description IS NOT NULL'⟧
```
