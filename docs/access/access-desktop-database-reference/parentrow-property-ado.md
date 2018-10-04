---
title: ParentRow Property (ADO)
TOCTitle: ParentRow Property (ADO)
ms:assetid: c7520353-9428-9c8f-9d21-ff42e30e1193
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249971(v=office.15)
ms:contentKeyID: 48547638
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ParentRow Property (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Return Values  
Applies To  

Sets the container of an OLE DB **Row** object on an **ADORecordConstruction** object, so that the parent of the row is turned into an ADO **Record** object.

Write-only.

## Syntax

HRESULT put\_ParentRow(\[in\] IUnknown\* pParent);

## Parameters

  - *pParent*

  - A container of a row.

## Return Values

This property method returns the standard HRESULT values, including S\_OK and E\_FAIL.

## Applies To

[ADORecordConstruction](adorecordconstruction-interface-ado.md)

