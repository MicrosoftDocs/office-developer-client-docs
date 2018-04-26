---
title: "xlAddInManagerInfo/xlAddInManagerInfo12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- xlAddInManagerInfo
keywords:
- xladdinmanagerinfo function [excel 2007]
 
localization_priority: Normal
ms.assetid: 63a73cd2-6479-4233-ad68-93379f940717
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlAddInManagerInfo/xlAddInManagerInfo12

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Called by Microsoft Excel when the Add-in Manager is invoked for the first time in an Excel session. This function is used to provide the Add-In Manager with information about your add-in.
  
Excel 2007 and later versions call **xlAddInManagerInfo12** in preference to **xlAddInManagerInfo** if exported by the XLL. The **xlAddInManagerInfo12** function should work in the same way as **xlAddInManagerInfo** to avoid version-specific differences in the behavior of the XLL. Excel expects **xlAddInManagerInfo12** to return an **XLOPER12** data type, whereas **xlAddInManagerInfo** should return an **XLOPER**.
  
The **xlAddInManagerInfo12** function is not called by versions of Excel earlier than Excel 2007, as these do not support the **XLOPER12**.
  
Excel does not require an XLL to implement and export either of these functions.
  
```cs
LPXLOPER WINAPI xlAddInManagerInfo(LPXLOPER pxAction);
LPXLOPER12 WINAPI xlAddInManagerInfo12(LPXLOPER12 pxAction);
```

## Parameters

 _pxAction:_ A pointer to a numeric **XLOPER/XLOPER12** ( **xltypeInt** or **xltypeNum**).
  
The information that Excel is asking for.
  
## Property Value/Return Value

If  _pxAction_ is, or can be coerced to, the number 1, then your implementation of this function should return a string containing some information about the add-in, typically its name and perhaps a version number. Otherwise it should return #VALUE!. 
  
If you do not return a string, Excel tries to convert the returned value to a string.
  
## Remarks

If the returned string points to dynamically allocated buffer, you must make sure that this buffer is eventually freed. If the string was allocated by Excel, you do this by setting **xlbitXLFree**. If the string was allocated by the DLL, you do this by setting **xlbitDLLFree**, and you must also implement in [xlAutoFree](xlautofree-xlautofree12.md) (if you are returning an **XLOPER**) or **xlAutoFree12** (if you are returning an **XLOPER12**).
  
## Example

 `\SAMPLES\GENERIC\GENERIC.C`
  
```cs
LPXLOPER12 WINAPI xlAddInManagerInfo12(LPXLOPER12 xAction)
{
    static XLOPER12 xInfo, xIntAction;
/*
** This code coerces the passed-in value to an integer. This is how the
** code determines what is being requested. If it receives a 1, it returns a
** string representing the long name. If it receives anything else, it
** returns a #VALUE! error.
*/
    Excel12f(xlCoerce, &amp;xIntAction, 2, xAction, TempInt12(xltypeInt));
    if(xIntAction.val.w == 1) 
    {
        xInfo.xltype = xltypeStr;
        xInfo.val.str = L"\026Example Standalone DLL";
    }
    else 
    {
        xInfo.xltype = xltypeErr;
        xInfo.val.err = xlerrValue;
    }
// Word of caution - returning static XLOPERs/XLOPER12s is not thread safe
// for UDFs declared as thread safe. Use alternate memory allocation mechanisms.
    return (LPXLOPER12)&amp;xInfo;
} 

```

## See also

#### Concepts

[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)

