---
title: "CreateIProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CreateIProp
api_type:
- COM
ms.assetid: 9bf68814-2564-433d-b762-3d2c83ca3c60
description: "Last modified: March 09, 2015"
---

# CreateIProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a property data object, that is, an [IPropData](ipropdataimapiprop.md) object. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE CreateIProp(
  LPCIID lpInterface,
  ALLOCATEBUFFER FAR * lpAllocateBuffer,
  ALLOCATEMORE FAR * lpAllocateMore,
  FREEBUFFER FAR * lpFreeBuffer,
  LPVOID lpvReserved,
  LPPROPDATA FAR * lppPropData
);
```

## Parameters

 _lpInterface_
  
> [in] Pointer to an interface identifier (IID) for the property data object. The valid interface identifier is IID_IMAPIPropData. Passing NULL in the _lpInterface_ parameter also causes the property data object returned in the _lppPropData_ parameter to be cast to the standard interface for a property data object. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory. 
    
 _lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used to allocate additional memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory. 
    
 _lpvReserved_
  
> [in] Reserved; must be zero. 
    
 _lppPropData_
  
> [out] Pointer to a pointer to the returned property data object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_INTERFACE_NOT_SUPPORTED 
  
> The requested interface is not supported for this object.
    
## Remarks

The  _lpAllocateBuffer_,  _lpAllocateMore_, and  _lpFreeBuffer_ input parameters point to the [MAPIAllocateBuffer](mapiallocatebuffer.md), [MAPIAllocateMore](mapiallocatemore.md), and [MAPIFreeBuffer](mapifreebuffer.md) functions, respectively. A client application calling **CreateIProp** passes in pointers to the MAPI functions just named; a service provider passes the pointers to these functions it received in its initialization call or retrieved with a call to the [IMAPISupport::GetMemAllocRoutines](imapisupport-getmemallocroutines.md) method. 
  

