---
title: "xlGetInst"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlGetInst
keywords:
- xlgetinst function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 631a8f4e-ea7c-4743-9ee1-b2233fd7d98d

---

# xlGetInst

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns the instance handle of the instance of Microsoft Excel that is currently calling a DLL.
  
```cs
Excel4(xlGetInst, LPXLOPER pxRes, 0); /* returns low part only */
Excel12(xlGetInst, LPXLOPER12 pxRes, 0); /* returns full handle */
```

## Parameters

This function has no arguments.
  
## Property value/Return value

The instance handle (**xltypeInt**) will be in the **val.w** field. 
  
## Remarks

This function can be used to distinguish between multiple running instances of Excel that are calling the DLL.
  
When you are calling this function using [Excel4](excel4-excel12.md) or [Excel4v](excel4v-excel12v.md), the returned XLOPER integer variable is a signed 16-bit short int. This is only capable of containing the low 16 bits of the 32-bit Windows handle. Starting in Excel 2007, the integer variable of the **XLOPER12** is a signed 32-bit int and therefore contains the entire handle, removing the need to iterate all open windows. 
  
> [!IMPORTANT]
> If the **xlGetInst** function is used with the 64-bit version of Microsoft Excel, then the function will fail. This is because the **xltypeInt** value type is not wide enough to hold the 64-bit long handle returned by Excel in this case. For this purpose, Excel 2010 introduced a new function named [xlGetInstPtr](xlgetinstptr.md), which runs correctly with both the 32-bit and 64-bit versions of Excel. 
  
## Example

The following example compares the instance of the last copy of Excel that called it to the current copy of Excel that called it. If they are the same, it returns 1; if not, it returns 0; if the function fails, it returns -1.
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlGetInstExample(void)
{
    XLOPER12 xRes;
    static HANDLE hOld = 0;
    short iRet;
    if (Excel12(xlGetInst, &xRes, 0) != xlretSuccess)
        iRet = -1;
    else
    {
    HANDLE hNew;
    hNew = (HANDLE)xRes.val.w;
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



[xlGetHwnd](xlgethwnd.md)
  
[xlGetInstPtr](xlgetinstptr.md)


[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

