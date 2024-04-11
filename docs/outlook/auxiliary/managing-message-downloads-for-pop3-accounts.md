---
title: "Managing message downloads for POP3 accounts"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: b4218aa6-1591-49db-9782-f286135fc79a
description: "This section describes how the POP3 provider of Outlook uses the Unique ID Listing (UIDL) history on a POP3 account to identify messages that the provider has downloaded or deleted from the POP3 server, to avoid downloading the same message more than once."
---

# Managing message downloads for POP3 accounts

This section describes how the POP3 provider of Outlook uses the Unique ID Listing (UIDL) history on a POP3 account to identify messages that the provider has downloaded or deleted from the POP3 server, to avoid downloading the same message more than once.
  
## Introduction to POP

The Post Office Protocol (POP) specifies an application layer protocol for an email client such as Outlook to download email messages from a mail server. It allows a user to download a copy of an email message to a local device (such as a smart phone or computer), and either leave a copy on the server or delete it. The protocol supports only one mail client to be connected to the mailbox at one time. It specifies only how to retrieve but not send email messages from the mail server. When using POP, a mail client typically has to check for new email messages, connects to the mail server for only the amount of time it takes to download new messages, and does not stay connected to the server to get new mail notifications. POP supports only email messages but not other item types such as contacts and appointments unless they are encapsulated in an email. POP3 is version 3 of the protocol.
  
Messages for a POP account are identified by unique identifiers (UIDs). An email client that leaves mail on the server uses the UIDL command to retrieve the UIDL map that associates each message that has been delivered to the mailbox to its UID. The client also gets the UIDL history for messages that have been downloaded or deleted for the Inbox on that client. Based on the UIDL history, the client can determine which messages are new and should be downloaded.

- [Locating the message download history for a POP3 account](locating-the-message-download-history-for-a-pop3-account.md): This topic describes how a mail client accesses the [PidTagAttachDataBinary](https://msdn.microsoft.com/library/3b0a8b28-863e-4b96-a4c0-fdb8f40555b9%28Office.15%29.aspx) property to get the UIDL history for messages in the client Inbox of a POP3 account. 
    
- [Parsing the message download history for a POP3 account](parsing-the-message-download-history-for-a-pop3-account.md): This topic describes how to parse the POP3 BLOB that represents the UIDL history for messages in the client Inbox of a POP3 account, to identify the messages that have been downloaded or deleted on that account.
    
## See also

- [Outlook account management](outlook-account-management.md)    
- [Locating the message download history for a POP3 account](locating-the-message-download-history-for-a-pop3-account.md) 
- [Parsing the message download history for a POP3 account](parsing-the-message-download-history-for-a-pop3-account.md)   
- [PROP_POP_LEAVE_ON_SERVER](prop_pop_leave_on_server.md)  
- [Constants (Account management API)](constants-account-management-api.md)    
- [Properties (Account management API)](properties-account-management-api.md)
    

