---
title: "IMAPITableCreateBookmark"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.CreateBookmark
api_type:
- COM
ms.assetid: 320af2ff-c2a5-43b1-b3a1-76cb5ffd6a4f
description: "Last modified: July 23, 2011"
---

# IMAPITable::CreateBookmark

  
  
**Applies to**: Outlook 
  
Creates a bookmark at the table's current position.
  
```cpp
HRESULT CreateBookmark(
BOOKMARK FAR * lpbkPosition
);
```

## Parameters

 _lpbkPosition_
  
> [out] Pointer to the returned 32-bit bookmark value. This bookmark can later be passed in a call to the [IMAPITable::SeekRow](imapitable-seekrow.md) method. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_UNABLE_TO_COMPLETE 
  
> The requested operation could not be completed.
    
## Remarks

The **IMAPITable::CreateBookmark** method marks a table position by creating a value called a bookmark. A bookmark can be used to return to the position identified by the bookmark. The bookmarked position is associated with the object at that row in the table. 
  
Bookmarks are not supported on attachment tables, and attachment table implementations of **CreateBookmark** return MAPI_E_NO_SUPPORT. 
  
## Notes to implementers

Because of the memory expense of maintaining cursor positions with bookmarks, limit the number of bookmarks that you can create. When you reach that number, return MAPI_E_UNABLE_TO_COMPLETE from all subsequent calls to **CreateBookmark**.
  
Sometimes a bookmark points to a row that is no longer in the table view. If a caller uses such a bookmark, move the cursor to the next visible row and stop there. 
  
When the caller attempts to use a bookmark that is pointing to a nonvisible row because it has been collapsed, return MAPI_W_POSITION_CHANGED after moving the bookmark. You can reposition the bookmark to the next visible row either at this time or when the collapsing occurs in the **SetCollapseState** method. If you move the bookmark at the time the row is collapsed, you must retain a bit in the bookmark that indicates exactly when the bookmark was moved: since its last use or if it has never been used since its creation. 
  
## Notes to callers

 **CreateBookmark** allocates memory for the bookmark it creates. Release the resources for the bookmark by calling the [IMAPITable::FreeBookmark](imapitable-freebookmark.md) method. 
  
## See also



[IMAPITable::FreeBookmark](imapitable-freebookmark.md)
  
[IMAPITable::SeekRow](imapitable-seekrow.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

