# locale

## Syntax

```G1ANT
locale = ⟦text⟧
```

## Description

This variable sets locale for the commands that follow it.

## Example

```G1ANT
♥locale = en-US
♥piDot1 = 3.141
♥piCom1 = 3,141
program notepad
keyboard ‴♥locale: ♥piDot1 and ♥piCom1‴⋘ENTER⋙
♥locale = pl-PL
♥piDot2 = 3.141
♥piCom2 = 3,141
keyboard ‴♥locale: ♥piDot1 and ♥piCom1‴⋘ENTER⋙
keyboard ‴♥locale: ♥piDot2 and ♥piCom2‴
```

This example shows the differences with interpreting dots and commas in numbers when you change the locale setting. In English notation, dots are interpreted as decimal separators, whereas commas separate thousands and this is how both `♥pi` variables are printed in Notepad: *3.141* and *3141*. But when you switch to some European locale, such as Polish, which uses comma as a decimal separator, you can see that the first variable is now presented in new notation. Meanwhile, the same values (`3.141` and `3,141`) declared as new variables are interpreted identically: as *3,141*.