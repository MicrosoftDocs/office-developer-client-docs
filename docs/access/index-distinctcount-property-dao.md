---
title: "Index.DistinctCount Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053119
  
localization_priority: Normal
ms.assetid: 24cb7247-76b4-1fce-c3c4-892f16634eff
description: "Returns a value that indicates the number of unique values for the Index object that are included in the associated table (Microsoft Access workspaces only)."
---

# Index.DistinctCount Property (DAO)

Returns a value that indicates the number of unique values for the **[Index](index-object-dao.md)** object that are included in the associated table (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **DistinctCount**
  
 *expression*  A variable that represents an **Index** object. 
  
## Remarks

Check the **DistinctCount** property to determine the number of unique values, or keys, in an index. Any key is counted only once, even though there may be multiple occurrences of that value if the index permits duplicate values. This information is useful in applications that attempt to optimize data access by evaluating index information. The number of unique values is also known as the cardinality of an **Index** object. 
  
The **DistinctCount** property won't always reflect the actual number of keys at a particular time. For example, a change caused by a rolled back transaction won't be reflected immediately in the **DistinctCount** property. The **DistinctCount** property value also may not reflect the deletion of records with unique keys. The number will be accurate immediately after you use the **[CreateIndex](tabledef-createindex-method-dao.md)** method. 
  
## Example

This example uses the **DistinctCount** property to show how you can determine the number of unique values in an **Index** object. However, this value is only accurate immediately after creating the **Index**. It will remain accurate if no keys change, or if new keys are added and no old keys are deleted; otherwise, it will not be reliable. (If this procedure is run several times, you can see the effect on the **DistinctCount** property values of the existing Index objects.) 
  
```
Sub DistinctCountX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim idxCountry As Index 
 Dim idxLoop As Index 
 Dim rstEmployees As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind!Employees 
 
 With tdfEmployees 
 ' Create and append new Index object to the Employees 
 ' table. 
 Set idxCountry = .CreateIndex("CountryIndex") 
 idxCountry.Fields.Append _ 
 idxCountry.CreateField("Country") 
 .Indexes.Append idxCountry 
 
 ' The collection must be refreshed for the new 
 ' DistinctCount data to be available. 
 .Indexes.Refresh 
 
 ' Enumerate Indexes collection to show the current 
 ' DistinctCount values. 
 Debug.Print "Indexes before adding new record" 
 For Each idxLoop In .Indexes 
 Debug.Print " DistinctCount = " &amp; _ 
 idxLoop.DistinctCount &amp; ", Name = " &amp; _ 
 idxLoop.Name 
 Next idxLoop 
 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees") 
 
 ' Add a new record to the Employees table. 
 With rstEmployees 
 .AddNew 
 !FirstName = "April" 
 !LastName = "LaMonte" 
 !Country = "Canada" 
 .Update 
 End With 
 
 ' Enumerate Indexes collection to show the modified 
 ' DistinctCount values. 
 Debug.Print "Indexes after adding new record and " &amp; _ 
 "refreshing Indexes" 
 .Indexes.Refresh 
 For Each idxLoop In .Indexes 
 Debug.Print " DistinctCount = " &amp; _ 
 idxLoop.DistinctCount &amp; ", Name = " &amp; _ 
 idxLoop.Name 
 Next idxLoop 
 
 ' Delete new record because this is a demonstration. 
 With rstEmployees 
 .Bookmark = .LastModified 
 .Delete 
 .Close 
 End With 
 
 ' Delete new Indexes because this is a demonstration. 
 .Indexes.Delete idxCountry.Name 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 

```


