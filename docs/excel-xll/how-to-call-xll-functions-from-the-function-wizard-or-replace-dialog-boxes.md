---
title: "How to Call XLL Functions from the Function Wizard or Replace Dialog Boxes"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- xll functions [excel 2007], calling from replace dialog box,Replace dialog box [Excel 2007], calling XLL functions,Function Wizard [Excel 2007], calling XLL functions,XLL functions [Excel 2007], calling from Function Wizard
 
localization_priority: Normal
ms.assetid: dc7e840e-6d1d-427b-97f9-7912e60ec954
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# How to: Call XLL Functions from the Function Wizard or Replace Dialog Boxes

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Microsoft Excel usually calls XLL functions during the normal recalculation of the workbook, or a part of it if the calculation is under the control of a macro. Remember that the function might not reside in a cell formula but might be part of a named range definition, or a conditional formatting expression.
  
There are two circumstances where a function can be called from an Excel dialog box. One is the **Paste Function Arguments** dialog box, where users are able to construct a function call one argument at a time. The other is when formulas are being modified and reentered by Excel in the **Replace** dialog box. For the **Paste Function Arguments** dialog box, you might not want your function to execute normally. This may be because it takes a long time to execute and you do not want to slow down the use of the dialog box. 
  
Both the **Paste Function** dialog box and the **Replace** dialog box have the Windows class name **bosa_sdm_XL**n, where n is a number. Windows provides an API function, **GetClassName**, that obtains this name from a Windows handle, an HWND variable type. It also provides another function, **EnumWindows**, that calls a supplied callback function (within your DLL) once for every top-level window that is currently open.
  
The callback function needs to perform only the following steps:
  
1. Check if the parent of this window is the current instance of Excel (in case there are multiple instances running).
    
2. Get the class name from the handle passed in by Windows.
    
3. Check if the class name is of the form **bosa_sdm_XL**n.
    
4. If you need to distinguish between the two dialog boxes, check if the dialog box title contains some identifying text. The window title is obtained using the Windows API call **GetWindowText**.
    
The following C++ code shows a class and callback to be passed to Windows that performs these steps. This is called by the functions that call test specifically for either of the dialog boxes concerned. 
  
> [!NOTE]
> Window titles of future Excel versions might change and invalidate this code. Note also that setting **window_title_text** to **NULL** has the effect of ignoring window title in the callback search. 
  
```cs
#define CLASS_NAME_BUFFSIZE  50
#define WINDOW_TEXT_BUFFSIZE  50
// Data structure used as input to xldlg_enum_proc(), called by
// called_from_paste_fn_dlg(), called_from_replace_dlg(), and
// called_from_Excel_dlg(). These functions tell the caller whether
// the current worksheet function was called from one or either of
// these dialog boxes.
typedef struct
{
  bool is_dlg;
  short low_hwnd;
  char *window_title_text; // set to NULL if don't care
}
  xldlg_enum_struct;
// The callback function called by Windows for every top-level window.
BOOL CALLBACK xldlg_enum_proc(HWND hwnd, xldlg_enum_struct *p_enum)
{
// Check if the parent window is Excel.
// Note: Because of the change from MDI (Excel 2010)
// to SDI (Excel 2013), comment out this step in Excel 2013.
  if(LOWORD((DWORD)GetParent(hwnd)) != p_enum->low_hwnd)
    return TRUE; // keep iterating
  char class_name[CLASS_NAME_BUFFSIZE + 1];
//  Ensure that class_name is always null terminated for safety.
  class_name[CLASS_NAME_BUFFSIZE] = 0;
  GetClassName(hwnd, class_name, CLASS_NAME_BUFFSIZE);
//  Do a case-insensitve comparison for the Excel dialog window
//  class name with the Excel version number truncated.
  size_t len; // The length of the window's title text
  if(_strnicmp(class_name, "bosa_sdm_xl", 11) == 0)
  {
// Check if a searching for a specific title string
    if(p_enum->window_title_text) 
    {
// Get the window's title and see if it matches the given text.
      char buffer[WINDOW_TEXT_BUFFSIZE + 1];
      buffer[WINDOW_TEXT_BUFFSIZE] = 0;
      len = GetWindowText(hwnd, buffer, WINDOW_TEXT_BUFFSIZE);
      if(len == 0) // No title
      {
        if(p_enum->window_title_text[0] != 0)
          return TRUE; // No match, so keep iterating
      }
// Window has a title so do a case-insensitive comparison of the
// title and the search text, if provided.
      else if(p_enum->window_title_text[0] != 0
      &amp;&amp; _stricmp(buffer, p_enum->window_title_text) != 0)
        return TRUE; // Keep iterating
    }
    p_enum->is_dlg = true;
    return FALSE; // Tells Windows to stop iterating.
  }
  return TRUE; // Tells Windows to continue iterating.
}
```

The **Paste Function** dialog box does not have a title, so the following function passes a search title string of "", that is, an empty string, to the callback to indicate that the match condition is that the window should not have a title. 
  
```cs
bool called_from_paste_fn_dlg(void)
{
    XLOPER xHwnd;
// Calls Excel4, which only returns the low part of the Excel
// main window handle. This is OK for the search however.
    if(Excel4(xlGetHwnd, &amp;xHwnd, 0))
        return false; // Couldn't get it, so assume not
// Search for bosa_sdm_xl* dialog box with no title string.
    xldlg_enum_struct es = {FALSE, xHwnd.val.w, ""};
    EnumWindows((WNDENUMPROC)xldlg_enum_proc, (LPARAM)&amp;es);
    return es.is_dlg;
}
```

## See also

#### Concepts

[Accessing XLL Code in Excel](accessing-xll-code-in-excel.md)
  
[Calling into Excel from the DLL or XLL](calling-into-excel-from-the-dll-or-xll.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)

