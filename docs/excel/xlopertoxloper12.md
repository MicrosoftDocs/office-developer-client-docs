---
title: "XLOperToXLOper12"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- XLOperToXLOper12
keywords:
- xlopertoxloper12 function [excel 2007]
ms.localizationpriority: medium
ms.assetid: b2d4581b-ebf6-4eba-aa95-69a5a9ee8028

---

# XLOperToXLOper12

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Conversion routine used to convert from the old **XLOPER** to the new **XLOPER12**.
  
```cs
BOOL XLOperToXLOper12(LPXLOPER pxloper, LPXLOPER12 pxloper12);
```

## Parameters

_pxloper_ (**LPXLOPER**)
  
Pointer to the source **XLOPER** to be converted.
  
_pxloper12_ (**LPXLOPER12**)
  
Pointer to the target **XLOPER12** to contain the converted value.
  
## Property value/Return value

**TRUE** if the conversion succeeded, **FALSE** otherwise.
  
## Remarks

Depending on the type of the **XLOPER**, this function allocates a new memory buffer for the converted values, which are pointed to in the target **XLOPER12**. The caller is responsible for freeing any memory associated with the copy if the conversion is a success; **FreeXLOper12T** can be used, or it can be done directly using **free**.
  
If the conversion fails, the caller does not need to free any memory.
  
In general, conversion from any **XLOPER** to an **XLOPER12** is possible. In contrast, conversion from an **XLOPER12** to an **XLOPER** can fail when the **XLOPER12** contains an array or reference that is too large or a string that is too long for the **XLOPER** to contain.
  
**XLOPER** ASCII byte strings are converted to **XLOPER12** Unicode wide-character strings in a way that is locale-dependent.
  
### Example

See the file `\SAMPLES\FRAMEWRK\FRAMEWRK.C` for the code for this function.
  