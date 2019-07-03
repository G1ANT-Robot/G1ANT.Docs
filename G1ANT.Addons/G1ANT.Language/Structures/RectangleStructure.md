# rectangle

This structure is designed to store coordinates of pixels in the two rectangle's corners — top left and bottom right — in `x1⫽y1⫽x2⫽y2` format, where `x1⫽y1` are the coordinates of the top left corner and `x2⫽y2` are the coordinates of the bottom right corner. The values are separated with the [point separator](../../../appendices/special-characters/point-separator.md) character.

The rectangle structure has six fields:

| Field    | Type    | Description                       |
| -------- | ------- | --------------------------------- |
| `left`   | integer | Top left pixel’s X coordinate     |
| `top`    | integer | Top left pixel’s Y coordinate     |
| `right`  | integer | Bottom right pixel’s X coordinate |
| `bottom` | integer | Bottom right pixel’s Y coordinate |
| `width`  | integer | Width of a rectangle              |
| `height` | integer | Height of a rectangle             |

## Example

In this script a rectangle variable is declared and then the rectangle’s properties (fields values) are displayed in dialog boxes:

```G1ANT
♥rectangle = 5⫽15⫽100⫽200
dialog ♥rectangle⟦width⟧
dialog ♥rectangle⟦height⟧
dialog ♥rectangle⟦left⟧
dialog ♥rectangle⟦top⟧
dialog ♥rectangle⟦right⟧
dialog ♥rectangle⟦bottom⟧
```

Width and height are the lengths of rectangle's sides. G1ANT.Robot calculates these lengths based on the corners’ coordinates.

Rectangles can also be easily inserted with the `Rectangle` tool available from `Insert` menu or using **Ctrl+R** keyboard shortcut.