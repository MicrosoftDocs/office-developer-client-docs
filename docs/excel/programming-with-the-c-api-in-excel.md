---
title: "Programming with the C API in Excel"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- c api [excel 2007],programming interfaces [Excel 2007],C API [Excel 2007], when to use,C API [Excel 2007], relation to XLM,Excel programming interfaces
 
localization_priority: Normal
ms.assetid: 142bc0ce-7d16-4b69-9799-ce6558da2def
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Programming with the C API in Excel

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
You can use the Microsoft Excel 2013 XLL Software Development Kit and the C API to create high-performance worksheet functions for Excel 2013. The upgrades to the Excel 2013 C API reflect ongoing support for users for whom the performance of third-party or in-house functionality is critical.
  
## Excel Programming Interfaces

Excel provides several options for developing applications that interface with it. The Excel programming interfaces were added to earlier versions in the following order:
  
- **XLM macro language:** The first user-accessible language for the extension of Excel and the basis of the C API. Although still supported in Excel 2010, XLM has long been superseded by Visual Basic for Applications (VBA). 
    
- **C API and XLLs:** DLLs that are integrated with Excel. These DLLs provide the most direct and fastest interface for the addition of high-performance worksheet functions, although at the cost of some complexity compared with later technologies. 
    
- **VBA:** Visual Basic code objects that are associated with Excel workbook objects. VBA allows event trapping, customization, and the addition of user-defined functions and commands. VBA is the most commonly used and most easily available of the extensibility options. 
    
- **COM:** The interoperability standard for Windows-based applications, through which Excel exposes its events and objects. VBA uses COM to interact with Excel. Excel exports COM type libraries that can help you create C++ COM code resources and applications that can control Excel externally. 
    
- **The Microsoft .NET Framework:** The multi-language managed code environment designed for rapid application development for distributed environments. The primary programming language for code that is based on the .NET Framework is C#, although many languages can be compiled to the Microsoft intermediate language (MSIL). Excel 2013 can access code resources contained within .NET Framework assemblies. 
    
## When to Use the C API

The primary reason for writing XLLs and using the C API is to create high-performance worksheet functions. Although XLL functions are frequently referred to as user-defined functions, the investment in time to obtain the understanding and skills that are required to write XLLs make this a technology impractical for most users. Nevertheless, the applications of high-performance functions—and, in Excel 2013, the ability to write multithreaded interfaces to powerful server resources—make this a very important part of Excel extensibility. 
  
The revision of the C API that was introduced in Excel 2007 is mainly concerned with the aspects relating to high-performance calculations, rather than features such as the user interface.
  
### Writing High-Performance User-Defined Worksheet Functions

The Excel C API is the ideal choice when you want to create high-performance worksheet functions by creating XLL add-ins. The C API provides you with the most direct access to worksheet data. XLLs provide Excel with the most direct access to the DLL resources. The performance of XLLs is further enhanced in Excel 2013 by the addition of new data types and, most importantly, support for running user-defined functions on clustered servers.
  
Working with XLLs comes at a cost: The C API has none of the higher-level rapid development features of VBA, COM, or the .NET Framework. Memory management is low level and, therefore, puts greater responsibility on the developer. Many Excel features that are exposed via COM, making them available through VBA and the .NET Framework, are not exposed to the C API.
  
### Accessing Multithreaded Servers by Using XLL Worksheet Functions

Multithreaded recalculation (MTR), which was introduced in Excel 2007, enables you to create thread-safe XLL worksheet functions. You can use these functions to access multithreaded servers. Later sections describe more fully how this can dramatically increase the performance observed by the user. For Excel users who sometimes need access to a lot of processing power, the combination of an XLL that uses MTR and a powerful calculation server provides the highest-performance solution.
  
### Customizing the Excel User Interface

For many versions of Excel, the C API has not been the best choice for customizing the user interface. VBA has superior access to Excel objects and events. The user interface introduced in Excel 2007 is significantly different from earlier versions both in appearance and underlying technology. You can best customize this interface by using managed code resources.
  
### Creating Applications that Can Be Accessed on the Internet

Excel Services, introduced with the 2007 Microsoft Office system, provides the best way to give users access to workbooks and Excel functionality by using standard Web browser tools. Together with .NET Framework development languages and resources, these technologies represent an important part of Excel deployment to users in the future.
  
### Controlling Excel from External Applications

Excel exposes its objects, methods, and events through the COM interface. You can, therefore, use COM to create stand-alone applications that can start and control an Excel session or control an existing Excel session. You can access the COM-exposed Excel interface within several development languages, including C++ and VBA. C# and the .NET Framework similarly provide an interface to Excel that enables remote access to and control of Excel.
  
## Asynchronous Calling of Excel

