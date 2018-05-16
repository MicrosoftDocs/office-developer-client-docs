---
title: "IMAPIFolderCreateMessage"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.CreateMessage
api_type:
- COM
ms.assetid: e0222afa-c148-4735-a603-cac7be6c91f9
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::CreateMessage

  
  
**Applies to**: Outlook 
  
Creates a new message.
  
```
HRESULT CreateMessage(
  LPCIID lpInterface,
  ULONG ulFlags,
  LPMESSAGE FAR * lppMessage
);
```

## Parameters

 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the new message. Valid interface identifiers include IID_IUnknown, IID_IMAPIProp, IID_IMAPIContainer, and IID_IMAPIFolder. Passing NULL causes the message store provider to return the standard message interface, [IMessage : IMAPIProp](imessageimapiprop.md). 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the message is created. The following flags can be set:
    
ITEMPROC_FORCE
  
> Indicates to the personal folder store (PST) that the message is eligible for rules processing before the store notifies any listening client of the arrival of the new message. Rules processing only applies to new messages that are created on a server that is not a Microsoft Exchange Server, because Exchange Server processes rules for messages on the server. Therefore, the provider or client creating the message must pass this flag in combination with saving a message with [IMAPIPProp::SaveChanges](imapiprop-savechanges.md) using NON_EMS_XP_SAVE, which indicates that the server is not an Exchange Server. 
    
MAPI_ASSOCIATED 
  
> The message to be created should be included in the associated contents table instead of the standard contents table. Associated messages are hidden from user interaction.
    
MAPI_DEFERRED_ERRORS 
  
> **CreateMessage** is allowed to succeed even if the create operation has not fully completed. This implies that the new message might not be immediately available to the caller. 
    
 _lppMessage_
  
> [out] A pointer to a pointer to the newly created message.
    
## Return value

S_OK 
  
> The message was successfully created.
    
## Remarks

The **IMAPIFolder::CreateMessage** method creates a new message with generic or associated content and assigns an entry identifier. The entry identifier consists of a part that represents the message store provider and a part that represents the individual message. 
  
## Notes to Implementers

You can choose whether to set all of the required message properties in **CreateMessage** or in the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. You do not have to make these properties available until a successful save has occurred. 
  
For more information about how to work with associated information, see [Folder-Associated Information Tables](folder-associated-information-tables.md) and [Contents Tables](contents-tables.md). 
  
## Notes to Callers

Some message store providers allow the entry identifier of the new message to be available immediately after **CreateMessage** returns; other message store providers delay its availability until the message is saved. Because not all message store providers generate an entry identifier for a new message until you have called the message's **IMAPIProp::SaveChanges** method, you may be unable to access the entry identifier when **CreateMessage** returns. Also, the new message may not be included in the folder's contents table until the save occurs. 
  
Expect the entry identifier assigned to the new message to be unique not only in the current message store, but most likely across all of the message stores that are open at the same time. One exception to this rule occurs when multiple entries for a message store appear in the profile. This causes the message store to be opened multiple times and entry identifiers to be duplicated. 
  
To create an outgoing message, call the Outbox folder's **IMAPIFolder::CreateMessage** method. 
  
If you delete a folder that contains a new message before the message is saved, the results are undefined.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |CFolder::OnNewMessage  <br/> |MFCMAPI uses the **IMAPIFolder::CreateMessage** method to create and save a new message.  <br/> |
   
## See also

#### Reference

[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

