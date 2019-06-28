# keydelay

## Syntax

```G1ANT
♥keydelay = ⟦integer⟧
```

## Description

Determines the time (in ms) between the execution of consecutive [keyboard](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Commands/KeyboardCommand.md)) commands; the default value is 10.

## Example

```G1ANT
program notepad
keyboard ‴fast input:‴⋘ENTER⋙
keyboard 1⋘ENTER⋙
keyboard 2⋘ENTER⋙
keyboard 3⋘ENTER⋙
♥keydelay = 1000
keyboard ‴slow input:‴⋘ENTER⋙
keyboard 1⋘ENTER⋙
keyboard 2⋘ENTER⋙
keyboard 3⋘ENTER⋙
```
