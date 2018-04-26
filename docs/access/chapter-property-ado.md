---
title: "Chapter Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d7c9478e-487f-7023-1dd8-5313433dbc5e
---

# Chapter Property (ADO)

Gets or sets an OLE DB **Chapter** object from/on an **ADORecordsetConstruction** object. When you use **put_Chapter** to set the **Chapter** object, a subset of rows is turned into an ADO **Recordset** object. This sets the current chapter of the **Rowset** object. Read/write. 
  
## Syntax

HRESULT get_Chapter([out, retval] long\* plChapter);
  
HRESULT put_Chapter([in] long lChapter);
  
## Parameters

-  *plChapter* 
    
- Pointer to the handle of a chapter.
    
-  *LChapter* 
    
- Handle of a chapter.
    
## Return Values

This property method returns the standard HRESULT values, including S_OK and E_FAIL.
  
## Applies To

[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md)
  

