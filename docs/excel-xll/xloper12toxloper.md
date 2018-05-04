---
title: "XLOper12ToXLOper"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- XLOper12ToXLOper
keywords:
- xloper12toxloper function [excel 2007]
 
localization_priority: Normal
ms.assetid: b46f87c4-778b-4502-be57-c3725f73a644
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# XLOper12ToXLOper

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Conversion routine used to convert from the new **XLOPER12** to the old **XLOPER**.
  
```cs
BOOL XLOper12ToXLOper(LPXLOPER12 pxloper12, LPXLOPER pxloper);
```

## Parameters

 _pxloper12_ ( **LPXLOPER12**)
  
Pointer to the source **XLOPER12** to be converted. 
  
 _pxloper_ ( **LPXLOPER**)
  
Pointer to the target **XLOPER** to contain the converted value. 
  
## Property Value/Return Value

 **TRUE** if the conversion succeeded, **FALSE** otherwise. 
  
## Remarks

Depending on the type of the **XLOPER12**, this function allocates a new memory buffer for the converted values, which are pointed to in the target **XLOPER**. The caller is responsible for freeing any memory associated with the copy if the conversion is a success; **FreeXLOperT** can be used, or it can be done directly by using **free**.
  
If the conversion fails, the caller does not need to free any memory.
  
Conversion from an **XLOPER12** to an **XLOPER** can fail when the **XLOPER12** contains an array or reference that is too large or a string that is too long for the **XLOPER** to contain. 
  
 **XLOPER12** Unicode wide-character strings are converted to **XLOPER** ASCII byte strings in a way that is locale-dependent. 
  
The **XLOPER12** **xltypeInt** is a 32-bit signed integer, whereas the **XLOPER** **xltypeInt** is a 16-bit signed integer. When a supplied **XLOPER12** integer exceeds the limit of an **XLOPER** integer, the integer is converted to an 8-byte double and returned in an **XLOPER** of type **xltypeNum**. This is the only case in which this function changes the type of the converted **XLOPER**.
  
### Example

See the file  `\SAMPLES\FRAMEWRK\FRAMEWRK.C` for the code for this function. 
  
## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

