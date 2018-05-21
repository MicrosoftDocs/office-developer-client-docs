---
title: "RUNADDON Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251492
 
localization_priority: Normal
ms.assetid: 122c1d30-3cb9-7e7d-b4cc-e93ab8e4da4f
description: "Executes an add-on or a macro in a Microsoft Visual Basic for Applications (VBA) project."
---

# RUNADDON Function

Executes an add-on or a macro in a Microsoft Visual Basic for Applications (VBA) project. 
  
## Syntax

RUNADDON(" *string*  ") 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _string_ <br/> |Required  <br/> |**String** <br/> | The name of an add-on in the **Addons** collection or a macro in a VBA project.  <br/> |
   
## Remarks

If the project of the document that contains the RUNADDON function call (or another project if it is referenced) does not have a macro (a procedure with no arguments) named  _string_, Microsoft Visio runs the add-on named  _string_. If no add-on named  _string_ can be found, Visio does nothing and reports no error. (You can use the **TraceFlags** property to monitor the procedures and add-ons that Visio attempts to run.) 
  
When you call a procedure in a standard module, it is recommended that you prefix the string with the module name that contains the procedure (for example,  *moduleName.procName*), because more than one module can have a procedure with the same name. 
  
To call a procedure in a project other than the project of the document that contains the RUNADDON function call, use the syntax  *projName.modName.procName*  (you must have explicitly set a reference to  *projName*  in your VBA project). 
  
> [!NOTE]
>  Beginning with Visio 2002, the RUNADDON function cannot execute a string containing arbitrary VBA code. Code that was formerly passed to the RUNADDON function can be moved to a procedure in a document's VBA project that is called from the RUNADDON function. 
  
For more information about running code in Visio, see [About Security Settings and Running Code in Visio](about-security-settings-and-running-code-in-visio-shapesheet.md) in this ShapeSheet Reference. 
  
In earlier versions of Visio, this function appears as _RUNADDON. Visio versions 4.0 and later accept either style. 
  
## Example 1

RUNADDON("Calendar.exe")
  
Launches an add-on called Calendar.exe.
  
## Example 2

RUNADDON("Array Shapes")
  
Launches the (VSL-implemented) add-on whose name is Array Shapes.
  
## Example 3

RUNADDON("ThisDocument.ReportStatistics")
  
Calls the ReportStatistics macro in the **ThisDocument** module in the document project containing this function call. 
  
> [!NOTE]
>  To invoke a macro in the **ThisDocument** module, you must preface the string with "ThisDocument" as shown. 
  
## Example 4

RUNADDON(" *ModuleName*  .ReportStatistics") 
  
Calls the ReportStatistics macro in  *ModuleName*  in the document project that contains this function call. 
  

