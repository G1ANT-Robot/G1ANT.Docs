# Schedule Trigger

Schedule Trigger executes tasks at a specified time.

## Initial Arguments

| Trigger Argument | Required | Default value | Description |
| -------- | ---- | -------- | ------------- |
| `CrontabExpression` | yes |  | Time specified for the trigger to be called at. For more information about setting this crontab argument, please visit [Crontab](https://crontab.guru/) website. |

## Task Arguments

| Trigger Argument | Description |
| -------- | ---- |
| `Time` | Amount of time it took the trigger to perform the action |

## Example of Defining a Schedule Trigger in Settings

![ScheduleTrigger in Settings](/G1ANT.Addon.Core/Triggers/https://manual.g1ant.com/link/G1ANT.Manual/-assets/scheduletriggerexample.png)

## Example of Defining a Schedule Trigger in the Config File

```G1ANT
<Trigger Class="ScheduleTrigger" Name="test" TaskName="C:\Users\Robot\Documents\G1ANT.Robot\test.robot">
	<Arguments>
		<Argument Key="CrontabExpression">5 4 * * *</Argument>
	</Arguments>
</Trigger>
```
