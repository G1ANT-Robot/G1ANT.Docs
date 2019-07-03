# keyboard

## Syntax

```G1ANT
keyboard text ⟦text⟧
```

## Description

This command sends keyboard actions to a window.

The text input executed with the [`keyboard`](KeyboardCommand.md) command will only be affected with this setting if keystrokes are used (individual keys specified within the `⋘⋙` [key code special characters](../../../appendices/special-characters/key-code.md)), not text strings (text within the `‴‴` [text special characters](../../../appendices/special-characters/text.md)) — see the example below.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`text`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes|  | Text to be send to a window; it may contain [key codes](../../../appendices/special-characters/key-code.md) |
|`wait`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | yes | [♥keyboardwait](../Variables/KeyboardWaitVariable.md) | When the value is `true`, the robot executing the `keyboard` command waits for another keystroke |
|`keydelay`| [integer](../../G1ANT.Language/Structures/IntegerStructure.md) | yes | [♥keydelay](../Variables/KeyDelayVariable.md) | Determines the time (in ms) between the execution of consecutive [keyboard](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/G1ANT.Language/G1ANT.Addon.Core/Commands/KeyboardCommand.md) commands |
|`window`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no | [♥keyboardwindow](../Variables/KeyboardWindowVariable.md) | Specifies application window title to receive the keyboard input |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

### text Argument

The `text` argument can be continuous combination of three different forms (see examples 3, 6). The first form is a sequence of characters, for example `‴abc !# 闈河圬曅‴` (the `‴‴` [text special characters](../../../appendices/special-characters/text.md)) can be omitted if text does not contain any white space characters).

The second option for specifying keyboard input is to use the `⋘⋙` [key code special characters](../../../appendices/special-characters/key-code.md).

The third option is to use a variable, which stores the text input (see example 3).

>**Note:** The following examples assume your Windows language version is English. If it's not, please change Notepad window titles used for the `window` command to reflect their real names in your OS language.

## Example 1

This script shows the basic use of the `keyboard` command:

```G1ANT
program notepad
keyboard Hello!
```

## Example 2

Here is an example of key codes used as text input. The key codes in the last line will serve as keyboard shortcuts for selecting all text (`ctrl+a`), copying it to clipboard (`ctrl+c`) and then pasting it (`ctrl+v`) into a new line (deselecting the text with the `right` arrow and then `enter`  to move to a new line):

```G1ANT
program notepad
keyboard ‴This is random text‴
keyboard ⋘ctrl+a⋙⋘ctrl+c⋙⋘right⋙⋘enter⋙⋘ctrl+v⋙
```

## Example 3

The script below uses key codes to navigate the Notepad’s menu as you would with keyboard shortcuts available after pressing **Alt** key. Here, it is used to open the Font dialog and change the font size to 20. Then the content of the `♥text` variable is typed by the `keyboard` command:

```G1ANT
♥text = ‴Welcome to G1ANT.Robot!‴
program notepad
keyboard ⋘alt+o⋙⋘f⋙⋘tab 2⋙20⋘enter⋙
keyboard ♥text
```

## Example 4

This example shows how the `window last` argument can be used to make sure the data is copied to a proper window after an interruption caused by a mouse click in `mouse.click position 0⫽0 relative false`. This argument always refers to the last window selected by the `window` command. The `delay` commands here help to wait for Chrome to open the page and then to notice that Notepad is out of focus after the mouse click.

```G1ANT
chrome http://www.lipsum.com/
delay 5
program notepad
window ‴Lorem Ipsum✱‴
keyboard ⋘ctrl+a⋙⋘ctrl+c⋙
window Untitled✱
mouse.click position 0⫽0 relative false
delay 5
keyboard ⋘ctrl+v⋙ window last
```

## Example 5

This example shows where the `keyboard` command should paste the copied text — by specifying the `window` argument:

```G1ANT
program notepad
chrome http://www.lipsum.com/
delay 5
keyboard ⋘ctrl+a⋙⋘ctrl+c⋙
keyboard ⋘ctrl+v⋙ window ✱Notepad
```

## Example 6

This example shows how to combine character sequence, white space characters and key codes:

```G1ANT
program notepad
keyboard ‴The first line of text⋘shift down⋙⋘left 20⋙⋘shift up⋙⋘ctrl+c⋙⋘end⋙⋘enter⋙pasted line: ⋘ctrl+v⋙‴
```
