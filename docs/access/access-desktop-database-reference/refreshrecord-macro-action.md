---
title: RefreshRecord Macro Action
TOCTitle: RefreshRecord Macro Action
ms:assetid: 68c90d7d-f59c-9e83-bc30-8f37cf5a3696
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195261(v=office.15)
ms:contentKeyID: 48545396
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm62122
f1_categories:
- Office.Version=v15
---

# RefreshRecord Macro Action


**Applies to**: Access 2013 | Office 2013

**In this article**  
Remarks  
Client database  
Web database  

You can use the **RefreshRecord** action to update the underlying record source for the active form or datasheet to reflect changes made to the records in the current set.

## Remarks

the **RefreshRecord** action shows only changes made to records in the current set. Because the **RefreshRecord** action does not actually requery the database, the current set will not include records that have been added or exclude records that have been deleted since the database was last requeried; Nor will it exclude records that no longer satisfy the criteria of the query or filter. To requery the database, use the **[Requery](requery-macro-action.md)** method. When the record source for a form is requeried, the current set of records will accurately reflect all data in the record source.

The behavior of this macro action depends on whether you are calling it in a client database or a web database.

## Client database

In a client database, you can use the **RefreshRecord** action to update the underlying record source for the active form or datasheet to reflect changes made to the data in the current set. Changes include those made by the current user or by other users in a multiuser environment. It is equivalent to the **[Refresh](https://msdn.microsoft.com/library/ff836021\(v=office.15\))** method.

The **RefreshRecord** macro action does the following in a client database:

1.  Updates the record source for the active form or datasheet to reflect the changes made to rows in the current set. For ODBC linked tables, retrieves changes to records in the current set from the data source.

2.  Updates the current set to reflect the changes. If a row in the record source has been deleted, it is changed to show \#Deleted.

3.  Refreshes the active or datasheet to display any changed records and any \#Deleted records, in the current set.

4.  Requeries any subforms and subreports on the active form or datasheet.

## Web database

In a web database, you can use the **RefreshRecord** action to update the underlying record source for the active form or datasheet to reflect changes made to the records in the current set. Changes include those made by the current user or other users.

The **RefreshRecord** macro action does the following in a web database:

1.  Retrieves changes from the server for any base tables in the current set. For ODBC linked tables, retrieves changes to records in the current set from the data source.

2.  Updates the current set to reflect the changes. If a row in the current set has been deleted, it is changed to show \#Deleted.

3.  Refreshes the active form or datasheet to display any changed records and any \#Deleted records, in the current set.

4.  Requeries any subforms and subreports on the active form or datasheet.

