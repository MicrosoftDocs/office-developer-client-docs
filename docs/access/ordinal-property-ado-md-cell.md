---
title: "Ordinal Property (ADO MD Cell)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: be705823-6c5e-0c8f-f780-87df19423a72

---

# Ordinal Property (ADO MD Cell)

Uniquely identifies a cell by its position within a cellset.
  
## Return Values

Returns a **Long** integer and is read-only. 
  
## Remarks

The cell's ordinal value uniquely identifies the cell within a cellset. Conceptually, cells are numbered in a cellset as if the cellset were a  *p*  -dimensional array, where  *p*  is the number of [axes](axes-collection-ado-md.md). Cells are numbered starting from zero in row-major order. 
  
The cell's ordinal value can be used with the [Item](item-property-ado-md-cellset.md) property of the [Cellset](cellset-object-ado-md.md) object to quickly retrieve the [Cell](cell-object-ado-md.md).
  

