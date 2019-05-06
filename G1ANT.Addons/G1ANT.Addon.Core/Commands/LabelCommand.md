# label

## Syntax

```G1ANT
label ⟦label⟧
```

## Description

This command defines a place anywhere in the script code that can be navigated to with the [`jump`](JumpCommand.md) command.

## Example

The following script shows how the `jump` and the `label` commands work: the robot opens Notepad, then, instead of typing *“Jump over this text”*, it types *“Congratulations! You've made a jump!”*, because of the `jump` command, which tells the robot to move to the `start` label and skip the lines in between.

```G1ANT
program notepad
jump start
keyboard ‴Jump over this text‴

label start
keyboard ‴Congratulations! You've made a jump!‴
```


