---
title: "Handling message store notification"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3e0cc2f9-a88d-4cec-bef5-b60f2ec80f1c
description: "Last modified: March 09, 2015"
---

# Handling message store notification
  
**Applies to**: Outlook 
  
To register for message store notifications, call either the [IMAPISession::Advise](imapisession-advise.md) or [IMsgStore::Advise](imsgstore-advise.md) method and specify a message store, folder, or message entry identifier in the contents of the  _lpEntryID_ parameter. Message store providers support both object and table notifications. Whether you register with particular message store objects, with the folder hierarchy and contents tables that describe these objects, or with both objects and tables depends on the notifications you expect to see, the calls you make to perform operations, and how the message store provider supports notification. 
  
Because MAPI allows flexibility in how providers support notifications, be aware that you will not always receive the same type of notification in response to a particular event from all message store providers. Some message store providers do not support notifications at all. To determine if the message store you are using supports notification, look for the STORE_NOTIFY_OK bit in its **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property.
  
At one end of the spectrum of message store providers that support notification are the providers that generate "rich" notifications; these providers send descriptive notifications for all registered advise sources. At the other end are the message store providers that support limited notifications; these providers send general notifications for a restricted number of advise sources. 
  
For example, if you copy a message to a folder with which you have registered to receive both object copied and object moved notifications, you may or may not receive the object copied notification. Whether or not you receive it depends on:
  
- The method that you called to perform the copy. This could be [IMAPIFolder::CopyMessages](imapifolder-copymessages.md), [IMAPIProp::CopyTo](imapiprop-copyto.md), or [IMAPIProp::CopyProps](imapiprop-copyprops.md).
    
- How the message store provider implements the copy method.
    
- Whether or not the message store provider supports object copied notifications on folders.
    
Because there are no strict guidelines that describe how to implement event notification for message store providers, clients cannot expect consistent behavior. MAPI does make recommendations as to how message store providers implement event notification and the following table outlines these recommendations. Read the table as follows: after you perform the operation in the first column, expect to receive a notification of the type listed in the second column if you have registered for that type with the object listed in the third column. For example, after you have created a folder, you will receive an  _fnevObjectCreated_ notification only if you have registered for  _fnevObjectCreated_ notifications with the message store. 
  
|**Operation**|**Event type**|**Advise source**|
|:-----|:-----|:-----|
|Create a folder  <br/> | _fnevObjectCreated_ <br/> |Message store  <br/> |
|Delete a folder  <br/> | _fnevObjectDeleted_ <br/> |Message store Deleted folder  <br/> |
|Move a folder from one folder to another  <br/> | _fnevObjectMoved_ <br/> |Message store Moved folder  <br/> |
|Copy a folder from one folder to another  <br/> | _fnevObjectCopied_ <br/> |Message store and copied folder (no  _fnevObjectCreated_ notification sent for the new copy of the folder)  <br/> |
|Change in a computed folder property (**PR_SUBFOLDERS** ([PidTagSubfolders](pidtagsubfolders-canonical-property.md)), **PR_CONTENT_UNREAD** ([PidTagContentUnreadCount](pidtagcontentunreadcount-canonical-property.md)), **PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md))  <br/> | _fnevObjectModified_ <br/> |Message store Changed folder (No notification to parent folder)  <br/> |
|Create a message  <br/> | _fnevObjectCreated_ <br/> |Message store  <br/> |
|Delete a message, causing a change in the parent folder's **PR_CONTENT_COUNT** property  <br/> | _fnevObjectDeleted_ <br/> |Message store Deleted message  <br/> |
|Move a message from one folder to another  <br/> | _fnevObjectMoved_ <br/> |Message store Moved message  <br/> |
|Copy a message from one folder to another  <br/> | _fnevObjectCopied_ <br/> |Message store Copied message (No  _fnevObjectCreated_ notification for new copy of the message)  <br/> |
|Save a message, causing a change in the parent folder's **PR_CONTENT_COUNT** property  <br/> | _fnevObjectCreated_ <br/> |Message store on first save only  <br/> |
|Save a message  <br/> | _fnevObjectModified_ <br/> |Message store on saves after the first save Changed message (No notification to parent folder)  <br/> |
|Complete a search operation  <br/> | _fnevSearchComplete_ <br/> |Message store Search folder  <br/> |
|New message  <br/> | _fnevNewMail_ <br/> |Message store  <br/> |
   
> [!NOTE]
> When you receive an object modified notification, remember that the property tag array portion of the [OBJECT_NOTIFICATION](object_notification.md) structure pointed to by the  _lpNotifications_ parameter in the **OnNotify** call may or may not be NULL. Message store providers are not required to insert property information in this array and most do not. Make sure your **OnNotify** method can handle the case where the  _lpPropTagArray_ pointer is NULL. 
  
For most, if not all object notifications, update the view of the affected folder or folders.
  

