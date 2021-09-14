---
title: "Component Object Model and MAPI"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: cca4c70d-b73a-4834-80b5-9cb5889f63cc
description: "Last modified: March 09, 2015"
 
 
---

# Component Object Model and MAPI

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The Windows SDK documentation includes a comprehensive discussion of the rules for implementing objects that conform to the Component Object Model (COM). These rules address how to do the following:
  
- Design interfaces and objects.
    
- Implement the [IUnknown](https://msdn.microsoft.com/library/ms680509%28VS.85%29.aspx) interface. 
    
- Manage memory.
    
- Handle reference counting.
    
- Implement apartment-threaded objects.
    
Although all MAPI objects are considered COM-based because they implement interfaces that inherit from [IUnknown](https://msdn.microsoft.com/library/ms680509%28VS.85%29.aspx), MAPI deviates in some situations from the standard COM rules. This deviation allows developers more flexibility in their implementations. For example, a MAPI interface, like any COM interface, describes a contract between implementer and caller. Once the interface is created and published, its definition cannot and does not change. MAPI does not deviate from this description, but it relaxes the description somewhat. Implementers can choose to not implement particular methods, returning one of the following error values to the caller: 
  
- MAPI_E_NO_SUPPORT
    
- MAPI_E_TOO_COMPLEX
    
- MAPI_E_BAD_CHARWIDTH
    
- MAPI_E_TYPE_NO_SUPPORT
    
The other deviations from the standard COM rules are described in the following table.
  
|**COM programming rule**|**MAPI variation**|
|:-----|:-----|
|All string parameters in interface methods should be Unicode.  <br/> |MAPI interfaces are defined to permit either Unicode or ANSI string parameters. Many methods that have a string parameter also have a **ulFlags** parameter; the width of a string parameter is indicated by the value of the MAPI_UNICODE flag in **ulFlags**. Some MAPI interfaces do not support Unicode and return MAPI_E_BAD_CHARWIDTH when the MAPI_UNICODE flag is set.  <br/> |
|All interface methods should have a return type of HRESULT.  <br/> |MAPI has at least one method that returns a non-HRESULT value: [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md).  <br/> |
|Callers and implementers should allocate and free memory for interface parameters by using the standard COM task allocators.  <br/> |All MAPI methods use the linked allocators [MAPIAllocateBuffer](mapiallocatebuffer.md), [MAPIAllocateMore](mapiallocatemore.md), and [MAPIFreeBuffer](mapifreebuffer.md) to manage memory for interface parameters. All MAPI implementations of interfaces defined by OLE, such as [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx), use the standard COM task allocators.  <br/> |
|All out pointer parameters must explicitly be set to NULL when a method fails.  <br/> |MAPI interfaces require that out pointer parameters either be set to NULL or remain unchanged when a method fails. All MAPI implementations of interfaces defined by OLE explicitly set out parameters to NULL on failure.  <br/> |
|Implement aggregatable objects whenever possible.  <br/> |MAPI interfaces are not aggregatable.  <br/> |
   
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)


[MAPI Object and Interface Overview](mapi-object-and-interface-overview.md)

