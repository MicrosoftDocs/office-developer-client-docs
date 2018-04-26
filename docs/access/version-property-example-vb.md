---
title: "Version Property Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ffb7b04a-55b9-fa2f-41ec-44af225bd15f
description: "This example uses the Version property of a Connection object to display the current ADO version. It also uses several dynamic properties to show:"
---

# Version Property Example (VB)

This example uses the [Version](version-property-ado.md) property of a [Connection](connection-object-ado.md) object to display the current ADO version. It also uses several dynamic properties to show: 
  
- the current DBMS name and version.
    
- OLE DB version.
    
- provider name and version.
    
- ODBC version.
    
- ODBC driver name and version.
    
```
 
'BeginVersionVB 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 Dim Cnxn As ADODB.Connection 
 Dim strCnxn As String 
 Dim strVersionInfo As String 
 
 ' Open connection 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 
 strVersionInfo = "ADO Version: " &amp; Cnxn.Version &amp; vbCr 
 strVersionInfo = strVersionInfo &amp; "DBMS Name: " &amp; Cnxn.Properties("DBMS Name") &amp; vbCr 
 strVersionInfo = strVersionInfo &amp; "DBMS Version: " &amp; Cnxn.Properties("DBMS Version") &amp; vbCr 
 strVersionInfo = strVersionInfo &amp; "OLE DB Version: " &amp; Cnxn.Properties("OLE DB Version") &amp; vbCr 
 strVersionInfo = strVersionInfo &amp; "Provider Name: " &amp; Cnxn.Properties("Provider Name") &amp; vbCr 
 strVersionInfo = strVersionInfo &amp; "Provider Version: " &amp; Cnxn.Properties("Provider Version") &amp; vbCr 
 
 MsgBox strVersionInfo 
 
 ' clean up 
 Cnxn.Close 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
'EndVersionVB 

```


