# timeoutconnect

## Syntax

```G1ANT
♥timeoutconnect = ⟦timespan⟧
```

## Description

Determines the timeout value (in ms) for the [is.accessible](../Commands/IsAccessibleCommand.md) and [ping](../Commands/PingCommand.md) commands; the default value is 1000 (1 second).

## Example

```G1ANT
♥timeoutconnect = 20
ping microsoft.com
```

In this example the 20ms timeout value is too short to get a server response, so an error message appears.

