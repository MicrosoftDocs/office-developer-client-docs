---
title: "Step 6 Changes are Sent to the Server (RDS Tutorial)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c5915d89-77b6-bb3f-a962-49378160751f
description: "If the Recordset object is edited, any changes (that is, rows that are added, changed, or deleted) can be sent back to the server."
---

# Step 6: Changes are Sent to the Server (RDS Tutorial)

If the **Recordset** object is edited, any changes (that is, rows that are added, changed, or deleted) can be sent back to the server. 
  
> [!NOTE]
> The default behavior of RDS can be invoked implicitly with ADO objects and the Microsoft OLE DB Remoting Provider. Queries can return **Recordset** s, and edited **Recordset** s can update the data source. This tutorial does not invoke RDS with ADO objects, but this is how it would look if it did: 
  
```
 
Dim rs as New ADODB.Recordset 
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" &amp; _ 
 "Remote Server=http://yourServer;Remote Provider=SQLOLEDB;" 
... ' Edit the Recordset. 
rs.UpdateBatch ' The equivalent of SubmitChanges. 
... 

```

 **Part A** Assume for this case that you have only used the [RDS.DataControl](datacontrol-object-rds.md) and that a **Recordset** object is now associated with the **RDS.DataControl**. The [SubmitChanges](submitchanges-method-rds.md) method updates the data source with any changes to the **Recordset** object if the [Server](server-property-rds.md) and [Connect](connect-property-rds.md) properties are still set. 
  
```
 
Sub RDSTutorial6A() 
Dim DC as New RDS.DataControl 
Dim RS as ADODB.Recordset 
DC.Server = "http://yourServer" 
DC.Connect = "DSN=Pubs" 
DC.SQL = "SELECT * FROM Authors" 
DC.Refresh 
... 
Set RS = DC.Recordset 
 ' Edit the Recordset. 
... 
DC.SubmitChanges 
... 

```

 **Part B** Alternatively, you could update the server with the [RDSServer.DataFactory](datafactory-object-rdsserver.md) object, specifying a connection and a **Recordset** object. 
  
```
 
Sub RDSTutorial6B() 
Dim DS As New RDS.DataSpace 
Dim RS As ADODB.Recordset 
Dim DC As New RDS.DataControl 
Dim DF As Object 
Dim blnStatus As Boolean 
Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer") 
Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors") 
DC.SourceRecordset = RS ' Visual controls can now bind to DC. 
 ' Edit the Recordset. 
blnStatus = DF.SubmitChanges "DSN=Pubs", RS 
End Sub 

```

 **This is the end of the tutorial.**
  

