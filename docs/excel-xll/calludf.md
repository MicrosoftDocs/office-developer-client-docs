---
title: "CallUDF"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6421c9a2-07f7-4deb-aa43-c50d82cb0002
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# CallUDF

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Calls a user-defined function in a high-performance computing environment.
  
```
int CallUDF(int SessionId, WCHAR *XllName, WCHAR *UDFName, LPXLOPER12 pxAsyncHandle, int (*CallBackAddr)(), int ArgCount, LPXLOPER12 Parameter1, ...)
```

## Parameters

 _SessionId_
  
> The ID of the session in which to make the call.
    
 _XLLName_
  
> The name of the XLL that contains the user-defined function.
    
 _UDFName_
  
> The name of the user-defined function.
    
 _CallBackAddr_
  
> The function that the connector should call when the user-defined function is finished.
    
 _pxAsyncHandle_
  
> The asynchronous handle used by Excel and the connector to track the pending user-defined function call. The connector uses it later when the call is finished, when it calls back into Excel using the function pointer passed in the  _CallBackAddr_ argument. 
    
 _ArgCount_
  
> The number of arguments to pass to the user-defined function. The maximum value allowed is 255.
    
 _Parameter1_
  
> A value to pass to the user-defined function. Repeat this argument for each parameter indicated by  _ArgCount_.
    
## Return Value

 **xlHpcRetSuccess** if the UDF call is successfully initiated; **xlHpcRetInvalidSessionId** if the  _SessionId_ argument is invalid; **xlHpcRetCallFailed** on other failures, including time-out. If the call returns any error code (anything except **xlHpcRetSuccess**), then Excel considers the UDF call to have failed, invalidates the  _pxAsyncHandle_, and does not expect a callback to occur.
  
## Remarks

This function executes asynchronously.
  
## See also

#### Concepts

[Excel Cluster Connector Functions](excel-cluster-connector-functions.md)

