---
title: "IMAPIMessageSiteGetSiteStatus"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIMessageSite.GetSiteStatus
api_type:
- COM
ms.assetid: 02718898-7857-4e43-8f46-622269f812e6
description: "Last modified: March 09, 2015"
---

# IMAPIMessageSite::GetSiteStatus

  
  
**Applies to**: Outlook 
  
Returns information from a message site object about the message site's capabilities for the current message.
  
```cpp
HRESULT GetSiteStatus(
  ULONG FAR * lpulStatus
);
```

## Parameters

 _lpulStatus_
  
> [out] A pointer to a bitmask of flags that provides information about message status. The following flags can be set:
    
VCSTATUS_COPY 
  
> The message can be copied. 
    
VCSTATUS_DELETE 
  
> The message can be deleted.
    
VCSTATUS_DELETE_IS_MOVE 
  
> When deleted, a message is moved to a **Deleted Items** folder in its message store instead of being immediately removed from its message store. 
    
VCSTATUS_MOVE 
  
> The message can be moved.
    
VCSTATUS_NEW_MESSAGE 
  
> A new message can be created.
    
VCSTATUS_SAVE 
  
> The message can be saved.
    
VCSTATUS_SUBMIT 
  
> The message can be submitted.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Form objects call the **IMAPIMessageSite::GetSiteStatus** method to obtain the message site object's capabilities for the current message. The flags returned in the  _lpulStatus_ parameter provide information about the message site. Typically, a form enables or disables menu commands, depending on information the flags provide about the capabilities of the message site implementation. If a new message is loaded into a form by the [IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md) method or the [IPersistMessage::Load](ipersistmessage-load.md) method, the status flags must be checked. Some message site objects, especially read-only objects, do not allow messages to be saved or deleted. 
  
## Notes to implementers

The **IMAPIMessageSite::GetSiteStatus** method may require the client application to do some calculation to determine what operations can or cannot be performed on the current message. Typically, that involves looking at the status row for the current message's message store provider, or querying the store provider to determine which actions the client application can perform by using the message store. For example, to determine whether to return the MAPI_DELETE_IS_MOVE flag, check the message store object's **PR_IPM_WASTEBASKET_ENTRYID** ([PidTagIpmWastebasketEntryId](pidtagipmwastebasketentryid-canonical-property.md)) property to see whether there is a **Deleted Items** folder in the message store. 
  
For a list of interfaces related to form servers, see [MAPI Form Interfaces](mapi-form-interfaces.md).
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::GetSiteStatus  <br/> |MFCMAPI uses the **IMAPIMessageSite::GetSiteStatus** method to get the status of the specified site. It can return VCSTATUS_NEW_MESSAGE, VCSTATUS_SAVE, or VCSTATUS_SUBMIT.  <br/> |
   
## See also



[IPersistMessage::Load](ipersistmessage-load.md)
  
[IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md)
  
[PidTagIpmWastebasketEntryId Canonical Property](pidtagipmwastebasketentryid-canonical-property.md)
  
[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Form Interfaces](mapi-form-interfaces.md)

