---
title: "Documents Collection (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: ae2fef58-34e7-eea6-ca51-d3903432c7f5
description: "A Documents collection contains all of the Document objects for a specific type of object (Microsoft Access database engine databases only)."
---

# Documents Collection (DAO)

A **Documents** collection contains all of the **Document** objects for a specific type of object (Microsoft Access database engine databases only). 
  
## Remarks

Each **Container** object has a **Documents** collection containing **Document** objects that describe instances of built-in objects of the type specified by the **Container**. 
  
To refer to a **Document** object in a collection by its ordinal number or by its **Name** property setting, use any of the following syntax forms: 
  
- **Documents** (0) 
    
- **Documents** ("  *name*  ") 
    
- **Documents** ![  *name*  ] 
    
## Example

This example enumerates the **Documents** collection of the Tables container, and then enumerates the **Properties** collection of the first **Document** object in the collection. 
  
```
Sub DocumentX() 
 
 Dim dbsNorthwind As Database 
 Dim docLoop As Document 
 Dim prpLoop As Property 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind.Containers!Tables 
 Debug.Print "Documents in " &amp; .Name &amp; " container" 
 ' Enumerate the Documents collection of the Tables 
 ' container. 
 For Each docLoop In .Documents 
 Debug.Print " " &amp; docLoop.Name 
 Next docLoop 
 With .Documents(0) 
 ' Enumerate the Properties collection of the first. 
 ' Document object of the Tables container. 
 Debug.Print "Properties of " &amp; .Name &amp; " document" 
 On Error Resume Next 
 For Each prpLoop In .Properties 
 Debug.Print " " &amp; prpLoop.Name &amp; " = " &amp; _ 
 prpLoop 
 Next prpLoop 
 On Error GoTo 0 
 End With 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 
 
```


