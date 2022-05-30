---
title: "HrAddColumns"
description: This article describes the HrAddColumns function and provides syntax, parameters, return value, and additional remarks.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 8c980257-9372-4478-b635-bd91d0a66af9
---

# HrAddColumns

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Adds or moves columns to the beginning of an existing table.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers. |
   
```cpp
HRESULT HrAddColumns(
  LPMAPITABLE lptbl,
  LPSPropTagArray lpproptagColumnsNew,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPFREEBUFFER lpFreeBuffer
);
```

## Parameters

 _lptbl_
  
> [in] Pointer to the MAPI table affected.
    
 _lpproptagColumnsNew_
  
> [in] Pointer to an **SPropTagArray** structure that contains an array of property tags for the properties to be added or moved to the beginning of the table. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the **MAPIAllocateBuffer** function. Used to allocate memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the **MAPIFreeBuffer** function. Used to free memory. 
    
## Return value

 **S_OK**
  
> The call succeeded and the specified columns were moved or added.
    
## Remarks

The **HrAddColumns** function is equivalent to using **HrAddColumnsEx** with  _lpfnFilterColumns_ set to NULL. 
  
## See also



[HrAddColumnsEx](hraddcolumnsex.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropTagArray](sproptagarray.md)

