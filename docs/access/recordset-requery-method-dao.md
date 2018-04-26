---
title: "Recordset.Requery Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a5d66eb5-499c-4133-f6c3-c7a1619a8a11
description: "Updates the data in a Recordset object by re-executing the query on which the object is based."
---

# Recordset.Requery Method (DAO)

Updates the data in a **[Recordset](recordset-object-dao.md)** object by re-executing the query on which the object is based. 
  
## Syntax

 *expression*  . **Requery**( ** *NewQueryDef* ** ) 
  
 *expression*  A variable that represents a **Recordset** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _NewQueryDef_ <br/> |Optional  <br/> |**Variant** <br/> | Represents the **Name** property value of a **[QueryDef](querydef-object-dao.md)** object  <br/> |
   
## Remarks

Use this method to make sure that a **Recordset** contains the most recent data. This method re-populates the current **Recordset** by using either the current query parameters or (in a Microsoft Access workspace) the new ones supplied by the  _newquerydef_ argument. 
  
If you don't specify a  _newquerydef_ argument, the **Recordset** is re-populated based on the same query definition and parameters used to originally populate the **Recordset**. Any changes to the underlying data will be reflected during this re-population. If you didn't use a **QueryDef** to create the **Recordset**, the **Recordset** is re-created from scratch. 
  
If you specify the original **QueryDef** in the  _newquerydef_ argument, then the **Recordset** is requeried using the parameters specified by the **QueryDef**. Any changes to the underlying data will be reflected during this re-population. To reflect any changes to the query parameter values in the **Recordset**, you must supply the  _newquerydef_ argument. 
  
If you specify a different **QueryDef** than what was originally used to create the **Recordset**, the **Recordset** is re-created from scratch. 
  
When you use **Requery**, the first record in the **Recordset** becomes the current record. 
  
You can't use the **Requery** method on dynaset- or snapshot-type **Recordset** objects whose **[Restartable](recordset-restartable-property-dao.md)** property is set to **False**. However, if you supply the optional  _newquerydef_ argument, the **Restartable** property is ignored. 
  
If both the **[BOF](recordset-bof-property-dao.md)** and **[EOF](recordset-eof-property-dao.md)** property settings of the **Recordset** object are **True** after you use the **Requery** method, the query didn't return any records and the **Recordset** contains no data. 
  
## Example

This example shows how the **Requery** method can be used to refresh a query after underlying data has been changed. 
  
```
Sub RequeryX() 
 
 Dim dbsNorthwind As Database 
 Dim qdfTemp As QueryDef 
 Dim rstView As Recordset 
 Dim rstChange As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set qdfTemp = dbsNorthwind.CreateQueryDef("", _ 
 "PARAMETERS ViewCountry Text; " &amp; _ 
 "SELECT FirstName, LastName, Country FROM " &amp; _ 
 "Employees WHERE Country = [ViewCountry] " &amp; _ 
 "ORDER BY LastName") 
 
 qdfTemp.Parameters!ViewCountry = "USA" 
 Debug.Print "Data after initial query, " &amp; _ 
 [ViewCountry] = USA" 
 Set rstView = qdfTemp.OpenRecordset 
 Do While Not rstView.EOF 
 Debug.Print " " &amp; rstView!FirstName &amp; " " &amp; _ 
 rstView!LastName &amp; ", " &amp; rstView!Country 
 rstView.MoveNext 
 Loop 
 
 ' Change underlying data. 
 Set rstChange = dbsNorthwind.OpenRecordset("Employees") 
 rstChange.AddNew 
 rstChange!FirstName = "Nina" 
 rstChange!LastName = "Roberts" 
 rstChange!Country = "USA" 
 rstChange.Update 
 
 rstView.Requery 
 Debug.Print "Requery after changing underlying data" 
 Set rstView = qdfTemp.OpenRecordset 
 Do While Not rstView.EOF 
 Debug.Print " " &amp; rstView!FirstName &amp; " " &amp; _ 
 rstView!LastName &amp; ", " &amp; rstView!Country 
 rstView.MoveNext 
 Loop 
 
 ' Restore original data because this is only a 
 ' demonstration. 
 rstChange.Bookmark = rstChange.LastModified 
 rstChange.Delete 
 rstChange.Close 
 
 rstView.Close 
 dbsNorthwind.Close 
 
End Sub 

```

This example shows how the **Requery** method can be used to refresh a query after the query parameters have been changed. 
  
```
Sub RequeryX2() 
 
 Dim dbsNorthwind As Database 
 Dim qdfTemp As QueryDef 
 Dim prmCountry As Parameter 
 Dim rstView As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set qdfTemp = dbsNorthwind.CreateQueryDef("", _ 
 "PARAMETERS ViewCountry Text; " &amp; _ 
 "SELECT FirstName, LastName, Country FROM " &amp; _ 
 "Employees WHERE Country = [ViewCountry] " &amp; _ 
 "ORDER BY LastName") 
 Set prmCountry = qdfTemp.Parameters!ViewCountry 
 
 qdfTemp.Parameters!ViewCountry = "USA" 
 Debug.Print "Data after initial query, " &amp; _ 
 [ViewCountry] = USA" 
 Set rstView = qdfTemp.OpenRecordset 
 Do While Not rstView.EOF 
 Debug.Print " " &amp; rstView!FirstName &amp; " " &amp; _ 
 rstView!LastName &amp; ", " &amp; rstView!Country 
 rstView.MoveNext 
 Loop 
 
 ' Change query parameter. 
 qdfTemp.Parameters!ViewCountry = "UK" 
 ' QueryDef argument must be included so that the 
 ' resulting Recordset reflects the change in the query 
 ' parameter. 
 rstView.Requery qdfTemp 
 Debug.Print "Requery after changing parameter, " &amp; _ 
 "[ViewCountry] = UK" 
 Do While Not rstView.EOF 
 Debug.Print " " &amp; rstView!FirstName &amp; " " &amp; _ 
 rstView!LastName &amp; ", " &amp; rstView!Country 
 rstView.MoveNext 
 Loop 
 
 rstView.Close 
 dbsNorthwind.Close 
 
End Sub 
 
```


