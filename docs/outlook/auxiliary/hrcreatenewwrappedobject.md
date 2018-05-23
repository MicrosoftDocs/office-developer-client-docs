---
title: "HrCreateNewWrappedObject"
 
 
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 780ade1c-88d0-04d2-ba7e-251c19c43438
description: "Creates an object that a client can access in a preferred character format."
---

# HrCreateNewWrappedObject

Creates an object that a client can access in a preferred character format.
  
## Quick info

|||
|:-----|:-----|
|Exported by:  <br/> |msmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
   
```
HRESULT HrCreateNewWrappedObject( 
    LPVOID        pvUnwrapped, 
    ULONG         ulUnwrappedFlags, 
    ULONG         ulWrappedFlags, 
    const IID     *pIID, 
    const ULONG   *pulReserved, 
    BOOL          fCheckWrap, 
    LPVOID       *ppvWrapped 
);

```

## Parameters

 _pvUnwrapped_
  
> [in] The initial unwrapped Outlook object. Must implement one of the following interfaces:
    
    - [IMailUser : IMAPIProp](http://msdn.microsoft.com/library/74c25870-62d9-484a-9a99-4dc35c52479e%28Office.15%29.aspx), [IMAPIFolder : IMAPIContainer](http://msdn.microsoft.com/library/bc2e8d17-7687-43c2-8f01-b677703f7288%28Office.15%29.aspx), [IMessage : IMAPIProp](http://msdn.microsoft.com/library/7e244d40-595e-432c-aa8c-f9f62ca3c138%28Office.15%29.aspx), [IMsgStore : IMAPIProp](http://msdn.microsoft.com/library/20090114-b183-4767-8971-a304a9aa47e6%28Office.15%29.aspx), [IMSLogon : IUnknown](http://msdn.microsoft.com/library/d87093dc-f705-465f-ab3c-944ca0cd3e54%28Office.15%29.aspx), or [IOSTX](http://msdn.microsoft.com/library/f374d8d9-be8e-2489-d5fe-8a92e0ecfc6f%28Office.15%29.aspx).
    
 _ulUnwrappedFlags_
  
> [in] Flags that characterize the unwrapped initial object. Must be one or more of the following values:
    
    - DDLWRAP_FLAG_ANSI—Unwrapped object is ANSI.
    
    - DDLWRAP_FLAG_UNICODE—Unwrapped object is UNICODE.
    
 _ulWrappedFlags_
  
>  [in] Flags for the preferred character format. Must be one or more of the following values: 
    
    - DDLWRAP_FLAG_ANSI—Wrapped object will be exposed as ANSI.
    
    - DDLWRAP_FLAG_UNICODE—Wrapped object will be exposed as UNICODE.
    
 _pIID_
  
>  [in] The identifier of the interface supported by the unwrapped object; set it to NULL if this is unknown. 
    
 _pulReserved_
  
>  [in] This parameter is not used. It must be NULL. 
    
 _fCheckWrap_
  
>  [in] Set this parameter to **true** if  _pvUnwrapped_ should be checked for its format before wrapping; set it to **false** if the object should be wrapped without checking. 
    
 _ppvWrapped_
  
>  [out] A pointer to the requested object, wrapped in the requested character format. 
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

Passing in a wrapped object with  _fCheckWrap_ set to **true** will result in an unwrapped object. Regardless of whether or not the returned object is wrapped, the client is responsible for releasing the reference on the returned object. 
  
When using **GetProcAddress** to look for the address of this function in msmapi32.dll, specify **HrCreateNewWrappedObject@28** as the procedure name. 
  
## See also



[About the Data Degradation Layer API](about-the-data-degradation-layer-api.md)
  
[Constants (Data degradation layer API)](constants-data-degradation-layer-api.md)

