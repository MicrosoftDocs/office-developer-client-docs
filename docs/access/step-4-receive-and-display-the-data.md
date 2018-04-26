---
title: "Step 4 Receive and Display the Data"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a27cc1d8-0ee0-95a5-ad70-88c454c10485

---

# Step 4: Receive and Display the Data

## Step 4: Receive and Display the Data

In this step you will create an HTML file with an embedded [RDS.DataControl](datacontrol-object-rds.md) object that points at the XMLResponse.asp file to get the **Recordset**. Open default.htm with a text editor, such as Windows Notepad, and add the code below. Replace "sqlserver" in the URL with the name of your server computer. 
  
```
 
<HTML> 
<HEAD><TITLE>ADO Recordset Persistence Sample</TITLE></HEAD> 
<BODY> 
 
<TABLE DATASRC="#RDC1" border="1"> 
  <TR> 
<TD><SPAN DATAFLD="title"></SPAN></TD> 
<TD><SPAN DATAFLD="price"></SPAN></TD> 
  </TR> 
</TABLE> 
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1"> 
   <PARAM NAME="URL" VALUE="XMLResponse.asp"> 
</OBJECT> 
 
</BODY> 
</HTML> 

```

Close the default.htm file and save it to the same folder where you saved XMLResponse.asp. Using Internet Explorer 4.0 or later, open the URL http:// *sqlserver*  /XMLPersist/default.htm and observe the results. The data is displayed in a bound DHTML table. Now open the URL http://  *sqlserver*  /XMLPersist/XMLResponse.asp and observe the results. The XML is displayed. 
  

