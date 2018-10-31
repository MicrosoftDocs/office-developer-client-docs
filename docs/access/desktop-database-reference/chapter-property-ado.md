---
title: Chapter property (ADO)
TOCTitle: Chapter property (ADO)
ms:assetid: d7c9478e-487f-7023-1dd8-5313433dbc5e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250085(v=office.15)
ms:contentKeyID: 48548014
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Chapter property (ADO)


**Applies to**: Access 2013 | Office 2013
 

Gets or sets an OLE DB **Chapter** object from/on an **ADORecordsetConstruction** object. When you use **put\_Chapter** to set the **Chapter** object, a subset of rows is turned into an ADO **Recordset** object. This sets the current chapter of the **Rowset** object. Read/write.

## Syntax

HRESULT get\_Chapter(\[out, retval\] long\* plChapter);

HRESULT put\_Chapter(\[in\] long lChapter);

## Parameters

  - *plChapter*

  - Pointer to the handle of a chapter.

  - *LChapter*

  - Handle of a chapter.

## Return values

This property method returns the standard HRESULT values, including S\_OK and E\_FAIL.

## Applies To

[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md)

