# Index Of All Addon Elements


 All Commands

| Name | Description |
| ---- | ----------- |
| [image.expected](Commands/ImageExpectedCommand.md) | This command checks if `image1` is exactly the same as `image2` (or is displayed somewhere on the screen) and returns a true/false result |
| [image.find](Commands/ImageFindCommand.md) | This command finds a specified image in another image (or in a part of the screen/entire screen) and returns the coordinates of the matching image |
| [image.findrectangles](Commands/ImageFindRectanglesCommand.md) | This command finds objects separated by a black background in a specified image and returns a list of their coordinates, width and height |
| [image.sharpen](Commands/ImageSharpenCommand.md) | This command sharpens a specified image |
| [waitfor.image](Commands/WaitForImageCommand.md) | This command waits for a specified image to appear on the screen and returns the coordinates of the matching image |

 All Variables

| Name | Description |
| ---- | ----------- |
| [timeoutimageexpected](Variables/TimeoutImageExpectedVariable.md) | Determines the timeout value (in ms) for the image.expected command; the default value is 20000 (20 seconds) |
| [timeoutimagefind](Variables/TimeoutImageFindVariable.md) | Determines the timeout value (in ms) for the image.find and waifor.image commands; the default value is 20000 (20 seconds) |
