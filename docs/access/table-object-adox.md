---
title: "Table Object (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 53a3e2f9-4ec0-8fed-d482-4f995921587b

---

# Table Object (ADOX)

Represents a database table including columns, indexes, and keys.
  
## Remarks

The following code creates a new **Table**: 
  
```
Dim obj As New Table

```

With the properties and collections of a **Table** object, you can: 
  
- Identify the table with the [Name](name-property-adox.md) property. 
    
- Determine the type of table with the [Type](http://msdn.microsoft.com/library/d07cdfc1-da65-74b7-ab9c-f2b79f24b59e%28Office.15%29.aspx) property. 
    
- Access the database columns of the table with the [Columns](columns-collection-adox.md) collection. 
    
- Access the indexes of the table with the [Indexes](indexes-collection-adox.md) collection. 
    
- Access the keys of the table with the [Keys](keys-collection-adox.md) collection. 
    
- Specify the [Catalog](catalog-object-adox.md) that owns the table with the [ParentCatalog](parentcatalog-property-adox.md) property. 
    
- Return date information with the [DateCreated](datecreated-property-adox.md) and [DateModified](datemodified-property-adox.md) properties. 
    
- Access provider-specific table properties with the [Properties](properties-collection-ado.md) collection. 
    
> [!NOTE]
> Your data provider may not support all properties of **Table** objects. An error will occur if you have set a value for a property that the provider does not support. For new **Table** objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property. 
  
When creating **Table** objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation. 
  

