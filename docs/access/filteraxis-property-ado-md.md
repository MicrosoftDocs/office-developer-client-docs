---
title: "FilterAxis Property (ADO MD)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 36720d77-4b16-1d17-6d80-d35265f4a8ad

---

# FilterAxis Property (ADO MD)

Indicates filter information about the current cellset.
  
## Return Values

Returns an [Axis](axis-object-ado-md.md) object, and is read-only. 
  
## Remarks

Use the **FilterAxis** property to return information about the dimensions that were used to slice the data. The [DimensionCount](dimensioncount-property-ado-md.md) property of the **Axis** returns the number of slicer dimensions. This axis usually has just one row. 
  
The **Axis** returned by [FilterAxis](filteraxis-property-ado-md.md) is not contained in the [Axes](axes-collection-ado-md.md) collection for a [Cellset](cellset-object-ado-md.md) object. 
  

