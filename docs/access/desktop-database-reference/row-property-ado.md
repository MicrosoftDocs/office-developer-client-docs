---
title: Row Property (ADO)
TOCTitle: Row Property (ADO)
ms:assetid: 1c2b0e27-7232-4b1c-826c-9dc15d758851
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248959(v=office.15)
ms:contentKeyID: 48543562
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Row Property (ADO)


**Applies to**: Access 2013 | Office 2013



Gets or sets an OLE DB **Row** object from/on an **ADORecordConstruction** object. When you use **put\_Row** to set a **Row** object, a row is turned into an ADO **Record** object. Read/write.

## Syntax

HRESULT get\_Row(\[out, retval\] IUnknown\*\* ppRow);

HRESULT put\_Row(\[in\] IUnknown\* pRow);

## Parameters

  - *ppRow*

  - Pointer to an OLE DB **Row** object.

  - *PRow*

  - An OLE DB **Row** object.

## Return Values

This property method returns the standard HRESULT values, including S\_OK and E\_FAIL.

## Applies To

[ADORecordConstruction](adorecordconstruction-interface-ado.md)

