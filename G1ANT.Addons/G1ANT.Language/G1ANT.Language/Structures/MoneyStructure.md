# money

This structure represents a decimal number with up to 29 significant digits, which is important for financial calculations to avoid rounding errors.

## Example

In the script below you can see what happens when you assign the same number with 30 digits to a variable of float and money structure:

```G1ANT
♥float = ⟦float⟧1,00000000000000000000000000006
♥money = ⟦money⟧1,00000000000000000000000000006
program notepad
keyboard ♥float⋘ENTER⋙♥money
```

In both cases the resulting values are rounded, but money variable is lots more precise.