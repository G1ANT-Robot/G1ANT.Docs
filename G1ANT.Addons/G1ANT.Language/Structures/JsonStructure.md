# json

This structure stores the content of imported JSON files. A JSON file can be imported as text into G1ANT.Robot using the [`text.read`](../../G1ANT.Addon.Core/Commands/TextReadCommand.md) command. It can be then converted to the json structure to enable various operations on the data.

## Example

This example shows how json variables can be declared:

```G1ANT
text.read C:\json.txt result ♥jsonTxt
♥json = ⟦json⟧♥jsonTxt
```

The json structure fields depend on the JSON file content. You can access individual fields by their names equal to JSON key names. In the following script a sample JSON file is downloaded from the Web to the user’s Desktop, then its content is read, assigned to the `♥jsonTxt` variable  and displayed in a dialog box. Finally, the variable is converted to the json structure and values of specified keys are displayed in a dialog box:

```G1ANT
♥file = ♥environment⟦USERPROFILE⟧\Desktop\json.txt
file.download https://support.oneskyapp.com/hc/en-us/article_attachments/202761727/example_2.json filename ♥file
text.read ♥file result ♥jsonTxt
dialog ♥jsonTxt
♥json = ⟦json⟧♥jsonTxt
dialog ♥json⟦quiz.maths.q1.question⟧
dialog ♥json⟦quiz.sport.q1.options⟧
```

If you don’t want to download a sample file from the Web, you can use this code to replace lines 1-4 of the script above:

```G1ANT
♥jsonTxt = ‴{"quiz": {"sport": {"q1": {"question": "Which one is correct team name in NBA?","options": ["New York Bulls","Los Angeles Kings","Golden State Warriros","Huston Rocket"],"answer": "Huston Rocket"}},"maths": {"q1": {"question": "5 + 7 = ?","options": ["10","11","12","13"],"answer": "12"},"q2": {"question": "12 - 8 = ?","options": ["1","2","3","4"],"answer": "4"}}}}‴
```

You can also write new values in particular fields. Add the following lines to the example above and see the results:

```G1ANT
dialog ♥json⟦quiz.maths.q2.answer⟧
♥json⟦quiz.maths.q2.answer⟧ = 2
dialog ♥json⟦quiz.maths.q2.answer⟧
```

Please note that there is no way to write directly to the core (here: `quiz`). The core is allowed to be read only.

