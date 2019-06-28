# timeoutchrome

## Syntax

```G1ANT
♥timeoutchrome = ⟦timespan⟧
```

## Description

Determines the timeout value (in ms) for the [chrome](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Commands/ChromeCommand.md)) command; the default value is 10000 (10 seconds).

## Example

```G1ANT
♥timeoutchrome = 500
chrome www.g1ant.com
```

In this example the 500ms timeout value is too short to open the browser, so an error message appears.

