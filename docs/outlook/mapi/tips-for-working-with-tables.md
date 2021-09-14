---
title: "Tips for Working with Tables"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: adb4d589-7e03-4222-8717-898ef397c6b6
description: "Last modified: July 23, 2011"
 
 
---

# Tips for Working with Tables

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Working with a MAPI table is a little like working with a relational database table. A user can limit the number of rows and columns in the view and specify their order. Rows can be retrieved one at a time or in groups. A cursor that keeps track of the current position can be moved to a specific place in the table. 
  
To work with tables, clients use the read-only interface, [IMAPITable : IUnknown](imapitableiunknown.md), whereas service providers, depending on whether they own the data that the table is based on, can use either **IMAPITable** or [ITableData : IUnknown](itabledataiunknown.md). The operations defined in these interfaces can be categorized as operations that all users of tables either do or can invoke and operations that are not as widely used because they are more advanced. Some of the advanced operations are more complex to implement; others are no more complex, but are of interest to a small minority of MAPI components. 
  
The more common operations are:
  
- Column operations, which affect single columns. These include specifying the properties to be included in the column set and the order in which they should be included.
    
- Row operations, which affect single rows. These include data retrieval and the maintenance operations: adding, deleting, and modifying a single row or rows.
    
- Global operations, which affect the entire table. These include event notification, searching and sorting.
    
## See also



[MAPI Tables](mapi-tables.md)

