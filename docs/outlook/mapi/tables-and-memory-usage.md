---
title: "Tables and memory usage"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 7ac11e60-6b2c-4241-96e2-20219f84d949
description: "Last modified: July 23, 2011"
---

# Tables and memory usage

**Applies to**: Outlook 
  
An important issue connected with retrieving data from a table is memory usage. Lack of available memory can cause [IMAPITable::QueryRows](imapitable-queryrows.md) and [HrQueryAllRows](hrqueryallrows.md) to fail, returning less than the desired number of rows. Deciding which method or function to use to retrieve table data depends on whether the table can be expected to fit in memory, and if it cannot, if failure is acceptable. 
  
Because it is not always easy to determine the amount of data that will fit into memory at one time, MAPI provides some basic guidelines for a client application or service provider to follow. Remember that there are always exceptions, based on the particular table implementation and how the underlying data is stored.
  
The following guidelines can be used to evaluate table memory usage:
  
- Clients that can tolerate occasional working set memory usage in the megabyte range and can assume they will have no problems reading an entire table into memory. 
    
- Restrictions have an affect on a table's usage of memory. A severely restricted table with an extensive number of rows, such as a contents table, can be expected to fit into memory while an unrestricted large table usually cannot. 
    
- Several of the tables owned by MAPI such as the status, profile, message service, provider, and message store tables, will usually fit in memory. These are generally small tables. However, there are exceptions. For example, a server-based profile provider might generate a larger profile table that will not be able to fit.
    
To retrieve all of the rows from a table that will fit into memory with no problems, call [HrQueryAllRows](hrqueryallrows.md), setting the maximum number of rows to zero.
  
To retrieve all of the rows from a table that might or might not fit into memory, generating an error, call **HrQueryAllRows** specifying a maximum number of rows. The maximum number of rows should be set to a number greater than the minimum number of rows that are needed. If a client must access at least 50 rows from a 300 row table, the maximum number of rows should be set to at least 51. 
  
To retrieve all of the rows from a table that is not expected to fit into memory, call [IMAPITable::QueryRows](imapitable-queryrows.md) in a loop with a relatively small row count, as the following code sample illustrates: 
  
```cpp
HRESULT     hr;
LPSRowSet   pRows = NULL;
LONG        irow;
LONG            cAsk = 50;                  // adjust this value
while ((hr = pTable->QueryRows(cAsk, 0, &pRows)) == hrSuccess
        && pRows->cRows != 0)
{
    for (irow = 0; irow < prows->cRows; ++irow)
    {
        // process the row...
    }
    FreeProws(pRows);
    pRows = NULL;
}
if (hr)
{
    // handle the error...
}
 
```

When this loop completes and all the rows in the table have been processed and  _cRows_ is zero, the position of the cursor will usually be at the bottom of the table. 
  
## See also

- [MAPI Tables](mapi-tables.md)