Excel allows XLLs to call the C API only when Excel has passed control to the XLL. A worksheet function that is called by Excel can call back into Excel by using the C API. An XLL command that is called by Excel can call the C API. DLL and XLL functions and commands that are called by VBA when VBA has itself been called by Excel can call the C API. You cannot, for example, set a timed Windows callback into your XLL and call the C API from it, and you cannot call the C API from a background thread created by your XLL. Calling Excel asynchronously by using COM from a DLL or XLL is not recommended.
  
This is very limiting because there may be applications in which you want Excel to react to an event asynchronously. For example, you might want Excel to retrieve a piece of data on the Internet and recalculate whenever that data changes. Or you might want a background thread to perform a calculation and have Excel recalculate when it is finished.
  
You can do this by having Excel actively poll for changes, but this is inefficient and limiting because it involves Excel frequently interrupting its regular activity. You can set up repeated timed command using the C API or VBA, although this is not an ideal solution.
  
Ideally you would want a more efficient external process to check for the change in data, and for that external process to trigger Excel to retrieve the update and perform a recalculation. You can do this by using an application that interfaces to Excel by using COM. COM is not restricted in the same manner as the C API to making calls only when Excel has explicitly passed it control. COM applications can invoke Excel methods whenever Excel is in a ready state, although these method calls might be ignored if dialog boxes are being displayed, menus are pulled down, or when a macro is executing.
  
## C API and Its Relation to XLM

The Excel macro (XLM) language was the first user-accessible programming environment provided in Excel. It enabled users to create custom commands and functions on special macro sheets that look like ordinary worksheets. XLM macro sheets are still supported in Excel 2013. You can use all the usual worksheet functions like **SUM** and **LOG** on a macro sheet, in addition to the following items that cannot be entered on a worksheet: 
  
- Workspace information functions such as **GET.CELL** and **GET.WORKBOOK**.
    
- Command-equivalent functions that enable automation of ordinary user operations such as **DEFINE.NAME** and **PASTE**.
    
- Functions that relate to add-ins such as **REGISTER**.
    
- Command-equivalent event traps such as **ON.ENRTY** and **ON.TIME**.
    
- Macro function-specific operations such as **ARGUMENT** and **VOLATILE**.
    
- Flow-control operations such as **GOTO** and **RETURN**.
    
A limited version of the C API existed in Excel version 3. However, in Excel version 4, the XLM language was mapped to the C API. Since then, DLLs have been able to call all worksheet functions, macro sheet information functions, and commands, and to set event traps. DLLs cannot call XLM flow control functions from within the C API. These macro-sheet functions and commands are documented in the Help file XLMacr8.hlp (formerly named Macrofun.hlp). To obtain this help file, go to the [Microsoft Download Center](https://download.microsoft.com) and search for "XLMacr8.hlp". 
  
> [!NOTE]
> Windows Vista and Windows 7 do not directly support .hlp files, but you can download the [Windows Help program (WinHlp32.exe) for Windows Vista](https://go.microsoft.com/fwlink/?LinkID=82148) or the [Windows Help program (WinHlp32.exe) for Windows 7](https://www.microsoft.com/download/en/details.aspx?id=91) from Microsoft that enables them to be opened. 
  
DLLs call C API equivalents of these functions and commands by using the callback functions **Excel4**, **Excel4v**, **Excel12**, and **Excel12v** (the last two were introduced in Excel 2007). Enumerated constants that correspond to each function and command are defined in a header file and passed as one of the arguments to these callbacks. For example, **GET.CELL** is represented by **xlfGetCell**, **REGISTER** by **xlfRegister**, and **DEFINE.NAME** by **xlcDefineName**.
  
In addition to providing the worksheet functions and macro-sheet functions and commands, the C API provides function and command enumerations that can be called only by using these callbacks from within a DLL. For example, **xlGetName** enables the DLL to find out its own the full path and file name, which is required when you register functions and commands with Excel. 
  
Since the introduction of Visual Basic for Applications (VBA) sheets in Excel version 5, and the Visual Basic Editor (VBE) in version 8 (Excel 97), the easiest way for users to customize Excel is to use VBA instead of XLM. Consequently, much of the new functionality introduced in later versions of Excel is available through VBA, but not through XLM or the C API. For example, several commands, event traps, and enhanced dialog box capabilities are available through VBA, but not through XLM or the C API.
  
For more information, see [What's New in the C API for Excel](what-s-new-in-the-c-api-for-excel.md).
  
## See also



[What's New in the C API for Excel](what-s-new-in-the-c-api-for-excel.md)
  
[C API Callback Functions Excel4, Excel12](c-api-callback-functions-excel4-excel12.md)


[Getting Started with the Excel XLL SDK](getting-started-with-the-excel-xll-sdk.md)

