---
title: 'Step 2: Get the Data'
TOCTitle: 'Step 2: Get the Data'
ms:assetid: e6be8801-6e57-d287-e8d2-348963706edc
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250171(v=office.15)
ms:contentKeyID: 48548387
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Step 2: Get the Data


**Applies to**: Access 2013 | Office 2013

## Step 2: Get the Data

In this step, you will write the code to open an ADO **Recordset** and prepare to send it to the client. Open the file XMLResponse.asp with a text editor, such as Windows Notepad, and insert the following code:

```vb 
 
<%@ language="VBScript" %> 
 
<!-- #include file='adovbs.inc' --> 
 
<% 
  Dim strSQL, strCon 
  Dim adoRec  
  Dim adoCon  
  Dim xmlDoc  
 
  ' You will need to change "slqServer" below to the name of the SQL  
  ' server machine to which you want to connect. 
  strCon = "Provider=sqloledb;Data Source=sqlServer;Initial Catalog=Pubs;Integrated Security=SSPI;" 
  Set adoCon = server.createObject("ADODB.Connection") 
  adoCon.Open strCon 
 
  strSQL = "SELECT Title, Price FROM Titles ORDER BY Price" 
  Set adoRec = Server.CreateObject("ADODB.Recordset") 
  adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText 
```

Be sure to change the value of the Data Source parameter in parameter in strCon to the name of your Microsoft SQL Server computer.

Keep the file open and go on to the next step.

**Next** [Step 3: Send the Data](step-3-send-the-data.md)

