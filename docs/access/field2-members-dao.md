---
title: "Field2 Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 27829bbc-8b4e-c7eb-f29b-bcbef341f9fd
description: "A Field2 object represents a column of data with a common data type and a common set of properties."
---

# Field2 Members (DAO)

A **Field2** object represents a column of data with a common data type and a common set of properties. 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[AppendChunk](field2-appendchunk-method-dao.md)** <br/> |Appends data from a string expression to a Memo or Long Binary **Field2** object in a **[Recordset](recordset-object-dao.md)**.  <br/> |
|**[CreateProperty](field2-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
|**[GetChunk](field2-getchunk-method-dao.md)** <br/> |Returns all or a portion of the contents of a **Memo** or **Long Binary** **Field2** object in the **[Fields](fields-collection-dao.md)** collection of a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[LoadFromFile](field2-loadfromfile-method-dao.md)** <br/> |Loads the specified file from disk.  <br/> |
|**[SaveToFile](field2-savetofile-method-dao.md)** <br/> |Saves an attachment to disk. .  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[AllowZeroLength](field2-allowzerolength-property-dao.md)** <br/> |Sets or returns a value that indicates whether a zero-length string ("") is a valid setting for the **[Value](field-value-property-dao.md)** property of the **Field2** object with a Text or Memo data type (Microsoft Access workspaces only).  <br/> |
|**[AppendOnly](field2-appendonly-property-dao.md)** <br/> |Gets or sets a **Boolean** that indicates whether the spcified field is set to append new values to the existing contents of the field as they are added. Read/write.  <br/> |
|**[Attributes](field2-attributes-property-dao.md)** <br/> |Sets or returns a value that indicates one or more characteristics of a **Field2** object. Read/write **Long**.  <br/> |
|**[CollatingOrder](field2-collatingorder-property-dao.md)** <br/> |Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only **Long**.  <br/> |
|**[ComplexType](field2-complextype-property-dao.md)** <br/> |Returns a **[ComplexType](complextype-object-dao.md)** object that represents a multi-valued field. Read-only.  <br/> |
|**[DataUpdatable](field2-dataupdatable-property-dao.md)** <br/> |Returns a value that indicates whether the data in the field represented by a **Field2** object is updatable.  <br/> |
|**[DefaultValue](field2-defaultvalue-property-dao.md)** <br/> |Sets or returns the default value of a **Field2** object. For a **Field2** object not yet appended to the **[Fields](fields-collection-dao.md)** collection, this property is read/write (Microsoft Access workspaces only).  <br/> |
|**[Expression](field2-expression-property-dao.md)** <br/> |Read/write  <br/> |
|**[FieldSize](field2-fieldsize-property-dao.md)** <br/> |Returns the number of bytes used in the database (rather than in memory) of a Memo or Long Binary **Field2** object in the **[Fields](fields-collection-dao.md)** collection of a **[Recordset](recordset-object-dao.md)** object.  <br/> |
|**[ForeignName](field2-foreignname-property-dao.md)** <br/> |Sets or returns a value that specifies the name of the **Field2** object in a foreign table that corresponds to a field in a primary table for a relationship (Microsoft Access workspaces only).  <br/> |
|**[IsComplex](field2-iscomplex-property-dao.md)** <br/> |Returns **Boolean** that indicates whether the specified field is a multi-valued data type. Read-only.  <br/> |
|**[Name](field2-name-property-dao.md)** <br/> |Returns or sets the name of the specified object. Read/write **String** if the object has not been appended to a collection. Read-only **String** if the object has been appended to a collection.  <br/> |
|**[OrdinalPosition](field2-ordinalposition-property-dao.md)** <br/> |Sets or returns the relative position of a **Field2** object within a **[Fields](fields-collection-dao.md)** collection. .  <br/> |
|**[OriginalValue](field2-originalvalue-property-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns the value of a **Field2** in the database that existed when the last batch update began (ODBCDirect workspaces only).  <br/> |
|**[Properties](field2-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[Required](field2-required-property-dao.md)** <br/> |Sets or returns a value that indicates whether a **Field2** object requires a non-Null value.  <br/> |
|**[Size](field2-size-property-dao.md)** <br/> |Sets or returns a value that indicates the maximum size, in bytes, of a **Field2** object.  <br/> |
|**[SourceField](field2-sourcefield-property-dao.md)** <br/> |Returns a value that indicates the name of the field that is the original source of the data for a **Field2** object. Read-only **String**.  <br/> |
|**[SourceTable](field2-sourcetable-property-dao.md)** <br/> |Returns a value that indicates the name of the table that is the original source of the data for a **Field2** object. Read-only **String**.  <br/> |
|**[Type](field2-type-property-dao.md)** <br/> |Sets or returns a value that indicates the operational type or data type of an object. Read/write **Integer**.  <br/> |
|**[ValidateOnSet](field2-validateonset-property-dao.md)** <br/> |Sets or returns a value that specifies whether or not the value of a **Field2** object is immediately validated when the object's **Value** property is set (Microsoft Access workspaces only).  <br/> |
|**[ValidationRule](field2-validationrule-property-dao.md)** <br/> |Sets or returns a value that validates the data in a field as it's changed or added to a table (Microsoft Access workspaces only). Read/write **String**.  <br/> |
|**[ValidationText](field2-validationtext-property-dao.md)** <br/> |Sets or returns a value that specifies the text of the message that your application displays if the value of a **Field2** object doesn't satisfy the validation rule specified by the **ValidationRule** property setting (Microsoft Access workspaces only). Read/write **String**.  <br/> |
|**[Value](field2-value-property-dao.md)** <br/> |Sets or returns the value of an object. Read/write **Variant**.  <br/> |
|**[VisibleValue](field2-visiblevalue-property-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Returns a value currently in the database that is newer than the **OriginalValue** property as determined by a batch update conflict (ODBCDirect workspaces only).  <br/> |
   

