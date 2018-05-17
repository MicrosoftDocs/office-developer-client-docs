---
title: "PidTagDisplayTypeEx Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagDisplayTypeEx
api_type:
- HeaderDef
ms.assetid: 23074402-6ac1-47f1-8a49-b8909f98a26e
description: "Last modified: March 09, 2015"
---

# PidTagDisplayTypeEx Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the type of an entry, with respect to how the entry should be displayed in a row in a table for the Global Address List. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DISPLAY_TYPE_EX  <br/> |
|Identifier:  <br/> |0x3905  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI address book  <br/> |
   
## Remarks

This property specifies the type of an entry, with respect to how it should be displayed in the Global Address List. It provides additional information that cannot be represented in **PR_DISPLAY_TYPE** ( [PidTagDisplayType](pidtagdisplaytype-canonical-property.md)).
  
> [!NOTE]
> The values of both **PR_DISPLAY_TYPE** and this property begin with "DT_" and are defined in Mapitags.h. All values not documented are reserved for MAPI. Client applications must not define any new values and must be prepared to deal with an undocumented value. 
  
There are some macros that can help determine attributes of an object such as whether it is local, remote, or security-controlled. These macros include: 
  
|**Macro**|**Value**|
|:-----|:-----|
|DTE_FLAG_REMOTE_VALID  <br/> |0x80000000)  <br/> |
|DTE_FLAG_ACL_CAPABLE  <br/> |0x40000000  <br/> |
|DTE_MASK_REMOTE  <br/> |0x0000ff00  <br/> |
|DTE_MASK_LOCAL  <br/> |0x000000ff  <br/> |
|DTE_IS_REMOTE_VALID(v)  <br/> |(!!((v) &amp; DTE_FLAG_REMOTE_VALID)  <br/> |
|DTE_IS_ACL_CAPABLE(v)  <br/> |(!!((v) &amp; DTE_FLAG_ACL_CAPABLE))  <br/> |
|DTE_REMOTE(v)  <br/> |(((v) &amp; DTE_MASK_REMOTE) \>\> 8)  <br/> |
|DTE_LOCAL(v)  <br/> |((v) &amp; DTE_MASK_LOCAL)  <br/> |
|DT_ROOM  <br/> |((ULONG) 0x00000007)  <br/> |
|DT_EQUIPMENT  <br/> |((ULONG) 0x00000008)  <br/> |
|DT_SEC_DISTLIST  <br/> |((ULONG) 0x00000009)  <br/> |
   
The following are a few notes about how to use these macros. 
  
- To check whether an entry is a remote entry in another forest, apply the DTE_IS_REMOTE_VALID macro to the value of this property to check whether the DTE_FLAG_REMOTE_VALID flag is set in the entry. If it is a remote entry, you can then find out the type of the remote entry by using the DTE_REMOTE macro. 
    
- In both single-forest and cross-forest configurations, when **PR_DISPLAY_TYPE** has the value of DT_DISTLIST, and DTE_IS_REMOTE_VALID is false, applying the macro DTE_LOCAL to the value of this property can let you further identify the type of the object as either DT_DISTLIST (a distribution list) or DT_SEC_DISTLIST (a security distribution list). 
    
- If you apply the macro DTE_LOCAL to the value of **PR_DISPLAY_TYPE_EX** and it returns the type DT_REMOTE_MAILUSER, then the entry is a remote entry. 
    
- In a single forest or in a cross-forest configuration where replication is controlled by an Access Control List (ACL), you can use the DTE_IS_ACL_CAPABLE macro to determine whether an entry is a security principal.
    
In a cross-forest configuration, **PR_DISPLAY_TYPE** has the value of DT_REMOTE_MAILUSER. Applying the macro DTE_REMOTE to the value of this property can let you obtain the type of the remote entry. The possible types of remote entry are the following: 
  
|**Type of Remote Entry**|**Value**|**Description**|
|:-----|:-----|:-----|
|DT_AGENT  <br/> |((ULONG) 0x00000003)  <br/> |Dynamic distribution list.  <br/> |
|DT_DISTLIST  <br/> |((ULONG) 0x00000001)  <br/> |Distribution list.  <br/> |
|DT_EQUIPMENT  <br/> |((ULONG) 0x00000008)  <br/> |Equipment, for example, a printer or a projector.  <br/> |
|DT_MAILUSER  <br/> |((ULONG) 0x00000000)  <br/> |User with a mailbox.  <br/> |
|DT_REMOTE_MAILUSER  <br/> |((ULONG) 0x00000000)  <br/> |An address list entry in the Global Address List.  <br/> |
|DT_ROOM  <br/> |((ULONG) 0x00000007)  <br/> |Conference room.  <br/> |
|DT_SEC_DISTLIST  <br/> |((ULONG) 0x00000009)  <br/> |Security distribution list.  <br/> |
   
In both a single forest and in a cross-forest configuration, when **PR_DISPLAY_TYPE** has the value of DT_DISTLIST and DTE_IS_REMOTE_VALID is false, applying the DTE_LOCAL macro to the value of this property can let you obtain the type of the distribution list. The possible types of distribution list are the following: 
  
|**Type of Distribution List**|**Value**|**Description**|
|:-----|:-----|:-----|
|DT_DISTLIST  <br/> |((ULONG) 0x00000001)  <br/> |Distribution list.  <br/> |
|DT_SEC_DISTLIST  <br/> |((ULONG) 0x00000009)  <br/> |Security distribution list.  <br/> |
   
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

