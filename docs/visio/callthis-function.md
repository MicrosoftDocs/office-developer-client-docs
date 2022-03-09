---
title: "CALLTHIS Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251403
 
ms.localizationpriority: medium
ms.assetid: 461abfc1-d2cc-2354-1c2f-395c9e351a78
description: "Calls a procedure in a Microsoft Visual Basic for Applications (VBA) project."
---

# CALLTHIS Function

Calls a procedure in a Microsoft Visual Basic for Applications (VBA) project.
  
## Syntax

CALLTHIS(" ***procedure*** ",[" ***project*** "],[ ***arg1* **, ***arg2* **,...])
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *procedure* <br/> |Required  <br/> |**String** <br/> | The name of the procedure to call. |
| *project* <br/> |Optional  <br/> |**String** <br/> |The project that contains the procedure. |
| *arg* <br/> |Optional  <br/> |**Number, String, Date, or Currency** <br/> |Passed as parameters to the procedure. |

## Remarks

In the VBA project, *procedure* is defined as follows:
  
procedure(*vsoShape* As Visio.Shape [arg1 As type, arg2 As type...])
  
where *vsoShape* is a reference to the **Shape** object that contains the CALLTHIS formula being evaluated, and *arg1*, *arg2* ... are the arguments specified in that formula.
  
Notice that *vsoShape* is very much like the "this" argument passed to a C++ member procedure; hence the name "CALLTHIS." In effect, a cell that contains a formula that includes CALLTHIS can be read as, "Call this procedure and pass it a reference to my shape."
  
If *project* is specified, Microsoft Visio scans all open documents for the one containing *project* and calls *procedure* in that project. If *project* is omitted or null (""), Visio assumes *procedure* is in the VBA project of the document that contains the CALLTHIS formula that is being evaluated.
  
Numbers in  arg1*,*arg2...* are passed in external units. For example, if you pass the value of the Height cell from a shape that is 3 cm tall, 3 is passed. To pass different units with a number, use the FORMATEX function or explicitly coerce units by adding a null number-unit pair, for example, 0 ft + Height.
  
The second comma in the CALLTHIS function is optional. It corresponds to the number of additional parameters added to your procedure. If you do not use any additional parameters, except `(vsoShape as Visio.Shape)`, do not add the second comma; use CALLTHIS("",). If you add two additional parameters, for example, use CALLTHIS("",,,).
  
The CALLTHIS function always evaluates to 0, and the call to *procedure* occurs during idle time after the recalculation process finishes. *Procedure* can return a value, but Visio ignores it. *Procedure* returns a value that Visio can recognize by setting the formula or result of another cell in the document, but not the cell that called *procedure*, unless you want to overwrite the CALLTHIS formula.
  
The CALLTHIS function differs from the RUNADDON function in that a document's project does not need to reference another project in order to call into that project.
  
> [!NOTE]
> VBA code that is invoked when the Visio instance evaluates a CALLTHIS function in a formula should not close the document containing the cell using the function because an application error results and Visio terminates.
  
If you need to close the document containing the cell that uses the CALLTHIS function, use one of the following techniques:
  
- Close the document from code that is not VBA.

- Close the document from a project other than the one that is closing.

- Post window messages to close windows in the document rather than closing the document.

For more information about running code in Visio, see [About Security Settings and Running Code in Visio](about-security-settings-and-running-code-in-visio-shapesheet.md) in this ShapeSheet Reference.
  
## Example 1

CALLTHIS("p",,FORMATEX(Height,"#.00 u",,"cm"))
  
Calls the procedure named p located in a module and passes the value of Height in centimeters, such as 7.62 cm.
  
## Example 2

CALLTHIS("q",,0 cm+Height,Width)
  
Calls the procedure named q located in a module and passes the cell's height in centimeters and width in internal units.
  
## Example 3

Use the following procedure in the *ThisDocument* class module.
  
Use any of the following syntax in a shape's EventDblClick cell with the preceding procedures.
  
CALLTHIS("ThisDocument.A",)
  
CALLTHIS("ThisDocument.B",,"Click")
  
CALLTHIS("ThisDocument.C",,"Click", " OK.")
  