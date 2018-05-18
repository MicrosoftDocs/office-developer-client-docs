---
title: "IMAPIContainerGetContentsTable"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIContainer.GetContentsTable
api_type:
- COM
ms.assetid: 88c7a666-875d-473a-b126-dbbb7009f7d9
description: "Last modified: March 09, 2015"
---

# IMAPIContainer::GetContentsTable

  
  
**Applies to**: Outlook 
  
Returns a pointer to the container's contents table.
  
```cpp
HRESULT GetContentsTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how the contents table is returned. The following flags can be set:
    
MAPI_ASSOCIATED 
  
> The container's associated contents table should be returned instead of the standard contents table. This flag is used only with folders. The messages that are included in the associated contents table were created with the MAPI_ASSOCIATED flag set in the call to the [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method. Clients typically use the associated contents table to retrieve forms, views, and other hidden messages. 
    
ACLTABLE_FREEBUSY
  
> Enables access to the frightsFreeBusySimple and frightsFreeBusyDetailed rights in **PR_MEMBER_RIGHTS**.
    
MAPI_DEFERRED_ERRORS 
  
> **GetContentsTable** can return successfully, possibly before the table is made available to the caller. If the table is not available, making a subsequent table call can raise an error. 
    
MAPI_UNICODE 
  
> Requests that the columns that contain string data be returned in the Unicode format. If the MAPI_UNICODE flag is not set, the strings should be returned in the ANSI format. 
    
SHOW_SOFT_DELETES
  
> Shows items that are currently marked as soft deleted—that is, they are in the deleted item retention time phase.
    
 _lppTable_
  
> [out] A pointer to a pointer to the contents table.
    
## Return value

S_OK 
  
> The contents table was successfully retrieved.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_NO_SUPPORT 
  
> The container has no contents and cannot provide a contents table.
    
## Remarks

The **IMAPIContainer::GetContentsTable** method returns a pointer to the contents table of a container. A contents table contains summary information about objects in the container. 
  
Contents tables have lengthy column sets. For a complete list of the required and optional columns in contents tables, see [Contents Tables](contents-tables.md). 
  
It is possible for some containers to have no contents. These containers return MAPI_E_NO_SUPPORT from their implementations of **GetContentsTable**.
  
## Notes to Implementers

If you support a contents table for your container, you must also do the following:
  
- Support calls to the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) property.
    
- Return **PR_CONTAINER_CONTENTS** in response to a call to the container's 
    
    [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPIProp::GetPropList](imapiprop-getproplist.md) methods. 
    
A remote transport provider's implementation of this method must return a pointer to an [IMAPITable : IUnknown](imapitableiunknown.md) interface in the  _ppTable_ parameter passed into the **GetContentsTable** method. If your transport provider has an existing contents table, it is sufficient to return a pointer to it. If not, this method must create a new [IMAPITable : IUnknown](imapitableiunknown.md) object, populate the table with message headers (if any are available), and return a pointer to the new table. The [ITableData::HrGetView](itabledata-hrgetview.md) method is useful for generating a return value and storing the table pointer in the  _ppTable_ parameter. The contents table must support at least the following property columns: 
  
- **PR_ENTRYID** ([PidTagEntryID](pidtagentryid-canonical-property.md))
    
- **PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md))
    
- **PR_SENT_REPRESENTING_NAME** ([PidTagSentRepresentingName](pidtagsentrepresentingname-canonical-property.md))
    
- **PR_DISPLAY_TO** ([PidTagDisplayTo](pidtagdisplayto-canonical-property.md))
    
- **PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md))
    
- **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md))
    
- **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md))
    
- **PR_MESSAGE_SIZE** ([PidTagMessageSize](pidtagmessagesize-canonical-property.md))
    
- **PR_PRIORITY** ([PidTagPriority](pidtagpriority-canonical-property.md))
    
- **PR_IMPORTANCE** ([PidTagImportance](pidtagimportance-canonical-property.md))
    
- **PR_SENSITIVITY** ([PidTagSensitivity](pidtagsensitivity-canonical-property.md))
    
- **PR_MESSAGE_DELIVERY_TIME** ([PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md))
    
- **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md))
    
- **PR_MESSAGE_DOWNLOAD_TIME** ([PidTagMessageDownloadTime](pidtagmessagedownloadtime-canonical-property.md))
    
- **PR_HASATTACH** ([PidTagHasAttachments](pidtaghasattachments-canonical-property.md))
    
- **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))
    
- **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))
    
- **PR_NORMALIZED_SUBJECT** ([PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md))
    
## Notes to Callers

String and binary contents table columns can be truncated. Typically, providers return 255 characters. Because you cannot know beforehand whether a table includes truncated columns, assume that a column is truncated if the length of the column is either 255 or 510 bytes. You can always retrieve the full value of a truncated column, if necessary, directly from the object by using its entry identifier to open it and then calling the **IMAPIProp::GetProps** method. 
  
Depending on the provider's implementation, restrictions and sorting operations can apply to all of a string or to the truncated version of that string.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableDialog.cpp  <br/> |CContentsTableDlg::CContentsTableDlg  <br/> |The **CContentsTableDlg** class uses **GetContentsTable** to obtain the entries in a contents table.  <br/> |
   
## See also

#### Reference

[IMAPIProp::GetPropList](imapiprop-getproplist.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
  
[PidTagContainerContents Canonical Property](pidtagcontainercontents-canonical-property.md)
  
[IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

