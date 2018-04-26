---
title: "Creating and Executing a Simple Command"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 9ace1abe-cfae-0677-bc57-5cbda85b79db
description: "Though not a typical usage of the Command object, the following code shows the basic method of using the Command object to execute a command against a data source. In this case, it is a row-returning command, so it returns the results of the command execution into a Recordset object."
---

# Creating and Executing a Simple Command

Though not a typical usage of the **Command** object, the following code shows the basic method of using the **Command** object to execute a command against a data source. In this case, it is a row-returning command, so it returns the results of the command execution into a **Recordset** object. 
  
```
 
 'BeginBasicCmd 
 On Error GoTo ErrHandler: 
 
 Dim objConn As New ADODB.Connection 
 Dim objCmd As New ADODB.Command 
 Dim objRs As New ADODB.Recordset 
 
 objCmd.CommandText = "SELECT OrderID, OrderDate, " &amp; _ 
 "RequiredDate, ShippedDate " &amp; _ 
 "FROM Orders " &amp; _ 
 "WHERE CustomerID = 'ALFKI' " &amp; _ 
 "ORDER BY OrderID" 
 objCmd.CommandType = adCmdText 
 
 ' Connect to the data source. 
 Set objConn = GetNewConnection 
 objCmd.ActiveConnection = objConn 
 
 ' Execute once and display... 
 Set objRs = objCmd.Execute 
 
 Debug.Print "ALFKI" 
 Do While Not objRs.EOF 
 Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _ 
 objRs(2) &amp; vbTab &amp; objRs(3) 
 objRs.MoveNext 
 Loop 
 
 'clean up 
 objRs.Close 
 objConn.Close 
 Set objRs = Nothing 
 Set objConn = Nothing 
 Set objCmd = Nothing 
 Exit Sub 
 
ErrHandler: 
 'clean up 
 If objRs.State = adStateOpen Then 
 objRs.Close 
 End If 
 
 If objConn.State = adStateOpen Then 
 objConn.Close 
 End If 
 
 Set objRs = Nothing 
 Set objConn = Nothing 
 Set objCmd = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
'EndBasicCmd 

```

The command to be executed is specified with the **CommandText** property. 
  
> [!NOTE]
> Several examples in this section call a utility function, GetNewConnection, to establish a connection with the data provider. To avoid redundancy, it is listed only once, here: 
  
```
 
'BeginNewConnection 
Private Function GetNewConnection() As ADODB.Connection 
 Dim oCn As New ADODB.Connection 
 Dim sCnStr As String 
 
 sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" &amp; _ 
 "Integrated Security='SSPI';Database='Northwind';" 
 oCn.Open sCnStr 
 
 If oCn.State = adStateOpen Then 
 Set GetNewConnection = oCn 
 End If 
 
End Function 
'EndNewConnection 

```


