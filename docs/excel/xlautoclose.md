---
title: "xlAutoClose"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlAutoClose
keywords:
- xlautoclose function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 147e46cd-d4d7-49eb-acdc-5a2ebc2fb6c2

---

# xlAutoClose

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Called by Microsoft Excel whenever the XLL is deactivated. The add-in is deactivated when an Excel session ends normally. The add-in can be deactivated by the user during an Excel session, and this function will be called in that case.
  
Excel does not require an XLL to implement and export this function, although it is advisable so that your XLL can unregister functions and commands, release resources, undo customizations, and so on. If functions and commands are not explicitly unregistered by the XLL, Excel does this after calling the **xlAutoClose** function. 
  
```cs
int WINAPI xlAutoClose(void);
```

## Parameters

This function takes no arguments.
  
## Property value/Return value

Your implementation of this function must return 1 (**int**).
  
## Remarks

Excel calls the **xlAutoClose** function whenever the XLL is deactivated, that is, unloaded from memory. The XLL is deactivated in the following situations: 
  
- At the normal end of an Excel session if active during that session.
    
- If explicitly unloaded during an Excel session.
    
- An XLL can be unloaded in several ways:
    
- Using the Add-In Manager.
    
- From another XLL that calls [xlfUnregister](xlfunregister-form-1.md) with the name of this DLL as the only argument. 
    
- From an XLM macro sheet that calls [UNREGISTER](xlfunregister-form-1.md) with the name of this DLL as the only argument. 
    
This function should do the following:
  
- Remove any menus or menu items that were added by the XLL.
    
- Perform any necessary global cleanup.
    
- Delete any names that were created, especially names of exported functions. Remember that registering functions may cause some names to be created, if the fourth argument to **REGISTER** is present. 
    
## Example

See the files  `SAMPLES\EXAMPLE\EXAMPLE.C` and  `SAMPLES\GENERIC\GENERIC.C` for example implementations of this function. The following code is from  `SAMPLES\GENERIC\GENERIC.C`.
  
```cs
int WINAPI xlAutoClose(void)
{
   int i;
   XLOPER12 xRes;
//
// This block first deletes all names added by xlAutoOpen or
// xlAutoRegister12. Next, it checks if the drop-down menu Generic still
// exists. If it does, it is deleted using xlfDeleteMenu. It then checks
// if the Test toolbar still exists. If it is, xlfDeleteToolbar is
// used to delete it.
//
// The following code to delete the defined names
// does not work in the current version of Excel. 
// You cannot delete these names once they are Registered.
// The code is left here in case the functionality becomes 
// available in a future version.
//
   for (i = 0; i < g_rgWorksheetFuncsRows; i++)
      Excel12f(xlfSetName, 0, 1, TempStr12(g_rgWorksheetFuncs[i][2]));
   for (i = 0; i < g_rgCommandFuncsRows; i++)
      Excel12f(xlfSetName, 0, 1, TempStr12(g_rgCommandFuncs[i][2]));
//
// Everything else works as documented.
//
   Excel12f(xlfGetBar, &amp;xRes, 3, TempInt12(10), TempStr12(L"Generic"), TempInt12(0));
   if (xRes.xltype != xltypeErr)
   {
      Excel12f(xlfDeleteMenu, 0, 2, TempNum12(10), TempStr12(L"Generic"));
      // Free the XLOPER12 returned by xlfGetBar //
      Excel12f(xlFree, 0, 1, (LPXLOPER12) &amp;xRes);
   }
   Excel12f(xlfGetToolbar, &amp;xRes, 2, TempInt12(7), TempStr12(L"Test"));
   if (xRes.xltype != xltypeErr)
   {
      Excel12f(xlfDeleteToolbar, 0, 1, TempStr12(L"Test"));
      // Free the XLOPER12 returned by xlfGetToolbar //
      Excel12f(xlFree, 0, 1, (LPXLOPER12) &amp;xRes);
   }
   return 1;
}
```

## See also



[xlAutoOpen](xlautoopen.md)


[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)

