---
title: "Linking to the MAPI DLLs"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 19fd4678-21d3-47a6-a439-1d4959cac407
description: "Last modified: July 23, 2011"
 
 
---

# Linking to the MAPI DLLs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI clients can link to the MAPI DLLs implicitly, or explicitly by using the Windows functions **LoadLibrary** and **GetProcAddress**. For information on explicitly linking MAPI DLLs, see [Link to MAPI Functions](how-to-link-to-mapi-functions.md).
  
MAPI provides type definition statements in the MAPIX.H header file for each of the following functions:
  
[MAPILogonEx](mapilogonex.md)
  
[MAPIUninitialize](mapiuninitialize.md)
  
[MAPIInitialize](mapiinitialize.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[MAPIAdminProfiles](mapiadminprofiles.md)
  
Use these type definitions to correctly call the corresponding entry points if you link explicitly to the MAPI DLLs.
  
Service providers can contain non-MAPI functionality — features that are completely unrelated to MAPI — in their DLL. If you need to use these features, call **LoadLibrary** before using the DLL and **FreeLibrary** to remove the DLL from memory after its use. Because MAPI is unaware of non-MAPI uses of a service provider DLL, there is no guarantee that the DLL will be available when needed. MAPI releases a service provider DLL when there are no longer any clients with active sessions that require its services. 
  

