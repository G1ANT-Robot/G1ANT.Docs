# bool

This structure is used for variables storing the Boolean values: `true` and `false`. It has two fields:

| Field    | Type    | Description                                                  |
| -------- | ------- | ------------------------------------------------------------ |
| `number` | integer | Numerical representation of a Boolean variable (`0` or `1`)  |
| `text`   | text    | Text representation of a Boolean variable (`true`,`yes`, `false` or `no`) |

## Example

The structure can be declared explicitly:

```G1ANT
♥x = ⟦bool⟧true
```

or without the `⟦bool⟧` declaration, because G1ANT.Robot will understand either `true`,`false`, `yes` or `no`:

```G1ANT
♥y = false
```

In G1ANT.Language, `true` and `yes` equal `1`, and `false` and `no` equal `0`. You can see it, when you use the numerical representation (`⟦number⟧` field) of a Boolean variable:

```G1ANT
♥var=true
dialog ♥var⟦number⟧
```
