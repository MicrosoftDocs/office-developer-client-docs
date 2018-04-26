---
title: "Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 3c129aec-cd69-5822-4dad-ebef226538e1
---

# Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VB)

This example triggers an error, traps it, and displays the [Description](description-property-ado.md), [HelpContext](helpcontext-helpfile-properties-ado.md), [HelpFile](helpcontext-helpfile-properties-ado.md), [NativeError](nativeerror-property-ado.md), [Number](number-property-ado.md), [Source](source-property-ado-error.md), and [SQLState](sqlstate-property-ado.md) properties of the resulting [Error](error-object-ado.md) object. 
  
```
'BeginDescriptionVB
Public Sub Main()
    Dim Cnxn As ADODB.Connection
    Dim Err As ADODB.Error
    Dim strError As String
    
    On Error GoTo ErrorHandler
    
    ' Intentionally trigger an error
    Set Cnxn = New ADODB.Connection
    Cnxn.Open "nothing"
    
    Set Cnxn = Nothing
    Exit Sub
ErrorHandler:
    ' Enumerate Errors collection and display
    ' properties of each Error object
    For Each Err In Cnxn.Errors
        strError = "Error #" &amp; Err.Number &amp; vbCr &amp; _
            "   " &amp; Err.Description &amp; vbCr &amp; _
            "   (Source: " &amp; Err.Source &amp; ")" &amp; vbCr &amp; _
            "   (SQL State: " &amp; Err.SQLState &amp; ")" &amp; vbCr &amp; _
            "   (NativeError: " &amp; Err.NativeError &amp; ")" &amp; vbCr
        If Err.HelpFile = "" Then
            strError = strError &amp; "   No Help file available"
        Else
            strError = strError &amp; _
               "   (HelpFile: " &amp; Err.HelpFile &amp; ")" &amp; vbCr &amp; _
               "   (HelpContext: " &amp; Err.HelpContext &amp; ")" &amp; _
               vbCr &amp; vbCr
        End If
         
        Debug.Print strError
    Next
    Resume Next
End Sub
'EndDescriptionVB

```


