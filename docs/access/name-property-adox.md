---
title: "Name Property (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c92a3b2b-6e3f-1ed9-c7be-bf348a0737af

---

# Name Property (ADOX)

Indicates the name of the object.
  
## Settings and Return Values

Sets or returns a **String** value. 
  
## Remarks

Names do not have to be unique within a collection.
  
The **Name** property is read/write on [Column](column-object-adox.md), [Group](group-object-adox.md), [Key](key-object-adox.md), [Index](index-object-adox.md), [Table](table-object-adox.md), and [User](user-object-adox.md) objects. The **Name** property is read-only on [Catalog](catalog-object-adox.md), [Procedure](procedure-object-adox.md), and [View](view-object-adox.md) objects. 
  
For read/write objects ( **Column**, **Group**, **Key**, **Index**, **Table** and **User** objects), the default value is an empty string (""). 
  
> [!NOTE]
> For keys, this property is read-only on **Key** objects already appended to a collection. 
  
> [!NOTE]
> For tables, this property is read-only for **Table** objects already appended to a collection. 
  

