# procedure

This structure stores names of procedures. It can be used not only to directly call a procedure, but also indirectly — with a variable.

### Example

The following script utilizes procedure structure to store the procedure names in a list variable, so that the procedures can be called consecutively from within a `foreach` loop. The procedure names, which are read from a variable, are also used in dialog messages:

```G1ANT
♥proclist = no1❚no2❚no3

foreach ♥proc in ♥proclist
  call ♥proc
end

procedure no1
  dialog ‴This is procedure ‴♥proc
end

procedure no2
  dialog ‴And this is procedure ‴♥proc
end

procedure no3
  dialog ‴And finally, procedure ‴♥proc
end
```

