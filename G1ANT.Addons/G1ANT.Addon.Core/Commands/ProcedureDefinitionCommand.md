# procedure

## Syntax

```G1ANT
procedure ⟦procedure⟧
```

## Description

This command defines a procedure, with or without input parameters, anywhere in the script code. You can call the procedure later with specific parameters, if necessary. Designed for sets of repeatable commands, which can be used multiple times with different parameters.

When defining, make sure to:

1. Set the default value after the parameter name — it is needed to define the structure of an input parameter.
2. Finish the defined procedure block with the `end` command.

## Example 1

In the following example a procedure named `test` displays a simple message in a dialog box. Even though the procedure is defined at the beginning of the script, a dialog box displaying *Hi!* will pop up first, because the procedure is executed only when it’s called with the [`call`](CallCommand.md) command.

When the procedure ends, the script execution is continued from the place where the procedure was called. This is why another message, *Bye!*, is displayed.

```G1ANT
procedure test
  dialog ‴You've just called a procedure.‴
end

dialog Hi!
call test
dialog Bye!
```

## Example 2

Here is an example of calling a procedure with input parameters. First, a procedure named `forLoop` is declared with its input parameters defined as `start` and `end`. These parameters have their default values of 0 and 2, respectively (as mentioned earlier, you must set the default parameter value). They are used as border values for the counter in a `for` loop.

When the procedure is called for the first time with no input parameters provided, it uses its default parameter values and the loop will cause displaying *0*, *1* and *2* in the dialog boxes. The second call passes new input parameters values to the procedure, so the loop output will be *55*, *56* and *57*.

```G1ANT
procedure forLoop start 0 end 2
  for ♥loopCount from ♥start to ♥end
    dialog ♥loopCount
  end
end

dialog ‴These are the procedure's own parameters:‴
call forLoop
dialog ‴Now calling the procedure with new parameters:‴
call forLoop start 55 end 57
```
