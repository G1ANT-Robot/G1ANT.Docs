# continue

## Syntax

```G1ANT
continue
```

## Description

This command stops executing the current block and goes to the next iteration.

| Argument       | Type                                                         | Required | Default Value                                               | Description                                                  |
| -------------- | ------------------------------------------------------------ | -------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |

## Example

In the following script a list is created containing three elements, then the robot retrieves each element in a `foreach` loop and displays it in a dialog box. Because of the `continue` command, it skips the rest of the command block and immediately goes to the next element in a list, so a dialog box with *“You won't see me!”* message never appears:

```G1ANT
♥list = one❚two❚three
foreach ♥element in ♥list
    dialog ♥element
    continue
    dialog ‴You won't see me!‴
end
```

