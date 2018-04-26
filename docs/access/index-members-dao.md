---
title: "Index Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e261c5fa-ca7d-0d63-1c29-48e9231b39d1
description: "Index objects specify the order of records accessed from database tables and whether or not duplicate records are accepted, providing efficient access to data. For external databases, Index objects describe the indexes established for external tables (Microsoft Access workspaces only)."
---

# Index Members (DAO)

 **Index** objects specify the order of records accessed from database tables and whether or not duplicate records are accepted, providing efficient access to data. For external databases, **Index** objects describe the indexes established for external tables (Microsoft Access workspaces only). 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[CreateField](index-createfield-method-dao.md)** <br/> |Creates a new **[Field](field-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
|**[CreateProperty](index-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Clustered](index-clustered-property-dao.md)** <br/> |Sets or returns a value that indicates whether an **Index** object represents a clustered index for a table (Microsoft Access workspaces only). Read/write **Boolean**.  <br/> |
|**[DistinctCount](index-distinctcount-property-dao.md)** <br/> |Returns a value that indicates the number of unique values for the **[Index](index-object-dao.md)** object that are included in the associated table (Microsoft Access workspaces only).  <br/> |
|**[Fields](index-fields-property-dao.md)** <br/> |Returns a **Fields** collection that represents all stored **Field** objects for the specified object. Read/write.  <br/> |
|**[Foreign](index-foreign-property-dao.md)** <br/> |Returns a value that indicates whether an **[Index](index-object-dao.md)** object represents a foreign key in a table (Microsoft Access workspaces only). .  <br/> |
|**[IgnoreNulls](index-ignorenulls-property-dao.md)** <br/> |Sets or returns a value that indicates whether records that have Null values in their index fields have index entries (Microsoft Access workspaces only).  <br/> |
|**[Name](index-name-property-dao.md)** <br/> |Returns or sets the name of the specified object. Read/write **String** if the object has not been appended to a collection. Read-only **String** if the object has been appended to a collection.  <br/> |
|**[Primary](index-primary-property-dao.md)** <br/> |Sets or returns a value that indicates whether an **[Index](index-object-dao.md)** object represents a primary key index for a table (Microsoft Access workspaces only).  <br/> |
|**[Properties](index-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[Required](index-required-property-dao.md)** <br/> |Sets or returns a value that indicates whether a **[Field](field-object-dao.md)** object requires a non-Null value.  <br/> |
|**[Unique](index-unique-property-dao.md)** <br/> |Sets or returns a value that indicates whether an **[Index](index-object-dao.md)** object represents a unique (key) index for a table (Microsoft Access workspaces only).  <br/> |
   

