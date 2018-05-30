---
title: "Setting a Table Position with a Bookmark"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 56ab37f9-5aa6-4e9d-9dc8-b3d95aa19f35
description: "Last modified: March 09, 2015"
 
 
---

# Setting a Table Position with a Bookmark

  
  
**Applies to**: Outlook 
  
A bookmark is a resource that indicates a particular location in a table. Setting a bookmark makes it possible to return to a position at a later time, a feature that can significantly improve the performance of table operations. MAPI defines three standard bookmarks: 
  
|||
|:-----|:-----|
|BOOKMARK_CURRENT  <br/> |Points to the current row in a table.  <br/> |
|BOOKMARK_BEGINNING  <br/> |Points to the first row in a table.  <br/> |
|BOOKMARK_END  <br/> |Points to the last row in a table.  <br/> |
   
Table implementers are required to support these standard bookmarks and can also support others. However, because bookmarks are resources and resources are limited, bookmark users should free them as soon as possible. 
  
 **To set a bookmark at the current table position**
  
- Call [IMAPITable::CreateBookmark](imapitable-createbookmark.md). Occasionally there will be insufficient memory available to allocate the new bookmark, causing **CreateBookmark** to return the MAPI_E_UNABLE_TO_COMPLETE error value. 
    
 **To free a bookmark**
  
- Call [IMAPITable::FreeBookmark](imapitable-freebookmark.md).
    
 **To move the cursor to a bookmarked position**
  
- Call [IMAPITable::SeekRow](imapitable-seekrow.md). **SeekRow** establishes a new value for the BOOKMARK_CURRENT position. **SeekRow** can be used, for example, to position a table ten rows from the current position or to start over at the beginning. Clients or service providers can seek to the current, beginning, or end of a table, or any other position that is associated with a predefined bookmark. They can move in either a forward or backward direction and limit the operation to a specified number of rows. As a rule, callers should seek through no more than 50 rows with **SeekRow**; [IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md) should be used with larger numbers of rows. 
    
## See also



[MAPI Tables](mapi-tables.md)

