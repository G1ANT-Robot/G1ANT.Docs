# sap.getchildren

## Syntax

```G1ANT
sap.getchildren parent ⟦sapcomponent⟧
```

## Description
Gets list of all `Parent`'s child components.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `parent`        | [sapcomponent](../../../Structures/SapComponentStructure.md)      | no       |               | Optional component which is one of parents of components to be found. This parameter must contain `sapcomponent` that is a container. |
| `result`        | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structure with components). |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)   | no      | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.


## Result
Gets the list of all `Parent`'s child components in a form of a [list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) 
structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structures. If nothing is found returned
list will be empty.

Properties of each component may vary, therefore no list will be presented here.

##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can view details of specific 
child component on `Variables` panel if you assign a component from the list
of child components to a variable.