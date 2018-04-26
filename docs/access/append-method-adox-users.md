---
title: "Append Method (ADOX Users)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b7a1128b-c6e7-2071-c914-913b6bd245ae
---

# Append Method (ADOX Users)

Adds a new [User](user-object-adox.md) object to the [Users](users-collection-adox.md) collection. 
  
## Syntax

 *Users*  . **Append** *User*  [,  *Password*  ] 
  
## Parameters

-  *User* 
    
- A **Variant** value that contains the **User** object to append or the name of the user to create and append. 
    
-  *Password* 
    
- Optional. A **String** value that contains the password for the user. The  *Password*  parameter corresponds to the value specified by the [ChangePassword](changepassword-method-adox.md) method of a **User** object. 
    
## Remarks

The **Users** collection of a [Catalog](catalog-object-adox.md) represents all the catalog's users. The **Users** collection for a [Group](group-object-adox.md) represents only the users that have a membership in the specific group. 
  
An error will occur if the provider does not support creating users.
  
> [!NOTE]
> Before appending a **User** object to the **Users** collection of a **Group** object, a **User** object with the same [Name](name-property-adox.md) as the one to be appended must already exist in the **Users** collection of the **Catalog**. 
  

