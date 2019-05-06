# newline

## Syntax

```G1ANT
⟦text⟧ = ♥newline
```

## Description

Allows to insert a new line (carriage return and line feed character) into text. It’s equal to this C# snippet:

```G1ANT
♥altNewLine = ⊂"\r\n"⊃
```

## Example

This simple script shows how to use the `♥newline` variable. When it’s placed in text, new lines will be created. If you don’t want to have the extra spaces before and after the variable, you should use either the ‴ special character to separate text from the variable or the C# snipped mentioned above instead. You can see the the difference in the following example:

```G1ANT
♥text = This is the first line, ♥newline This is the second line, ♥newline And this is the third line
dialog ♥text
♥text = ‴This is the first line,‴♥newline‴This is the second line,‴♥newline‴And this is the third line‴
dialog ♥text
♥text = This is the first line,⊂"\r\n"⊃This is the second line,⊂"\r\n"⊃And this is the third line
dialog ♥text
```
