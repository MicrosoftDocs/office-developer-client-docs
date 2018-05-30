---
title: "BOOKMARK"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.BOOKMARK
api_type:
- COM
ms.assetid: 678bdc52-3404-48b2-9154-64ce2a941555
description: "Last modified: March 09, 2015"
---

# BOOKMARK

  
  
**Applies to**: Outlook 
  
Defines bookmarks data for remembering a position in a table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related methods:  <br/> |[IMAPITable::CreateBookmark](imapitable-createbookmark.md)[IMAPITable::FreeBookmark](imapitable-freebookmark.md) <br/> |
   
```cpp
typedef ULONG_PTR BOOKMARK;
```

## Remarks

MAPI defines three bookmarks, listed as follows:
  
BOOKMARK_BEGINNING 
  
> Remembers the starting position of the table. 
    
BOOKMARK_CURRENT 
  
> Remembers the current position of the table.
    
BOOKMARK_END 
  
> Remembers the ending position of the table.
    
Clients can create other bookmarks for remembering other table positions. Bookmarks are valid only when the table is open. Clients must free any bookmarks that they have created before closing the associated table. 
  
## See also



[IMAPITable::CreateBookmark](imapitable-createbookmark.md)
  
[IMAPITable::FindRow](imapitable-findrow.md)
  
[IMAPITable::FreeBookmark](imapitable-freebookmark.md)
  
[IMAPITable::SeekRow](imapitable-seekrow.md)


[MAPI Data Types](mapi-data-types.md)

