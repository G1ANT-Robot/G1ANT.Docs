# attachment
The attachment structure stores current information about a mail attachment, which was downloaded with the `mail.` commands and stored in the `attachments` field of the [mail](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/MailStructure.md)) structure. It contains the following fields:

| Field  | Type | Description                                                  |
| ------ | ---- | ------------------------------------------------------------ |
| `name` | text | The full name (with extension) of the attachment             |
| `size` | text | Size of the attachment in bytes                              |
| `type` | text | Type of the attachment, for example “document”               |
| `path` | text | Path to the downloaded attachment on the local machine (in a temporary folder) |

## Example
This example shows how to download an attachment using the [`mail.imap`](https://github.com/G1ANT-Robot/G1ANT.Addon/blob/develop/G1ANT.Addon.Net/G1ANT.Addon.Net/Commands/MailImapCommand.md) command and save it on the desktop:

```G1ANT
♥host = yourmailhost
♥login = yourlogin
♥password = yourpassword
♥from = 5/1/2018 8:30:52 AM

mail.imap host ♥host port 993 login ♥login password ♥password sincedate ♥from todate ♥date onlyunreadmessages false markallmessagesasread false ignorecertificateerrors true result ♥messagesList

foreach ♥element in ♥messagesList
  ♥attachments = ♥element⟦attachments⟧
  foreach ♥singleAttachment in ♥attachments
    ♥path = ♥singleAttachment⟦path⟧
    dialog ♥path
    file.copy path ♥path destinationpath ♥environment⟦USERPROFILE⟧\Desktop\♥singleAttachment⟦name⟧‴
  end
end
```

First, the `mail.imap` command receives all emails from the given time period and stores them in the `♥messagesList` variable. Each of the email messages is then processed and its attachments (if any) are retrieved and stored in the `♥attachments` variable. Next, each attachment’s local path is displayed and then the file is copied to the user’s desktop using a proper filename, which is read from the `⟦name⟧` field of the variable.

> **Note:** The values for `♥host`, `♥login` and `♥password` variables are of course just examples. You have to provide your real mail server credentials for the command to work.

