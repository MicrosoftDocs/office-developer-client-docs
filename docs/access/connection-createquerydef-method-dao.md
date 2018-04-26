---
title: "Connection.CreateQueryDef Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053067
  
localization_priority: Normal
ms.assetid: 254fe81a-9b45-e8e7-108d-503c1c1c0fcc
description: "Creates a new QueryDef object."
---

# Connection.CreateQueryDef Method (DAO)

Creates a new **[QueryDef](querydef-object-dao.md)** object. 
  
## Syntax

 *expression*  . **CreateQueryDef**( ** *Name* **, ** *SQLText* ** ) 
  
 *expression*  A variable that represents a **Connection** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Optional  <br/> |**Variant** <br/> |A **Variant** ( **String** subtype) that uniquely names the new **QueryDef**.  <br/> |
| _SQLText_ <br/> |Optional  <br/> |**Variant** <br/> |A **Variant** ( **String** subtype) that is an SQL statement defining the **QueryDef**. If you omit this argument, you can define the **QueryDef** by setting its **[SQL](querydef-sql-property-dao.md)** property before or after you append it to a collection.  <br/> |
   
### Return Value

QueryDef
  
## Remarks

In a Microsoft Access workspace, if you provide anything other than a zero-length string for the name when you create a **QueryDef**, the resulting **QueryDef** object is automatically appended to the **[QueryDefs](querydefs-collection-dao.md)** collection. 
  
If the object specified by  _name_ is already a member of the **QueryDefs** collection, a run-time error occurs. You can create a temporary **QueryDef** by using a zero-length string for the  _name_ argument when you execute the **CreateQueryDef** method. You can also accomplish this by setting the **[Name](connection-name-property-dao.md)** property of a newly created **QueryDef** to a zero-length string (""). Temporary **QueryDef** objects are useful if you want to repeatedly use dynamic SQL statements without having to create any new permanent objects in the **QueryDefs** collection. You can't append a temporary **QueryDef** to any collection because a zero-length string isn't a valid name for a permanent **QueryDef** object. You can always set the **Name** and **SQL** properties of the newly created **QueryDef** object and subsequently append the **QueryDef** to the **QueryDefs** collection. 
  
To run the SQL statement in a **QueryDef** object, use the **[Execute](connection-execute-method-dao.md)** or **[OpenRecordset](connection-openrecordset-method-dao.md)** method. 
  
Using a **QueryDef** object is the preferred way to perform SQL pass-through queries with ODBC databases. 
  
To remove a **QueryDef** object from a **QueryDefs** collection in a Microsoft Access database engine database, use the **[Delete](fields-delete-method-dao.md)** method on the collection. 
  

