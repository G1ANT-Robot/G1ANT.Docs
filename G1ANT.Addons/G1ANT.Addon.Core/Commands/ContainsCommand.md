# contains

## Syntax

```G1ANT
contains dictionary ⟦dictionary⟧ key ⟦text⟧
```

## Description

This command checks if a specified dictionary contains a given key.

| Argument       | Type                                                         | Required | Default Value                                               | Description                                                  |
| -------------- | ------------------------------------------------------------ | -------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
|`dictionary`| [dictionary](../../G1ANT.Language/Structures/DictionaryStructure.md) | yes |  | Dictionary to be checked for a presence of a specified key |
|`key`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes | | Key to look for in a dictionary |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command result (`true` or `false`) will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In this simple example two dictionary entries are created containing `username:g1ant` and `password:mypass123` key-value pairs, then the robot checks whether this dictionary contains a key named `password`. Since it does, a dialog box displays *true* as the `contains` command result:

```G1ANT
♥dictionary = ⟦dictionary⟧username❚g1ant❚password❚mypass123
contains ♥dictionary key password
dialog ♥result
```

