---
title: "xlAutoRemove"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlAutoRemove
keywords:
- xlautoremove function [excel 2007]
 
localization_priority: Normal
ms.assetid: fff0de4d-605d-49e6-a5be-a000410c09d8
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlAutoRemove

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Called by Microsoft Excel whenever the user deactivates the XLL during an Excel session by using the Add-In Manager. This function is not called when an Excel session closes, normally or abnormally, with the add-in installed.
  
This function can be used to display a custom dialog box telling the user that the add-in has been deactivated, or to read from or write to the registry, for example.
  
Excel does not require an XLL to implement and export this function. 
  
```cs
int WINAPI xlAutoRemove(void);
```

## Parameters

This function takes no arguments.
  
## Property Value/Return Value

Your implementation of this function must return 1 ( **int**).
  
## Remarks

Use this function if your XLL needs to complete any task when it is removed by the Add-In Manager.
  
## Example

See the files  `\SAMPLES\EXAMPLE\EXAMPLE.C` and  `\SAMPLES\GENERIC\GENERIC.C` for example implementations of this function. The following code is from  `\SAMPLES\EXAMPLE\EXAMPLE.C`.
  
```cs
int WINAPI xlAutoRemove(void)
{
/* Display a dialog box indicating that the XLL was successfully removed */
   Excel12f(xlcAlert, 0, 2,
      TempStr12(L"Thank you for removing Example.XLL!"),
      TempInt12(2));
   return 1;
}
```

## See also

#### Reference

[xlAutoAdd](xlautoadd.md)
#### Concepts

[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)

