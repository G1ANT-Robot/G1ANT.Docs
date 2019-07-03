# chrome

## Syntax

```G1ANT
chrome url ⟦text⟧
```

## Description

The `chrome` command opens Google Chrome browser and displays the specified page.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`url`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes| | A web address to be displayed in Google Chrome browser |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
|`timeout`| [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutchrome](../Variables/TimeoutCommandVariable.md) | defines time in milliseconds for Google Chrome to launch |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example 1

In the following example the Google website opens with the query results for “g1ant” keyword:

```G1ANT
chrome url https://www.google.com/search?q=g1ant
```

## Example 2

This example opens a website, waits 5 seconds for a page to load, then the `keyboard` command emulates **Tab** key and presses it twice, then presses **Enter**. The page http://irpaai.com/membership/ opens as a result. Sometimes an advertising banner shows up on this website, so pressing **Esc** key first is a precaution to avoid this obstacle during automation process.

```G1ANT
chrome url www.irpaai.com
delay 5
keyboard ⋘esc⋙⋘tab 2⋙⋘enter⋙
```

