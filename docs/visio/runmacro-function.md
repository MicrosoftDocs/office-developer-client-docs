---
title: "RUNMACRO Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033809
 
ms.localizationpriority: medium
ms.assetid: 86b0f071-5e0b-56de-ff5b-63c114ad823a
description: "Calls a macro in a Microsoft Visual Basic for Applications (VBA) project."
---

# RUNMACRO Function

Calls a macro in a Microsoft Visual Basic for Applications (VBA) project. 
  
## Syntax

RUNMACRO (** *macroname* ** [, ** *projname_opt* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _macroname_ <br/> |Required  <br/> |**String** <br/> |The name of the macro to call. |
| _projname_opt_ <br/> |Optional  <br/> |**String** <br/> | The project that contains the macro. |
   
## Remarks

If a project is specified, Microsoft Visio scans all open documents for the one containing  _projname_opt_ and calls  _macroname_ in that project. If  _projname_opt_ is omitted or null (""),  _macroname_ is assumed to be in the VBA project of the document that contains the RUNMACRO formula being evaluated. 
  
The RUNMACRO function differs from the CALLTHIS function in that it does not pass a reference to the shape that owns the formula being evaluated to  _macroname_. Like CALLTHIS, the RUNMACRO function doesn't require a reference to  _projname_opt_ to call into it. 
  
 VBA code that is invoked when the Visio instance evaluates a RUNMACRO function in a formula should not close the document containing the cell using the function because an application error results and Visio terminates. 
  
If you need to close the document containing the cell that uses the RUNMACRO function, use one of the following techniques:
  
- Close the document from code that is not VBA.
    
- Close the document from a project other than the one that is closing.
    
- Post window messages to close windows in the document rather than closing the document.
    
For more information about running code in Visio, see [About security settings and running code in Visio](about-security-settings-and-running-code-in-visio-shapesheet.md) in this ShapeSheet Reference. 
  
## Example

The following example invokes a macro called MyTest in the ThisDocument class module of the VBA project containing the RUNMACRO formula. 
  
RUNMACRO ("ThisDocument.MyTest") 
  

