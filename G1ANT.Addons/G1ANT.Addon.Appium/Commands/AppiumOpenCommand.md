# appium.open

## Syntax

```G1ANT
appium.open appactivity ⟦text⟧ apppackage ⟦text⟧ automationname ⟦text⟧ devicename ⟦text⟧ platformname ⟦text⟧ platformversion ⟦text⟧
```

## Description

This command starts a new Appium session.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`appactivity`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | | Starting activity of the automated application |
|`apppackage`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | |Package of the automated application |
|`automationname`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no | UiAutomator2 | Name of the automating driver |
|`devicename`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | Android | Name of your device to be automated |
|`platformname`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |Android | Name of the automated platform |
|`platformversion`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no | | Version of the automated platform |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

This simple script opens a default Google Calculator app:

```G1ANT
appium.open apppackage com.android.calculator2 appactivity com.android.calculator2.Calculator
```
