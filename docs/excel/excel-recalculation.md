---
title: "Excel Recalculation"
manager: kelbow
ms.date: 08/22/2018
ms.audience: Developer
ms.topic: overview
keywords:
- forced calculation [excel 2007],selective recalculation [Excel 2007],functions [Excel 2007], volatile,calculation modes,recalculated cells [Excel 2007],dependence [Excel 2007],specified worksheet calculation [Excel 2007],recalculation [Excel 2007],workbook tree rebuild [Excel 2007],range calculation [Excel 2007],Excel recalculation,volatile functions [Excel 2007],functions [Excel 2007], non-volatile,active worksheet calculation [Excel 2007],dirty cells [Excel 2007],non-volatile functions [Excel 2007],forced recalculation [Excel 2007]
 
ms.assetid: b4c38442-42e6-4fd2-a1b0-97cfa3300379
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
localization_priority: Priority
---

# Excel Recalculation

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
The user can trigger recalculation in Microsoft Excel in several ways, for example:
  
- Entering new data (if Excel is in Automatic recalculation mode, described later in this topic).
    
- Explicitly instructing Excel to recalculate all or part of a workbook.
    
- Deleting or inserting a row or column.
    
- Saving a workbook while the **Recalculate before save** option is set. 
    
- Performing certain Autofilter actions.
    
- Double-clicking a row or column divider (in Automatic calculation mode).
    
- Adding, editing, or deleting a defined name.
    
- Renaming a worksheet.
    
- Changing the position of a worksheet in relation to other worksheets.
    
- Hiding or unhiding rows, but not columns.
    
> [!NOTE]
> This topic does not distinguish between the user directly pressing a key or clicking the mouse, and those tasks being done by a command or macro. The user runs the command, or does something to cause the command to run so that it is still considered a user action. Therefore the phrase "the user" also means "the user, or a command or process started by the user." 
  
## Dependence, Dirty Cells, and Recalculated Cells

The calculation of worksheets in Excel can be viewed as a three-stage process:
  
1. Construction of a dependency tree
    
2. Construction of a calculation chain
    
3. Recalculation of cells
    
The dependency tree informs Excel about which cells depend on which others, or equivalently, which cells are precedents for which others. From this tree, Excel constructs a calculation chain. The calculation chain lists all the cells that contain formulas in the order in which they should be calculated. During recalculation, Excel revises this chain if it comes across a formula that depends on a cell that has not yet been calculated. In this case, the cell that is being calculated and its dependents are moved down the chain. For this reason, calculation times can often improve in a worksheet that has just been opened in the first few calculation cycles.
  
When a structural change is made to a workbook, for example, when a new formula is entered, Excel reconstructs the dependency tree and calculation chain. When new data or new formulas are entered, Excel marks all the cells that depend on that new data as needing recalculation. Cells that are marked in this way are known as  *dirty*  . All direct and indirect dependents are marked as dirty so that if B1 depends on A1, and C1 depends on B1, when A1 is changed, both B1 and C1 are marked as dirty. 
  
If a cell depends, directly or indirectly, on itself, Excel detects the circular reference and warns the user. This is usually an error condition that the user must fix, and Excel provides very helpful graphical and navigational tools to help the user to find the source of the circular dependency. In some cases, you might deliberately want this condition to exist. For example, you might want to run an iterative calculation where the starting point for the next iteration is the result of the previous iteration. Excel supports control of iterative calculations through the calculation options dialog box.
  
After marking cells as dirty, when a recalculation is next done, Excel reevaluates the contents of each dirty cell in the order dictated by the calculation chain. In the example given earlier, this means B1 is first, and then C1. This recalculation occurs immediately after Excel finishes marking cells as dirty if the recalculation mode is automatic; otherwise, it occurs later.
  
Starting in Microsoft Excel 2002, the **Range** object in Microsoft Visual Basic for Applications (VBA) supports a method, **Range.Dirty**, which marks cells as needing calculation. When it is used together with the **Range.Calculate** method (see next section), it enables forced recalculation of cells in a given range. This is useful when you are performing a limited calculation during a macro, where the calculation mode is set to manual, to avoid the overhead of calculating cells unrelated to the macro function. Range calculation methods are not available through the C API. 
  
