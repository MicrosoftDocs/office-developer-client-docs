---
title: "Allocating and Freeing Memory in MAPI"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e238f6bc-e9f6-4ea4-a2e4-ff5da2a04bd5
description: "Last modified: March 09, 2015"
 
 
---

# Allocating and Freeing Memory in MAPI

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
In addition to specifying how to allocate and free memory, MAPI defines a model for knowing when memory passed between public interface method and API function calls should be freed. The model applies only to memory allocated for parameters that are not pointers to interfaces, such as strings and pointers to structures. Interface pointers use the reference counting mechanism implemented through **IUnknown**. When allocating and freeing non-MAPI related memory internally within a client application or service provider, use whatever mechanism makes sense. 
  
The model defines parameters as one of three types. They can be input parameters, set by the caller with information to be used by the called function or method, output parameters, set by the called function or method and returned to the caller, or input-output parameters, a combination of the two types. Output parameters are frequently pointers to data or pointers to pointers to data. Although the called function is responsible for allocating the data for output parameters, the caller allocates the memory for the pointer. 
  
The rules for allocating and releasing memory for these types of parameters are explained in the following table.
  
|**Type**|**Memory allocation**|**Memory release**|
|:-----|:-----|:-----|
|Input  <br/> |Caller is responsible and can use any mechanism.  <br/> |Caller is responsible and can use any mechanism.  <br/> |
|Output  <br/> |Called function is responsible and must use **MAPIAllocateBuffer**. For more information, see [MAPIAllocateBuffer](mapiallocatebuffer.md).  <br/> |Caller is responsible and must use **MAPIFreeBuffer**. For more information, see [MAPIFreeBuffer](mapifreebuffer.md).  <br/> |
|Input-output  <br/> |Caller is responsible for the initial allocation and called function can reallocate if necessary using **MAPIAllocateBuffer**.  <br/> |Called function is responsible for initial freeing if reallocation is necessary. Caller must free the final return value.  <br/> |
   
During failure conditions, implementers of interface methods need to pay attention to output and input-output parameters because the caller generally has no way to clean them up. If an error is returned, then each output or input-output parameter must either be left at the value initialized by the caller or set to a value that can be cleaned up without any action on the part of the caller. For example, an output pointer-parameter of  `void ** ppv` must be left as it was on input or can be set to NULL (  `*ppv = NULL`).
  

