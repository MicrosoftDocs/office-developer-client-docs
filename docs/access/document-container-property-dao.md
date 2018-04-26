---
title: "Document.Container Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053320
  
localization_priority: Normal
ms.assetid: aa1ace1d-f0b8-e0b0-20b6-d3e296254c51
description: "Returns the name of the Container object to which a Document object belongs (Microsoft Access workspaces only). ."
---

# Document.Container Property (DAO)

Returns the name of the **[Container](container-object-dao.md)** object to which a **Document** object belongs (Microsoft Access workspaces only). . 
  
## Syntax

 *expression*  . **Container**
  
 *expression*  A variable that represents a **Document** object. 
  
## Example

This example displays the **Container** property for a variety of **Document** objects. 
  
```
Sub ContainerPropertyX() 
 
 Dim dbsNorthwind As Database 
 Dim ctrLoop As Container 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 ' Display the container name for the first Document 
 ' object in each Container object's Documents collection. 
 For Each ctrLoop In dbsNorthwind.Containers 
 Debug.Print "Document: " &amp; ctrLoop.Documents(0).Name 
 Debug.Print " Container = " &amp; _ 
 ctrLoop.Documents(0).Container 
 Next ctrLoop 
 
 dbsNorthwind.Close 
 
End Sub 
 
```


