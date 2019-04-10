# integer

The integer structure stores a number that can be written without a fractional component and ranging from -2,147,483,648 to 2,147,483,647.

## Example

Simple declaration of an integer value to a variable:

```G1ANT
♥i = 4
```

Calculation of mathematical operations:

```G1ANT
♥result = 39812 + 1
dialog ♥result
```

Accessing a chosen digit in a stored number — the second digit in “*467*” is read and displayed in a dialog box, then it’s replaced with a new value (“*8*”) and the resulting number is displayed:

```G1ANT
♥i = 467
dialog ♥i⟦2⟧
♥i⟦2⟧ = 8
dialog ♥i
```

