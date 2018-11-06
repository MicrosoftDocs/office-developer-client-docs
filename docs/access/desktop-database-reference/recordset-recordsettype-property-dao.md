---
title: Recordset.RecordsetType property (DAO)
TOCTitle: RecordsetType Property
ms:assetid: a66d4043-08cc-ead1-f9ff-efc7d7ea21bf
ms:mtpsurl: https://msdn.microsoft.com/library/Ff821178(v=office.15)
ms:contentKeyID: 48546853
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm13361
f1_categories:
- Office.Version=v15
---

# Recordset.RecordsetType property (DAO)

**Applies to**: Access 2013, Office 2013

You can use the **RecordsetType** property to specify what kind of recordset is made available to a form. Read/write **Byte**.

## Syntax

*expression* .RecordsetType

*expression* A variable that represents a **Form** object.

## Remarks

The **RecordsetType** property uses the following settings in a Microsoft Access database.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Setting</p></th>
<th><p>Type of Recordset</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Dynaset</p></td>
<td><p>(Default) You can edit bound controls based on a single table or tables with a one-to-one relationship. For controls bound to fields based on tables with a one-to-many relationship, you can't edit data from the join field on the &quot;one&quot; side of the relationship unless cascade update is enabled between the tables.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Dynaset (Inconsistent Updates)</p></td>
<td><p>All tables and controls bound to their fields can be edited.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Snapshot</p></td>
<td><p>No tables or the controls bound to their fields can be edited.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> If you don't want data in bound controls to be edited when a form is in Form view or Datasheet view, you can set the **RecordsetType** property to 2.

The **RecordsetType** property uses the following settings in a Microsoft Access project (.adp).

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Setting</p></th>
<th><p>Type of Recordset</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>3</p></td>
<td><p>Snapshot</p></td>
<td><p>No tables or the controls bound to their fields can be edited.</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Updatable Snapshot</p></td>
<td><p>(Default) All tables and controls bound to their fields can be edited.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> Changing the **RecordsetType** property of an open form or report causes an automatic recreation of the recordset.

You can create forms based on multiple underlying tables with fields bound to controls on the forms. Depending on the **RecordsetType** property setting, you can limit which of these bound controls can be edited.

In addition to the editing control provided by **RecordsetType**, each control on a form has a **Locked** property that you can set to specify whether the control and its underlying data can be edited. If the **Locked** property is set to Yes, you can't edit the data.

## Example

In the following example, only if the user ID is ADMIN can records be updated. This code sample sets the **RecordsetType** property to Snapshot if the public variable gstrUserID value is not ADMIN.

```vb
    Sub Form_Open(Cancel As Integer) 
     Const conSnapshot = 2 
     If gstrUserID <> "ADMIN" Then 
     Forms!Employees.RecordsetType = conSnapshot 
     End If 
    End Sub
```

## See also

- [Form Object](https://docs.microsoft.com/office/vba/api/Access.Form)


