---
title: "CREATE VIEW Statement (Microsoft Access SQL)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: ecaabd75-3081-fd35-830d-5a59b0a51922
description: "Creates a new view."
---

# CREATE VIEW Statement (Microsoft Access SQL)

Creates a new view.
  
> [!NOTE]
> The Microsoft Access database engine does not support the use of CREATE VIEW, or any of the DDL statements, with non-Microsoft Access database engine databases. 
  
## Syntax

CREATE VIEW  *view*  [(  *field1*  [,  *field2*  [, …]])] AS  *selectstatement* 
  
The CREATE VIEW statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *view*  <br/> |The name of the view to be created.  <br/> |
| *field1*  ,  *field2*  <br/> |The name of field or fields for the corresponding fields specified in  *selectstatement*  .  <br/> |
| *selectstatement*  <br/> |A SQL SELECT statement. For more information, see [SELECT Statement](select-statement-microsoft-access-sql.md).  <br/> |
   
## Remarks

The SELECT statement that defines the view cannot be a [SELECT INTO](select-into-statement-microsoft-access-sql.md) statement. 
  
The SELECT statement that defines the view cannot contain any parameters.
  
The name of the view cannot be the same as the name of an existing table.
  
If the query defined by the SELECT statement is updatable, then the view is also updatable. Otherwise, the view is read-only.
  
If any two fields in the query defined by the SELECT statement have the same name, the view definition must include a field list specifying unique names for each of the fields in the query.
  

