---
title: "GetPermissions and SetPermissions Methods Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 930d9b58-2fc8-efa9-edfe-05ef9039a74d
description: "This example demonstrates the GetPermissions and SetPermissions methods. The following code gives full access for the Orders table to the Admin user."
---

# GetPermissions and SetPermissions Methods Example (VB)

This example demonstrates the [GetPermissions](getpermissions-method-adox.md) and [SetPermissions](setpermissions-method-adox.md) methods. The following code gives full access for the Orders table to the Admin user. 
  
```
 
' BeginGrantPermissionsVB 
Sub GrantPermissions() 
 On Error GoTo GrantPermissionsError 
 
 Dim cnn As New ADODB.Connection 
 Dim cat As New ADOX.Catalog 
 Dim lngPerm As Long 
 
 ' Opens a connection to the northwind database 
 ' using the Microsoft Jet 4.0 provider 
 cnn.Provider = "Microsoft.Jet.OLEDB.4.0" 
 cnn.Open "Data Source='c:\Program Files\" &amp; _ 
 "Microsoft Office\Office\Samples\Northwind.mdb';" &amp; _ 
 "jet oledb:system database=" &amp; _ 
 "'c:\Program Files\Microsoft Office\Office\system.mdw'" 
 
 Set cat.ActiveConnection = cnn 
 
 ' Retrieve original permissions 
 lngPerm = cat.Users("admin").GetPermissions("Orders", adPermObjTable) 
 Debug.Print "Original permissions: " &amp; Str(lngPerm) 
 
 ' Revoke all permissions 
 cat.Users("admin").SetPermissions "Orders", adPermObjTable, _ 
 adAccessRevoke, adRightFull 
 
 ' Display permissions 
 Debug.Print "Revoked permissions: " &amp; _ 
 Str(cat.Users("admin").GetPermissions("Orders", adPermObjTable)) 
 
 ' Give the Admin user full rights on the orders object 
 cat.Users("admin").SetPermissions "Orders", adPermObjTable, _ 
 adAccessSet, adRightFull 
 
 ' Display permissions 
 Debug.Print "Full permissions: " &amp; _ 
 Str(cat.Users("admin").GetPermissions("Orders", adPermObjTable)) 
 
 ' Restore original permissions 
 cat.Users("admin").SetPermissions "Orders", adPermObjTable, _ 
 adAccessSet, lngPerm 
 
 ' Display permissions 
 Debug.Print "Final permissions: " &amp; _ 
 Str(cat.Users("admin").GetPermissions("Orders", adPermObjTable)) 
 
 'Clean up 
 cnn.Close 
 Set cat = Nothing 
 Set cnn = Nothing 
 Exit Sub 
 
GrantPermissionsError: 
 
 Set cat = Nothing 
 
 If Not cnn Is Nothing Then 
 If cnn.State = adStateOpen Then cnn.Close 
 End If 
 Set cnn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
 
End Sub 
' EndGrantPermissionsVB 

```


