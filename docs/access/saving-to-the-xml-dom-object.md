---
title: "Saving to the XML DOM Object"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 3c61fc30-9862-347b-c215-08597eccfead

---

# Saving to the XML DOM Object

## Saving to the XML DOM Object

You can save a **Recordset** in XML format to an instance of an MSXML DOM object, as shown in the following Visual Basic code: 
  
```
 
Dim xDOM As New MSXML.DOMDocument 
Dim rsXML As New ADODB.Recordset 
Dim sSQL As String, sConn As String 
     
sSQL = "SELECT customerid, companyname, contactname FROM customers" 
sConn="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\Program Files" &amp; _ 
        "\Common Files\System\msadc\samples\NWind.mdb" 
rsXML.Open sSQL, sConn 
rsXML.Save xDOM, adPersistADO   'Save Recordset directly into a DOM tree. 
... 

```


