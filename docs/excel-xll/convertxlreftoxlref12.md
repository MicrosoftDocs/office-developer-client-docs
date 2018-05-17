---
title: "ConvertXLRefToXLRef12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- ConvertXLRefToXLRef12
keywords:
- convertxlreftoxlref12 function [excel 2007]
 
localization_priority: Normal
ms.assetid: 94580044-9497-425f-a31e-53bb4d94dc30
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# ConvertXLRefToXLRef12

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework function that attempts to convert an **XLREF** into an **XLREF12**.
  
```cs
BOOL ConvertXLRefToXLRef12(LPXLREF pxRef, LPXLREF12 pxRef12);
```

## Parameters

 _pxRef_ ( **LPXLREF**)
  
Pointer to the source reference structure.
  
 _pxRef12_ ( **LPXLREF12**)
  
Pointer to the target reference structure into which the converted value is to be placed.
  
## Property Value/Return Value

 **TRUE** if the conversion succeeded, **FALSE** otherwise. 
  
## Remarks

Provided that the passed-in **XLREF** is valid, this operation should always be successful. In contrast, conversion the other way from **XLREF12** to **XLREF**, performed by [ConvertXLRef12ToXLRef](convertxlref12toxlref.md), fails if the supplied reference refers to part of an Excel 2007 worksheet that is not supported in earlier versions.
  
## Example

 `\SAMPLES\FRAMEWRK\FRAMEWRK.C`
  
```cs
BOOL ConvertXLRefToXLRef12(LPXLREF pxref, LPXLREF12 pxref12)
{
   if (pxref->rwLast >= pxref->rwFirst &amp;&amp; pxref->colLast >= pxref->colFirst)
   {
      if (pxref->rwFirst >= 0 &amp;&amp; pxref->colFirst >= 0)
      {
         pxref12->rwFirst = pxref->rwFirst;
         pxref12->rwLast = pxref->rwLast;
         pxref12->colFirst = pxref->colFirst;
         pxref12->colLast = pxref->colLast;
         return TRUE;
      }
   }
   return FALSE;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

