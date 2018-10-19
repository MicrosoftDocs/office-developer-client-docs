---
title: Rowset property (ADO)
TOCTitle: Rowset property (ADO)
ms:assetid: 1a1cb3ef-8f3c-30c1-3eb0-8618fdcacd53
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248946(v=office.15)
ms:contentKeyID: 48543515
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Rowset property (ADO)


**Applies to**: Access 2013, Office 2013



Gets or sets an OLE DB **Rowset** object from/on an **ADORecordsetConstruction** object. When you use put\_Rowset, the rowset is turned into an ADO **Recordset** object.

Read/write.

## Syntax

HRESULT get\_Rowset(\[out, retval\] IUnknown\*\* ppRowset);

HRESULT put\_Rowset(\[in\] IUnknown\* pRowset);

## Parameters

  - *ppRowset*

  - Pointer to an OLE DB **Rowset** object.

  - *PRowset*

  - An OLE DB **Rowset** object.

## Return values

This property method returns the standard HRESULT values, including S\_OK and E\_FAIL.

## Applies To

[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md)

