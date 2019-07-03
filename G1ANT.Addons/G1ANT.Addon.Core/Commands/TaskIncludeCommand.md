# task.include

## Syntax

```G1ANT
task.include filepath ⟦text⟧
```

## Description

This command includes a script read from a file. The script will be inserted into the place where the `task.include` command was executed.

The full filepath can be specified or just the filename — by default, the command tries to find the file in the *%currentuser%/[My ]Documents/G1ANT.Robot* folder. Please note that all lines from the script will be imported, so if there is something more than just procedures, it will be executed in the current script.

| Name | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`filepath`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Full path or a name (if a file is located in G1ANT.Robot folder) to a file with the script to be included |

## Example

The following script will import the contents of the *forloop.G1ANT* file, which is a simple procedure, and then calls it with `start` and `end` parameters.

The external `forLoop` procedure normally has two iterations of the `for` loop defined by the `start` and `end` parameters with the values of 0 and 1, respectively. But when it’s called from the current script, new `start` and `end` values are passed to it — 3 and 6, respectively — so the loop will be executed four times, displaying dialog boxes with numbers from 3 to 6.

```G1ANT
task.include forloop.G1ANT
dialog ‴Now call a procedure from the external script file‴
call forLoop start 3 end 6
```

The contents of the *forloop.G1ANT* file:

```G1ANT
procedure forLoop start 0 end 1
  for ♥loopCount from ♥start to ♥end
    dialog ♥loopCount
  end
end
```
