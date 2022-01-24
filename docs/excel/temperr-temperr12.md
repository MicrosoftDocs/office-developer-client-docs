---
title: "TempErr/TempErr12"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- TempErr
- TempErr12
keywords:
- temperr function [excel 2007],TempErr12 function [Excel 2007]
 
ms.localizationpriority: medium
ms.assetid: cf8c26b2-ca2b-4dda-a02d-0ccbeac19106

---

# TempErr/TempErr12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that creates a temporary **XLOPER**/ **XLOPER12** containing a Microsoft Excel worksheet error. 
  
```cs
LPXLOPER TempErr(WORD err);
LPXLOPER12 TempErr12(BOOL err);
```

## Parameters

 _err_
  
The desired error code, or its literal numeric equivalent, as shown in the following table.
  
|**Error**|**Error code defined in XLCALL.H**|**Decimal equivalent**|
|:-----|:-----|:-----|
|#NULL  <br/> |**xlerrNull** <br/> |0  <br/> |
|#DIV/0!  <br/> |**xlerrDiv0** <br/> |7  <br/> |
|#VALUE!  <br/> |**xlerrValue** <br/> |15  <br/> |
|#REF!  <br/> |**xlerrRef** <br/> |23  <br/> |
|#NAME?  <br/> |**xlerrName** <br/> |29  <br/> |
|#NUM!  <br/> |**xlerrNum** <br/> |36  <br/> |
|#N/A  <br/> |**xlerrNA** <br/> |42  <br/> |
   
## Return value

Returns an **xltypeBool** containing the error code passed in. 
  
## Example

This example uses the **TempErr12** function to return a #VALUE! error to Excel. 
  
> [!NOTE]
> The Framework library function **TempErr12** allocates memory from an internal buffer, which is normally freed when the Framework function **Excel12f** is called. If this example function is called repeatedly without **Excel12f** being called, a memory leak occurs. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
LPXLOPER WINAPI TempErrExample(void)
{
    return TempErr12(xlerrValue);
}
```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

