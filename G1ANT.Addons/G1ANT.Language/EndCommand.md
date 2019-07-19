# end

## Syntax

```G1ANT
end
```

## Description

This command ends a command block started with the following commands: [`for`](../G1ANT.Addon.Core/Commands/ForCommand.md), [`foreach`](../G1ANT.Addon.Core/Commands/ForEachCommand.md), [`if`](../G1ANT.Addon.Core/Commands/IfCommand.md), [`procedure`](../G1ANT.Addon.Core/Commands/ProcedureDefinitionCommand.md), [`try`](../G1ANT.Addon.Core/Commands/TryCommand.md), [`while`](../G1ANT.Addon.Core/Commands/WhileCommand.md).

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