In Excel 2002 and earlier versions, Excel built a calculation chain for each worksheet in each open workbook. This resulted in some complexity in the way links between worksheets were handled, and required some care to ensure efficient recalculation. In particular, in Excel 2000, you should minimize cross-worksheet dependencies and name worksheets in alphabetical order so that sheets that depend on other sheets come alphabetically after the sheets they depend on.
  
In Excel 2007, the logic was improved to enable recalculation on multiple threads so that sections of the calculation chain are not interdependent and can be calculated at the same time. You can configure Excel to use multiple threads on a single processor computer, or a single thread on a multi-processor or multi-core computer. 
  
## Asynchronous User Defined Functions (UDFs)

When a calculation encounters an asynchronous UDF, it saves the state of the current formula, starts the UDF and continues evaluating the rest of the cells. When the calculation finishes evaluating the cells Excel waits for the asynchronous functions to complete if there are still asynchronous functions running. As each asynchronous function reports results, Excel finishes the formula, and then runs a new calculation pass to re-compute cells that use the cell with the reference to the asynchronous function.
  
## Volatile and Non-Volatile Functions

Excel supports the concept of a volatile function, that is, one whose value cannot be assumed to be the same from one moment to the next even if none of its arguments (if it takes any) has changed. Excel reevaluates cells that contain volatile functions, together with all dependents, every time that it recalculates. For this reason, too much reliance on volatile functions can make recalculation times slow. Use them sparingly.
  
The following Excel functions are volatile:
  
- **NOW**
    
- **TODAY**
    
- **RANDBETWEEN**
    
- **OFFSET**
    
- **INDIRECT**
    
- **INFO** (depending on its arguments) 
    
- **CELL** (depending on its arguments) 
    
- **SUMIF** (depending on its arguments) 
    
Both the VBA and C API support ways to inform Excel that a user-defined function (UDF) should be handled as volatile. By using VBA, the UDF is declared as volatile as follows.
  
```vb
Function MyUDF(MakeMeVolatile As Boolean) As Double
   ' Good practice to call this on the first line.
   Application.Volatile (MakeMeVolatile)
   MyUDF = Now
End Function

```

By default, Excel assumes that VBA UDFs are not volatile. Excel only learns that a UDF is volatile when it first calls it. A volatile UDF can be changed back to non-volatile as in this example.
  
Using the C API, you can register an XLL function as volatile before its first call. It also enables you to switch on and off the volatile status of a worksheet function.
  
By default, Excel handles XLL UDFs that take range arguments and that are declared as macro-sheet equivalents as volatile. You can turn this default state off using the **xlfVolatile** function when the UDF is first called. 
  
## Calculation Modes, Commands, Selective Recalculation, and Data Tables

Excel has three calculation modes:
  
- Automatic
    
- Automatic Except Tables
    
- Manual
    
When calculation is set to automatic, recalculation occurs after every data input and after certain events such as the examples given in the previous section. For very large workbooks, recalculation time might be so long that users must limit when this happens, that is, only recalculating when they need to. To enable this, Excel supports the manual mode. The user can select the mode through the Excel menu system, or programmatically using VBA, COM, or the C API.
  
Data tables are special structures in a worksheet. First, the user sets up the calculation of a result on a worksheet. This depends on one or two key changeable inputs and other parameters. The user can then create a table of results for a set of values for one or both of the key inputs. The table is created by using the **Data Table Wizard**. After the table is set up, Excel plugs the inputs one-by-one into the calculation and copies the resulting value into the table. As one or two inputs can be used, data tables can be one- or two-dimensional. 
  
Recalculation of data tables is handled slightly differently:
  
- Recalculation is handled asynchronously to regular workbook recalculation so that large tables might take longer to recalculate than the rest of the workbook.
    
- Circular references are tolerated. If the calculation that is used to get the result depends on one or more values from the data table, Excel does not return an error for the circular dependency. 

