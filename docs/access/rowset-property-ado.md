---
title: "Rowset Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 1a1cb3ef-8f3c-30c1-3eb0-8618fdcacd53

---

# Rowset Property (ADO)

Gets or sets an OLE DB **Rowset** object from/on an **ADORecordsetConstruction** object. When you use put_Rowset, the rowset is turned into an ADO **Recordset** object. 
  
Read/write.
  
## Syntax

HRESULT get_Rowset([out, retval] IUnknown\*\* ppRowset);
  
HRESULT put_Rowset([in] IUnknown\* pRowset);
  
## Parameters

-  *ppRowset* 
    
- Pointer to an OLE DB **Rowset** object. 
    
-  *PRowset* 
    
- An OLE DB **Rowset** object. 
    
## Return Values

This property method returns the standard HRESULT values, including S_OK and E_FAIL.
  
## Applies To

[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md)
  

