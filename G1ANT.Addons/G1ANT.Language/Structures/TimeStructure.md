# time

This structure stores information about time. It has the following fields:

| Field         | Type    | Description         |
| ------------- | ------- | ------------------- |
| `millisecond` | integer | Milliseconds value  |
| `second`      | integer | Seconds value       |
| `minute`      | integer | Minute value        |
| `hour`        | integer | Hour value          |

## Example

This example shows how a time variable can be declared and the individual time elements (fields) read or written. When declaring a time variable, it is important to force the structure using `⟦time⟧` keyword:

```G1ANT
♥time = ⟦time⟧10:30
dialog ♥time
♥time = ⟦time⟧12:45:11.250
dialog ‴It's ♥time⟦minute⟧ minutes past ‴♥time⟦hour⟧
♥time⟦hour⟧ = 11
dialog ‴Sorry, it's exactly ♥time‴
```
