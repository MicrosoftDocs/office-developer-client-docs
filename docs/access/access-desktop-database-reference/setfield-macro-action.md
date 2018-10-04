---
title: SetField Macro Action
TOCTitle: SetField Macro Action
ms:assetid: 66bd26e3-e8c3-b9a1-2f16-f29adc44a345
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195227(v=office.15)
ms:contentKeyID: 48545349
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SetField Macro Action


**Applies to**: Access 2013 | Office 2013

The **SetField** action can be used to assign a value to a field.


> [!NOTE]
> <P>The <STRONG>SetField</STRONG> action is available only in Data Macros.</P>



## Setting

The **SetField** action has the arguments listed in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>A string that identifies the field.</p></td>
</tr>
<tr class="even">
<td><p><strong>Value</strong></p></td>
<td><p>An expression that specifies the value to assign to the field.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **SetField** action cannot be used outside of an **[CreateRecord](createrecord-data-block.md)** or **[EditRecord](editrecord-data-block.md)** data block.

