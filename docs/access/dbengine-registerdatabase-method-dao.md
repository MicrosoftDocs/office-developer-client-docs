---
title: "DBEngine.RegisterDatabase Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052938
  
localization_priority: Normal
ms.assetid: ed87a694-2c89-0a78-5d8b-0cc7e09fadff
description: "Enters connection information for an ODBC data source in the Windows Registry. The ODBC driver needs connection information when the ODBC data source is opened during a session."
---

# DBEngine.RegisterDatabase Method (DAO)

Enters connection information for an ODBC data source in the Windows Registry. The ODBC driver needs connection information when the ODBC data source is opened during a session.
  
## Syntax

 *expression*  . **RegisterDatabase**( ** *Dsn* **, ** *Driver* **, ** *Silent* **, ** *Attributes* ** ) 
  
 *expression*  A variable that represents a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Dsn_ <br/> |Required  <br/> |**String** <br/> |the name used in the **[OpenDatabase](dbengine-opendatabase-method-dao.md)** method. It refers to a block of descriptive information about the data source. For example, if the data source is an ODBC remote database, it could be the name of the server.  <br/> |
| _Driver_ <br/> |Required  <br/> |**String** <br/> | The name of the ODBC driver. This isn't the name of the ODBC driver DLL file.  <br/> |
| _Silent_ <br/> |Required  <br/> |**Boolean** <br/> |**True** if you don't want to display the ODBC driver dialog boxes that prompt for driver-specific information; or **False** if you want to display the ODBC driver dialog boxes. If  _silent_ is **True**,  _attributes_ must contain all the necessary driver-specific information or the dialog boxes are displayed anyway.  <br/> |
| _Attributes_ <br/> |Required  <br/> |**String** <br/> |A list of keywords to be added to the Windows Registry. The keywords are in a carriage-return-delimited string.  <br/> |
   
## Remarks

If the database is already registered (connection information is already entered) in the Windows Registry when you use the **RegisterDatabase** method, the connection information is updated. 
  
If the **RegisterDatabase** method fails for any reason, no changes are made to the Windows Registry, and an error occurs. 
  
For more information about ODBC drivers such as SQL Server, see the Help file provided with the driver.
  
## Example

This example uses the **RegisterDatabase** method to register a Microsoft SQL Server data source named Publishers in the Windows Registry. 
  
```
Sub RegisterDatabaseX() 
 
 Dim dbsRegister As Database 
 Dim strDescription As String 
 Dim strAttributes As String 
 Dim errLoop As Error 
 
 ' Build keywords string. 
 strDescription = InputBox( "Enter a description " &amp; _ 
 "for the database to be registered.") 
 strAttributes = "Database=pubs" &amp; _ 
 vbCr &amp; "Description=" &amp; strDescription &amp; _ 
 vbCr &amp; "OemToAnsi=No" &amp; _ 
 vbCr &amp; "Server=Server1" 
 
 ' Update Windows Registry. 
 On Error GoTo Err_Register 
 DBEngine.RegisterDatabase "Publishers", "SQL Server", _ 
 True, strAttributes 
 On Error GoTo 0 
 
 MsgBox "Use regedit.exe to view changes: " &amp; _ 
 "HKEY_CURRENT_USER\" &amp; _ 
 "Software\ODBC\ODBC.INI" 
 
 Exit Sub 
 
Err_Register: 
 
 ' Notify user of any errors that result from 
 ' the invalid data. 
 If DBEngine.Errors.Count > 0 Then 
 For Each errLoop In DBEngine.Errors 
 MsgBox "Error number: " &amp; errLoop.Number &amp; _ 
 vbCr &amp; errLoop.Description 
 Next errLoop 
 End If 
 
 Resume Next 
 
End Sub 
 
```


