# list

This structure stores multiple countable ordered values within a single variable. It behaves as a “container” and the values can occur a number of times. Every value inside of a list has to be separated with an [array separator](G1ANT.Manual/appendices/special-characters/array-separator.md) (❚). What is more, the values have to be of the same structure: [text](TextStructure.md), [integer](IntegerStructure.md), [datetime](DateTimeStructure.md), [date](DateStructure.md), etc. If you accidentally insert a different value type into a list, G1ANT.Robot will convert it to the structure of the first value from the list, because the first element defines the type of a list.

The list structure has the following indexes:

| Index   | Type    | Description                                    |
| ------- | ------- | ---------------------------------------------- |
| `first` | text    | Returns the first element in a list            |
| `last`  | text    | Returns the last element in a list             |
| `count` | integer | Returns the total number of elements in a list |
| `add`   | text    | Adds another element to a list                 |

## Example

In the following script a simple, 3-element list is created, then three dialog boxes are displayed showing how you can use list indexes:

```G1ANT
♥list = value1❚value 2❚value 3
dialog ‴List elements: ‴♥list
dialog ‴Total elements: ‴♥list⟦count⟧
dialog ‴Second element: ‴♥list⟦2⟧
```

Individual elements not only can be read, but also written:

```G1ANT
♥fruits = apple❚mango❚melon❚kiwi
♥fruits⟦2⟧ = banana
dialog ♥fruits
```

You can also add a new element to an existing list:

```G1ANT
♥fruits = apple❚mango❚melon❚kiwi
♥fruits⟦add⟧ = banana
dialog ♥fruits
```