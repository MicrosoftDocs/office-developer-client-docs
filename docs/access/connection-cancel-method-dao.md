---
title: "Connection.Cancel Method (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 43ad7b64-823d-3fac-e4d4-5e9514f60011
---

# Connection.Cancel Method (DAO)

## Syntax

 *expression*  . **Cancel**
  
 *expression*  A variable that represents a **Connection** object. 
  
## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the  _dbRunAsync_ option). **Cancel** will return a run-time error if  _dbRunAsync_ was not used in the method you're trying to terminate. 
  
An error will occur if, following a **Cancel** method call, you try to reference the object that would have been created by an asynchronous **OpenConnection** call (that is, the **Connection** object from which you called the **Cancel** method). 
  
## Example

This example uses the **StillExecuting** property and the **Cancel** method to asynchronously open a **Connection** object. 
  
```
Sub CancelConnectionX() 
 
 Dim wrkMain As Workspace 
 Dim conMain As Connection 
 Dim sngTime As Single 
 
 Set wrkMain = CreateWorkspace("ODBCWorkspace", _ 
 "admin", "", dbUseODBC) 
 ' Open the connection asynchronously. 
 
 ' Note: The DSN referenced below must be configured to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the Microsoft SQL Server. 
 Set conMain = wrkMain.OpenConnection("Publishers", _ 
 dbDriverNoPrompt + dbRunAsync, False, _ 
 "ODBC;DATABASE=pubs;DSN=Publishers") 
 
 sngTime = Timer 
 
 ' Wait five seconds. 
 Do While Timer - sngTime < 5 
 Loop 
 
 ' If the connection has not been made, ask the user 
 ' if she wants to keep waiting. If she does not, cancel 
 ' the connection and exit the procedure. 
 Do While conMain.StillExecuting 
 
 If MsgBox("No connection yet--keep waiting?", _ 
 vbYesNo) = vbNo Then 
 conMain.Cancel 
 MsgBox "Connection cancelled!" 
 wrkMain.Close 
 Exit Sub 
 End If 
 
 Loop 
 
 With conMain 
 ' Use the Connection object conMain. 
 .Close 
 End With 
 
 wrkMain.Close 
 
End Sub 

```


