# html

This structure stores values of imported HTML files.

A HTML file can be imported using the [`text.read`](](https://manual.g1ant.com/link/G1ANT.Addon.Core/G1ANT.Addon.Core/Commands/TextReadCommand.md)) command. It is imported as text by default, but can then be converted to the html structure to enable various operations on the data.

## Example

This example shows how HTML variables can be declared:

```G1ANT
text.read C:\html.txt result ♥htmlDoc
♥html = ⟦html⟧♥htmlDoc
```

The html structure fields depend on the HTML document content. You can access individual fields by their names equal to HTML nodes, for example:

```G1ANT
♥source = ‴<!doctype html><html lang="en"><head><meta charset="utf-8"/><link rel="shortcut icon" href="/favicon.ico"/><meta name="viewport" content="width=device-width,initial-scale=1,shrink-to-fit=no"/><meta name="theme-color" content="#000000"/><meta http-equiv="X-UA-Compatible" content="IE=edge"><link rel="manifest" href="/manifest.json"/><title>G1ANT.Manual</title><link href="/static/css/1.dd049548.chunk.css" rel="stylesheet"><link href="/static/css/main.aba137a9.chunk.css" rel="stylesheet"></head><body><noscript>You need to enable JavaScript to run this app.</noscript><div id="root"></div><script src="/static/js/1.d5964837.chunk.js">first script</script><script src="/static/js/main.22ab479a.chunk.js">second script</script></body></html>‴
♥html = ⟦html⟧♥source
dialog ♥html⟦//title⟧
dialog ♥html⟦//noscript⟧
dialog ♥html⟦//body⟧
dialog ♥html⟦//script⟧
dialog ♥html⟦//script[2]⟧
```


Not only can these parts be read, but also written:

```G1ANT
-now let's clear whole body of html:
♥html⟦//body⟧ = cleared
dialog ♥html
```

Please note, that the root of file has to be addressed with a `/` (slash), so before the HTML path `//` (double slash) must be added.
