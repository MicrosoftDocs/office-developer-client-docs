---
title: Index.Required Property (DAO)
TOCTitle: Required Property
ms:assetid: ec8fafc4-8155-c48e-b3c8-2d9be425175a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff836310(v=office.15)
ms:contentKeyID: 48548518
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052963
f1_categories:
- Office.Version=v15
---

# Index.Required Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

Sets or returns a value that indicates whether a **[Field](field-object-dao.md)** object requires a non-Null value.

## Syntax

*expression* .Required

*expression* A variable that represents an **Index** object.

## Remarks


> [!NOTE]
> <P>When you can set this property for either an <STRONG>Index</STRONG> object or a <STRONG>Field</STRONG> object, set it for the <STRONG>Field</STRONG> object. The validity of the property setting for a <STRONG>Field</STRONG> object is checked before that of an <STRONG>Index</STRONG> object.</P>



The availability of the **Required** property depends on the object that contains the [Fields](fields-collection-dao.md) collection, as shown in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
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

