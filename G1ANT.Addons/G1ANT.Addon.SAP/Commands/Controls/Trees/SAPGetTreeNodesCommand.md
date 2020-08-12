# sap.getreenodes

## Syntax

```G1ANT
sap.getreenodes parenttree ⟦sapcomponent⟧ key ⟦text⟧ path ⟦text⟧
```

## Description
Returns all tree nodes of a tree in a flat structure.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `parenttree`   | [sapcomponent](../../../Structures/SapComponentStructure.md)       | **yes**  |               | Tree which is parent of the tree node. This parameter must contain `sapomponent` with tree. |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`      | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.


## Result
Returns all tree nodes in a flat structure (a [list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) 
structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structures with node components).

Each element of list has following properties:

| Property name     | Type                                                         | Description                                                  |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Key`            | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Unique (within parent tree) key of the node, which is string containing absolute index of a node filled with zeros to the length of 8. Read-only. |
| `RelativePath`  | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Same as `Path`, used only for compatibility with Addon internals. Read-only. |
| `Path`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Backslash-separated path inside the tree built from relative indexes of nodes within their parent nodes. For example `2\1`, which means first child of second root node. Read-only. |
| `Name`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Same as `Key`, used only for compatibility with Addon internals. Read-only. |
| `Text`        | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Display caption of a node. Read-only. |
| `Level`        | [integer](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)     | Nesting level. Root nodes have `Level` equal to 0. Read-only. |


##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can see all the details
of your node on the `SAP UI object tree`.
Also, you can view details of specific node on `Variables` panel if you assign
a node from node list to a variable.