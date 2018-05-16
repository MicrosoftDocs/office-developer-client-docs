---
title: "xlGetInstPtr"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a166f39c-f10b-4e56-8b5d-e6a54ee08c8f
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlGetInstPtr

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns the instance handle of the instance of Microsoft Excel that is currently calling a DLL.
  
```cs
Excel4(xlGetInstPtr, LPXLOPER pxRes, 0);Excel12(xlGetInstPtr, LPXLOPER12 pxRes, 0);
```

## Parameters

This function has no arguments.
  
## Property Value/Return Value

The instance handle ( **xltypeBigData**) will be in the **val.bigdata.h.hdata** field. 
  
## Remarks

This function can be used to distinguish between multiple running instances of Excel that are calling the DLL.
  
This function returns a correct value with both 32-bit and 64-bit versions of Excel. It was introduced in Excel 2010 as an extension to the [xlGetInst](xlgetinst.md) function, which works correctly only with 32-bit versions of Excel. 
  
This function works correctly when it is called by using both the [Excel4 and Excel12](excel4-excel12.md) varieties of the API callback functions, because both **XLOPER** and **XLOPER12** have the same structure that supports the **xltypeBigData** value type. 
  
## Example

The following example compares the instance of the last copy of Excel that called it to the current copy of Excel that called it. If they are the same, it returns 1; if not, it returns 0; if the function fails, it returns -1. This sample works with both 32-bit and 64-bit versions of Excel.
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlGetInstPtrExample(void)
{
    XLOPER12 xRes;
    static HANDLE hOld = 0;
    short iRet;
    if (Excel12(xlGetInstPtr, &amp;xRes, 0) != xlretSuccess)
    iRet = -1;
    else
    {
    HANDLE hNew;
    hNew =  xRes.val.bigdata.h.hdata;
    if (hNew != hOld)
    iRet = 0;
    else
    iRet = 1;
    hOld = hNew;
    }
    return iRet;
}
```

## See also

#### Reference

[xlGetHwnd](xlgethwnd.md)
  
[xlGetInst](xlgetinst.md)
#### Concepts

[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

