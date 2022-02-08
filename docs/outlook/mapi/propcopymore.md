---
title: "PropCopyMore"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PropCopyMore
api_type:
- HeaderDef
ms.assetid: 133d47cf-3592-44f3-8cdd-be402d160ee4
description: "Last modified: March 09, 2015"
---

# PropCopyMore

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies a single property value from a source location to a destination location. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE PropCopyMore(
  LPSPropValue lpSPropValueDest,
  LPSPropValue lpSPropValueSrc,
  ALLOCATEMORE * lpfAllocMore,
  LPVOID lpvObject
);
```

## Parameters

 _lpSPropValueDest_
  
> [out] Pointer to the location to which this function writes an [SPropValue](spropvalue.md) structure defining the copied property value. 
    
 _lpSPropValueSrc_
  
> [in] Pointer to the [SPropValue](spropvalue.md) structure that contains the property value to be copied. 
    
 _lpfAllocMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function to be used to allocate additional memory if the destination location is not large enough to hold the property to be copied. 
    
 _lpvObject_
  
> [in] Pointer to an object for which **MAPIAllocateMore** will allocate space if necessary. 
    
## Return value

S_OK
  
> The single property value was copied successfully.
    
MAPI_E_NO_SUPPORT
  
> An unknown property type was encountered.
    
## Remarks

A client application or service provider can use the **PropCopyMore** function to copy a property out of a table that is about to be freed in order to use it elsewhere. 
  
 **PropCopyMore** does not need to allocate memory unless the property value copied is of a type, such as PT_STRING8, that does not fit in an [SPropValue](spropvalue.md) structure. For these large properties, the function allocates memory using the [MAPIAllocateMore](mapiallocatemore.md) function to which a pointer is passed in the _lpfAllocMore_ parameter. 
  
Injudicious use of **PropCopyMore** fragments memory; consider using the [ScCopyProps](sccopyprops.md) function instead. 
  

