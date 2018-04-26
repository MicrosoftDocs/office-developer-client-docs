---
title: "RunApplication Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm93359
  
localization_priority: Normal
ms.assetid: 29967e6e-c441-b115-3ee6-2299b8a3bc25
description: "Security NoteUse caution when running executable files or code in macros or applications. Executable files or code can be used to carry out actions that might compromise the security of your computer and data."
---

# RunApplication Macro Action

> [!SECURITY NOTE]

You can use the **RunApplication** action to run a Microsoft Windows-based or MS-DOS-based application, such as Microsoft Excel, Microsoft Word, or Microsoft PowerPoint, from within Microsoft Access. For example, you may want to paste Excel spreadsheet data into your Access database. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **RunApplication** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Command Line** <br/> |The command line used to start the application (including the path and any other necessary parameters, such as switches that run the application in a particular mode). Enter the command line in the **Command Line** box in the **Action Arguments** section of the Macro Builder pane. This is a required argument.  <br/> |
   
## Remarks

The application selected with this action loads and runs in the foreground. The macro containing this action continues to run after starting the application.
  
You can transfer data between the other application and Access by using the Microsoft Windows dynamic data exchange (DDE) facility or the Clipboard. You can use the **SendKeys** action to send keystrokes to the other application (although DDE is a more efficient method for transferring data). You can also share data among applications by using automation. 
  
MS-DOS-based applications run in an MS-DOS window within the Windows environment.
  
In Windows operating systems, there are a number of ways to run an application, including starting the program from the Windows Explorer, using the **Run** command on the **Start** menu, and double-clicking a program icon on the Windows Desktop. 
  
You can't run the **RunApplication** action in a Visual Basic for Applications (VBA) module. Use the VBA **Shell** function instead. 
  

