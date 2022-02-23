---
title: "xlAutoOpen" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlAutoOpen
keywords:
- xlautoopen function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 748cecb6-61d0-496b-a1a4-a73d22eb29e2

---

# xlAutoOpen

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Callback function that must be implemented and exported by every valid XLL. The **xlAutoOpen** function is the recommended place from where to register XLL functions and commands, initialize data structures, customize the user interface, and so on.
  
```cs
int WINAPI xlAutoOpen(void);
```

## Parameters

This function takes no arguments.
  
## Property value/Return value

Your implementation of this function must return 1 (**int**).
  
## Remarks

Microsoft Excel calls **xlAutoOpen** whenever the XLL is activated. The XLL is activated in the following situations:
  
- At the start of an Excel session if it was active in the last Excel session that ended normally.

- If loaded during an Excel session.

- An XLL can be loaded in several ways:

- By choosing **Open** on the **File** menu (where the version of Excel supports this method of loading XLLs).

- Using the Add-In Manager.

- From another XLL that calls [xlfRegister](xlfregister-form-1.md) with the name of this DLL as the only argument.

- From an XLM macro sheet that calls [REGISTER](xlfregister-form-1.md) with the name of this DLL as the only argument.

- If the add-in is deactivated and reactivated during an Excel session, this function is called on reactivation.

### Example

See the files `SAMPLES\EXAMPLE\EXAMPLE.C` and `SAMPLES\GENERIC\GENERIC.C`, and for example implementations of this function.
  
## See also

[xlAutoClose](xlautoclose.md)  
[xlAutoRegister/xlAutoRegister12](xlautoregister-xlautoregister12.md)
[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)
