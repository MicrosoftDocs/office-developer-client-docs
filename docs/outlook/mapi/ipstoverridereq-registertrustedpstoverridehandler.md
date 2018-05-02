---
title: "IPSTOVERRIDEREQRegisterTrustedPSTOverrideHandler"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPSTOVERRIDEREQ.RegisterTrustedPSTOverrideHandler
api_type:
- COM
ms.assetid: 4a73c77c-7e32-4302-bffe-a1ea13574731
description: "Last modified: February 24, 2013"
---

# IPSTOVERRIDEREQ::RegisterTrustedPSTOverrideHandler

 **Last modified:** February 24, 2013 
  
 * **Applies to:** Outlook * 
  
Initiates the unlocking procedure for a Personal Folders (.pst) file.
  
```
HRESULT RegisterTrustedPSTOverrideHandler (
  LPCWSTR pwzDllPath, 
  LPVOID pvClientData
); 

```

## Parameters

 _pwzDllPath_
  
> [in] A pointer to the path of a third-party dynamic-link library (DLL).
    
 _pvClientData_
  
> [in] A pointer to client data, which will be passed by the PST provider into subsequent calls to the DLL's HrTrustedPSTOverrideHandlerCallback function. This client data may be used by the DLL to assist in verifying whether the PST should be unlocked.
    
## Return value

S_OK
  
> The function call was successful.
    
## Remarks

The DLL specified by the wzDllPath parameter must be signed using a digital certificate. The DLL must also export a function with the following signature.
  
```
extern "C" HRESULT __cdecl HrTrustedPSTOverrideHandlerCallback(IMsgStore *pmstore, IUnknown *pOverride, LPVOID pvClientData)
```

This function will be called with a pointer to the IMsgStore object for the PST, a pointer to an IUnknown object that implements the IPSTOVERRIDE1 interface, and a pointer to the data originally supplied through pvClientData.
  
For more information see [How to implement a PST override handler to bypass the PSTDisableGrow policy in Outlook 2007](http://support.microsoft.com/kb/956070).
  
## See also

#### Reference

[IPSTOVERRIDE1 : IUnknown](ipstoverride1iunknown.md)
  
[IPSTOVERRIDEREQ : IUnknown](ipstoverridereqiunknown.md)

