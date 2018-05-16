---
title: "ConvertXLRef12ToXLRef"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- ConvertXLRef12ToXLRef
keywords:
- convertxlref12toxlref function [excel 2007]
 
localization_priority: Normal
ms.assetid: b620ed21-73ef-489b-9c00-7be12bb41214
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# ConvertXLRef12ToXLRef

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Tries to convert an **XLREF12** into an **XLREF**.
  
```cs
BOOL ConvertXLRefToXLRef12(LPXLREF12 pxRef12, LPXLREF pxRef);
```

## Parameters

 _pxRef12_ ( **LPXLREF12**)
  
Pointer to the source reference structure.
  
 _pxRef_ ( **LPXLREF**)
  
Pointer to the target reference structure into which the converted value is to be placed.
  
## Property Value/Return Value

 **TRUE** if the conversion succeeded, **FALSE** otherwise. 
  
## Remarks

The conversion from **XLREF12** to **XLREF** fails if the supplied reference refers to part of a Excel 2007 worksheet that is not supported in earlier versions. 
  
## Example

 `\SAMPLES\FRAMEWRK\FRAMEWRK.C`
  
```cs
BOOL ConvertXLRef12ToXLRef(LPXLREF12 pxref12, LPXLREF pxref)
{
   if (pxref12->rwLast >= pxref12->rwFirst &amp;&amp; pxref12->colLast >= pxref12->colFirst)
   {
      if (pxref12->rwFirst >=0 &amp;&amp; pxref12->colFirst >= 0)
      {
         if (pxref12->rwLast < rwMaxO8 &amp;&amp; pxref12->colLast < colMaxO8)
         {
            pxref->rwFirst = (WORD)pxref12->rwFirst;
            pxref->rwLast = (WORD)pxref12->rwLast;
            pxref->colFirst = (BYTE)pxref12->colFirst;
            pxref->colLast = (BYTE)pxref12->colLast;
            return TRUE;
         }
      }
   }
   return FALSE;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

