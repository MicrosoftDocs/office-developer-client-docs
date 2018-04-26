---
title: "CubeDef Object (ADO MD)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 199235b7-3d98-f655-27bc-94f66e994e06
---

# CubeDef Object (ADO MD)

Represents a cube from a multidimensional schema, containing a set of related dimensions.
  
## Remarks

With the collections and properties of a **CubeDef** object, you can do the following: 
  
- Identify a **CubeDef** with the [Name](name-property-ado-md.md) property. 
    
- Return a string that describes the cube with the [Description](description-property-ado-md.md) property. 
    
- Return the dimensions that make up the cube with the [Dimensions](dimensions-collection-ado-md.md) collection. 
    
- Obtain additional information about the **CubeDef** with the standard ADO [Properties](properties-collection-ado.md) collection. 
    
The **Properties** collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties. 
  
|**Name**|**Description**|
|:-----|:-----|
|CatalogName  <br/> |The name of the catalog to which this cube belongs.  <br/> |
|CreatedOn  <br/> |Date and time of cube creation.  <br/> |
|CubeGUID  <br/> |Cube GUID.  <br/> |
|CubeName  <br/> |The name of the cube.  <br/> |
|CubeType  <br/> |The type of the cube.  <br/> |
|DataUpdatedBy  <br/> |User ID of the person doing the last data update.  <br/> |
|Description  <br/> |A meaningful description of the cube.  <br/> |
|LastSchemaUpdate  <br/> |Date and time of last schema update.  <br/> |
|SchemaName  <br/> |The name of the schema to which this cube belongs.  <br/> |
|SchemaUpdatedBy  <br/> |User ID of the person doing the last schema update.  <br/> |
   

