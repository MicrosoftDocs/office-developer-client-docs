---
title: "IMAPIPropSaveChanges"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.SaveChanges
api_type:
- COM
ms.assetid: 864dbc3e-2039-435a-a279-385d79d1d13f
description: "Last modified: July 23, 2011"
---

# IMAPIProp::SaveChanges

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Makes permanent any changes that were made to an object since the last save operation. 
  
```cpp
HRESULT SaveChanges(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls what happens to the object when the **IMAPIProp::SaveChanges** method is called. The following flags can be set: 
    
NON_EMS_XP_SAVE
  
> Indicates that the message has not been delivered from a Microsoft Exchange Server. This flag should be used in combination with the [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method and the ITEMPROC_FORCE flag to indicate to a PST store that the message is eligible for rules processing before the Personal Folders file (PST) store notifies any listening client that the message has arrived. This rules processing only applies to new messages that are created with [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) on a server that is not an Exchange Server, in which case the Exchange Server would have already processed rules on the message. 
    
FORCE_SAVE 
  
> Changes should be written to the object, overriding any previous changes that were made to the object, and the object should be closed. Read/write permission must be set for the operation to succeed. The FORCE_SAVE flag is used after a previous call to **SaveChanges** returned MAPI_E_OBJECT_CHANGED. 
    
KEEP_OPEN_READONLY 
  
> Changes should be committed and the object should be kept open for reading. No additional changes will be made. 
    
KEEP_OPEN_READWRITE 
  
> Changes should be committed and the object should be kept open for read/write permission. This flag is usually set when the object was first opened for read/write permission. Subsequent changes to the object are allowed. 
    
MAPI_DEFERRED_ERRORS 
  
> Allows **SaveChanges** to return successfully, possibly before the changes have been fully committed. 
    
SPAMFILTER_ONSAVE
  
> Enables spam filtering on a message that is being saved. Spam filtering support is available only if the sender's email address type is Simple Mail Transfer Protocol (SMTP), and the message is being saved to a store for a Personal Folders file (PST).
    
## Return value

S_OK 
  
> The commitment of changes was successful.
    
MAPI_E_NO_ACCESS 
  
> **SaveChanges** cannot keep the object open for read-only permission if KEEP_OPEN_READONLY is set, or read/write permission if KEEP_OPEN_READWRITE is set. No changes are committed. 
    
MAPI_E_OBJECT_CHANGED 
  
> The object has changed since it was opened.
    
MAPI_E_OBJECT_DELETED 
  
> The object has been deleted since it was opened.
    
## Remarks

The **IMAPIProp::SaveChanges** method makes property changes permanent for objects that support the transaction model of processing, such as messages, attachments, address book containers, and messaging user objects. Objects that do not support transactions, such as folders, message stores, and profile sections, make changes permanent immediately. No call to **SaveChanges** is required. 
  
Because service providers do not have to generate an entry identifier for their objects until all properties have been saved, an object's **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property might not be available until after its **SaveChanges** method has been called. Some providers wait until the KEEP_OPEN_READONLY flag is set on the **SaveChanges** call. KEEP_OPEN_READONLY indicates that the changes to be saved in the current call will be the last changes that will be made on the object. 
  
Some message store implementations do not show newly created messages in a folder until a client saves the message changes by using **SaveChanges** and releases the message objects by using the [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) method. In addition, some object implementations cannot generate a **PR_ENTRYID** property for a newly created object until after **SaveChanges** has been called, and some can do so only after **SaveChanges** has been called by using KEEP_OPEN_READONLY set in  _ulFlags_.
  
## Notes to implementers

If you receive the KEEP_OPEN_READONLY flag, you have the option of leaving the object's access as read/write. However, a provider can never leave an object in a read-only state when the KEEP_OPEN_READWRITE flag is passed.
  
When a client saves multiple attachments to multiple messages, it calls the **SaveChanges** method for every attachment and every message. Often clients will set MAPI_DEFERRED_ERRORS for each of these calls except for the last one. You can return errors either with the last call or earlier calls. You can even ignore the flag. 
  
If either KEEP_OPEN_READWRITE or KEEP_OPEN_READONLY is set together with MAPI_DEFERRED_ERRORS, you can ignore the error deferment request. If MAPI_DEFERRED_ERRORS is not set in  _ulFlags_, one of the previously deferred errors can be returned for the **SaveChanges** call. 
  
Whether a remote transport provider provides a functional implementation of this method is optional and depends on other design choices in your implementation. If you implement this method, do so according to the documentation here. Because folder objects and status objects are not transacted, at a minimum a remote transport provider's implementation of **SaveChanges** must return S_OK without actually doing any work. 
  
## Notes to callers

If a client passes KEEP_OPEN_READONLY, calls the [IMAPIProp::SetProps](imapiprop-setprops.md) method, and then calls **SaveChanges** again, the same implementation might fail. 
  
After receiving MAPI_E_NO_ACCESS from a call in which you set KEEP_OPEN_READWRITE, you will continue to have read/write permission to the object. You can call **SaveChanges** again, passing either the KEEP_OPEN_READONLY flag or no flags with KEEP_OPEN_SUFFIX. 
  
Whether a provider supports the KEEP_OPEN_READWRITE flag depends on the provider's implementation. 
  
To indicate that the only call to be made on the object after **SaveChanges** is **IUnknown::Release**, set no flags for the  _ulFlags_ parameter. An error from **SaveChanges** indicates that it could not make the pending changes permanent. Different providers handle the absence of flags on the **SaveChanges** call differently. Some providers treat this state the same as KEEP_OPEN_READONLY; other providers interpret it the same as KEEP_OPEN_READWRITE. Still other providers shut down the object when they do not receive flags on the **SaveChanges** call. 
  
Some properties, typically computed properties, cannot be processed until you call **SaveChanges** and, in some cases, **Release**.
  
When you make bulk changes, such as saving attachments to multiple messages, defer error processing by setting the MAPI_DEFERRED_ERRORS flag in  _ulFlags_. If you save multiple attachments to multiple messages, make one **SaveChanges** call to each attachment and one **SaveChanges** call to each message. Set the MAPI_DEFERRED_ERRORS flag for each attachment call and for all messages except for the last one. 
  
If **SaveChanges** returns MAPI_E_OBJECT_CHANGED, check whether the original object has been modified. If so, warn the user, who can either request that the changes overwrite the previous changes or save the object elsewhere. If the original object has been deleted, warn the user to give them the opportunity to save the object in another location. 
  
You cannot call **SaveChanges** with the FORCE_SAVE flag on an open object that has been deleted. 
  
If **SaveChanges** returns an error, the object whose changes were to be saved remains open, regardless of the flags set in the  _ulFlags_ parameter. 
  
> [!IMPORTANT]
> The  _ulFlags_ NON_EMS_XP_SAVE and SPAMFILTER_ONSAVE might not be defined in the downloadable header file you currently have, in which case you can add it to your code using the following values: >  `#define SPAMFILTER_ONSAVE ((ULONG) 0x00000080)`>  `#define NON_EMS_XP_SAVE ((ULONG) 0x00001000)`
  
For more information, see [Saving MAPI Properties](saving-mapi-properties.md).
  
## See also



[IMAPIProp::SetProps](imapiprop-setprops.md)
  
[PidTagEntryId Canonical Property](pidtagentryid-canonical-property.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[Saving MAPI Properties](saving-mapi-properties.md)

