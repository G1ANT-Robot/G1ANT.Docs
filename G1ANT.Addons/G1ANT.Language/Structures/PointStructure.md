# point

This structure stores pixel coordinates values. It uses `x⫽y` format, where XY values are separated with the [point separator](../../../appendices/special-characters/point-separator.md) character (⫽), and has two fields:

| Field | Type    | Description          |
| ----- | ------- | -------------------- |
| `x`   | integer | Pixel’s X coordinate |
| `y`   | integer | Pixel’s Y coordinate |

## Example

In the following script a point variable is declared, then X and Y coordinates are displayed separately and finally one of these coordinates is replaced with a new value:

```G1ANT
♥point = 935⫽580
dialog ♥point⟦x⟧
dialog ♥point⟦y⟧
♥point⟦x⟧ = 800
dialog ♥point
```

Mouse position is also stored in the point structure: you can insert a mouse position with the `Mouse position` tool available from `Insert` menu or using **Ctrl+E** keyboard shortcut.

