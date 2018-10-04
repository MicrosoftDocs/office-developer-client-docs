---
title: Field.Attributes Property (DAO)
TOCTitle: Attributes Property
ms:assetid: 8e6f6afb-1a89-7315-c129-cf7ff19e0ca9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197380(v=office.15)
ms:contentKeyID: 48546287
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Field.Attributes Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Sets or returns a value that indicates one or more characteristics of a **[Field](field-object-dao.md)** object. Read/write **Long**.

## Syntax

*expression* .Attributes

*expression* A variable that represents a **Field** object.

## Remarks

The value specifies characteristics of the field represented by the **Field** object and can be a combination of these constants.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>dbAutoIncrField</strong></p></td>
<td><p>The field value for new records is automatically incremented to a unique Long integer that can't be changed (in a Microsoft Access workspace, supported only for Microsoft Access database engine database tables).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbDescending</strong></p></td>
<td><p>The field is sorted in descending (Z to A or 100 to 0) order; this option applies only to a <strong>Field</strong> object in a <strong>Fields</strong> collection of an <strong>Index</strong> object. If you omit this constant, the field is sorted in ascending (A to Z or 0 to 100) order. This is the default value for <strong>Index</strong> and <strong>TableDef</strong> fields (Microsoft Access workspaces only)..</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbFixedField</strong></p></td>
<td><p>The field size is fixed (default for Numeric fields).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbHyperlinkField</strong></p></td>
<td><p>The field contains hyperlink information (Memo fields only).</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSystemField</strong></p></td>
<td><p>The field stores replication information for replicas; you can't delete this type of field (Microsoft Access workspace only).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbUpdatableField</strong></p></td>
<td><p>The field value can be changed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbVariableField</strong></p></td>
<td><p>The field size is variable (Text fields only).</p></td>
</tr>
</tbody>
</table>


For an object not yet appended to a collection, this property is read/write. For an appended **Field** object, the availability of the **Attributes** property depends on the object that contains the **Fields** collection.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>If the Field object belongs to an</p></th>
<th><p>Then Attributes is</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Index</strong> object</p></td>
<td><p>Read/write until the <strong>TableDef</strong> object that the <strong>Index</strong> object is appended to is appended to a <strong>Database</strong> object; then the property is read-only.</p></td>
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


When you set multiple attributes, you can combine them by summing the appropriate constants. Any invalid values are ignored without producing an error.

## Example

This example displays the **Attributes** property for **Field**, **Relation**, and **TableDef** objects in the Northwind database.

``` 
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

