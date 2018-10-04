---
title: "PidTagSearchKey Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_type:
- COM
ms.assetid: fcab369a-a1f4-4425-a272-e35046914a4d
description: "Last modified: March 09, 2015"
---

# PidTagSearchKey Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a binary-comparable key that identifies correlated objects for a search.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SEARCH_KEY  <br/> |
|Identifier:  <br/> |0x300B  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |ID properties  <br/> |
   
## Remarks

This property provides a trace for related objects, such as message copies, and facilitates finding unwanted occurrences, such as duplicate recipients.
  
MAPI uses specific rules for constructing search keys for message recipients. The search key is formed by concatenating the address type (in uppercase characters), the colon character ':', the email address in canonical form, and the terminating null character. Canonical form here means that case-sensitive addresses appear in the correct case, and addresses that are not case-sensitive are converted to uppercase. This is important in preserving correlations among messages.
  
For message objects, this property is available through the [IMAPIProp::GetProps](imapiprop-getprops.md) method immediately following message creation. For other objects, it is available following the first call to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. Because this property is changeable, it is unreliable to obtain it through **GetProps** until a **SaveChanges** call has committed any values set or changed by the [IMAPIProp::SetProps](imapiprop-setprops.md) method. 
  
For profiles, MAPI also furnishes a hard-coded profile section named **MUID_PROFILE_INSTANCE**, with this property as its single property. This key is guaranteed to be unique among all profiles ever created, and can be more reliable than the **PR_PROFILE_NAME** ([PidTagProfileName](pidtagprofilename-canonical-property.md)) property, which can be, for example, deleted and recreated with the same name.
  
The following table summarizes important differences among the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)), **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)), and this property.
  
|**Characteristic**|****PR_ENTRYID****|****PR_RECORD_KEY****|****PR_SEARCH_KEY****|
|:-----|:-----|:-----|:-----|
|Required on attachment objects  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Required on folder objects  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Required on message store objects  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Required on status objects  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|Creatable by client  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Available before **SaveChanges** <br/> |Depends on the provider implementation  <br/> |Depends on the provider implementation  <br/> |For messages, Yes. For others, It depends on the provider implementation.  <br/> |
|Changed in a copy operation  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Changeable by client after a copy  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Unique within ...  <br/> |Entire world  <br/> |Provider instance  <br/> |Entire world  <br/> |
|Binary comparable (as with memcmp)  <br/> |No -- use [IMAPISupport::CompareEntryIDs](imapisupport-compareentryids.md) <br/> |Yes  <br/> |Yes  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagResponsibility Canonical Property](pidtagresponsibility-canonical-property.md)
  
[PidTagStoreRecordKey Canonical Property](pidtagstorerecordkey-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

