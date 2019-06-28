# capslock

## Syntax

```G1ANT
♥capslock = ⟦bool⟧
```

## Description

Switches the **CapsLock** key on or off. You can also use the [`keyboard.capslock`](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Commands/KeyboardCapsLockCommand.md)) command to achieve the same results.

> **Note:** The text input executed with the [`keyboard`](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Commands/KeyboardCommand.md)) command will only be affected with this variable if keystrokes are used (individual keys specified within the `⋘⋙` [key code special characters](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/special-characters/key-code.md)), not text strings (text within the `‴‴` [text special characters](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/special-characters/text.md)) — see the example below.

## Example

The following script shows the difference between the same text input sent with the `keyboard` command using two methods and how they are affected by the `♥capslock` variable.

```G1ANT
program notepad
♥capslock = true
keyboard ‴a‴⋘a⋙‴b‴⋘b⋙⋘ENTER⋙
♥capslock = false
keyboard ‴a‴⋘a⋙‴b‴⋘b⋙
```
