# date

The date structure stores information about the date. It has the following fields:

| Field       | Type    | Description         |
| ----------- | ------- | ------------------- |
| `day`       | integer | Day value           |
| `month`     | integer | Month value         |
| `year`      | integer | Year value          |
| `dayofyear` | integer | Day of a year value |
| `dayofweek` | integer | Day of a week value |

## Example

This example shows how dates can be declared. Please note that while declaring a date, you need to force (cast) the type by using `⟦date⟧` keyword before declaring the content of the variable:

```G1ANT
♥myDate = ⟦date⟧8/07/2019
```

```G1ANT
♥myDate2 = ⟦date⟧2.04.2019
```

You can either use `/` , `-`, `,` or `.` separator characters, but the default format is MM/dd/yyyy. To change the order, in which the input numbers are recognized as particular date fields, you have to set the date format during casting:

```G1ANT
♥myDate2 = ⟦date:dd-MM-yyyy⟧21-02-2019
```

Elements of date (year, month, day etc.) can be accessed using the index names of fields:

```G1ANT
♥myDate=⟦date⟧8.07.2018
dialog ♥myDate
dialog ♥myDate⟦year⟧
dialog ♥myDate⟦month⟧
dialog ♥myDate⟦day⟧
```

