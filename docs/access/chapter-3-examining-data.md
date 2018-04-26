---
title: "Chapter 3 Examining Data"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 73c69134-3127-3344-d5c3-5ecb9e0e958b
description: "Chapter 2 explained how to retrieve data from a data source as a Recordset object. This chapter will discuss the Recordset in more detail, including how to navigate through the Recordset and view its data."
---

# Chapter 3: Examining Data

Chapter 2 explained how to retrieve data from a data source as a **Recordset** object. This chapter will discuss the **Recordset** in more detail, including how to navigate through the **Recordset** and view its data. 
  
 **Recordsets** have methods and properties designed to make it easy to move through them and examine their contents. Depending on the functionality supported by the provider, some **Recordset** methods or properties might not be available. To continue exploring the **Recordset** object, consider a **Recordset** that would be returned from the Northwind sample database on Microsoft SQL Server 2000, using the following code: 
  
```
 
'BeginRsTour 
Public Sub RecordsetTour() 
 On Error GoTo ErrHandler: 
 
 Dim objRs As New ADODB.Recordset 
 Dim strSQL As String 
 
 strSQL = "SELECT ProductID, ProductName, UnitPrice FROM Products " &amp; _ 
 "WHERE CategoryID = 7" '7 = Produce 
 
 objRs.Open strSQL, strConnStr, adOpenForwardOnly, _ 
 adLockReadOnly, adCmdText 
 
 'Clean up 
 objRs.Close 
 Set objRs = Nothing 
 Exit Sub 
 
ErrHandler: 
 If Not objRs Is Nothing Then 
 If objRs.State = adStateOpen Then objRs.Close 
 Set objRs = Nothing 
 End If 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
'EndRsTour 

```

This SQL query returns a **Recordset** with five rows (records) and three columns (fields). The values for each row are shown in the following table. 
  
|**FIELD 0          Name = ProductID**|**FIELD 1          Name = ProductName**|**FIELD 2          Name = UnitPrice**|
|:-----|:-----|:-----|
|7  <br/> |Uncle Bob's Organic Dried Pears  <br/> |30.0000  <br/> |
|14  <br/> |Tofu  <br/> |23.2500  <br/> |
|28  <br/> |Rssle Sauerkraut  <br/> |45.6000  <br/> |
|51  <br/> |Manjimup Dried Apples  <br/> |53.0000  <br/> |
|74  <br/> |Longlife Tofu  <br/> |10.0000  <br/> |
   
The next section will explain how to locate the current position of the cursor in this sample **Recordset**. 
  

