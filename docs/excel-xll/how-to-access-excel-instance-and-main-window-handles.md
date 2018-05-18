---
title: "Access Excel Instance and Main Window Handles"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- accessing excel handles,handles [Excel 2007], accessing,Excel instances, accessing,window handles [Excel 2007], accessing
 
localization_priority: Normal
ms.assetid: 21e1dbdc-06fa-4514-9437-c4cffc3b4621
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Access Excel Instance and Main Window Handles

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
To program in the Windows environment, sometimes you must know the Microsoft Excel instance handle or main window handle. For example, these handles are useful when you are creating and displaying custom Windows dialog boxes.
  
There are two XLL-only C API functions that provide access to these handles: the [xlGetInst](xlgetinst.md) function and the [xlGetHwnd](xlgethwnd.md) function respectively. In Win32, all handles are 32-bit integers. However, when the **XLOPER** was designed, Windows was a 16-bit system. Therefore, the structure only allowed for 16-bit handles. In Win32, when called with **Excel4** or **Excel4v**, the **xlGetInst** function and the **xlGetHwnd** function return only the low part of the full 32-bit handle. 
  
In Excel 2007 and later versions, when these functions are called with [Excel12](excel4-excel12.md) or [Excel12v](excel4v-excel12v.md), the returned **XLOPER12** contains the full 32-bit handle. 
  
Obtaining the full instance handle is simple in any version of Excel, as it is passed to the Windows callback **DllMain**, which is called when the DLL is loaded. If you record this instance handle in a global variable, you never need to call the **xlGetInst** function. 
  
## Obtaining the Main Excel Handle in Excel 2003 and Earlier

To obtain the main Excel handle in Excel 2003 and earlier 32-bit versions, you must first call the **xlGetHwnd** function to obtain the low word of the actual handle. Then, you must iterate the list of top-level windows to search for a match with the returned low word. The following code illustrates the technique. 
  
```cs
typedef struct _EnumStruct
{
  HWND hwnd;  // Return value for Excel main hWnd.
  unsigned short wLoword; //Contains LowWord of the Excel main hWnd
} EnumStruct;
#define CLASS_NAME_BUFFER  50
BOOL CALLBACK EnumProc(HWND hwnd, EnumStruct * pEnum)
{
  // First check the class of the window. Must be "XLMAIN".
  char rgsz[CLASS_NAME_BUFFER];
  GetClassName(hwnd, rgsz, CLASS_NAME_BUFFER);
  if (!lstrcmpi(rgsz, "XLMAIN"))
  {
    // If that hits, check the loword of the window handle.
    if (LOWORD((DWORD) hwnd) == pEnum->wLoword)
    {
      // We have a match, return Excel main hWnd.
      pEnum->hwnd = hwnd;
      return FALSE;
    }
  }
  // No match - continue the enumeration.
  return TRUE;
}
BOOL GetHwnd(HWND * pHwnd)
{
  XLOPER x;
  //
  // xlGetHwnd only returns the LoWord of Excel hWnd
  // so all the windows have to be enumerated to see
  // which match the LoWord retuned by xlGetHwnd.
  //
  if (Excel4(xlGetHwnd, &x, 0) == xlretSuccess)
  {
    EnumStruct enm;
    enm.hwnd = NULL;
    enm.wLoword = x.val.w;
    EnumWindows((WNDENUMPROC) EnumProc, (LPARAM) &enm);
    if (enm.hwnd != NULL)
    {
      *pHwnd = enm.hwnd;
      return TRUE;
    }
  }
  return FALSE;
}
```

## See also

#### Concepts

[Displaying Dialog Boxes from Within a DLL or XLL](displaying-dialog-boxes-from-within-a-dll-or-xll.md)
  
[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)

