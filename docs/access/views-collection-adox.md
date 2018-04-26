---
title: "Views Collection (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 8d0f9517-4be1-be9c-d4cd-6d50cd5a8983

---

# Views Collection (ADOX)

Contains all [View](view-object-adox.md) objects of a catalog. 
  
## Remarks

The [Append](append-method-adox-views.md) method for a **Views** collection is unique for ADOX. You can: 
  
- Add a new view to the collection with the **Append** method. 
    
The remaining properties and methods are standard to ADO collections. You can:
  
- Access a view in the collection with the [Item](item-property-ado.md) property. 
    
- Return the number of views contained in the collection with the [Count](count-property-ado.md) property. 
    
- Remove a view from the collection with the [Delete](delete-method-adox-collections.md) method. 
    
- Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method. 
    

