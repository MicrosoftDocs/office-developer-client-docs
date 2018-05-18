---
title: "IMAPISupportIStorageFromStream"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.IStorageFromStream
api_type:
- COM
ms.assetid: da9e8fdc-dfc5-4ecc-9f9b-b76921b92d7c
description: "Last modified: July 23, 2011"
---

# IMAPISupport::IStorageFromStream

  
  
**Applies to**: Outlook 
  
Implements a storage object to access a stream.
  
```cpp
HRESULT IStorageFromStream(
  LPUNKNOWN lpUnkIn,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPSTORAGE FAR * lppStorageOut
);
```

## Parameters

 _lpUnkIn_
  
> [in] A pointer to a stream object.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the stream pointed to by  _lpUnkIn_. Any of the following values are valid: IID_IStream, IID_ILockBytes, or **null**, which indicates that the [IStream](http://msdn.microsoft.com/en-us/library/aa380034%28VS.85%29.aspx) interface should be used to access the stream. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the storage object is to be created relative to the stream object. By default, the storage is created with read-only access and the stream starts at position zero in the storage. The following flags can be set:
    
STGSTRM_CREATE 
  
> A new storage object should be created for the stream object.
    
STGSTRM_CURRENT 
  
> The storage object should start at the current position of the stream.
    
STGSTRM_MODIFY 
  
> The caller should have read/write permission to the returned storage object.
    
STGSTRM_RESET 
  
> The storage object should start at position zero.
    
 _lppStorageOut_
  
> [out] A pointer to a pointer to the storage object.
    
## Return value

S_OK 
  
> The storage object was successfully created.
    
## Remarks

The **IMAPISupport::IStorageFromStream** method is implemented for all service provider support objects. Service providers call **IStorageFromStream** to create a storage object to use for opening particular properties. Service providers that have their own implementation of the [IStorage](http://msdn.microsoft.com/en-us/library/aa380015%28VS.85%29.aspx) interface do not need to call **IStorageFromStream**. 
  
The storage object created by **IStorageFromStream** calls the stream's [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28v=VS.85%29.aspx) method to increment its reference count and then decrements the count when the storage is released. 
  
## Notes to callers

When the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method of one of your objects is called to open a property with the **IStorage** interface, perform the following tasks: 
  
1. Open a stream object with read/write permission for the property.
    
2. Internally mark the property stream as a storage object.
    
3. Call **IStorageFromStream** to generate a storage object. 
    
4. Return a pointer to this storage object.
    
If you implement additional interfaces that use the storage object, create an object that wraps the storage object and implement a higher level [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx) method. 
  
Do not allow a property to be opened with the **IStream** interface if it was created with **IStorage**. Conversely, do not allow a property to be opened with the **IStorage** interface if it was created with **IStream**. 
  
With one exception, it is acceptable to use the **IStreamDocfile** interface to stream a storage object from one container to another, but the IID_IStreamDocfile interface identifier must be passed in the **OpenProperty** method's  _lpInterface_ parameter. 
  
## See also



[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

