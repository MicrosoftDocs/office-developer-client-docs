---
title: "ActiveCommand Property Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 831032cb-d557-aa98-5637-07bad65f924a
description: "This example demonstrates the ActiveCommand property."
---

# ActiveCommand Property Example (VB)

This example demonstrates the [ActiveCommand](activecommand-property-ado.md) property. 
  
A subroutine is given a [Recordset](recordset-object-ado.md) object whose **ActiveCommand** property is used to display the command text and parameter that created the **Recordset**. 
  
```
 
'BeginActiveCommandVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'recordset and connection variables 
 Dim cmd As ADODB.Command 
 Dim rst As ADODB.Recordset 
 Dim Cnxn As ADODB.Connection 
 Dim strCnxn As String 
 'record variables 
 Dim strPrompt As String 
 Dim strName As String 
 
 Set Cnxn = New ADODB.Connection 
 Set cmd = New ADODB.Command 
 
 strPrompt = "Enter an author's name (e.g., Ringer): " 
 strName = Trim(InputBox(strPrompt, "ActiveCommandX Example")) 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 
 'create SQL command string 
 cmd.CommandText = "SELECT * FROM Authors WHERE au_lname = ?" 
 cmd.Parameters.Append cmd.CreateParameter("LastName", adChar, adParamInput, 20, strName) 
 
 Cnxn.Open strCnxn 
 cmd.ActiveConnection = Cnxn 
 
 'create the recordset by executing command string 
 Set rst = cmd.Execute(, , adCmdText) 
 'see the results 
 Call ActiveCommandXprint(rst) 
 
 ' clean up 
 Cnxn.Close 
 Set rst = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rst Is Nothing Then 
 If rst.State = adStateOpen Then rst.Close 
 End If 
 Set rst = Nothing 
 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
'EndActiveCommandVB 

```

The **ActiveCommandXprint** routine is given only a **Recordset** object, yet it must print the command text and parameter that created the **Recordset**. This can be done because the **Recordset** object's **ActiveCommand** property yields the associated [Command](command-object-ado.md) object. 
  
The **Command** object's [CommandText](commandtext-property-ado.md) property yields the parameterized command that created the **Recordset**. The **Command** object's [Parameters](parameters-collection-ado.md) collection yields the value that was substituted for the command's parameter placeholder (" **?** "). 
  
Finally, an error message or the author's name and ID are printed.
  
```
 
'BeginActiveCommandPrintVB 
Public Sub ActiveCommandXprint(rstp As ADODB.Recordset) 
 
 Dim strName As String 
 
 strName = rstp.ActiveCommand.Parameters.Item("LastName").Value 
 
 Debug.Print "Command text = '"; rstp.ActiveCommand.CommandText; "'" 
 Debug.Print "Parameter = '"; strName; "'" 
 
 If rstp.BOF = True Then 
 Debug.Print "Name = '"; strName; "', not found." 
 Else 
 Debug.Print "Name = '"; rstp!au_fname; " "; rstp!au_lname; _ 
 "', author ID = '"; rstp!au_id; "'" 
 End If 
 
 rstp.Close 
 Set rstp = Nothing 
End Sub 
'EndActiveCommandPrintVB 

```


