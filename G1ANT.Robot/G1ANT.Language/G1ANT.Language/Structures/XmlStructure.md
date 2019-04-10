# xml

This structure stores the content of imported XML files as text into G1ANT.Robot using the [`text.read`](G1ANT.Addon.Core/G1ANT.Addon.Core/Commands/TextReadCommand.md) command. It can be then converted to the xml structure to enable various operations on the data.

## Example

This example shows how xml variables can be declared:

```G1ANT
text.read C:\xml.txt result ♥xmlTxt
♥xml = ⟦xml⟧♥xmlTxt
```

The xml structure fields depend on the XML document content. You can access individual fields by their names equal to XML nodes, for example:

```G1ANT
♥source=‴<?xml version="1.0" encoding="UTF-8"?><note><to>Robot</to><from>G1ANT</from><heading>Reminder</heading><body>Don't stop working!</body></note>‴
♥xml = ⟦xml⟧♥source
dialog ♥xml
dialog ♥xml⟦note⟧
dialog ♥xml⟦note/body⟧
```

You can also write new values in particular fields. Add the following lines to the example above and see the results:

```G1ANT
dialog ♥xml⟦note/heading⟧
♥xml⟦note/heading⟧ = Please!
dialog ♥xml⟦note/heading⟧
```



