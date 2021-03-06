# Index Of All Addon Elements


 All Commands

| Name | Description |
| ---- | ----------- |
| [as400.open](Commands/AS400OpenCommand.md) | This command opens a terminal connection to work with the IBM AS/400 server |
| [imap.close](Commands/ImapCloseCommand.md) | This command closes IMAP connection to mail server |
| [imap.getmails](Commands/ImapGetEmailsCommand.md) | This command uses the IMAP protocol to check an email inbox and allows the user to analyze their messages received within a specified time span, with the option to consider only unread messages and/or mark all of the checked ones as read |
| [imap.open](Commands/ImapOpenCommand.md) | This command uses the IMAP protocol to check an email inbox and allows the user to analyze their messages received within a specified time span, with the option to consider only unread messages and/or mark all of the checked ones as read |
| [imap.reconnect](Commands/ImapReconnectCommand.md) | This command restores IMAP connection to mail server |
| [is.accessible](Commands/IsAccessibleCommand.md) | This command checks if a host is accessible |
| [mail.imap](Commands/MailImapCommand.md) | This command uses the IMAP protocol to check an email inbox and allows the user to analyze their messages received within a specified time span, with the option to consider only unread messages and/or mark all of the checked ones as read |
| [mail.moveto](Commands/MailMoveToCommand.md) | This command moves a selected message to another folder |
| [mail.smtp](Commands/MailSmtpCommand.md) | This command sends a mail message from a provided email address to a specified recipient |
| [ping](Commands/PingCommand.md) | This command pings a specified IP address and returns an approximate round-trip time in milliseconds |
| [rest](Commands/RestCommand.md) | This command prepares a request to a desired URL with a selected method |
| [vnc.connect](Commands/VncConnectCommand.md) | This command connects to a remote machine with a running VNC server, using a remote desktop connection |

 All Variables

| Name | Description |
| ---- | ----------- |
| [timeoutconnect](Variables/TimeoutConnectVariable.md) | Determines the timeout value (in ms) for the is.accessible and ping commands; the default value is 1000 (1 second) |
| [timeoutmailsmtp](Variables/TimeoutMailSmtpVariable.md) | Determines the timeout value (in ms) for the mail.smtp command; the default value is 10000 (10 seconds) |
| [timeoutremotedesktop](Variables/TimeoutRemoteDesktopVariable.md) | Determines the timeout value (in ms) for the vnc.connect command; the default value is 10000 (10 seconds) |
| [timeoutrest](Variables/TimeoutRestVariable.md) | Determines the timeout value (in ms) for the rest command; the default value is 5000 (5 seconds) |
