﻿---
title: Filter Property (ADO)
TOCTitle: Filter Property (ADO)
ms:assetid: 5abc528a-a6ee-34de-5d44-a3249194b0a0
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249314(v=office.15)
ms:contentKeyID: 48545053
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Filter Property (ADO)


**Applies to**: Access 2013 | Office 2013

Indicates a filter for data in a [Recordset](recordset-object-ado.md).

## Settings and Return Values

Sets or returns a **Variant** value, which can contain one of the following:

  - **Criteria string** — a string made up of one or more individual clauses concatenated with **AND** or **OR** operators.

  - **Array of bookmarks** — an array of unique bookmark values that point to records in the **Recordset** object.

  - A [FilterGroupEnum](filtergroupenum.md) value.

## Remarks

Use the **Filter** property to selectively screen out records in a **Recordset** object. The filtered **Recordset** becomes the current cursor. Other properties that return values based on the current cursor are affected, such as [AbsolutePosition](absoluteposition-property-ado.md), [AbsolutePage](absolutepage-property-ado.md), [RecordCount](recordcount-property-ado.md), and [PageCount](pagecount-property-ado.md). This is because setting the **Filter** property to a specific value will move the current record to the first record that satisfies the new value.

The criteria string is made up of clauses in the form *FieldName-Operator-Value* (for example, "LastName = 'Smith'"). You can create compound clauses by concatenating individual clauses with **AND** (for example, "LastName = 'Smith' AND FirstName = 'John'") or **OR** (for example, "). You can create compound clauses by concatenating individual clauses with **AND** (for example, "LastName = 'Smith' AND FirstName = 'John'") or **OR** (for example, "LastName = 'Smith' OR LastName = 'Jones'"). Use the following guidelines for criteria strings:

  - *FieldName* must be a valid field name from the **Recordset**. If the field name contains spaces, you must enclose the name in square brackets.

  - *Operator* must be one of the following: \<, \>, \<=, \>=, \<\>, =, or **LIKE**.

  - *Value* is the value with which you will compare the field values (for example, 'Smith', \#8/24/95\#, 12.345, or $50.00). Use single quotes with strings and pound signs (\#) with dates. For numbers, you can use decimal points, dollar signs, and scientific notation. If *Operator* is **LIKE**, *Value* can use wildcards. Only the asterisk (\*) and percent sign (%) wild cards are allowed, and they must be the last character in the string. *Value* cannot be null.
    

    > [!NOTE]
    > <P>To include single quotation marks (') in the filter Value, use two single quotation marks to represent one. For example, to filter on O'Malley, the criteria string should be "col1 = 'O''Malley'". To include single quotation marks at both the beginning and the end of the filter value, enclose the string with pound signs (#). For example, to filter on '1', the criteria string should be "col1 = #'1'#".</P>



  - There is no precedence between **AND** and **OR**. Clauses can be grouped within parentheses. However, you cannot group clauses joined by an **OR** and then join the group to another clause with an **AND**, like this:

  - Instead, you would construct this filter as

  - In a **LIKE** clause, you can use a wildcard at the beginning and end of the pattern (for example, LastName Like '\*mit\*'), or only at the end of the pattern (for example, LastName Like 'Smit\*').

The filter constants make it easier to resolve individual record conflicts during batch update mode by allowing you to view, for example, only those records that were affected during the last [UpdateBatch](updatebatch-method-ado.md) method call.

Setting the **Filter** property itself may fail because of a conflict with the underlying data (for example, a record has already been deleted by another user). In such a case, the provider returns warnings to the [Errors](errors-collection-ado.md) collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records. Use the [Status](status-property-ado-recordset.md) property to locate records with conflicts.

Setting the **Filter** property to a zero-length string ("") has the same effect as using the **adFilterNone** constant.

Whenever the **Filter** property is set, the current record position moves to the first record in the filtered subset of records in the **Recordset**. Similarly, when the **Filter** property is cleared, the current record position moves to the first record in the **Recordset**.

See the [Bookmark](bookmark-property-ado.md) property for an explanation of bookmark values from which you can build an array to use with the **Filter** property.

Only **Filters** in the form of Criteria Strings (e.g. OrderDate \> '12/31/1999') affect the contents of a persisted **Recordset**. **Filters** created with an Array of **Bookmarks** or using a value from the **FilterGroupEnum** will not affect the contents of the persisted Recordset. These rules apply to **Recordsets** created with either client-side or server-side cursors.


> [!NOTE]
> <P>When you apply the <STRONG>adFilterPendingRecords</STRONG> flag to a filtered and modified <STRONG>Recordset</STRONG> in the batch update mode, the resultant <STRONG>Recordset</STRONG> is empty if the filtering was based on the key field of a single-keyed table and the modification was made on the key field values. The resultant <STRONG>Recordset</STRONG> will be non-empty if one of the following is true:</P>



  - The filtering was based on non-key fields in a single-keyed table.

  - The filtering was based on any fields in a multiple-keyed table.

  - Modifications were made on non-key fields in a single-keyed table.

  - Modifications were made on any fields in a multiple-keyed table.

The following table summarizes the effects of **adFilterPendingRecords** in different combinations of filtering and modifications. The left column shows the possible modifications; modifications can be made on any of the non-keyed fields, on the key field in a single-keyed table, or on any of the key fields in a multiple-keyed table. The top row shows the filtering criterion; filtering can be based on any of the non-keyed fields, the key field in a single-keyed table, or any of the key fields in a multiple-keyed table. The intersecting cells show the results: + means that applying **adFilterPendingRecords** results in a non-empty **Recordset**; **-** means an empty **Recordset**.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p><br />
</p></th>
<th><p>Non keys</p></th>
<th><p>Single Key</p></th>
<th><p>Multiple Keys</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Non keys</p></td>
<td><p>+</p></td>
<td><p>+</p></td>
<td><p>+</p></td>
</tr>
<tr class="even">
<td><p>Single Key</p></td>
<td><p>+</p></td>
<td><p>-</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>Multiple Keys</p></td>
<td><p>+</p></td>
<td><p>N/A</p></td>
<td><p>+</p></td>
</tr>
</tbody>
</table>

