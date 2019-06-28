# break

## Syntax

```G1ANT
break
```

## Description

The `break` command immediately exits current block and continues process execution.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
| `if` | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no | true | Executes the command only if a given condition is true |

For more information about the `if` argument, please see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

### Example

```G1ANT
for counter ♥cnt from 1 to 20
  if ⊂♥cnt==10⊃
    dialog Break!
    break
    dialog ‴This will not show, because the loop was broken‴
  end
end

dialog ♥cnt
```

As you can see from the above example, `break` will only affect the `if` block command, not the `for` loop, which continues execution after the message dialog is closed.
