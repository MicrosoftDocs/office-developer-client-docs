---
title: "TableDef Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bc55315e-bafe-d89e-ad31-fd4c9bb6486e
description: "A TableDef object represents the stored definition of a base table or a linked table (Microsoft Access workspaces only)."
---

# TableDef Members (DAO)

A **TableDef** object represents the stored definition of a base table or a linked table (Microsoft Access workspaces only). 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[CreateField](tabledef-createfield-method-dao.md)** <br/> |Creates a new **[Field](field-object-dao.md)** object (Microsoft Access workspaces only). .  <br/> |
|**[CreateIndex](tabledef-createindex-method-dao.md)** <br/> |Creates a new **[Index](index-object-dao.md)** object (Microsoft Access workspaces only). .  <br/> |
|**[CreateProperty](tabledef-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
|**[OpenRecordset](tabledef-openrecordset-method-dao.md)** <br/> |Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection.  <br/> |
|**[RefreshLink](tabledef-refreshlink-method-dao.md)** <br/> |Updates the connection information for a linked table (Microsoft Access workspaces only).  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Attributes](tabledef-attributes-property-dao.md)** <br/> |Sets or returns a value that indicates one or more characteristics of a **TableDef** object. Read/write **Long**.  <br/> |
|**[ConflictTable](tabledef-conflicttable-property-dao.md)** <br/> |Returns the name of a conflict table containing the database records that conflicted during the synchronization of two replicas (Microsoft Access workspaces only). Read-only **String**.  <br/> |
|**[Connect](tabledef-connect-property-dao.md)** <br/> |Sets or returns a value that provides information about a linked table. Read/write **String**.  <br/> |
|**[DateCreated](tabledef-datecreated-property-dao.md)** <br/> |Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only **Variant**.  <br/> |
|**[Fields](tabledef-fields-property-dao.md)** <br/> |Returns a **Fields** collection that represents all stored **Field** objects for the specified object. Read-only.  <br/> |
|**[Indexes](tabledef-indexes-property-dao.md)** <br/> |Returns an **Indexes** collection that contains all of the stored **Index** objects for the specified table. Read-only.  <br/> |
|**[LastUpdated](tabledef-lastupdated-property-dao.md)** <br/> |Returns the date and time of the most recent change made to an object. Read-only **Variant**.  <br/> |
|**[Name](tabledef-name-property-dao.md)** <br/> |Returns or sets the name of the specified object. Read/write **String**.  <br/> |
|**[Properties](tabledef-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[RecordCount](tabledef-recordcount-property-dao.md)** <br/> |Returns the total number of records in a **[TableDef](tabledef-object-dao.md)** object. Read-only **Long**.  <br/> |
|**[ReplicaFilter](tabledef-replicafilter-property-dao.md)** <br/> |Sets or returns a value on a **[TableDef](tabledef-object-dao.md)** object within a partial replica that indicates which subset of records is replicated to that table from a full replica. (Microsoft Access workspaces only).  <br/> |
|**[SourceTableName](tabledef-sourcetablename-property-dao.md)** <br/> |Sets or returns a value that specifies the name of a linked table or the name of a base table (Microsoft Access workspaces only).  <br/> |
|**[Updatable](tabledef-updatable-property-dao.md)** <br/> |Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**.  <br/> |
|**[ValidationRule](tabledef-validationrule-property-dao.md)** <br/> |Sets or returns a value that validates the data in a field as it's changed or added to a table (Microsoft Access workspaces only).Read/write **String**.  <br/> |
|**[ValidationText](tabledef-validationtext-property-dao.md)** <br/> |Sets or returns a value that specifies the text of the message that your application displays if the value of a **Field** object doesn't satisfy the validation rule specified by the **ValidationRule** property setting (Microsoft Access workspaces only). Read/write **String**.  <br/> |
   

