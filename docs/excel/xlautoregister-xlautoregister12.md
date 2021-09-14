---
title: "xlAutoRegister/xlAutoRegister12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlAutoRegister
keywords:
- xlautoregister function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: aa4673cf-8e97-4678-b8d4-6a74426334f9
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlAutoRegister/xlAutoRegister12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Excel calls the [xlAutoRegister function](xlautoregister-xlautoregister12.md) whenever a call has been made to the XLM function **REGISTER**, or the C API equivalent [xlfRegister function](xlfregister-form-1.md), with the return and argument types of the function being registered missing. It allows the XLL to search its internal lists of exported functions and commands to register the function with the argument and return types specified.
  
Starting in Excel 2007, Excel calls the **xlAutoRegister12** function in preference to the **xlAutoRegister** function if it is exported by the XLL. 
  
Excel does not require an XLL to implement and export either of these functions.
  
> [!NOTE]
> If **xlAutoRegister**/ **xlAutoRegister12** tries to register the function without supplying the argument and return types, a recursive calling loop occurs which eventually overflows the call stack and crashes Excel. 
  
```cs
LPXLOPER12 WINAPI xlAutoRegister12(LPXLOPER12 pxName);
LPXLOPER WINAPI xlAutoRegister(LPXLOPER pxName);
```

## Parameters

 _pxName_ (**xltypeStr**)
  
The name of the XLL function that is being registered.
  
## Property value/Return value

The function should return the result of the attempt to register the XLL function  _pxName_ using the **xlfRegister** function. If the specified function is not one of the XLL's exports, it should return the **#VALUE!** error, or **NULL** which Excel will interpret at **#VALUE!**.
  
## Remarks

Your implementation of **xlAutoRegister** should perform a case-insensitive search through your XLL's internal lists of the functions and commands it exports looking for a match with the passed-in name. If the function or command is found, **xlAutoRegister** should attempt to register it, using the **xlfRegister** function, making sure to provide the string that tells Excel the return and argument types of the function, as well as any other required information about the function. It should then return to Excel whatever the call to **xlfRegister** returned. If the function was registered successfully, **xlfRegister** returns an **xltypeNum** value containing the Register ID of the function. 
  
### Example

See the file  `SAMPLES\EXAMPLE\EXAMPLE.C` for an example implementation of this function. 
  
## See also



[REGISTER](xlfregister-form-1.md)
  
[UNREGISTER](xlfunregister-form-1.md)

