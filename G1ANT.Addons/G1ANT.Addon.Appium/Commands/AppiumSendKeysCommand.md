# appium.sendkeys

## Syntax

```G1ANT
appium.sendkeys search ⟦text⟧ by ⟦text⟧ keys ⟦text⟧
```

## Description

This command sends keystrokes to a specified element.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`search`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Name of an element to send keystrokes to |
|`by`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Specifies an element selector: `id`, `accessibilityid`, `text`, `partialid`, `xy`, `xpath` |
|`keys`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | |Keys to be sent to the element |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

> **Note:** the `appium.` commands require opening a mobile app with the `appium.open` command first.

## Example

.

```G1ANT
appium.open apppackage com.android.vending appactivity com.google.android.finsky.activities.MainActivity
appium.click search com.android.vending:id/search_box_idle_text by Id
appium.sendkeys search com.android.vending:id/search_box_text_input by Id keys netflix
delay 3
appium.close
```
