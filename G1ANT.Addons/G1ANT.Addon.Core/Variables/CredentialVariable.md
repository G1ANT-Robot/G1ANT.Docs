# credential

## Syntax

```G1ANT
⟦text⟧ = ♥credential⟦index⟧
```

## Description

Reads the value of a specified key stored in the [Credential Container](../../../g1ant.robot-window/auxiliary-windows/credential-container.md).

## Example

```G1ANT
mail.imap imap.google.com login ♥credential⟦mail:login⟧ password ♥credential⟦mail:password⟧ sincedate 2019-01-01 onlyunreadmessages true result ♥emails
```

The `mail.imap` command will retrieve unread email messages from the GMail IMAP server using user credentials stored in the Credential Container in `mail:login` and `mail:password` fields.
