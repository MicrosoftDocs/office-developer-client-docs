---
title: "Managing Memory in MAPI"
description: MAPI provides both functions and macros that your client or service provider can use to manage memory in a consistent way.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 9eee6925-ab91-413e-8907-c747ab4a4bb5
---

# Managing Memory in MAPI

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Knowing how and when to allocate and free memory is an important part of programming with MAPI. MAPI provides both functions and macros that your client or service provider can use to manage memory in a consistent way. The three functions are as follows:
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
When clients and service providers use these functions, the issue of who "owns" — that is, knows how to release — a particular block of memory is eliminated. A client calling a service provider method need not pass a buffer large enough to hold a return value of any size. The service provider can simply allocate the appropriate amount of memory using **MAPIAllocateBuffer** and, if necessary, **MAPIAllocateMore**, and the client can later release it at will using **MAPIFreeBuffer**, independent of the service provider. 
  
The memory macros are used to allocate structures or arrays of structures of a specific size. Clients and service providers should use these macros rather than allocate the memory manually. For example, if a client needs to perform name resolution processing on a recipient list with three entries, the **SizedADRLIST** macro can be used to create an **ADRLIST** structure to pass to **IAddrBook::ResolveName** with the correct number of **ADRENTRY** members. All of the memory macros are defined in the MAPIDEFS.H header file. These macros are: 
  
|Macro |Macro |
|:-----|:-----|
|[SizedADRLIST](sizedadrlist.md) <br/> |[SizedDtblPage](sizeddtblpage.md) <br/> |
|[SizedDtblButton](sizeddtblbutton.md) <br/> |[SizedENTRYID](sizedentryid.md) <br/> |
|[SizedDtblCheckBox](sizeddtblcheckbox.md) <br/> |[SizedSPropProblemArray](sizedspropproblemarray.md) <br/> |
|[SizedDtblComboBox](sizeddtblcombobox.md) <br/> |[SizedSPropTagArray](sizedsproptagarray.md) <br/> |
|[SizedDtblEdit](sizeddtbledit.md) <br/> |[SizedSRowSet](sizedsrowset.md) <br/> |
|[SizedDtblGroupBox](sizeddtblgroupbox.md) <br/> |[SizedSSortOrderSet](sizedssortorderset.md) <br/> |
|[SizedDtblLabel](sizeddtbllabel.md) <br/> | <br/> |
   
MAPI also supports the use of the COM interface [IMalloc](https://msdn.microsoft.com/library/ms678425%28VS.85%29.aspx) for memory management. Service providers are given an **IMalloc** interface pointer by MAPI at initialization time and can also retrieve one through the [MAPIGetDefaultMalloc](mapigetdefaultmalloc.md) function. The main advantage to using the **IMalloc** methods for managing memory over the MAPI functions is that with the COM methods it is possible to reallocate an existing buffer. The MAPI memory functions do not support reallocation. 
  

