# dictionary

The dictionary structure stores a dictionary entry, which is a key-value pair separated with an [array separator](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/special-characters/array-separator.md) (❚). Dictionaries are used in databases, for example.

## Example

Here is a simple declaration of a dictionary entry (key: `address`, value: `street`) and accessing a value of a specified key:

```G1ANT
♥entry = ⟦dictionary⟧address❚street
dialog ♥entry⟦address⟧
```

