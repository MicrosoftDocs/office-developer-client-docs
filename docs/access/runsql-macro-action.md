---
title: "RunSQL Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm12983
  
localization_priority: Normal
ms.assetid: 3692142d-f8a8-e194-0b38-051167f46319
description: "You can use the RunSQL action to run a Access action query by using the corresponding SQL statement. You can also run a data-definition query."
---

# RunSQL Macro Action

You can use the **RunSQL** action to run a Access action query by using the corresponding SQL statement. You can also run a data-definition query. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **RunSQL** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**SQL Statement** <br/> |The SQL statement for the action query or data-definition query you want to run. The maximum length of this statement is 255 characters. This is a required argument.  <br/> |
|**Use Transaction** <br/> |Select **Yes** to include this query in a transaction. Select **No** if you don't want to use a transaction. The default is **Yes**. If you select **No** for this argument, the query might run faster.  <br/> |
   
## Remarks

You can use action queries to append, delete, and update records and to save a query's result set as a new table. You can use data-definition queries to create, alter, and delete tables, and to create and delete indexes. You can use the **RunSQL** action to perform these operations directly from a macro without having to use stored queries. 
  
If you need to type an SQL statement longer than 255 characters, use the **RunSQL** method of the **DoCmd** object in a Visual Basic for Applications (VBA) module instead. You can type SQL statements of up to 32,768 characters in VBA. 
  
Access queries are actually SQL statements that are created when you design a query by using the design grid in the Query window. The following table shows the Access action queries and data-definition queries and their corresponding SQL statements.
  
|**Query type**|**SQL statement**|
|:-----|:-----|
|**Action** <br/> ||
|Append  <br/> |INSERT INTO  <br/> |
|Delete  <br/> |DELETE  <br/> |
|Make-table  <br/> |SELECT...INTO  <br/> |
|Update  <br/> |UPDATE  <br/> |
|**Data-definition (SQL-specific)** <br/> ||
|Create a table  <br/> |CREATE TABLE  <br/> |
|Alter a table  <br/> |ALTER TABLE  <br/> |
|Delete a table  <br/> |DROP TABLE  <br/> |
|Create an index  <br/> |CREATE INDEX  <br/> |
|Delete an index  <br/> |DROP INDEX  <br/> |
   
You can also use an IN clause with these statements to modify data in another database.
  
> [!NOTE]
> To run a select query or crosstab query from a macro, use the View argument of the **OpenQuery** action to open an existing select query or crosstab query in Datasheet view. You can also run existing action queries and SQL-specific queries in the same way. 
  

