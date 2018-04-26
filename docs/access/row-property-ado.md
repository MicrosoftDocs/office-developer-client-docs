---
title: "Row Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 1c2b0e27-7232-4b1c-826c-9dc15d758851

---

# Row Property (ADO)

Gets or sets an OLE DB **Row** object from/on an **ADORecordConstruction** object. When you use **put_Row** to set a **Row** object, a row is turned into an ADO **Record** object. Read/write. 
  
## Syntax

HRESULT get_Row([out, retval] IUnknown\*\* ppRow);
  
HRESULT put_Row([in] IUnknown\* pRow);
  
## Parameters

-  *ppRow* 
    
- Pointer to an OLE DB **Row** object. 
    
-  *PRow* 
    
- An OLE DB **Row** object. 
    
## Return Values

This property method returns the standard HRESULT values, including S_OK and E_FAIL.
  
## Applies To

[ADORecordConstruction](adorecordconstruction-interface-ado.md)
  

