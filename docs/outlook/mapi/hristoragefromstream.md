---
title: "HrIStorageFromStream"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- HrIStorageFromStream
api_type:
- HeaderDef
ms.assetid: 1cdc95b8-a156-4600-9e20-caaa02680e87
description: "Last modified: March 09, 2015"
---

# HrIStorageFromStream

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Layers an **IStorage** interface onto an **IStream** object. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrIStorageFromStream(
  LPUNKNOWN lpUnkIn,
  PIID lpInterface,
  ULONG ulFlags,
  LPSTORAGE FAR * lppStorageOut
);
```

## Parameters

 _lpUnkIn_
  
> [in] Pointer to the **IUnknown** object implementing **IStream**. 
    
 _lpInterface_
  
> [in] Pointer to the interface identifier (IID) for the stream object. Any of the following values can be passed in the _lpInterface_ parameter: NULL, IID_IStream, or IID_ILockBytes. Passing NULL in  _lpInterface_ is the same as passing IID_IStream. 
    
 _ulFlags_
  
> [in] Bitmask of flags that controls how the storage object is to be created relative to the stream. The default setting is STGSTRM_RESET, which gives the storage object read-only access and starts it at position zero of the stream. The following flags can be set in any combination, except as noted:
    
STGSTRM_CREATE 
  
> Creates a new storage object for the stream object. This flag cannot be set if the STGSTRM_RESET flag is set. 
    
STGSTRM_CURRENT 
  
> Starts storage at the current position of the stream. This flag cannot be set if the STGSTRM_RESET flag is set. 
    
STGSTRM_MODIFY 
  
> Allows the calling service provider to write to the returned storage. This flag cannot be set if the STGSTRM_RESET flag is set. 
    
STGSTRM_RESET 
  
> Starts storage at position zero. This flag cannot be set if any other flag is set. 
    
 _lppStorageOut_
  
> [out] Pointer to a pointer to the returned **IStorage** object. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Message store providers support the **HrIStorageFromStream** function using the **IStorage** interface for attachments. Store providers must implement the **IStream** interface. **HrIStorageFromStream** provides the **IStorage** interface for the **IStream** object. It is possible to pass either an **ILockBytes** or an **IStream** interface in  _lpUnkIn_. 
  

