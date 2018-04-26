---
title: "TableDef.CreateIndex Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052970
  
localization_priority: Normal
ms.assetid: 857b25c1-01fa-b926-0c74-7105e71b7505
description: "Creates a new Index object (Microsoft Access workspaces only). ."
---

# TableDef.CreateIndex Method (DAO)

Creates a new **[Index](index-object-dao.md)** object (Microsoft Access workspaces only). . 
  
## Syntax

 *expression*  . **CreateIndex**( ** *Name* ** ) 
  
 *expression*  A variable that represents a **TableDef** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Optional  <br/> |**Variant** <br/> |A **String** that uniquely names the new **Index** object. See the **Name** property for details on valid **Index** names.  <br/> |
   
### Return Value

Index
  
## Remarks

You can use the **CreateIndex** method to create a new **Index** object for a **TableDef** object. If you omit the optional  _name_ part when you use **CreateIndex**, you can use an appropriate assignment statement to set or reset the **Name** property before you append the new object to a collection. After you append the object, you may or may not be able to set its **Name** property, depending on the type of object that contains the **Indexes** collection. See the **Name** property topic for more details. 
  
If  _name_ refers to an object that is already a member of the collection, a run-time error occurs when you use the **[Append](fields-append-method-dao.md)** method. 
  
To remove an **Index** object from a collection, use the **[Delete](fields-delete-method-dao.md)** method on the collection. 
  
## Example

This example uses the **CreateIndex** method to create two new **Index** objects and then appends them to the **Indexes** collection of the Employees **TableDef** object. It then enumerates the Indexes collection of the **TableDef** object, the **Fields** collection of the new **Index** objects, and the Properties collection of the new **Index** objects. The CreateIndexOutput function is required for this procedure to run. 
  
```
Sub CreateIndexX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim idxCountry As Index 
 Dim idxFirstName As Index 
 Dim idxLoop As Index 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind!Employees 
 
 With tdfEmployees 
 ' Create first Index object, create and append Field 
 ' objects to the Index object, and then append the 
 ' Index object to the Indexes collection of the 
 ' TableDef. 
 Set idxCountry = .CreateIndex("CountryIndex") 
 With idxCountry 
 .Fields.Append .CreateField("Country") 
 .Fields.Append .CreateField("LastName") 
 .Fields.Append .CreateField("FirstName") 
 End With 
 .Indexes.Append idxCountry 
 
 ' Create second Index object, create and append Field 
 ' objects to the Index object, and then append the 
 ' Index object to the Indexes collection of the 
 ' TableDef. 
 Set idxFirstName = .CreateIndex 
 With idxFirstName 
 .Name = "FirstNameIndex" 
 .Fields.Append .CreateField("FirstName") 
 .Fields.Append .CreateField("LastName") 
 End With 
 .Indexes.Append idxFirstName 
 
 ' Refresh collection so that you can access new Index 
 ' objects. 
 .Indexes.Refresh 
 
 Debug.Print .Indexes.Count &amp; " Indexes in " &amp; _ 
 .Name &amp; " TableDef" 
 
 ' Enumerate Indexes collection. 
 For Each idxLoop In .Indexes 
 Debug.Print " " &amp; idxLoop.Name 
 Next idxLoop 
 
 ' Print report. 
 CreateIndexOutput idxCountry 
 CreateIndexOutput idxFirstName 
 
 ' Delete new Index objects because this is a 
 ' demonstration. 
 .Indexes.Delete idxCountry.Name 
 .Indexes.Delete idxFirstName.Name 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 
 
Function CreateIndexOutput(idxTemp As Index) 
 
 Dim fldLoop As Field 
 Dim prpLoop As Property 
 
 With idxTemp 
 ' Enumerate Fields collection of Index object. 
 Debug.Print "Fields in " &amp; .Name 
 For Each fldLoop In .Fields 
 Debug.Print " " &amp; fldLoop.Name 
 Next fldLoop 
 
 ' Enumerate Properties collection of Index object. 
 Debug.Print "Properties of " &amp; .Name 
 For Each prpLoop In .Properties 
 Debug.Print " " &amp; prpLoop.Name &amp; " - " &amp; _ 
 IIf(prpLoop = "", "[empty]", prpLoop) 
 Next prpLoop 
 End With 
 
End Function 

```


