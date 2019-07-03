# test

## Syntax

```G1ANT
test condition ⊂⊃
```

## Description

This command checks if the expression specified in the `condition` argument is true.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`condition`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | yes| | Condition to be tested: a C# snippet embraced with `⊂⊃` special characters |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example 1

In this example two variables are compared. They are not equal, so the result is false and the `errormessage` argument displays a dialog box with a message:

```G1ANT
♥firstText = bananas and kiwi
♥secondText = orange
test condition ⊂♥firstText==♥secondText⊃ errormessage ‴Texts don't match‴
```

## Example 2

The following script first checks if a system drive is C:, and if it is, the robot verifies the Windows version. If it’s other than Windows XP, a dialog box appears.

In case any of these tests fail, an error message is displayed.

```G1ANT
test condition ⊂♥environment⟦HOMEDRIVE⟧=="C:"⊃
test condition ⊂♥environment⟦OS⟧ != "Windows_xp"⊃
dialog ‴Your system settings passed the test.‴
```


