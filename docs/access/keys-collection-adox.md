---
title: "Keys Collection (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0d480c01-1b36-28b9-9135-51958f313995

---

# Keys Collection (ADOX)

Contains all [Key](key-object-adox.md) objects of a table. 
  
## Remarks

The [Append](append-method-adox-keys.md) method for a **Keys** collection is unique for ADOX. You can: 
  
- Add a new key to the collection with the **Append** method. 
    
The remaining properties and methods are standard to ADO collections. You can:
  
- Access a key in the collection with the [Item](item-property-ado.md) property. 
    
- Return the number of keys contained in the collection with the [Count](count-property-ado.md) property. 
    
- Remove a key from the collection with the [Delete](delete-method-adox-collections.md) method. 
    
- Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method. 
    

