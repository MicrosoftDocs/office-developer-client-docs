---
title: "MAPI Object and Interface Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: d4ece3af-cb54-4727-8072-0c055381ec11
 
 
---

# MAPI Object and Interface Overview

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A MAPI object is a C++ object class or C data structure inherited from one or more MAPI interfaces, or collections of related functions. These collections of related functions are known to C++ developers as pure virtual functions. For a pure virtual function, MAPI supplies only the function prototype, not an implementation. It is expected that a client application, a service provider, or MAPI will provide this implementation by creating an object class that inherits from the interface and conforms to the function descriptions of the Messaging API. A MAPI interface can be instantiated only through an inherited class.
  
There are many different MAPI objects, each object inheriting from an interface that is ultimately inherited from the [IUnknown](https://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx) interface. **IUnknown** is the OLE Component Object Model (COM) base interface. It provides MAPI objects with a standard mechanism for communication and control. COM dictates how object implementers handle issues such as memory management, parameter management, and multithreading. By conforming to this model, an object implementer adheres to a contract as specified by the interfaces included in the object. 
  
Many MAPI interfaces are inherited directly from **IUnknown**, while others are inherited indirectly through one of two other base interfaces: [IMAPIProp : IUnknown](imapipropiunknown.md) for property management and [IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md) for folder and address book access. Base interfaces are never implemented as separate, standalone objects; they are always implemented as part of other objects, objects that implement derived interfaces. 
  
MAPI defines many types of objects, each implemented by one or more MAPI components. Objects implemented by clients are used by MAPI, by service providers, and by custom form components. Objects implemented by service providers are typically used by MAPI and by clients. Objects implemented by form library providers and form servers are used by other form components and by clients. 
  
## See also



[IMAPIProp : IUnknown](imapipropiunknown.md)
  
[IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)


[MAPI Concepts](mapi-concepts.md)

