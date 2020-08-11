# sap.exists

## Syntax

```G1ANT
sap.exists path ⟦text⟧ parent ⟦sapcomponent⟧
```

## Description
Returns true if component with a given path exists.
Returns false if:
* path is incorrect;
* window, connection or session is not found;
* no component has been found by a given path;
* application (SAP Logon) has not been started or is incorectly registered (COM or ROT) or there is any other problem.


## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `path`          | [text](../../G1ANT.Language/Structures/TextStructure.md)          | **yes** | | Path to a SAP component, can be absolute (/app/con[0]/ses[0]/wnd[0]/path/to/component) or relative to window (path/to/component), session or connection |
| `parent`        | [sapcomponent](../../../Structures/SapComponentStructure.md)      | **yes**  |               | Optional one of parents of component to enable relative search, must contain `⟦sapcomponent⟧`. |
| `if`            | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.