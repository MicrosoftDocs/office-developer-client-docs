---
title: "PidTagAnr Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAnr
api_type:
- HeaderDef
ms.assetid: eca3d4ff-2e92-4d20-a498-98e0773c1962
description: "Last modified: March 09, 2015"
---

# PidTagAnr Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a string value for use in a property restriction on an address book container contents table. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ANR, PR_ANR_A, PR_ANR_W  <br/> |
|Identifier:  <br/> |0x360C  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

These properties do not belong to any object; it is furnished by address book providers in [SPropertyRestriction](spropertyrestriction.md) structures. This property contains an ambiguous name resolution (ANR) string that can be tested against an address book container's contents table to find corresponding message recipients. 
  
Address book providers match the value of **PR_ANR** and associated properties against every entry in the contents table, using a provider-defined matching algorithm. The column or columns that are used in this match are chosen by the provider as part of the algorithm. The **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) column is the most commonly used; the **PR_ACCOUNT** ( [PidTagAccount](pidtagaccount-canonical-property.md)) column is also useful when it contains the user's e-mail name. 
  
For more information on ambiguous name resolution, see [Address Book Restrictions](address-book-restrictions.md). 
  
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
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Reference

[IAddrBook::ResolveName](iaddrbook-resolvename.md)
  
[IABContainer::ResolveNames](iabcontainer-resolvenames.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