- Data tables do not use multi-threaded calculation.
    
Given the different way that Excel handles recalculation of data tables, and the fact that large tables that depend on complex or lengthy calculations can take a long time to calculate, Excel lets you disable the automatic calculation of data tables. To do this, set the calculation mode to Automatic except Data Tables. When calculation is in this mode, the user recalculates the data tables by pressing F9 or some equivalent programmatic operation.
  
Excel exposes methods through which you can alter the recalculation mode and control recalculation. These methods have been improved from version to version to allow for finer control. The capabilities of the C API in this regard reflect those that were available in Excel version 5, and so do not give you the same control that you have using VBA in more recent versions. 
  
Most frequently used when Excel is in manual calculation mode, these methods allow selective calculation of workbooks, worksheets, and ranges, complete recalculation of all open workbooks, and even complete rebuild of the dependency tree and calculation chain.
  
### Range Calculation

Keystroke: None
  
VBA: **Range.Calculate** (introduced in Excel 2000, changed in Excel 2007) and **Range.CalculateRowMajorOrder** (introduced in Excel 2007) 
  
C API: Not supported
  
- **Manual mode**
    
    Recalculates just the cells in the given range regardless of whether they are dirty or not. Behavior of the **Range.Calculate** method changed in Excel 2007; however, the old behavior is still supported by the **Range.CalculateRowMajorOrder** method. 
    
- **Automatic or Automatic Except Tables modes**
    
    Recalculates the workbook but does not force recalculation of the range or any cells in the range.
    
### Active Worksheet Calculation

Keystroke: SHIFT+F9
  
VBA: **ActiveSheet.Calculate**
  
C API: **xlcCalculateDocument**
  
- **All modes**
    
    Recalculates the cells marked for calculation in the active worksheet only.
    
### Specified Worksheet Calculation

Keystroke: None
  
VBA: **Worksheets(**reference **).Calculate**
  
C API: Not supported
  
- **All modes**
    
    Recalculates the dirty cells and their dependents within the specified worksheet only. Reference is the name of the worksheet as a string or the index number in the relevant workbook.
    
    Excel 2000 and later versions expose a **Boolean** worksheet property, the **EnableCalculation** property. Setting this to **True** from **False** dirties all cells in the specified worksheet. In automatic modes, this also triggers a recalculation of the whole workbook. 
    
    In manual mode, the following code causes recalculation of the active sheet only.
    
  ```vb
  With ActiveSheet
    .EnableCalculation = False
    .EnableCalculation = True
    .Calculate
  End With
  
  ```

### Workbook Tree Rebuild and Forced Recalculation

Keystroke: CTRL+ALT+SHIFT+F9 (introduced in Excel 2002)
  
VBA: **Workbooks(**reference **).ForceFullCalculation** (introduced in Excel 2007) 
  
C API: Not supported
  
- **All modes**
    
    Causes Excel to rebuild the dependency tree and the calculation chain for a given workbook and forces a recalculation of all cells that contain formulas.
    
### All Open Workbooks

Keystroke: F9
  
VBA: **Application.Calculate**
  
C API: **xlcCalculateNow**
  
- **All modes**
    
    Recalculates all cells that Excel has marked as dirty, that is, dependents of volatile or changed data, and cells programmatically marked as dirty. If the calculation mode is Automatic Except Tables, this calculates those tables that require updating and also all volatile functions and their dependents.
    
### All Open Workbooks Tree Rebuild and Forced Calculation

Keystroke: CTRL+ALT+F9
  
VBA: **Application.CalculateFull**
  
C API: Not supported
  
- **All modes**
    
    Recalculates all cells in all open workbooks. If the calculation mode is Automatic Except Tables, it forces the tables to be recalculated.
    
## See also



[Multithreaded Recalculation in Excel](multithreaded-recalculation-in-excel.md)
  
[Data Types Used by Excel](data-types-used-by-excel.md)
  
[Memory Management in Excel](memory-management-in-excel.md)
  
[Excel Programming Concepts](excel-programming-concepts.md)

