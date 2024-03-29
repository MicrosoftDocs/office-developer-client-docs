---
title: Field.Attributes property (DAO)
TOCTitle: Attributes Property
description: Attributes property
ms:assetid: 8e6f6afb-1a89-7315-c129-cf7ff19e0ca9
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197380(v=office.15)
ms:contentKeyID: 48546287
ms.date: 09/14/2021
mtps_version: v=office.15
ms.localizationpriority: high
---

# Field.Attributes property (DAO)

**Applies to**: Access 2013, Office 2013

Sets or returns a value that indicates one or more characteristics of a **[Field](field-object-dao.md)** object. Read/write **Long**.

## Syntax

*expression* .Attributes

*expression* A variable that represents a **Field** object.

## Remarks

The **Attributes** property of a **Field** object specifies characteristics of the field represented by the **Field** object. The **Attributes** property is stored as a single Long Integer and is the sum of the following Long constants:


|**Constant**|**Value**|**Description**|
|:----------|:----------|:----------|
|**dbAutoIncrField**|**16**|The field value for new records is automatically incremented to a unique Long integer that can't be changed (in a Microsoft Access workspace, supported only for Microsoft Access database engine database tables).|
|**dbDescending**|**1**|The field is sorted in descending (Z to A or 100 to 0) order; this option applies only to a <strong>Field</strong> object in a <strong>Fields</strong> collection of an <strong>Index</strong> object. If you omit this constant, the field is sorted in ascending (A to Z or 0 to 100) order. This is the default value for <strong>Index</strong> and <strong>TableDef</strong> fields (Microsoft Access workspaces only).|
|**dbFixedField**|**1**|The field size is fixed (default for Numeric fields).|
|**dbHyperlinkField**|**32768**|The field contains hyperlink information (Memo fields only).|
|**dbSystemField**|**8192**|The field stores replication information for replicas; you can't delete this type of field (Microsoft Access workspace only).|
|**dbUpdatableField**|**32**|The field value can be changed.|
|**dbVariableField**|**2**|The field size is variable (Text fields only).\

For an object not yet appended to a collection, this property is read/write. For an appended **Field** object, the availability of the **Attributes** property depends on the object that contains the **Fields** collection.

|**If the Field object belongs to an**|**Then Attributes is**|
|:----------|:----------|
|**Index**object|Read/write until the **TableDef** object that the **Index** object is appended to is appended to a **Database** object; then the property is read-only.|
|**QueryDef**object|Read-only|
|**Recordset**object|Read-only|
|**Relation**object|Not supported|
|**TableDef**object|Read/write|

When you set multiple attributes, you can combine them by summing the appropriate constants. Any invalid values are ignored without producing an error.

## Example

This example displays the **Attributes** property for **Field**, **Relation**, and **TableDef** objects in the Northwind database.

```vb 
Sub AttributesX() 
 
 Dim dbsNorthwind As Database 
 Dim fldLoop As Field 
 Dim relLoop As Relation 
 Dim tdfloop As TableDef 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 
 ' Display the attributes of a TableDef object's 
 ' fields. 
 Debug.Print "Attributes of fields in " & _ 
 .TableDefs(0).Name & " table:" 
 For Each fldLoop In .TableDefs(0).Fields 
 Debug.Print " " & fldLoop.Name & " = " & _ 
 fldLoop.Attributes 
 Next fldLoop 
 
 ' Display the attributes of the Northwind database's 
 ' relations. 
 Debug.Print "Attributes of relations in " & _ 
 .Name & ":" 
 For Each relLoop In .Relations 
 Debug.Print " " & relLoop.Name & " = " & _ 
 relLoop.Attributes 
 Next relLoop 
 
 ' Display the attributes of the Northwind database's 
 ' tables. 
 Debug.Print "Attributes of tables in " & .Name & ":" 
 For Each tdfloop In .TableDefs 
 Debug.Print " " & tdfloop.Name & " = " & _ 
 tdfloop.Attributes 
 Next tdfloop 
 
 .Close 
 End With 
 
End Sub 
 
```

