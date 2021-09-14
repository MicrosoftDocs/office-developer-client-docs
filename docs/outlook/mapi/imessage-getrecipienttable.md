---
title: "IMessageGetRecipientTable"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMessage.GetRecipientTable
api_type:
- COM
ms.assetid: a335dfca-44da-452e-b16f-25d314b1758f
description: "Last modified: July 23, 2011"
---

# IMessage::GetRecipientTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the message's recipient table.
  
```cpp
HRESULT GetRecipientTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags that controls the return of the table. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **GetRecipientTable** to return successfully, possibly before the table is fully available to the calling client. If the table is not available, making a subsequent call to it can cause an error. 
    
MAPI_UNICODE 
  
> String columns should be in Unicode format. If the MAPI_UNICODE flag is not set, the string columns should be in ANSI format.
    
 _lppTable_
  
> [out] Pointer to a pointer to the recipient table.
    
## Return value

S_OK 
  
> The recipient table was returned successfully.
    
## Remarks

The **IMessage::GetRecipientTable** method returns a pointer to the message's recipient table, which includes information about all of the recipients for the message. There is one row for every recipient. 
  
Recipient tables have a different column set depending on whether the message has been submitted. For a complete list of the columns in a recipient table, see [Recipient Tables](recipient-tables.md).
  
Some recipient tables support a wide variety of restrictions; others do not. Support for restrictions depends on the message store provider's implementation. 
  
Setting the MAPI_UNICODE flag in the  _ulFlags_ parameter affects the following calls to the recipient table: 
  
- [IMAPITable::QueryColumns](imapitable-querycolumns.md) to retrieve the column set. 
    
- [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve rows. 
    
- [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) to retrieve the sort order. 
    
Setting the Unicode flag requests that the information for any string columns returned from these calls be in Unicode format. However, because not all message store providers support Unicode, setting this flag is only a request.
  
## Notes to callers

You can change a recipient table while it is open by calling the [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method. **ModifyRecipients** adds recipients, deletes recipients, or modifies recipient properties. 
  
## See also



[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMessage::ModifyRecipients](imessage-modifyrecipients.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)

