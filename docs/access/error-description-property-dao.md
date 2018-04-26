---
title: "Error.Description Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053358
  
localization_priority: Normal
ms.assetid: 47a84bec-3258-f2c7-e1af-239da39844dc
description: "Returns a descriptive string associated with an error. This is the default property for the Error object."
---

# Error.Description Property (DAO)

Returns a descriptive string associated with an error. This is the default property for the **Error** object. 
  
## Syntax

 *expression*  . **Description**
  
 *expression*  A variable that represents an **Error** object. 
  
## Remarks

The **Description** property comprises a short description of the error. Use this property to alert the user about an error that you cannot or do not want to handle. 
  
## Example

This example forces an error, traps it, and displays the **Description**, **Number**, **Source**, **HelpContext**, and **HelpFile** properties of the resulting Error object. 
  
```
Sub DescriptionX() 
 
 Dim dbsTest As Database 
 
 On Error GoTo ErrorHandler 
 
 ' Intentionally trigger an error. 
 Set dbsTest = OpenDatabase("NoDatabase") 
 
 Exit Sub 
 
ErrorHandler: 
 Dim strError As String 
 Dim errLoop As Error 
 
 ' Enumerate Errors collection and display properties of 
 ' each Error object. 
 For Each errLoop In Errors 
 With errLoop 
 strError = _ 
 "Error #" &amp; .Number &amp; vbCr 
 strError = strError &amp; _ 
 " " &amp; .Description &amp; vbCr 
 strError = strError &amp; _ 
 " (Source: " &amp; .Source &amp; ")" &amp; vbCr 
 strError = strError &amp; _ 
 "Press F1 to see topic " &amp; .HelpContext &amp; vbCr 
 strError = strError &amp; _ 
 " in the file " &amp; .HelpFile &amp; "." 
 End With 
 MsgBox strError 
 Next 
 
 Resume Next 
 
End Sub 
 
```


