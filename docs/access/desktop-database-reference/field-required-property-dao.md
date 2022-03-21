---
title: Field.Required property (DAO)
TOCTitle: Required Property
ms:assetid: 2f1dbdeb-a37a-59b2-fdc2-f16c7ae1a575
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192247(v=office.15)
ms:contentKeyID: 48543999
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Field.Required property (DAO)


**Applies to**: Access 2013, Office 2013

Sets or returns a value that indicates whether a **[Field](field-object-dao.md)** object requires a non-Null value.

## Syntax

*expression* .Required

*expression* A variable that represents a **Field** object.

## Remarks

For a **Field** not yet appended to the **Fields** collection, this property is read/write.

The availability of the **Required** property depends on the object that contains the [Fields](fields-collection-dao.md) collection, as shown in the following table.

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>If the Fields collection belongs to a</p></th>
<th><p>Then Required is</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Index</strong> object</p></td>
<td><p>Not supported</p></td>
</tr>
<tr class="even">
<td><p><strong>QueryDef</strong> object</p></td>
<td><p>Read-only</p></td>
</tr>
<tr class="odd">
<td><p><strong>Recordset</strong> object</p></td>
<td><p>Read-only</p></td>
</tr>
<tr class="even">
<td><p><strong>Relation</strong> object</p></td>
<td><p>Not supported</p></td>
</tr>
<tr class="odd">
<td><p><strong>TableDef</strong> object</p></td>
<td><p>Read/write</p></td>
</tr>
</tbody>
</table>


You can use the **Required** property along with the **[AllowZeroLength](field-allowzerolength-property-dao.md)**, **[ValidateOnSet](field-validateonset-property-dao.md)**, or **[ValidationRule](field-validationrule-property-dao.md)** property to determine the validity of the **[Value](field-value-property-dao.md)** property setting for that **Field** object. If the **Required** property is set to **False**, the field can contain **null** values as well as values that meet the conditions specified by the **AllowZeroLength** and **ValidationRule** property settings.


> [!NOTE]
> When you can set this property for either an **Index** object or a **Field** object, set it for the **Field** object. The validity of the property setting for a **Field** object is checked before that of an **Index** object.



## Example

This example uses the **Required** property to report which fields in three different tables must contain data in order for a new record to be added. The RequiredOutput procedure is required for this procedure to run.

```vb 
Sub RequiredX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfloop As TableDef 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 ' Show which fields are required in the Fields 
 ' collections of three different TableDef objects. 
 RequiredOutput .TableDefs("Categories") 
 RequiredOutput .TableDefs("Customers") 
 RequiredOutput .TableDefs("Employees") 
 .Close 
 End With 
 
End Sub 
 
Sub RequiredOutput(tdfTemp As TableDef) 
 
 Dim fldLoop As Field 
 
 ' Enumerate Fields collection of the specified TableDef 
 ' and show the Required property. 
 Debug.Print "Fields in " & tdfTemp.Name & ":" 
 For Each fldLoop In tdfTemp.Fields 
 Debug.Print , fldLoop.Name & ", Required = " & _ 
 fldLoop.Required 
 Next fldLoop 
 
End Sub 
 
```

