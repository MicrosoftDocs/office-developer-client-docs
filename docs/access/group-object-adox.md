---
title: "Group Object (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 91cf1b87-c928-1d89-2731-138f6299cc60

---

# Group Object (ADOX)

Represents a group account that has access permissions within a secured database.
  
## Remarks

The [Groups](groups-collection-adox.md) collection of a [Catalog](catalog-object-adox.md) represents all the catalog's group accounts. The **Groups** collection for a [User](user-object-adox.md) represents only the group to which the user belongs. 
  
With the properties, collections, and methods of a **Group** object, you can: 
  
- Identify the group with the [Name](name-property-adox.md) property. 
    
- Determine whether a group has read, write, or delete permissions with the [GetPermissions](getpermissions-method-adox.md) and [SetPermissions](setpermissions-method-adox.md) methods. 
    
- Access the user accounts that have memberships in the group with the [Users](users-collection-adox.md) collection. 
    
- Access provider-specific properties with the [Properties](properties-collection-ado.md) collection. 
    

