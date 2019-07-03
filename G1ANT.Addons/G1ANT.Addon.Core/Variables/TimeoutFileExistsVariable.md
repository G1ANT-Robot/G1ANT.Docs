# timeoutfileexists

## Syntax

```G1ANT
♥timeoutfileexists = ⟦timespan⟧
```

## Description

Determines the timeout value (in ms) for the [file.exists](../indexes/commands/file.exists.md) command; the default value is 10000 (10 seconds).

## Example

```G1ANT
♥timeoutfileexists = 200

file.exists ♥environment⟦USERPROFILE⟧\Desktop\test.txt errorjump onExpectedTimeoutException
dialog ‴File exists!‴

label onExpectedTimeoutException
dialog ‴No such file!‴
```

The `file.exists` command checks for file presence in a specified location and waits until timeout expires, then displays an error. In the example above, the command will wait 200ms instead of the default 10 seconds, and then will display a dialog box with a “*No such file!*” message.