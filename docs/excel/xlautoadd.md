---
title: "xlAutoAdd"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlAutoAdd
keywords:
- xlautoadd function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: c69299af-a28a-44d9-be10-9c9fb92e21f2

---

# xlAutoAdd

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Added by Microsoft Excel whenever the user activates the XLL during an Excel session by using the Add-In Manager. This function is not called when Excel starts up and loads a pre-installed add-in.
  
This function can be used to display a custom dialog box that tells the user that the add-in has been activated, or to read from or write to the registry, or check licensing information, for example.
  
Excel does not require an XLL to implement and export this function.
  
```cs
int WINAPI xlAutoAdd(void);
```

## Parameters

This function takes no arguments.
  
## Property value/Return value

Your implementation of this function should return 1. (**int**).
  
## Remarks

Use this function if there is anything your XLL needs to do when it is added by the Add-In Manager.
  
## Example

See `\SAMPLES\EXAMPLE\EXAMPLE.C` and `\SAMPLES\GENERIC\GENERIC.C` for example implementations of this function. The following code is from `\SAMPLES\EXAMPLE\EXAMPLE.C`.
  
```cs
int WINAPI xlAutoAdd(void)
{
    XCHAR szBuf[255];
    wsprintfW((LPWSTR)szBuf, L"Thank you for adding Example.XLL\n"
            L"build date %hs, time %hs",__DATE__, __TIME__);
/* Display a dialog indicating that the XLL was successfully added */
    Excel12f(xlcAlert, 0, 2, TempStr12(szBuf), TempInt12(2));
    return 1;
}
```

## See also

[xlAutoRemove](xlautoremove.md)
[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)
