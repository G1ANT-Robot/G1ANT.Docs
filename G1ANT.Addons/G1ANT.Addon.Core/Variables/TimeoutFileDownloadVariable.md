# timeoutfiledownload

## Syntax

```G1ANT
♥timeoutfiledownload = ⟦timespan⟧
```

## Description

Determines the timeout value (in ms) for the [file.download](../Commands/FileDownloadCommand.md) command; the default value is 10000 (10 seconds).

## Example

```G1ANT
♥timeoutfiledownload = 10
♥downloadedFilePath = ♥environment⟦USERPROFILE⟧\Desktop\test.txt

file.download http://www.g1ant.com/ filename ♥downloadedFilePath
```

In the example above the 10ms timeout is not enough to download content from the specified website.