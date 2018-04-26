---
title: "Key Object (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 727198ec-57d2-7766-790c-370beb931de6

---

# Key Object (ADOX)

Represents a primary, foreign, or unique key field from a database table.
  
## Remarks

The following code creates a new **Key**: 
  
```
Dim obj As New Key

```

With the properties and collections of a **Key** object, you can: 
  
- Identify the key with the [Name](name-property-adox.md) property. 
    
- Determine whether the key is primary, foreign, or unique with the [Type](http://msdn.microsoft.com/library/119a39e3-a397-1afb-2588-8129140810bf%28Office.15%29.aspx) property. 
    
- Access the database columns of the key with the [Columns](columns-collection-adox.md) collection. 
    
- Specify the name of the related table with the [RelatedTable](relatedtable-property-adox.md) property. 
    
- Determine the action performed on deletion or update of a primary key with the [DeleteRule](deleterule-property-adox.md) and [UpdateRule](updaterule-property-adox.md) properties. 
    

