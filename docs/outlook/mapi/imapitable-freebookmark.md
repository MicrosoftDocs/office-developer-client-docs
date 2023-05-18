---
title: "IMAPITableFreeBookmark"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.FreeBookmark
api_type:
- COM
ms.assetid: 797833f7-8295-41bc-8980-977e5f5e05e8
---

# IMAPITable::FreeBookmark

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Releases the memory associated with a bookmark.
  
```cpp
HRESULT FreeBookmark(
BOOKMARK bkPosition
);
```

## Parameters

 _bkPosition_
  
> [in] The bookmark to be freed, created by calling the [IMAPITable::CreateBookmark](imapitable-createbookmark.md) method. 
    
## Return value

S_OK 
  
> The bookmark was successfully freed.
    
MAPI_E_INVALID_BOOKMARK 
  
> The specified bookmark does not exist.
    
## Remarks

The **IMAPITable::FreeBookmark** method releases a bookmark that is no longer needed. The bookmark is no longer valid after this call. Whenever a table is released from memory, all of its associated bookmarks are also released. 
  
## Notes to implementers

If the caller passes one of the three predefined bookmarks in the _bkPosition_ parameter, ignore the request and return S_OK. 
  
## See also



[IMAPITable::CreateBookmark](imapitable-createbookmark.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

