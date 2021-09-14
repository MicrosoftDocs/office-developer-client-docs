---
title: "IMAPISupportGetOneOffTable"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.GetOneOffTable
api_type:
- COM
ms.assetid: 6800fd3a-aa43-45fe-9cc2-102d0ef43edf
description: "Last modified: July 23, 2011"
---

# IMAPISupport::GetOneOffTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a pointer to the MAPI one-off table (a list of templates that all address book providers support for creating new recipients).
  
```cpp
HRESULT GetOneOffTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the string columns. The following flag can be set:
    
MAPI_UNICODE 
  
> The string columns are in Unicode format. If the MAPI_UNICODE flag is not set, the string columns are in ANSI format.
    
 _lppTable_
  
> [out] A pointer to a pointer to the one-off table.
    
## Return value

S_OK 
  
> The one-off table was successfully retrieved.
    
## Remarks

The **IMAPISupport::GetOneOffTable** method is implemented for address book provider support objects. Address book providers call **GetOneOffTable** to retrieve the complete list of templates for creating new recipients. This table includes templates that address book providers that are active in the session support, as well as templates that MAPI supports. 
  
The newly created recipients can be used to address a message or can be added to an address book container.
  
For a list of the properties that make up the required column set in one-off tables, see [One-Off Tables](one-off-tables.md).
  
Setting the MAPI_UNICODE flag in the  _ulFlags_ parameter affects the format of the columns returned from the [IMAPITable::QueryColumns](imapitable-querycolumns.md) and [IMAPITable::QueryRows](imapitable-queryrows.md) methods. This flag also controls the property types in the sort order returned by the [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method. 
  
## Notes to callers

If you are registered to receive notifications of changes to this one-off table, you will also receive notifications of changes to other providers' one-off tables. Based on these notifications, you can support new address types that are added during the current session.
  
## See also



[IABContainer::CreateEntry](iabcontainer-createentry.md)
  
[IMAPISupport::NewEntry](imapisupport-newentry.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
  
[IMAPITable::QueryColumns](imapitable-querycolumns.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
  
[PidTagCreateTemplates Canonical Property](pidtagcreatetemplates-canonical-property.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)


[One-Off Tables](one-off-tables.md)

