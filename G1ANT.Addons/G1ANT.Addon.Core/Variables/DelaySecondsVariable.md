# delayseconds

## Syntax

```G1ANT
♥delayseconds = ⟦integer⟧
```

## Description

Determines the time value (in seconds) for the [delay](../Commands/DelayCommand.md) command; the default value is 1.

## Example

```G1ANT
♥delayseconds = 3
program notepad
keyboard Wait...
delay
keyboard ‴ for it!‴
```

The script above will write the first part of the text, stop for 3 seconds, then write the rest of the text.
