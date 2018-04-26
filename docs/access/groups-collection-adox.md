---
title: "Groups Collection (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9aec57df-bc5c-f9b3-5aec-e7e7efa47ba8

---

# Groups Collection (ADOX)

Contains all stored [Group](group-object-adox.md) objects of a catalog or user. 
  
## Remarks

The **Groups** collection of a [Catalog](catalog-object-adox.md) represents all of the catalog's group accounts. The **Groups** collection for a [User](user-object-adox.md) represents only the group to which the user belongs. 
  
The [Append](append-method-adox-groups.md) method for a **Groups** collection is unique for ADOX. You can: 
  
- Add a new security group to the collection with the **Append** method. 
    
The remaining properties and methods are standard to ADO collections. You can:
  
- Access a group in the collection with the [Item](item-property-ado.md) property. 
    
- Return the number of groups contained in the collection with the [Count](count-property-ado.md) property. 
    
- Remove a group from the collection with the [Delete](delete-method-adox-collections.md) method. 
    
- Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method. 
    
> [!NOTE]
> Before appending a **Group** object to the **Groups** collection of a **User** object, a **Group** object with the same [Name](name-property-adox.md) as the one to be appended must already exist in the **Groups** collection of the **Catalog**. 
  

