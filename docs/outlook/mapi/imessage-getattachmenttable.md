---
title: "IMessageGetAttachmentTable"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMessage.GetAttachmentTable
api_type:
- COM
ms.assetid: e568917e-6085-4094-8728-89ba90a78c40
description: "Last modified: July 23, 2011"
---

# IMessage::GetAttachmentTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the message's attachment table.
  
```cpp
HRESULT GetAttachmentTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags that relate to the creation of the table. The following flag can be set: 
    
MAPI_UNICODE 
  
> The string columns are in Unicode format. If the MAPI_UNICODE flag is not set, the string columns are in ANSI format.
    
MAPI_DEFERRED_ERRORS 
  
> Allows **GetAttachmentTable** to return successfully, possibly before the table is fully available to the calling client. If the table is not available, making a subsequent call to it can cause an error. 
    
 _lppTable_
  
> [out] Pointer to a pointer to the attachment table.
    
## Return value

S_OK 
  
> The attachment table was successfully retrieved.
    
## Remarks

The **IMessage::GetAttachmentTable** method returns a pointer to the message's attachment table, which includes information about all of the attachments in the message. Clients can get access to an attachment only through the attachment table. By retrieving an attachment's number its **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property a client can use several of the **IMessage** methods to work with the attachment. 
  
There is one row for each attachment. For a complete list of the columns in an attachment table, see [Attachment Tables](attachment-tables.md).
  
An attachment usually does not appear in the attachment table until both the attachment and the message have been saved with a call to [IMAPIProp::SaveChanges](imapiprop-savechanges.md). Attachment tables are dynamic. If a client creates a new attachment, deletes an existing attachment, or changes one or more properties once the **SaveChanges** calls have been made on the attachment on the message, the attachment table will be updated to reflect the new information. 
  
Some attachment tables support a wide variety of restrictions; others do not. Support for restrictions depends on the message store provider's implementation. 
  
When initially opened, attachment tables are not necessarily sorted in any particular order. 
  
Setting the MAPI_UNICODE flag in the  _ulFlags_ parameter affects the following calls to the attachment table: 
  
- [IMAPITable::QueryColumns](imapitable-querycolumns.md) to retrieve the column set. 
    
- [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve rows. 
    
- [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) to retrieve the sort order. 
    
Setting the Unicode flag requests that the information for any string columns returned from these calls be in Unicode format. However, because not all message store providers support Unicode, setting this flag is only a request.
  
## See also



[IMessage::CreateAttach](imessage-createattach.md)
  
[IMessage::DeleteAttach](imessage-deleteattach.md)
  
[IMessage::OpenAttach](imessage-openattach.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)

