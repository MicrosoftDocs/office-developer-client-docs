---
title: Accounts
TOCTitle: Accounts
ms:assetid: 28df6dbd-4d24-42f3-91c1-fd8b3a4ea722
ms:mtpsurl: https://msdn.microsoft.com/library/office/ff184597(v=office.15) 
ms:contentKeyID: 55119790
ms.date: 07/24/2014
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Accounts 

This section provides sample tasks that involve email accounts. Examples of email accounts are Microsoft Exchange Server, Post Office Protocol 3 (POP3), Internet Message Access Protocol (IMAP), and Hypertext Transfer Protocol (HTTP) accounts. An account for the current profile is represented by an [Account](/dotnet/api/microsoft.office.interop.outlook.account) object.


|Topic|Description|
|:----|:----------|
|[Get account information](how-to-get-account-information.md) | Takes as an input argument a trusted Microsoft Outlook [Application](/dotnet/api/microsoft.office.interop.outlook.application) object, and uses the **Account** object to display the details of each account that is available for the current Outlook profile.|
|[Create a sendable item for a specific account based on the current folder](how-to-create-a-sendable-item-for-a-specific-account-based-on-the-current-folder.md) | Contains two code examples that show how to create a sendable email item and meeting request, and then send them by using a specific account that is based on the current folder.|
|[Get the account for a folder](how-to-get-the-account-for-a-folder.md) | Gets the account that is associated with a folder in the current session.|
|[Get information about multiple accounts](how-to-get-information-about-multiple-accounts.md) | Obtains and displays miscellaneous information about each account in the current profile.|
|[Send a mail item by using a Hotmail account](how-to-send-a-mail-item-by-using-a-hotmail-account.md) | Uses the [SendUsingAccount](/dotnet/api/microsoft.office.interop.outlook._mailitem.sendusingaccount) property to send a mail item by using a Windows Live Hotmail account.|

## See also

- [Exchange users](exchange-users.md)
- [Mail](mail.md)
- [Recipients](recipients.md)
- [How do I... (Outlook 2013 PIA reference)](how-do-i-outlook-2013-pia-reference.md)

