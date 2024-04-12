---
title: "Initializing the Transport Provider"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 977c18ce-ece5-4ad1-ac97-5a680846ab83
 
 
---

# Initializing the Transport Provider

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The transport-spooler interface defines calls the MAPI spooler makes to a transport provider. Transport providers implement these routines in a dynamic-link library (DLL). The first direct entry point into the DLL used by the MAPI spooler must be the transport provider initialization function [XPProviderInit](xpproviderinit.md).
  
MAPI uses the routine **GetProcAddress** to get the address of the service provider's initialization routine and then calls that routine. The name of the initialization routine is **XPProviderInit** for transport providers. It is different for other types of MAPI service providers so that one DLL can contain any combination of service provider types, but only one service provider of a particular type. However, one service provider of a given type can implement multiple services of its type. For example, one transport provider can implement message transport functionality to multiple message services. 
  
The mapispi.h header file has a type definition for the function prototype of the transport provider initialization function, and a predefined procedure name for it. By naming the initialization routines in your C and C++ files with the same names used by **GetProcAddress** and by using a straightforward export declaration in your DLL.DEF file, you automatically get type checking of the parameters on your initialization routine. See the sample transport provider source code for examples. For more information, see [Transport Provider Sample](transport-provider-sample.md).
  
If a service provider's initialization call succeeds but returns a service provider interface version number too small for MAPI to handle, MAPI immediately calls the **Release** method of the service provider object and proceeds as if the initialization call had failed with MAPI_E_VERSION. This way MAPI and the service provider jointly define the range of service provider interface version numbers they can handle, and if nothing matches then service provider loading fails with a MAPI_E_VERSION return value. 
  
The last step for the MAPI spooler in getting access to service provider resources is to log on to the transport provider. The MAPI spooler calls the [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) method of the [IXPProvider : IUnknown](ixpprovideriunknown.md) object returned from **XPProviderInit**. This is the call where credentials, if used, are checked and dialog boxes can be allowed.
  
If a process opens a second transport session on the same transport provider and MAPI session, the transport provider DLL should not create a second provider object. The first provider object should be used to log on to the second transport session. A transport provider should be programmed to support multiple transport sessions in a single provider object. A second provider object should only be created if different MAPI sessions are used in the same process.
  

