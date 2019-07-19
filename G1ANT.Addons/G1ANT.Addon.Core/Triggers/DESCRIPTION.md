# Triggering

Triggers can execute user defined processes based on events. There are three triggers that can be used by G1ANT.Robot: [File Trigger](FileTrigger.md), [Mail Trigger](MailTrigger.md) and [Schedule Trigger](ScheduleTrigger.md). Their names are self-explanatory, as they are activated on a specified file, mail or schedule event.

## Initial Arguments

These are the arguments needed for a trigger to be called before running the script. In order to set them, you need to follow these steps:

1. Select `Settings` from `Tools` menu.
2. In the resulting Settings window, navigate to the `Triggers` entry. Right-click it and select `Add` from the context menu.
3. Expand the `Triggers` entry by clicking its arrow on the left. You should see a new entry with the default `trigger1` name. Expand it.
4. Click the field next to the `TaskName` entry and enter the full path to the robot script file you have just saved. This is the script to be run by the trigger.
5. Click the field next to the `Class` entry and type the desired trigger name: `FileTrigger`, `MailTrigger` or `ScheduleTrigger`.
6. Right-click the `Arguments` entry and select `Add` from the context menu.
7. Expand the resulting `argument1` entry, click the field next to the `Key` entry and type the name of a key.
8. Click the field next to the `Value` entry and type the key value.
9. Repeat steps 6-8 to add more arguments.

Another way of defining a trigger is to paste some XML code between `<Triggers>` … `</Triggers>` tags in G1ANT.Robot.config file (its location is provided in the *File name:* drop down list at the top of Settings window). Here’s a sample code:

```G1ANT
<Trigger Class="FileTrigger" Name="test" TaskName="C:\Users\Robot\Documents\G1ANT.Robot\test.robot">
	<Arguments>
		<Argument Key="Directory">C:\Users\Robot\Documents\G1ANT.Robot</Argument>
	</Arguments>
</Trigger> 
```

Note that some possible arguments are not required to be set because they already have a default value.

### Arguments to Define a Trigger

- `Class` describes the type of a trigger (FileTrigger, ScheduleTrigger or MailTrigger)
- `Name` is a unique name declared to distinguish triggers of the same Class
- `TaskName` is either a name of a robot script (with or without extension) that should be launched by a trigger, or just a path to this script

### Argument to Define the Trigger Initial Arguments

`Key` is a name of a trigger initial argument; its value should be declared in a `Value` field or put between `<Argument>` ... `</Argument>` tags in the G1ANT.Robot’s config file.

## Task Arguments

These are the arguments that the trigger will pass to the script on its execution. In order to use them in the executed script, insert the `♥task` special variable with the name of an argument embraced with the `⟦⟧` double brackets special character (available with **Ctrl+[** keyboard shortcut), e.g.: `♥task⟦filepath⟧`.

For the list of possible task or initial arguments, refer to a description of a specific trigger.

> **Note:** Triggers are not active when G1ANT.Robot starts. Select `Activate` from the `Triggers` menu to enable triggering.

