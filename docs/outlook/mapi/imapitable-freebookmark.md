---
title: "IMAPITableFreeBookmark"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.FreeBookmark
api_type:
- COM
ms.assetid: 797833f7-8295-41bc-8980-977e5f5e05e8
description: "Last modified: July 23, 2011"
---

# IMAPITable::FreeBookmark

  
  
**Applies to**: Outlook 
  
Releases the memory associated with a bookmark.
  
```
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
  
## Notes to Implementers

If the caller passes one of the three predefined bookmarks in the  _bkPosition_ parameter, ignore the request and return S_OK. 
  
## See also

#### Reference

[IMAPITable::CreateBookmark](imapitable-createbookmark.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

