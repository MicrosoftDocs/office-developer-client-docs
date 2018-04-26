---
title: "Step 5 DataControl is Made Usable (RDS Tutorial)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9eff5732-2743-6891-dfa6-0991645e17ad
description: "The returned Recordset object is available for use. You can examine, navigate, or edit it as you would any other Recordset . What you can do with the Recordset depends on your environment. Visual Basic and Visual C++ have visual controls that can use a Recordset directly or indirectly with the aid of an enabling data control."
---

# Step 5: DataControl is Made Usable (RDS Tutorial)

The returned **Recordset** object is available for use. You can examine, navigate, or edit it as you would any other **Recordset**. What you can do with the **Recordset** depends on your environment. Visual Basic and Visual C++ have visual controls that can use a **Recordset** directly or indirectly with the aid of an enabling data control. 
  
For example, if you are displaying a Web page in Microsoft Internet Explorer, you might want to display the **Recordset** object data in a visual control. Visual controls on a Web page cannot access a **Recordset** object directly. However, they can access the **Recordset** object through the [RDS.DataControl](datacontrol-object-rds.md). The **RDS.DataControl** becomes usable by a visual control when its [SourceRecordset](recordset-sourcerecordset-properties-rds.md) property is set to the **Recordset** object. 
  
The visual control object must have its **DATASRC** parameter set to the **RDS.DataControl**, and its **DATAFLD** property set to a **Recordset** object field (column). 
  
In this tutorial, set the **SourceRecordset** property: 
  
```
 
Sub RDSTutorial5() 
 Dim DS as New RDS.DataSpace 
 Dim RS as ADODB.Recordset 
 Dim DC as New RDS.DataControl 
 Dim DF as Object 
 Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer") 
 Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors") 
 DC.SourceRecordset = RS ' Visual controls can now bind to DC. 
... 

```


