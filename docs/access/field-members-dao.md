---
title: "Field Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4b6a587f-1fd0-37fb-db7d-75b587a8dc60
description: "A Field object represents a column of data with a common data type and a common set of properties."
---

# Field Members (DAO)

A **Field** object represents a column of data with a common data type and a common set of properties. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[AppendChunk](field-appendchunk-method-dao.md)** <br/> |Appends data from a string expression to a Memo or Long Binary **[Field](field-object-dao.md)** object in a **[Recordset](recordset-object-dao.md)**.  <br/> |
|**[CreateProperty](field-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
|**[GetChunk](field-getchunk-method-dao.md)** <br/> |Returns all or a portion of the contents of a **Memo** or **Long Binary** **[Field](field-object-dao.md)** object in the **[Fields](fields-collection-dao.md)** collection of a **[Recordset](recordset-object-dao.md)** object.  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[AllowZeroLength](field-allowzerolength-property-dao.md)** <br/> |Sets or returns a value that indicates whether a zero-length string ("") is a valid setting for the **[Value](field-value-property-dao.md)** property of the **[Field](field-object-dao.md)** object with a Text or Memo data type (Microsoft Access workspaces only).  <br/> |
|**[Attributes](field-attributes-property-dao.md)** <br/> |Sets or returns a value that indicates one or more characteristics of a **[Field](field-object-dao.md)** object. Read/write **Long**.  <br/> |
|**[CollatingOrder](field-collatingorder-property-dao.md)** <br/> |Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only **Long**.  <br/> |
|**[DataUpdatable](field-dataupdatable-property-dao.md)** <br/> |Returns a value that indicates whether the data in the field represented by a **[Field](field-object-dao.md)** object is updatable.  <br/> |
|**[DefaultValue](field-defaultvalue-property-dao.md)** <br/> |Sets or returns the default value of a **[Field](field-object-dao.md)** object. For a **Field** object not yet appended to the **[Fields](fields-collection-dao.md)** collection, this property is read/write (Microsoft Access workspaces only).  <br/> |
|**[FieldSize](field-fieldsize-property-dao.md)** <br/> |Returns the number of bytes used in the database (rather than in memory) of a Memo or Long Binary **[Field](field-object-dao.md)** object in the **[Fields](fields-collection-dao.md)** collection of a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[ForeignName](field-foreignname-property-dao.md)** <br/> |Sets or returns a value that specifies the name of the **[Field](field-object-dao.md)** object in a foreign table that corresponds to a field in a primary table for a relationship (Microsoft Access workspaces only).  <br/> |
|**[Name](field-name-property-dao.md)** <br/> |Returns or sets the name of the specified object. Read/write **String** if the object has not been appended to a collection. Read-only **String** if the object has been appended to a collection.  <br/> |
|**[OrdinalPosition](field-ordinalposition-property-dao.md)** <br/> |Sets or returns the relative position of a **[Field](field-object-dao.md)** object within a **[Fields](fields-collection-dao.md)** collection. .  <br/> |
|**[OriginalValue](field-originalvalue-property-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns the value of a **Field** in the database that existed when the last batch update began (ODBCDirect workspaces only).  <br/> |
|**[Properties](field-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[Required](field-required-property-dao.md)** <br/> |Sets or returns a value that indicates whether a **[Field](field-object-dao.md)** object requires a non-Null value.  <br/> |
|**[Size](field-fieldsize-property-dao.md)** <br/> |Returns the number of bytes used in the database (rather than in memory) of a Memo or Long Binary **[Field](field-object-dao.md)** object in the **[Fields](fields-collection-dao.md)** collection of a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[SourceField](field-sourcefield-property-dao.md)** <br/> |Returns a value that indicates the name of the field that is the original source of the data for a **Field** object. Read-only **String**.  <br/> |
|**[SourceTable](field-sourcetable-property-dao.md)** <br/> |Returns a value that indicates the name of the table that is the original source of the data for a **Field** object. Read-only **String**.  <br/> |
|**[Type](field-type-property-dao.md)** <br/> |Sets or returns a value that indicates the operational type or data type of an object. Read/write **Integer**.  <br/> |
|**[ValidateOnSet](field-validateonset-property-dao.md)** <br/> |Sets or returns a value that specifies whether or not the value of a **[Field](field-object-dao.md)** object is immediately validated when the object's **[Value](field-value-property-dao.md)** property is set (Microsoft Access workspaces only).  <br/> |
|**[ValidationRule](field-validationrule-property-dao.md)** <br/> |Sets or returns a value that validates the data in a field as it's changed or added to a table (Microsoft Access workspaces only). Read/write **String**.  <br/> |
|**[ValidationText](field-validationtext-property-dao.md)** <br/> |Sets or returns a value that specifies the text of the message that your application displays if the value of a **Field** object doesn't satisfy the validation rule specified by the **ValidationRule** property setting (Microsoft Access workspaces only). Read/write **String**.  <br/> |
|**[Value](field-value-property-dao.md)** <br/> |Sets or returns the value of an object. Read/write **Variant**.  <br/> |
|**[VisibleValue](field-visiblevalue-property-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns a value currently in the database that is newer than the **OriginalValue** property as determined by a batch update conflict (ODBCDirect workspaces only).  <br/> |
   

