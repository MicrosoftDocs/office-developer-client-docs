---
title: EditMode Property (ADO)
TOCTitle: EditMode Property (ADO)
ms:assetid: 28ca8f14-abee-ad20-9c16-11bb36b487e4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249045(v=office.15)
ms:contentKeyID: 48543867
ms.date: 09/18/2015
mtps_version: v=office.15
---

# EditMode Property (ADO)


_**Applies to:** Access 2013 | Office 2013_

Indicates the editing status of the current record.

## Return Value

Returns an [EditModeEnum](editmodeenum.md) value.

## Remarks

ADO maintains an editing buffer associated with the current record. This property indicates whether changes have been made to this buffer, or whether a new record has been created. Use the **EditMode** property to determine the editing status of the current record. You can test for pending changes if an editing process has been interrupted and determine whether you need to use the [Update](update-method-ado.md) or [CancelUpdate](cancelupdate-method-ado.md) method.

See the [AddNew](addnew-method-ado.md) method for a more detailed description of the **EditMode** property under different editing conditions.

When a call to [Delete](delete-method-ado-recordset.md) does not successfully delete the record or records in the data source (due to referential integrity violations, for example), the [Recordset](recordset-object-ado.md) will remain in edit mode (**EditMode** = **adEditInProgress**). This means that **CancelUpdate** must be called before moving off the current record (with [Move](move-method-ado.md), [NextRecordset](nextrecordset-method-ado.md), or [Close](close-method-ado.md), for example).


> [!NOTE]
> <P><STRONG>EditMode</STRONG> can return a valid value only if there is a current record. <STRONG>EditMode</STRONG> will return an error if <A href="bof-eof-properties-ado.md">BOF or EOF</A> is true, or if the current record has been deleted.</P>


