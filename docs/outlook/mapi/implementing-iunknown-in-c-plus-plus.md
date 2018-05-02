---
title: "Implementing IUnknown in C++"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 68519f6c-fba8-47f5-9401-316e276f770e
description: "Last modified: July 23, 2011"
 
 
---

# Implementing IUnknown in C++

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Implementing the [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx), [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28v=VS.85%29.aspx), and [IUnknown::Release](http://msdn.microsoft.com/en-us/library/ms682317%28v=VS.85%29.aspx) methods of the [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx) interface in C++ is fairly simple. After some standard validation of the parameters that are passed in, an implementation of **QueryInterface** checks the identifier of the requested interface against the list of supported interfaces. If the requested identifier is among those supported, **AddRef** is called and the **this** pointer is returned. If the requested identifier is not on the supported list, the output pointer is set to NULL and the MAPI_E_INTERFACE_NOT_SUPPORTED value is returned. 
  
The following code example shows how you can implement **QueryInterface** in C++ for a status object, an object that is a subclass of the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface. **IMAPIStatus** inherits from **IUnknown** through [IMAPIProp : IUnknown](imapipropiunknown.md). Therefore, if a caller asks for any of these interfaces, the **this** pointer can be returned because the interfaces are related through inheritance. 
  
```
HRESULT CMyMAPIObject::QueryInterface (REFIID   riid,
                                       LPVOID * ppvObj)
{
    // Always set out parameter to NULL, validating it first.
    if (!ppvObj)
        return E_INVALIDARG;
    *ppvObj = NULL;
    if (riid == IID_IUnknown || riid == IID_IMAPIProp ||
        riid == IID_IMAPIStatus)
    {
        // Increment the reference count and return the pointer.
        *ppvObj = (LPVOID)this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

```

The following code example shows how to implement the **AddRef** and **Release** methods for the  `CMyMAPIObject` object. Because implementing **AddRef** and **Release** is straightforward, many service providers choose to implement them inline. The calls to the Win32 functions **InterlockedIncrement** and **InterlockedDecrement** ensure thread safety. The memory for the object is freed by the destructor, which is called when the **Release** method deletes the object. 
  
```
ULONG CMyMAPIObject::AddRef()
{
    InterlockedIncrement(m_cRef);
    return m_cRef;
}
ULONG CMyMAPIObject::Release()
{
    // Decrement the object's internal counter.
    ULONG ulRefCount = InterlockedDecrement(m_cRef);
    if (0 == m_cRef)
    {
        delete this;
    }
    return ulRefCount;
}
 
```

## See also

#### Concepts

[Implementing MAPI Objects](implementing-mapi-objects.md)
  
[Implementing the IUnknown Interface](implementing-the-iunknown-interface.md)

