# end

## Syntax

```G1ANT
end
```

## Description

This command ends a command block started with the following commands: [`for`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/Commands/ForCommand.md)), [`foreach`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/Commands/ForEachCommand.md)), [`if`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/Commands/IfCommand.md)), [`procedure`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/Commands/ProcedureDefinitionCommand.md)), [`try`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/Commands/TryCommand.md)), [`while`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/Commands/WhileCommand.md)).

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

