# keyboard.capslock

## Syntax

```G1ANT
keyboard.capslock state ⟦text⟧
```

## Description

This command switches the **CapsLock** key on or off. You can also use the [`♥capslock`](../../Variables/CapsLockVariable.md) special variable to achieve the same results.

> **Note:** The text input executed with the [`keyboard`](KeyboardCommand.md) command will only be affected with this setting if keystrokes are used (individual keys specified within the `⋘⋙` [key code special characters](../../../appendices/special-characters/key-code.md)), not text strings (text within the `‴‴` [text special characters](../../../appendices/special-characters/text.md)) — see the example below.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`state`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no | | The value can be either `on` or `off` |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

The following script shows the difference between the same text input sent with the `keyboard` command using two methods and how they are affected by the `keyboard.capslock` command: with this command set to `on`, the first `keyboard` command output will be *aAbB*, whereas the `off` setting changes the output to *aabb*.

```G1ANT
program notepad
keyboard.capslock on
keyboard ‴a‴⋘a⋙‴b‴⋘b⋙⋘ENTER⋙
keyboard.capslock off
keyboard ‴a‴⋘a⋙‴b‴⋘b⋙
```

