---
title: "Container Object (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 22e487cd-e966-fe68-fff3-c680b460cbeb
description: "A Container object groups similar types of Document objects together."
---

# Container Object (DAO)

A **Container** object groups similar types of **Document** objects together. 
  
## Remarks

Each **Database** object has a **Containers** collection consisting of built-in **Container** objects. Applications can define their own document types and corresponding containers (Microsoft Access database engine databases only); however, these objects may not always be supported through DAO. 
  
Some of these **Container** objects are defined by the Microsoft Access database engine while others may be defined by other applications. The following table lists the name of each **Container** object defined by the Microsoft Access database engine and what type of information it contains. 
  
|**Container name**|**Contains information about**|
|:-----|:-----|
|Databases  <br/> |Saved databases  <br/> |
|Tables  <br/> |Saved tables and queries  <br/> |
|Relations  <br/> |Saved relationships  <br/> |
   
> [!NOTE]
> Don't confuse the **Container** objects listed in the preceding table with the collections of the same name. The Databases **Container** object refers to all saved database objects, but the **Databases** collection refers only to database objects that are open in a particular workspace. 
  
Each **Container** object has a **Documents** collection containing **Document** objects that describe instances of built-in objects of the type specified by the **Container**. You typically use a **Container** object as an intermediate link to the information in the **Document** object. You can also use the **Containers** collection to set security for all **Document** objects of a given type. 
  
With an existing **Container** object, you can: 
  
- Use the **Name** property to return the predefined name of the **Container** object. 
    
- Use the **Owner** property to set or return the owner of the **Container** object. To set the **Owner** property, you must have write permission for the **Container** object, and you must set the property to the name of an existing **User** or **Group** object. 
    
- Use the **Permissions** and **UserName** properties to set access permissions for the **Container** object; any **Document** object created in the **Documents** collection of a **Container** object inherits these access permission settings. 
    
Because **Container** objects are built-in, you can't create new **Container** objects or delete existing ones. 
  
To refer to a **Container** object in a collection by its ordinal number or by its **Name** property setting, use any of the following syntax forms: 
  
- **Containers** (0) 
    
- **Containers** ("  *name*  ") 
    
- **Containers** ![  *name*  ] 
    
## Example

This example enumerates the **Containers** collection of the Northwind database and the **Properties** collection of each **Container** object in the collection. 
  
```
Sub ContainerObjectX() 
 
 Dim dbsNorthwind As Database 
 Dim ctrLoop As Container 
 Dim prpLoop As Property 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 
 ' Enumerate Containers collection. 
 For Each ctrLoop In .Containers 
 Debug.Print "Properties of " &amp; ctrLoop.Name _ 
 &amp; " container" 
 
 ' Enumerate Properties collection of each 
 ' Container object. 
 For Each prpLoop In ctrLoop.Properties 
 Debug.Print " " &amp; prpLoop.Name _ 
 &amp; " = " prpLoop 
 Next prpLoop 
 
 Next ctrLoop 
 
 .Close 
 End With 
 
End Sub 

```


