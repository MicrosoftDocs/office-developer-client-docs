---
title: "Opening a message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 142c4975-08df-4501-9996-557aa44eafb3
description: "Last modified: July 23, 2011"
---

# Opening a message
 
**Applies to**: Outlook 
  
### To open a message
  
1. Retrieve the message's entry identifier from one of the following sources:
    
   - The row that represents the message in the contents table of its parent folder. For more information about working with a folder contents table, see [Contents Tables](contents-tables.md).
    
   - The **lpEntryID** member of the [NEWMAIL_NOTIFICATION](newmail_notification.md) structure that is sent with a new mail notification. For more information about receiving and handling notifications, see [Handling Notifications](handling-notifications.md).
    
   - A call to the message's [IMAPIProp::GetProps](imapiprop-getprops.md) method requesting the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property. 
    
2. Call one of the following **OpenEntry** methods to open the message, setting  _lpEntryID_ to the message's entry identifier: 
    
   - [IMAPIContainer::OpenEntry](imapicontainer-openentry.md)
    
   - [IMsgStore::OpenEntry](imsgstore-openentry.md)
    
   - [IMAPISession::OpenEntry](imapisession-openentry.md)
    
  The fastest method is usable only for incoming messages and involves calling the receive folder's **IMAPIFolder::OpenEntry** method. The next fastest method, calling the message store's **IMsgStore::OpenEntry** method, is usable for all messages as is the slowest method, calling **IMAPISession::OpenEntry**.
    
> [!NOTE]
> Folders and their contents tables can be closed at any time without adversely affecting any of the messages that were opened from within them. 
  
### To open a message that has been saved on disk
  
1. Call **StgOpenStorage** to retrieve an **IStorage** interface pointer, passing the name of the message file for the  _pwcsName_ parameter. 
    
   ```cpp
    LPSTORAGE pStorage = NULL;
    HRESULT hr = StgOpenStorage (L"MESSAGE.MSG", NULL,
                                STGM_TRANSACTED |
                                STGM_READWRITE |
                                STGM_SHARE_EXCLUSIVE,
                                NULL, 0, &pStorage);
    
   ```

2. Call **OpenIMsgOnIStg** to retrieve an **IMessage** interface pointer to access the message. 
    
   ```cpp
    LPMESSAGE pMessage = NULL;
    LPMALLOC pMalloc = MAPIGetDefaultMalloc();
    hr = OpenIMsgOnIStg (NULL, MAPIAllocateBuffer, MAPIAllocateMore,
                        MAPIFreeBuffer, pMalloc, NULL, pStorage,
                        NULL, 0, 0, &pMessage);
    
   ```


