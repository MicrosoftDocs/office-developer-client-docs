---
title: "Level Object (ADO MD)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ddbcabce-8777-1068-98a3-be209084f497

---

# Level Object (ADO MD)

Contains a set of members, each of which has the same rank within a hierarchy.
  
## Remarks

With the collections and properties of a **Level** object, you can do the following: 
  
- Identify the **Level** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties. 
    
- Return a string to use when displaying the **Level** with the [Caption](caption-property-ado-md.md) property. 
    
- Return a meaningful string that describes the **Level** with the [Description](description-property-ado-md.md) property. 
    
- Return the [Member](member-object-ado-md.md) objects that make up the **Level** with the [Members](members-collection-ado-md.md) collection. 
    
- Return the number of levels from the root of the **Level** with the [Depth](depth-property-ado-md.md) property. 
    
- Use the standard ADO [Properties](properties-collection-ado.md) collection to obtain additional information about the **Level** object. 
    
The **Properties** collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties. 
  
|**Name**|**Description**|
|:-----|:-----|
|CatalogName  <br/> |The name of the catalog to which this cube belongs.  <br/> |
|CubeName  <br/> |The name of the cube.  <br/> |
|Description  <br/> |A meaningful description of the level.  <br/> |
|DimensionUniqueName  <br/> |The unambiguous name of the [dimension](dimension-object-ado-md.md).  <br/> |
|HierarchyUniqueName  <br/> |The unambiguous name of the hierarchy.  <br/> |
|LevelCaption  <br/> |A label or caption associated with the level.  <br/> |
|LevelCardinality  <br/> |The number of members in the level.  <br/> |
|LevelGUID  <br/> |The GUID of the level.  <br/> |
|LevelName  <br/> |Name of the level.  <br/> |
|LevelNumber  <br/> |The distance between the level and the root of the hierarchy.  <br/> |
|LevelType  <br/> |The type of level.  <br/> |
|LevelUniqueName  <br/> |The unambiguous name of the level.  <br/> |
|SchemaName  <br/> |The name of the schema to which this cube belongs.  <br/> |
   

