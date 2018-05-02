---
title: "BuildDisplayTable"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- BuildDisplayTable
api_type:
- HeaderDef
ms.assetid: 0846415b-6fe1-4504-8620-108af6719015
description: "Last modified: March 09, 2015"
---

# BuildDisplayTable

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates a display table from the property page data contained in one or more [DTPAGE](dtpage.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```
STDAPI BuildDisplayTable(
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPALLOCATEMORE lpAllocateMore,
  LPFREEBUFFER lpFreeBuffer,
  LPMALLOC lpMalloc,
  HINSTANCE hInstance,
  UINT cPages,
  LPDTPAGE lpPage,
  ULONG ulFlags,
  LPMAPITABLE * lppTable,
  LPTABLEDATA * lppTblData
);
```

## Parameters

 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory. 
    
 _lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used to allocate additional memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory. 
    
 _lpMalloc_
  
> Unused; should be set to NULL. 
    
 _hInstance_
  
> [in] An instance of a MAPI object from which **BuildDisplayTable** retrieves resources. 
    
 _cPages_
  
> [in] Count of [DTPAGE](dtpage.md) structures in the array pointed to by the  _lpPage_ parameter. 
    
 _lpPage_
  
> [in] Pointer to an array of **DTPAGE** structures that contain information about the display table pages to be built. 
    
 _ulFlags_
  
> [in] Bitmask of flags. The following flag can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppTable_
  
> [out] Pointer to a pointer to the display table, which exposes the [IMAPITable](imapitableiunknown.md) interface. 
    
 _lppTblData_
  
> [in, out] Pointer to a pointer to a table data object exposing the [ITableData](itabledataiunknown.md) interface on the table returned in the  _lppTable_ parameter. If no table data object is desired,  _lppTblData_ should be set to NULL instead of a pointer value. 
    
## Return value

None
  
## Remarks

MAPI uses the functions pointed to by  _lpAllocateBuffer_,  _lpAllocateMore_, and  _lpFreeBuffer_ for most memory allocation and deallocation, in particular to allocate memory for use by client applications when calling object interfaces such as [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPITable::QueryRows](imapitable-queryrows.md). 
  
## Notes to Callers

Everything possible is read from the dialog resource, including:
  
- The page title that is, the  _ulbLpszLabel_ member of the [DTBLPAGE](dtblpage.md) structure read from the dialog title in the resource. 
    
- All control titles that is, the  _ulbLpszLabel_ members of other control structures read from the control text in the resource. 
    
 **BuildDisplayTable** overwrites anything passed in the input control structures with information from the dialog resource, which means the caller of **BuildDisplayTable** cannot dynamically specify page or control titles. Callers who need to do that can have **BuildDisplayTable** return the table data object in  _lppTableData_ and change rows in it; or they can build the display table by hand in a table data object instead. 
  
If  _lppTableData_ is not set to NULL, the provider is responsible for freeing the table data object when it is finished with the display table. 
  

