---
title: "FreeProws"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- FreeProws
api_type:
- HeaderDef
ms.assetid: 0f8f9fc4-4940-4c0a-92cc-2a6409b9a13f
description: "Last modified: March 09, 2015"
---

# FreeProws

  
  
**Applies to**: Outlook 
  
Destroys an [SRowSet](srowset.md) structure and frees associated memory, including memory allocated for all member arrays and structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
void FreeProws(
  LPSRowSet prows
);
```

## Parameters

 _prows_
  
> [in] Pointer to the **SRowSet** structure to be destroyed. 
    
## Return value

None.
  
## Notes to callers

As part of its implementation of **FreeProws**, MAPI calls the [MAPIFreeBuffer](mapifreebuffer.md) function to free every entry in the **SRowSet** structure before freeing the complete structure. Therefore all such entries must have followed the allocation rules for the [SRowSet](srowset.md) structure, using an individual [MAPIAllocateBuffer](mapiallocatebuffer.md) call for each member array and structure. 
  
For more information about allocating memory for **ADRLIST** and **SRowSet** structures, see [Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md). 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |DwThreadFuncLoadTable  <br/> |MFCMAPI uses the **FreeProws** method to free an SRowSet structure containing rows of the table being processed.  <br/> |
   
## See also



[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

