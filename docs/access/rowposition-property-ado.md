---
title: "RowPosition Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b87f14b0-136b-0564-3e12-f9d5ecc4f7c8

---

# RowPosition Property (ADO)

Gets or sets an OLE DB **RowPosition** object from/on an **ADORecordsetConstruction** object. When you use **put_RowPosition** to set the **RowPosition** object, the resulting **Recordset** object uses the **RowPosition** object to determine the current row. 
  
Read/write.
  
## Syntax

HRESULT get_RowPosition([out, retval] IUnknown\*\* ppRowPos);
  
HRESULT put_RowPosition([in] IUnknown\* pRowPos);
  
## Parameters

-  *ppRowPos* 
    
- Pointer to an OLE DB **RowPosition** object. 
    
-  *PRowPos* 
    
- An OLE DB **RowPosition** object. 
    
## Return Values

This property method returns the standard HRESULT values, including S_OK and E_FAIL.
  
## Remarks

When this property is set, if the **Rowset** object on the **RowPosition** object is different from the **Rowset** object on the **Recordset** object, the former overrides the latter. The same behavior applies to the current **Chapter** of the **RowPosition** as well. 
  
## Applies To

[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md)
  

