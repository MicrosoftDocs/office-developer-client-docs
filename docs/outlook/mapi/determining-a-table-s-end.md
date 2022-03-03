---
title: "Determining a Table's End"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c879e972-05f4-4716-8fc2-db5b22f34ca8
 
 
---

# Determining a Table's End

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 A common error is to assume that the end of the table has been reached when: 
  
- [IMAPITable::QueryRows](imapitable-queryrows.md) has been called in a loop, with the end of the loop determined by the row count returned by [IMAPITable::GetRowCount](imapitable-getrowcount.md). The count that **GetRowCount** returns does not always represent the exact number of rows in the table; it is an approximate count. 
    
- **QueryRows** has been called with a fixed number of rows and fewer rows are returned. It is not until **QueryRows** returns a row set with a row count equal to zero that there are no more rows to retrieve. 
    
> [!IMPORTANT]
> The only time that a caller can assume that the cursor is positioned at the end of the table for a positive row count or at the beginning of the table for a negative row count is when the value S_OK and zero rows are returned. The value MAPI_E_NOT_FOUND is never returned. 
  
## See also



[MAPI Tables](mapi-tables.md)

