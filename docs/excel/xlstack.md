---
title: "xlStack"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlStack
keywords:
- xlstack function [excel 2007]
ms.localizationpriority: medium
ms.assetid: f9f030e8-1ec9-4cbf-92e1-360526260916

---

# xlStack

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Checks the amount of space left on the stack.
  
```cs
Excel12(xlStack, LPXLOPER12 pxRes, 0);
```

## Parameters

This function takes no arguments.
  
## Property value/Return value

Returns the number of bytes (**xltypeInt**) remaining on the stack.
  
## Remarks

The amount of available stack space of recent versions overflows the 16-bit signed integer of the **XLOPER**. This means that **xlStack** can return a value between -32767 and 32768 when called using **XLOPER**s and **Excel4** or **Excel4v**. To obtain the correct value in this case, you must cast the returned value to an unsigned short.
  
Starting in Excel 2007, you should call this function using **XLOPER12**s and **Excel12** or **Excel12v**, in which case the returned value is amount of stack space available or 64 KB, whichever is the lesser.
  
Excel has a limited amount of space on the stack, and you should take care not to overrun this space. Never put very large data structures on the stack, and make as many local variables as possible static. Avoid calling functions recursively, because that will quickly fill up the stack.
  
If you suspect that you are overrunning the stack, call this function frequently to see how much stack space is left.
  
## Example

The first example displays an alert message containing the amount of stack space left and is contained in `\SAMPLES\EXAMPLE\EXAMPLE.C`. The second example does the same thing, working with **XLOPER**s and is not contained in the SDK example code.
  
```cs
short WINAPI xlStackExample(void)
{
   XLOPER12 xRes;
   Excel12(xlStack, &xRes, 0);
   Excel12(xlcAlert, 0, 1, (LPXLOPER12)&xRes);
   return 1;
} 
short int WINAPI xlStackExample_XLOPER(void)
{
    XLOPER xRes;
    Excel4(xlStack, (LPXLOPER)&xRes, 0);
    xRes.xltype = xltypeNum; // Change the type to double
    // Cast to an unsigned short to get rid of the overflow problem
    xRes.val.num = (double)(unsigned short) xRes.val.w;
    Excel4(xlcAlert, 0, 1, (LPXLOPER)& xRes);
    return 1;
}
```

## See also

- [C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)
