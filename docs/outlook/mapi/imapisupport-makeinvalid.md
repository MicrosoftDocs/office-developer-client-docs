---
title: "IMAPISupportMakeInvalid"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.MakeInvalid
api_type:
- COM
ms.assetid: c630ecaf-b19c-4991-9779-e13cc492c755
description: "Last modified: July 23, 2011"
---

# IMAPISupport::MakeInvalid

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Marks an object as unusable.
  
```cpp
HRESULT MakeInvalid(
ULONG ulFlags,
LPVOID lpObject,
ULONG ulRefCount,
ULONG cMethods
);
```

## Parameters

 _ulFlags_
  
> Reserved; must be zero.
    
 _lpObject_
  
> [in] A pointer to the object to be invalidated. The object's interface must be derived from **IUnknown**.
    
 _ulRefCount_
  
> [in] The object's present reference count.
    
 _cMethods_
  
> [in] The count of methods in the object's vtable.
    
## Return value

S_OK 
  
> The object was successfully marked as unusable.
    
## Remarks

The **IMAPISupport::MakeInvalid** method is implemented for all support objects. The object to be invalidated must be derived from the **IUnknown** interface or from an interface derived from **IUnknown**.
  
 **MakeInvalid** marks an object as unusable by replacing the object's vtable with a stub vtable of similar size in which the **IUnknown::AddRef** and **IUnknown::Release** methods perform as expected. However, any other methods fail, returning the value MAPI_E_INVALID_OBJECT. 
  
## Notes to callers

Service providers and message services typically call **MakeInvalid** at shutdown time. However, **MakeInvalid** can be called at any time. For example, if a client releases an object without releasing some of its subobjects, you can call **MakeInvalid** immediately to release those subobjects. 
  
You must own the object that you attempt to invalidate. It must be at least 16 bytes long and have at least three methods in its vtable. 
  
You can call **MakeInvalid** and then perform any shutdown work, such as discarding associated data structures, that is usually done during the release of an object. Code to support the object need not be kept in memory, because MAPI frees the memory by calling [MAPIFreeBuffer](mapifreebuffer.md) and then releases the object. You can release resources, call **MakeInvalid**, and then ignore the invalidated object. 
  
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

