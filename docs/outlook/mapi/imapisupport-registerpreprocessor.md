---
title: "IMAPISupportRegisterPreprocessor"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.RegisterPreprocessor
api_type:
- COM
ms.assetid: 9b5659ab-2b49-41ab-92ce-ca343e35d670
description: "Last modified: July 23, 2011"
---

# IMAPISupport::RegisterPreprocessor

  
  
**Applies to**: Outlook 
  
Registers a transport provider's preprocessor function (a function that conforms to the [PreprocessMessage](preprocessmessage.md) prototype). 
  
```cpp
HRESULT RegisterPreprocessor(
LPMAPIUID lpMuid,
LPSTR lpszAdrType,
LPSTR lpszDLLName,
LPSTR lpszPreprocess,
LPSTR lpszRemovePreprocessInfo,
ULONG ulFlags
);
```

## Parameters

 _lpMuid_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the identifier that the preprocessor function handles. The  _lpMuid_ parameter can be NULL. 
    
 _lpszAdrType_
  
> [in] A pointer to the address type for the messages the function operates on, such as FAX, SMTP, or X500. The  _lpszAdrType_ parameter can be NULL. 
    
 _lpszDLLName_
  
> [in] A pointer to the name of the dynamic-link library (DLL) that contains the entry point for the preprocessor function.
    
 _lpszPreprocess_
  
> [in] A pointer to the name of the preprocessor function. The  _lpszPreprocess_ parameter can be NULL. 
    
 _lpszRemovePreprocessInfo_
  
> [in] A pointer to the name of the function that removes preprocessor information (a function that conforms to the [RemovePreprocessInfo](removepreprocessinfo.md) prototype). The  _lpszRemovePreprocessInfo_ parameter can be NULL. 
    
 _ulFlags_
  
> Reserved; must be zero.
    
## Return value

S_OK 
  
> The preprocessor function was successfully registered.
    
## Remarks

The **IMAPISupport::RegisterPreprocessor** method is implemented for transport provider support objects only. Transport providers call **RegisterPreprocessor** to register a preprocessor function (a function that conforms to the [PreprocessMessage](preprocessmessage.md) prototype). A preprocessor function must be registered before the MAPI spooler can call it. 
  
The  _lpszPreprocess_,  _lpszRemovePreprocessInfo_, and  _lpszDLLName_ parameters should all point to strings that can be used in conjunction with calls to the Win32 **GetProcAddress** function, allowing the preprocessor's DLL entry point to be called correctly. 
  
## Notes to callers

Calls to preprocessors are specific to transport provider order. This means that if another transport provider ahead of your provider is able to handle a message, your preprocessor function will not be called for that message. Your preprocessor function will be called only for messages that you will handle.
  
You can write preprocessor functions to handle either a specific identifier stored in a [MAPIUID](mapiuid.md) structure or a type of address. If you specify both a **MAPIUID** structure in the  _lpMuid_ parameter and an address type in the  _lpszAdrType_ parameter, your function will be called for message recipients that match either the **MAPIUID** or the address type. If  _lpMuid_ is NULL and  _lpszAdrType_ is non-NULL, your function will be called only for recipients that have an address that matches the type pointed to by  _lpszAdrType_. If  _lpMuid_ is non-NULL and  _lpszAdrType_ is NULL, your function will be called for recipients that match **MAPIUID**, regardless of their address type. If both are NULL, your function is called for all recipients of the message.
  
## See also



[MAPIUID](mapiuid.md)
  
[PreprocessMessage](preprocessmessage.md)
  
[RemovePreprocessInfo](removepreprocessinfo.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

