# macronamespaces

## Syntax

```G1ANT
♥macronamespaces = ⟦text⟧
```

## Description

Defines a comma-separated list of namespaces required by C# snippets.

## Example

```G1ANT
dialog ♥macronamespaces
♥open = ⊂new System.Windows.Forms.OpenFileDialog().ShowDialog().ToString()⊃
dialog ♥open
♥macronamespaces = System.Windows.Forms
dialog ♥macronamespaces
♥openAgain = ⊂new OpenFileDialog().ShowDialog().ToString()⊃
dialog ♥openAgain
```

This example first displays the default namespace (*System*). Then, a C# snippet opens a common Open File dialog box. Whichever file you choose, the result displayed in the next dialog box will be *OK* unless you click Cancel — then the result displayed will be *Cancel*. When you define a new namespace (*System.Windows.Forms*), you can use a shortened C# snippet, which will do exactly the same as the first one.