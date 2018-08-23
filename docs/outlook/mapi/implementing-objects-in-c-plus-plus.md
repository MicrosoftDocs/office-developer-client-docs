---
title: "Implementing objects in C++"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d1a050ff-3cf9-4bf7-812d-b7c1b31056e7
description: "Last modified: July 23, 2011"
---

# Implementing objects in C++

**Applies to**: Outlook 2013 | Outlook 2016 
  
C++ clients and service providers define MAPI objects by creating classes that inherit from the interfaces they are implementing. Each of the interface methods is public, as are the constructor and destructor for the class. If the class has additional methods, they can be public or private, depending on the implementation. All data members are private. 
  
The following example code shows how to define a C++ status object. The  `CMyMAPIObject` class inherits from the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface. Many of the macros used in this example are defined in the OLE header file Compobj.h. The first members of the class are the methods of the base interface, followed by the methods of the inherited interfaces in order of inheritance. Following the interface definitions are any additional methods, the constructor and destructor, and the data members. 
  
```cpp
class  CMyMAPIObject : public IMAPIStatus
{
public:
// Methods of IUnknown.
    STDMETHODIMP QueryInterface (REFIID riid, LPVOID * ppvObj);
    STDMETHODIMP_(ULONG) AddRef ();
    STDMETHODIMP_(ULONG) Release ();
    MAPI_IMAPIPROP_METHODS(IMPL);
    MAPI_IMAPISTATUS_METHODS(IMPL);
// Other methods specific to CMyMAPIObject.
    BOOL WINAPI Method1 ();
    void WINAPI Method2 ();
// Constructors and destructors.
public :
    CMyMAPIObject () {};
    ~CMyMAPIObject () {};
// Data members specific to CMyMAPIObject.
private :
    ULONG               m_cRef;
    CAnotherObj *       m_pObj;
};
 
```

To use an instance of the  `CMyMAPIObject` class, C++ clients or service providers make a call to one of its methods as follows: 
  
```cpp
lpMyObj->ValidateState(ulUIParam, ulFlags);

```

## See also

- [Implementing MAPI Objects](implementing-mapi-objects.md)

