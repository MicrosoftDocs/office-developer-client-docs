---
title: "SetPermissions Method (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 63d1053d-fb32-456b-ae67-3a4e45aa01af

---

# SetPermissions Method (ADOX)

Specifies the permissions for a group or user on an object.
  
## Syntax

 *GroupOrUser*  . **SetPermissions** *Name*  ,  *ObjectType*  ,  *Action*  ,  *Rights*  [,  *Inherit*  ] [,  *ObjectTypeId*  ] 
  
## Parameters

-  *Name* 
    
- A **String** value that specifies the name of the object for which to set permissions. 
    
-  *ObjectType* 
    
- A **Long** value which can be one of the [ObjectTypeEnum](objecttypeenum.md) constants, that specifies the type of the object for which to get permissions. 
    
-  *Action* 
    
- A **Long** value which can be one of the [ActionEnum](actionenum.md) constants that specifies the type of action to perform when setting permissions. 
    
-  *Rights* 
    
- A **Long** value which can be a bitmask of one or more of the [RightsEnum](rightsenum.md) constants, that indicates the rights to set. 
    
-  *Inherit* 
    
- Optional. A **Long** value which can be one of the [InheritTypeEnum](inherittypeenum.md) constants, that specifies how objects will inherit these permissions. The default value is **adInheritNone**. 
    
-  *ObjectTypeId* 
    
- Optional. A **Variant** value that specifies the GUID for a provider object type not defined by the OLE DB specification. This parameter is required if  *ObjectType*  is set to **adPermObjProviderSpecific**; otherwise, it is not used. 
    
## Remarks

An error will occur if the provider does not support setting access rights for groups or users.
  
> [!NOTE]
> When calling **SetPermissions**, setting Actions to **adAccessRevoke** overrides any settings of the  *Rights*  parameter. Do not set  *Actions*  to **adAccessRevoke** if you want the rights specified in the  *Rights*  parameter to take effect. 
  

