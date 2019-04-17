# timeoutwaitforcolor

## Syntax

```G1ANT
♥timeoutwaitforcolorexpected = ⟦timespan⟧
```

## Description

Determines the timeout value (in ms) for the [waitfor.color](G1ANT.Language/G1ANT.Addon.Core/Commands/WaitforColorCommand.cs) command; the default value is 10000 (10 seconds).

## Example

```G1ANT
♥timeoutwaitforcolor = 300
♥position = 10⫽20
color position ♥position result ♥color
♥color = ♥color + 1

waitfor.color position ♥position color ♥color errorjump onExpectedException
break

label onExpectedException
dialog Timeout!
```

In this example the given pixel has other color than the one specified in the waitfor.color command, so after the 300ms timeout (not the default 10000ms) a dialog box appears with “*Timeout!*” message.
