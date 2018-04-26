---
title: "Worksheet References"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- references [excel 2007], worksheet,worksheet references [Excel 2007],external worksheet references [Excel 2007],active worksheet [Excel 2007],current worksheet [Excel 2007],internal worksheet references [Excel 2007]
 
localization_priority: Normal
ms.assetid: 53406fb8-4ca5-4204-a6ad-b21ca9e6a100
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Worksheet References

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
A reference in Microsoft Excel is a data type that refers to a rectangular block of cells (which can be just one cell), or in some cases, a number of disjoint blocks of cells. Internally, Excel uses one reference type for cells on the current sheet, known as an internal reference. Any cell that is not on the current sheet is described by another type of reference known as an external reference. See the next section for the definition of active and current.
  
## Active vs. Current

In Excel, the term active refers to what the user is viewing. The active workbook and worksheet are those that the user is currently looking at, or, if Excel has lost focus to another application, was looking at when Excel last had focus. The active sheet is always in the active workbook. The one or more cells that are selected in the active sheet are known as the active cells. If an embedded object has focus, the last-selected cells are still active. 
  
The term current refers to what Excel is recalculating. The current workbook and worksheet are those that are currently being recalculated. The current sheet is always in the current workbook. The cell being recalculated is known as the current cell, or, in the case of an array formula being recalculated, the current cells. 
  
The important points to remember are as follows:
  
- The active workbook/worksheet/cell is not generally the current one, although it can be.
    
- An add-in function, whether in a Visual Basic for Applications (VBA) module or a DLL or XLL, is always called from the current cell on the current sheet, or one of them in the case of multithreaded recalculation (MTR).
    
Many Excel functions that provide information about a cell, a range of cells, or a sheet in a workbook distinguish between the active workbook, sheet, or cell and the current workbook, sheet, or cell. This difference is reflected in the data types used to describe references to blocks of cells, as described in the following section.
  
## Internal and External Worksheet References

The key difference between internal and external references is that the external reference data type contains an ID for the worksheet and also a description of which cells are referred to. An internal reference contains no reference to the sheet—it is implicit that the sheet is the current sheet. 
  
Many C API functions return references or take reference arguments. Any C API function that takes reference arguments accepts either internal or external references, except the **xlSheetNm** function, which requires an external reference. Some functions only return either internal or external references. For example, the C API function [xlfCaller](xlfcaller.md) returns a reference to the calling cells, by definition, on the current sheet. The returned reference is always an internal reference, although the function can return non-reference types where the function is not called from a worksheet cell. The C API function [xlSheetId](xlsheetid.md) always returns the ID of a worksheet contained within an external reference data type. 
  
The other key difference between the internal and external reference types is that the external reference data type can describe multiple disjoint blocks of cells on the same sheet. Internal references can describe only a single block on the current sheet. Disjoint references can be passed to any function that takes a range argument.
  
## See also

#### Concepts

[Excel Programming Concepts](excel-programming-concepts.md)
  
[Evaluating Names and Other Worksheet Formula Expressions](evaluating-names-and-other-worksheet-formula-expressions.md)
  
[Excel Worksheet and Expression Evaluation](excel-worksheet-and-expression-evaluation.md)

