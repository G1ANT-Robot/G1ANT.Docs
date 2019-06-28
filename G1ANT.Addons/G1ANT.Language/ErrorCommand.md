# error

## Syntax

```G1ANT
error error ⟦error⟧
```

## Description

This command allows error handling using variables of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure.

## Example

The script below shows how can an error be handled using the `errorcall` argument and the `error` command. The robot waits 200ms for the *test.txt* file to appear on the user’s Desktop. Since there’s no such file, the `errorproc` procedure is called and the error information is stored in the `♥errresult` variable. The procedure simply displays the stored error information — change the `error` command to `dialog` and see the difference:

```G1ANT
waitfor.file ♥environment⟦USERPROFILE⟧\Desktop\test.txt timeout 200 errorcall errorproc errorresult ♥errresult

procedure errorproc
    - Add your own logging and error handling here
    error ♥errresult
end
```

>**Note:** Before using the `error` command to display the error message in this example, you can apply your own logging and error handling.
