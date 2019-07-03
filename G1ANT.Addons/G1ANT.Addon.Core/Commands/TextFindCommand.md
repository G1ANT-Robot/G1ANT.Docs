# text.find

## Syntax

```G1ANT
text.find text ⟦text⟧ search ⟦text⟧ search2 ⟦text⟧ search3 ⟦text⟧ regex ⟦text⟧ casesensitivity ⟦bool⟧
```

## Description

This command searches for some text within another text or a variable and assigns the result to a specified variable.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`text`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes| |Source text or a variable to be searched|
|`search, search2, search3`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  |Text to be found in a variable or text|
|`regex`| [text](../../G1ANT.Language/Structures/TextStructure.md) | no |  |[Regular expression](../../../appendices/regex.md) to be used in order to find a text value |
|`casesensitivity`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | true | Switches case sensitivity on or off |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example 1

In the example below the source text is stored in the `♥source` variable. The `text.find` command searches for all characters between the words `Name:` and `Surname:`, using the [Search Place](../../../appendices/special-characters/search-place.md) special character (✱). The resulting match (`John ` with space at the end) is displayed in a dialog box:

```G1ANT
♥source = ‴Name: John Surname: Smith‴
text.find ♥source search Name:✱Surname: result ♥name
dialog ♥name
```

## Example 2

Here, regular expression (regex) is used to find the street number data (building number) in the specified address stored in a variable. The result — “57B” in this case — is displayed in a dialog box:

```G1ANT
♥address = ‴57B Rathbone Place‴
text.find text ♥address regex ‴(\d+)-?(\d+)*(\D)?(w+)?‴ result ♥house
dialog ♥house
```

Visit [this site](https://regex101.com/) for an explanation on the regex used here.

## Example 3

This is an example of multiple searches within one `text.find` command. The first search — `Wack✱in.` — returns all characters after the first word (“Wack”) and before the last one (“in.”). The second search narrows this result further to all characters between the words “window” and “blinds”, and the last search strips the result down to a phrase: “ munch on tasty moths or sweet beast” (notice the white space character at the beginning of the resulting phrase):

```G1ANT
♥catText = Wack the mini furry mouse run outside as soon as door open yet run in circles, or try to jump onto window and fall while scratching at wall so munch on tasty moths or sweet beast. Play time destroy the blinds, and jump around on couch, meow constantly until given food, so meow to be let in.
text.find text ♥catText search Wack✱in. search2 window✱blinds search3 ‴at wall so✱. Play‴ result ♥textBefore
dialog ♥textBefore
```

## Example 4

Here’s an example of mixing multiple searches with regex search. The first search returns all characters between `<html>` and `</html>` tags, then between `<crazydiv>` and `</crazydiv>` tags, and finally the regex searches for three consecutive digits inside the result and returns “123”:

```G1ANT
♥html = <html><body>This is fake page With some spaces<crazydiv>`#$**&amp; and special ch`rs !09 <number>123</number>();</crazydiv> '|+</body></html>
text.find text ♥html search <html>✱</html> search2 <crazydiv>✱</crazydiv> regex \d\d\d result ♥toExpect
dialog ♥toExpect
```

