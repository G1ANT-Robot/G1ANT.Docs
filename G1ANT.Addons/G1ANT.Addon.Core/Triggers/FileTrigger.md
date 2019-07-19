# File Trigger

File Trigger monitors files in a specified folder and provides information whether they were changed, deleted, renamed or there are some new created files.

## Initial Arguments

| Trigger Argument | Required | Default value | Description |
| -------- | ---- | -------- | ------------- |
| `Directory` | yes |  | Path of the folder to be monitored |
| `Filter` | no |  `*.*` | Determines what files are monitored in a directory; all files are watched by default (`*.*`) |
| `AddExistingFilesAtStart` | no | false | Determines whether all initially existing files will be triggered or not |

## Task Arguments

Arguments passed to the script for each file in the monitored folder:

| Trigger Argument | Description |
| -------- | ---- |
| `FilePath` | Path to a file in the monitored folder |
| `FileName` | Name of a file (with extension) |
| `FileNameWithoutExtension` | Name of a file (without extension) |
| `ChangeType` | Information about the type of modification that was applied to a file (created, changed, deleted or renamed) |
| `OldFilePath` | Path to the file that has been changed |

## Example of Defining a File Trigger in Settings

![FileTrigger Example](https://raw.githubusercontent.com/G1ANT-Robot/G1ANT.Addon.Core/develop/G1ANT.Addon.Core/Triggers/https://raw.githubusercontent.com/G1ANT-Robot/G1ANT.Manual/develop/-assets/filetriggerexample.png)

## Example of Defining a File Trigger in the Config File

```G1ANT
<Trigger Class="FileTrigger" Name="test" TaskName="C:\Users\Robot\Documents\G1ANT.Robot\test.robot">
	<Arguments>
		<Argument Key="Directory">C:\Users\Robot\Documents\G1ANT.Robot</Argument>
	</Arguments>
</Trigger> 
```

## Example

The script executed by the File Trigger can make use of task arguments mentioned earlier. The following line included in the script will display the full path to a file, which triggered the script execution, along with the information on the type of change to this file:

```G1ANT
dialog ‴Triggering file ♥task⟦filepath⟧ was ♥task⟦changetype⟧‴
```
