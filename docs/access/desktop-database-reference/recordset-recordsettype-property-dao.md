---
title: Recordset.RecordsetType property (DAO)
TOCTitle: RecordsetType Property
ms:assetid: a66d4043-08cc-ead1-f9ff-efc7d7ea21bf
ms:mtpsurl: https://msdn.microsoft.com/library/Ff821178(v=office.15)
ms:contentKeyID: 48546853
ms.date: 03/22/2022
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm13361
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# Recordset.RecordsetType property (DAO)

**Applies to**: Access 2013, Office 2013

You can use the **RecordsetType** property to specify what kind of recordset is made available to a form. Read/write **Byte**.

## Syntax

*expression* .RecordsetType

*expression* A variable that represents a **Form** object.

## Remarks

The **RecordsetType** property uses the following settings in a Microsoft Access database.

|**Setting**|**Type of Recordset**|**Description**|
|:----------|:--------------------|:--------------|
| 0 | Dynaset (Default)  | You can edit bound controls based on a single table or tables with a one-to-one relationship. For controls bound to fields based on tables with a one-to-many relationship, you can't edit data from the join field on the &quot;one&quot; side of the relationship unless cascade update is enabled between the tables.</br>|
| 1 | Dynaset (Inconsistent Updates) | All tables and controls bound to their fields can be edited.</br>|
| 2| Snapshot | No tables or the controls bound to their fields can be edited.</br>|

> [!NOTE]
> If you don't want data in bound controls to be edited when a form is in Form view or Datasheet view, you can set the **RecordsetType** property to 2.

The **RecordsetType** property uses the following settings in a Microsoft Access project (.adp).

|**Setting**|**Type of Recordset**|**Description**|
|:----------|:--------------------|:--------------|
| 3 | Snapshot | No tables or the controls bound to their fields can be edited.</br>|
| 4 | Updatable Snapshot | (Default) All tables and controls bound to their fields can be edited.</br>|

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

- [Form Object](/office/vba/api/Access.Form.md)
