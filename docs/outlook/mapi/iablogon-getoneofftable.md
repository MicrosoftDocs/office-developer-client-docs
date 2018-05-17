---
title: "IABLogonGetOneOffTable"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABLogon.GetOneOffTable
api_type:
- COM
ms.assetid: 7ac2a8d4-6890-4346-a6b6-34deca9dab50
description: "Last modified: July 23, 2011"
---

# IABLogon::GetOneOffTable

  
  
**Applies to**: Outlook 
  
Returns a table of one-off templates for creating recipients to be added to the recipient list of an outgoing message.
  
```
HRESULT GetOneOffTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of string columns included in the table. The following flag can be set:
    
MAPI_UNICODE 
  
> The string columns are in Unicode format. If the MAPI_UNICODE flag is not set, the string columns are in ANSI format.
    
 _lppTable_
  
> [out] A pointer to a pointer to the one-off table.
    
## Return value

S_OK 
  
> The one-off table was successfully retrieved.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the address book provider does not support Unicode, or MAPI_UNICODE was not set and the address book provider supports only Unicode.
    
MAPI_E_NO_SUPPORT 
  
> The address book provider does not supply any one-off templates.
    
## Remarks

MAPI calls the **GetOneOffTable** method to make available one-off templates to create recipients. The new recipients are added to the recipient list of an outgoing message. Address book providers should support notification on their one-off table to inform MAPI of template modifications. MAPI keeps the one-off table open to enable dynamic updating. 
  
Address book providers can also support a one-off table for each of their containers. Callers retrieve this one-off table by calling the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method and requesting the **PR_CREATE_TEMPLATES** ( [PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property. The templates available through this table are used to add recipients to the container. For a discussion of the differences between the two types of one-off tables, see [Implementing One-Off Tables](implementing-one-off-tables.md).
  
For a list of the required columns in an address book provider's one-off table, see [One-Off Tables](one-off-tables.md).
  
## See also

#### Reference

[IABContainer::CreateEntry](iabcontainer-createentry.md)
  
[IAddrBook::NewEntry](iaddrbook-newentry.md)
  
[IMAPISupport::GetOneOffTable](imapisupport-getoneofftable.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

