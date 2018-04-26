---
title: "Cell Object (ADO MD)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b9d00b71-1f40-5bd1-4b89-fbdb59c552ba
---

# Cell Object (ADO MD)

Represents the data at the intersection of axis coordinates contained in a cellset.
  
## Remarks

A **Cell** object is returned by the [Item](item-property-ado-md-cellset.md) property of a [Cellset](cellset-object-ado-md.md) object. 
  
With the collections and properties of a **Cell** object, you can do the following: 
  
- Return the data in the **Cell** with the [Value](value-property-ado-md.md) property. 
    
- Return the string representing the formatted display of the **Value** property with the [FormattedValue](formattedvalue-property-ado-md.md) property. 
    
- Return the ordinal value of the **Cell** within the **Cellset** with the [Ordinal](ordinal-property-ado-md-cell.md) property. 
    
- Determine the position of the **Cell** within the [CubeDef](cubedef-object-ado-md.md) with the [Positions](positions-collection-ado-md.md) collection. 
    
- Retrieve other information about the **Cell** with the standard ADO [Properties](properties-collection-ado.md) collection. 
    
The **Properties** collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties. 
  
|**Name**|**Description**|
|:-----|:-----|
|BackColor  <br/> |Background color used when displaying the cell.  <br/> |
|FontFlags  <br/> |Bitmask detailing effects on the font.  <br/> |
|FontName  <br/> |Font used to display the cell value.  <br/> |
|FontSize  <br/> |Font size used to display the cell value.  <br/> |
|ForeColor  <br/> |Foreground color used when displaying the cell.  <br/> |
|FormatString  <br/> |Value in a formatted string.  <br/> |
   

