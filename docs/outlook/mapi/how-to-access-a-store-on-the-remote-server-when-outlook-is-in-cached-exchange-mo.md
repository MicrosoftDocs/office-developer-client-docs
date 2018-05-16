---
title: "Access a Store on the Remote Server When Outlook is in Cached Exchange Mode"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 5c6df156-4015-2d0f-26b7-07055a3f7810
description: "Last modified: July 02, 2012"
 
 
---

# Access a Store on the Remote Server When Outlook is in Cached Exchange Mode

 
  
**Applies to**: Outlook 
  
This topic contains a code sample in C++ that shows how to use the **MAPI_NO_CACHE** flag to open a folder or a message on a message store on the remote server when Microsoft Office Outlook is in Cached Exchange Mode. 
  
Cached Exchange Mode permits Outlook to use a local copy of a user's mailbox while Outlook maintains an online connection to a remote copy of the user's mailbox on the remote Exchange server. When Outlook is running in Cached Exchange Mode, by default, any MAPI solutions that log on to the same session are also connected to the cached message store. Any data that is accessed and any changes that are made are made against the local copy of the mailbox.
  
A client or service provider can override the connection to the local message store and open a message or a folder on the remote store by setting the bit for **MAPI_NO_CACHE** in the  *ulFlags*  parameter when calling **[IMsgStore::OpenEntry](imsgstore-openentry.md)**. 
  
The following code sample shows how to call **IMsgStore::OpenEntry** with the **MAPI_NO_CACHE** flag set in the  *ulFlags*  parameter to open the root folder on the remote message store. 
  
```
HRESULT HrOpenRootFolder ( 
    LPMDB lpMDB, 
    LPMESSAGE* lpRootFolder) 
{ 
    ULONG ulObjType = NULL; 
    HRESULT hRes = lpMDB-&amp;gt;OpenEntry( 
        0,// size of entry ID       
        NULL,                                   // Pointer to entry ID 
        NULL,                                   // Use default interface (IMAPIFolder) 
        MAPI_BEST_ACCESS | MAPI_NO_CACHE,       // Flags 
        &amp;amp;ulObjType,
// Output parameter indicates the type of object returned 
        (LPUNKNOWN *) lpRootFolder));           // Pointer to put the opened folder in 
    return hRes; 
 
}
```

If you opened the message store with the **MDB_ONLINE** flag on the remote server, you do not have to use the **MAPI_NO_CACHE** flag. 
  
## See also

#### Concepts

[About MAPI Additions](about-mapi-additions.md)
  
[Open a Store on the Remote Server When Outlook is in Cached Exchange Mode](how-to-open-a-store-on-the-remote-server-when-outlook-is-in-cached-exchange-mode.md)
  
[Manage a Message in an OST Without Invoking a Synchronization in Cached Exchange Mode](how-to-manage-a-message-in-an-ost-without-invoking-a-synchronization.md)

