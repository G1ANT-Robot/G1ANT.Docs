# float

The float structure represents a number with a decimal point separator.

## Example

These three variables will be properly recognized as floating point numbers by G1ANT.Robot:

```G1ANT
♥var1 = 8.33
♥var2 = 1.345
♥var3 = -3.14159265359
```

When you want the robot to recognize an integer number as a floating point one, you have to force (cast) the float structure:

```G1ANT
♥price = ⟦float⟧399
dialog ♥price
```

This is useful when you are assigning, for example, a list with prices to a variable, and some of them might be integers like 399,459 and others may be float numbers like 399.99. If you force the type to `⟦float⟧`, then G1ANT.Robot will be aware that prices may not be integers. If you force the type to `⟦integer⟧`, G1ANT.Robot will ignore floats and round numbers to integers.

You can also force a whole [list](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ListStructure.md)) structure to have all of its elements as floats:

```G1ANT
♥price_list = ⟦list:float⟧399.99❚19❚458.59❚199
dialog ♥price_list
```

In case of floating point numbers, it’s important to be aware of differences with interpreting dots and commas in numbers, depending on your system’s locale setting. In English notation, dots are interpreted as decimal separators, whereas commas separate thousands. But when you switch to some European locale, such as Polish, which uses comma as a decimal separator, the same numbers can be interpreted differently. This problem can be solved by using the [`♥locale`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/G1ANT.Addon.Core/Variables/LocaleVariable.md)) special variable.