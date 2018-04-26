---
title: "Delete Method (ADOX Collections)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: bcf9b8dd-cc7a-c1f9-fd93-58694766c4d9
---

# Delete Method (ADOX Collections)

Removes an object from a collection.
  
## Syntax

 *Collection*  . **Delete** *Name* 
  
## Parameters

-  *Name* 
    
- A **Variant** that specifies the name or ordinal position (index) of the object to delete. 
    
## Remarks

An error will occur if the  *Name*  does not exist in the collection. 
  
For [Tables](tables-collection-adox.md) and [Users](users-collection-adox.md) collections, an error will occur if the provider does not support deleting tables or users, respectively. For [Procedures](procedures-collection-adox.md) and [Views](views-collection-adox.md) collections, **Delete** will fail if the provider does not support persisting commands. 
  

