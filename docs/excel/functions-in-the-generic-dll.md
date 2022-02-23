---
title: "Functions in the Generic DLL" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- generic dll [excel 2007], functions,functions [Excel 2007], Generic DLL
 
ms.localizationpriority: medium
ms.assetid: 80ce2247-d69d-45b0-b5e2-4ff0d7078a2c

---

# Functions in the Generic DLL

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
The folder `\EXAMPLES\GENERIC\` contains Microsoft Visual Studio project files and source code files that are needed to compile the example DLL GENERIC.xll. You can use this project as a template for writing your own Microsoft Excel XLLs. The source code in this project demonstrates many of the features of the Excel C API.
  
When you load GENERIC.xll, it creates a new **Generic** menu with four commands:
  
- **Dialog** - Displays a Microsoft Excel dialog box.
- **Dance** - Moves the selection around until you press the **ESC** key.
- **Native Dialog** - Displays a Windows dialog box.
- **Exit** - Unloads GENERIC.xll and removes the **Generic** menu.

GENERIC.xll also provides three worksheet functions, Func1, FuncSum, and FuncFib, which can be used whenever GENERIC.xll is loaded. GENERIC.xll can be loaded using the Add-in Manager, or it is loaded if it was active at the normal end of the last Excel session.
  
This project uses the framework library (FRMWRK32.lib).
  
## In this section

[DIALOGMsgProc](dialogmsgproc.md)
  
[ExcelCursorProc](excelcursorproc.md)
  
[HookExcelWindow](hookexcelwindow.md)
  
[UnhookExcelWindow](unhookexcelwindow.md)
  
[fShowDialog](fshowdialog.md)
  
[fDance](fdance.md)
  
[fDialog/fDialog12](fdialog-fdialog12.md)
  
[fExit](fexit.md)
  
[Func1](func1.md)
  
[FuncSum](funcsum.md)
  
[FuncFib](funcfib.md)
  
## See also

[Functions in the Framework Library](functions-in-the-framework-library.md)
