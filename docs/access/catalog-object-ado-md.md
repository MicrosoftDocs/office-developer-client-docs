---
title: "Catalog Object (ADO MD)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 708c4082-3589-7f3b-5ea3-f3705f3d3ff1
---

# Catalog Object (ADO MD)

Contains multidimensional schema information (that is, cubes and underlying dimensions, hierarchies, levels, and members) specific to a multidimensional data provider (MDP).
  
## Remarks

With the collections and properties of a **Catalog** object, you can do the following: 
  
- Open the catalog by setting the [ActiveConnection](activeconnection-property-ado-md.md) property to a standard ADO [Connection](connection-object-ado.md) object or to a valid connection string. 
    
- Identify the **Catalog** with the [Name](name-property-ado-md.md) property. 
    
- Iterate through the cubes in a catalog using the [CubeDefs](cubedefs-collection-ado-md.md) collection. 
    

