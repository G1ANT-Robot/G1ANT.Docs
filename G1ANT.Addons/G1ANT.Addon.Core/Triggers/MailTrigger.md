# Mail Trigger

Mail Trigger provides information about incoming emails.

## Initial Arguments

| Trigger Argument | Required | Default value | Description |
| -------- | ---- | -------- | ------------- |
| `Host` | yes |  | IMAP server address |
| `Login` | yes |  | Login (e.g.: email address) for the account the emails will be sent from |
| `Password` | yes |  | Password for this email account |
| `Frequency` | no | 30000 | Time interval between updates on incoming emails (in milliseconds) |
| `Port` | yes |  | Incoming mail server port |

## Task Arguments

Arguments that are passed to the script on its execution for each incoming email:

| Trigger Argument | Description |
| -------- | ---- |
| `Title` | Title of an incoming mail |
| `AttachmentNames` | List of attachments in an incoming mail |
| `Content` | Incoming mail content (text) |
| `From` | Sender's email address |
| `To` | Recipient's email address |
| `HtmlBody` | Incoming mail content (HTML) |
| `Uid` | Unique identifier of a mail given by a server |
| `Date` | Sent date |
| `Priority` | Priority set by a sender |

## Example of Defining a Mail Trigger in Settings

![MailTrigger in Settings](https://raw.githubusercontent.com/G1ANT-Robot/G1ANT.Addon.Core/develop/G1ANT.Addon.Core/Triggers/https://raw.githubusercontent.com/G1ANT-Robot/G1ANT.Manual/develop/-assets/mailtriggerexample.png)

## Example of Defining a Mail Trigger in the Config File

```G1ANT
<Trigger Class="MailTrigger" Name="test" TaskName="C:\Users\Robot\Documents\G1ANT.Robot\test.robot">
	<Arguments>
		<Argument Key="Host">imap.gmail.com</Argument>
		<Argument Key="Login">example@example.com</Argument>
		<Argument Key="Password">password123</Argument>
		<Argument Key="Frequency">300000</Argument>
		<Argument Key="Port">993</Argument>
	</Arguments>
</Trigger> 
```

## Example

The script executed by the Mail Trigger can make use of task arguments mentioned earlier. The following line included in the script will display the title and the recipient’s name of an email, which triggered the script execution:

```G1ANT
dialog ‴Incoming email: ♥task⟦title⟧ to task⟦to⟧‴
```


