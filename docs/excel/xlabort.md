---
title: "xlAbort"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlAbort
keywords:
- xlabort function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 0fe71454-6b00-464b-8abf-afb209d57754

---

# xlAbort

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Yields the processor to other tasks in the system and checks whether the user has pressed **ESC** to cancel a macro. If the user has pressed **ESC** during a workbook recalculation, it can also be detected from within a worksheet function by calling this function. 
  
```cs
Excel12(xlAbort, LPXLOPER12 pxRes, 1, LPXLOPER12 pxRetain);
```

## Parameters

 _pxRetain_ (**xltypeBool**)
  
(Optional). If **FALSE**, this function checks for the break condition and clears any pending break. This enables the user to continue despite the break condition. If this argument is omitted or is **TRUE**, the function checks for a user abort without clearing it.
  
## Property value/Return value

Returns **TRUE** (**xltypeBool**) if the user has pressed **ESC**.
  
## Remarks

### 

#### Frequent Calls May Be Needed

Functions and commands that could take a long time should call this function frequently to yield the processor to other tasks in the system.
  
#### Avoid Sensitive Language

Avoid using the term "Abort" in your user interface. Consider using "Cancel," "Halt," "Break," or "Stop" instead.
  
## Example

The following code repeatedly moves the active cell on a sheet until one minute has elapsed or until the user presses **ESC**. It calls the function **xlAbort** occasionally. This yields the processor, easing cooperative multitasking. 
  
 `\SAMPLES\GENERIC\GENERIC.C`
  
```cs
int WINAPI fDance(void)
{
   DWORD dtickStart;
   XLOPER12 xAbort, xConfirm;
   int boolSheet;
   int col=0;
   XCHAR rgch[32];
//
// Check what kind of sheet is active. If it is a worksheet or macro
// sheet, this function will move the selection in a loop to show
// activity. In any case, it will update the status bar with a countdown.
//
// Call xlSheetId; if that fails the current sheet is not a macro sheet or
// worksheet. Next, get the time at which to start. Then start a while
// loop that will run for one minute. During the while loop, check if the
// user has pressed ESC. If true, confirm the abort. If the abort is
// confirmed, clear the message bar and return; if the abort is not
// confirmed, clear the abort state and continue. After checking for an
// abort, move the active cell if on a worksheet or macro. Then
// update the status bar with the time remaining.
//
// This block uses TempActiveCell12(), which creates a temporary XLOPER12.
// The XLOPER12 contains a reference to a single cell on the active sheet.
// This function is part of the framework library.
//
   boolSheet = (Excel12f(xlSheetId, 0, 0) == xlretSuccess);
   dtickStart = GetTickCount();
   while (GetTickCount() < dtickStart + 60000L)
   {
      Excel12f(xlAbort, &xAbort, 0);
      if (xAbort.val.xbool)
      {
         Excel12f(xlcAlert, &xConfirm, 2,
           TempStr12(L"Are you sure you want to cancel this operation?"),
              TempNum12(1));
         if (xConfirm.val.xbool)
         {
            Excel12f(xlcMessage, 0, 1, TempBool12(0));
            return 1;
         }
         else
         {
            Excel12f(xlAbort, 0, 1, TempBool12(0));
         }
      }
      if (boolSheet)
      {
         Excel12f(xlcSelect, 0, 1,
            TempActiveCell12(0,(BYTE)col));
         col = (col + 1) & 3;
      }
      wsprintfW(rgch,L"0:%lu",
         (60000 + dtickStart - GetTickCount()) / 1000L);
      Excel12f(xlcMessage, 0, 2, TempBool12(1), TempStr12(rgch));
   }
   Excel12f(xlcMessage, 0, 1, TempBool12(0));
   return 1;
}
```

## See also



[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

