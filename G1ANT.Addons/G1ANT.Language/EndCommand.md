# end

## Syntax

```G1ANT
end
```

## Description

This command ends a command block started with the following commands: [`for`](../Commands/ForCommand.md), [`foreach`](../Commands/ForEachCommand.md), [`if`](../Commands/IfCommand.md), [`procedure`](../Commands/ProcedureDefinitionCommand.md), [`try`](../Commands/TryCommand.md), [`while`](../Commands/WhileCommand.md).

## Example

In the script below two command blocks are used: `procedure` and `for`, and both close with the `end` command:

```G1ANT
call loop

procedure loop
  for ♥i from 1 to 3
    dialog ♥i
  end
end
```

