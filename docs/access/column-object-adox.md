---
title: "Column Object (ADOX)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: ad38c2df-f704-0599-4b7a-8556e430ba46
---

# Column Object (ADOX)

Represents a column from a table, index, or key.
  
## Remarks

The following code creates a new **Column**: 
  
```
Dim obj As New Column

```

With the properties and collections of a **Column** object, you can: 
  
- Identify the column with the [Name](name-property-adox.md) property. 
    
- Specify the data type of the column with the [Type](http://msdn.microsoft.com/library/3e222e89-f57e-28f9-8488-81828f882643%28Office.15%29.aspx) property. 
    
- Determine if the column is fixed-length, or if it can contain null values with the [Attributes](attributes-property-adox.md) property. 
    
- Specify the maximum size of the column with the [DefinedSize](definedsize-property-adox.md) property. 
    
- For numeric data values, specify the scale with the [NumericScale](numericscale-property-adox.md) property. 
    
- For numeric data value, specify the maximum precision with the [Precision](precision-property-adox.md) property. 
    
- Specify the [Catalog](catalog-object-adox.md) that owns the column with the [ParentCatalog](parentcatalog-property-adox.md) property. 
    
- For key columns, specify the name of the related column in the related table with the [RelatedColumn](relatedcolumn-property-adox.md) property. 
    
- For index columns, specify whether the sort order is ascending or descending with the [SortOrder](sortorder-property-adox.md) property. 
    
- Access provider-specific properties with the [Properties](properties-collection-ado.md) collection. 
    
> [!NOTE]
> Not all properties of **Column** objects may be supported by your data provider. An error will occur if you have set a value for a property that the provider does not support. For new **Column** objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property. 
  
When creating **Column** objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation. 
  

