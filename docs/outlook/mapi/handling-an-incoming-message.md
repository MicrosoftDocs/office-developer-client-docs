---
title: "Handling an incoming message"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: d45d5ed9-41cd-4aaf-91d2-1e4a27bb16d4
---

# Handling an incoming message

**Applies to**: Outlook 2013 | Outlook 2016 
  
An incoming message is a message that has been sent across one or more messaging systems. It may have been sent only to you or to many other recipients. Incoming messages are placed in a receive folder designated to hold messages of a particular class. You can set up a different receive folder for each message class that you handle or use one folder for all of the classes.
  
If you have registered for new mail notifications with the message store, you will be notified whenever a message is placed in a receive folder. If you have not registered for new mail notifications, you must open the appropriate receive folder periodically to manually check for the arrival of new messages.
  
Clients register for new mail notifications by setting the parameters to [IMsgStore::Advise](imsgstore-advise.md) as follows: 
  
- Set  _cbEntryID_ to 0. 
    
- Set  _lpEntryID_ to NULL. 
    
- Set  _ulEventMask_ to fnevNewMail. 
    
The  _lpNotifications_ parameter in the call to your **IMAPIAdviseSink::OnNotify** method points to a **NEWMAIL\_NOTIFICATION** structure that contains information about the incoming message, such as its message class, its entry identifier, the entry identifier of its parent folder, and the contents of its **PR_MESSAGE_FLAGS** property. For more information about registering for and handling notifications, see [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md), [NEWMAIL_NOTIFICATION](newmail_notification.md), **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)), and [Handling Notifications](handling-notifications.md). 
  
Before displaying an incoming message to a user, determine if its message class is a class that your client supports. If not, ignore the message. If the class is one that you support, you can open and display the message with a form that is appropriate for the message class of the message. The choice of forms is based on message class. Messages that belong to the IPM class use a default form implemented by MAPI. Messages that belong to custom classes defined by clients can use either client-defined specialized forms or the MAPI default form.
  
## Open and display an incoming message
  
1. Call **IMsgStore::GetReceiveFolder** to retrieve the entry identifier of the receive folder for the message class of the message and pass this entry identifier to **IMsgStore::OpenEntry** to open the folder. For more information, see [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md), [IMsgStore::OpenEntry](imsgstore-openentry.md), and [Opening a Message Store Folder](opening-a-message-store-folder.md).
    
2. Call the receive folder's **IMAPIContainer::GetContentsTable** method to retrieve its contents table. For more information, see [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md). Call the table's **IMAPITable::QueryRows** method to retrieve all the rows in the table. For more information see [IMAPITable::QueryRows](imapitable-queryrows.md) and [Contents Tables](contents-tables.md). For more information about displaying a contents table, see [Displaying a Folder Contents Table](displaying-a-folder-contents-table.md).
    
3. If your client is interactive, allow the user to select a message from the table and determine the form to be used to display that message. Clients can use the default form provided by MAPI or a custom form. For more information, see [Handling MAPI Forms](handling-mapi-forms.md).
    
4. Call **IMsgStore::OpenEntry** to open the message. For more information, see [Opening a Message](opening-a-message.md).
    
5. Process the message text. For more information, see [Opening Message Text](opening-message-text.md).
    
6. Render each of the message attachments. For more information, see [Rendering an Attachment in Plain Text](rendering-an-attachment-in-plain-text.md) or [Rendering an Attachment in RTF Text](rendering-an-attachment-in-rtf-text.md).
    
7. Open an attachment if desired. For more information see [Opening an Attachment](opening-an-attachment.md).
    
## In this section

- [Opening Message Text](opening-message-text.md): Describes how to open the message text.
    
- [Rendering an Attachment in Plain Text](rendering-an-attachment-in-plain-text.md): Describes how to render an attachment in plain text.
    
- [Rendering an Attachment in RTF Text](rendering-an-attachment-in-rtf-text.md): Describes how to render an attachment in formatted text.
    
- [Opening an Attachment](opening-an-attachment.md): Describes how to open an attachment.
    

