---
title: "Tips for better table performance"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: ac82f7e8-6453-4b4f-8223-3c23d09ca4c6
description: "Last modified: July 23, 2011"
---

# Tips for better table performance
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Because many of the table operations can be time-consuming and there is no way to indicate progress, it is helpful to use the following techniques for improving performance:
  
- **Make [IMAPITable : IUnknown](imapitableiunknown.md) calls in the correct order**
    
   Clients and service providers can work with tables in a variety of ways. They can open the table and retrieve the data for all of the rows using the default column set and sort order. Alternatively, they can modify this default view of the table by changing the column set, changing the sort order, or establishing a restriction to narrow the table's scope. Table users that intend to perform one or more of these operations before retrieving any data should perform them in the following order:
    
    1. Define a column set with [IMAPITable::SetColumns](imapitable-setcolumns.md).
        
    2. Establish a restriction with [IMAPITable::Restrict](imapitable-restrict.md).
        
    3. Define a sort order with [IMAPITable::SortTable](imapitable-sorttable.md).
    
    Performing these tasks in this order limits the number of rows and columns that will be sorted, thereby improving performance.
    
- **Delay an operation using the TBL_BATCH flag if possible**
    
    Setting the TBL\_BATCH flag on a method allows the table implementer to collect several calls before acting on any one of them. Instead of make potentially many calls to a remote server; a table implementer can make one, performing all the operations at one time. The results of the operations are not evaluated until they are needed. 
    
    For example, when a client calls [IMAPITable::Restrict](imapitable-restrict.md) to specify a restriction with the TBL\_BATCH flag set, the restriction do not have to go into effect until the client calls [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve the data. This allows the table implementer to combine the work of two calls into one. Table users that take advantage of the TBL\_BATCH flag should be aware that error handling under these conditions can be more complex. 
    
    Because handling the errors from a delayed operation is similar to handling the errors when the MAPI\_DEFERRED_ERRORS flag is set, see [Deferring MAPI Errors](deferring-mapi-errors.md) for more information. 
    
- **Keep a cache of commonly used properties**
    
    Service providers implementing tables can lessen the time it takes to create a view by caching copies of commonly used object properties. Keeping a copy of these properties in memory saves having to retrieve them from the object each time the view must be rebuilt.
    
## See also

- [MAPI Tables](mapi-tables.md)

