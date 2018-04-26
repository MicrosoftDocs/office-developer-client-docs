---
title: "ParentRow Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c7520353-9428-9c8f-9d21-ff42e30e1193

---

# ParentRow Property (ADO)

Sets the container of an OLE DB **Row** object on an **ADORecordConstruction** object, so that the parent of the row is turned into an ADO **Record** object. 
  
Write-only.
  
## Syntax

HRESULT put_ParentRow([in] IUnknown\* pParent);
  
## Parameters

-  *pParent* 
    
- A container of a row.
    
## Return Values

This property method returns the standard HRESULT values, including S_OK and E_FAIL.
  
## Applies To

[ADORecordConstruction](adorecordconstruction-interface-ado.md)
  

