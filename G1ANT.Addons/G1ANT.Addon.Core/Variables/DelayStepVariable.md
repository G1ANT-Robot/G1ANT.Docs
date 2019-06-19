# delaystep

## Syntax

```G1ANT
♥delaystep = ⟦integer⟧
```

## Description

Determines the delay value (in ms) before the next command is executed; the default value is 500.

The variable applies to the following commands:

- `as400.open`
- `chrome`
- `keyboard`
- `mouse`
- `outlook.close`
- `outlook.findmails`
- `outlook.newmessage`
- `outlook.open`
- `program`
- `vnc.connect`
- `waitfor.window`
- `watson.speechtotext`			
- `window`
- `word.close`
- `word.export`
- `word.gettext`
- `word.inserttext`
- `word.open`
- `word.replace`
- `word.runmacro`
- `word.save`
- `word.switch`

## Example

```G1ANT
♥delaystep = 3000
program notepad
keyboard Wait...
keyboard ‴ for...‴
keyboard ‴ IT!‴
```

The script above will execute each command with a 3-second delay.
