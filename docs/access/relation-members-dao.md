---
title: "Relation Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9ee36e7d-3825-1de8-65fb-64bbcada847c
description: "A Relation object represents a relationship between fields in tables or queries (Microsoft Access database engine databases only)."
---

# Relation Members (DAO)

A **Relation** object represents a relationship between fields in tables or queries (Microsoft Access database engine databases only). 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[CreateField](relation-createfield-method-dao.md)** <br/> |Creates a new **[Field](field-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Attributes](relation-attributes-property-dao.md)** <br/> |Sets or returns a value that indicates one or more characteristics of a **Relation** object. Read/write **Long**.  <br/> |
|**[Fields](relation-fields-property-dao.md)** <br/> |Returns a **Fields** collection that represents all stored **Field** objects for the specified object. Read-only.  <br/> |
|**[ForeignTable](relation-foreigntable-property-dao.md)** <br/> |Sets or returns the name of the foreign table in a relationship (Microsoft Access workspaces only). .  <br/> |
|**[Name](relation-name-property-dao.md)** <br/> |Returns or sets the name of the specified object. Read/write **String** if the object has not been appended to a collection. Read-only **String** if the object has been appended to a collection.  <br/> |
|**[PartialReplica](relation-partialreplica-property-dao.md)** <br/> |Sets or returns a value on a **Relation** object indicating whether that relation should be considered when populating a partial replica from a full replica. (Microsoft Access database engine databases only). Read/write **Boolean**.  <br/> |
|**[Properties](relation-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[Table](relation-table-property-dao.md)** <br/> |Indicates the name of a **[Relation](relation-object-dao.md)** object's primary table. This should be equal to the **[Name](connection-name-property-dao.md)** property setting of a **[TableDef](tabledef-object-dao.md)** or **[QueryDef](querydef-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
   

