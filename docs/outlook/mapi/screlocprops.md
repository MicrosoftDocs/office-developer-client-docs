---
title: "ScRelocProps"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.ScRelocProps
api_type:
- COM
ms.assetid: 4aafb254-6074-4a7c-b915-d3d33304ac38
description: "Adjusts the pointers in an SPropValue array after the array and its data have been copied or moved to a new location."
---

# ScRelocProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Adjusts the pointers in an [SPropValue](spropvalue.md) array after the array and its data have been copied or moved to a new location. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScRelocProps(
  int cprop,
  LPSPropValue rgprop,
  LPVOID pvBaseOld,
  LPVOID pvBaseNew,
  ULONG FAR * pcb
);
```

## Parameters

 _cprop_
  
> [in] Count of properties in the array pointed to by the  _rgprop_ parameter. 
    
 _rgprop_
  
> [in] Pointer to an array of [SPropValue](spropvalue.md) structures for which pointers are to be adjusted. 
    
 _pvBaseOld_
  
> [in] Pointer to the original base address of the array pointed to by the  _rgprop_ parameter. 
    
 _pvBaseNew_
  
> [in] Pointer to the new base address of the array pointed to by the  _rgprop_ parameter. 
    
 _pcb_
  
> [in, out] Optional pointer to the size, in bytes, of the array indicated by the  _pvBaseNew_ parameter. If not NULL, the  _pcb_ parameter is set to the number of bytes stored in the _pvD_ parameter. 
    
## Return value

S_OK
  
> Pointers were adjusted successfully.
    
MAPI_E_INVALID_PARAMETER
  
> One or both parameters were invalid, or an unknown property type was encountered.
    
## Remarks

The **ScRelocProps** function operates on the assumption that the property value array for which pointers are adjusted was originally allocated in a single call similar to a call to the **ScCopyProps** function. If a client application or service provider is working with a property value that is built from disjointed blocks of memory, it should use [ScCopyProps](sccopyprops.md) to copy properties instead. 
  
 **ScRelocProps** is used to maintain the validity of pointers in an [SPropValue](spropvalue.md) array. To maintain pointers' validity when writing such an array to and reading it from a disk, perform the following operations: 
  
1. Before writing the array and data to a disk, call **ScRelocProps** on the array with the  _pvBaseNew_ parameter pointing to some standard value zero, for instance. 
    
2. After reading the array and data from a disk, call **ScRelocProps** on the array with the  _pvBaseOld_ parameter equal to the same standard value used in Step 1. The array and data must be read into a buffer created with a single allocation. 
    
3. The  _pcb_ parameter to **ScRelocProps** is optional. 
    
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[ScCountProps](sccountprops.md)
  
[ScDupPropset](scduppropset.md)
  
[ScRelocNotifications](screlocnotifications.md)

