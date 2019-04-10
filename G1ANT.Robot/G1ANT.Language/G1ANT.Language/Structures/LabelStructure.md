# label

This structure stores names of labels, which are called by the `jump` command.

## Example

In the following example the robot jumps directly to a label named `start`, skipping the `dialog` command in the second line:

```G1ANT
jump start
dialog ‴Jump over this text‴
label start
dialog ‴Congratulations! You've made a jump to the start label!‴
```

