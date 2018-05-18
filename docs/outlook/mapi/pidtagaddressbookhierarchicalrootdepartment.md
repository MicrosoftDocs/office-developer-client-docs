---
title: "PidTagAddressBookHierarchicalRootDepartment"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAddressBookHierarchicalRootDepartment
api_type:
- HeaderDef
ms.assetid: c611640b-1a70-4a76-b7ff-c8ad8d320892
description: "Last modified: March 09, 2015"
---

# PidTagAddressBookHierarchicalRootDepartment

  
  
**Applies to**: Outlook 
  
 Contains the distinguished name (DN) of the hierarchical address root (HAB). 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EMS_AB_HAB_ROOT_DEPARTMENT, PR_EMS_AB_HAB_ROOT_DEPARTMENT_A  <br/> |
|Property set:  <br/> |Address Book  <br/> |
|Long ID (LID):  <br/> |0x8C98  <br/> |
|Data type:  <br/> |PT_STRING8  <br/> |
|Area:  <br/> |Exchange Address Book  <br/> |
   
## Remarks

This is a property on the global address list (GAL) container and represents the distinguished name of the hierarchical address root. This property is only present in the offline address book and never in Active Directory Domain Services (AD DS). Callers should pass MAPI_CACHE_ONLY to the GetProps call to avoid a remote procedure call. If this is not present, callers should use PR_EMS_AB_HAB_ROOT_DEPARTMENT, which is of type PT_OBJECT, to find the root department. 
  
Once the root department is obtained, it can have an object type MAPI_MAILUSER or MAPI_DISTLIST. If the object type is MAPI_DISTLIST, the new schema is being employed. If the object type is MAPI_MAILUSER, the previous schema is being employed. 
  
- Microsoft Office Outlook 2007 Service Pack 2 supports both schemas. 
    
- Microsoft Outlook 2010 and Microsoft Outlook 2013 support the new schema.
    
In the new schema, all departmental groups are also distribution lists and are of type MAPI_DISTLIST. Members of departmental groups, and departments within departmental groups are obtained by using PR_EMS_AB_MEMBER, exactly like distribution list members.
  
Once the root department is obtained, it can have an object type MAPI_MAILUSER or MAPI_DISTLIST. If the object type is MAPI_DISTLIST, the new schema is being used. If the object type is MAPI_MAILUSER, the old schema is being used. 
  
In the new schema, all departmental groups are also DLs and are of type MAPI_DISTLIST.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Microsoft Exchange Server protocol specifications.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

