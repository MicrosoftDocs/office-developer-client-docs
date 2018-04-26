---
title: "Dimension Object (ADO MD)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 12f43cfc-c74e-a2e8-7f6e-75fc68472c4b
---

# Dimension Object (ADO MD)

Represents one of the dimensions of a multidimensional cube, containing one or more hierarchies of members.
  
## Remarks

With the collections and properties of a **Dimension** object, you can do the following: 
  
- Identify the **Dimension** with the [Name](name-property-ado-md.md) and [UniqueName](uniquename-property-ado-md.md) properties. 
    
- Return a meaningful string that describes the **Dimension** with the [Description](description-property-ado-md.md) property. 
    
- Return the [Hierarchy](hierarchy-object-ado-md.md) objects that make up the **Dimension** with the [Hierarchies](hierarchies-collection-ado-md.md) collection. 
    
- Use the standard ADO [Properties](properties-collection-ado.md) collection to obtain additional information about the **Dimension** object. 
    
The **Properties** collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties. 
  
|**Name**|**Description**|
|:-----|:-----|
|CatalogName  <br/> |The name of the catalog to which this cube belongs.  <br/> |
|CubeName  <br/> |The name of the cube.  <br/> |
|DefaultHierarchy  <br/> |The unique name of the default hierarchy.  <br/> |
|Description  <br/> |A meaningful description of the cube.  <br/> |
|DimensionCaption  <br/> |A label or caption associated with the dimension.  <br/> |
|DimensionCardinality  <br/> |The number of members in the dimension.  <br/> |
|DimensionGUID  <br/> |The GUID of the dimension.  <br/> |
|DimensionName  <br/> |The name of the dimension.  <br/> |
|DimensionOrdinal  <br/> |The ordinal number of the dimension among the group of dimensions that form the cube.  <br/> |
|DimensionType  <br/> |The dimension type.  <br/> |
|DimensionUniqueName  <br/> |The unambiguous name of the dimension.  <br/> |
|SchemaName  <br/> |The name of the schema to which this cube belongs.  <br/> |
   

