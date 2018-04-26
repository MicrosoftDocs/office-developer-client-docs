---
title: "GetObjectOwner Method (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 716dd49a-8663-3f7a-32a3-0be353aea506

---

# GetObjectOwner Method (ADOX)

Returns the owner of an object in a [Catalog](catalog-object-adox.md).
  
## Syntax

 *Owner*  =  *Catalog*  . **GetObjectOwner**( *ObjectName*  ,  *ObjectType*  [,  *ObjectTypeId*  ]) 
  
## Return Value

Returns a **String** value that specifies the [Name](name-property-adox.md) of the [User](user-object-adox.md) or [Group](group-object-adox.md) that owns the object. 
  
## Parameters

-  *ObjectName* 
    
- A **String** value that specifies the name of the object for which to return the owner. 
    
-  *ObjectType* 
    
- A **Long** value which can be one of the [ObjectTypeEnum](objecttypeenum.md) constants, that specifies the type of the object for which to get the owner. 
    
-  *ObjectTypeId* 
    
- Optional. A **Variant** value that specifies the GUID for a provider object type not defined by the OLE DB specification. This parameter is required if  *ObjectType*  is set to **adPermObjProviderSpecific**; otherwise, it is not used. 
    
## Remarks

An error will occur if the provider does not support returning object owners.
  

