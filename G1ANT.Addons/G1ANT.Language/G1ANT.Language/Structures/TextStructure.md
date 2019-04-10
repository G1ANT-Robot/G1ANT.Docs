# text

This structure stores text values.

## Example

Variables can be recognized automatically as text structure:

```G1ANT
♥text = Please call our support.
```

Or they can be forced (cast), when you want to use numbers as text, for example:

```G1ANT
♥text = ⟦text⟧12345
```

Individual characters in a text variable can be addressed using indexes:

```G1ANT
♥myText = 123456789ThisIsMyText
-addressing the 4th character in a variable:
dialog ♥myText⟦4⟧
-addressing characters from 4 to 13 in a variable:
dialog ♥mytext⟦4:13⟧
```

   
