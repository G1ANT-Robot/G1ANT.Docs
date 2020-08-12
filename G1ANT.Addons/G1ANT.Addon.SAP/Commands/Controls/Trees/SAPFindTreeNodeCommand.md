# sap.findtreenode

## Syntax

```G1ANT
sap.findtreenode parenttree ⟦sapcomponent⟧ key ⟦text⟧ path ⟦text⟧
```

## Description
Returns tree node by key (string with unique value) or by path (backslash-separated path inside the tree built
from relative indexes of nodes within their parent nodes).


## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `parenttree`   | [sapcomponent](../../../Structures/SapComponentStructure.md)       | **yes**  |               | Tree which is parent of the tree node. This parameter must contain SAPComponent with GuiShell (`⟦sapcomponent⟧<GuiShell>`). |
| `key`           | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | yes if `Path` is empty | | Unique key of the node, which is string containing absolute index of a node filled with zeros to the length of 8. You must set `Path` or `Key` argument. |
| `path`          | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | yes if `Key` is empty | | Backslash-separated path inside the tree built from relative indexes of nodes within their parent nodes. For example `2\1`, which means first child of second root node. You must set `Path` or `Key` argument. |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`      | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.


## Result
Returned node has following properties:

| Property name     | Type                                                         | Description                                                  |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Key`            | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Unique (within parent tree) key of the node, which is string containing absolute index of a node filled with zeros to the length of 8. Read-only. |
| `RelativePath`  | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Same as `Path`, used only for compatibility with Addon internals. Read-only. |
| `Path`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Backslash-separated path inside the tree built from relative indexes of nodes within their parent nodes. For example `2\1`, which means first child of second root node. Read-only. |
| `Name`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Same as `Key`, used only for compatibility with Addon internals. Read-only. |
| `Text`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Display caption of a node. Read-only. |
| `Level`        | [integer](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Nesting level. Root nodes have `Level` equal to 0. Read-only. |

> ###### Example
Example tree node object serialized to json returned by this command:
```json
{
  "Key": "00000003",
  "Position": "21, 45, 32, 20",
  "ScreenPosition": "33, 538, 32, 20",
  "Name": "00000003",
  "Type": "GuiTreeNode",
  "TypeAsNumber": -1,
  "Path": "1\2",
  "RelativePath": "1\2",
  "Id": "/app/con[0]/ses[0]/wnd[0]/shell",
  "IsContainer": true
}
```
