# selenium.click

## Syntax

```G1ANT
selenium.click waitfornewwindow ⟦bool⟧ search ⟦text⟧ by ⟦text⟧ iframesearch ⟦text⟧ iframeby ⟦text⟧
```

## Description

This command clicks a specified element on an active webpage.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
| `waitfornewwindow` | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | false | If set to `true`, the command should wait for a new window to appear after clicking the specified element |
|`search`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | Phrase to find an element by |
|`by`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Specifies an element selector: `id`, `class`, `cssselector`, `tag`, `xpath`, `name`, `query`, `jquery` |
|`iframesearch`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Phrase to find an iframe by |
|`iframeby`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  | Specifies an iframe selector: `id`, `class`, `cssselector`, `tag`, `xpath`, `name`, `query`, `jquery` |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                         | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutselenium](../Variables/TimeoutSeleniumVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                              | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                              | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                              | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                              | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

> **Note:** the `selenium.` commands require opening a browser with the `selenium.open` command first, and they refer to the browser’s first tab by default. If you have more tabs opened and want to use the `selenium.` commands on a tab other than the first one, use the `selenium.activatetab` command to change the active tab.

## Example

This example shows how to click an element on a website: the robot opens Chrome, maximizes its window, then the `selenium.click` command searches for a class called `btn-print` and clicks this element (a printer icon). A printer-friendly version of the page appears and the two `keyboard` commands start printing of the document:

```G1ANT
selenium.open chrome url https://www.cia.gov/library/publications/the-world-factbook/geos/dj.html
window ✱Factbook✱ style maximize
selenium.click search btn-print by class
keyboard ⋘CTRL+P⋙
keyboard ⋘ENTER⋙
```

> **Note:** The element could also be searched by other selectors: `id`, `class`, `cssselector`, `tag`, `xpath`, `name`, `query`, `jquery`. In order to search any element on a website using the `selenium.click` command, you need to use web browser developer tools (right-click an element and select `Inspect element` or `Inspect` from the resulting context menu).