---
title: "debugPrintf"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- debugPrintf
keywords:
- debugprintf function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 9ad541f6-0b35-4f50-926a-8940e3f8033a
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# debugPrintf

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that writes a null-terminated byte-string to the active debugger via the Windows SDK function **OutputDebugStringA**. If the application has no debugger, the system debugger displays the string. If the application has no debugger and the system debugger is not active, **debugPrintf** does nothing. 
  
This function does not return a value.
  
```cs
void WINAPI debugPrintf(LPSTR lpFormat, arguments);
```

## Parameters

 _lpFormat (LPSTR)_
  
The format string, which follows the syntax and rules for that used with the **sprintf** function. 
  
 _arguments_
  
Zero or more arguments to match the format string.
  
## Example

This function prints a string to show that control was passed to it. The _DEBUG flag must be defined before compiling or else this function does nothing.
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI debugPrintfExample(void)
{
#ifdef _DEBUG
   debugPrintf("Made it!\r");
#endif
   return 1;
}

```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

