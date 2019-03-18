# timeout

## Syntax

```G1ANT
♥timeout = ⟦timespan⟧
```

## Description

Defines the maximal robot process duration time (in milliseconds), after which the process terminates; the default value is 180000 (3 minutes).

>**Note:** This special variable works only when the script is run in Production mode (`Debug/Run (Production)` menu or **Ctrl+F9** keyboard shortcut).

## Example

```G1ANT
♥timeout = 50
program notepad
```

The 50ms timeout in the script above is not enough to complete the process, so an error message appears.