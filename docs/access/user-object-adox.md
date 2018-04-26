---
title: "User Object (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e88b9a8a-e70f-c7ca-cb8c-bd274ff24948

---

# User Object (ADOX)

Represents a user account that has access permissions within a secured database.
  
## Remarks

The [Users](users-collection-adox.md) collection of a [Catalog](catalog-object-adox.md) represents all the catalog's users. The **Users** collection for a [Group](group-object-adox.md) represents only the users of the specific group. 
  
With the properties, collections, and methods of a **User** object, you can: 
  
- Identify the user with the [Name](name-property-adox.md) property. 
    
- Change the password for a user with the [ChangePassword](changepassword-method-adox.md) method. 
    
- Determine whether a user has read, write, or delete permissions with the [GetPermissions](getpermissions-method-adox.md) and [SetPermissions](setpermissions-method-adox.md) methods. 
    
- Access the groups to which a user belongs with the [Groups](groups-collection-adox.md) collection. 
    
- Access provider-specific properties with the [Properties](properties-collection-ado.md) collection. 
    

