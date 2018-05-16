---
title: "MAPI Receive Folders"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 2e1287a3-0f15-4d9a-b7ee-738fce9cd51f
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Receive Folders

  
  
**Applies to**: Outlook 
  
A receive folder holds inbound messages of a particular message class. Receive folder associations can be established by clients, by the message store provider, or by MAPI. MAPI has two default receive folders: the root folder of the message store, and the Inbox folder of the interpersonal message (IPM) subtree. The root folder of the message store is the default receive folder for all interprocess communication (IPC) messages.
  
 The Inbox folder is created by MAPI for every new message store and acts as the default receive folder for the following message classes: 
  
- The IPM message class.
    
- The report message class.
    
- An empty, or missing, class.
    
All report messages, even those sent in response to an IPC message, are placed in the Inbox folder. IPC client applications that process their own reports must explicitly add a receive folder for the particular class of report. For example, if a client expects to receive messages with the class IPC.Paper.Order, it should call the [IMsgStore::SetReceiveFolder](imsgstore-setreceivefolder.md) method to establish a receive folder for reports with the class Report.IPC.Paper.Order. 
  
Receive folder associations are based on the hierarchical organization of message classes. Clients can explicitly establish an association between a receive folder and a message class or use the MAPI default receive folders. Typically, clients designate one folder to receive messages for a base class and all of its subclasses. For example, a typical client would establish an association for messages with the class **MyClass**. Then if the client received messages with classes **MyClass.Home** or **MyClass.Home.Kitchen.Computer**, these messages would go to the receive folder for the base class, **MyClass**.
  
There are three message store methods that clients use to work with receive folders:
  
- [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md)
    
- [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md)
    
- [IMsgStore::SetReceiveFolder](imsgstore-setreceivefolder.md)
    
The receive folder table is a listing of information about all of the receive folders established for a message store. Its required column set includes the message class, record key, and entry identifier.
  
To retrieve a receive folder for a particular message class, clients pass the message class string to the [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md) method. The message store provider returns an entry identifier for the corresponding folder. To implement **GetReceiveFolder**, a message store provider should use an algorithm that selects the folder whose associated message class matches the longest possible prefix of the specified message class. For example, assume the message store has the following associations between receive folders and message classes in its receive folder table:
  
- **IPM** messages are placed in the Inbox folder. 
    
- **IPM.Note.Sample** messages are placed in the Samples folder. 
    
The following table shows how messages with various classes would be routed to the appropriate receive folder.
  
|**Inbound message class**|**Receive folder**|
|:-----|:-----|
|**IPM.Note.Sample.Simple** <br/> |Samples folder  <br/> |
|**IPM.Note** <br/> |Inbox folder  <br/> |
|**IPM.Timecard** <br/> |Inbox folder  <br/> |
|**IPM.Note.Sample.Simple.Totally** <br/> |Samples folder  <br/> |
   
Clients call the **SetReceiveFolder** method to make an explicit association between a particular message class and receive folder. When a message is delivered to an empty message class, MAPI places the message in the receive folder that is defined for a prefix of the empty class. For example, if your client has a receive folder established for messages with class **IPM** and a message with class **IPM.Note.Test** is delivered, this message will be placed in the receive folder for the **IPM** message class. 
  
In calling **SetReceiveFolder**, clients typically pass a message class string and the entry identifier of the new receive folder. However, clients can pass in NULL for one or both of these parameters. The following table describes the behavior that results from specifying NULL for the message class and entry identifier parameters. 
  
|**_SetReceiveFolder_ parameter**|**Resulting behavior**|
|:-----|:-----|
|Entry identifier set to NULL  <br/> |The message store deletes the association between the specified message class and its existing receive folder. A new receive folder is not established.  <br/> Subsequent calls to **GetReceiveFolder** with this message class will return the receive folder for a prefix of the message class; for new message stores, **GetReceiveFolder** will return the Inbox in the IPM subtree.  <br/> |
|Message class set to NULL  <br/> |The message store changes the association for the empty message class to the indicated folder. Incoming messages whose class is otherwise unrecognized will go to this folder.  <br/> |
|Entry identifier and message class set to NULL  <br/> |The message store deletes the class/folder association for the empty message class. You should not set both parameters to NULL, because it typically results in inbound messages being placed in the root folder of the message store, a folder that is invisible to the client.  <br/> |
   
Although a message's class should never be empty, an empty message class can occur. It is the message store's responsibility to assign the message class to **IPM** for new outbound messages that have an empty class; it is the transport provider's responsibility to assign **IPM.Note** as the class for inbound messages that have any empty class. 
  
## See also

#### Concepts

[MAPI Folders](mapi-folders.md)

