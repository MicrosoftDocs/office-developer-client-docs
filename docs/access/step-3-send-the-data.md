---
title: "Step 3 Send the Data"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d22ffe59-179b-fd1a-1211-be1a0d76b02f

---

# Step 3: Send the Data

## Step 3: Send the Data

Now that you have a **Recordset**, you need to send it to the client by saving it as XML to the ASP **Response** object. Add the following code to the bottom of XMLResponse.asp: 
  
```
 
  Response.ContentType = "text/xml" 
  Response.Expires = 0 
  Response.Buffer = False 
 
  Response.Write "<?xml version='1.0'?>" &amp; vbNewLine 
  adoRec.save Response, adPersistXML 
  adoRec.Close 
  Set adoRec=Nothing 
%> 

```

Notice that the ASP **Response** object is specified as the destination for the **Recordset**[Save](save-method-ado.md) method. The destination of the **Save** method can be any object that supports the **IStream** interface, such as an ADO [Stream](stream-object-ado.md) object, or a file name that includes the complete path to which the **Recordset** is to be saved. 
  
Save and close XMLResponse.asp before going to the next step. Also copy the adovbs.inc file from C:\Program Files\Common Files\System\Ado folder to the same folder where you have the XMLResponse.asp file.
  
 **Next**[Step 4: Receive the Data](step-4-receive-and-display-the-data.md)
  

