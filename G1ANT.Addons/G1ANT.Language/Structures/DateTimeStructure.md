# datetime

The datetime structure stores information about date and time. It has the following fields:

| Field         | Type    | Description         |
| ------------- | ------- | ------------------- |
| `millisecond` | integer | Milliseconds value  |
| `second`      | integer | Seconds value       |
| `minute`      | integer | Minute value        |
| `hour`        | integer | Hour value          |
| `day`         | integer | Day value           |
| `month`       | integer | Month value         |
| `year`        | integer | Year value          |
| `dayofyear`   | integer | Day of a year value |
| `dayofweek`   | integer | Day of a week value |

## Example

You can declare datetime variables in the following ways:

```G1ANT
♥myDate = ⟦datetime⟧10/05/2018 12:4:8
```

This sets the date and time for a variable. As with the [`date`](DateStructure.md) structure, you can either use `/` , `-`, `,` or `.` separator characters for the date, but the default format is MM/dd/yyyy.

```G1ANT
♥myDate = ⟦datetime⟧12:4:8
```

In the above example, only time is specified. The date will be set automatically as the current day.

Elements of the `datetime` structure can be accessed using their respective indexes (field names):

```G1ANT
♥myDate =  ⟦datetime⟧12:4:8
dialog ♥myDate
dialog ♥myDate⟦hour⟧
dialog ♥myDate⟦year⟧
dialog ♥myDate⟦dayofyear⟧
```

​      
