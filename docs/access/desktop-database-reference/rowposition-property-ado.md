---
title: RowPosition property (ADO)
TOCTitle: RowPosition property (ADO)
ms:assetid: b87f14b0-136b-0564-3e12-f9d5ecc4f7c8
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249887(v=office.15)
ms:contentKeyID: 48547325
ms.date: 09/18/2015
mtps_version: v=office.15
---

# RowPosition property (ADO)

**Applies to**: Access 2013, Office 2013

Gets or sets an OLE DB **RowPosition** object from/on an **ADORecordsetConstruction** object. When you use **put\_RowPosition** to set the **RowPosition** object, the resulting **Recordset** object uses the **RowPosition** object to determine the current row.

Read/write.

## Syntax

HRESULT get\_RowPosition(\[out, retval\] IUnknown\*\* ppRowPos);

HRESULT put\_RowPosition(\[in\] IUnknown\* pRowPos);

## Parameters

|Parameter|Description|
|:--------|:----------|
|*ppRowPos* |Pointer to an OLE DB **RowPosition** object.|
|*PRowPos* |An OLE DB **RowPosition** object.|

## Return values

This property method returns the standard HRESULT values, including S\_OK and E\_FAIL.

## Remarks

When this property is set, if the **Rowset** object on the **RowPosition** object is different from the **Rowset** object on the **Recordset** object, the former overrides the latter. The same behavior applies to the current **Chapter** of the **RowPosition** as well.

## Applies to

[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md)

