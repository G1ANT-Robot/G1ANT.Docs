# call

## Syntax

```G1ANT
call ⟦procedure⟧
```

## Description

When the `call` command is used, the robot goes to a specified procedure (block of commands) and executes it until its end is reached. Then the robot returns to the point where the procedure was called and continues the execution of the remaining script.

| Argument       | Type                                                         | Required | Default Value                                               | Description                                                  |
| -------------- | ------------------------------------------------------------ | -------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In this example, a procedure named `increaseNumber` is called twice and each time this procedure ends, a dialog box is displayed with the same `♥number` variable, but showing different values. It’s because the procedure increases the variable’s value by 1 every time it’s called.

```G1ANT
♥number = 1
call increaseNumber
dialog ♥number
call increaseNumber
dialog ♥number

procedure increaseNumber
  ♥number = ♥number + 1
end
```

