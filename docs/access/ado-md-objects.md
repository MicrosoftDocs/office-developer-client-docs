---
title: "ADO MD Objects"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 13501e44-70b6-1036-a8b7-c276f187e4f4
description: "Also, the Catalog object is connected to an ADO Connection object, which is included with the standard ADO library:"
---

# ADO MD Objects

|||
|:-----|:-----|
|[Axis](axis-object-ado-md.md) <br/> |Represents a positional or filter axis of a cellset, containing selected members of one or more dimensions.  <br/> |
|[Catalog](catalog-object-ado-md.md) <br/> |Contains multidimensional schema information (that is, cubes and underlying dimensions, hierarchies, levels, and members) specific to a multidimensional data provider (MDP).  <br/> |
|[Cell](cell-object-ado-md.md) <br/> |Represents the data at the intersection of axis coordinates, contained in a cellset.  <br/> |
|[Cellset](cellset-object-ado-md.md) <br/> |Represents the results of a multidimensional query. It is a collection of cells selected from cubes or other cellsets.  <br/> |
|[CubeDef](cubedef-object-ado-md.md) <br/> |Represents a cube from a multidimensional schema, containing a set of related dimensions.  <br/> |
|[Dimension](dimension-object-ado-md.md) <br/> |Represents one of the dimensions of a multidimensional cube, containing one or more hierarchies of members.  <br/> |
|[Hierarchy](hierarchy-object-ado-md.md) <br/> |Represents one way in which the members of a dimension can be aggregated or "rolled up." A dimension can be aggregated along one or more hierarchies.  <br/> |
|[Level](level-object-ado-md.md) <br/> |Contains a set of members, each of which has the same rank within a hierarchy.  <br/> |
|[Member](member-object-ado-md.md) <br/> |Represents a member of a level in a cube, the children of a member of a level, or a member of a position along an axis of a cellset.  <br/> |
|[Position](position-object-ado-md.md) <br/> |Represents a set of one or more members of different dimensions that defines a point along an axis.  <br/> |
   
Also, the **Catalog** object is connected to an ADO **Connection** object, which is included with the standard ADO library: 
  
|**Object**|**Description**|
|:-----|:-----|
|[Connection](connection-object-ado.md) <br/> |Represents an open connection to a data source.  <br/> |
   
Many ADO MD objects can be contained in a corresponding collection. For example, a [CubeDef](cubedef-object-ado-md.md) object can be contained in a [CubeDefs](cubedefs-collection-ado-md.md) collection of a **Catalog**. For more information, see [ADO MD Collections](ado-md-collections.md).
  

