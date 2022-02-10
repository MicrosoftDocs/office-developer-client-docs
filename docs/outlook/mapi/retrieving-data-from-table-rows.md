---
title: "Retrieving Data from Table Rows"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 19a42794-a3a2-4336-af2a-473f24431252
description: "Last modified: March 09, 2015"
 
 
---

# Retrieving Data from Table Rows

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieving rows from a table involves:
  
- Obtaining the property values for all the columns.
    
- Modifying the current position.
    
One of the required columns in most tables is an entry identifier — the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property — that can be used to open the object that represents the row. This entry identifier is usually a short-term entry identifier, one that does not persist past the lifetime of the table. However, it can be a long-term identifier if the service provider implementing the table only supports one type of entry identifier.
  
Clients and service providers can make one of the following calls to retrieve rows:
  
|||
|:-----|:-----|
|[IMAPITable::QueryRows](imapitable-queryrows.md) <br/> |Retrieves a specified number of rows starting with the current row in either a forward or backward direction. |
|[HrQueryAllRows](hrqueryallrows.md) <br/> |Retrieves all of the rows in a table. |
|[ITableData::HrQueryRow](itabledata-hrqueryrow.md) <br/> |Retrieves a row in a table according to the value of its index column. **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) is usually the index column for a table. |
   
When an optional property is included as one of the columns in a table, some of the rows might have valid values for the column while others might not. Whether a valid value exists for a column depends on whether the object providing the information for the row sets the property. Depending on the implementation of the object, a non-existent property can be represented in the table as **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)) or an arbitrary value. Users of tables must be careful to differentiate between properties that are nonexistent and have meaningless values and properties that do exist and have valid values. 
  
## See also



[MAPI Tables](mapi-tables.md)

