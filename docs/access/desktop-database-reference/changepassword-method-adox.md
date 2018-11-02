---
title: ChangePassword method (ADOX)
TOCTitle: ChangePassword method (ADOX)
ms:assetid: 999826a5-3e6b-b6da-b8f6-d61b9a50ceca
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249690(v=office.15)
ms:contentKeyID: 48546519
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ChangePassword method (ADOX)


**Applies to**: Access 2013, Office 2013



Changes the password for a user account.

## Syntax

*User*.ChangePassword*OldPassword*, *NewPassword*

## Parameters

- *OldPassword*

  - A **String** value that specifies the user's existing password. If the user doesn't currently have a password, use an empty string ("") for *OldPassword*.

- *NewPassword*

  - A **String** value that specifies the new password.

## Remarks

For security reasons, the old password must be specified in addition to the new password.

An error will occur if the provider does not support the administration of trustee properties.

