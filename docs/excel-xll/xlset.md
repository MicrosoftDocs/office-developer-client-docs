---
title: "xlSet"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlSet
keywords:
- xlset function [excel 2007]
 
localization_priority: Normal
ms.assetid: 121e6212-0692-4430-97be-4792b53719bf
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlSet

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Puts constant values into cells or ranges very quickly. For more information, see "xlSet and Workbooks with Array Formulas" in [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
```cs
Excel12(xlSet, LPXLOPER12 pxRes, 2, LPXLOPER12 pxReference, LPXLOPER pxValue);
```

## Parameters

 _pxReference_ ( **xltypeRef** or **xltypeSRef**)
  
A rectangular reference describing the target cell or cells. The reference must describe adjacent cells, so that in an **xltypeRef** `val.mref.lpmref->count` must be set to 1. 
  
 _pxValue_
  
The value or values to be placed into the cell or cells. For more information, see the "Remarks" section.
  
## Remarks

### pxValue Argument

 _pxValue_ can either be a value or an array. If it is a value, the entire destination range is filled with that value. If it is an array ( **xltypeMulti**), the elements of the array are put into the corresponding locations in the rectangle.
  
If you use a horizontal array for the second argument, it is duplicated down to fill the entire rectangle. If you use a vertical array, it is duplicated right to fill the entire rectangle. If you use a rectangular array, and it is too small for the rectangular range you want to put it in, that range is padded with **#N/A**s.
  
If the target range is smaller than the source array, the values are copied in up to the limits of the target range and the extra data are ignored.
  
To clear an element of the destination rectangle, use an **xltypeNil** type array element in the source array. To clear the entire destination rectangle, omit the second argument. 
  
### Restrictions

 **xlSet** cannot be undone. In addition, it destroys any undo information that may have been available before. 
  
 **xlSet** can put only constants, not formulas, into cells. 
  
 **xlSet** behaves as a Class 3 command-equivalent function; that is, it is available only inside a DLL when the DLL is called from an object, macro, menu, toolbar, shortcut key, or the **Run** button in the **Macro** dialog box (accessed from **View** tab on the ribbon starting in Excel 2007, and the **Tools** menu in earlier versions). 
  
## Example

The following example fills B205:B206 with the value that was passed in from a macro. This command function example requires an argument, and so will only work if called from an XLM macro sheet, or from a VBA module using the **Application.Run** method. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlSetExample(short int iVal)
{
   XLOPER12 xRef, xValue;
   xRef.xltype = xltypeSRef;
   xRef.val.sref.count = 1;
   xRef.val.sref.ref.rwFirst = 204;
   xRef.val.sref.ref.rwLast = 205;
   xRef.val.sref.ref.colFirst = 1;
   xRef.val.sref.ref.colLast = 1;
   xValue.xltype = xltypeInt;
   xValue.val.w = iVal;
   Excel12(xlSet, 0, 2, (LPXLOPER12)&xRef, (LPXLOPER12)&xValue);
   return 1;
}
```

## See also

#### Reference

[xlCoerce](xlcoerce.md)
#### Concepts

[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

