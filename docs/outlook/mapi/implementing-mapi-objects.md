---
title: "Implementing MAPI Objects"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b1ee2533-8077-4976-846b-d42d148bf8c6
description: "Last modified: July 23, 2011"
 
 
---

# Implementing MAPI Objects

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
MAPI objects can be implemented by using C++ classes or C data structures, depending on the language and the API set a client or service provider is using. Service providers can be written in C or C++ with the MAPI service provider interface; client applications can also use C or C++. If possible, clients and service providers that use the object-oriented programming interface should use C++. 
  
C++ is the preferred choice because MAPI is an object-oriented technology, and C++ lends itself more readily to object-oriented development. The resulting code is simpler and more straightforward, making it easier to maintain. The MAPI documentation is written primarily for C++ developers; all of the syntax descriptions for the MAPI interface methods in this Reference are in C++.
  
Developers can use Microsoft Visual Studio and third-party development tools to develop solutions that call MAPI. Note that developers should use C or unmanaged C++, but not managed C++ to write MAPI solutions.
  
When a MAPI object is implemented, a client or service provider creates code for all of the interface methods, code for any private methods that are specific to the implementation, and code to support private data members for maintaining state information. The code for the interface methods must follow the specifications published by MAPI that document expected behavior. 
  
There are many macros in the Mapidefs.h header file and OLE header files that clients and service providers in either language can use to help them with their definitions of MAPI objects. For example, there is a macro to define the methods of each of the MAPI interfaces. The macro to define the methods of the [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx) interface appears in Mapidefs.h as follows: 
  
```
#define MAPI_IUNKNOWN_METHODS(IPURE)          \
    MAPIMETHOD(QueryInterface)                \
        (THIS_ REFIID riid, LPVOID FAR * ppvObj) IPURE;    \
    MAPIMETHOD_(ULONG,AddRef)  (THIS) IPURE;               \
    MAPIMETHOD_(ULONG,Release) (THIS) IPURE;   \
 
```

## See also

#### Concepts

[MAPI Object and Interface Overview](mapi-object-and-interface-overview.md)

