---
title: "Excel Commands, Functions, and States"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- states [excel 2007],commands [Excel 2007],worksheet functions [Excel 2007],macro-sheet functions [Excel 2007],Excel states
 
localization_priority: Normal
ms.assetid: 20f19aa4-f184-47be-bcdd-7ded78778974
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Excel Commands, Functions, and States

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Microsoft Excel recognizes two very different types of added functionality: commands and functions.
  
## Commands

In Excel, commands have the following characteristics:
  
- They perform actions in the same way that users do.
    
- They can do anything a user can do (subject to the limits of the interface used), such as altering Excel settings, opening, closing, and editing documents, initiating recalculations, and so on.
    
- They can be set up to be called when certain trapped events occur.
    
- They can display dialog boxes and interact with the user.
    
- They can be linked to control objects so that they are called when some action is taken on that object, such as left-clicking.
    
- They are never called by Excel during a recalculation.
    
- They cannot be called by functions during a recalculation.
    
## Functions

Functions in Excel do the following:
  
- They usually take arguments and always return a result.
    
- They can be entered into one or more cells as part of an Excel formula.
    
- They can be used in defined name definitions.
    
- They can be used in conditional formatting limit and threshold expressions.
    
- They can be called by commands.
    
- They cannot call commands.
    
Excel makes a further distinction between user-defined worksheet functions and user-defined functions that are designed to work on macro sheets. Excel does not limit user-defined macro sheet functions only to being used on macro sheets: these functions can be used anywhere a normal worksheet function can be used.
  
### Worksheet Functions

The following is true of Excel worksheet functions:
  
- They cannot access macro sheet information functions.
    
- They cannot obtain the values of uncalculated cells.
    
- They can be written and registered as thread-safe starting in Excel 2007.
    
### Macro-Sheet Functions

The following is true of Excel macro-sheet functions:
  
- They can access macro sheet information functions.
    
- They can obtain the values of uncalculated cells including the values of the calling cells.
    
- They are not considered thread safe starting in Excel 2007.
    
How Excel treats a user-defined function (UDF), what it permits the function to do, and how it recalculates the function are all determined when you register the function. If a function is registered as a worksheet function but tries to do something that only a macro-sheet function can do, the operation fails. Starting in Excel 2007, if a worksheet function registered as thread safe tries to call a macro sheet function, again, the operation fails.
  
Excel treats Microsoft Visual Basic for Applications (VBA) UDFs as macro sheet-equivalent functions, in that they can access workspace information and the value of uncalculated cells, and they are not considered as thread safe starting in Excel 2007.
  
## Excel States

Excel can be in one of a number of states at any given time depending on the actions of the user, an external process, a trapped event running a macro, or a timed Excel housekeeping event such as **Autosave**.
  
The states that the user experiences are as follows:
  
- **Ready state:** No commands or macros are being run. No dialog boxes are being displayed. No cells are being edited and the user is not in the middle of a cut/copy and paste operation. No embedded object has focus. 
    
- **Edit mode:** The user has started to type valid input characters into an unlocked or unprotected cell, or has pressed **F2** on one or more unlocked or unprotected cells. 
    
- **Cut/copy and paste mode:** The user has cut or copied a cell or range of cells and has not yet pasted them, or has pasted them using the paste-special dialog box, which enables multiple paste operations. 
    
- **Point mode:** The user is editing a formula and is selecting cells whose addresses are added to the formula being edited. 
    
The user can clear the edit, point, and cut/copy modes by pressing the **ESC** key, which returns Excel to its ready state. Other events can clear these states, such as the following: 
  
- The user opens a built-in dialog box.
    
- The user initiates a recalculation.
    
- The user runs a command.
    
- Excel performs an **Autosave** operation. 
    
- A timer event is trapped.
    
The last example is of importance to add-in developers. You should consider the impact of the normal usability of Excel where frequent timer event traps are being set and executed. When this is an important part of your add-in's functionality, you should provide users with an easily accessible way of suspending it, so that they can cut/copy and paste normally when they need to.
  
## See also

#### Concepts

[Excel Programming Concepts](excel-programming-concepts.md)
  
[Permitting User Breaks in Lengthy Operations](permitting-user-breaks-in-lengthy-operations.md)

