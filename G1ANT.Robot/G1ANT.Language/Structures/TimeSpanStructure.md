# timespan

This structure stores a time interval value (duration of time or elapsed time) that is measured as a positive or negative number of days, hours, minutes, seconds and milliseconds. The timespan structure is used by timeout variables and arguments, and the input value has to be provided in milliseconds.

## Example

This simple script shows how a value of 1000000100 milliseconds will be stored by a timespan variable:

```G1ANT
♥timespan = ⟦timespan⟧1000000100
dialog ♥timespan
```

This value translates into 11 days, 13 hours, 46 minutes, 40 seconds and 100 milliseconds