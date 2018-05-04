---
title: "Permitting User Breaks in Lengthy Operations"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- xlabort function [excel 2007],concurrent tasks [Excel 2007],user breaks [Excel 2007]
 
localization_priority: Normal
ms.assetid: 0e3df597-0aa6-497f-bc52-58c7dc064538
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Permitting User Breaks in Lengthy Operations

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Even though Windows uses preemptive multitasking, where your functions or commands can take a long time to execute, it is good practice to yield some time to the operating system now and again to help it schedule concurrent tasks. Using native Windows calls, you can do this by using the sleep function. Using the C API, you can do it by using the [xlAbort function](xlabort.md), which not only yields the processor for an instant, but also checks to see if the user has pressed the cancel key, **ESC**.
  
The **xlAbort** function therefore enables your code to check whether the user wants to end the process, do the necessary cleanup, and then return control to Excel. The function also enables you to clear the break condition. This enables your commands to display a dialog box to verify whether the user wants to end the command. If the user does not want to end the command, calling the **xlAbort** function with the argument  *FALSE*  clears the break. (The default argument is  *TRUE*  , which simply checks the condition but does not clear it.) 
  
You can call the **xlAbort** function from a user-defined function (UDF) or from an XLL command. In a UDF, when the **xlAbort** function returns **TRUE**, having detected a user break, you would typically cut short the function calculation and return some value to indicate that the calculation was not completed, perhaps an error or zero. You would not clear the break condition so that other instances of lengthy functions that also check this condition also break. Excel implicitly clears this condition when a recalculation ends.
  
When you detect a break condition in a command, you typically clear the condition by calling the **xlAbort** function again with the argument **FALSE**, although Excel implicitly clears this condition when a command ends.
  
## See also

#### Concepts

[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)
  
[Multithreaded Recalculation in Excel](multithreaded-recalculation-in-excel.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)
  
[How to: Access Excel Instance and Main Window Handles](how-to-access-excel-instance-and-main-window-handles.md)

