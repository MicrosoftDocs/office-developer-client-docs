---
title: CursorType Property (ADO)
TOCTitle: CursorType Property (ADO)
ms:assetid: f42ded8f-9f92-ef03-a198-ffb892324611
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250239(v=office.15)
ms:contentKeyID: 48548682
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CursorType Property (ADO)


_**Applies to:** Access 2013 | Office 2013_

Indicates the type of cursor used in a [Recordset](recordset-object-ado.md) object.

## Settings and Return Values

Sets or returns a [CursorTypeEnum](cursortypeenum.md) value. The default value is **adOpenForwardOnly**.

## Remarks

Use the **CursorType** property to specify the type of cursor that should be used when opening the **Recordset** object.

Only a setting of **adOpenStatic** is supported if the [CursorLocation](cursorlocation-property-ado.md) property is set to **adUseClient**. If an unsupported value is set, then no error will result; the closest supported **CursorType** will be used instead.

If a provider does not support the requested cursor type, it may return another cursor type. The **CursorType** property will change to match the actual cursor type in use when the [Recordset](recordset-object-ado.md) object is open. To verify specific functionality of the returned cursor, use the [Supports](supports-method-ado.md) method. After you close the **Recordset**, the **CursorType** property reverts to its original setting.

The following chart shows the provider functionality (identified by **Supports** method constants) required for each cursor type.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>For a Recordset of this CursorType</p></th>
<th><p>The Supports method must return True for all of these constants</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>adOpenForwardOnly</strong></p></td>
<td><p>none</p></td>
</tr>
<tr class="even">
<td><p><strong>adOpenKeyset</strong></p></td>
<td><p><strong>adBookmark</strong>, <strong>adHoldRecords</strong>, <strong>adMovePrevious</strong>, <strong>adResync</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>adOpenDynamic</strong></p></td>
<td><p><strong>adMovePrevious</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>adOpenStatic</strong></p></td>
<td><p><strong>adBookmark</strong>, <strong>adHoldRecords</strong>, <strong>adMovePrevious</strong>, <strong>adResync</strong></p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>Although <STRONG>Supports</STRONG>(<STRONG>adUpdateBatch</STRONG>) may be true for dynamic and forward-only cursors, for batch updates you should use either a keyset or static cursor. Set the <A href="locktype-property-ado.md">LockType</A> property to <STRONG>adLockBatchOptimistic</STRONG> and the <STRONG>CursorLocation</STRONG> property to <STRONG>adUseClient</STRONG> to enable the Cursor Service for OLE DB, which is required for batch updates.</P>



The **CursorType** property is read/write when the **Recordset** is closed and read-only when it is open.

**Remote Data Service Usage**When used on a client-side Recordset object, the **CursorType** property can be set only to **adOpenStatic**.

