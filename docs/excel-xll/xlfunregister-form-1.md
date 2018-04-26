---
title: "xlfUnregister (Form 1)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- xlfUnregister
keywords:
- xlfunregister function [excel 2007]
 
localization_priority: Normal
ms.assetid: 850bf65f-a151-44d6-b49f-d53ae2c83760
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlfUnregister (Form 1)

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Can be called from a DLL or XLL command that has itself been called by Microsoft Excel. This is equivalent to calling **UNREGISTER** from an Excel XLM macro sheet. 
  
 **xlfUnregister** can be called in two forms: 
  
- Form 1: Unregisters an individual command or function.
    
- Form 2: Unloads and deactivates an XLL.
    
Called in Form 1, this function reduces the use count of a DLL function or command that was previously registered using **xlfRegister** or **REGISTER**. If the usage count is already zero, this function has no effect. When the use count of all the functions in a DLL reaches zero, the DLL is unloaded from memory.
  
 **xlfRegister** (Form 1) also defines a hidden name which is the function text argument,  _pxFunctionText_, and which evaluates to the function or command's registration ID. When unregistering the function, this name should be deleted using **xlfSetName** so that the function name is no longer listed by the Function Wizard. For more information, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
```cs
Excel4(xlfUnregister, LPXLOPER pxRes, 1, LPXLOPER pxRegisterId);
```

## Parameters

 _pxRegisterId_ ( **xltypeNum**)
  
The registration ID of the function to be unregistered.
  
## Property Value/Return Value

If successful, returns **TRUE** ( **xltypeBool**), otherwise it returns FALSE.
  
## Remarks

The registration ID of the function is returned by **xlfRegister** when the function is first registered. It can also be obtained by calling the [xlfRegisterId function](xlfregisterid.md) or the [xlfEvaluate function](xlfevaluate.md). Note that xlfRegisterId tries to register the function if it has not already been registered. For this reason, if you are only trying to get the ID so that you can unregister the function, it is better to obtain it by passing the registered name to **xlfEvaluate**. If the function has not been registered, **xlfEvaluate** fails with a #NAME? error. 
  
## Example

See the code for the **fExit** function in  `\SAMPLES\GENERIC\GENERIC.C`.
  
```cs
int WINAPI fExit(void)
{
   XLOPER12  xDLL,    // The name of this DLL //
   xFunc,             // The name of the function //
   xRegId;            // The registration ID //
   int i;
//
// This code gets the DLL name. It then uses this along with information
// from g_rgFuncs[] to obtain a REGISTER.ID() for each function. The
// register ID is then used to unregister each function. Then the code
// frees the DLL name and calls xlAutoClose.
//
   // Make xFunc a string //
   xFunc.xltype = xltypeStr;
   Excel12f(xlGetName, &amp;xDLL, 0);
   for (i = 0; i < g_rgWorksheetFuncsRows; i++)
   {
      xFunc.val.str = (LPWSTR) (g_rgWorksheetFuncs[i][0]);
      Excel12f(xlfRegisterId,&amp;xRegId,2,(LPXLOPER12)&amp;xDLL,(LPXLOPER12)&amp;xFunc);
      Excel12f(xlfUnregister, 0, 1, (LPXLOPER12) &amp;xRegId);
   }
   for (i = 0; i < g_rgCommandFuncsRows; i++)
   {
      xFunc.val.str = (LPWSTR) (g_rgCommandFuncs[i][0]);
      Excel12f(xlfRegisterId,&amp;xRegId,2,(LPXLOPER12)&amp;xDLL,(LPXLOPER12)&amp;xFunc);
      Excel12f(xlfUnregister, 0, 1, (LPXLOPER12) &amp;xRegId);
   }
   Excel12f(xlFree, 0, 1,  (LPXLOPER12) &amp;xDLL);
   return xlAutoClose();
}
```

## See also

#### Reference

[xlfRegister (Form 1)](xlfregister-form-1.md)
  
[xlfRegisterId](xlfregisterid.md)
  
[xlfUnregister (Form 2)](xlfunregister-form-2.md)
#### Concepts

[Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

