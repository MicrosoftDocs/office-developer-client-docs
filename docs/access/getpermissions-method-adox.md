---
title: "GetPermissions Method (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 98a2b2b6-a8af-15ee-b052-622a6f0661b9

---

# GetPermissions Method (ADOX)

Returns the permissions for a group or user on an object or object container.
  
## Syntax

 *ReturnValue*  =  *GroupOrUser*  . **GetPermissions**( *Name*  ,  *ObjectType*  [,  *ObjectTypeId*  ]) 
  
## Return Value

Returns a **Long** value that specifies a bitmask containing the permissions that the group or user has on the object. This value can be one or more of the [RightsEnum](rightsenum.md) constants. 
  
## Parameters

-  *Name* 
    
- A **Variant** value that specifies the name of the object for which to set permissions. Set  *Name*  to a null value if you want to get the permissions for the object container. 
    
-  *ObjectType* 
    
- A **Long** value which can be one of the [ObjectTypeEnum](objecttypeenum.md) constants, that specifies the type of the object for which to get permissions. 
    
-  *ObjectTypeId* 
    
- Optional. A **Variant** value that specifies the GUID for a provider object type not defined by the OLE DB specification. This parameter is required if  *ObjectType*  is set to **adPermObjProviderSpecific**; otherwise, it is not used. 
    

